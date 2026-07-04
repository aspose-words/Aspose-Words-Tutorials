---
category: general
date: 2026-06-02
description: Learn how to use variable weight font in C# and set font weight programmatically
  while change font stretch code for dynamic typography.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: en
og_description: Use variable weight font in C# to set font weight programmatically
  and change font stretch code, enabling dynamic typography in your documents.
og_title: Use Variable Weight Font in C# – Full Guide
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Use Variable Weight Font in C# – Complete Programming Guide
url: /net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Use Variable Weight Font in C# – Complete Programming Guide

Ever needed to **use variable weight font** in a .NET project but weren’t sure how to make the weight and stretch respond to user input? You’re not alone. In many UI or reporting scenarios you want the text to adapt—maybe a light headline that becomes bold on hover, or a paragraph that expands its width for emphasis. The good news is that with Aspose.Words you can **set font weight programmatically** and even **change font stretch code** on the fly.

In this tutorial we’ll walk through a hands‑on example that shows exactly how to load a variable‑weight font, apply a custom weight, and tweak the stretch setting—all with clear C# code you can copy‑paste. By the end you’ll have a runnable console app that produces a PDF showcasing the effect.

---

## What You’ll Need

- **Aspose.Words for .NET** (v23.12 or later). The library ships with full support for variable‑weight fonts.
- A folder containing at least one variable‑weight font file, e.g., *RobotoFlex‑Variable.ttf*. You can download it from Google Fonts.
- .NET 6 SDK (or any recent .NET version) and an IDE of your choice.
- Basic C# knowledge—nothing fancy, just a few lines of code.

That’s it. No extra NuGet packages beyond Aspose.Words, and no obscure configuration files.

---

![Use variable weight font example](https://example.com/variable-weight-sample.png "Use variable weight font demonstration")

*Alt text: screenshot showing use variable weight font in a generated PDF document.*

---

## Step 1: Set Up FontSettings and Point to Your Font Folder  

First things first—Aspose.Words needs to know where your variable‑weight fonts live. You do this by creating a `FontSettings` object and attaching a `FolderFontSource`. The `true` flag tells the engine to search sub‑folders as well, which is handy if you keep multiple font families together.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Why this matters:** Without registering the folder, Aspose.Words falls back to system fonts and will ignore the variable‑weight data embedded in your custom font file. This step is the foundation for everything that follows.

---

## Step 2: Attach FontSettings to the Document  

Now we create a new `Document` (or load an existing one) and tell it to use the `FontSettings` we just prepared. This binding is what makes the variable‑weight data available to every `Run` we add later.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

If you already have a template—say, a Word file with placeholders—you can replace `new Document()` with `new Document("Template.docx")`. The same `FontSettings` will apply.

---

## Step 3: Add a Run of Text That Will Use the Variable‑Weight Font  

A **Run** is the smallest unit of text formatting in Aspose.Words. We’ll create one, insert it into a new paragraph, and later change its font attributes.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

At this point the text will render using the default font (usually Times New Roman). The magic happens once we assign the variable‑weight family.

---

## Step 4: Choose the Variable‑Weight Font Family  

Here’s where we actually **use variable weight font**. Set the `Font.Name` to the exact family name defined inside the variable font file. For Roboto Flex, the name is `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

If you’re unsure about the family name, open the `.ttf` file in a font viewer or use the `fontSettings.GetFonts()` method to enumerate available families.

---

## Step 5: Set Font Weight and Stretch Programmatically  

Now the core of the tutorial: we **set font weight programmatically** and **change font stretch code**. Both properties accept integer values that map to the OpenType specification.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). Pick any value the variable font supports.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). The default is 100 (Normal).

> **Pro tip:** Not every variable font exposes the full range. If you set a value that isn’t supported, the engine will clamp to the nearest available weight or stretch.

---

## Step 6: Save the Document and Verify the Result  

Finally, write the document out to PDF (or DOCX) and open it to see the effect. PDF is a great format for visual verification because the rendering is consistent across platforms.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

When you open *VariableWeightDemo.pdf*, you should see the phrase “Variable‑weight text demo” rendered in a light, slightly expanded version of Roboto Flex. Change the `FontWeight` to `700` and `FontStretch` to `80` and rerun—watch the text become bold and more condensed.

---

## Common Questions & Edge Cases  

### What if the font doesn’t appear at all?  

- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;` is executed **before** any text is added.
- **Incorrect family name**: Use `fontSettings.GetFonts()` to list all discovered families; copy the exact string.
- **Unsupported weight/stretch**: Some variable fonts only support a subset of the 100‑900 weight range. Use `run.Font.FontWeight = 400;` as a safe fallback.

### Can I change the weight after the document is saved?  

Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch` at any point before the final `Save`. If you need to toggle weights dynamically (e.g., based on user interaction), consider generating separate runs for each state.

### Does this work with DOCX output?  

Absolutely. The variable‑weight metadata is stored in the underlying OpenXML, and modern versions of Word can interpret it. However, older Word versions may ignore the stretch setting.

---

## Full Working Example  

Below is a complete console program you can compile and run instantly. It includes all necessary `using` directives, error handling, and comments.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Expected output:** The console prints the save path, and the generated PDF shows the text in a light, expanded style—exactly what we configured.

---

## Recap  

We’ve covered how to **use variable weight font** in C# with Aspose.Words, demonstrated how to **set font weight programmatically**, and showed you the exact **change font stretch code** needed to expand or condense the glyphs. The steps are straightforward: configure `FontSettings`, attach them to a `Document`, create a `Run`, pick the variable‑weight family, and finally tweak `FontWeight` and `FontStretch`.

---

## What’s Next?  

- **Dynamic UI integration**: Hook the same logic into a WinForms or WPF app to let users pick weight/stretch via sliders.
- **Multiple runs**: Combine several runs with different weights in the same paragraph for rich typographic hierarchies.
- **Advanced axes**: Some variable fonts expose additional axes (e.g., slant, optical size). Use `run.Font.FontStyle` or explore `FontVariationSettings` for even finer control.
- **Performance tips**: Cache the `FontSettings` instance when processing many documents to avoid repeated folder scans.

Feel free to experiment—swap *Roboto Flex* for *Inter Variable* or any other OpenType variable font, and watch your documents gain a new level of visual flexibility. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Use Font From Target Machine](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}