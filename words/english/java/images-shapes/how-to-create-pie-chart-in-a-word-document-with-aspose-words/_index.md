---
category: general
date: 2026-10-20
description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
  guide that shows how to set color, explode slice, and save Word document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: en
lastmod: 2026-10-20
og_description: Create pie chart in a Word document with Aspose.Words. Learn how to
  set color, explode slice, and save Word document in a single, runnable example.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Create a pie chart in a Word document – full C# guide
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: How to create pie chart in a Word document with Aspose.Words
url: /java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create pie chart in a Word document with Aspose.Words

If you need to **create pie chart** inside a Word file, this guide shows you exactly how to do it. You’ll see how to set a custom color, explode a slice for emphasis, and finally **save Word document** with the chart embedded.

Generating charts programmatically removes the manual steps of opening Word, inserting a chart, and tweaking its appearance. By the end of this tutorial you will have a complete, runnable C# console application that creates a pie chart, customizes it, and writes the result to disk.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK or later installed  
* A valid Aspose.Words for .NET license (or a free evaluation key)  
* An IDE such as Visual Studio 2022 or VS Code  

No additional NuGet packages are required beyond `Aspose.Words`.

## How to create pie chart in a Word document

The first step is to instantiate a `Document` and a `DocumentBuilder`. The builder gives you access to high‑level Word features, including chart insertion.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

At this point the document already contains a basic pie chart. The next sections explain **how to explode slice**, **how to set color**, and **how to save Word document**.

## How to explode slice for emphasis

Exploding a slice separates it from the rest of the pie, drawing the reader’s eye. The Aspose.Words API lets you specify an explosion distance in points.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Why explode the slice? In reports that highlight a particular category—such as “Top‑selling product”—the visual separation makes the data point instantly recognizable.

## How to set color on a chart slice

Custom colors improve brand consistency and readability. You can assign any `System.Drawing.Color` to a specific data point.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

You are not limited to predefined colors; you can create a `Color.FromArgb` value for precise shades.

## How to save Word document with the chart

Once the chart looks the way you want, persisting the file is straightforward. The `Document.Save` method writes the document in the format you specify—here we use the default `.docx`.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Running the program creates `PieChart.docx`. Opening the file in Microsoft Word shows a pie chart where the first slice is exploded and colored red, exactly as the code specifies.

### Expected result

* A Word file named **PieChart.docx** in `C:\Temp`.  
* The document contains a single pie chart, 400 × 300 points in size.  
* Slice 0 is offset by 20 points and filled with red, while the other slices keep the default color.  

You can verify the explosion and color by selecting the chart in Word and inspecting the slice properties.

## Pro tips and common pitfalls

* **Pro tip:** If you need to change the chart title or legend, use `pieChart.Title.Text` and `pieChart.Legend` properties before saving.  
* **Watch out for:** Forgetting to clear the default data points can lead to extra, unwanted slices. Always call `Series[0].DataPoints.Clear()` before adding your own data.  
* **Performance tip:** For large documents, reuse a single `DocumentBuilder` instance instead of creating many builders; this reduces memory overhead.

## How to create chart using Aspose.Words (additional context)

The `InsertChart` method supports many chart types besides pie charts, such as column, line, and area charts. To switch to a different type, replace `ChartType.Pie` with the desired enum value, e.g., `ChartType.Column`. The rest of the customization steps (exploding slices, setting colors) follow the same pattern, though not all chart types expose an “explosion” property.

## How to explode slice in other chart types

Only pie‑type charts expose the `SetExplosion` method. If you try to call it on a bar chart, the API throws an `ArgumentException`. In those cases, consider using data labels or callouts to highlight a particular bar.

## How to set color on a series instead of a single slice

If you want every slice in a series to share the same color, loop over the data points:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

This approach is handy when you need a uniform color scheme across multiple charts.

## How to save Word document in other formats

Aspose.Words can export to PDF, HTML, and many other formats. Change the file extension in `Save` and optionally pass a `SaveOptions` object:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

The chart rendering engine automatically converts the chart to the target format, preserving colors and explosion settings.

## Conclusion

You now know how to **create pie chart** in a Word document, customize its appearance by **exploding a slice** and **setting color**, and finally **save Word document** with the chart embedded. This end‑to‑end example gives you a solid foundation for automating report generation, dashboards, or any scenario where visual data needs to be inserted programmatically.

### Next steps

* Explore other chart types (`ChartType.Column`, `ChartType.Line`) to broaden your reporting toolkit.  
* Combine multiple charts in a single document to build comprehensive dashboards.  
* Experiment with `ChartDataLabel` to show percentages or values directly on the slices.  

Feel free to adapt the code to your own data sources—whether you pull values from a database, an API, or a CSV file, the same Aspose.Words workflow applies. Happy charting!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Explode Pie Chart Slice in C# with Aspose.Words – Full Guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Insert Custom Column Chart in Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}