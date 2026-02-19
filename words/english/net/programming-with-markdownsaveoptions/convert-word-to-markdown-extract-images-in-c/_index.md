---
category: general
date: 2026-02-18
description: Convert Word to Markdown and extract images from docx using Aspose.Words.
  Learn how to generate markdown from word with a complete C# example.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- generate markdown from word
- how to convert docx to markdown
language: en
og_description: Convert Word to Markdown and extract images from docx with Aspose.Words.
  This guide shows how to generate markdown from word step‑by‑step.
og_title: Convert Word to Markdown – Extract Images in C#
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: Convert Word to Markdown – Extract Images in C#
url: /net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convert Word to Markdown – Extract Images in C#

Ever wondered how to **convert Word to Markdown** while pulling every picture out of a `.docx` file? You're not the only one. Many developers hit a wall when they need a clean markdown version of a contract, a blog post, or a technical spec that was originally authored in Word. The good news? With Aspose.Words for .NET you can do it in a few lines of code, and you’ll end up with a markdown file *plus* a folder full of the original images.

In this tutorial we’ll walk through a full, ready‑to‑run C# program that **generates markdown from Word**, extracts images from docx, and saves everything to disk. By the end you’ll know exactly how to **convert docx to markdown**, how to **extract images from docx**, and how to tweak the process for your own projects.

## What You’ll Need

- **Aspose.Words for .NET** (v23.10 or later). You can grab a free trial NuGet package with `Install-Package Aspose.Words`.
- .NET 6+ SDK (any recent version works fine).
- A sample `input.docx` that contains at least one picture.
- A folder where you want the markdown and image assets to live.

No other third‑party libraries are required. The code below includes every `using` directive you need, so you can copy‑paste it into a console app and hit **F5**.

![Convert Word to Markdown example](/images/convert-word-to-markdown.png "convert word to markdown")

*Image alt text: convert word to markdown illustration showing a Word file turning into a Markdown file with images.*

---

## Step 1: Load the Source Word Document

The first thing is to point Aspose.Words at the file you want to transform. Think of `Document` as the gateway to everything inside the `.docx`—text, tables, images, you name it.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 👉 Step 1: Load the Word document that contains images.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document document = new Document(inputPath);
```

> **Why this matters:** Loading the document once keeps memory usage low and lets the library inspect the internal package structure, which is essential for later extracting images.

---

## Step 2: Tell Aspose.Words How to Save as Markdown

Aspose.Words ships with a `MarkdownSaveOptions` class. It lets you control everything from line endings to the folder where external resources (like images) land.

```csharp
        // 👉 Step 2: Configure Markdown save options with a resource‑saving callback.
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
        {
            // The callback fires for each external resource (e.g., an image) that needs a file.
            ResourceSavingCallback = new ResourceSavingCallback(args =>
            {
                // 👉 Step 3 inside the callback: decide where and how to store each image.
                string resourceFolder = @"YOUR_DIRECTORY\markdown-resources";
                Directory.CreateDirectory(resourceFolder); // creates if it doesn’t exist

                // Give each image a unique name to avoid collisions.
                string uniqueFileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
                args.FileName = Path.Combine(resourceFolder, uniqueFileName);

                // Optional: you could compress PNGs here by manipulating args.Stream.
            })
        };
```

> **Why a callback?** The `ResourceSavingCallback` gives you full control over the file name and location of each extracted image. Without it, Aspose would dump everything into the same folder with generic names, which can be messy for larger projects.

---

## Step 3: Save the Document as Markdown

Now that the options are set, saving is a one‑liner. The library does the heavy lifting: it converts paragraphs, headings, lists, tables, and—thanks to the callback—writes each picture to the folder you specified.

```csharp
        // 👉 Step 4: Save the document as a Markdown file.
        string outputPath = @"YOUR_DIRECTORY\output.md";
        document.Save(outputPath, markdownOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputPath}");
        Console.WriteLine($"Images extracted to: {Path.GetDirectoryName(outputPath)}\\markdown-resources");
    }
}
```

### Expected Result

- `output.md` contains markdown syntax (e.g., `![Image](markdown-resources/img_1234.png)`).
- `markdown-resources` folder holds every image from the original Word file, each named uniquely.

Open `output.md` in any markdown viewer (VS Code, GitHub, or a static site generator) and you should see the text and images identical to the original Word layout—just in a lightweight, web‑friendly format.

---

## Step 4: Common Variations & Edge Cases

### 4.1 Handling Existing Resource Folders

If you run the conversion multiple times, you might end up with stale images. A quick guard clause can clean the folder before each run:

```csharp
if (Directory.Exists(resourceFolder))
{
    foreach (var file in Directory.GetFiles(resourceFolder))
        File.Delete(file);
}
else
{
    Directory.CreateDirectory(resourceFolder);
}
```

### 4.2 Changing Image Formats

Sometimes you need all images as JPEGs for web optimisation. Inside the callback you can re‑encode the stream:

```csharp
using (var img = System.Drawing.Image.FromStream(args.Stream))
{
    var jpegStream = new MemoryStream();
    img.Save(jpegStream, System.Drawing.Imaging.ImageFormat.Jpeg);
    jpegStream.Position = 0;
    args.Stream = jpegStream;
    args.FileName = Path.ChangeExtension(args.FileName, ".jpg");
}
```

> **Pro tip:** `System.Drawing.Common` works on Windows; on Linux/macOS you might prefer `ImageSharp` for cross‑platform safety.

### 4.3 Preserving Table Styles

If your Word doc relies heavily on table formatting, you can tweak `MarkdownSaveOptions`:

```csharp
markdownOptions.ExportTableColumnWidths = true;   // keeps column widths
markdownOptions.ExportTableBorders = true;       // adds markdown border syntax
```

### 4.4 Using a Different Output Directory

The `Save` method accepts any absolute or relative path. For CI pipelines you might point to a temporary build folder:

```csharp
document.Save(Path.Combine(Path.GetTempPath(), "doc.md"), markdownOptions);
```

---

## Frequently Asked Questions

**Q: Does this work with `.doc` (binary) files?**  
A: Yes. `new Document("file.doc")` automatically detects the format, so the same code handles both `.doc` and `.docx`.

**Q: What if the Word file contains embedded SVG images?**  
A: Aspose.Words extracts them as their original format. If you need raster versions, you’ll have to convert the SVG stream inside the callback (e.g., using `Svg.Skia`).

**Q: Can I skip the image extraction altogether?**  
A: Set `markdownOptions.ExportImagesAsBase64 = true;` to embed images directly in the markdown using data URIs—useful for single‑file README generation.

---

## Recap & Next Steps

We’ve just covered the full **convert word to markdown** workflow:

1. Load the `.docx`.
2. Configure `MarkdownSaveOptions` with a `ResourceSavingCallback`.
3. Save the document, letting the callback write each picture to a dedicated folder.

That’s the entire solution in under 50 lines of C#.  

If you’re ready to take it further, consider:

- **Generating a static site**: Feed the markdown into a generator like Hugo or Jekyll.
- **Batch processing**: Wrap the code in a `foreach` loop to handle dozens of files automatically.
- **Advanced image handling**: Resize, watermark, or convert images on the fly using the callback.

Feel free to experiment—swap out the callback logic, tweak save options, or integrate this into a larger document‑pipeline. The sky’s the limit, and now you have a solid foundation for any **generate markdown from word** project.

Happy coding, and may your markdown always be clean and your images always found!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}