---
category: general
date: 2026-06-30
description: Aprende a cargar fuentes en .NET usando LoadOptions, configurar la tipografía,
  habilitar fuentes personalizadas y detectar fuentes faltantes mediante callbacks
  de advertencia.
draft: false
keywords:
- how to load fonts
- set font settings
- how to handle warnings
- enable custom fonts
- detect missing fonts
language: es
og_description: ¿Cómo cargar fuentes en .NET? Esta guía le muestra cómo establecer
  la configuración de fuentes, habilitar fuentes personalizadas y detectar fuentes
  faltantes mediante callbacks de advertencia.
og_title: Cómo cargar fuentes en .NET – Configurar ajustes de fuentes y advertencias
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  headline: How to Load Fonts in .NET – Set Font Settings & Warnings
  type: TechArticle
- description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  name: How to Load Fonts in .NET – Set Font Settings & Warnings
  steps:
  - name: Creating `LoadOptions` and configuring **set font settings**.
    text: Creating `LoadOptions` and configuring **set font settings**.
  - name: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
    text: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
  - name: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
    text: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
  - name: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
    text: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
  - name: Saving the document, confirming that the fallback
    text: Saving the document, confirming that the fallback
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Cómo cargar fuentes en .NET – Configurar ajustes de fuentes y advertencias
url: /es/net/working-with-fonts/how-to-load-fonts-in-net-set-font-settings-warnings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo cargar fuentes en .NET – Configurar ajustes de fuentes y advertencias

¿Alguna vez te has preguntado **cómo cargar fuentes** en un documento .NET sin volverte loco? No eres el único. Glifos faltantes, sustituciones silenciosas y advertencias crípticas pueden convertir un simple generador de informes en una pesadilla.  

En este tutorial recorreremos un ejemplo completo, listo para ejecutar, que muestra **cómo cargar fuentes**, configurar **ajustes de fuentes**, **habilitar fuentes personalizadas** y **detectar fuentes faltantes** manejando advertencias. Al final tendrás un patrón sólido que podrás incorporar en cualquier proyecto que use Aspose.Words o una biblioteca similar.

> **Vista rápida:** crearemos un objeto `LoadOptions`, adjuntaremos una devolución de llamada de advertencia y cargaremos un DOCX que deliberadamente hace referencia a una tipografía faltante. La consola imprimirá un mensaje claro cada vez que el motor sustituya una fuente.

## Qué necesitarás

- .NET 6.0 o posterior (el código también funciona en .NET Framework 4.6+)
- Aspose.Words para .NET (el paquete NuGet de prueba gratuita está bien)
- Un archivo DOCX que haga referencia a una fuente que *no* tengas instalada (por ejemplo, `MissingFont.docx`)

Eso es todo: sin servicios extra, sin archivos de configuración obscuros. Si tienes esos tres elementos, estás listo para seguir.

![how to load fonts example diagram](https://example.com/how-to-load-fonts-diagram.png)

*Texto alternativo de la imagen: diagrama de ejemplo de cómo cargar fuentes*

## Paso 1: Crear Load Options y habilitar la configuración de fuentes personalizadas  

Lo primero que haces cuando quieres **configurar ajustes de fuentes** es instanciar un objeto `LoadOptions`. Dentro de él colocas una instancia de `FontSettings` que apunta a una carpeta que contiene los archivos .ttf o .otf personalizados que puedas necesitar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Step 1: Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // Point to a folder that holds extra fonts (optional but useful)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

**Por qué es importante:** Por defecto Aspose.Words solo busca fuentes instaladas en el sistema. Si tu documento usa una fuente corporativa que está en un recurso compartido de red, debes indicarle a la biblioteca dónde encontrarla. Esa es la esencia de **habilitar fuentes personalizadas**.

## Paso 2: Adjuntar un manejador de advertencias para detectar fuentes faltantes  

Si omites el manejo de advertencias, los glifos faltantes se sustituyen silenciosamente por una fuente de respaldo—a menudo Times New Roman. Eso puede romper la identidad de marca o incluso causar desplazamientos de diseño. Para **cómo manejar advertencias**, adjunta una devolución de llamada que inspeccione `WarningType.FontSubstitution`.

```csharp
        // Step 2: Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution detected: {args.Description}");
        };
```

**Consejo profesional:** El `WarningCallback` se dispara para *cualquier* advertencia, no solo para fuentes faltantes. Filtrar por `WarningType.FontSubstitution` mantiene la salida limpia y responde directamente a la pregunta **detectar fuentes faltantes**.

## Paso 3: Cargar el documento usando las opciones configuradas  

Ahora que hemos preparado las opciones, finalmente podemos **cargar fuentes** en el documento. El constructor `Document` acepta la ruta al archivo más el `LoadOptions` que acabamos de crear.

```csharp
        // Step 3: Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);
```

Si el archivo fuente hace referencia a una fuente que no está en la carpeta del sistema *o* en la carpeta personalizada que configuramos antes, la devolución de llamada de advertencia del Paso 2 imprimirá una línea útil en la consola.

## Paso 4: Verificar el conjunto de fuentes cargado (Opcional pero revelador)  

A veces quieres confirmar qué fuentes se resolvieron realmente. Aspose.Words expone el `FontSettings` que pasaste, de modo que puedes enumerar las fuentes resueltas.

```csharp
        // Step 4: (Optional) List all font sources that were used
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");
```

Ejecutar este fragmento después de cargar imprimirá algo como:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was substituted with 'Arial'.
Loaded font sources:
- FolderFontSource
- SystemFontSource
```

La línea de advertencia confirma que **detectamos fuentes faltantes** con éxito, mientras que la lista muestra que se consultaron tanto las carpetas del sistema como la personalizada.

## Paso 5: Guardar o renderizar el documento  

Una vez que el documento está cargado y has verificado las fuentes, puedes continuar con cualquier procesamiento—guardar como PDF, renderizar a imágenes o manipular el DOM. Para completitud, aquí tienes una línea única que guarda el resultado como PDF:

```csharp
        // Step 5: Save the document as PDF (fonts now embedded where possible)
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ Document saved as PDF.");
    }
}
```

Cuando se abre el PDF, cualquier glifo faltante habrá sido reemplazado por la fuente de respaldo que viste en la salida de la consola. Si añadiste la fuente faltante a `C:\MyCustomFonts`, vuelve a ejecutar el programa y la advertencia desaparece—prueba de que **habilitar fuentes personalizadas** realmente funciona.

---

## Ejemplo completo funcional

Copia todo el bloque a continuación en un nuevo proyecto de consola, agrega el paquete NuGet de Aspose.Words y pulsa **Run**. Ajusta las rutas de archivo para que coincidan con tu entorno.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };
        // Point to a folder with extra fonts (if you have any)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);

        // 2️⃣ Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        };

        // 3️⃣ Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);

        // 4️⃣ (Optional) List loaded font sources for debugging
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");

        // 5️⃣ Save as PDF – you’ll see the same warnings if fonts were missing
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ PDF saved successfully.");
    }
}
```

### Salida esperada

```
⚠️ Font substitution: Font 'Papyrus' was substituted with 'Arial'.

Loaded font sources:
- FolderFontSource
- SystemFontSource

✅ PDF saved successfully.
```

Si colocas el archivo `Papyrus.ttf` faltante en `C:\MyCustomFonts` y ejecutas el programa nuevamente, la línea de advertencia desaparece, confirmando que la carpeta personalizada fue consultada correctamente.

---

## Preguntas frecuentes y trampas comunes

| Pregunta | Respuesta |
|----------|-----------|
| **¿Qué pasa si no tengo una devolución de llamada de advertencia?** | El documento aún se carga, pero no sabrás cuándo ocurrió una sustitución. Añadir la devolución de llamada es la forma más sencilla de **cómo manejar advertencias**. |
| **¿Puedo cargar fuentes desde un archivo zip?** | Sí—usa `new FolderFontSource(zipPath, true)` o implementa un `IFontSource` personalizado. Esto sigue estando bajo **habilitar fuentes personalizadas**. |
| **¿Necesito incrustar fuentes en el PDF?** | Configura `doc.SaveOptions.PdfSaveOptions.EmbedFullFonts = true;` antes de guardar. Incrustar garantiza que el PDF se vea igual en cualquier máquina. |
| **¿Qué ocurre si el documento usa una fuente con licencia que no se puede redistribuir?** | Aún puedes *detectar* la fuente faltante mediante advertencias, pero no deberías incrustarla a menos que tengas los derechos. Considera sustituirla por una fuente de código abierto similar. |

---

## Recapitulación

Hemos cubierto **cómo cargar fuentes** en .NET mediante:

1. Crear `LoadOptions` y configurar **ajustes de fuentes**.  
2. **Habilitar fuentes personalizadas** apuntando a una carpeta con tipografías adicionales.  
3. **Cómo manejar advertencias** con un `WarningCallback` que imprime mensajes de sustitución de fuentes.  
4. **Detectar fuentes faltantes** filtrando `WarningType.FontSubstitution`.  
5. Guardar el documento, confirmando que la sustitución de respaldo funciona.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Configurar carpetas de fuentes del sistema y carpeta personalizada](/words/english/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/)
- [Cómo detectar fuentes en Aspose.Words – Manejar advertencias y configuraciones](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Cómo capturar fuentes en Aspose.Words – Guía completa](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}