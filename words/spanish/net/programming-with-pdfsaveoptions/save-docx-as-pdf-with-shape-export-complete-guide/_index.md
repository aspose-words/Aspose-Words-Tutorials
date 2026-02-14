---
category: general
date: 2026-02-13
description: Guardar docx como pdf preservando las formas flotantes. Aprende cómo
  convertir Word a pdf, exportar formas y manejar casos límite en C#.
draft: false
keywords:
- save docx as pdf
- convert word to pdf
- how to export shapes
- convert word document pdf
- how to convert docx pdf
language: es
og_description: Guardar docx como pdf mientras se preservan las formas flotantes.
  Esta guía muestra cómo convertir Word a pdf, exportar formas y manejar los problemas
  comunes.
og_title: Guardar docx como pdf con Shape Export – Guía completa
tags:
- Aspose.Words
- C#
- PDF conversion
title: Guardar docx como pdf con Shape Export – Guía completa
url: /es/net/programming-with-pdfsaveoptions/save-docx-as-pdf-with-shape-export-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Guardar docx como pdf – Tutorial Full‑stack (C#)

¿Alguna vez necesitaste **guardar docx como pdf** y mantener esos diagramas flotantes exactamente iguales? No estás solo. Muchos desarrolladores se topan con un problema cuando las formas de Word desaparecen o se deforman después de la conversión. ¿La buena noticia? Con unas pocas líneas de C# puedes indicarle a la biblioteca que trate cada forma como un elemento de nivel bloque, y el resultado es una réplica fiel en PDF.

En esta guía recorreremos todo el proceso: cargar un archivo `.docx`, configurar las opciones de **convert word to pdf** para que las formas se exporten correctamente, y finalmente escribir el PDF en disco. Al final sabrás **cómo exportar formas**, comprenderás los compromisos de los diferentes modos de exportación y tendrás un ejemplo de código listo para ejecutar que puedes incorporar en cualquier proyecto .NET.

> **Lo que obtendrás:** un ejemplo completo y ejecutable, explicaciones de *por qué* cada configuración es importante, consejos para casos extremos y ideas para ampliar la solución (p. ej., manejo de imágenes, fuentes personalizadas o PDFs protegidos con contraseña).

---

## Requisitos previos

- .NET 6+ (o .NET Framework 4.7+). La API que usamos funciona en ambos.
- Aspose.Words para .NET (versión de prueba gratuita o con licencia). Instálalo vía NuGet: `Install-Package Aspose.Words`.
- Un documento Word (`input.docx`) que contiene formas flotantes (cuadros de texto, auto‑shapes, SmartArt, etc.).
- Visual Studio 2022 o cualquier IDE que prefieras.
- No se requieren otras bibliotecas de terceros.

---

## Implementación paso a paso

Debajo de cada paso verás un fragmento de código breve, una explicación en inglés sencillo y una nota sobre **cómo exportar formas** correctamente.

### ## Paso 1 – Cargar el documento fuente (guardar docx como pdf)

```csharp
// Step 1: Load the source document
// This is the starting point for any conversion – you must have a Document object.
Document doc = new Document(@"C:\MyFolder\input.docx");
```

*Por qué es importante:* La clase `Document` representa todo el archivo Word en memoria. Si omites este paso, no habrá nada que convertir y las opciones de PDF posteriores no tendrán nada sobre lo que actuar.

### ## Paso 2 – Configurar opciones de guardado PDF (cómo exportar formas)

```csharp
// Step 2: Configure PDF save options to export floating shapes as block‑level tags
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
{
    // ExportFloatingShapesAsInlineTag determines how shapes are rendered in PDF.
    // Setting it to Block ensures each shape gets its own block, preserving layout.
    ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block
};
```

**Explicación**

- `PdfSaveOptions` es una “bolsa de configuraciones” que indica a Aspose.Words cómo traducir los constructos de Word a PDF.
- La propiedad **ExportFloatingShapesAsInlineTag** tiene tres valores posibles:
  1. **Inline** – las formas se convierten en elementos en línea (a menudo aplastados dentro del texto circundante).
  2. **Block** – cada forma se coloca en su propio bloque, que es la forma más segura de mantener la apariencia original.
  3. **Auto** – la biblioteca decide automáticamente (puede no siempre elegir la mejor opción).

Elegir **Block** es el enfoque recomendado cuando *necesitas exportar formas* exactamente como aparecen en el documento original. Previene el problema de “la forma desaparece” que muchos encuentran al simplemente llamar a `doc.Save("out.pdf")`.

### ## Paso 3 – Guardar el documento como PDF (convert word to pdf)

```csharp
// Step 3: Save the document as PDF using the configured options
doc.Save(@"C:\MyFolder\FloatingShapes.pdf", pdfSaveOptions);
```

*Lo que verás:* Después de ejecutar esta línea, `FloatingShapes.pdf` se encuentra en `C:\MyFolder`. Ábrelo y deberías ver cada cuadro de texto, llamada y SmartArt posicionados exactamente como en el `.docx` de origen.

---

## Ejemplo completo

A continuación se muestra el **programa completo** que puedes compilar y ejecutar como una aplicación de consola. Incluye todas las instrucciones `using` necesarias y comentarios para mayor claridad.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the DOCX file you want to convert.
        // Replace the path with your own file location.
        Document doc = new Document(@"C:\MyFolder\input.docx");

        // 2️⃣ Set up PDF options – this is where we tell Aspose.Words
        //    how to handle floating shapes.
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            // ExportFloatingShapesAsInlineTag = Block makes each shape a separate block.
            ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block,

            // Optional: preserve the original page size.
            PageMode = PdfPageMode.UseOutlines,

            // Optional: embed fonts to avoid missing‑glyph issues.
            EmbedFullFonts = true
        };

        // 3️⃣ Write the PDF to disk.
        string outPath = @"C:\MyFolder\FloatingShapes.pdf";
        doc.Save(outPath, pdfOptions);

        Console.WriteLine($"Successfully saved DOCX as PDF: {outPath}");
    }
}
```

**Salida esperada**

```
Successfully saved DOCX as PDF: C:\MyFolder\FloatingShapes.pdf
```

Abre el PDF resultante y verifica que todas las formas mantengan sus posiciones originales. Si alguna forma aún se ve incorrecta, verifica que realmente sea una forma *flotante* (en lugar de una imagen en línea) en Word.

---

## Preguntas frecuentes y casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Puedo exportar formas como inline en lugar de block?** | Sí – establece `ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Inline`. Esto puede ser útil para diseños simples, pero espera un flujo de texto más estrecho y posible superposición. |
| **¿Qué pasa si mi documento contiene imágenes dentro de formas?** | La misma opción funciona; Aspose.Words rasteriza la forma junto con su imagen. Para la mayor fidelidad, también habilita `PdfSaveOptions.JpegQuality` si necesitas mejor compresión de imágenes. |
| **¿Esto funciona con archivos DOCX protegidos con contraseña?** | Carga el documento con un objeto `LoadOptions` que proporcione la contraseña, luego continúa normalmente. |
| **¿Puedo convertir varios archivos DOCX en lote?** | Envuelve la lógica de tres pasos en un bucle `foreach` sobre una lista de archivos. Recuerda reutilizar `PdfSaveOptions` para mejorar el rendimiento. |
| **¿El PDF es compatible con lectores antiguos (Acrobat 7)?** | Por defecto Aspose.Words crea archivos PDF 1.7. Configura `pdfOptions.Compliance = PdfCompliance.PdfA1b` para PDFs de grado archivístico que funcionen en lectores legados. |

---

## Consejos profesionales y errores comunes

- **Consejo profesional:** Si notas ligeros desplazamientos verticales después de la conversión, intenta establecer `pdfOptions.UsePdfDocumentStructure = true`. Esto obliga al motor PDF a respetar la jerarquía de diseño de Word.
- **Cuidado con:** documentos que combinan formas flotantes con tablas ancladas. En algunos casos, la exportación en bloque puede mover una tabla a una nueva página; puedes mitigar esto ajustando `pdfOptions.PageSetup` antes de guardar.
- **Nota de rendimiento:** Reutilizar una única instancia de `PdfSaveOptions` para muchos archivos reduce la presión del GC y acelera las conversiones por lotes.

---

## Referencia visual

A continuación se muestra una captura de pantalla esquemática (marcador de posición) que muestra el antes/después de un documento con un cuadro de texto flotante.

![ejemplo de guardar docx como pdf con formas flotantes](image-placeholder.png "ejemplo de guardar docx como pdf con formas flotantes")

*La imagen ilustra cómo la forma permanece exactamente donde estaba en el archivo Word original después de la conversión.*

---

## Conclusión

Hemos cubierto **cómo guardar docx como pdf** manteniendo cada forma flotante intacta, explorado las configuraciones de **convert word to pdf** que importan, y respondido las preguntas más comunes sobre “**cómo exportar formas**”. El ejemplo de código completo está listo para incorporarse en cualquier proyecto C#, y los ajustes opcionales te brindan flexibilidad para escenarios reales como procesamiento por lotes o cumplimiento PDF/A.

### Próximos pasos

- Prueba **convert word document pdf** con diferentes niveles de cumplimiento (`PdfCompliance.PdfA2b`, `PdfCompliance.PdfUa`) para cumplir con requisitos regulatorios.
- Experimenta con **how to convert docx pdf** para archivos protegidos con contraseña—agrega `LoadOptions` con una contraseña y `PdfSaveOptions` con `EncryptionDetails`.
- Explora otros formatos de salida (p. ej., XPS, HTML) usando el mismo objeto `Document`; el único cambio es el argumento de formato del método `Save`.

¿Tienes más preguntas? Deja un comentario, ¡y feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}