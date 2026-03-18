---
category: general
date: 2026-03-17
description: Convert Word to Markdown in C# while extracting images from DOCX. Learn
  how to extract images, set up callbacks, and save markdown with an assets folder.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- how to convert docx
language: en
og_description: Convert Word to Markdown in C# and learn how to extract images from
  DOCX. Step‑by‑step code, explanations, and tips for a smooth conversion.
og_title: Convert Word to Markdown & Extract Images from DOCX (C#) – Full Guide
tags:
- Aspose.Words
- C#
- Markdown
- Document Conversion
title: Convert Word to Markdown & Extract Images from DOCX (C#)
url: /net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-from-docx-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convert Word to Markdown & Extract Images from DOCX (C#)

Ever needed to **convert Word to Markdown** but got stuck on the images that magically disappear? You're not the only one. In many real‑world projects—think static site generators, documentation pipelines, or headless CMSes—you need the markdown text **and** the original pictures, neatly tucked away in an *assets* folder.  

In this tutorial you’ll see exactly **how to convert docx** to markdown **while extracting images** using Aspose.Words for .NET. We'll walk through setting up a resource‑saving callback, handling edge cases like duplicate filenames, and ending up with a clean folder structure ready for your static site builder.  

## What You’ll Learn

- Load a `.docx` file and prepare it for conversion.  
- Implement `IResourceSavingCallback` to **extract images from DOCX**.  
- Configure `MarkdownSaveOptions` so the markdown references the assets correctly.  
- Run the code and verify that both the `.md` file and the image folder are generated as expected.  

**Prerequisites** – you need .NET 6+ (or .NET Framework 4.7.2+) and an Aspose.Words license (the free trial works for this demo). A basic grasp of C# and file I/O will make things smoother, but the guide is self‑contained.

![Convert Word to Markdown folder layout](https://example.com/convert-word-to-markdown.png "Convert Word to Markdown folder layout")

*The folder layout after conversion – the markdown file lives beside an `assets` folder that holds every extracted image.*

---

## Step 1: Load the Source Document (convert word to markdown)

The first thing we do is read the `.docx` you want to turn into markdown. Aspose.Words abstracts away the low‑level OPC format, so a single line gets the job done.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

// Adjust these paths to match your environment.
string inputPath  = Path.Combine("YOUR_DIRECTORY", "input.docx");
string outputDir  = Path.Combine("YOUR_DIRECTORY", "output");

// Ensure the output folder exists.
Directory.CreateDirectory(outputDir);

// Load the DOCX file.
Document document = new Document(inputPath);
```

*Why this matters:* Loading the document early gives us a `Document` object that holds both the textual content **and** the embedded resources (images, charts, etc.). Without this step you can't **how to extract images** later on.

---

## Step 2: Create a Callback to **how to extract images** from the DOCX

Aspose.Words calls your `IResourceSavingCallback` every time it needs to write a resource (like an image). By providing our own implementation we decide **where** the file lands and **how** the markdown will reference it.

```csharp
/// <summary>
/// Saves each extracted resource (image, video, etc.) into an "assets" sub‑folder
/// and rewrites the markdown reference to point at that relative path.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _outputDirectory;

    public MyMarkdownResourceCallback(string outputDirectory)
    {
        _outputDirectory = outputDirectory;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the assets folder path.
        string assetsFolder = Path.Combine(_outputDirectory, "assets");
        Directory.CreateDirectory(assetsFolder);

        // 2️⃣ Resolve potential filename collisions.
        string safeFileName = GetUniqueFileName(assetsFolder, args.ResourceFileName);

        // 3️⃣ Write the resource stream to disk.
        string assetPath = Path.Combine(assetsFolder, safeFileName);
        using (FileStream fs = new FileStream(assetPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // 4️⃣ Tell the markdown writer the *relative* path it should embed.
        args.ResourceFileName = Path.Combine("assets", safeFileName);
        args.KeepResourceStreamOpen = false; // we already closed it
    }

    // Helper: ensure we don't overwrite an existing file.
    private string GetUniqueFileName(string folder, string originalName)
    {
        string filePath = Path.Combine(folder, originalName);
        if (!File.Exists(filePath))
            return originalName;

        string nameWithoutExt = Path.GetFileNameWithoutExtension(originalName);
        string ext = Path.GetExtension(originalName);
        int counter = 1;

        while (File.Exists(filePath))
        {
            string candidate = $"{nameWithoutExt}_{counter}{ext}";
            filePath = Path.Combine(folder, candidate);
            counter++;
        }

        return Path.GetFileName(filePath);
    }
}
```

**Key points**  

- **Why an assets sub‑folder?** Keeping images separate from the `.md` file mirrors the layout most static site generators expect.  
- **Collision handling** prevents the dreaded “file already exists” exception when the same image appears multiple times.  
- Setting `args.KeepResourceStreamOpen = false` signals Aspose that we’ve taken care of the stream, avoiding memory leaks.

---

## Step 3: Wire the Callback into **MarkdownSaveOptions**

Now we tell Aspose.Words to use our callback whenever it writes a resource. This is the core of **how to convert docx** while preserving its media.

```csharp
// Instantiate the callback with the output directory.
var resourceCallback = new MyMarkdownResourceCallback(outputDir);

// Configure markdown options.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // The callback does the heavy lifting for image extraction.
    ResourceSavingCallback = resourceCallback,

    // Optional: make the markdown more GitHub‑friendly.
    ExportImagesAsBase64 = false, // we want separate files, not embedded data URIs.
    ExportHeadersFooters = true,
    ExportDocumentProperties = false
};
```

*Why we set `ExportImagesAsBase64 = false`*: Base64‑encoded images bloat the markdown file and defeat the purpose of having a clean `assets` folder. By disabling it, the markdown will contain a simple `![](assets/image.png)` reference.

---

## Step 4: Save the Document as Markdown

With everything prepared, the final step is a one‑liner that produces both the `.md` file and the images.

```csharp
string markdownPath = Path.Combine(outputDir, "output.md");

// Save the document.
document.Save(markdownPath, markdownOptions);
Console.WriteLine($"✅ Conversion complete! Markdown saved to: {markdownPath}");
Console.WriteLine($"📁 Extracted images are in: {Path.Combine(outputDir, "assets")}");
```

**What you should see**  

- `output.md` containing markdown text where each image tag points to `assets/<image_name>`.  
- An `assets` folder populated with PNG, JPEG, or GIF files that were originally embedded in `input.docx`.  

Open `output.md` in any markdown viewer (VS Code, GitHub, MkDocs) and you’ll see the images rendered exactly as they appeared in the Word document.

---

## Handling Common Pitfalls (FAQ)

### What if the DOCX contains duplicate image names?
Our `GetUniqueFileName` helper appends an incremental suffix (`image_1.png`, `image_2.png`, …) so no file gets overwritten.

### Do I need a license for Aspose.Words?
A trial works fine for experimentation, but for production you should purchase a license to remove the evaluation watermark and get full performance.

### Can I convert multiple Word files in a batch?
Absolutely. Wrap the loading and saving code in a `foreach (var file in Directory.GetFiles(sourceFolder, "*.docx"))` loop, reusing the same `MyMarkdownResourceCallback` instance (or create a new one per file if you want isolated asset folders).

### What about non‑image resources (e.g., embedded PDFs)?
The callback receives **any** resource type. You can inspect `args.ResourceType` and decide whether to keep, ignore, or rename them.

### Is this approach compatible with .NET Core?
Yes. The code above targets .NET 6, but you can downgrade to .NET Framework 4.7.2 by adjusting the project file. Aspose.Words supports both runtimes.

---

## Pro Tips & Best Practices

- **Keep the assets folder tidy** – after a batch conversion, run a quick script to delete zero‑byte files that may have been created by empty placeholders.  
- **Use meaningful filenames** – if you need human‑readable image names, extract the original `AltText` (if present) from `args.ResourceFileName` and incorporate it.  
- **Version control** – store only the markdown in your repo; the assets folder can be generated as part of the CI pipeline, keeping the repository lightweight.  
- **Performance** – for huge documents, consider streaming the output by setting `markdownOptions.SaveFormat = SaveFormat.Markdown;` and writing to a `MemoryStream` first.

---

## Full Working Example (Copy‑Paste Ready)

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

/// <summary>
/// Demonstrates converting a DOCX to Markdown while extracting images into an assets folder.
/// </summary>
class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1️⃣ Paths – adjust these to your environment.
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        string outputDir = Path.Combine("YOUR_DIRECTORY", "output");
        Directory.CreateDirectory(outputDir);

        // -----------------------------------------------------------------
        // 2️⃣ Load the source document.
        // -----------------------------------------------------------------
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // 3️⃣ Set up the resource‑saving callback.
        // -----------------------------------------------------------------
        var callback = new MyMarkdownResourceCallback(outputDir);

        // -----------------------------------------------------------------
        // 4️⃣ Configure Markdown options.
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = callback,
            ExportImagesAsBase64 = false,
            ExportHeadersFooters = true,
            ExportDocumentProperties = false
        };

        // -----------------------------------------------------------------
        // 5️⃣ Save as Markdown.
        // -----------------------------------------------------------------
        string markdownFile = Path

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}