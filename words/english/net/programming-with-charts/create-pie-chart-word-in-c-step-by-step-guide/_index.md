---
category: general
date: 2026-08-07
description: Create pie chart word in C# quickly. Learn how to insert pie chart, add
  data labels pie, show percentage chart, and customize chart data labels.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: en
lastmod: 2026-08-07
og_description: Create pie chart word in C# with Aspose.Words. This tutorial shows
  how to insert pie chart, add data labels pie, and show percentage chart while customizing
  chart data labels.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Create pie chart word in C# – complete tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Create pie chart word in C# – step‑by‑step guide
url: /net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create pie chart word in C# – step‑by‑step guide

If you need to **create pie chart word** documents in C#, this guide provides a complete, ready‑to‑run solution. You’ll see how to **insert pie chart**, **add data labels pie**, and **show percentage chart** while **customize chart data labels** for a polished look.

Generating charts programmatically saves you from manual editing, especially when reports or dashboards must be produced automatically. In the sections below you’ll learn everything required to embed a fully labeled pie chart into a Word file using Aspose.Words for .NET.

## Prerequisites and setup

Before you start, make sure you have:

* .NET 6.0 SDK or later installed.  
* A valid Aspose.Words for .NET license (or a temporary evaluation key).  
* Visual Studio 2022 (or any IDE that supports C#).  

Add the Aspose.Words NuGet package to your project:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** If you plan to generate many charts, enable the **Free‑Form Drawing** mode (`DocumentBuilder.UseFreeFormDrawing = true`) for better performance.

## Create pie chart word with Aspose.Words

The first major step is to create a blank Word document and a `DocumentBuilder`. This object drives all subsequent insertions.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters*: `Document` represents the entire `.docx` file, while `DocumentBuilder` provides a fluent API to add paragraphs, tables, and charts. Starting with a clean document ensures no hidden formatting interferes with the chart layout.

## Insert pie chart into the document

Now we place a pie chart of the desired size. The `InsertChart` method returns a `Chart` object that we can further configure.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Why this matters*: The `ChartType.Pie` flag tells Aspose.Words to generate a circular chart. The width (`400`) and height (`300`) are expressed in points, giving you precise control over the visual footprint.

## Populate the chart with data

A pie chart needs at least one series of numeric values. Here we add three categories: “Apples”, “Bananas”, and “Cherries”.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Why this matters*: Each `AddCategory` call creates a slice. The numeric value determines the slice size, while the label becomes the category name displayed when data labels are turned on.

## Add data labels pie and show percentage chart

To make the chart informative, we enable data labels, position them outside the slices, and ask Aspose.Words to display both the category name and the percentage.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Why this matters*: Setting `Position` to `OutsideEnd` improves readability, especially when slices are small. Enabling `ShowCategoryName` and `ShowPercentage` fulfills the **show percentage chart** requirement and satisfies the **add data labels pie** objective.

## Customize chart data labels further (optional)

You may want to change the font, add a leader line, or hide the legend. The following snippet demonstrates common customizations:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Why this matters*: Customizing the label appearance ensures the chart matches your document’s style guide. Removing the legend reduces visual clutter when data labels already convey the same information.

## Save the document with the customized chart

Finally, write the document to disk. Choose a path you have write access to.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

When you open `ChartWithCustomLabels.docx` in Microsoft Word, you’ll see a pie chart where each slice is labeled with its category name and percentage, positioned outside the slice, and styled with the custom font settings.

### Expected output

| Slice   | Value | Percentage | Label shown in Word |
|---------|-------|------------|---------------------|
| Apples  | 40    | 40 %       | Apples – 40 %       |
| Bananas | 35    | 35 %       | Bananas – 35 %      |
| Cherries| 25    | 25 %       | Cherries – 25 %     |

The chart should look similar to the illustration below:

![Word document displaying a pie chart with percentage labels outside each slice](pie-chart-word.png "Create pie chart word example")

*Image alt text includes the primary keyword for SEO.*

## Handling multiple series and edge cases

The basic example uses a single series, which is typical for a pie chart. If you need to display multiple series (e.g., comparing two years), you must:

1. Call `chart.Series.Add()` for each additional series.  
2. Ensure each series uses the same categories; otherwise, Aspose.Words will throw an `ArgumentException`.  
3. Optionally, set `labels.ShowSeriesName = true` to differentiate slices.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

When multiple series exist, the chart automatically renders as a **clustered pie** (also called a “pie of pies”). Review the output to verify that labels remain legible.

## Common pitfalls and how to avoid them

| Problem | Cause | Fix |
|---------|-------|-----|
| Labels overlap slices | Small chart area or many categories | Increase chart dimensions (`InsertChart(width, height)`) or switch `Position` to `InsideEnd`. |
| Percentages don’t add up to 100 % | Rounding errors in data | Use `labels.ShowPercentage = true` (Aspose.Words automatically normalizes). |
| Chart appears blank in Word | Missing license or evaluation timeout | Ensure a valid Aspose.Words license is loaded before creating the document. |
| Font colors differ from Word theme | Custom font set in code | Remove custom font settings or match Word’s theme colors (`System.Drawing.Color.Black`). |

## Full source code (runnable)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Running the program produces `ChartWithCustomLabels.docx`, which contains a **create pie chart word** example that meets all the requirements listed in the tutorial.

## Conclusion

You now know how to **create pie chart word** documents in C# using Aspose.Words. The guide covered inserting a pie chart, **add data labels pie**, **show percentage chart**, and **customize chart data labels** to achieve a professional, data‑driven Word file.  

From here you can explore related topics such as **insert pie chart** into existing paragraphs, generate **bar** or **line** charts, or automate batch creation of reports with varying data sets. Experiment with different label positions, font styles, and multi‑series configurations to tailor the output to your specific reporting needs.

Happy charting!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}