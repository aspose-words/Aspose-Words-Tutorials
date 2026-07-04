---
category: general
date: 2026-06-05
description: How to save PDF from a DOCX while preserving floating shapes as inline
  tags. Learn to save docx as pdf, convert word to pdf, and export shapes correctly.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- save word pdf inline
language: en
og_description: How to save PDF from a Word document while exporting floating shapes
  as inline tags. Follow this step‑by‑step guide to save docx as pdf and convert word
  to pdf correctly.
og_title: How to Save PDF from Word with Inline Shapes – Full Tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: How to save PDF from a DOCX while preserving floating shapes as inline
    tags. Learn to save docx as pdf, convert word to pdf, and export shapes correctly.
  headline: How to Save PDF from Word with Inline Shapes – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX while preserving floating shapes as inline
    tags. Learn to save docx as pdf, convert word to pdf, and export shapes correctly.
  name: How to Save PDF from Word with Inline Shapes – Complete Guide
  steps:
  - name: Large Images
    text: 'If a floating shape contains a high‑resolution image, converting it to
      inline may cause the line height to expand dramatically. To keep the PDF tidy:'
  - name: Multiple Sections with Different Layouts
    text: 'When a document has sections with distinct page setups, you might need
      to apply the inline conversion only to a specific section:'
  - name: Converting Multiple DOCX Files in a Batch
    text: 'If you need to **convert word to pdf** for dozens of files, wrap the logic
      into a utility method:'
  - name: Expected Result
    text: Running the program should produce `inlineShapes.pdf`. Open it, and you’ll
      notice that any floating text boxes, callouts, or images now sit **inline**
      with the surrounding text, mirroring the layout you designed in Word.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF conversion
title: How to Save PDF from Word with Inline Shapes – Complete Guide
url: /java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Save PDF from Word with Inline Shapes – Complete Guide

Ever wondered **how to save PDF** from a Word file without losing the layout of floating images? You’re not the only one. In many reporting or invoicing apps, those floating shapes—think text boxes, callouts, or decorative icons—often end up misplaced when you simply click “Save As PDF.”  

Luckily, there’s a clean, programmatic way to keep those objects exactly where you expect them: configure the PDF export to turn floating shapes into `<inline>` tags. In this tutorial we’ll walk through **how to export shapes**, **save docx as pdf**, and **convert word to pdf** using a few lines of Java code. By the end, you’ll have a ready‑to‑run snippet that produces a PDF with every shape rendered inline.

## What You’ll Learn

- Load a DOCX file from disk (or any stream) with Aspose.Words for Java.  
- Enable the **save word pdf inline** option so floating objects become inline tags.  
- Save the document as a PDF using the configured `PdfSaveOptions`.  
- Tips for handling edge cases like large images or complex tables.  

No external tools, no manual fiddling with Word’s UI—just clean code you can drop into any Java project.

---

## Prerequisites

Before we dive in, make sure you have:

| Requirement | Why it matters |
|-------------|----------------|
| **Java 17+** (or any recent JDK) | Aspose.Words for Java runs on modern JDKs. |
| **Aspose.Words for Java** library (latest version) | Provides `Document`, `PdfSaveOptions`, and the `setExportFloatingShapesAsInlineTag` method. |
| A **DOCX** file that contains floating shapes (e.g., a text box). | Without shapes you won’t see the effect of the inline export. |
| An IDE or build tool (Maven/Gradle) to manage dependencies. | Makes compilation painless. |

If you’re using Maven, add the dependency:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check for the latest version -->
</dependency>
```

---

## Step 1: Load the Source Document

The first thing you need is a `Document` object that represents your Word file. Think of it as the canvas that Aspose.Words will later paint onto a PDF.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Why this matters:* Loading the file into memory gives you full access to its object model—paragraphs, runs, shapes, everything. If the path is wrong, you’ll get a `FileNotFoundException`, so double‑check that the file exists.

> **Pro tip:** If you’re pulling the DOCX from a database or a web service, you can use the `InputStream` constructor instead of a file path.

---

## Step 2: Configure PDF Save Options to Export Floating Shapes as Inline Tags

By default, Aspose.Words tries to keep floating shapes floating in the PDF, which can cause mis‑alignment when the PDF viewer interprets the layout differently. The `PdfSaveOptions` class lets us change that behavior.

```java
// Step 2: Configure PDF save options to export floating shapes as <inline> tags
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

*Why this matters:* Setting `setExportFloatingShapesAsInlineTag(true)` tells the exporter to treat each floating shape as if it were part of the surrounding paragraph. The result is a PDF where the shape moves with the text, eliminating gaps or overlapping elements.

> **Common question:** *What if I still want some shapes to stay floating?*  
> You can selectively set the `WrapType` of individual shapes in the Word document before export, or disable the inline conversion for the whole document and handle those shapes manually.

---

## Step 3: Save the Document as a PDF with the Configured Options

Now that the document is loaded and the export behavior is tuned, it’s time to write the PDF file to disk.

```java
// Step 3: Save the document as a PDF with the configured options
doc.save("YOUR_DIRECTORY/inlineShapes.pdf", pdfOptions);
```

*Why this matters:* The `save` method takes both the output path and the `PdfSaveOptions` instance, ensuring your inline‑shape setting is respected. If you omit the options, you’ll fall back to the default behavior (floating shapes remain floating).

> **Expected output:** Open `inlineShapes.pdf` in any PDF viewer. All previously floating text boxes or images should now appear **inline** with the paragraph text, preserving the visual layout you saw in Word.

---

## Handling Edge Cases and Variations

### Large Images

If a floating shape contains a high‑resolution image, converting it to inline may cause the line height to expand dramatically. To keep the PDF tidy:

```java
// Reduce image size before export (optional)
Shape shape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
shape.getImageData().setImageBytes(resizeImage(shape.getImageData().getImageBytes(), 800, 600));
```

*Explanation:* Resizing the image reduces its dimensions, preventing oversized lines in the final PDF.

### Multiple Sections with Different Layouts

When a document has sections with distinct page setups, you might need to apply the inline conversion only to a specific section:

```java
for (Section sec : doc.getSections()) {
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(sec.getPageSetup().getPaperSize() == PaperSize.A4);
    doc.save("section_" + sec.getId() + ".pdf", opts);
}
```

*Why this works:* The loop creates a separate PDF per section, applying the inline conversion conditionally based on paper size.

### Converting Multiple DOCX Files in a Batch

If you need to **convert word to pdf** for dozens of files, wrap the logic into a utility method:

```java
public static void convertDocxToPdfInline(String inputPath, String outputPath) throws Exception {
    Document doc = new Document(inputPath);
    PdfSaveOptions options = new PdfSaveOptions();
    options.setExportFloatingShapesAsInlineTag(true);
    doc.save(outputPath, options);
}
```

You can then call this method inside a `Files.list(Paths.get("batch_folder"))` stream.

---

## Full Working Example (All Steps Combined)

Below is the complete, ready‑to‑run Java program that demonstrates **how to save pdf** with inline shapes from a DOCX file.

```java
import com.aspose.words.*;

public class InlineShapePdfExporter {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Set PDF options to export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF
            doc.save("YOUR_DIRECTORY/inlineShapes.pdf", pdfOptions);

            System.out.println("PDF saved successfully with inline shapes!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

### Expected Result

Running the program should produce `inlineShapes.pdf`. Open it, and you’ll notice that any floating text boxes, callouts, or images now sit **inline** with the surrounding text, mirroring the layout you designed in Word.

---

## Frequently Asked Questions

| Question | Answer |
|----------|--------|
| **Does this work with .doc files?** | Yes. Aspose.Words can load older `.doc` formats; the same `PdfSaveOptions` apply. |
| **Can I keep some shapes floating?** | You’d need to adjust the shape’s `WrapType` to `INLINE` manually before export, or run a second export without the inline flag for those sections. |
| **Is there any performance impact?** | The extra conversion step adds negligible overhead—usually a few milliseconds per document. |
| **What about password‑protected DOCX?** | Load the document with `LoadOptions` that include the password, then proceed as usual. |
| **Will this work on Linux/macOS?** | Absolutely. Aspose.Words for Java is platform‑agnostic. |

---

## Next Steps & Related Topics

Now that you’ve mastered **how to export shapes** and **save docx as pdf**, consider exploring:

- **Styling PDFs** – use `PdfSaveOptions.setCompliance(PdfCompliance.PDF_A_1_B)` for archival‑grade PDFs.  
- **Adding Watermarks** – inject `Watermark` objects before saving.  
- **Converting to other formats** – try `doc.save("output.html", SaveFormat.HTML)` for web‑ready output.  
- **Batch processing** – combine the utility method with a scheduler for automated document pipelines.  

Each of these builds on the foundation you just laid down, expanding your ability to **convert word to pdf** in sophisticated ways.

---

## Conclusion

We’ve covered **how to save pdf** from a Word document while ensuring floating shapes become inline tags, a technique that eliminates layout surprises in the final PDF. By loading the DOCX, configuring `PdfSaveOptions` with `setExportFloatingShapesAsInlineTag(true)`, and saving the output, you get a clean, reliable conversion—perfect for reports, invoices, or any automated document workflow.

Give it a spin, tweak the options, and you’ll quickly see why this approach is the go‑to solution for developers who need to **save word pdf inline** without a hitch. Happy coding, and may your PDFs always look exactly as you intended!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [aspose word to pdf – Convert DOCX to PDF in Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)
- [save docx as pdf with Aspose.Words – Complete C# Guide](/words/english/net/basic-conversions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}