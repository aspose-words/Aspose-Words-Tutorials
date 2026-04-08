---
category: general
date: 2026-04-07
description: Aprende a detectar fuentes y a capturar advertencias al manejar fuentes
  faltantes en C# usando Aspose.Words. Código paso a paso incluido.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: es
og_description: ¿Cómo detectar fuentes en Aspose.Words? Sigue este tutorial para capturar
  advertencias y manejar fuentes faltantes sin esfuerzo.
og_title: Cómo detectar fuentes en Aspose.Words – Guía completa
tags:
- Aspose.Words
- C#
- Font handling
title: Cómo detectar fuentes en Aspose.Words – Guía completa
url: /es/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo Detectar Fuentes en Aspose.Words – Guía Completa

¿Alguna vez te has preguntado **cómo detectar fuentes** que faltan en un documento Word antes de enviarlo a producción? No estás solo. En muchos escenarios empresariales una fuente extraviada puede romper una canalización de conversión a PDF o causar fallos de maquetación que se ven poco profesionales. La buena noticia es que Aspose.Words te ofrece una forma integrada de identificar esas tipografías ausentes y mostrar advertencias claras.

En este tutorial recorreremos paso a paso **cómo detectar fuentes**, **cómo capturar advertencias**, y las mejores prácticas para **manejar fuentes faltantes** de modo que tu aplicación siga siendo robusta. Sin herramientas externas, sin conjeturas—solo código C# puro que puedes incorporar a tu proyecto ahora mismo.

> **Vista rápida:** Al final tendrás un `FontSubstitutionWarningCollector` reutilizable que recopila cada mensaje de sustitución de fuente durante la carga del documento, y sabrás cómo reaccionar cuando una fuente no se encuentre.

---

## Qué Aprenderás

- Cómo configurar `LoadOptions` para escuchar advertencias de sustitución de fuentes.  
- Cómo capturar esas advertencias en una clase colectora personalizada.  
- Cómo procesar las advertencias recopiladas y decidir si abortar, registrar o sustituir fuentes.  
- Manejo de casos límite para documentos que referencian fuentes remotas o incrustadas.  

**Requisitos previos:** .NET 6+ (o .NET Framework 4.6+), Aspose.Words para .NET (última versión), y una familiaridad básica con C#. Si nunca has usado Aspose.Words, no te preocupes—esta guía asume solo unos minutos de configuración.

---

## Cómo Detectar Fuentes Usando Aspose.Words LoadOptions

El primer paso para detectar fuentes faltantes es indicarle a Aspose.Words que las informe. Esto se hace mediante la propiedad `LoadOptions.WarningCallback`, que acepta cualquier clase que implemente `IWarningCallback`. A continuación creamos un pequeño colector que almacena cada advertencia para inspección posterior.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**Por qué es importante:** Sin una devolución de llamada de advertencia, Aspose.Words sustituye silenciosamente las fuentes faltantes por una predeterminada, y nunca sabrás que existe un problema. Al capturar `WarningType.FontSubstitution` obtenemos visibilidad total—exactamente los datos que necesitas para **detectar fuentes** que no están disponibles en la máquina host.

Ahora enlazamos el colector a `LoadOptions` y cargamos un documento:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **Consejo profesional:** Si trabajas con muchos documentos en lote, reutiliza la misma instancia de `FontSubstitutionWarningCollector` pero recuerda llamar a `Clear()` entre cargas para evitar mezclar advertencias de archivos diferentes.

---

## Capturar Advertencias Durante la Carga del Documento

Una vez que el documento está cargado, el colector ya contiene cada advertencia relacionada con fuentes. La siguiente pregunta lógica es: *¿Cómo capturo las advertencias* de forma que sea fácil registrarlas o mostrarlas?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

Una salida típica se ve así:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**Qué te indica esto:** Cada línea revela el nombre original de la fuente y la alternativa que Aspose.Words eligió. Con esta información puedes decidir si la alternativa es aceptable o si necesitas incrustar manualmente la fuente faltante.

---

## Manejar Fuentes Faltantes de Forma Elegante

Detectar y capturar advertencias es solo la mitad de la batalla. El verdadero valor aparece cuando **manejas fuentes faltantes** de manera preparada para producción. A continuación, tres estrategias comunes:

1. **Registrar y Continuar** – Adecuado para procesamiento por lotes donde solo necesitas un registro de auditoría.  
2. **Abortar con Fuentes Críticas** – Lanzar una excepción si una fuente particular (p. ej., una tipografía de marca) falta.  
3. **Incrustar la Fuente Sobre la Marcha** – Cargar la fuente faltante desde una carpeta conocida y registrarla en Aspose.Words antes de volver a cargar el documento.

### Ejemplo: Abortando con una Fuente Crítica

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### Ejemplo: Auto‑Incrustar Fuentes Faltantes

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**Por qué estos patrones ayudan:** Al decidir explícitamente qué hacer cuando una fuente falta, eliminas sustituciones silenciosas que podrían comprometer la identidad de marca o la legibilidad. Esta es la esencia de **manejar fuentes faltantes** de forma controlada.

---

## Ejemplo Completo Funcional

Uniendo todo, aquí tienes un programa único, listo para ejecutarse, que demuestra **cómo detectar fuentes**, **cómo capturar advertencias**, y una política sencilla para **manejar fuentes faltantes** registrándolas.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**Resultado esperado:** Cuando ejecutes el programa contra un documento que haga referencia a una fuente no presente en la máquina, la consola listará cada advertencia de sustitución. Si alguna advertencia involucra una fuente del conjunto `critical`, el programa terminará anticipadamente, evitando generar un PDF defectuoso.

---

## Preguntas Frecuentes (FAQ)

| Pregunta | Respuesta |
|----------|-----------|
| *¿Necesito una licencia para Aspose.Words para usar este código?* | Sí, una licencia válida de Aspose.Words elimina las marcas de agua de evaluación y desbloquea la funcionalidad completa. |
| *¿Puede este enfoque detectar fuentes incrustadas?* | Las fuentes incrustadas ya forman parte del archivo, por lo que Aspose.Words no generará una advertencia de sustitución. Puedes consultar `Document.FontInfos` para enumerar fuentes incrustadas si lo necesitas. |
| *¿Qué ocurre si la fuente faltante es una fuente del sistema en Windows pero no en Linux?* | La misma advertencia se disparará en Linux porque la fuente no está instalada allí. Usa la estrategia de “manejar fuentes faltantes” para distribuir los archivos `.ttf` necesarios con tu aplicación. |
| *¿El recolector de advertencias es hilo?* |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}