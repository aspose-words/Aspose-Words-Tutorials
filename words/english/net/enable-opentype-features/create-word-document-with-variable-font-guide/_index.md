---
category: general
date: 2026-03-19
description: Create Word document using Aspose.Words and a variable font. Learn how
  to change font weight, set font width, and define font variation in C#.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: en
og_description: Create Word document with a variable font using Aspose.Words. This
  tutorial shows you how to load the font, change font weight, set font width, and
  define font variation.
og_title: Create Word Document with Variable Font – Complete Guide
tags:
- Aspose.Words
- C#
- Variable Font
title: Create Word Document with Variable Font – Guide
url: /net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word Document with Variable Font – Guide

Ever needed to **create word document** that uses a modern variable font, but weren't sure where to start? You're not alone. In many projects—think of dynamic reports or brand‑consistent brochures—being able to **change font weight** on the fly is a real game‑changer.  

In this tutorial we'll walk through the entire process: from loading a variable font into Aspose.Words, to setting its weight and width, and finally saving a DOCX that looks exactly as you designed. No vague references, just concrete code you can drop into your C# project right now.

## What You'll Learn

- How to **load variable font** files into Aspose.Words using `FontSettings`.
- The syntax for **define font variation** axes such as `wght` (weight) and `wdth` (width).
- Ways to **set font width** and **change font weight** on a single `Run`.
- Tips for troubleshooting common pitfalls (missing glyphs, incorrect folder paths, etc.).
- A complete, runnable example you can copy‑paste and test instantly.

> **Prerequisites**: .NET 6+ (or .NET Framework 4.6+), Aspose.Words for .NET installed via NuGet, and a variable‑font file like *RobotoFlex.ttf* placed in a local *Fonts* folder.

---

## Step 1 – Load the Variable Font into Aspose.Words

First, we have to tell Aspose.Words where to look for our custom fonts. The `FontSettings` class does the heavy lifting.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Why this matters**: Without registering the folder, Aspose.Words falls back to system fonts and will ignore any OpenType variation data you try to apply later. By pointing it at a specific directory you guarantee that *RobotoFlex* (or any other variable font) is found every time the code runs.

> **Pro tip**: Set the second parameter of `SetFontsFolder` to `true` if you want Aspose to search sub‑folders as well. This helps when you organize fonts by style or weight.

---

## Step 2 – Create a New Document and Add Sample Text

Now that the font engine knows where to look, we spin up a blank `Document` and insert a paragraph with a `Run`.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**What’s happening**: `Run` represents a contiguous piece of text with uniform formatting. By creating it first, we keep the formatting logic isolated—perfect for later applying different variation axes to separate runs if needed.

---

## Step 3 – Define the Desired Variation Axes (Weight & Width)

Variable fonts expose *axes* that you can tweak at runtime. The two most common are `wght` (font weight) and `wdth` (font width). Aspose.Words models this with the `OpenTypeFontVariation` collection.

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Why these numbers**: In the OpenType spec, `wght` ranges from the font’s minimum to maximum weight (often 100–900). A value of **700** maps to a bold appearance. `wdth` works similarly; **100** means the default (normal) width, while values below 100 condense the glyphs.

> **Edge case**: Some variable fonts don’t support a particular axis. If you supply an unsupported tag, Aspose will ignore it silently. Always double‑check the font’s specification (usually found in the `.ttf` or `.otf` file’s metadata).

---

## Step 4 – Apply the Variation to the Run Using the Font Name

Now we bind the variation data to the actual text. The `FontInfo` class holds the font family name and the axes collection.

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Explanation**: By setting `FontInfo`, we bypass the usual `Font.Name` property and hand the engine a fully‑qualified font configuration. This is the only way to tell Aspose.Words to use a variable font with custom axes.

> **Common mistake**: Forgetting to match the exact family name inside the font file (`RobotoFlex` in this example). A typo will cause Aspose to fall back to a default font, and your variation will be lost.

---

## Step 5 – Save the Document and Verify the Result

Finally, write the document to disk. The generated DOCX will contain the variable‑font instructions, which Microsoft Word (2016+) can render correctly.

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Open the resulting file in Word, select the text, and look at the **Font** dialog. You should see *Roboto Flex* listed, and the text will appear bolder than the surrounding content—exactly what our `wght = 700` setting requested.

> **Verification tip**: If the text looks unchanged, double‑check that the font file truly supports the `wght` axis. Some “variable” fonts only expose `ital` (italic) or `opsz` (optical size).

---

## Optional: Add More Variation – Changing Width Dynamically

If you want to *set font width* differently for another paragraph, just repeat steps 3‑4 with a new `OpenTypeFontVariation` collection.

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Now you have two runs—one bold, one slightly wider—demonstrating both **change font weight** and **set font width** in the same document.

---

## Full Working Example

Copy the snippet below into a new console app (`Program.cs`) and run it. Make sure the `Fonts` folder contains `RobotoFlex.ttf` (or any variable font you prefer).

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Expected output**: A `VariableFont.docx` file where the phrase “Variable‑weight text” appears bolded, thanks to the `wght = 700` axis, while retaining the default width.

---

## Frequently Asked Questions & Edge Cases

| Question | Answer |
|----------|--------|
| *What if the font isn’t found?* | Verify the folder path, ensure the file name matches, and that the process has read permissions. You can also call `fontSettings.GetFonts()` to list detected fonts. |
| *Can I combine multiple runs with different variations?* | Absolutely. Each `Run` can carry its own `FontInfo`. Just repeat steps 3‑4 for each run. |
| *Do older versions of Word support variable fonts?* | Word 2016 (Build 16.0.8001) introduced basic support. If you target older versions, the document will fall back to the nearest static instance of the font. |
| *Is there a limit to how many axes I can set?* | You can set any number the font defines. Common tags are `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Supplying an unsupported tag simply has no effect. |
| *How do I debug missing glyphs?* | Use `FontSettings.GetFontSources()` to inspect loaded fonts, and `FontInfo.HasGlyph(char)` to test individual characters. |

---

## Conclusion

In a handful of steps we’ve shown **how to create word document** files that leverage the power of variable fonts, letting you **change font weight**, **set font width**, **load variable font** files, and **define font variation** axes—all with Aspose.Words for .NET.  

The core idea is straightforward: register the font folder, describe the desired axes, attach them to a `Run`, and save. From here you can expand the technique to whole sections, tables, or even program‑matically generate brand‑specific reports.

**Next steps**: try swapping `RobotoFlex` for another variable font, experiment with the `ital` (italic) axis, or generate a PDF version of the same document using Aspose.PDF. The same pattern applies—load, define, apply, save.

Happy coding, and enjoy the flexibility that variable fonts bring to your Word automation projects!  

<img src="variable-font-demo.png" alt="Create word document with variable font example">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}