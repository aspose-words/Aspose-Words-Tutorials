---
category: general
date: 2026-05-26
description: Embed images as base64 while you convert docx to markdown with Aspose.Words
  for Java. Learn to convert word to markdown, save word as markdown, and handle images.
draft: false
keywords:
- embed images as base64
- convert docx to markdown
- convert word to markdown
- convert images to base64
- save word as markdown
language: en
og_description: Embed images as base64 while converting docx to markdown with Aspose.Words
  for Java. Complete guide to convert word to markdown and save word as markdown.
og_title: Embed Images as Base64 When Converting DOCX to Markdown
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Embed images as base64 while you convert docx to markdown with Aspose.Words
    for Java. Learn to convert word to markdown, save word as markdown, and handle
    images.
  headline: Embed Images as Base64 When Converting DOCX to Markdown
  type: TechArticle
- description: Embed images as base64 while you convert docx to markdown with Aspose.Words
    for Java. Learn to convert word to markdown, save word as markdown, and handle
    images.
  name: Embed Images as Base64 When Converting DOCX to Markdown
  steps:
  - name: 'H3: Why Use `setSaveToMemory(true)`?'
    text: 'When `saveToMemory` is true, Aspose writes the image bytes to a memory
      stream instead of a file. The Markdown exporter then converts that stream to
      a Base64 string and inserts it directly into the Markdown image tag:'
  - name: Troubleshooting Checklist
    text: '| Issue | Likely Cause | Fix | |-------|--------------|-----| | Image appears
      as a broken link | `setSaveToMemory` was omitted | Ensure `args.setSaveToMemory(true);`
      is inside the callback | | Base64 string is truncated | Output file encoding
      mismatch | Save the Markdown using UTF‑8 (default for Asp'
  - name: Convert Only Selected Images
    text: 'If you only want to embed certain images (e.g., those larger than 100 KB),
      add a size check:'
  - name: Use a Different Image Format
    text: The `ResourceSavingArgs` gives you the raw bytes, so you could re‑encode
      JPEGs as PNGs before embedding—useful when the target Markdown consumer prefers
      PNG.
  type: HowTo
tags:
- Aspose.Words
- Java
- Markdown
- Base64
title: Embed Images as Base64 When Converting DOCX to Markdown
url: /java/document-conversion-and-export/embed-images-as-base64-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Embed Images as Base64 When Converting DOCX to Markdown

Ever wondered how to **embed images as base64** while you **convert docx to markdown**? You’re not the only one—developers constantly ask how to keep images inline without juggling separate files. The good news is that Aspose.Words for Java makes it a breeze: you can convert a Word document to Markdown and automatically embed every picture as a Base64 string.

In this tutorial we’ll walk through the entire process—from loading a `.docx` that contains pictures, to configuring a `MarkdownSaveOptions` callback that does the heavy lifting, and finally saving the result as a clean `.md` file. By the end you’ll know exactly how to **convert word to markdown**, **convert images to base64**, and **save word as markdown** without leaving stray image folders behind. No external tools, no manual post‑processing—just pure Java code that you can drop into any project.

## What You’ll Need

- **Java 17** (or any recent JDK) – the code uses lambda syntax, but you can adapt it to older versions.
- **Aspose.Words for Java** library (latest version as of 2026). Add the Maven dependency or the JAR to your classpath.
- A sample **DOCX** file that contains at least one image.  
- An IDE or a simple text editor—Visual Studio Code, IntelliJ IDEA, or even `vim` will do.

If you already have these, great—let’s dive straight in.

## Step 1: Load the Word Document

First we create a `Document` instance that points to the source file. This is the same step whether you’re **convert docx to markdown** or just reading the file for other purposes.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Load the source DOCX that contains images
        Document doc = new Document("YOUR_DIRECTORY/doc-with-images.docx");
```

> **Why this matters:** The `Document` object is the entry point for every Aspose operation. It holds the whole Word structure—including images, tables, and styles—so the later callback can inspect each resource.

## Step 2: Create MarkdownSaveOptions and Register a Resource‑Saving Callback

The magic lives in `MarkdownSaveOptions`. By attaching an `IResourceSavingCallback` we gain control over how each external resource (like an image) is written.

```java
        // Configure Markdown save options
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

        // Register the callback that will embed images as Base64
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                // The callback fires for every resource Aspose wants to write
                if (args.getResourceType() == ResourceType.IMAGE) {
                    // Tell Aspose we don’t want a separate image file
                    args.setKeepResourceOriginalName(false);
                    // Give the image a predictable name (optional)
                    args.setResourceFileName("image_" + args.getResourceFileName());
                    // Force in‑memory saving – this triggers Base64 embedding
                    args.setSaveToMemory(true);
                }
            }
        });
```

### H3: Why Use `setSaveToMemory(true)`?

When `saveToMemory` is true, Aspose writes the image bytes to a memory stream instead of a file. The Markdown exporter then converts that stream to a Base64 string and inserts it directly into the Markdown image tag:

```markdown
![image_image1.png](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

That’s the core of **embed images as base64**.

## Step 3: Save the Document as Markdown

Now that the callback is in place, the final step is simply calling `save`. This is where we actually **convert word to markdown** and, because of the callback, also **convert images to base64**.

```java
        // Save the document as Markdown – this triggers the callback
        doc.save("YOUR_DIRECTORY/out.md", mdOptions);
    }
}
```

> **Result:** `out.md` contains Markdown text with every image represented as a `data:` URI. No extra image files are created on disk, so the folder stays tidy.

## Step 4: Verify the Output and Common Pitfalls

Open the generated `out.md` in any Markdown viewer (VS Code, GitHub, or a static site generator). You should see something like:

```markdown
# Sample Document

Here is an inline image:

![image_image1.png](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

### Troubleshooting Checklist

| Issue | Likely Cause | Fix |
|-------|--------------|-----|
| Image appears as a broken link | `setSaveToMemory` was omitted | Ensure `args.setSaveToMemory(true);` is inside the callback |
| Base64 string is truncated | Output file encoding mismatch | Save the Markdown using UTF‑8 (default for Aspose) |
| Unexpected file names | `setKeepResourceOriginalName(true)` | Keep it `false` to force the custom naming logic |

## Step 5: Advanced Variations (Optional)

### Convert Only Selected Images

If you only want to embed certain images (e.g., those larger than 100 KB), add a size check:

```java
if (args.getResourceType() == ResourceType.IMAGE) {
    if (args.getResourceData().length > 100_000) {
        args.setSaveToMemory(true);
    }
}
```

### Use a Different Image Format

The `ResourceSavingArgs` gives you the raw bytes, so you could re‑encode JPEGs as PNGs before embedding—useful when the target Markdown consumer prefers PNG.

```java
if (args.getResourceFileName().endsWith(".jpg")) {
    // Convert JPEG bytes to PNG bytes (requires an image library)
    byte[] pngBytes = convertJpegToPng(args.getResourceData());
    args.setResourceData(pngBytes);
    args.setResourceFileName(args.getResourceFileName().replace(".jpg", ".png"));
    args.setSaveToMemory(true);
}
```

These tweaks illustrate how flexible the **embed images as base64** approach is when you **convert docx to markdown**.

## Conclusion

You’ve just learned how to **embed images as base64** while you **convert docx to markdown** using Aspose.Words for Java. By wiring a simple `IResourceSavingCallback`, the library does all the heavy lifting: it **convert word to markdown**, **convert images to base64**, and finally **save word as markdown** with a single `save` call.  

Feel free to experiment—try different image‑filtering rules, switch to HTML output, or chain this step with a static‑site generator. The same pattern works for other formats (HTML, EPUB) as well, so you can reuse the callback wherever you need inline resources.

**Next steps:**  
- Explore `HtmlSaveOptions` for HTML‑with‑Base64 images.  
- Combine this with a CI pipeline to automate documentation generation.  
- Dive into Aspose’s `DocumentVisitor` if you need even finer control over the conversion process.

Happy coding, and enjoy your clean, self‑contained Markdown files!


## Related Tutorials

- [How to Embed Images in Markdown When Converting DOCX](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [Convert docx to markdown – Export Math Equations to LaTeX with Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [Save Images from Word – Aspose.Words for Java Guide](/words/english/java/document-loading-and-saving/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}