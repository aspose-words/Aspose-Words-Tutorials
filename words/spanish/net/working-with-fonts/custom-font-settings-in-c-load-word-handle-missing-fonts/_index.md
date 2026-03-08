---
category: general
date: 2026-03-08
description: La configuración de fuentes personalizada le permite establecer la configuración
  de fuentes, cargar documentos Word de forma segura y manejar fuentes faltantes con
  Aspose.Words.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: es
og_description: La configuración de fuentes personalizada le permite establecer la
  configuración de fuentes, cargar documentos de Word de forma segura y gestionar
  fuentes faltantes con Aspose.Words.
og_title: Configuración de fuentes personalizadas en C# – Cargar Word y manejar fuentes
  faltantes
tags:
- Aspose.Words
- C#
- Font Management
title: Configuración de fuentes personalizadas en C# – Cargar Word y gestionar fuentes
  faltantes
url: /es/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

to preserve headings levels.

Proceed to output.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Configuración de fuentes personalizadas en C# – Cargar Word y manejar fuentes faltantes

¿Alguna vez te has preguntado cómo funcionan los **custom font settings** cuando un archivo Word hace referencia a fuentes que no tienes instaladas? Es un problema frecuente: tu documento se ve bien en una máquina y, de repente, cada párrafo cambia a una fuente de reserva en otra.  

¿La buena noticia? Con Aspose.Words puedes **set font settings**, **load Word document** content y **handle missing fonts** todo en un flujo ordenado. A continuación encontrarás un ejemplo completo, listo‑para‑ejecutar, que muestra exactamente cómo hacerlo, además del “por qué” detrás de cada paso.

## Lo que aprenderás

* Crear un objeto `LoadOptions` y adjuntar una instancia de `FontSettings`.  
* Registrar una callback de advertencia para que puedas ver qué fuentes se sustituyen.  
* Cargar un archivo DOCX que puede tener fuentes faltantes y imprimir los detalles de sustitución en la consola.  

Al final podrás distribuir tu aplicación C# con confianza, sabiendo que cada escenario de fuente faltante se registra y puede abordarse más tarde.

> **Prerequisite:** Aspose.Words for .NET (v23.12 o posterior) instalado a través de NuGet, y una familiaridad básica con aplicaciones de consola C#.

---

## Configuración de fuentes personalizadas – Configurar LoadOptions

Lo primero que necesitas es un objeto `LoadOptions`. Esto indica a Aspose.Words cómo tratar el archivo entrante. Al asignar una nueva instancia de `FontSettings` le damos a la biblioteca un lugar donde buscar fuentes personalizadas.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Por qué esto es importante:**  
Si omites `FontSettings`, Aspose.Words recurre a la colección de fuentes predeterminada del sistema. Eso significa que cualquier fuente faltante será sustituida silenciosamente, y no sabrás cuáles se cambiaron. Al crear un contenedor explícito de `FontSettings` obtienes control total sobre el proceso de búsqueda.

---

## Establecer Font Settings en LoadOptions

Ahora que tenemos un objeto `FontSettings`, quizás te preguntes a dónde apuntarlo. Normalmente agregarías una carpeta que contiene las fuentes que distribuyes con tu aplicación:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Si no tienes una carpeta privada, puedes omitir este bloque—Aspose.Words seguirá informando fuentes faltantes a través de la callback de advertencia.*

**Consejo profesional:** Utiliza la bandera `recursive: true` si tus fuentes están repartidas en sub‑carpetas. Te ahorra agregar cada ruta manualmente.

---

## Cargar documento Word con Font Settings personalizados

Con las opciones preparadas, cargar el documento es muy sencillo. El constructor `Document` acepta la ruta del archivo y el `LoadOptions` que acabamos de crear.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**¿Qué está sucediendo internamente?**  
Aspose.Words analiza el DOCX, verifica cada referencia `<w:font>` y consulta los `FontSettings` que proporcionaste. Si no se encuentra una fuente, genera una advertencia del tipo `FontSubstitution`. Nuestro manejador personalizado (mostrado a continuación) capturará esas advertencias.

---

## Manejar fuentes faltantes con Warning Callback

La interfaz `IWarningCallback` te permite reaccionar a cualquier problema que surja durante la carga. Implementarla es sencillo:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Cuando el documento se carga, cada fuente faltante generará una línea como:

```
Font substituted: Arial -> Liberation Sans
```

**Por qué deberías registrar esto:**  
En producción puedes redirigir estos mensajes a un archivo o a un sistema de telemetría, facilitando la identificación de las fuentes que necesitas empaquetar o licenciar.

---

## Ejemplo completo y funcional

A continuación tienes un programa de consola autónomo que une todo. Copia‑pega el código en un nuevo proyecto de consola .NET Core y pulsa **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Salida esperada** (suponiendo que `input.docx` usa una fuente que no tienes):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Si todas las fuentes están presentes, solo verás la línea de confirmación final.

---

## Preguntas frecuentes y casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Qué pasa si necesito incrustar las fuentes faltantes en el PDF?** | Después de cargar, llama a `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` y luego habilita la incrustación con `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **¿Puedo suprimir las advertencias en lugar de registrarlas?** | Sí—establece `loadOptions.WarningCallback = null;` o implementa la callback para ignorar las advertencias que no sean de fuentes. |
| **¿Funciona esto con archivos `.doc` y `.rtf`?** | Absolutamente. El mismo objeto `LoadOptions` se aplica a cualquier formato soportado por Aspose.Words. |
| **¿Es la callback segura para subprocesos?** | La callback se ejecuta en el mismo hilo que carga el documento, por lo que puedes escribir de forma segura en la consola. Para escenarios multihilo, usa una colección concurrente o un framework de registro. |

---

## Consejos profesionales y trampas

* **Consejo profesional:** Si distribuyes una fuente que no está instalada en la máquina objetivo, añádela a la carpeta que pasas a `SetFontsFolder`. Esto garantiza una renderización determinista.
* **Cuidado con las licencias:** Algunas fuentes requieren licencias comerciales para su incrustación. Siempre verifica la EULA de la fuente antes de empaquetarla.
* **Nota de rendimiento:** Cargar bibliotecas grandes de fuentes puede ralentizar el análisis del documento. Mantén la carpeta ligera—incluye solo las fuentes que realmente necesitas.
* **Caso límite:** Cuando un documento hace referencia a una fuente por su *nombre PostScript* en lugar del nombre de familia, Aspose.Words aún la resuelve siempre que el archivo de fuente esté presente en la ruta de búsqueda.

---

## Conclusión

Ahora tienes un patrón completo y listo para producción para usar **custom font settings** en C#. Configurando `LoadOptions`, registrando una callback de advertencia y, opcionalmente, apuntando a una carpeta de fuentes privada, puedes **set font settings**, **load Word document** content de manera fiable

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}