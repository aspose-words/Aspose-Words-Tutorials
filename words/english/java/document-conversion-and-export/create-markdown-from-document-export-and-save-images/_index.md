---
category: general
date: 2026-02-18
description: Create markdown from document with easy steps to export document to markdown
  and save images to subfolder. Learn how to save document as markdown in C#.
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: en
og_description: Create markdown from document in C# and learn how to export document
  to markdown while saving images to a subfolder. Follow the step‑by‑step guide.
og_title: Create markdown from document – Export and save images
tags:
- C#
- Aspose.Words
- Markdown export
title: Create markdown from document – Export and save images
url: /java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create markdown from document – Export and save images

Ever needed to **create markdown from document** but weren’t sure how to keep the embedded pictures tidy? You’re not alone. In many projects we generate reports, manuals, or blog drafts programmatically, and the last thing we want is a mess of image files scattered across the output folder.  

In this tutorial we’ll walk through a complete, ready‑to‑run solution that **exports document to markdown**, stores every image in a dedicated *md‑resources* sub‑folder, and finally **saves document as markdown** using the Aspose.Words for .NET API. By the end you’ll have a single method you can drop into any C# codebase, plus a handful of tips for handling edge cases.

> **Quick glance:**  
> • Set up `MarkdownSaveOptions`  
> • Provide a `IResourceSavingCallback` that redirects images to a subfolder  
> • Call `Document.Save` with the configured options  

If you’re curious about why we choose a callback instead of post‑processing, keep reading – the reasoning is explained step by step.

---

## Prerequisites

- .NET 6.0 or later (the code works with .NET Framework 4.7+ as well)  
- Aspose.Words for .NET (NuGet package `Aspose.Words`)  
- A source `Document` object (could be a .docx, .pdf, .rtf, etc.)  

No additional libraries are required; the callback API is built into Aspose.Words.

---

## Step 1: Create markdown from document – configure save options

The first thing we do is instantiate `MarkdownSaveOptions`. This object tells Aspose.Words how the conversion should behave, such as which Markdown flavor to use, whether to embed images as Base64, and where to place the generated files.

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **Why this matters:**  
> Without explicitly creating `MarkdownSaveOptions`, the library falls back to default settings that embed images directly into the Markdown file as Base64 strings. That makes the file huge and defeats the purpose of having a clean *images* folder.

---

## Step 2: Export document to markdown and define resource handling

Now we tell the saver **where** to put each image. The `IResourceSavingCallback` interface gives us a hook that fires for every resource (image, SVG, etc.) discovered during the export. Inside the callback we:

1. Ensure the target folder exists (`md-resources/`).  
2. Set `OutputFileName` to the folder plus the original resource name.  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **Common question:** *What if I want to embed images instead of saving them?*  
> Just skip the callback or set `args.OutputFileName = null;` – the saver will embed the image as a Base64 string automatically.

> **Edge case:** Some older documents contain duplicate image names. The callback above will overwrite the previous file. To avoid that, you could append a GUID:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## Step 3: Save document as markdown and verify saved images

With the options fully configured, the final call is a one‑liner that writes the Markdown file and the associated images to disk.

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

If everything goes well you’ll see:

- `MyReport.md` – the Markdown representation of your source document.  
- `md-resources/` – a folder next to the .md file containing every extracted image (e.g., `image001.png`, `image002.jpg`).  

**Sample Markdown snippet** (auto‑generated by Aspose.Words):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **Pro tip:** Open the generated `.md` file in VS Code or any Markdown previewer; the images should render instantly because the relative paths match the folder structure.

---

## Full, runnable example

Below is a self‑contained console program you can paste into a new .NET project and run. It creates a simple Word document, adds an image, and then **creates markdown from document** while storing the image in a subfolder.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**What you should see** after running:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

Open `ExportedDoc.md` – the image reference will point to `md-resources/sample-image.png`, and the picture will display correctly in any Markdown viewer.

---

## Frequently asked variations

| Scenario | How to adapt the code |
|----------|----------------------|
| **Skip image export** (embed as Base64) | Omit `ResourceSavingCallback` entirely, or set `args.OutputFileName = null;` inside the callback. |
| **Change image format** (e.g., all PNG) | Inside the callback, modify `args.ResourceFileName` and optionally convert the stream before writing. |
| **Custom folder name** | Replace `"md-resources/"` with any relative or absolute path you prefer. |
| **Multiple documents in a batch** | Loop over a collection of `Document` objects, reusing the same `MarkdownSaveOptions` instance (just ensure the folder is cleared or uniquely named per run). |

---

## Conclusion

We’ve just shown you **how to create markdown from document**, **export document to markdown**, and **save images to subfolder** using a clean, callback‑driven approach. The key takeaways are:

- Use `MarkdownSaveOptions` to gain fine‑grained control over the export.  
- Implement `IResourceSavingCallback` to direct images into a dedicated folder, keeping your Markdown tidy.  
- The same pattern works for other resource types (SVG, audio) – just inspect `args.ResourceType`.  

Next, you might explore **saving document as markdown** with custom heading styles, or integrate this routine into an ASP.NET Web API that returns a ZIP containing the `.md` file and its resources. Either way, the building blocks are now in your toolbox.

Got questions, or spotted a corner case we didn’t cover? Drop a comment below, and happy coding!

---

![create markdown from document example](placeholder.png "create markdown from document example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}