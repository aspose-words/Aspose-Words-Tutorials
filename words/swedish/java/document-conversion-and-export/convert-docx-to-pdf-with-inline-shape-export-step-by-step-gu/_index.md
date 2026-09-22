---
category: general
date: 2026-02-18
description: Lär dig hur du konverterar DOCX till PDF och sparar Word som PDF samtidigt
  som du bevarar flytande former. Den här guiden visar hur du exporterar former korrekt.
draft: false
keywords:
- convert docx to pdf
- save word as pdf
- how to export shapes
language: sv
og_description: Konvertera DOCX till PDF och lär dig hur du exporterar former. Följ
  den här kompletta handledningen för att spara Word som PDF med korrekt taggning.
og_title: Konvertera DOCX till PDF – Guide för export av infogade former
tags:
- Aspose.Words
- Java
- PDF conversion
title: Konvertera DOCX till PDF med inline‑formexport – Steg‑för‑steg‑guide
url: /sv/java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convert DOCX to PDF – Inline Shape Export Guide

Har du någonsin behövt **konvertera DOCX till PDF** men oroat dig för att flytande bilder eller textrutor skulle försvinna eller flyttas? Du är inte ensam. I många projekt—tänk automatiska rapportgeneratorer eller batch‑processpipelines—är det icke‑förhandlingsbart att bevara den exakta layouten i ett Word‑dokument.  

Den goda nyheten? Med några få rader kod kan du **spara Word som PDF** och styra om de flytande formerna blir inline‑taggar eller förblir block‑nivåelement. Nedan ser du exakt **hur du exporterar former** på det sätt du vill, plus ett antal tips som sparar dig från vanliga fallgropar.

---

## What You’ll Learn

* Ladda en `.docx`‑fil från disk.  
* Konfigurera `PdfSaveOptions` så att flytande former exporteras som inline‑taggar.  
* Skriv den resulterande PDF‑filen till en mapp du själv väljer.  
* Förstå varför flaggan `setExportFloatingShapesAsInlineTag` är viktig och när du eventuellt vill ändra den.  

Ingen extern tjänst, ingen magisk “klick‑för‑nedladdning”-UI—bara ren Java‑kod som du kan släppa in i vilket Maven‑ eller Gradle‑projekt som helst.

---

## Prerequisites

| Requirement | Why it matters |
|-------------|----------------|
| **Aspose.Words for Java** (v23.12 or later) | Provides the `Document` and `PdfSaveOptions` classes used in the example. |
| **JDK 8+** | The library is compiled for Java 8 and newer; older runtimes will throw `UnsupportedClassVersionError`. |
| **A DOCX file** with at least one floating shape (image, text box, WordArt) | To see the effect of the shape‑export option, you need a document that actually contains floating objects. |

If you already have these pieces, great—let’s jump in.

---

## Step 1 – Load the Source Document  

First we create a `Document` instance pointing at the `.docx` you want to convert. The constructor reads the file into memory, parses the OpenXML package, and prepares the internal object model.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

// Adjust the path to your environment
String inputPath = "YOUR_DIRECTORY/input.docx";

Document doc = new Document(inputPath);
```

> **Pro tip:** If you’re processing many files in a loop, reuse a single `Document` object only after you’ve called `doc.close()` (or let the garbage collector handle it). This prevents file‑handle leaks on Windows.

---

## Step 2 – Configure PDF Save Options to Export Shapes  

The heart of the tutorial lives here. `PdfSaveOptions` lets you dictate how the conversion behaves. Setting `setExportFloatingShapesAsInlineTag(true)` forces every floating shape to be treated as an *inline* element in the PDF’s tag structure. That means screen‑readers will read the shape in the same order as surrounding text, which is often required for accessibility compliance.

```java
import com.aspose.words.PdfSaveOptions;

PdfSaveOptions pdfOptions = new PdfSaveOptions();
// true → inline tagging (shape behaves like a character)
// false → block‑level tagging (shape sits in its own block)
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

**When would you set it to `false`?**  
If your PDF is destined for print‑only distribution and you want the shapes to retain their original positioning without affecting the logical reading order, you might prefer block‑level tagging. The default is `false`, so we explicitly enable the inline behavior for this tutorial.

---

## Step 3 – Save the Document as a PDF  

Now that the options are ready, call `save` with the target filename and the options object. The library handles the heavy lifting: layout engine, font embedding, and tag generation.

```java
String outputPath = "YOUR_DIRECTORY/shapes.pdf";
doc.save(outputPath, pdfOptions);
```

After the call finishes, you’ll find `shapes.pdf` in the specified folder. Open it in Adobe Acrobat or any PDF viewer that shows tags (usually under **File → Properties → Tags**) and you’ll see that the floating shape appears as an inline tag.

---

## Full, Runnable Example  

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

---

## Frequently Asked Questions & Edge Cases  

### 1️⃣ Does this work with password‑protected DOCX files?  
Yes—just supply the password before loading:

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document doc = new Document(inputPath, loadOptions);
```

### 2️⃣ What about SVG or EMF images inside the Word file?  
Aspose.Words automatically rasterizes vector graphics when saving to PDF. If you need them to stay vector, set:

```java
pdfOptions.setRasterizeTransformedElements(false);
```

### 3️⃣ How do I preserve hyperlinks while converting?  
Links are kept by default. However, if you disable tags (`pdfOptions.setSaveFormat(SaveFormat.PDF)` without options), you might lose the logical structure. Keep the `PdfSaveOptions` object to retain both tags and links.

### 4️⃣ Can I batch‑process a folder of DOCX files?  
Absolutely. Wrap the `DocxToPdfWithShapes` logic in a loop that iterates over `Files.list(Paths.get("YOUR_DIRECTORY"))`. Remember to handle exceptions per file so one bad document doesn’t halt the whole run.

---

## Tips from the Trenches  

* **Watch out for missing fonts.** If the source DOCX uses a custom font not installed on the server, the PDF will substitute a fallback, potentially breaking layout. Use `pdfOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)` to force embedding.  
* **Testing accessibility.** After conversion, run Acrobat’s **Accessibility Checker**. Inline tagging usually improves the score, but you may still need to add alternate text to images manually.  
* **Performance tip:** For large documents (100+ pages), enable `pdfOptions.setMemoryOptimization(true)` to reduce heap usage.

---

## Visual Confirmation  

Below is a quick screenshot of the PDF opened in Adobe Acrobat, showing the inline‑tagged shape highlighted in the **Tags** pane.

![Convert DOCX to PDF example output](image.png)

*Alt text: exempel på konvertering av DOCX till PDF som visar inline‑formtaggar.*

---

## Wrap‑Up  

You now know **how to convert DOCX to PDF** while controlling the way floating objects are exported. By toggling `setExportFloatingShapesAsInlineTag`, you decide whether shapes become part of the reading order or stay as independent blocks—crucial for both accessibility and visual fidelity.  

From here you can:

* **Save Word as PDF** in bulk for archiving.  
* Experiment with other `PdfSaveOptions` like `setCompliance(PdfCompliance.PDF_A_1B)` for long‑term preservation.  
* Dive deeper into **how to export shapes** by exploring the full Aspose.Words documentation or trying out the `setExportDocumentStructure(true)` flag for richer tag trees.

Give it a spin, tweak the options, and let your PDFs look exactly how you need them to. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}