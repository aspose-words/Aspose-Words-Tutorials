---
category: general
date: 2026-03-25
description: Crear una devolución de llamada de advertencia para cargar un documento
  Word y detectar fuentes faltantes. Aprende a configurar la configuración de fuentes
  en Aspose.Words para .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: es
og_description: Crear una devolución de llamada de advertencia para cargar un documento
  Word y detectar fuentes faltantes. Esta guía muestra cómo configurar los ajustes
  de fuentes en Aspose.Words.
og_title: Crear devolución de llamada de advertencia – Cargar documento Word y detectar
  fuentes faltantes
tags:
- Aspose.Words
- C#
- Font handling
title: Crear una función de devolución de llamada de advertencia para cargar documentos
  Word – Guía completa
url: /es/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear callback de advertencia – Cargar documento Word y detectar fuentes faltantes

¿Alguna vez necesitaste **crear un callback de advertencia** al cargar un documento Word y te preguntaste por qué algunas fuentes simplemente desaparecen? No eres el único. En muchas aplicaciones empresariales, las fuentes faltantes provocan desastres de maquetación, y sin un callback adecuado es posible que nunca notes el problema.  

¿La buena noticia? Con Aspose.Words for .NET puedes **cargar un documento Word**, **detectar fuentes faltantes** y **configurar la configuración de fuentes** en unas pocas líneas de código ordenadas. En este tutorial recorreremos un ejemplo completo y ejecutable, explicaremos por qué cada parte es importante y te mostraremos cómo verificar que el callback de advertencia está cumpliendo su función.

> **Lo que obtendrás**  
> * Un programa completo en C# que carga un DOCX, informa cualquier sustitución de fuentes y te permite personalizar las rutas de búsqueda de fuentes.  
> * Comprensión de las clases `FontSettings`, `LoadOptions` y `IWarningCallback`.  
> * Consejos para manejar casos límite como fuentes incrustadas o carpetas de fuentes a nivel del sistema.

---

## Requisitos previos

- .NET 6+ (o .NET Framework 4.7.2+) con un compilador C#.  
- Paquete NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Un archivo Word de ejemplo (`input.docx`) que utilice al menos una fuente no instalada en la máquina (p. ej., *Calibri Light* en un contenedor Windows mínimo).  
- Familiaridad básica con aplicaciones de consola en C#.

No se requieren bibliotecas adicionales; todo reside dentro de Aspose.Words.

---

## Paso 1: Crear callback de advertencia para detectar fuentes faltantes

La pieza **principal** de este rompecabezas es una clase que implementa `IWarningCallback`. Aspose.Words invocará este callback cada vez que encuentre una situación que justifique una advertencia, siendo la sustitución de fuentes la más común.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Por qué es importante** – Sin un callback tendrías que revisar los registros después del hecho. Al manejar las advertencias en tiempo real puedes decidir si abortar la carga, reemplazar la fuente faltante por una alternativa o simplemente registrar el problema para revisarlo más tarde.

---

## Paso 2: Configurar FontSettings para el manejo personalizado de fuentes

Antes de cargar realmente el documento, puede que queramos indicarle a Aspose.Words dónde buscar fuentes que no estén presentes en el sistema. Ahí es donde entra `FontSettings`.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Por qué es importante** – Al apuntar a una carpeta que contenga las fuentes faltantes, a menudo evitas la sustitución por completo. Cuando eso no es posible, un valor predeterminado sensato (como *Arial*) mantiene el documento legible.

---

## Paso 3: Cargar documento Word con el callback de advertencia configurado

Ahora unimos todo: creamos `LoadOptions`, conectamos nuestras `FontSettings` y `FontWarningHandler`, y finalmente cargamos el documento.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Por qué es importante** – `LoadOptions` es el único lugar donde configuras *cómo* se lee un documento. Al proporcionar tanto la configuración de fuentes como el callback de advertencia garantizamos que cualquier fuente faltante sea buscada en los lugares correctos **y** reportada inmediatamente.

---

## Paso 4: Verificar la salida – ¿qué deberías ver?

Ejecuta el programa desde una consola. Si `input.docx` usa una fuente que no está instalada y tampoco está en `C:\SharedFonts`, verás algo como:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Si todas las fuentes están disponibles, la línea de advertencia simplemente nunca aparece. Este bucle de retroalimentación inmediato es invaluable en canalizaciones automatizadas de procesamiento de documentos donde los cambios silenciosos de fuentes podrían romper las directrices de marca.

---

## Paso 5: Trampas comunes y consejos de mejores prácticas

| Trampa | Cómo evitarla |
|--------|----------------|
| **Olvidar referenciar `Aspose.Words.Fonts`** | Asegúrate de tener `using Aspose.Words.Fonts;` al inicio; de lo contrario el compilador reclamará tipos inexistentes. |
| **La ruta de la carpeta de fuentes es incorrecta** | Verifica la ruta y establece `recursive: true` si tienes subcarpetas. Usa `Path.GetFullPath` para depurar. |
| **Múltiples callbacks de advertencia** | Aspose.Words solo respeta el último `WarningCallback` que asignas. Mantén un único manejador que delegue si necesitas lógica más compleja. |
| **Ejecutar en un servidor sin UI** | Las escrituras en consola están bien, pero para aplicaciones web quizá prefieras registrar en un archivo o sistema de monitoreo en lugar de `Console.WriteLine`. |
| **Documentos grandes generan impacto de rendimiento** | Reutiliza una única instancia de `FontSettings` en múltiples cargas; crearla repetidamente puede ser costoso. |

**Consejo profesional:** Si necesitas *recopilar* advertencias para análisis posterior, almacénalas en un `List<string>` dentro del manejador en lugar de imprimirlas directamente.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Luego puedes inspeccionar `handler.Messages` después de cargar el documento.

---

## Paso 6: Extender la solución – ¿qué pasa si necesito incrustar una fuente de respaldo?

A veces deseas que la fuente faltante se *incruste* en el PDF de salida para que los visualizadores posteriores vean la apariencia exacta. Después de cargar el documento, puedes forzar la incrustación:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Este fragmento muestra cómo el mismo enfoque de **configurar la configuración de fuentes** puede ampliarse más allá de la simple carga.

---

## Ejemplo completo ejecutable

A continuación tienes el programa completo que puedes copiar y pegar en un nuevo proyecto de aplicación de consola. Incluye todas las piezas discutidas anteriormente.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Salida esperada** (cuando hay una fuente faltante):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

Si no ocurre sustitución, solo aparecen los mensajes de éxito.

---

## Conclusión

Acabamos de **crear un callback de advertencia** que detecta de forma fiable **fuentes faltantes** mientras **cargamos un documento Word** con Aspose.Words, y mostramos cómo **configurar la configuración de fuentes** para controlar dónde busca la biblioteca las fuentes y qué alternativa usar. Al conectar `FontSettings` y `LoadOptions`, obtienes total visibilidad sobre los problemas relacionados con fuentes—no más fallos silenciosos de maquetación.

¿Próximos pasos? Prueba a sustituir `FontWarningHandler` por un registrador que escriba en una base de datos, o experimenta con **reglas de sustitución de fuentes** para mapear fuentes faltantes específicas a alternativas aprobadas por la marca. También podrías explorar **carga dinámica de fuentes** desde almacenamiento en la nube si tu aplicación se ejecuta en un entorno contenedorizado.

¿Tienes preguntas sobre algún caso límite—como manejar características OpenType o documentos DOCX cifrados? Deja un comentario abajo, ¡y feliz codificación!  

---

![Create warning callback diagram](https://example.com/images/create-warning-callback.png "Create warning callback diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}