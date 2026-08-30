---
category: general
date: 2026-05-04
description: How to set resolution for Markdown export from Word. Learn markdown image
  resolution, how to export equations, and save Word as markdown in Java.
draft: false
keywords:
- how to set resolution
- markdown image resolution
- how to use markdown
- how to export equations
- save word as markdown
language: en
og_description: How to set resolution for Markdown export from Word. This guide shows
  markdown image resolution, exporting equations, and saving Word as markdown.
og_title: How to Set Resolution When Saving Word as Markdown
tags:
- Aspose.Words
- Java
- Markdown
- Document Export
title: How to Set Resolution When Saving Word as Markdown
url: /java/document-conversion-and-export/how-to-set-resolution-when-saving-word-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Set Resolution When Saving Word as Markdown

Ever wondered **how to set resolution** for images that appear in a Markdown file generated from a Word document? You're not the only one. Many developers hit a snag when the default rasterized math images look blurry, especially on high‑DPI screens.  

In this tutorial we’ll walk through the exact steps to control *markdown image resolution* while also showing **how to export equations** as LaTeX, and finally how to **save Word as markdown** using Aspose.Words for Java. By the end you’ll have a crisp, production‑ready Markdown file that renders equations cleanly and images at the quality you need.

## Prerequisites

- Java 17 (or any recent JDK)  
- Aspose.Words for Java 23.6 or newer – you can grab it from Maven Central  
- A Word document (`.docx`) that contains OfficeMath objects (equations) and possibly raster images  
- Basic familiarity with Maven/Gradle and an IDE (IntelliJ IDEA, Eclipse, VS Code, etc.)

No additional libraries are required; everything else is handled by Aspose.Words.

---

## How to Set Resolution for Markdown Export

> **Pro tip:** The resolution you choose directly influences the file size of the generated images. A value of **300 dpi** is a good balance for most web‑based Markdown viewers.

```java
// Step 1: Load the source Word document containing equations
Document doc = new Document("YOUR_DIRECTORY/Math.docx");

// Step 2: Create Markdown save options to control the export behavior
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

// Step 3: Export OfficeMath objects as LaTeX expressions
saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Step 4 (optional): Set image resolution for any rasterized Math images
saveOptions.setImageResolution(300);   // <-- this is where we set the resolution

// Step 5: Save the document as a Markdown file using the configured options
doc.save("YOUR_DIRECTORY/MathExport.md", saveOptions);
```

The `setImageResolution(int dpi)` call is the heart of **how to set resolution**. It tells Aspose.Words to rasterize any fallback images (e.g., when an equation cannot be represented in pure LaTeX) at the specified dots‑per‑inch. If you omit this line, the library falls back to its default 220 dpi, which may look fuzzy on retina displays.

### Why Use LaTeX for Equations?

When you export equations as LaTeX (`OfficeMathExportMode.LATEX`), the resulting Markdown contains raw LaTeX code wrapped in `$…$` or `$$…$$`. Most modern Markdown renderers (GitHub, GitLab, MkDocs with MathJax) will render those as crisp, scalable vector graphics—no resolution worries there. The resolution setting only matters for **markdown image resolution** of any raster fallback images, such as embedded charts or pictures that aren’t natively supported in Markdown.

---

## How to Use Markdown Image Resolution Effectively

If you need to embed regular pictures (e.g., screenshots) inside your Word file, they’ll be converted to PNG by Aspose.Words. The same `setImageResolution` method applies, ensuring those PNGs inherit the DPI you specify. Here’s a quick checklist:

1. **Choose a DPI that matches your target platform** – 72 dpi for legacy web, 150 dpi for standard displays, 300 dpi for print‑quality PDFs.  
2. **Test the output** – open the generated `.md` file in your favorite viewer and zoom in to verify sharpness.  
3. **Consider file size** – higher DPI yields larger PNGs; if bandwidth is a concern, experiment with 200 dpi and compare.

---

## How to Export Equations as LaTeX

The line `saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);` tells Aspose.Words to translate every OfficeMath object into LaTeX. This is the recommended approach because:

- **Scalability** – LaTeX renders at any size without losing quality.  
- **Editability** – You can later tweak the LaTeX directly in the Markdown file.  
- **Compatibility** – Most static site generators and documentation tools already support LaTeX rendering.

If you ever need the old image‑based fallback, simply switch to `OfficeMathExportMode.IMAGE`. In that case, the resolution you set becomes even more critical.

---

## Save Word as Markdown – Full End‑to‑End Example

Below is a complete, runnable Maven project snippet that demonstrates the whole flow, from dependency declaration to execution.

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>markdown-export</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.6</version>
        </dependency>
    </dependencies>
</project>
```

```java
// src/main/java/com/example/MarkdownMathExport.java
package com.example;

import com.aspose.words.*;

public class MarkdownMathExport {
    public static void main(String[] args) throws Exception {
        // Load the source Word document containing equations and images
        Document doc = new Document("src/main/resources/Math.docx");

        // Configure Markdown export options
        MarkdownSaveOptions options = new MarkdownSaveOptions();
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX); // export equations as LaTeX
        options.setImageResolution(300); // set resolution for rasterized images

        // Save as Markdown
        doc.save("output/MathExport.md", options);

        System.out.println("✅ Markdown export complete! Check output/MathExport.md");
    }
}
```

**Expected result:** `MathExport.md` will contain LaTeX blocks for each equation, and any embedded pictures will appear as PNG links whose DPI is 300. Open the file in a Markdown viewer that supports MathJax (e.g., VS Code with the Markdown Preview Enhanced extension) and you should see perfectly sharp equations and images.

---

## Common Questions & Edge Cases

### What if I need a different DPI for only one image?

Aspose.Words applies the DPI globally via `setImageResolution`. To handle per‑image DPI, you’d need to post‑process the generated Markdown: replace the PNG files with higher‑resolution versions and adjust the image links manually. Not ideal, but doable for a handful of special cases.

### Does this work on Linux/macOS?

Absolutely. The library is pure Java, so the same code runs anywhere the JDK does. Just ensure the file paths use forward slashes or `Paths.get(...)` for platform‑independent handling.

### What about SVG output?

If you prefer vector images for charts, you can set `saveOptions.setExportImagesAsSvg(true);`. SVGs ignore DPI, so the **markdown image resolution** concern disappears. However, not all Markdown renderers handle SVG gracefully, so test your target platform first.

### Can I embed the generated Markdown into a static site generator?

Yes. The output is plain `.md` with standard Markdown syntax plus LaTeX delimiters. Most generators (Jekyll, Hugo, MkDocs) will accept it out of the box. Just remember to enable MathJax or KaTeX in your site config.

---

## Conclusion

We've covered **how to set resolution** for images when you **save Word as markdown**, explored **markdown image resolution** nuances, demonstrated **how to export equations** as LaTeX, and shown the full Java implementation. By tweaking `setImageResolution` and choosing the right `OfficeMathExportMode`, you gain precise control over both visual fidelity and file size.

Ready for the next step? Try combining this approach with Aspose.PDF to convert the same Word source directly to PDF, or experiment with `setExportImagesAsSvg(true)` for vector‑based graphics. The techniques you’ve learned here are building blocks for any automated documentation pipeline.

If you found this guide useful, give it a star on GitHub, share it with teammates, or drop a comment below with your own tips. Happy coding!  

![How to set resolution example](resolution.png "How to set resolution when saving Word as Markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}