---
category: general
date: 2026-03-25
description: Convert DOCX to Markdown quickly while extracting images from Word using
  Aspose.Words. Learn step‑by‑step with full code.
draft: false
keywords:
- convert docx to markdown
- extract images from word
language: en
og_description: Convert DOCX to Markdown and extract images from Word with Aspose.Words.
  Follow this complete tutorial for a ready‑to‑run solution.
og_title: Convert DOCX to Markdown in C# – Step‑by‑Step Guide
tags:
- Aspose.Words
- C#
- Markdown
title: Convert DOCX to Markdown in C# – Complete Guide
url: /net/programming-with-markdownsaveoptions/convert-docx-to-markdown-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convert DOCX to Markdown with Aspose.Words

Ever needed to **convert DOCX to markdown** but weren’t sure how to keep the embedded pictures intact? You’re not alone—many developers hit this snag when they try to move Word content into a static‑site generator or a documentation repo.  
The good news is that Aspose.Words for .NET can do the heavy lifting for you, and with a tiny callback you can also **extract images from Word** files at the same time.

In this tutorial we’ll walk through a real‑world example that loads a `.docx`, saves it as a Markdown file, and writes every image to a dedicated folder. By the end you’ll have a ready‑to‑run console app that you can drop into any .NET project.

> **Pro tip:** If you only need the text and don’t care about images, you can skip the `ResourceSavingCallback` entirely – the code will still produce clean Markdown.

## What You’ll Need

- **Aspose.Words for .NET** (the latest version, e.g., 24.12). You can grab it from NuGet: `Install-Package Aspose.Words`.
- **.NET 6.0** or later (the API works on .NET Framework as well, but .NET 6 gives you the best performance).
- A simple console project or any C# host you prefer.
- An input Word file (`input.docx`) that contains at least one picture so we can see the extraction in action.

That’s it—no extra libraries, no fiddly command‑line tools. Let’s dive in.

![convert docx to markdown example](images/convert-docx-to-markdown.png)

*Image alt text: convert docx to markdown example*

## Step 1 – Set Up the Project and Add Aspose.Words

To keep things tidy, create a fresh console app:

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

Open `Program.cs` and clear the auto‑generated code. We’ll paste the full solution later, but for now just make sure the project builds.

## Step 2 – Load the Source DOCX

The first thing we do is tell Aspose.Words to read the Word file. This operation is **fast**—the library parses the document structure without opening Word itself.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Path to your source document
string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Load the DOCX into a Document object
Document doc = new Document(inputPath);
```

Why do we wrap the path in `Path.Combine`? It makes the code portable across Windows, macOS, and Linux—something you’ll appreciate when you move the project to a CI pipeline.

## Step 3 – Configure Markdown Save Options with a Resource Callback

When you ask Aspose.Words to save as Markdown, it normally embeds images as Base64 strings. That’s fine for tiny icons, but for larger photos it blows up the file size. Instead, we attach a **resource‑saving callback** that writes each image to disk and updates the Markdown link.

```csharp
// Define where the Markdown and resources will live
string outputDir = Path.Combine("YOUR_DIRECTORY", "Output");
string resourcesDir = Path.Combine(outputDir, "Resources");

// Ensure directories exist
Directory.CreateDirectory(outputDir);
Directory.CreateDirectory(resourcesDir);

// Create Markdown options and plug in the callback
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver(resourcesDir)
};
```

Notice we pass `resourcesDir` into the callback’s constructor—this keeps the path logic out of the callback itself and makes the class reusable.

## Step 4 – Implement the Resource‑Saving Callback

The callback implements `IResourceSavingCallback`. For each image Aspose.Words wants to write, it hands us a `ResourceSavingArgs` object. We decide **where** to store the file, give it a unique name, and then tell the engine to skip its default saving behavior.

```csharp
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique, deterministic file name
        string ext = Path.GetExtension(args.FileName);          // e.g., ".png"
        string fileName = $"img_{args.Index}{ext}";            // img_0.png, img_1.jpg, …

        // Full path on disk
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Write the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown URI so it points to the saved image
        args.Uri = $"Resources/{fileName}";

        // Tell Aspose.Words we handled the saving
        args.Cancel = true;
    }
}
```

**Why this matters:** By setting `args.Uri` we control exactly how the image will be referenced in the resulting `.md` file. The relative path `Resources/img_0.png` works whether you open the Markdown in VS Code, GitHub, or a static‑site generator.

## Step 5 – Save the Document as Markdown

Now the final piece: ask Aspose.Words to write the Markdown file. The callback we wired up will fire for each image automatically.

```csharp
// Destination Markdown file
string markdownPath = Path.Combine(outputDir, "output.md");

// Perform the conversion
doc.Save(markdownPath, mdOptions);
```

When the line finishes, you’ll have:

- `output.md` – a clean Markdown representation of the original Word content.
- `Resources/` folder – containing every picture extracted from the DOCX.

## Full Working Example

Below is the **complete, copy‑paste‑ready** program. Replace `YOUR_DIRECTORY` with the absolute or relative path that holds your `input.docx`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // ------------------------------------------------------------
        // 1️⃣  Define paths
        // ------------------------------------------------------------
        string baseDir = Path.Combine(Environment.CurrentDirectory, "DemoFiles");
        string inputPath = Path.Combine(baseDir, "input.docx");
        string outputDir = Path.Combine(baseDir, "Output");
        string resourcesDir = Path.Combine(outputDir, "Resources");

        // Create folders if they don't exist
        Directory.CreateDirectory(outputDir);
        Directory.CreateDirectory(resourcesDir);

        // ------------------------------------------------------------
        // 2️⃣  Load the DOCX
        // ------------------------------------------------------------
        Document doc = new Document(inputPath);

        // ------------------------------------------------------------
        // 3️⃣  Prepare Markdown options with a resource callback
        // ------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyResourceSaver(resourcesDir)
        };

        // ------------------------------------------------------------
        // 4️⃣  Save as Markdown
        // ------------------------------------------------------------
        string markdownPath = Path.Combine(outputDir, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown file: {markdownPath}");
        Console.WriteLine($"Images folder: {resourcesDir}");
    }
}

// -----------------------------------------------------------------
// Callback that writes each image to the Resources folder
// -----------------------------------------------------------------
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create a deterministic file name like img_0.png
        string extension = Path.GetExtension(args.FileName);
        string fileName = $"img_{args.Index}{extension}";
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Persist the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown link to point to the saved image
        args.Uri = $"Resources/{fileName}";

        // Cancel default saving because we already wrote the file
        args.Cancel = true;
    }
}
```

### Expected Output

Open `Output/output.md` in any Markdown viewer and you should see something like:

```markdown
# My Sample Document

Here is a paragraph that came from Word.

![Image 1](Resources/img_0.png)

Another paragraph with **bold** text.
```

The `Resources` folder will contain `img_0.png`, `img_1.jpg`, etc., matching the images that were originally embedded in `input.docx`.

## Frequently Asked Questions (FAQ)

**Does this work with .doc files?**  
Yes. Aspose.Words can load `.doc`, `.docx`, `.rtf`, and many other formats. Just change the file extension in `inputPath`.

**What if I need absolute URLs for the images?**  
Replace `args.Uri = $"Resources/{fileName}";` with something like `args.Uri = $"https://mycdn.com/docs/{fileName}";`. The Markdown will then reference the remote location.

**Can I control image quality or format?**  
The callback receives the original image stream. If you want to convert PNG to JPEG, you could load the stream into `System.Drawing.Image`, re‑encode, and write the new bytes before setting `args.Uri`.

**Is the `ResourceSavingCallback` thread‑safe?**  
Aspose.Words invokes the callback sequentially for each resource, so

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}