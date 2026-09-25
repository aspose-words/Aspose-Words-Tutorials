---
category: general
date: 2026-02-28
description: Learn how to embed images while you convert doc to markdown. Export markdown
  with images and get inline images in markdown using Java.
draft: false
keywords:
- how to embed images
- convert doc to markdown
- convert word to markdown
- export markdown with images
- inline images in markdown
language: en
og_description: Discover how to embed images while converting a Word document to Markdown.
  This guide shows you how to export markdown with images and keep them inline.
og_title: How to Embed Images When Converting Word to Markdown
tags:
- markdown
- java
- Aspose.Words
- image handling
title: How to Embed Images When Converting Word to Markdown – Complete Guide
url: /java/document-conversion-and-export/how-to-embed-images-when-converting-word-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Embed Images When Converting Word to Markdown – Complete Guide

Ever wondered **how to embed images** in a Markdown file that you generate from a Word document?  Maybe you’ve tried a quick export, only to end up with a bunch of dangling image files and broken links.  That’s a common pain point—especially when you need a single, portable `.md` that you can drop into a static‑site generator or a GitHub README.

The good news?  You can tell the exporter to inline every picture as a Base64‑encoded string, so the resulting Markdown is self‑contained.  In this tutorial we’ll walk through the exact steps, show you the full Java code, and explain why each piece matters.  By the end you’ll be able to **convert doc to markdown** with images embedded, and you’ll also see how to tweak the process for other scenarios like “export markdown with images” or “inline images in markdown”.

## What You’ll Learn

- The required libraries and a minimal project setup.  
- How to configure `MarkdownSaveOptions` so that images become Base64 data URIs.  
- Why using a `ResourceSavingCallback` is the cleanest way to control image handling.  
- How to verify that the Markdown file actually contains the embedded images.  
- Tips for edge cases (large images, different MIME types, and performance considerations).  

No prior experience with Aspose.Words is needed; a basic Java background is enough.

---

## Prerequisites

Before we dive into code, make sure you have:

| Requirement | Why it matters |
|-------------|----------------|
| **Java 17+** (or any recent JDK) | The Aspose.Words for Java API targets Java 8+, but using the latest JDK gives you the built‑in `Base64` utilities. |
| **Aspose.Words for Java** (latest version) | This library provides the `MarkdownSaveOptions` and the callback infrastructure we’ll use. |
| **A Word document** (`.docx`) that contains at least one image | We need something to convert; the example assumes a file called `sample.docx`. |
| **An IDE or text editor** (IntelliJ, VS Code, etc.) | To compile and run the sample quickly. |

Add the Aspose dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). Here’s the Maven snippet:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check the latest version on Maven Central -->
</dependency>
```

If you prefer Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Aspose offers a free 30‑day trial. Grab a temporary license key and register it early to avoid watermark messages.

---

## Step 1: Create the Markdown Save Options

The first thing we do is instantiate `MarkdownSaveOptions`. This object tells Aspose how we want the conversion to behave—font handling, list formatting, and, most importantly for us, image handling.

```csharp
// Step 1: Create Markdown save options
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();
```

In Java the syntax is identical; just replace the `csharp` keyword with `java` in the code block later.  
Why this matters: without customizing the options, Aspose will write each image to a separate file next to the `.md`.  By preparing the options object now, we give ourselves a hook to intercept that default behavior.

---

## Step 2: Intercept Image Resources and Encode Them as Base64

Aspose fires a callback every time it wants to write a resource (image, CSS, etc.). By implementing `IResourceSavingCallback` we can decide what to do with each resource. The snippet below checks if the resource is an image, clears the file name (so no external file is created), encodes the binary data to Base64, and sets the proper MIME type.

```java
// Step 2: Embed all images directly as Base64 data
markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Check if the resource being saved is an image
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Suppress writing an external image file
            args.setResourceFileName(null);
            // Encode the image bytes to a Base64 string
            args.setResourceData(Base64.getEncoder()
                    .encodeToString(args.getResourceData()));
            // Set the appropriate MIME type for the embedded image
            args.setResourceContentType("image/png");
        }
    }
});
```

**What’s happening under the hood?**

1. **`args.getResourceType()`** – Aspose classifies every outbound blob. We only care about `ResourceType.IMAGE`.  
2. **`args.setResourceFileName(null)`** – By null‑ing the filename we tell the library *not* to write a physical file.  
3. **`Base64.getEncoder().encodeToString(...)`** – The raw byte array becomes a text string that can be safely placed in a Markdown data URI.  
4. **`args.setResourceContentType("image/png")`** – This ensures the generated Markdown tag looks like `![alt](data:image/png;base64,…)`. If your source document contains JPEGs, you could inspect the original bytes and pick `"image/jpeg"` instead.

> **Why Base64?**  
> Markdown processors that understand data URIs will render the picture directly, and the resulting file stays portable—no extra assets to copy around. It’s especially handy for GitHub READMEs or documentation sites that disallow external resources.

---

## Step 3: Perform the Conversion

Now that the options are ready, simply load your Word document and call `save`. The path you provide will be the location of the generated Markdown file.

```java
// Step 3: Load the source Word document
Document doc = new Document("sample.docx");

// Step 4: Save the document as a Markdown file using the configured options
doc.save("output/doc.md", markdownSaveOptions);
```

That’s it—two lines of actual conversion code. The heavy lifting (reading the DOCX, extracting images, converting paragraphs) is all handled by Aspose.

---

## Step 4: Verify the Result – Inline Images Appear

Open `output/doc.md` in any text editor. You should see something like:

```markdown
# Sample Document

Here is an inline image:

![Image 1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

If you paste the Markdown into a viewer that supports data URIs (GitHub, VS Code preview, or a static‑site generator), the picture will render without any extra files.

**Quick sanity check**:  

- **Search for `data:image/`** – If you find a few long strings, the embedding worked.  
- **Count the `![](` patterns** – They should match the number of images in the original Word file.

---

## Handling Edge Cases

### Large Images

Base64 inflates the original size by roughly **33 %**. For very large pictures (e.g., high‑resolution photos), the Markdown file can become unwieldy. Consider these strategies:

| Strategy | When to use |
|----------|--------------|
| **Resize before conversion** – Use `java.awt.Image` to scale down. | When the source document contains high‑resolution assets that aren’t needed at full size. |
| **Switch to JPEG** – Change `args.setResourceContentType("image/jpeg")`. | For photographs where PNG’s lossless format is overkill. |
| **Chunk the document** – Split the Word file into sections and export each separately. | When you need to keep the Markdown file under a certain size limit (e.g., GitHub’s 10 MB file cap). |

### Non‑PNG Images

If your Word document contains mixed formats, you can dynamically detect the MIME type:

```java
String mime = args.getResourceContentType(); // returns something like "image/jpeg"
args.setResourceContentType(mime); // keep original type
```

Aspose already populates `ResourceContentType`, so you often don’t need to hard‑code `"image/png"`.

### Performance Tips

- **Reuse a single `Base64.Encoder` instance** if you’re converting many images in a loop.  
- **Enable `markdownSaveOptions.setExportImagesAsBase64(true)`** (if the API version supports it) to avoid the callback entirely.  
- **Run the conversion in a background thread** when processing bulk documents in a server environment.

---

## Full Working Example (All Together)

Below is a copy‑paste‑ready Java program that includes imports, error handling, and the complete flow we discussed.

```java
import com.aspose.words.*;
import java.util.Base64;
import java.nio.file.Paths;

public class WordToMarkdownWithEmbeddedImages {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("sample.docx");

            // Configure Markdown save options
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

            // Embed images as Base64 data URIs
            mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
                @Override
                public void resourceSaving(ResourceSavingArgs rsArgs) {
                    if (rsArgs.getResourceType() == ResourceType.IMAGE) {
                        // Prevent external file creation
                        rsArgs.setResourceFileName(null);
                        // Encode image bytes to Base64
                        String base64 = Base64.getEncoder()
                                .encodeToString(rsArgs.getResourceData());
                        rsArgs.setResourceData(base64);
                        // Preserve original MIME type (PNG, JPEG, etc.)
                        String mime = rsArgs.getResourceContentType();
                        rsArgs.setResourceContentType(mime);
                    }
                }
            });

            // Define output path (ensure directory exists)
            String outputPath = Paths.get("output", "doc.md").toString();
            doc.save(outputPath, mdOptions);

            System.out.println("Conversion complete! Markdown saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("Error during conversion: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Expected output**: a single `doc.md` file that contains inline Base64 images, ready for any Markdown‑aware tool.

---

## Frequently Asked Questions

**Q1: Does this work with older versions of Aspose.Words?**  
*Usually yes.* The callback API has been stable since version 19. However, the `setExportImagesAsBase64` shortcut appeared in later releases, so if you’re on an older build you’ll need the explicit callback shown above.

**Q2: What if I need to export to GitHub Flavored Markdown (GFM)?**  
Aspose’s `MarkdownSaveOptions` already emits GFM‑compatible syntax. The only extra step is to make sure your repository’s rendering engine supports data URIs—GitHub does.

**Q3: Can I use this approach for other formats, like HTML?**  
Absolutely. The same `ResourceSavingCallback` works for `HtmlSaveOptions`. Just change the options class and keep the Base64 logic.

---

##

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}