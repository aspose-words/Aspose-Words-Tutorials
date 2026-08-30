---
category: general
date: 2026-06-27
description: Aspose.Words for Java를 사용하여 docx를 markdown으로 변환합니다. 이미지를 base64로 삽입하고
  Word 문서를 손쉽게 markdown으로 내보내는 방법을 배워보세요.
draft: false
keywords:
- convert docx to markdown
- embed images as base64
- how to embed images markdown
- export word document to markdown
- convert docx to markdown with images
language: ko
og_description: Aspose.Words for Java를 사용하여 docx를 markdown으로 변환합니다. 이 튜토리얼에서는 이미지를
  base64로 삽입하고 Word 문서를 한 번의 흐름으로 markdown으로 내보내는 방법을 보여줍니다.
og_title: 임베디드 이미지가 포함된 docx를 마크다운으로 변환 – Java 가이드
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: convert docx to markdown using Aspose.Words for Java. Learn how to
    embed images as base64 and export Word document to markdown effortlessly.
  headline: convert docx to markdown with embedded images – Java guide
  type: TechArticle
- description: convert docx to markdown using Aspose.Words for Java. Learn how to
    embed images as base64 and export Word document to markdown effortlessly.
  name: convert docx to markdown with embedded images – Java guide
  steps:
  - name: Read the image file into a byte array (`Files.readAllBytes`).
    text: Read the image file into a byte array (`Files.readAllBytes`).
  - name: Encode with `Base64.getEncoder().encodeToString`.
    text: Encode with `Base64.getEncoder().encodeToString`.
  - name: 'Insert the data URI into your Markdown string: `![alt](data:image/png;base64,${base64})`.'
    text: 'Insert the data URI into your Markdown string: `![alt](data:image/png;base64,${base64})`.'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Conversion
title: 임베디드 이미지가 포함된 docx를 markdown으로 변환 – Java 가이드
url: /ko/java/document-conversion-and-export/convert-docx-to-markdown-with-embedded-images-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# docx를 markdown으로 변환하고 이미지 포함 – Java 가이드

Ever needed to **convert docx to markdown** but kept hitting a wall when images vanished or turned into broken links? You're not the only one. In many projects—static site generators, documentation pipelines, or quick‑look previews—preserving those pictures is a must, and the usual converters often drop them.  

Luckily, Aspose.Words for Java gives us a clean way to **embed images as base64** right inside the Markdown, so the output file is truly portable. In this guide we’ll walk through the whole process: loading a Word file, configuring the Markdown save options, handling image resources, and finally saving the result. By the end you’ll know exactly **how to embed images markdown** style and you’ll have a ready‑to‑run code snippet that you can drop into any Maven or Gradle project.

## What you’ll need

Before we dive in, make sure you have:

- Java 17 or newer (the API works with older versions too, but 17 is the sweet spot).
- Aspose.Words for Java library (you can grab the latest JAR from Maven Central: `com.aspose:aspose-words:23.12`).
- A `.docx` file you want to transform (we’ll call it `Report.docx`).
- A decent IDE (IntelliJ IDEA, Eclipse, or even VS Code with Java extensions).

No extra image‑processing tools are required—the library handles everything under the hood.

## Step 1: Load the Word document – **convert docx to markdown** foundation

The first thing we do is create a `Document` instance pointing at the source file. Think of this object as the in‑memory representation of your Word file, complete with paragraphs, tables, and of course, images.

```java
import com.aspose.words.*;

public class DocxToMarkdown {
    public static void main(String[] args) throws Exception {
        // Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/Report.docx");
        // … we’ll configure options next
    }
}
```

> **Pro tip:** If you’re reading the docx from a stream (e.g., an uploaded file), you can pass an `InputStream` to the `Document` constructor—perfect for web apps.

## Step 2: Configure MarkdownSaveOptions – **embed images as base64** magic

Aspose.Words ships with a `MarkdownSaveOptions` class that lets us tweak how the conversion behaves. The key to keeping images alive is the `IResourceSavingCallback`. Inside the callback we intercept every image stream, turn it into a Base64 string, and rewrite the resource name to a data URI.

```java
import java.io.ByteArrayOutputStream;
import java.util.Base64;
import com.aspose.words.*;

MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();

// Embed images directly as Base64 data URIs
markdownOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) throws Exception {
        // Only act on image resources
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Copy the image stream to a byte array
            ByteArrayOutputStream baos = new ByteArrayOutputStream();
            args.getStream().copyTo(baos);
            // Encode the bytes as Base64
            String base64 = Base64.getEncoder().encodeToString(baos.toByteArray());
            // Build a data URI (png assumed, adjust if needed)
            args.setResourceFileName("data:image/png;base64," + base64);
            // Close the original stream – we no longer need it
            args.setKeepResourceStreamOpen(false);
        }
    }
});
```

Why go through this extra step? Because **export word document to markdown** without a callback would dump images into a separate folder and reference them with relative paths. Those paths break once you move the Markdown file, especially in CI pipelines. By embedding the image as a Base64 string, the Markdown becomes a single, self‑contained artifact—perfect for GitHub READMEs or static‑site generators that don’t support external assets.

### Handling different image formats

The snippet above assumes PNG (`image/png`). If your source Word contains JPEGs, you can inspect the original content type:

```java
String mime = args.getContentType(); // e.g., "image/jpeg"
args.setResourceFileName("data:" + mime + ";base64," + base64);
```

That tiny tweak ensures the resulting Markdown renders correctly regardless of the original format.

## Step 3: Save the file – **export word document to markdown** final step

Now that the options are ready, we simply call `document.save`, passing the target path and the configured `MarkdownSaveOptions`. The library does the heavy lifting: it walks the document tree, converts paragraphs to Markdown syntax, and injects our Base64 images wherever they belong.

```java
// Save the document as Markdown with embedded Base64 images
document.save("YOUR_DIRECTORY/Report.md", markdownOptions);
System.out.println("Conversion complete! Check Report.md");
```

When you open `Report.md` in any Markdown viewer (VS Code, GitHub, typora, etc.), you’ll see the images rendered inline, no extra files needed.

## Step 4: Full, runnable example – **convert docx to markdown with images** in one place

Putting it all together, here’s the complete program you can copy‑paste, compile, and run:

```java
import com.aspose.words.*;
import java.io.*;
import java.util.Base64;

public class DocxToMarkdown {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/Report.docx");

        // 2️⃣ Set up Markdown save options with Base64 image embedding
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                if (args.getResourceType() == ResourceType.IMAGE) {
                    ByteArrayOutputStream baos = new ByteArrayOutputStream();
                    args.getStream().copyTo(baos);
                    String base64 = Base64.getEncoder().encodeToString(baos.toByteArray());
                    String mime = args.getContentType(); // Preserve original MIME type
                    args.setResourceFileName("data:" + mime + ";base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                }
            }
        });

        // 3️⃣ Save as Markdown – this is where we **export word document to markdown**
        document.save("YOUR_DIRECTORY/Report.md", markdownOptions);
        System.out.println("✅ convert docx to markdown with embedded images finished.");
    }
}
```

### Expected output

Open `Report.md` and you should see something like:

```markdown
# Sample Report

Here is an introductory paragraph.

![Image](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...==)

Another paragraph follows.
```

The long Base64 string represents the image data. Most editors truncate it in the UI, but the image renders perfectly when previewed.

## Common pitfalls and how to avoid them

| Issue | Why it happens | Fix |
|------|----------------|-----|
| Images appear as broken links | Callback didn’t fire because `ResourceType` check was missing. | Ensure `if (args.getResourceType() == ResourceType.IMAGE)` surrounds your logic. |
| Output file is huge | Base64 inflates data by ~33%. | Accept the trade‑off for portability, or switch to external images if size is a concern. |
| Wrong image format | Hard‑coded `image/png` for JPEGs. | Use `args.getContentType()` to preserve the original MIME type. |
| Out‑of‑memory for large docs | Loading a massive DOCX into memory. | Process the document in chunks or increase JVM heap (`-Xmx2g`). |

## When you need **how to embed images markdown** in other contexts

If you’re not using Aspose.Words but still want to embed Base64 images, the principle stays the same:

1. Read the image file into a byte array (`Files.readAllBytes`).
2. Encode with `Base64.getEncoder().encodeToString`.
3. Insert the data URI into your Markdown string: `![alt](data:image/png;base64,${base64})`.

The library just automates this for every image it encounters, saving you from writing a loop.

## Next steps – extending the conversion

Now that you’ve mastered **convert docx to markdown with images**, consider these upgrades:

- **Style preservation**: Use `HtmlSaveOptions` first, then convert HTML to Markdown with a tool like flexmark‑java for richer formatting.
- **Table handling**: Aspose already converts tables, but you can fine‑tune column alignment via `markdownOptions.setTableAlignment`.
- **Batch processing**: Wrap the above code in a directory scanner to convert dozens of reports automatically.
- **Integration with CI**: Add the JAR to your build pipeline and generate documentation on every commit.

Each of these ideas leans on the same core concepts we covered, so you’ll feel comfortable adapting the code.

## Conclusion

We’ve just walked through a complete, end‑to‑end solution for **convert docx to markdown** while ensuring every picture stays embedded as a Base64 string. The key steps—loading the document, configuring `MarkdownSaveOptions` with a custom `IResourceSavingCallback`, and saving the file—are straightforward, and the code works out‑of‑the‑box with Aspose.Words for Java.  

Armed with this knowledge, you can now automate documentation pipelines, generate portable Markdown reports, or simply keep a clean, single‑file version of your Word content. If you’re curious about further tweaks—like handling SVGs or customizing heading levels—explore the Aspose.Words API docs; they’re packed with examples that complement what we’ve built here.

Happy coding, and may your Markdown always stay image‑rich!  

![docx를 markdown으로 변환 다이어그램](convert-docx-to-markdown.png "docx를 markdown으로 변환")

---


## What Should You Learn Next?

다음에 배울 내용은?

- [How to Embed Images in Markdown When Converting DOCX](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [How to Export Markdown with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-markdown/)
- [Convert docx to markdown – Export Math Equations to LaTeX with Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}