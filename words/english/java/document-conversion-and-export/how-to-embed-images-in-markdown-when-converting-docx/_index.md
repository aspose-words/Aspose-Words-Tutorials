---
category: general
date: 2026-01-11
description: Learn how to embed images in Markdown while converting a DOCX file, using
  Base64 for small pictures and saving larger resources separately.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- export word document markdown
language: en
og_description: Learn how to embed images in Markdown while converting a DOCX file,
  using Base64 for small pictures and saving larger resources separately.
og_title: How to Embed Images in Markdown When Converting DOCX
tags:
- Aspose.Words
- Java
- Markdown
- Image Embedding
title: How to Embed Images in Markdown When Converting DOCX
url: /java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Embed Images in Markdown When Converting DOCX

Ever wondered **how to embed images** in a Markdown file that originates from a Word document? You're not alone. Most developers hit a snag when the conversion drops pictures or stores them in a way that breaks the final layout.  

In this guide we’ll walk through a complete, ready‑to‑run example that shows **how to embed images** as Base64 data URIs for tiny graphics, while larger assets get written to a side‑folder. Along the way we’ll also cover **convert docx to markdown**, touch on **how to convert docx** with Aspose.Words, and explain the difference between embedding images as Base64 versus exporting them as separate files.  

> **Pro tip:** If you only need a quick proof‑of‑concept, the code below works out‑of‑the‑box with a single Maven dependency.

---

## What You’ll Need

- **Java 17** (or any recent JDK) – the API is Java‑centric, but the concepts translate to other languages.
- **Aspose.Words for Java** – a commercial library that supports DOCX → Markdown conversion.
- A **sample DOCX** containing a mix of small icons and larger photos.
- A folder where you want the Markdown and its resources to live.

No additional frameworks, no external scripts. Just plain Java and Aspose.Words.

---

## Step 1 – Add Aspose.Words to Your Project (convert docx to markdown)

If you’re using Maven, drop the following snippet into your `pom.xml`. Feel free to replace the version with the latest release at the time of reading.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Why this matters:** Aspose.Words handles the heavy lifting of parsing the DOCX structure, extracting images, and rendering Markdown syntax. Trying to roll your own parser would be a rabbit hole you probably don’t need to go down.

---

## Step 2 – Load the Source DOCX Document

First, point the API at the Word file you want to transform. The `Document` constructor does all the work—no manual XML parsing required.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Notice the comment explains *why* this line is crucial: without a `Document` instance there’s nothing to convert.

---

## Step 3 – Prepare MarkdownSaveOptions with a Resource‑Saving Callback

This is the heart of **how to embed images** correctly. The callback gives you a hook for each resource (image, style, etc.) that the converter wants to write.

```java
        // Step 3: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Step 4: Decide how to handle each image
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    // Small image – embed as Base64
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger image – write to a folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        // Normalize path for Markdown (use forward slashes)
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });
```

### Why a callback?

- **Control:** You decide whether an image becomes an inline Base64 string or a separate file.
- **Performance:** Tiny icons become part of the Markdown, eliminating extra HTTP requests.
- **Portability:** Larger pictures stay as external files, keeping the Markdown size reasonable.

---

## Step 4 – Save the Document as Markdown

Finally, tell Aspose.Words to write the Markdown file using the options we just configured.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

Running the program produces two things:

1. `output.md` – the Markdown representation of your original DOCX.
2. A `markdown_resources` folder containing any large images that weren’t embedded.

---

## Full Working Example (All Steps in One Place)

Below is the complete source file, ready to copy‑paste into your IDE. Replace `YOUR_DIRECTORY` with the actual path on your machine.

```java
import com.aspose.words.*;
import java.nio.file.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Small images (<10 KB) become Base64 data URIs
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger images are written to a dedicated folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });

        // Step 3: Save the document as Markdown
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

**Expected output:** Open `output.md` in any Markdown viewer. Small icons appear inline, e.g.:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

Larger pictures are referenced like:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

That’s exactly what you need to **embed images** while still keeping the file size manageable.

---

## Common Questions & Edge Cases

### What if an image is a JPEG instead of PNG?

The callback above always prefixes the URI with `image/png`. For JPEGs, you can inspect the first few bytes of `args.getData()` or use `args.getFileName()` to infer the correct MIME type:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### Can I change the size threshold?

Absolutely. The `10_000` byte limit is just an example. If you have a generous bandwidth budget, bump it up to 50 KB or more. Conversely, lower it if you need ultra‑light Markdown files.

### Does this work with tables or other Word objects?

Yes. Aspose.Words automatically converts tables, lists, and even footnotes to Markdown. The resource callback only intercepts images, so you don’t need extra code for other elements.

### What about non‑ASCII filenames?

The API safely encodes Unicode file names when writing to the `markdown_resources` folder. Just make sure your file system supports UTF‑8 (most modern OSes do).

---

## Pro Tips for a Smooth Conversion

- **Keep the output folder clean.** Run `Files.createDirectories` only once per conversion, or delete the folder before each run if you want a fresh start.
- **Validate the Markdown.** Tools like `markdownlint` can catch stray characters introduced by malformed Base64 strings.
- **Version lock Aspose.Words.** A specific version ensures your code continues to work even after a major release changes default behavior.
- **Use a .gitignore** entry for `markdown_resources/

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}