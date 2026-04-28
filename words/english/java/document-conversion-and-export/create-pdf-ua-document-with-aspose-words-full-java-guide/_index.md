---
category: general
date: 2026-04-28
description: Create PDF UA document using Aspose.Words for Java. Learn to load docx
  with recovery, export equations to LaTeX, save markdown from Word, and retrieve
  missing fonts.
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: en
og_description: Create PDF UA document with Aspose.Words for Java. Step‑by‑step guide
  covering recovery loading, LaTeX export, Markdown saving, and missing‑font retrieval.
og_title: Create PDF UA Document – Complete Java Tutorial
tags:
- Aspose.Words
- Java
- PDF/UA
title: Create PDF UA Document with Aspose.Words – Full Java Guide
url: /java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create PDF UA Document – Complete Java Tutorial

Need to **create PDF UA document** from a Word file while handling corrupted content? In this tutorial we’ll walk you through loading a DOCX with recovery, exporting equations to LaTeX, saving Markdown from Word, and retrieving missing fonts—all with Aspose.Words for Java.  

If you’ve ever stared at a broken .docx and wondered why your PDF isn’t accessible, you’re in the right place. By the end you’ll have a fully‑compliant PDF/UA 1 file, a Markdown version that contains LaTeX equations, and a clear list of any font substitutions that occurred during loading.

## What You’ll Need

- **Aspose.Words for Java** (latest version as of 2026) – add the Maven/Gradle dependency or the JAR to your classpath.  
- Java 17 or newer (the API uses streams, so a recent JDK is recommended).  
- A sample `input.docx` that may contain corrupted sections, Office Math equations, and floating shapes.  

No extra libraries are required; everything lives inside Aspose.Words.

---

## Step 1 – Load DOCX with Recovery Mode  

When a document is partially damaged, the default loader throws an exception. By enabling recovery mode you tell Aspose.Words to keep going and surface warnings instead.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*Why this matters:* Recovery mode prevents your whole pipeline from breaking because of a single bad paragraph. It also populates `doc.getWarnings()` so you can later **retrieve missing fonts** and other issues.

---

## Step 2 – Export Equations to LaTeX Inside a Markdown File  

Most developers love Markdown for documentation, but Word’s built‑in equations are a pain to copy. Aspose.Words can translate them straight to LaTeX.

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*Pro tip:* The callback ensures every extracted image lands under `imgs/`. This mirrors how GitHub renders Markdown – clean and portable.

---

## Step 3 – Create PDF / UA Document with Proper Tagging  

PDF/UA (Universal Accessibility) compliance is mandatory for many public sector projects. The following options make Aspose.Words tag floating shapes correctly and set the PDF/UA compliance flag.

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*What you’ll see:* Opening `output.pdf` in Adobe Acrobat Pro will show “PDF/UA‑1 compliant” under the document properties. All floating shapes (text boxes, pictures) will have appropriate tags for screen readers.

---

## Step 4 – Tweak a Shape’s Shadow (Optional Styling)  

While not required for accessibility, tweaking visual aspects can be handy for internal reports.

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*Why bother?* If the PDF is also a marketing piece, a subtle shadow makes the layout feel polished without breaking compliance.

---

## Step 5 – Retrieve Missing Fonts and Other Warnings  

During the recovery load, Aspose.Words records any font substitutions. Listing them helps you decide whether to embed the correct font or accept the fallback.

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*Typical output* (your console will show something like):

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

If you see critical fonts missing, consider installing them on the server or embedding them via `PdfSaveOptions.setEmbedFullFonts(true)`.

---

## Full Working Example  

Below is the complete, ready‑to‑run Java class. Paste it into your IDE, adjust the paths, and hit **Run**.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**Expected results**

| Output | Description |
|--------|-------------|
| `output.md` | Markdown file where every Office Math equation appears as LaTeX (`$…$`). Images are stored under `imgs/`. |
| `output.pdf` | PDF/UA‑1 compliant document; open in Acrobat to see “PDF/UA‑1” under File → Properties → Standards. |
| Console | List of any missing fonts, e.g., “Missing: Calibri → substituted: Arial”. |

---

## Frequently Asked Questions (FAQ)

**Q: Does this work with older Aspose.Words versions?**  
A: The `RecoveryMode`, `OfficeMathExportMode.LATEX`, and `PdfCompliance.PDF_UA_1` enums were introduced in 22.8. If you’re on an older release, upgrade – the accessibility features are not back‑ported.

**Q: What if I need to embed the original fonts instead of substitution?**  
A: Set `pdfOptions.setEmbedFullFonts(true)` and ensure the font files are reachable on the JVM’s font path.

**Q: Can I export to other markup formats (e.g., HTML) while keeping LaTeX equations?**  
A: Yes. Use `HtmlSaveOptions` and set `setOfficeMathExportMode(OfficeMathExportMode.LATEX)` – the same enum works across formats.

**Q: My DOCX contains many floating shapes; will they all be tagged?**  
A: With `setExportFloatingShapesAsInlineTag(true)`, Aspose.Words wraps each floating shape in an `<Figure>` tag for PDF/UA, satisfying most screen‑reader checks.

---

## Wrap‑Up  

We’ve just shown you how to **create PDF UA document** from a Word source, while also **load docx with recovery**, **export equations to LaTeX**, **save markdown from Word**, and **retrieve missing fonts**. The code is fully self‑contained, runs on any Java 17+ environment, and produces assets ready for both accessibility audits and developer

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}