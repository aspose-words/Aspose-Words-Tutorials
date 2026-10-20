---
category: general
date: 2026-04-28
description: Learn how to set a markdown image relative path when you convert Word
  to markdown, extract images from word, and create resources folder for exported
  images.
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: en
og_description: Set a markdown image relative path while you convert Word to markdown,
  extract images from word, and create resources folder for exported images.
og_title: markdown image relative path – Convert Word to Markdown
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: markdown image relative path – Convert Word to Markdown
url: /net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown image relative path – Convert Word to Markdown

Ever needed a **markdown image relative path** while you **convert Word to markdown**? You’re not alone. Most developers hit a snag when the generated Markdown points to images in a flat folder, breaking the relative link structure you expect in a static site or a GitHub repo.

In this tutorial we’ll walk through a complete, end‑to‑end solution that **extracts images from Word**, **creates a resources folder**, and rewrites the image references so they use a clean *markdown image relative path*. By the end you’ll have a ready‑to‑publish `.md` file and a neatly organized `Resources` directory containing every picture extracted from the original `.docx`.

> **What you’ll get:** a single C# program (no external scripts), a clear explanation of *why* each piece matters, and a handful of practical tips you can copy‑paste into your own projects.

---

## Prerequisites

Before we dive into code, make sure you have:

- **.NET 6.0** or later installed (you can also target .NET Framework 4.7+, but .NET 6 is the sweet spot for new projects).
- **Aspose.Words for .NET** (the latest NuGet package at the time of writing, version 23.12). Install it with:
  ```bash
  dotnet add package Aspose.Words
  ```
- A Word document that actually contains images—let’s call it `WithImages.docx`.
- A folder where you want the output markdown and the images to live, e.g. `C:\Projects\MarkdownExport`.

No additional libraries are required; everything else is handled by Aspose.Words.

---

## Step 1: Load the source Word document (the starting point for convert word to markdown)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*Why this matters:* Loading the document gives us access to the internal node tree, which includes the image parts we later need to **export images from docx**. If the load fails, none of the later steps will run, so double‑check the path and file permissions.

---

## Step 2: Configure `MarkdownSaveOptions` with a custom callback (the heart of create resources folder)

The `ResourceSavingCallback` lets us intervene each time Aspose.Words wants to write an image file. Inside the callback we’ll **create a Resources sub‑folder** and adjust the reference so the generated markdown uses a *markdown image relative path*.

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

Notice we passed `resourcesFolder` into the callback’s constructor—this keeps the folder path flexible and avoids hard‑coding strings throughout the code.

---

## Step 3: Implement the callback that **creates resources folder** and rewrites the path

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*Why this works:* `args.Stream` contains the raw image bytes. By copying it to a file inside our `Resources` folder we **export images from docx** safely. Then we replace `args.ResourceFileName` with a relative URL (`Resources/image.png`). When Aspose.Words later writes the markdown, it injects exactly that string, giving us the desired *markdown image relative path*.

---

## Step 4: Verify the generated Markdown (what the final output looks like)

Open `Doc.md` in any text editor. You should see something similar to:

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

The important part is that each image reference points to `Resources/...` – that’s the **markdown image relative path** we were after.

![markdown image relative path example](example.png "markdown image relative path example")

*Tip:* If you open the markdown in a viewer that respects relative links (VS Code preview, GitHub, or a static site generator), the pictures will render correctly without any additional configuration.

---

## Step 5: Common pitfalls and pro‑tips

| Issue | Why it happens | How to fix it |
|-------|----------------|---------------|
| Images end up in the root folder instead of `Resources` | The callback wasn’t attached or `args.ResourceFileName` wasn’t overwritten. | Double‑check that `ResourceSavingCallback` is set **before** calling `doc.Save`. |
| Filenames contain illegal characters | Word sometimes names images with spaces or Unicode symbols. | Use `Path.GetInvalidFileNameChars()` to sanitize `args.ResourceFileName` inside the callback. |
| Large documents take a long time to process | Each image is written synchronously. | Switch to asynchronous I/O (`await args.Stream.CopyToAsync(fileStream)`) if you’re on .NET 6+ and need performance. |
| Relative paths break when the markdown is moved | The path is relative to the markdown file location. | Keep `Doc.md` and the `Resources` folder together, or adjust the callback to use a different relative prefix (e.g., `../assets`). |

---

## Step 6: Extending the solution (what if you need more control?)

- **Multiple output formats:** Replace `MarkdownSaveOptions` with `HtmlSaveOptions` or `PdfSaveOptions` while keeping the same callback—Aspose.Words will invoke it for every image regardless of format.
- **Custom image naming:** If you want to rename images (e.g., `figure-01.png`), modify `args.ResourceFileName` inside the callback before you write the file.
- **Embedding images as Base64:** Set `args.ResourceFileName` to a data URI (`data:image/png;base64,...`) and skip the file write. This is handy for single‑file markdown exports.

---

## Conclusion

You now have a fully functional C# program that **converts Word to markdown**, **extracts images from word**, **creates a resources folder**, and guarantees a clean **markdown image relative path** for every picture. The code is self‑contained, works with the latest Aspose.Words version, and can be dropped into any .NET project with minimal effort.

Next steps? Try feeding the generated markdown into a static site generator like Hugo or Jekyll, or experiment with the callback to embed images directly as Base64 strings. If you run into edge cases—say, SVG images or unusually large files—refer back to the “Common pitfalls” table; a tiny tweak usually solves the problem.

Happy coding, and may your markdown always point to the right folder!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}