---
category: general
date: 2026-06-05
description: Configura las opciones de carga de documentos en C# para manejar advertencias
  de sustitución de fuentes y personalizar el comportamiento de carga mediante una
  devolución de llamada de advertencia.
draft: false
keywords:
- configure document load options
- warning callback
- font substitution warning
- LoadOptions usage
- Aspose.Words document loading
- C# document loading options
language: es
og_description: Configura las opciones de carga de documentos en C# para gestionar
  advertencias de sustitución de fuentes y ajustar finamente la carga del documento
  con una devolución de llamada de advertencia.
og_title: Configura las opciones de carga de documentos en C# – Guía completa
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  headline: Configure document load options in C# – Complete Guide
  type: TechArticle
- description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  name: Configure document load options in C# – Complete Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Framework 4.6+ as well).
      - Aspose.Words for .NET installed (`dotnet add package Aspose.Words`). - Basic
      familiarity with C# syntax.'
  - name: Implement a Warning Callback for Font Substitution
    text: First things first—what’s a **warning callback**? In Aspose.Words it’s a
      delegate that gets invoked whenever the library encounters something worth flagging,
      like a missing font. By catching `WarningType.FontSubstitution` we can log the
      exact font the engine swapped out.
  - name: Set Up LoadOptions with the Callback
    text: Now that we have a callback, we need to **configure document load options**
      to actually use it. `LoadOptions` is a lightweight container that tells Aspose.Words
      how to behave during the `Document` constructor call.
  - name: Load the Document Using the Configured Options
    text: With the callback wired up, the final act is to actually **load the document**.
      The `Document` constructor accepts a file path and the `LoadOptions` we just
      prepared.
  - name: Optional – Verify Loaded Fonts (Edge Case Handling)
    text: Sometimes you might want to *pre‑validate* the document before loading it
      fully, especially in batch processing scenarios. Aspose.Words offers the `FontSettings`
      class that can enumerate required fonts.
  - name: What if the warning callback throws an exception?
    text: The callback runs on the same thread that loads the document. Throwing inside
      the delegate will abort the load and propagate the exception. Wrap your logic
      in a `try/catch` if you need resilience.
  - name: Can I suppress *all* warnings instead of handling them?
    text: Yes—set `loadOptions.WarningCallback = null;` or provide a callback that
      does nothing. Be aware you’ll lose visibility into potential problems.
  - name: Does this work with encrypted DOCX files?
    text: Absolutely. Just add `Password = "yourPassword"` to `LoadOptions` before
      creating the `Document`. The warning callback will still fire for font issues.
  - name: How does this differ from using `DocumentBuilder`?
    text: '`DocumentBuilder` is for *creating* or *modifying* a document after it’s
      loaded. **Configure document load options** influences the *initial* parsing
      stage, which is where font substitution decisions are made.'
  type: HowTo
tags:
- C#
- Aspose.Words
- LoadOptions
- DocumentProcessing
title: Configura las opciones de carga de documentos en C# – Guía completa
url: /es/net/programming-with-loadoptions/configure-document-load-options-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Configurar opciones de carga de documentos en C# – Guía completa

¿Alguna vez necesitaste **configurar opciones de carga de documentos** en C# porque el comportamiento de carga predeterminado simplemente no era suficiente? Tal vez estés viendo sustituciones de fuentes inesperadas o quieras registrar cada advertencia que aparece durante la importación de un archivo. En este tutorial recorreremos una solución práctica, de extremo a extremo, que no solo configura esas opciones sino que también muestra un **callback de advertencia** para advertencias de sustitución de fuentes.

Cubriremos todo, desde el pequeño fragmento de código que crea el callback hasta el momento en que finalmente abras el documento con tus configuraciones personalizadas. Al final tendrás un patrón reutilizable que puedes incorporar en cualquier proyecto de Aspose.Words, ya sea que estés procesando facturas, contratos legales o informes simples.

## Lo que aprenderás

- Cómo **configurar opciones de carga de documentos** con `LoadOptions`.
- Cómo implementar un **callback de advertencia** que capture alertas de `FontSubstitution`.
- Por qué manejar una **advertencia de sustitución de fuentes** temprano puede evitar sorpresas de maquetación.
- Manejo de casos límite para fuentes faltantes y cómo retroceder de forma elegante.
- Un ejemplo de código completo, listo para copiar y pegar, que puedes ejecutar hoy.

### Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+).
- Aspose.Words para .NET instalado (`dotnet add package Aspose.Words`).
- Familiaridad básica con la sintaxis de C#.

Si los tienes, vamos a sumergirnos.

## Configurar opciones de carga de documentos – Paso a paso

A continuación se muestra el flujo completo dividido en cuatro pasos claros. Cada paso se explica y luego se sigue con un bloque de código conciso que puedes pegar directamente en Visual Studio.

### Paso 1: Implementar un callback de advertencia para sustitución de fuentes

Primero lo primero—¿qué es un **callback de advertencia**? En Aspose.Words es un delegado que se invoca cada vez que la biblioteca encuentra algo que vale la pena señalar, como una fuente faltante. Al capturar `WarningType.FontSubstitution` podemos registrar la fuente exacta que el motor sustituyó.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Define a warning callback that reports font substitution warnings
var fontWarningCallback = new IWarningCallback(
    warningInfo =>
    {
        // Check if the warning is about font substitution
        if (warningInfo.WarningType == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or telemetry system
            Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
        }
    });
```

**Por qué es importante:** Sin un callback, la biblioteca reemplaza silenciosamente las fuentes faltantes, lo que puede provocar texto distorsionado en el PDF o DOCX final. Al exponer la advertencia obtienes visibilidad y puedes decidir si incrustar la fuente faltante, cambiar a una alternativa o alertar al usuario.

> **Consejo profesional:** Si necesitas capturar *todas* las advertencias, elimina la condición `if`. Simplemente registra `warningInfo.Description` para cada evento.

### Paso 2: Configurar LoadOptions con el callback

Ahora que tenemos un callback, necesitamos **configurar opciones de carga de documentos** para usarlo realmente. `LoadOptions` es un contenedor ligero que indica a Aspose.Words cómo comportarse durante la llamada al constructor `Document`.

```csharp
// Step 2: Attach the callback to the LoadOptions object
var loadOptions = new LoadOptions
{
    WarningCallback = fontWarningCallback,
    // Optional: enforce strict loading mode (throws on any warning)
    // LoadFormat = LoadFormat.Docx,
    // LoadOptions.LoadFormat can be left null to auto-detect based on file extension
};
```

**Por qué es importante:** Al asignar `WarningCallback`, cada advertencia emitida durante la fase de carga pasa por nuestro delegado. También puedes ajustar otras propiedades de `LoadOptions` aquí—como `LoadFormat` si conoces el tipo exacto de archivo, o `Password` para documentos cifrados.

### Paso 3: Cargar el documento usando las opciones configuradas

Con el callback configurado, el acto final es realmente **cargar el documento**. El constructor `Document` acepta una ruta de archivo y los `LoadOptions` que acabamos de preparar.

```csharp
// Step 3: Load the document with our custom options
string inputPath = @"C:\Docs\input.docx";   // Adjust to your environment
Document doc = new Document(inputPath, loadOptions);
```

Si el archivo fuente hace referencia a una fuente que no está instalada en la máquina, verás una línea como:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

en la consola. Esta retroalimentación inmediata te permite decidir si incluir la fuente faltante junto con tu aplicación o reemplazarla programáticamente.

### Paso 4: Opcional – Verificar fuentes cargadas (manejo de casos límite)

A veces podrías querer *pre‑validar* el documento antes de cargarlo completamente, especialmente en escenarios de procesamiento por lotes. Aspose.Words ofrece la clase `FontSettings` que puede enumerar las fuentes requeridas.

```csharp
// Optional: Check required fonts before full load
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
loadOptions.FontSettings = fontSettings;

// Re-load the document now that we have a custom font folder
Document docWithCustomFonts = new Document(inputPath, loadOptions);
```

**Cuándo usar esto:** Si mantienes un repositorio privado de fuentes (por ejemplo, fuentes de la marca corporativa), apuntar `FontSettings` a esa carpeta garantiza que el motor encuentre los tipos de letra correctos sin recurrir a genéricos.

## Ejemplo completo en funcionamiento

A continuación se muestra el programa completo—solo copia, pega y ejecuta. Demuestra todo, desde la creación del callback hasta la carga final del documento.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // 1️⃣ Define the warning callback
        var fontWarningCallback = new IWarningCallback(
            warningInfo =>
            {
                if (warningInfo.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
                }
            });

        // 2️⃣ Configure LoadOptions with the callback
        var loadOptions = new LoadOptions
        {
            WarningCallback = fontWarningCallback,
            // Uncomment the next line to point to a custom font folder
            // FontSettings = new FontSettings { SetFontsFolder(@"C:\MyFonts", true) }
        };

        // 3️⃣ Load the document using the custom options
        string inputFile = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputFile, loadOptions);

        // 4️⃣ (Optional) Save as PDF to verify everything works
        string outputFile = @"YOUR_DIRECTORY/output.pdf";
        doc.Save(outputFile);
        Console.WriteLine($"Document loaded and saved to {outputFile}");
    }
}
```

**Salida esperada**

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Document loaded and saved to C:\Your\Path\output.pdf
```

Si no existen fuentes faltantes, el callback simplemente permanece silencioso—no hay nada de qué preocuparse.

## Preguntas frecuentes y casos límite

### ¿Qué pasa si el callback de advertencia lanza una excepción?

El callback se ejecuta en el mismo hilo que carga el documento. Lanzar una excepción dentro del delegado abortará la carga y propagará la excepción. Envuelve tu lógica en un `try/catch` si necesitas resiliencia.

### ¿Puedo suprimir *todas* las advertencias en lugar de manejarlas?

Sí—establece `loadOptions.WarningCallback = null;` o proporciona un callback que no haga nada. Ten en cuenta que perderás visibilidad de posibles problemas.

### ¿Esto funciona con archivos DOCX cifrados?

Absolutamente. Solo agrega `Password = "yourPassword"` a `LoadOptions` antes de crear el `Document`. El callback de advertencia seguirá activándose para problemas de fuentes.

### ¿En qué se diferencia esto de usar `DocumentBuilder`?

`DocumentBuilder` sirve para *crear* o *modificar* un documento después de haberlo cargado. **Configurar opciones de carga de documentos** influye en la etapa de *análisis inicial*, donde se toman las decisiones de sustitución de fuentes.

## Visión general visual

![Diagrama que muestra el flujo de configuración de opciones de carga de documentos](https://example.com/images/load-options-flow.png "Diagrama que muestra el flujo de configuración de opciones de carga de documentos")

*La imagen ilustra el flujo: callback → LoadOptions → constructor Document → manejo de advertencias.*

## Conclusión

Ahora sabes cómo **configurar opciones de carga de documentos** en C# para capturar advertencias de sustitución de fuentes, inyectar carpetas de fuentes personalizadas y mantener el control total sobre el proceso de carga. Este patrón te brinda la confianza de que cada fuente faltante será reportada, permitiéndote mantener la fidelidad del documento en cualquier entorno.

¿Próximos pasos? Prueba cambiar el registro en consola por un sistema de telemetría más robusto, o combina este enfoque con `DocumentBuilder` para reemplazar automáticamente las fuentes faltantes por una predeterminada corporativa. También podrías explorar otros valores de `WarningType` como `DocumentStructure` para obtener una visión aún más profunda.

¡Feliz codificación, y que tus documentos siempre se rendericen exactamente como lo deseas!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Domina las opciones de carga de Markdown de Aspose.Words en Python para un procesamiento de documentos mejorado](/words/english/python-net/document-operations/aspose-words-markdown-load-options-python/)
- [Optimizar la carga de documentos con opciones HTML, RTF y TXT](/words/english/java/word-processing/optimizing-document-loading-options/)
- [Uso de opciones y configuraciones de documento en Aspose.Words para Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}