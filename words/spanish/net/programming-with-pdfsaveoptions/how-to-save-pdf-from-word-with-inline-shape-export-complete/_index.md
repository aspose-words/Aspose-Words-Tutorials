---
category: general
date: 2026-06-02
description: Cómo guardar PDF a partir de un DOCX usando Aspose.Words, exportar formas
  como etiquetas span en línea y convertir Word a PDF en solo unos pocos pasos.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: es
og_description: Cómo guardar PDF a partir de un documento Word usando Aspose.Words,
  exportando formas flotantes como etiquetas span en línea para obtener un resultado
  limpio al convertir Word a PDF.
og_title: Cómo guardar PDF desde Word – Tutorial de exportación de forma incrustada
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: Cómo guardar PDF desde Word con exportación de forma incrustada – Guía completa
url: /es/net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo guardar PDF desde Word con exportación de forma en línea – Guía completa

¿Alguna vez te has preguntado **cómo guardar PDF** desde un archivo Word manteniendo cada forma flotante bien integrada en el flujo? No eres el único. En muchas aplicaciones empresariales necesitamos *convertir Word a PDF* sin terminar con imágenes descolocadas u objetos de dibujo sueltos. ¿La buena noticia? Aspose.Words lo hace sin complicaciones, e incluso puedes indicarle a la biblioteca que **exporte las formas como etiquetas `<span>` en línea** para que el PDF se vea exactamente como el DOCX original.

En este tutorial recorreremos todo el proceso: cargar un DOCX, ajustar las `PdfSaveOptions` y, finalmente, guardar un PDF limpio. Al final sabrás **cómo guardar PDF**, **guardar docx como pdf**, e incluso **cómo exportar formas** usando *etiquetas span en línea*.

## Qué necesitarás

- **Aspose.Words for .NET** (última versión, 24.x al momento de escribir).
- **.NET 6.0** o posterior – el código también funciona en .NET Framework 4.7.2, pero .NET 6 es el punto óptimo.
- Un documento Word sencillo que contenga al menos una forma flotante (imagen, cuadro de texto o dibujo).
- Cualquier IDE que prefieras (Visual Studio, Rider, VS Code + extensión C#).

¡Eso es todo—sin paquetes NuGet extra, sin COM interop complicado. ¿Listo? Vamos a sumergirnos.

## Paso 1: Configura el proyecto y agrega Aspose.Words

Primero, crea una aplicación de consola (o integra el código en tu servicio existente).

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **Consejo profesional:** Si usas Visual Studio, puedes agregar el paquete mediante la UI del Administrador de paquetes NuGet—simplemente busca *Aspose.Words*.

## Paso 2: Carga el documento de origen

Ahora que la biblioteca está referenciada, podemos cargar el DOCX. Esta es la primera acción concreta de la parte **cómo guardar pdf**—obtener el origen en memoria.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**Por qué es importante:** Cargar el archivo valida que la ruta sea correcta y que Aspose pueda analizar la estructura de Word. Si el archivo contiene formas flotantes, formarán parte del árbol de nodos del objeto `Document`.

## Paso 3: Configura las opciones de guardado PDF – Exportar formas como etiquetas en línea

Este es el corazón de **cómo exportar formas**. Por defecto Aspose.Words renderiza las formas flotantes como objetos separados en el PDF, lo que puede desplazar el diseño. Establecer `ExportFloatingShapesAsInlineTag` a `true` indica al motor que envuelva cada forma en una etiqueta `<span>` en línea, preservando el flujo.

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**¿Por qué habilitar esta opción?** Imagina un contrato con un cuadro de firma que flota sobre el texto. Al convertirlo a PDF sin esta configuración, el cuadro podría aparecer en otra página. Las etiquetas `<span>` en línea mantienen la forma anclada al párrafo circundante, produciendo una réplica visual fiel.

## Paso 4: Guarda el documento como PDF

Finalmente, llamamos a `doc.Save` con las opciones que acabamos de crear. Este es el momento en que realmente **guardas docx como pdf**.

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

Ejecuta el programa (`dotnet run`) y revisa el `output.pdf`. Deberías ver tus formas flotantes renderizadas en línea, tal como aparecían en Word.

## Paso 5: Verifica el resultado – Lista de verificación rápida

1. **Todo el texto está presente** – sin párrafos faltantes.  
2. **Las formas flotantes aparecen donde deben** – ahora forman parte del flujo de texto.  
3. **El tamaño del PDF es razonable** – exportar como etiquetas en línea suele reducir el inflado del archivo comparado con flujos de imágenes separados.  

Si algo se ve extraño, verifica que el DOCX de origen realmente use formas *flotantes* (clic derecho → Diseño → “En línea con el texto” vs “Cuadrado/Detrás del texto”). Cambiar una forma a “En línea” antes de la conversión también funciona, pero la opción de etiqueta en línea te brinda control sin editar el archivo original.

## Casos límite y preguntas frecuentes

### ¿Qué pasa si mi documento contiene **SmartArt** o **Gráficos**?

SmartArt y los gráficos se tratan como objetos de dibujo. La bandera `ExportFloatingShapesAsInlineTag` seguirá envolviéndolos en etiquetas `<span>`, pero los gráficos complejos pueden perder algo de fidelidad. En esos casos, considera exportar el gráfico como imagen primero (`Chart.ToImage()`) e insertarlo en línea.

### ¿Puedo **preservar hipervínculos** y **marcadores**?

Claro. esos elementos no se ven afectados por la configuración `ExportFloatingShapesAsInlineTag`. Aspose.Words conserva automáticamente toda la información de hipervínculos y marcadores.

### ¿Cómo cambio la **compresión del PDF** o **incorporo fuentes**?

`PdfSaveOptions` ofrece muchas propiedades adicionales:

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

Siéntete libre de ajustar esas configuraciones según tus requisitos posteriores (p. ej., cumplimiento PDF/A).

## Ejemplo completo (listo para copiar y pegar)

A continuación tienes el programa completo que puedes copiar en `Program.cs`. Reemplaza `YOUR_DIRECTORY` con una ruta de carpeta real.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**Salida esperada en la consola:**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

Abre `output.pdf`—verás el diseño original, con cada forma flotante colocada cómodamente dentro del flujo de texto.

## Conclusión

Hemos cubierto **cómo guardar PDF** desde un documento Word asegurando que las formas flotantes se conviertan en etiquetas `<span>` en línea. Al cargar el DOCX, configurar `PdfSaveOptions` e invocar `doc.Save`, puedes guardar docx como pdf y **convertir word a pdf** de forma fiable sin sorpresas de diseño.

¿Próximos pasos? Prueba combinar este enfoque con cumplimiento **PDF/A** para archivado, o procesa por lotes una carpeta de archivos DOCX con un simple bucle `foreach`. También podrías explorar **renderizado personalizado** (p. ej., agregar marcas de agua) aprovechando la API `DocumentVisitor` de Aspose.Words.

¿Tienes más preguntas sobre el manejo de formas, incorporación de fuentes o afinación de rendimiento? Deja un comentario abajo, ¡y feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo guardar documento como pdf con Aspose.Words para Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Convertir Word a PDF con Aspose.Words para Java](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf – Convertir DOCX a PDF en Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}