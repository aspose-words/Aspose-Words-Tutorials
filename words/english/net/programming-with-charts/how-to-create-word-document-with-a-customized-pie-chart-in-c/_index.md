---
category: general
date: 2026-10-07
description: Learn how to create word document and insert pie chart using Aspose.Words
  in C#. The guide also shows how to generate word file with custom chart labels.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: en
lastmod: 2026-10-07
og_description: Create word document and insert pie chart in C#. Follow this step‑by‑step
  guide to generate word file with fully customized chart labels.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Create a Word document with a customized pie chart in C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: How to create word document with a customized pie chart in C#
url: /net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create word document with a customized pie chart in C#

If you need to **create word document** programmatically, this tutorial shows you how to **insert pie chart** and customize its data labels using Aspose.Words for .NET. You will also learn how to **generate word file** that contains a fully styled chart, covering everything from project setup to saving the final document.

The guide walks through each step required to add a chart, adjust label positions, enable leader lines, and finally save the result as a `.docx` file. No external tools are required beyond the Aspose.Words library, and the complete source code is provided so you can copy, paste, and run it instantly.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK or later installed  
* A valid Aspose.Words for .NET license (or a free evaluation key)  
* An IDE such as Visual Studio 2022 or Visual Studio Code  

You will also need to add the following NuGet packages to your project:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

These packages expose the `Document`, `DocumentBuilder`, and chart‑related classes used in the examples below.

## Create word document and add a chart

The first step is to **create word document** and obtain a `DocumentBuilder` that lets you insert content. The builder works like a cursor positioned inside the document.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

The `Document` object represents the entire Word file, while the `DocumentBuilder` provides methods such as `InsertChart` that place objects directly into the document flow.

## Insert pie chart into the document

Now that the builder is ready, you can **insert pie chart** with a specific size. The chart is added at the builder’s current position.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` returns a `Chart` object that you can manipulate further. The sample data creates four slices representing quarterly sales.

## Customize pie chart data labels

To make the chart more readable, you often need to **customize pie chart** labels—position them outside the slices and show leader lines. This is where the `ChartDataLabelCollection` comes into play.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

Setting `Position` to `OutsideEnd` moves each label beyond the slice’s edge, while `ShowLeaderLines` draws a line that connects the label to its slice. The optional flags `ShowValue` and `ShowPercentage` give readers both raw numbers and relative percentages.

**Pro tip:** If you need to format the label font, use `dataLabels.Font` to set size, color, and style. This ensures the chart matches your corporate branding.

## Save and generate word file

After the chart is fully configured, you can **generate word file** by saving the `Document` instance to disk. Choose the `.docx` format for maximum compatibility with modern Word versions.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

When you open `CustomPieChart.docx`, you will see a pie chart with four slices, each labeled outside the slice, connected by leader lines, and displaying both value and percentage.

![Screenshot of a Word document that contains a customized pie chart created with C#](image-placeholder.png)

*The image shows the final result of the **create word document** tutorial.*

## Common variations and edge cases

| Scenario | How to adapt the code |
|----------|----------------------|
| **Multiple series** | Add additional `ChartSeries` objects to `pieChart.Series`. Each series can have its own `DataLabels` collection for independent styling. |
| **Different chart size** | Change the width and height parameters in `InsertChart(width, height)`. Values are in points (1 pt ≈ 1/72 in). |
| **Chart title** | Use `pieChart.Title.Text = "Quarterly Sales"` to add a descriptive title. |
| **Export to PDF** | Call `document.Save("Report.pdf", SaveFormat.Pdf);` after the chart is built. |
| **License handling** | Place your license file (`Aspose.Words.lic`) in the application folder and load it with `new License().SetLicense("Aspose.Words.lic");` before creating the document. |

These variations let you answer the question **how to add pie chart** in many real‑world scenarios, from simple reports to complex dashboards.

## Conclusion

You now know how to **create word document**, **insert pie chart**, and **customize pie chart** labels using Aspose.Words for .NET. The complete example demonstrates a clean workflow: initialize the document, add a chart, adjust data‑label positioning, enable leader lines, and finally **generate word file** that can be shared with anyone.

Try extending this tutorial by experimenting with different chart types (`ChartType.Column`, `ChartType.Line`) or by applying custom color palettes to match your brand. If you run into issues, consult the Aspose.Words documentation or explore related topics such as “how to add pie chart” with multiple series and dynamic data sources.

Happy coding, and feel free to share your results or ask follow‑up questions in the comments!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)
- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}