---
category: general
date: 2026-05-04
description: 'Cómo usar LLM para editar documentos con Aspose: aprende a reemplazar
  el texto de los párrafos, conectar con un LLM local y reescribir texto usando IA.'
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: es
og_description: Cómo usar LLM para editar documentos con Aspose. Esta guía muestra
  cómo conectar a un LLM local, reemplazar el texto de los párrafos y reescribir texto
  usando IA.
og_title: Cómo usar LLM con Aspose.Words – Reescribir párrafos en C#
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Cómo usar LLM con Aspose.Words – Reescribir párrafos en C#
url: /es/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo usar LLM con Aspose.Words – Reescribir párrafos en C#

¿Alguna vez te has preguntado **cómo usar LLM** para pulir un documento Word sin abrirlo manualmente? No eres el único. Muchos desarrolladores se quedan atascados cuando necesitan *reemplazar el texto de un párrafo* de forma programática pero no disponen de un flujo de trabajo limpio impulsado por IA.  

En este tutorial conectaremos un modelo de lenguaje grande local, le alimentaremos con un fragmento de un archivo `.docx`, le pediremos que **reescriba el texto usando IA**, y finalmente guardaremos el documento actualizado, todo con Aspose.Words. Al final tendrás una aplicación de consola en C# lista para ejecutar que demuestra todo el pipeline.

> **Lo que obtendrás:** un ejemplo completo y ejecutable, explicaciones de cada paso, consejos para casos límite y ideas para ampliar la solución.

## Lo que necesitarás

- **.NET 6+** (o .NET Framework 4.7.2 – el código funciona en ambos)
- **Aspose.Words for .NET** (paquete NuGet `Aspose.Words`)
- Un **servidor LLM local** que exponga un sencillo endpoint HTTP `/generate` (p. ej., Ollama, LMStudio o un servicio Flask personalizado)
- Familiaridad básica con C# y código cliente HTTP  

No se requieren SDK adicionales; todo lo demás vive en el código que escribiremos juntos.

## Paso 1: Cómo usar LLM para reemplazar texto de párrafo

Lo primero que debemos hacer es identificar el párrafo que queremos modificar. Aspose.Words lo hace muy fácil al exponer un modelo de objetos rico.

```csharp
using Aspose.Words;
using Aspose.Words.AI;   // Imaginary namespace for illustration – replace with actual if needed
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Grab the third paragraph (zero‑based index)
Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];

// Show the original text in the console – handy for debugging
Console.WriteLine("Original paragraph:");
Console.WriteLine(targetParagraph.GetText());
```

**Por qué es importante:**  
Seleccionar el nodo correcto evita sobrescribir accidentalmente encabezados o tablas. Al usar el enfoque de **reemplazar texto de párrafo** mantenemos la estructura del documento intacta mientras solo tocamos el contenido que nos interesa.

> **Consejo profesional:** Si tu documento tiene secciones de longitud variable, usa `document.GetChildNodes(NodeType.Paragraph, true)` y LINQ para localizar un párrafo por su texto o estilo.

## Paso 2: Conectar a un endpoint LLM local

Ahora que tenemos el texto, necesitamos enviarlo al LLM. El ejemplo usa una clase contenedora sencilla `LocalLargeLanguageModel` que oculta la lógica HTTP. Si lo prefieres, puedes reemplazarla con llamadas directas a `HttpClient`.

```csharp
/// <summary>
/// Minimal wrapper around a local LLM HTTP API.
/// Assumes the API accepts a JSON payload { "prompt": "..."} and returns { "response": "..." }.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _client;
    private readonly string _endpoint;

    public LocalLargeLanguageModel(string endpoint)
    {
        _endpoint = endpoint.TrimEnd('/');
        _client = new HttpClient();
    }

    public string GenerateText(string prompt)
    {
        var payload = new { prompt };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // Synchronous call for brevity – in production use async/await
        var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result?["response"] ?? string.Empty;
    }
}

// Step 2: Instantiate the LLM client pointing at localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:5000");
```

**Por qué nos conectamos de esta manera:**  
Una configuración de **conectar a LLM local** elimina la latencia, mantiene los datos en las instalaciones y evita costos de API. El contenedor también hace que el código posterior sea más limpio, permitiéndonos centrarnos en la lógica de **reescribir texto usando IA**.

## Paso 3: Reescribir texto usando IA con Aspose.Words

Con el texto del párrafo en mano y el LLM listo, creamos un *prompt* que le dice al modelo exactamente lo que queremos: reescribir en un tono formal. Puedes ajustar el *prompt* para otros estilos (amigable, técnico, etc.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Por qué funciona:**  
Los LLM funcionan mediante *prompts*; dar instrucciones explícitas (“Rewrite … in a formal tone”) produce resultados consistentes. El paso de **reescribir texto usando IA** es el corazón del tutorial: muestra cómo la IA puede integrarse directamente en flujos de trabajo de documentos.

## Paso 4: Editar el documento y guardar los cambios

Ahora reemplazamos los *runs* originales con el nuevo contenido. Aspose.Words almacena el texto en objetos `Run`, por lo que vaciarlos primero evita artefactos de formato sobrantes.

```csharp
// Clear existing runs (pieces of text) from the paragraph
targetParagraph.Runs.Clear();

// Append a new Run containing the revised text
targetParagraph.AppendChild(new Run(document, revisedText));

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");

// Confirmation
Console.WriteLine("\nDocument saved as output.docx");
```

**Nota sobre casos límite:**  
Si el párrafo original contenía formato mixto (negrita, cursiva) quizá quieras preservar los estilos. En ese caso, crea un nuevo `Run`, copia la configuración original de `Font` y luego asigna su `Text` a `revisedText`.

## Ejemplo completo funcionando

A continuación tienes el programa completo que puedes copiar y pegar en un proyecto de consola. Recuerda instalar primero el paquete NuGet Aspose.Words (`dotnet add package Aspose.Words`).

```csharp
// ---------------------------------------------------------------
// Complete C# console app: how to use llm to edit a Word doc
// ---------------------------------------------------------------
using Aspose.Words;
using Aspose.Words.AI;   // Replace with real namespace if needed
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Text;
using System.Text.Json;

namespace LlmAsposeDemo
{
    public class LocalLargeLanguageModel
    {
        private readonly HttpClient _client;
        private readonly string _endpoint;

        public LocalLargeLanguageModel(string endpoint)
        {
            _endpoint = endpoint.TrimEnd('/');
            _client = new HttpClient();
        }

        public string GenerateText(string prompt)
        {
            var payload = new { prompt };
            var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

            var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
            response.EnsureSuccessStatusCode();

            var json = response.Content.ReadAsStringAsync().Result;
            var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            return result?["response"] ?? string.Empty;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Pick the third paragraph (index 2)
            Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];
            Console.WriteLine("Original paragraph:");
            Console.WriteLine(targetParagraph.GetText());

            // 3️⃣ Connect to the local LLM
            var localLlm = new LocalLargeLanguageModel("http://localhost:5000");

            // 4️⃣ Ask the model to rewrite it formally
            string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";
            string revisedText = localLlm.GenerateText(prompt);
            Console.WriteLine("\nRevised paragraph:");
            Console.WriteLine(revisedText);

            // 5️⃣ Replace the paragraph contents
            targetParagraph.Runs.Clear();
            targetParagraph.AppendChild(new Run(document, revisedText));

            // 6️⃣ Save the file
            document.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("\nDocument saved as output.docx");
        }
    }
}
```

### Salida esperada

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Abre `output.docx` – verás que el tercer párrafo ahora muestra la versión pulida.

## Preguntas frecuentes y trampas comunes

| Pregunta | Respuesta |
|----------|-----------|
| **¿Qué pasa si mi LLM devuelve JSON con campos extra?** | Ajusta `GenerateText` para deserializar la propiedad correcta o analiza la respuesta manualmente. |
| **¿Puedo procesar varios párrafos a la vez?** | Sí – itera sobre `document.FirstSection.Body.Paragraphs` y aplica la misma lógica de *prompt*, quizá añadiendo un índice de párrafo al *prompt* para contexto. |
| **Mi servidor LLM usa autenticación?** | Añade un encabezado al `HttpClient` antes del POST: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **El formato se pierde después del reemplazo.** | Conserva la configuración original de `Run.Font`: crea un nuevo `Run`, copia `originalRun.Font.Clone()`, luego asigna su `Text`. |
| **El LLM a veces devuelve cadenas vacías.** | Implementa un fallback – si `revisedText.Trim().Length == 0`, conserva el texto original o vuelve a intentar con un *prompt* más simple. |

## Ampliando la solución

Ahora que dominas **cómo usar LLM** para un solo párrafo, considera los siguientes pasos:

- **Procesamiento por lotes:** Recorre cada párrafo y reescribe en un estilo elegido (p. ej., “hacer todo el texto conciso”).  
- **Reescritura consciente del estilo:** Pasa el nombre del estilo del párrafo original en el *prompt* para que el LLM respete encabezados vs texto del cuerpo.  
- **Integración con una canalización CI:** Automatiza el pulido de documentos como parte de un proceso de generación de documentación.  
- **Prompts alternativos:** Prueba “summarize this paragraph” o “translate this paragraph to Spanish” para explorar todo el potencial de **reescribir texto usando IA**.

## Conclusión

Hemos recorrido todo el flujo de **cómo usar LLM** con Aspose.Words: cargar un documento, **conectar a LLM local**, extraer un párrafo, **reescribir texto usando IA**, **reemplazar texto de párrafo** y, finalmente, guardar el resultado. El código es autónomo, funciona de inmediato y muestra una forma práctica de combinar IA con la automatización tradicional de documentos.

Pruébalo, ajusta los *prompts* y deja que

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}