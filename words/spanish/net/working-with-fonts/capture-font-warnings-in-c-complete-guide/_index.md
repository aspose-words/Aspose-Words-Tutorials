---
category: general
date: 2026-03-06
description: Capture advertencias de fuentes al cargar un documento de Word en C#.
  Aprende a detectar fuentes faltantes, comprobar las fuentes del documento y gestionar
  las fuentes faltantes de manera eficiente.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: es
og_description: Captura advertencias de fuentes al cargar un documento de Word en
  C#. Este tutorial muestra cómo detectar fuentes faltantes, comprobar las fuentes
  del documento y gestionar fuentes faltantes.
og_title: Captura de advertencias de fuentes en C# – Guía completa
tags:
- Aspose.Words
- C#
- Font Management
title: Capturar advertencias de fuentes en C# – Guía completa
url: /es/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Captura de advertencias de fuentes en C# – Guía completa

¿Alguna vez necesitaste **capturar advertencias de fuentes** al procesar un documento Word? Capturar estas advertencias es esencial para **detectar fuentes faltantes** y asegurarse de que el resultado final se vea exactamente como esperas.  

En este tutorial recorreremos un ejemplo práctico, de extremo a extremo, que carga un archivo `.docx`, supervisa el proceso de carga y reporta cualquier sustitución de fuentes. Al final sabrás cómo **cargar word document** de forma segura, **comprobar fuentes del documento** y **manejar fuentes faltantes** sin errores inesperados en tiempo de ejecución.

## Lo que aprenderás

- Cómo adjuntar un recopilador de advertencias a un `Document` de Aspose.Words.  
- Qué tipos de advertencia indican una fuente faltante o sustituida.  
- Formas de registrar o reaccionar a esas advertencias en una aplicación de nivel de producción.  
- Consejos para configurar fuentes personalizadas si necesitas **manejar fuentes faltantes** de manera elegante.

> **Prerequisite:** Tienes una licencia válida de Aspose.Words for .NET (o estás usando la prueba gratuita) y un entorno de desarrollo .NET (Visual Studio, Rider o VS Code). No se requieren otras bibliotecas.

---

## Captura de advertencias de fuentes – Paso a paso

A continuación se muestra el código completo y ejecutable. Cada sección está dividida en su propio paso para que puedas copiar‑pegar, experimentar y ampliar la lógica.

![Diagrama de captura de advertencias de fuentes](image.png "Diagrama que muestra la recopilación de advertencias"){: alt="diagrama de captura de advertencias de fuentes"}

### Paso 1: Cargar el documento Word

Primero, necesitamos **cargar word document** que pueda contener fuentes no instaladas en la máquina actual. El constructor `Document` realiza el trabajo pesado, pero mantendremos la llamada aislada para que puedas cambiar a un stream o a un arreglo de bytes más adelante si lo deseas.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**Por qué es importante:** Cargar un documento sin un manejador de advertencias significa que cualquier sustitución de fuente se ignora silenciosamente. Al establecer `WarningCallback` *antes* de la carga garantizamos que veremos cada advertencia `FontSubstitution` que ocurra.

### Paso 2: Adjuntar un recopilador de advertencias

La clase `WarningInfoCollector` es una implementación incorporada de `IWarningCallback`. Simplemente almacena cada advertencia en una lista que luego podemos inspeccionar.

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Consejo profesional:** Si necesitas **manejar fuentes faltantes** de forma más agresiva (p. ej., abortar la carga o sustituir con una fuente de respaldo específica), puedes reemplazar el `Console.WriteLine` con lógica personalizada: lanzar una excepción, registrar en un archivo o incluso añadir una fuente personalizada.

### Paso 3: Verificar la salida

Ejecuta el programa desde una consola. Si tu `input.docx` usa una fuente que no está instalada, verás líneas como:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

Si no aparece ninguna salida, el documento o bien utilizó solo fuentes que ya están disponibles **o** Aspose.Words encontró una fuente coincidente en su colección de sustitución incorporada. De cualquier modo, has **comprobado fuentes del documento** con éxito.

---

## Detectar fuentes faltantes sin licencia (prueba gratuita)

Incluso si estás en la prueba de 30 días, el mecanismo de advertencias funciona exactamente igual. La única diferencia es que la prueba añade una marca de agua al resultado generado, lo que **no** afecta la recopilación de advertencias. Por lo tanto, puedes **detectar fuentes faltantes** de forma segura antes de decidir comprar una licencia completa.

---

## Manejar fuentes faltantes – Opciones avanzadas

A veces deseas proporcionar tus propios archivos de fuentes (p. ej., fuentes corporativas) para que la sustitución nunca ocurra. Aspose.Words te permite registrar carpetas de fuentes personalizadas:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

Coloca el código anterior **antes** de cargar el documento si quieres que el cargador considere esas fuentes durante la fase de análisis inicial. Esta es la forma más fiable de **manejar fuentes faltantes** sin depender de las fuentes del sistema predeterminado.

---

## Errores comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **Recopilador de advertencias adjuntado después de la carga** | El documento ya está analizado, por lo que no se registran advertencias. | Adjunta `WarningCallback` **antes** de llamar a `new Document(path)`. |
| **Solo aparecen advertencias genéricas** | Filtraste por el `WarningType` incorrecto. | Usa `WarningType.FontSubstitution` para centrarte en problemas de fuentes. |
| **No hay salida a pesar de fuentes faltantes** | Aspose.Words encontró una sustitución incorporada (p. ej., Arial). | Desactiva las sustituciones incorporadas mediante `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` |
| **Impacto de rendimiento al escanear documentos grandes** | Recopilar cada advertencia puede ser costoso. | Limita la recopilación a `FontSubstitution` únicamente, o procesa las advertencias en lotes. |

---

## Ejemplo completo y funcional (listo para copiar‑pegar)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Salida esperada en la consola** (suponiendo dos fuentes faltantes):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

Si la consola permanece silenciosa salvo por “Document loaded successfully”, has **comprobado fuentes del documento** y no se encontraron fuentes faltantes.

---

## Conclusión

Te hemos mostrado cómo **capturar advertencias de fuentes** en C# usando Aspose.Words, una forma fiable de **detectar fuentes faltantes**, **cargar word document** de forma segura, **comprobar fuentes del documento** y **manejar fuentes faltantes** mediante fuentes personalizadas.  

Con este patrón puedes integrar la validación de fuentes en cualquier canal de automatización, ya sea que estés generando PDFs, convirtiendo a HTML o simplemente archivando archivos Word.

### ¿Qué sigue?

- Explora la API **FontSettings.SubstitutionSettings** para definir tus propias reglas de sustitución.  
- Combina la recopilación de advertencias con un framework de registro (Serilog, NLog) para monitorizar en producción.  
- Usa el mismo enfoque para capturar otros tipos de advertencias, como resolución de imágenes o características no compatibles.

¿Tienes más preguntas sobre el manejo de fuentes o Aspose.Words en general? Deja un comentario o visita los foros de la comunidad de Aspose. ¡Feliz codificación y que tus documentos siempre se rendericen con las fuentes que esperas!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}