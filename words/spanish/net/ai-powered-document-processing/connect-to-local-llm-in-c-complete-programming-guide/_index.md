---
category: general
date: 2026-04-28
description: Conectar a un LLM local desde C# y solicitar al modelo de lenguaje grande
  que cargue un documento Word, llamar al LLM local y reescribir el texto automáticamente.
  Código paso a paso incluido.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: es
og_description: Conéctate a un LLM local desde C# y descubre cómo interactuar con
  un modelo de lenguaje grande, cargar un documento Word, invocar el LLM local y reescribir
  el texto automáticamente en minutos.
og_title: Conectar a un LLM local en C# – Guía completa de programación
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: Conectar a LLM local en C# – Guía completa de programación
url: /es/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Conectar a un LLM local en C# – Guía completa de programación

¿Alguna vez necesitaste **conectar a un LLM local** desde una aplicación .NET y te preguntaste cómo hacerlo hablar con un archivo Word? No estás solo. En esta guía recorreremos todo el proceso: conectar a un LLM local, **prompt large language model**, cargar un documento Word, **call local llm**, y finalmente **rewrite text automatically**. Al final tendrás un ejemplo ejecutable que transforma cualquier párrafo a un tono formal sin claves de API externas.

## Qué cubre este tutorial

Comenzaremos instalando los paquetes NuGet necesarios, luego pondremos en marcha un sencillo endpoint LLM local (piensa en Ollama en el puerto 11434). Después cargaremos un archivo `.docx` usando Aspose.Words, enviaremos un párrafo al LLM, recibiremos una versión reescrita y la volveremos a escribir en el mismo documento. También verás cómo manejar problemas comunes—párrafos nulos, eliminación asíncrona y peculiaridades de codificación—para que el código funcione en producción, no solo en una demo.

### Prerrequisitos

- .NET 6.0 SDK o posterior (también puedes usar .NET 8 si lo prefieres)
- Visual Studio 2022 o VS Code con la extensión C#
- **Aspose.Words for .NET** (la prueba gratuita funciona bien)
- Un LLM alojado localmente que siga el contrato `/api/generate` (p. ej., Ollama, LMStudio)
- Familiaridad básica con async/await en C#

> **Pro tip:** Si aún no has instalado Ollama, ejecuta `ollama serve` y descarga un modelo con `ollama pull llama3`. El endpoint HTTP predeterminado será `http://localhost:11434/api/generate`.

---

## Paso 1: Instalar los paquetes requeridos

Primero, agrega los paquetes NuGet Aspose.Words y Aspose.Words.AI a tu proyecto.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Estas bibliotecas nos dan la capacidad de **load word document** y un contenedor ligero para **call local llm** sin crear manualmente solicitudes HTTP.

---

## Paso 2: Conectar al endpoint LLM local

Conectar a un modelo alojado localmente es tan simple como instanciar `LocalLargeLanguageModel`. El constructor espera la URL completa del endpoint de generación.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

¿Por qué envolvemos el endpoint en una clase? `LocalLargeLanguageModel` maneja la serialización JSON, reintentos y respuestas en streaming por ti—para que puedas centrarte en la lógica del prompt en lugar de lidiar con `HttpClient`.

---

## Paso 3: Cargar el documento Word de origen

A continuación, traemos el documento a memoria. Aspose.Words soporta prácticamente todos los formatos de Word, así que `Document` analizará `input.docx` sin necesidad de tener Office instalado.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Si necesitas trabajar con un stream (p. ej., un archivo subido vía ASP.NET), simplemente reemplaza la ruta del archivo con un `MemoryStream` y pásalo al constructor de `Document`.

---

## Paso 4: Extraer el texto del párrafo actual

Usaremos `DocumentBuilder` para navegar por el documento. En este ejemplo reescribimos **el primer párrafo**, pero puedes iterar sobre `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` para procesar muchos.

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

El operador `?.` evita una `NullReferenceException` si el documento resulta estar vacío. Este es uno de esos **edge cases** que hacen tropezar a los principiantes.

---

## Paso 5: Prompt the LLM to Rewrite the Paragraph

Ahora realmente **prompt large language model**. El prompt está en inglés sencillo; el contenedor lo enviará como JSON al endpoint local.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

¿Por qué formular la solicitud de esta manera? Los LLM responden mejor a instrucciones claras y de una sola tarea. Añadir una nueva línea después de los dos puntos separa la instrucción del contenido, reduciendo la probabilidad de que el modelo repita el prompt.

**Salida esperada** – Si `originalParagraph` era `"Hey, what's up?"`, el LLM podría devolver:

> “Good day, how may I assist you?”

Puedes verificar el resultado imprimiéndolo:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## Paso 6: Insertar el texto reescrito de nuevo en el documento

Con el nuevo texto en mano, reemplazamos el párrafo antiguo. `DocumentBuilder.Writeln` escribe una nueva línea y avanza el cursor, lo que es perfecto para añadir contenido. Si necesitas *reemplazar* exactamente el mismo párrafo, puedes usar `docBuilder.CurrentParagraph.RemoveAllChildren()` antes de escribir.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Se muestran ambos enfoques para que elijas el que mejor se adapte a tu flujo de trabajo.

---

## Paso 7: Guardar el documento actualizado

Finalmente, persistimos los cambios en un archivo nuevo. Aspose.Words elige automáticamente el formato según la extensión del archivo.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Abre `output.docx` en Word y verás que el párrafo ahora se lee en un tono formal.

---

## Ejemplo completo y funcional

A continuación tienes el **programa completo y autocontenido**. Copia‑pega en un proyecto de consola, restaura los paquetes NuGet y ejecútalo—no se requiere configuración adicional más allá de un LLM local en funcionamiento.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### Qué esperar al ejecutarlo

1. La consola imprime los párrafos original y reescrito.  
2. `output.docx` aparece junto a `input.docx`.  
3. Al abrir el archivo se muestra el nuevo párrafo formal insertado después del original (o reemplazado, si usaste el código alternativo).

---

## Manejo de casos límite comunes

| Situación | Solución |
|-----------|----------|
| **Párrafo vacío o solo con espacios** | Verifica `string.IsNullOrWhiteSpace` antes de hacer el prompt (ver Paso 3). |
| **LLM devuelve un error o cadena vacía** | Envuelve `PromptAsync` en un `try/catch` y recurre al texto original. |
| **Varios párrafos necesitan reescritura** | Recorre `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` y aplica la misma lógica de prompt. |
| **Documentos grandes generan latencia** | Agrupa párrafos y envíalos en una sola solicitud (prompt de hasta 4 KB por llamada). |
| **Caracteres no ASCII se corrompen** | Asegúrate de que el endpoint LLM use UTF-8 (la mayoría de los modelos modernos lo hacen). |

---

## Próximos pasos y temas relacionados

- **Prompt large language model** con instrucciones más ricas (p. ej., guías de estilo, límites de longitud).  
- Usa **call local llm** en una API web para exponer la automatización de documentos como servicio.  
- Explora **load word document** en streams paralelos para escenarios de alto rendimiento.  
- Combina este enfoque con **rewrite text automatically** para generación masiva de correos electrónicos o estandarización de informes.  

Si deseas profundizar, revisa la documentación de Aspose sobre **document merging** y la referencia de la API de Ollama para parámetros de muestreo personalizados.

---

## Conclusión

Acabamos de mostrarte cómo **connect to local llm** desde C#, **prompt large language model**, **load word document**, **call local llm**, y **rewrite text automatically**, todo en una única aplicación de consola ejecutable. El patrón escala: cambia el prompt, itera sobre párrafos o expón la lógica mediante un endpoint ASP.NET. La lección clave es que los modelos de IA locales pueden integrarse estrechamente con bibliotecas clásicas de procesamiento de documentos, brindándote una automatización poderosa sin salir de tu entorno on‑prem confiable.

¿Tienes preguntas sobre threading?

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}