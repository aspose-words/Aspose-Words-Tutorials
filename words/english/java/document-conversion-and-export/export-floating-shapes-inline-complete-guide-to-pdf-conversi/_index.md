---
category: general
date: 2026-07-03
description: Export floating shapes inline while converting Word to PDF inline. Learn
  how to set PDF options and save Word as PDF options in Java.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: en
og_description: Export floating shapes inline when you convert a Word document to
  PDF. This tutorial shows how to set PDF options and save Word as PDF options.
og_title: Export Floating Shapes Inline – Java PDF Conversion Guide
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Export Floating Shapes Inline – Complete Guide to PDF Conversion
url: /java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Export Floating Shapes Inline – Complete Guide to PDF Conversion

Ever needed to **export floating shapes inline** when you convert a Word document to PDF? You’re not alone—many developers hit this snag when their diagrams or icons mysteriously shift to separate layers. The good news is that a single PDF option can keep those shapes snug inside `<span>` tags, preserving layout exactly as you see it in Word.

In this tutorial we’ll walk through **how to set PDF options** in Java, show you the exact code to **save Word as PDF options**, and explain why you might want to **convert Word to PDF inline** instead of the default block‑level export. By the end, you’ll have a ready‑to‑run snippet that you can drop into any Maven or Gradle project.

## What You’ll Learn

- The difference between inline `<span>` and block `<div>` export for floating shapes.  
- How to configure `PdfSaveOptions` to force inline rendering.  
- Step‑by‑step code that loads a `.docx`, applies the option, and writes out a PDF.  
- Common pitfalls (missing fonts, unsupported shapes) and how to avoid them.  
- Tips for testing the output and extending the approach to other document elements.

**Prerequisites** – you’ll need Java 8 or newer, the Aspose.Words for Java library (or any API that mirrors its `PdfSaveOptions` class), and a sample Word file with floating shapes (the tutorial uses `FloatingShapes.docx`). No other external tools are required.

---

## Step 1: Load the Source Word Document

The first thing you do is open the `.docx` you want to transform. This is straightforward, but make sure the path is absolute or correctly resolved from your classpath.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Why this matters:*  
If the document isn’t loaded correctly, the subsequent PDF conversion will throw a `FileNotFoundException`. Using `Document` ensures the internal object model is fully populated, including any floating shapes that live on the page.

---

## Step 2: Create PDF Save Options and Set Floating Shapes to Inline

Here’s where the magic happens. By default Aspose.Words exports floating shapes as block‑level `<div>` elements, which can break the flow in HTML‑based PDFs. Setting `setExportFloatingShapesAsInlineTag(true)` tells the engine to wrap each shape in an inline `<span>` instead.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Why this matters:*  
- **Layout fidelity** – Inline tags keep the shape aligned with surrounding text, avoiding unwanted gaps.  
- **Searchability** – Inline elements are more likely to be indexed correctly by PDF readers.  
- **Styling control** – You can target the `<span>` with CSS if you later convert the PDF back to HTML.

> **Pro tip:** If you ever need the old block behavior for a specific document, simply pass `false` or omit the call altogether.

---

## Step 3: Save the Document as a PDF Using the Configured Options

Now you combine the loaded `Document` with the `PdfSaveOptions` and write the file out. This single line does the heavy lifting.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Why this matters:*  
The `save` method respects every flag you set on `pdfOptions`. Forgetting to pass the options will revert to the default block export, defeating the purpose of **export floating shapes inline**.

---

## Full Working Example

Putting it all together, here’s a compact program you can compile and run right now. Replace `YOUR_DIRECTORY` with an actual path on your machine.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Expected output** – After running the program, open `FloatingShapes.pdf`. You should see the shapes sitting flush with the text, no extra white space, and the HTML representation (if you inspect the PDF’s internal structure) will contain `<span>` tags around each shape.

![Export floating shapes inline example](https://example.com/export-inline.png "Screenshot showing floating shapes rendered inline in the PDF")

*Image alt text:* **export floating shapes inline** screenshot of PDF with inline shapes.

---

## Common Questions & Edge Cases

### 1. “What if my document contains complex SmartArt?”

SmartArt is treated as a drawing object. The inline flag works for most vector shapes, but very intricate SmartArt may still be rendered as an image. In those cases, consider flattening the SmartArt in Word before conversion, or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.

### 2. “Can I combine inline and block exports in the same document?”

Unfortunately the API applies the setting globally. If you need mixed behavior, split the document into sections, export each section separately with different options, then merge the PDFs using `PdfMerger`.

### 3. “Does this affect font embedding?”

No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)` (default). You can safely enable or disable it without touching the inline shape flag.

### 4. “How do I verify that shapes are really `<span>`?”

Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** → **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>` element in the underlying XML. If you see `<div>`, the option wasn’t applied.

---

## Extending the Approach – Related Options

While you’re here, you might also want to explore other PDF conversion knobs:

| Option | What it does | Typical use‑case |
|--------|--------------|------------------|
| `setCompressImages(true)` | Reduces image size | Faster downloads |
| `setUseHighQualityRendering(true)` | Improves vector rendering | Print‑ready PDFs |
| `setExportDocumentStructure(true)` | Adds structural tags for accessibility | WCAG compliance |
| `setSaveFormat(SaveFormat.PDF)` | Explicitly sets format (rarely needed) | Multi‑format pipelines |

These settings pair nicely with **convert word to pdf inline** scenarios where you need both layout fidelity and performance.

---

## Testing Your Conversion

1. **Visual check** – Open the PDF in two viewers (Chrome and Adobe Reader) to ensure shapes line up.  
2. **Automated diff** – Use a library like `pdfbox` to extract the XML and assert the presence of `<span>` tags.  
3. **Performance benchmark** – Measure the time taken with and without `setCompressImages` to see the trade‑off.

A quick JUnit example:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## Conclusion

You now have a solid, end‑to‑end solution for **export floating shapes inline** when you **convert Word to PDF inline**. By configuring `PdfSaveOptions` you control the HTML tag used for each shape, keeping your PDFs tidy and searchable. Remember to test the output, adjust related options like image compression, and handle edge cases such as complex SmartArt.

Ready for the next step? Try applying the same technique to **export floating tables inline** or experiment with CSS‑styled PDFs using Aspose’s `HtmlSaveOptions`. The same pattern—load, configure, save—holds for almost every document‑to‑PDF scenario.

Got more questions about **how to set pdf options** or need help with **save word as pdf options** for a different library? Drop a comment, and happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}