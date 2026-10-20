---
category: general
date: 2026-09-21
description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
  add data labels to pie chart, and show percentages on pie chart in just a few steps.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: en
lastmod: 2026-09-21
og_description: Create pie chart in Word using Aspose.Words, insert chart into Word,
  add data labels to pie chart, and show percentages on pie chart—all with clear code
  examples.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Create a pie chart in Word with Aspose.Words – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: How to create pie chart in a Word document with Aspose.Words
url: /net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create pie chart in a Word document with Aspose.Words

If you need to **create pie chart** programmatically, Aspose.Words makes it straightforward. In this tutorial you’ll see how to **insert chart into Word**, configure the series, **add data labels to pie chart**, and finally **show percentages on pie chart** so the visual conveys exact values. By the end you’ll have a complete, runnable example that you can drop into any .NET project.

This guide covers everything you need to know: required NuGet packages, the full C# source, explanations of why each API call matters, and tips for customizing the chart. No external documentation is required—just copy, run, and adapt.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK or later installed.  
* Visual Studio 2022 (or any IDE that supports .NET).  
* An Aspose.Words for .NET license (the free trial works for testing).  
* Basic familiarity with C# and Word document structures.

If you already have these, you can move straight to the code.

## Step 1: Set up the project and import Aspose.Words

Create a new console project and add the Aspose.Words NuGet package:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

The package includes the `Aspose.Words.Drawing.Charts` namespace, which contains the `Chart` and `ChartSeries` classes we’ll use.

> **Pro tip:** Keep your license file (`Aspose.Words.lic`) in the project root and load it at startup to avoid evaluation watermarks.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Step 2: Create a blank document and a DocumentBuilder

A `Document` represents the Word file, while `DocumentBuilder` provides a fluent API for inserting content.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** The `DocumentBuilder` maintains the current insertion point, ensuring the chart appears exactly where you want it in the document flow.

## Step 3: Insert a pie chart into the Word document

Now we **insert chart into Word**. The `InsertChart` method takes the chart type, width, and height (in points).

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

At this point the chart contains a default data series with placeholder values (25, 25, 25, 25). You can replace them later if needed.

## Step 4: Access the first series and customize data labels

A pie chart typically has a single series. To **add data labels to pie chart**, we retrieve it and enable the percentage display.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Why we set `ShowPercentage`:** This flag tells Aspose.Words to calculate each slice’s contribution and render it as a percentage. The `Position` property ensures the label doesn’t overlap the slice, which improves legibility—especially when slices are small.

## Step 5: (Optional) Replace the placeholder data

If you want specific values, replace the default points:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

The percentages displayed will automatically adjust to reflect the new values.

## Step 6: Save the document

Finally, write the document to disk. The extension determines the format; `.docx` creates a modern Word file.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

Running the program produces a file named **PieChart.docx** in the output folder. Opening it in Microsoft Word shows a pie chart with each slice labeled by its percentage, positioned outside the slices.

### Expected output

When you open the generated document, you should see:

* A single pie chart, 400 × 300 pt in size.  
* Four slices (or however many points you added).  
* Percentage labels such as “40 %”, “30 %”, etc., displayed outside each slice.

If the labels appear inside the slices, double‑check that `ChartDataLabelPosition.OutsideEnd` was set correctly.

## Step 7: Common variations and edge cases

### Adding a title to the chart

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Changing slice colors

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Handling an empty series

If your data source might be empty, guard against `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Exporting to PDF instead of Word

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

The same chart rendering logic applies; Aspose.Words converts the Word layout to PDF automatically.

## Full source listing

Below is the complete, ready‑to‑run program. Copy it into `Program.cs` and execute `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Conclusion

You now know how to **create pie chart** in a Word file using Aspose.Words, **insert chart into Word**, **add data labels to pie chart**, and **show percentages on pie chart**. The example demonstrates the full workflow—from project setup to final document—so you can adapt it for dashboards, reports, or automated invoice generation.  

Next, explore related topics such as **how to display percentages in chart** legends, customizing chart colors, or converting the Word document to PDF for distribution. Experiment with different chart types (Bar, Line) using the same `InsertChart` method to broaden your automation capabilities.

Happy charting!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}