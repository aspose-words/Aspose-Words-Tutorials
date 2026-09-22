---
category: general
date: 2026-02-18
description: Crear markdown a partir de un documento con pasos fáciles para exportar
  el documento a markdown y guardar imágenes en una subcarpeta. Aprende cómo guardar
  el documento como markdown en C#.
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: es
og_description: Crea markdown a partir de un documento en C# y aprende cómo exportar
  el documento a markdown mientras guardas las imágenes en una subcarpeta. Sigue la
  guía paso a paso.
og_title: Crear markdown a partir del documento – Exportar y guardar imágenes
tags:
- C#
- Aspose.Words
- Markdown export
title: Crear markdown a partir del documento – Exportar y guardar imágenes
url: /es/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear markdown a partir de un documento – Exportar y guardar imágenes

¿Alguna vez necesitaste **crear markdown a partir de un documento** pero no estabas seguro de cómo mantener ordenadas las imágenes incrustadas? No estás solo. En muchos proyectos generamos informes, manuales o borradores de blogs de forma programática, y lo último que queremos es un caos de archivos de imagen dispersos por la carpeta de salida.  

En este tutorial recorreremos una solución completa, lista‑para‑ejecutar, que **exporta el documento a markdown**, almacena cada imagen en una sub‑carpeta dedicada *md‑resources*, y finalmente **guarda el documento como markdown** usando la API Aspose.Words for .NET. Al final tendrás un único método que puedes incorporar a cualquier base de código C#, además de varios consejos para manejar casos límite.

> **Vista rápida:**  
> • Configura `MarkdownSaveOptions`  
> • Proporciona un `IResourceSavingCallback` que redirige las imágenes a una subcarpeta  
> • Llama a `Document.Save` con las opciones configuradas  

Si tienes curiosidad de por qué elegimos un callback en lugar de un post‑procesamiento, sigue leyendo – la razón se explica paso a paso.

---

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7+).  
- Aspose.Words for .NET (paquete NuGet `Aspose.Words`)  
- Un objeto `Document` de origen (puede ser .docx, .pdf, .rtf, etc.)  

No se requieren bibliotecas adicionales; la API de callbacks está integrada en Aspose.Words.

---

## Paso 1: Crear markdown a partir de un documento – configurar opciones de guardado

Lo primero que hacemos es instanciar `MarkdownSaveOptions`. Este objeto indica a Aspose.Words cómo debe comportarse la conversión, como qué variante de Markdown usar, si debe incrustar imágenes como Base64 y dónde colocar los archivos generados.

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **Por qué es importante:**  
> Sin crear explícitamente `MarkdownSaveOptions`, la biblioteca recurre a la configuración predeterminada que incrusta las imágenes directamente en el archivo Markdown como cadenas Base64. Eso hace que el archivo sea enorme y anula el propósito de tener una carpeta *images* limpia.

---

## Paso 2: Exportar documento a markdown y definir el manejo de recursos

Ahora indicamos al guardador **dónde** colocar cada imagen. La interfaz `IResourceSavingCallback` nos brinda un punto de enganche que se dispara para cada recurso (imagen, SVG, etc.) descubierto durante la exportación. Dentro del callback, nosotros:

1. Asegurarnos de que la carpeta de destino exista (`md-resources/`).  
2. Establecer `OutputFileName` al folder más el nombre original del recurso.  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **Pregunta común:** *¿Qué pasa si quiero incrustar imágenes en lugar de guardarlas?*  
> Simplemente omite el callback o establece `args.OutputFileName = null;` – el guardador incrustará la imagen como una cadena Base64 automáticamente.

> **Caso límite:** Algunos documentos antiguos contienen nombres de imagen duplicados. El callback anterior sobrescribirá el archivo anterior. Para evitarlo, podrías añadir un GUID:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## Paso 3: Guardar documento como markdown y verificar imágenes guardadas

Con las opciones totalmente configuradas, la llamada final es una única línea que escribe el archivo Markdown y las imágenes asociadas en el disco.

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

Si todo va bien verás:

- `MyReport.md` – la representación Markdown de tu documento fuente.  
- `md-resources/` – una carpeta junto al archivo .md que contiene cada imagen extraída (p. ej., `image001.png`, `image002.jpg`).  

**Fragmento de Markdown de ejemplo** (generado automáticamente por Aspose.Words):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **Consejo profesional:** Abre el archivo `.md` generado en VS Code o cualquier visor de Markdown; las imágenes deberían mostrarse instantáneamente porque las rutas relativas coinciden con la estructura de carpetas.

---

## Ejemplo completo y ejecutable

A continuación hay un programa de consola autónomo que puedes pegar en un nuevo proyecto .NET y ejecutar. Crea un documento Word sencillo, añade una imagen y luego **crea markdown a partir de un documento** mientras almacena la imagen en una subcarpeta.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**Lo que deberías ver** después de ejecutar:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

Abre `ExportedDoc.md` – la referencia de la imagen apuntará a `md-resources/sample-image.png`, y la imagen se mostrará correctamente en cualquier visor de Markdown.

---

## Variaciones frecuentemente solicitadas

| Escenario | Cómo adaptar el código |
|----------|----------------------|
| **Omitir exportación de imágenes** (incrustar como Base64) | Omit `ResourceSavingCallback` entirely, or set `args.OutputFileName = null;` inside the callback. |
| **Cambiar formato de imagen** (p. ej., todas PNG) | Inside the callback, modify `args.ResourceFileName` and optionally convert the stream before writing. |
| **Nombre de carpeta personalizado** | Replace `"md-resources/"` with any relative or absolute path you prefer. |
| **Múltiples documentos en lote** | Loop over a collection of `Document` objects, reusing the same `MarkdownSaveOptions` instance (just ensure the folder is cleared or uniquely named per run). |

---

## Conclusión

Acabamos de mostrarte **cómo crear markdown a partir de un documento**, **exportar el documento a markdown**, y **guardar imágenes en una subcarpeta** usando un enfoque limpio basado en callbacks. Los puntos clave son:

- Usa `MarkdownSaveOptions` para obtener un control granular sobre la exportación.  
- Implementa `IResourceSavingCallback` para dirigir las imágenes a una carpeta dedicada, manteniendo tu Markdown ordenado.  
- El mismo patrón funciona para otros tipos de recursos (SVG, audio) – solo inspecciona `args.ResourceType`.  

A continuación, podrías explorar **guardar el documento como markdown** con estilos de encabezado personalizados, o integrar esta rutina en una API Web ASP.NET que devuelva un ZIP con el archivo `.md` y sus recursos. De cualquier forma, los bloques de construcción ahora están en tu caja de herramientas.

¿Tienes preguntas, o encontraste un caso límite que no cubrimos? Deja un comentario abajo, ¡y feliz codificación!

---

![ejemplo de crear markdown a partir de un documento](placeholder.png "ejemplo de crear markdown a partir de un documento")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}