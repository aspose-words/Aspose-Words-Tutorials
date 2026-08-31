---
category: general
date: 2026-01-03
description: Convert Word to Markdown and embed images as base64 in one go. Learn
  how to save Word as markdown, generate markdown from Word, and use base64 image
  data uri.
draft: false
keywords:
- convert word to markdown
- embed images as base64
- save word as markdown
- base64 image data uri
- generate markdown from word
language: en
og_description: Convert Word to Markdown and embed images as base64 data URIs. This
  step‑by‑step tutorial shows how to save Word as markdown and generate markdown from
  Word.
og_title: Convert Word to Markdown – Base64 Image Embedding Guide
tags:
- Aspose.Words
- C#
- Markdown
title: Convert Word to Markdown – Embed Images as Base64
url: /net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convert Word to Markdown – Embed Images as Base64

Ever needed to **convert Word to markdown** but kept stumbling over the images? You're not the only one. Word loves to store pictures as separate files, while markdown prefers those little `data:image/...;base64,` strings that keep everything tidy in a single file.  

In this tutorial we’ll walk through a complete, ready‑to‑run solution that **saves Word as markdown**, **embeds images as base64**, and even shows you how to **generate markdown from Word** using Aspose.Words for .NET. By the end, you’ll have a single `.md` file that renders exactly like the original document—no external image folders required.

## What You’ll Need

- **.NET 6.0 or later** (anything that can reference a NuGet package)
- **Aspose.Words for .NET** (the free trial works fine for testing)
- A simple `.docx` file with a few pictures (we’ll call it `input.docx`)
- Your favorite IDE (Visual Studio, Rider, VS Code—pick what you like)

If you already have those, great—let’s jump in. If not, installing the NuGet package is a single line:

```bash
dotnet add package Aspose.Words
```

## Step 1: Load the Word Document — the starting point for **convert word to markdown**

First we need to bring the `.docx` into memory. This is where the conversion magic begins.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file that contains the images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **Why this matters:**  
> Loading the document gives Aspose full access to the text, styles, and every embedded resource. Without this step, there’s nothing to convert.

## Step 2: Set Up MarkdownSaveOptions with a Resource‑Saving Callback

Aspose lets you intercept every resource (like images) that would normally be written to disk. By providing a custom `IResourceSavingCallback`, we can replace the default file‑based saving with a **base64 image data uri**.

```csharp
// Configure Markdown save options so that images become Base64 URIs.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceHandler()
};
```

### The Custom Handler – Turning images into Base64

Below is the full implementation. Notice how we check `args.ResourceType == ResourceType.Image` and then:

1. Write the image to a `MemoryStream`.
2. Convert the byte array to a Base64 string.
3. Build a `data:image/jpeg;base64,` URI and assign it to `args.Uri`.

```csharp
// Custom handler that converts each image resource to a Base64 data URI.
class MyResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process images – leave other resources untouched.
        if (args.ResourceType == ResourceType.Image)
        {
            // Prepare an in‑memory stream for the image.
            using (MemoryStream ms = new MemoryStream())
            {
                // Save the image using default JPEG options.
                args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                // Build the Base64 data URI.
                string base64 = Convert.ToBase64String(ms.ToArray());
                args.Uri = $"data:image/jpeg;base64,{base64}";
                // No need to keep the stream open after we set the URI.
                args.KeepResourceStreamOpen = false;
            }
        }
    }
}
```

> **Pro tip:** If your source Word uses PNGs, swap `ImageSaveOptions.DefaultJpeg` with `ImageSaveOptions.DefaultPng` and change the MIME type accordingly (`image/png`).

## Step 3: Save the Document as Markdown – the final **save word as markdown** step

Now that the callback is ready, the actual saving is a one‑liner.

```csharp
// Save the document to a Markdown file. Images are already embedded.
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

When you open `output.md` in any markdown viewer (VS Code preview, GitHub, etc.), you’ll see the text exactly as in the original Word file, and the pictures will appear inline without any separate image files.

## Expected Output

```markdown
# Sample Title

Here’s a paragraph that originally lived in Word.

![Embedded Image](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhU...
```

The `![Embedded Image]` line is a **base64 image data uri**—the whole image is encoded right there. No extra folders, no broken links.

## Edge Cases & How to Handle Them

| Situation | What to Do |
|-----------|------------|
| **Large Images** – Base64 inflates size by ~33% | Consider resizing before conversion: `args.ResourceData.Save(ms, new ImageSaveOptions { ImageResolution = 72 })`. |
| **Non‑JPEG Images** (PNG, GIF) | Detect the original format via `args.ResourceData.ImageType` and set the correct MIME type (`image/png`, `image/gif`). |
| **Very Long Documents** (hundreds of images) | Keep an eye on memory usage; you can stream each image to disk temporarily if the process runs out of RAM. |
| **Need Separate Image Files** (e.g., for a static site) | Return `false` from the callback for images you want to keep as files, and let Aspose write them to a folder. |

## Common Questions (Answered Up Front)

- **Does this work with .doc files?** Yes—Aspose.Words can load legacy `.doc` files the same way you load `.docx`. Just point `new Document("myfile.doc")` at it.
- **What about tables and footnotes?** They are fully supported by the Markdown exporter. Tables become markdown tables; footnotes become inline references.
- **Can I change the markdown flavor?** `MarkdownSaveOptions` has a `MarkdownVersion` property (CommonMark, GitHub, etc.). Set it before saving if you need a specific syntax.

## Full, Ready‑to‑Run Sample

Below is the complete program you can copy‑paste into a console app. It includes all using statements, the handler class, and error handling.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // 1️⃣ Load the source Word document.
                Document doc = new Document("YOUR_DIRECTORY/input.docx");

                // 2️⃣ Prepare Markdown options with our custom image handler.
                MarkdownSaveOptions options = new MarkdownSaveOptions
                {
                    ResourceSavingCallback = new MyResourceHandler()
                };

                // 3️⃣ Save as Markdown – images become Base64 URIs.
                string outputPath = "YOUR_DIRECTORY/output.md";
                doc.Save(outputPath, options);

                Console.WriteLine($"✅ Success! Markdown saved to {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
            }
        }
    }

    // Custom callback that embeds images as Base64 data URIs.
    class MyResourceHandler : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType == ResourceType.Image)
            {
                using (MemoryStream ms = new MemoryStream())
                {
                    // Preserve original format if you prefer PNG/GIF.
                    args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                    string base64 = Convert.ToBase64String(ms.ToArray());
                    args.Uri = $"data:image/jpeg;base64,{base64}";
                    args.KeepResourceStreamOpen = false;
                }
            }
        }
    }
}
```

Run the program, open the generated `output.md`, and you’ll see a perfect markdown replica of your Word file—**convert word to markdown** has never been simpler.

## Recap

We started with the problem of **convert word to markdown** while keeping images inline. By loading the document, configuring a `MarkdownSaveOptions` callback, and saving the file, we achieved a clean **save word as markdown** solution that produces **base64 image data uri** strings. You now also know how to **embed images as base64**, handle edge cases, and tweak the process for different image types.

## What’s Next?

- **Generate HTML instead of markdown** – swap `MarkdownSaveOptions` for `HtmlSaveOptions` and reuse the same callback.
- **Batch convert multiple files** – wrap the logic in a `foreach` loop over a folder.
- **Integrate into a CI pipeline** – automate documentation generation for static sites.

Feel free to experiment, tweak the image quality, or even add your own custom resource handling (e.g., uploading images to a CDN and inserting the URL). The sky’s the limit when you combine Aspose.Words with a little C# ingenuity.

Happy coding, and may your markdown always render perfectly! 

![Diagram showing convert word to markdown flow – embed images as base64](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHJlY3Qgd2lkdGg9IjYwMCIgaGVpZ2h0PSI0MDAiIGZpbGw9IiNmZmYiIHN0cm9rZT0iI2NjYyIgLz48dGV4dCB4PSI1MCIgeT0iMjAwIiBmb250LXNpemU9IjM2IiBmaWxsPSIjMDAwIj5JbWFnZSBJbWFnZSBJbWFnZSBJbWFnZTwvdGV4dD48L3N2Zz4= "convert word to markdown flow diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}