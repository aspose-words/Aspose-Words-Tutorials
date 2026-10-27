---
category: general
date: 2026-10-10
description: Translate paragraph to French and learn how to change chart data label,
  customize chart data label, and save edited docx file using Aspose.Words AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: en
lastmod: 2026-10-10
og_description: Translate paragraph to French and learn how to change chart data label,
  customize chart data label, and save edited docx file using Aspose.Words AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Translate paragraph to French and change chart label in Word
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: Translate paragraph to French and change chart label in Word
url: /net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Translate paragraph to French and change chart label in Word

If you need to **translate paragraph to French** while also updating a chart inside the same Word document, this guide shows you exactly how. Using Aspose.Words AI you can translate text automatically, then modify a chart’s data label and finally save the edited `.docx` file—all in a few straightforward steps.

The tutorial covers everything from loading the source file to persisting the changes. By the end you will be able to translate any paragraph, customize a chart data label, and produce a new Word file ready for distribution. No external scripts are required; the entire workflow lives in a single C# program.

## Prerequisites

- .NET 6.0 or later (the code also works with .NET Framework 4.7+)
- An Aspose.Words for .NET license (or a free evaluation key)
- Internet access for the Google AI translator (the `Translator` class uses Google’s API under the hood)
- A Word document (`input.docx`) that contains at least one paragraph and one chart

## Step 1: Set up the project and import namespaces

Create a new console application and add the Aspose.Words NuGet package:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Now include the required namespaces at the top of `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

These imports give you access to document loading, AI translation, and chart editing functionality.

## Step 2: Load the source Word document

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

Loading the file creates an in‑memory representation that you can query and modify without touching the original file on disk.

## Step 3: Translate the first paragraph to French

The first paragraph is often a title or introductory sentence, making it a good candidate for translation. The `Translator` class abstracts the call to Google’s AI model.

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**Why this works:**  
`paragraph.Runs.Clear()` removes all existing text runs, ensuring the new translation does not concatenate with the old content. `new Run(document, translatedText)` creates a fresh run that inherits the paragraph’s formatting.

## Step 4: Locate the first chart and customize its data label

Charts are stored as `Shape` nodes of type `NodeType.Shape`. The first chart can be fetched with `GetChild`.

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**Explanation of the key steps:**

- `GetChild(NodeType.Shape, 0, true)` performs a depth‑first search and returns the first shape, which in our case is a chart.
- `ChartSeries` represents a collection of data points; the first series (`Series[0]`) typically corresponds to the primary data set.
- `ChartDataLabelPosition.OutsideEnd` moves the label outside the end of the bar, improving readability.
- Setting `dataLabel.Text` to a French string aligns the label with the translated paragraph.

## Step 5: Save the document with the translated paragraph

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

At this point the document contains the French paragraph but still holds the original chart configuration.

## Step 6: Save the document with the updated chart

You can reuse the same `Document` instance—no need to reload it—because the chart modifications are already in memory.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Both files are now ready for distribution:

- **`translated.docx`** – contains the French paragraph.
- **`chart-updated.docx`** – contains the French paragraph *and* the customized chart label.

## Complete, runnable example

Below is the full program you can copy‑paste into `Program.cs`. It compiles and runs as‑is, assuming you have replaced `YOUR_DIRECTORY` with a real folder path.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

namespace WordAiDemo
{
    class Program
    {
        static void Main()
        {
            // ---------- Load the source document ----------
            string inputPath = @"YOUR_DIRECTORY/input.docx";
            Document document = new Document(inputPath);
            Console.WriteLine("Document loaded.");

            // ---------- Translate the first paragraph ----------
            Paragraph paragraph = document.FirstSection.Body.FirstParagraph;
            string original = paragraph.GetText();
            string translated = Translator.Translate(original, Language.French);
            Console.WriteLine


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}