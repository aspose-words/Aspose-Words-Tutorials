---
category: general
date: 2026-06-08
description: Aprende a usar LoadOptions en Aspose.Words para detectar fuentes faltantes
  durante la importación de documentos. Guía paso a paso con código, explicaciones
  y buenas prácticas.
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: es
og_description: Cómo usar LoadOptions en Aspose.Words y detectar fuentes faltantes
  al cargar un documento. Guía completa con código y consejos prácticos.
og_title: Cómo usar LoadOptions para detectar fuentes faltantes
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: Cómo usar LoadOptions para detectar fuentes faltantes
url: /es/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo usar LoadOptions para detectar fuentes faltantes

¿Alguna vez te has preguntado **cómo usar LoadOptions** al cargar un documento Word con Aspose.Words? En este tutorial te mostraremos exactamente **cómo usar LoadOptions** para **detectar fuentes faltantes** y manejarlas de forma elegante. Ya sea que estés construyendo un servicio de conversión de documentos o un motor de informes, las fuentes faltantes pueden causar sorpresas en el diseño, por lo que detectarlas temprano es imprescindible.

Recorreremos cada paso—desde conectar una devolución de llamada de advertencia hasta interpretar los resultados—para que termines con un ejemplo completo en C# que puedes insertar en cualquier proyecto .NET. Sin documentación externa, solo una solución autocontenida. Al final sabrás por qué existe el sistema de advertencias, cómo habilitarlo y qué hacer cuando se dispara la devolución de llamada.

## Prerrequisitos

Antes de sumergirnos, asegúrate de tener:

- **Aspose.Words for .NET** (cualquier versión reciente; la API que usamos es estable desde 2022).
- Un entorno de desarrollo .NET (Visual Studio, Rider o VS Code con la extensión C#).
- Un archivo Word de ejemplo (`input.docx`) que haga referencia a una fuente que *no* tienes instalada en la máquina.

Eso es todo—no se requieren paquetes NuGet adicionales más allá de Aspose.Words.

## Cómo usar LoadOptions con Aspose.Words

La clase **LoadOptions** es la puerta de entrada para personalizar la forma en que se lee un documento. Al conectar una devolución de llamada de advertencia, puedes **detectar fuentes faltantes** en el momento en que Aspose.Words analiza el archivo. Veamos los detalles.

### Paso 1: Crear un manejador de advertencias

Aspose.Words utiliza la interfaz `IWarningCallback` para notificarte sobre problemas no críticos, como la sustitución de fuentes. Implementa la interfaz y decide qué hacer cuando llega una advertencia.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**Por qué es importante:**  
Sin una devolución de llamada, Aspose.Words sustituye silenciosamente las fuentes faltantes por una predeterminada (usualmente Arial). Capturando la advertencia `FontSubstitution` puedes registrar el problema, alertar al usuario o incluso reemplazar la fuente faltante con una alternativa personalizada.

### Paso 2: Adjuntar el manejador a LoadOptions

Ahora creamos una instancia de `LoadOptions` y le indicamos que use nuestro `FontWarningHandler`. Aquí es donde **cómo usar LoadOptions** realmente brilla.

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**Por qué es importante:**  
`LoadOptions` es un punto único para muchas configuraciones de importación (codificación, contraseña, etc.). Al establecer `WarningCallback`, habilitas un mecanismo ligero y basado en eventos que funciona para cualquier documento que cargues con estas opciones.

### Paso 3: Cargar el documento usando las opciones configuradas

Finalmente, pasamos el `LoadOptions` al constructor de `Document`. Si el archivo de origen hace referencia a una fuente que no está instalada, Aspose.Words disparará la advertencia y tu manejador imprimirá un mensaje.

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Lo que verás:**  
Suponiendo que `input.docx` usa una fuente llamada *“MyCustomFont”* que no está en la máquina, la salida en la consola será similar a:

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

Si todas las fuentes están presentes, la devolución de llamada permanece silenciosa—sin salida, sin impacto en el rendimiento.

## Detectar fuentes faltantes con una devolución de llamada de advertencia (Palabra clave secundaria en acción)

La frase **detect missing fonts** aparece naturalmente en el encabezado anterior, reforzando la palabra clave secundaria. Exploremos algunas variaciones que podrías encontrar en proyectos reales.

### Múltiples documentos en un bucle

A menudo procesas un lote de archivos. La misma instancia de `LoadOptions` puede reutilizarse, pero recuerda que el `WarningCallback` persiste entre cargas. Si necesitas aislamiento por documento, crea un nuevo `LoadOptions` en cada iteración.

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### Lógica personalizada de sustitución de fuentes

En lugar de solo registrar, podrías querer sustituir una fuente faltante específica por una alternativa aprobada por la empresa. Extiende el manejador:

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

Ahora no solo **detect missing fonts**, también decides cómo reemplazarlas.

### Silenciar advertencias no deseadas

Si solo te interesan los problemas de fuentes y deseas suprimir todo lo demás, filtra por `WarningType` como se muestra. Por el contrario, para registrar *todas* las advertencias, elimina la condición `if` y muestra `info.WarningType` junto con `info.Description`.

## Ejemplo completo y ejecutable

Juntando todo, aquí tienes un programa completo que puedes compilar y ejecutar. Reemplaza `"YOUR_DIRECTORY/input.docx"` con la ruta a tu archivo de prueba.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Salida esperada en la consola (cuando falta una fuente):**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Si no faltan fuentes, simplemente verás:

```
Document loaded successfully.
```

## Errores comunes y consejos profesionales

- **Error:** Olvidar establecer `WarningCallback`. La API seguirá sustituyendo fuentes, pero nunca sabrás que ocurrió.  
  **Consejo profesional:** Siempre adjunta un manejador cuando necesites fidelidad tipográfica; prácticamente no tiene costo.

- **Error:**


## ¿Qué deberías aprender a continuación?


Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}