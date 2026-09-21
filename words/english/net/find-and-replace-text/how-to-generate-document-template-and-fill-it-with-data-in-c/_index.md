---
category: general
date: 2026-09-21
description: Learn how to generate document template, populate word template and replace
  placeholders in a DOCX file using C# – step‑by‑step guide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate document template
- populate word template
- how to replace placeholder
- fill docx template
- replace text docx
language: en
lastmod: 2026-09-21
og_description: Generate document template in C# by populating a Word template, replacing
  placeholders, and saving a filled DOCX file. Follow this complete guide.
og_image_alt: Screenshot of a C# program generating and filling a DOCX template
og_title: Generate document template in C# – fill DOCX files with data
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to generate document template, populate word template and
    replace placeholders in a DOCX file using C# – step‑by‑step guide.
  headline: How to generate document template and fill it with data in C#
  type: TechArticle
tags:
- C#
- DOCX
- template processing
title: How to generate document template and fill it with data in C#
url: /net/find-and-replace-text/how-to-generate-document-template-and-fill-it-with-data-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to generate document template and fill it with data in C#

If you need to **generate document template** files that can be reused for invoices, contracts, or reports, this guide shows you exactly how. You’ll learn to **populate word template** placeholders, replace them with real values, and finally **fill docx template** files programmatically.

Creating a reusable template eliminates manual copy‑pasting and ensures consistency across all generated documents. The steps below work with any `.docx` file that contains simple placeholder tokens such as `{{Name}}`.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK or later installed  
* Visual Studio 2022 (or any IDE you prefer)  
* The **Aspose.Words for .NET** NuGet package – it provides the `Document` class used in the example  

You can add the package with the following command:

```bash
dotnet add package Aspose.Words
```

## Step 1: Prepare the Word template

Create a Word document (`Template.docx`) that contains placeholders where dynamic data should appear. A common convention is double‑curly braces:

```
Dear {{Name}},

Your order #{{OrderId}} has been shipped on {{ShipDate}}.
```

Save the file in a folder you can reference from code, for example `C:\Docs\Template.docx`.

## Step 2: Load the template document

The first programmatic action is to load the template into memory. The `Document` constructor reads the file and builds an object model you can manipulate.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Load the template document from disk
        string templatePath = @"C:\Docs\Template.docx";
        Document doc = new Document(templatePath);
```

**Why this matters:** Loading the file creates a clean copy each time, so the original template remains untouched for future runs.

## Step 3: Replace placeholders with actual data

Aspose.Words provides a simple `Range.Replace` method that scans the document for a specific string and substitutes it. Wrap the call in a helper method to keep the main flow tidy.

```csharp
        // Helper to replace a single placeholder
        void ReplacePlaceholder(string placeholder, string value)
        {
            // The placeholder includes the curly braces exactly as they appear in the template
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());
        }

        // Populate the template with real values
        ReplacePlaceholder("{{Name}}", "John Doe");
        ReplacePlaceholder("{{OrderId}}", "A12345");
        ReplacePlaceholder("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));
```

**How it works:** `Range.Replace` walks through every paragraph, table cell, header, and footer, ensuring that all occurrences of the token are updated. This is the most reliable way to **how to replace placeholder** text in a DOCX file.

### Handling multiple occurrences and missing tokens

* If a placeholder appears more than once, `Replace` updates all instances automatically.  
* If a placeholder is absent, the method simply does nothing—no exception is thrown.  
* For large documents, you can improve performance by disabling `doc.UpdateFields()` until after all replacements are complete.

## Step 4: Save the filled document

Once all placeholders are replaced, write the result to a new file. Keeping the output separate preserves the original template for future runs.

```csharp
        // Save the filled document to a new file
        string outputPath = @"C:\Docs\FilledTemplate.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Result:** `FilledTemplate.docx` now contains the personalized content:

```
Dear John Doe,

Your order #A12345 has been shipped on September 21, 2026.
```

## Step 5: Verify the output (optional)

If you want to programmatically confirm that the replacements succeeded, you can read the saved file back and search for the expected values:

```csharp
        Document verifyDoc = new Document(outputPath);
        bool nameReplaced = verifyDoc.Range.Text.Contains("John Doe");
        Console.WriteLine($"Name replacement successful: {nameReplaced}");
```

Running the verification step prints `true` when the placeholder was correctly replaced.

## Common pitfalls and best‑practice tips

| Issue | Why it happens | Recommended fix |
|-------|----------------|-----------------|
| **Placeholders contain extra spaces** | `"{{ Name }}"` does not match `"{{Name}}"`. | Keep placeholder tokens free of whitespace, or trim both sides before replacement. |
| **Word adds hidden formatting** | Word may store the placeholder split across multiple runs, causing `Replace` to miss it. | Use `Document.Range.Replace` with `FindReplaceOptions` set to `MatchCase = false` and `FindWholeWordsOnly = false`. |
| **Large documents cause slowdown** | Replacing tokens one by one triggers a full document scan each time. | Batch replacements in a single pass by calling `Range.Replace` for each token before saving. |
| **Saving to a read‑only folder** | `doc.Save` throws an `UnauthorizedAccessException`. | Ensure the target directory has write permissions, or choose a user‑writable path (e.g., `%TEMP%`). |

## Full working example

Below is the complete, self‑contained program that you can copy, paste, and run.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Paths – adjust to your environment
        string templatePath = @"C:\Docs\Template.docx";
        string outputPath   = @"C:\Docs\FilledTemplate.docx";

        // 1️⃣ Load the template document
        Document doc = new Document(templatePath);

        // 2️⃣ Replace placeholders
        void Replace(string placeholder, string value) =>
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());

        Replace("{{Name}}", "John Doe");
        Replace("{{OrderId}}", "A12345");
        Replace("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));

        // 3️⃣ Save the filled document
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");

        // 4️⃣ (Optional) Verify replacement
        Document verify = new Document(outputPath);
        Console.WriteLine($"Verification – name found: {verify.Range.Text.Contains("John Doe")}");
    }
}
```

**Expected console output**

```
Document saved to C:\Docs\FilledTemplate.docx
Verification – name found: True
```

Open `FilledTemplate.docx` in Microsoft Word to see the personalized text.

## Conclusion

You now know how to **generate document template**, **populate word template**, and **fill docx template** files by **how to replace placeholder** tokens with real data. The approach works for any number of placeholders and scales to large documents when you follow the best‑practice tips.

### What’s next?

* **Dynamic tables:** Use `DocumentBuilder` to insert rows based on collections.  
* **Conditional sections:** Hide or show parts of the template with `IF` fields.  
* **PDF export:** Call `doc.Save("output.pdf")` to create a PDF version of the filled document.  

Experiment with these variations to build a full‑featured document generation engine for invoices, contracts, or any repeatable report.

---


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Word Document - Find And Replace Text](/words/english/net/find-and-replace-text/)
- [Generate Word Document](/words/english/java/word-processing/generate-word-document/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}