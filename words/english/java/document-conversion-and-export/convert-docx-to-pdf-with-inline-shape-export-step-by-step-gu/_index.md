---
category: general
date: 2026-10-07
description: Learn how to convert DOCX to PDF in Java, export floating shapes as inline
  tags, and batch convert DOCX to PDF efficiently.
draft: false
images:
- /java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/og-image.png
keywords:
- how to convert docx to pdf java
- batch convert docx to pdf
- export floating shapes inline
language: en
lastmod: 2026-10-07
og_description: Learn how to convert DOCX to PDF in Java, export floating shapes as
  inline tags, and batch convert DOCX to PDF efficiently.
og_image_alt: 'Developer guide: Convert DOCX to PDF in Java with inline shape export'
og_title: How to convert DOCX to PDF in Java – shape export guide
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to convert DOCX to PDF in Java, export floating shapes as
    inline tags, and batch convert DOCX to PDF efficiently.
  headline: How to convert DOCX to PDF in Java – shape export guide
  type: TechArticle
- questions:
  - answer: Yes—load the document with `LoadOptions` that include the password, then
      proceed with the same save logic.
    question: Does this work with password‑protected DOCX files?
  - answer: Aspose.Words rasterizes vector graphics by default; to keep them vector
      you can enable `pdfOptions.setVectorRasterizationMode(VectorRasterizationMode.VectorOnly)`.
    question: What about SVG or EMF images inside the Word file?
  - answer: Links are retained automatically when you use `PdfSaveOptions`. Avoid
      disabling tags, as that can drop the logical link structure.
    question: How do I preserve hyperlinks while converting?
  - answer: Absolutely. Iterate over `Files.list(Paths.get("YOUR_DIRECTORY"))`, apply
      the same load‑configure‑save sequence to each file, and handle exceptions per
      file so one bad document doesn’t halt the whole run.
    question: Can I batch‑process a folder of DOCX files?
  - answer: Enable `pdfOptions.setMemoryOptimization(true)` and consider streaming
      the output to avoid loading the entire PDF into memory.
    question: How can I improve performance for very large documents?
  type: FAQPage
tags:
- convert docx to pdf
- Aspose.Words
- Java
- PDF conversion
- batch convert docx to pdf
title: How to convert DOCX to PDF in Java – shape export guide
url: /java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to convert DOCX to PDF in Java – shape export guide

If you’re wondering **how to convert DOCX to PDF in Java** while preserving floating images or text boxes, you’ve come to the right place. In many projects—think automated report generators or batch‑processing pipelines—preserving the exact layout of a Word document is non‑negotiable.

Below you’ll see exactly **how to export shapes** the way you want, plus a handful of tips that save you from common pitfalls. No external services, no UI wizard—just pure Java code you can drop into any Maven or Gradle project.

## Quick answers
- **What library handles the conversion?** Aspose.Words for Java.
- **Can I batch convert DOCX to PDF?** Yes—wrap the same logic in a loop over a directory.
- **Do floating shapes stay in place?** Set `setExportFloatingShapesAsInlineTag(true)` to export them as inline tags.
- **Is a license required?** A free trial works for testing; a commercial license is needed for production.
- **Which Java version is required?** JDK 8 or higher.

## How to convert DOCX to PDF in Java?

Load the source `.docx` with `new Document("input.docx")` and call `doc.save("output.pdf", pdfOptions)`—Aspose.Words handles fonts, images, tables, and complex layouts automatically. By configuring `PdfSaveOptions` you can control whether floating shapes become inline tags or remain block‑level elements, which is essential for accessibility and accurate reading order.

This two‑step pattern works for single files and scales to **batch convert DOCX to PDF** by iterating over a folder of documents.

## What you’ll learn
* Load a `.docx` file from disk.  
* Configure `PdfSaveOptions` so that floating shapes are exported as inline tags.  
* Write the resulting PDF to a folder of your choice.  
* Understand why the `setExportFloatingShapesAsInlineTag` flag matters and when you might flip it.  

## Prerequisites

| Requirement | Why it matters |
|-------------|----------------|
| **Aspose.Words for Java** (v23.12 or later) | Provides the `Document` and `PdfSaveOptions` classes used in the example. |
| **JDK 8+** | The library is compiled for Java 8 and newer; older runtimes will throw `UnsupportedClassVersionError`. |
| **A DOCX file** with at least one floating shape (image, text box, WordArt) | To see the effect of the shape‑export option, you need a document that actually contains floating objects. |

If you already have these pieces, great—let’s jump in.

## Step 1 – Load the source document  

The `Document` class is Aspose.Words' top‑level object that represents a single Word file in memory. Instantiating it reads the file, parses the OpenXML package, and builds an object model you can manipulate.

First we create a `Document` instance pointing at the `.docx` you want to convert.  

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

// Adjust the path to your environment
String inputPath = "YOUR_DIRECTORY/input.docx";

Document doc = new Document(inputPath);
```

> **Pro tip:** If you’re processing many files in a loop, reuse a single `Document` object only after you’ve called `doc.close()` (or let the garbage collector handle it). This prevents file‑handle leaks on Windows.

## Step 2 – Configure PDF save options to export shapes  

`PdfSaveOptions` is the configuration object that dictates how the conversion behaves. Setting `setExportFloatingShapesAsInlineTag(true)` forces every floating shape to be treated as an *inline* element in the PDF’s tag structure, improving accessibility and reading order.

The `PdfSaveOptions` class controls layout, font embedding, compliance levels, and many performance knobs.  

```java
import com.aspose.words.PdfSaveOptions;

PdfSaveOptions pdfOptions = new PdfSaveOptions();
// true → inline tagging (shape behaves like a character)
// false → block‑level tagging (shape sits in its own block)
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

**When would you set it to `false`?**  
If your PDF is destined for print‑only distribution and you want the shapes to retain their original positioning without affecting the logical reading order, you might prefer block‑level tagging. The default is `false`, so we explicitly enable the inline behavior for this tutorial.

## Step 3 – Save the document as a PDF  

The `save` method writes the processed document to disk using the options you supplied. It handles layout, font embedding, and tag generation behind the scenes.

The `save` method on the `Document` class writes the PDF file to the target location using the configured `PdfSaveOptions`.  

```java
String outputPath = "YOUR_DIRECTORY/shapes.pdf";
doc.save(outputPath, pdfOptions);
```

After the call finishes, you’ll find `shapes.pdf` in the specified folder. Open it in Adobe Acrobat or any PDF viewer that shows tags (usually under **File → Properties → Tags**) and you’ll see that the floating shape appears as an inline tag.

## Why this approach matters  

Aspose.Words for Java supports **50+ input and output formats** and can process a 500‑page document in under **5 seconds** on a typical server, all without requiring Microsoft Word. By exporting floating shapes as inline tags you satisfy accessibility standards such as PDF/UA, and you avoid layout drift when the PDF is viewed on different devices.

## Full, runnable example  

Putting it all together, here’s a self‑contained Java class you can compile and run. Make sure the Aspose.Words JAR is on your classpath.

```java
import com.aspose.words.*;

public class DocxToPdfWithShapes {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            String inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF options – export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → inline tagging

            // 3️⃣ Save as PDF
            String outputPath = "YOUR_DIRECTORY/shapes.pdf";
            doc.save(outputPath, pdfOptions);

            System.out.println("✅ Conversion complete! PDF saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("❌ Something went wrong: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Expected result:**  
- The PDF file contains the same textual content as the original DOCX.  
- Any floating images or text boxes are now tagged *inline*, meaning they appear in the reading order rather than as separate blocks.  
- If you open the PDF’s **Tags** panel, you’ll see an `<Figure>` element nested inside a `<Paragraph>`—exactly what `setExportFloatingShapesAsInlineTag(true)` guarantees.

## Frequently asked questions & edge cases  

**Q: Does this work with password‑protected DOCX files?**  
A: Yes—load the document with `LoadOptions` that include the password, then proceed with the same save logic.  

**Q: What about SVG or EMF images inside the Word file?**  
A: Aspose.Words rasterizes vector graphics by default; to keep them vector you can enable `pdfOptions.setVectorRasterizationMode(VectorRasterizationMode.VectorOnly)`.  

**Q: How do I preserve hyperlinks while converting?**  
A: Links are retained automatically when you use `PdfSaveOptions`. Avoid disabling tags, as that can drop the logical link structure.  

**Q: Can I batch‑process a folder of DOCX files?**  
A: Absolutely. Iterate over `Files.list(Paths.get("YOUR_DIRECTORY"))`, apply the same load‑configure‑save sequence to each file, and handle exceptions per file so one bad document doesn’t halt the whole run.  

**Q: How can I improve performance for very large documents?**  
A: Enable `pdfOptions.setMemoryOptimization(true)` and consider streaming the output to avoid loading the entire PDF into memory.

## Tips from the trenches  

* **Watch out for missing fonts.** If the source DOCX uses a custom font not installed on the server, the PDF will substitute a fallback, potentially breaking layout. Use `pdfOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)` to force embedding.  
* **Testing accessibility.** After conversion, run Acrobat’s **Accessibility Checker**. Inline tagging usually improves the score, but you may still need to add alternate text to images manually.  
* **Performance tip:** For large documents (100+ pages), enable `pdfOptions.setMemoryOptimization(true)` to reduce heap usage.

## Visual confirmation  

Below is a quick screenshot of the PDF opened in Adobe Acrobat, showing the inline‑tagged shape highlighted in the **Tags** pane.

![Convert DOCX to PDF example output](image.png)

[Convert DOCX to PDF example output](image.png)

*Alt text: convert docx to pdf example output showing inline shape tags.*

## Wrap‑up  

You now know **how to convert DOCX to PDF in Java** while controlling the way floating objects are exported. By toggling `setExportFloatingShapesAsInlineTag`, you decide whether shapes become part of the reading order or stay as independent blocks—crucial for both accessibility and visual fidelity.  

From here you can:

* **Save Word as PDF** in bulk for archiving.  
* Experiment with other `PdfSaveOptions` like `setCompliance(PdfCompliance.PDF_A_1B)` for long‑term preservation.  
* Dive deeper into **how to export shapes** by exploring the full Aspose.Words documentation or trying out the `setExportDocumentStructure(true)` flag for richer tag trees.

Give it a spin, tweak the options, and let your PDFs look exactly how you need them to. Happy coding!

---

**Last Updated:** 2026-10-07  
**Tested with:** Aspose.Words for Java 23.12  
**Author:** Aspose  






```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document doc = new Document(inputPath, loadOptions);
```

```java
pdfOptions.setRasterizeTransformedElements(false);
```

## Related Tutorials

- [Convert Docx To Pdf In Java Step By Step Guide](/words/java/document-converting/convert-docx-to-pdf-in-java-step-by-step-guide/)
- [Save Docx As Pdf With Java Complete Step By Step Guide](/words/java/document-conversion-and-export/save-docx-as-pdf-with-java-complete-step-by-step-guide/)
- [Convert DOCX to PDF in Java with Aspose.Words – Using Document Converting](/words/java/document-converting/using-document-converting/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}