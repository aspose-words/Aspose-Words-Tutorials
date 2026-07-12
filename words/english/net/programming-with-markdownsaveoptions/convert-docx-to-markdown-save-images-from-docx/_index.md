---
category: general
date: 2026-06-27
description: Convert docx to markdown and save images from docx using Aspose.Words.
  Learn how to extract images from Word file and export Word document as markdown.
draft: false
keywords:
- convert docx to markdown
- save images from docx
- extract images from word file
- export word document as markdown
language: en
og_description: Convert docx to markdown and save images from docx. This guide shows
  how to extract images from Word file and export Word document as markdown.
og_title: Convert docx to markdown & save images from docx
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  headline: Convert docx to markdown & save images from docx
  type: TechArticle
- description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  name: Convert docx to markdown & save images from docx
  steps:
  - name: How the code works
    text: '- **Loading the document** (`new Document(inputPath)`) gives us an in‑memory
      representation of the Word file, complete with all its parts—paragraphs, tables,
      and **images**. - **`MarkdownSaveOptions`** is where the magic happens. By attaching
      a `ResourceSavingCallback`, we gain full control over eve'
  - name: Quick sanity check
    text: '- Does the Markdown file open without errors in VS Code’s preview pane?
      ✅ - Are all pictures displayed when you view the file on GitHub? ✅ - Did the
      `Images` directory contain one file per picture from the original `.docx`? ✅'
  - name: What’s next?
    text: '- **Style the Markdown** – add a front‑matter block for Jekyll or Hugo.
      - **Automate the pipeline** – embed this code in an Azure DevOps or GitHub Action
      step. - **Handle tables and footnotes** – explore other `MarkdownSaveOptions`
      flags like `ExportTableBorderStyles`.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Markdown
- Word
title: Convert docx to markdown & save images from docx
url: /net/programming-with-markdownsaveoptions/convert-docx-to-markdown-save-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convert docx to markdown & save images from docx

Ever wondered how to **convert docx to markdown** without losing the pictures embedded in your Word file? You're not alone—developers often need a clean Markdown version of a report while still keeping every diagram, logo, or screenshot intact.

In this tutorial we'll walk through a complete, ready‑to‑run example that **converts a .docx to Markdown**, **saves images from docx** to a folder of your choosing, and shows you how to **extract images from Word file** using the powerful Aspose.Words library. By the end you’ll also know how to **export Word document as markdown** in a single line of code.

## What you’ll need

- .NET 6+ (or .NET Framework 4.7.2+) installed on your machine  
- A NuGet reference to `Aspose.Words` (free trial works fine)  
- A sample `input.docx` that contains at least one picture  
- An IDE you like—Visual Studio, Rider, or even VS Code will do  

No additional third‑party tools, no fiddly command‑line gymnastics. Just straight C# code.

## Convert docx to markdown – Overview

The core idea is simple:

1. Load the source Word document.  
2. Tell Aspose.Words how you want external resources (like images) to be handled.  
3. Save the document as Markdown, letting the library do the heavy lifting.

Below is the **full, runnable program**. Feel free to copy‑paste it into a new console project and hit `Ctrl+F5`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load the source document that contains images
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // Step 2: Configure Markdown save options with a custom callback
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This callback runs for each external resource (images, CSS, etc.)
            ResourceSavingCallback = (sender, args) =>
            {
                // ---------------------------------------------------------
                // Step 3a: Save images to a custom folder using a unique name
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.Image)
                {
                    string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
                    Directory.CreateDirectory(imageFolder); // ensures folder exists

                    // Use a GUID so we never clash with existing files
                    string uniqueName = Guid.NewGuid().ToString() + args.Extension;
                    args.SavePath = Path.Combine(imageFolder, uniqueName);
                }

                // ---------------------------------------------------------
                // Step 3b: Skip CSS files – they aren't needed for plain Markdown
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.CssStyleSheet)
                    args.Cancel = true;
            }
        };

        // -----------------------------------------------------------------
        // Step 4: Export the document to Markdown, applying the options
        // -----------------------------------------------------------------
        string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Markdown saved to " + outputPath);
        Console.WriteLine("Images extracted to " + Path.Combine("YOUR_DIRECTORY", "Images"));
    }
}
```

### How the code works

- **Loading the document** (`new Document(inputPath)`) gives us an in‑memory representation of the Word file, complete with all its parts—paragraphs, tables, and **images**.
- **`MarkdownSaveOptions`** is where the magic happens. By attaching a `ResourceSavingCallback`, we gain full control over every external resource Aspose.Words tries to write out.
- Inside the callback we **extract images from Word file** by checking `args.ResourceType == ResourceType.Image`. The callback receives the image bytes, its original extension, and a `SavePath` property we set to a folder we create on the fly. Using `Guid.NewGuid()` guarantees a unique filename, so you won’t accidentally overwrite previous runs.
- We **skip CSS** (`ResourceType.CssStyleSheet`) because plain Markdown doesn’t need a stylesheet. This keeps the output tidy.
- Finally, `doc.Save(outputPath, mdOptions)` writes the Markdown file, replacing Word constructs with Markdown equivalents (headings become `#`, tables become pipe‑separated rows, etc.).

## Save images from docx – Custom folder strategy

Why bother with a custom folder? Imagine you’re generating documentation for a CI pipeline. You want the Markdown file and its assets to sit side‑by‑side in a clean, reproducible layout.

```csharp
string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
Directory.CreateDirectory(imageFolder);
```

A couple of **pro tips**:

- **Keep the folder path relative** to your project root. That way the Markdown file can reference images with a relative link (`![Alt text](Images/abc123.png)`), which works on GitHub, GitLab, or any static‑site generator.
- **If you need deterministic names** (e.g., the same image should always get the same filename), replace the GUID with a hash of the image bytes: `MD5.Create().ComputeHash(args.Data)`. That’s a small tweak but can be handy for caching.

## Extract images from Word file – Edge cases

1. **Multiple image formats** – Aspose.Words supports PNG, JPEG, GIF, BMP, and even SVG. The `args.Extension` property already contains the correct file extension, so you don’t have to guess.
2. **Very large images** – If your source document contains high‑resolution photos, the generated files can be sizable. Consider adding a compression step after the callback, using `System.Drawing` or `ImageSharp`.
3. **Hidden images** – Word can store images in headers/footers or even in text boxes. The callback sees them all, so you’ll extract **every** picture, not just the visible ones. If you only want body images, add a filter on `args.ImageIndex` or inspect `args.ImageType`.

## Export Word document as markdown – Verifying the result

After running the program, open `output.md` in any Markdown viewer. You should see something like:

```markdown
# My Report

Here is an introductory paragraph.

![Image1](Images/3f9c2d1e-7a5b-4c9e-9f6a-2b4e5d6f7a8b.png)

More text follows...
```

Notice how the image link points to the **Images** folder we created. That’s the hallmark of a successful **export Word document as markdown** operation.

### Quick sanity check

- Does the Markdown file open without errors in VS Code’s preview pane? ✅  
- Are all pictures displayed when you view the file on GitHub? ✅  
- Did the `Images` directory contain one file per picture from the original `.docx`? ✅  

If any of those checks fail, double‑check the `ResourceSavingCallback` logic and ensure the `YOUR_DIRECTORY` placeholder points to a writeable location.

## Common pitfalls and how to avoid them

| Pitfall | Why it happens | Fix |
|---------|----------------|-----|
| **Images not appearing** | Callback never fired because `ResourceSavingCallback` wasn’t assigned. | Assign the callback **before** calling `doc.Save`. |
| **Empty Images folder** | `args.Cancel = true` was set for all resources inadvertently. | Only cancel CSS (`ResourceType.CssStyleSheet`), leave images untouched. |
| **File‑path too long on Windows** | Using deep nested folders plus GUIDs can exceed 260 characters. | Keep the folder shallow, or enable long‑path support in Windows 10+. |
| **Duplicate image names** | Using `DateTime.Now.Ticks` instead of GUID can collide on fast loops. | Stick with `Guid.NewGuid()` for uniqueness. |

## Wrap‑up

We’ve just **converted docx to markdown**, **saved images from docx**, and demonstrated how to **extract images from Word file** while **exporting Word document as markdown** in a clean, repeatable way. The whole process hinges on Aspose.Words’ `ResourceSavingCallback`, which gives you granular control over every external asset.

### What’s next?

- **Style the Markdown** – add a front‑matter block for Jekyll or Hugo.  
- **Automate the pipeline** – embed this code in an Azure DevOps or GitHub Action step.  
- **Handle tables and footnotes** – explore other `MarkdownSaveOptions` flags like `ExportTableBorderStyles`.  

Feel free to tweak the folder structure, add image compression, or even switch the output format to HTML by swapping `MarkdownSaveOptions` for `HtmlSaveOptions`. The sky’s the limit when you have a solid base for **convert docx to markdown**.

Happy coding, and may your documentation always stay both beautiful **and** machine‑readable!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Convert Word to Markdown – Embed Images as Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}