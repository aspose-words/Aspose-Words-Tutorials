---
category: general
date: 2026-09-21
description: How to format series in a Word line chart using C#. Learn to create a
  Word document, insert a line chart, and apply a custom number format.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: en
lastmod: 2026-09-21
og_description: How to format series in a Word line chart using C#. This tutorial
  shows you how to create a Word document, insert a line chart, and apply a custom
  number format.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: How to format series in a Word line chart with C# – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: How to format series in a Word line chart with C#
url: /net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to format series in a Word line chart with C#

If you need to **how to format series** in a Word line chart, this guide gives you a complete, ready‑to‑run solution. You’ll see how to **create a Word document**, **insert line chart**, and **apply custom number format** to the Y‑values—all with Aspose.Words for .NET.

Word automation becomes straightforward once you understand the chart object model. By the end of this tutorial you will have a Word file that contains a line chart whose data series are displayed as percentages with two decimal places.

## What you will achieve

* Generate a blank `.docx` file programmatically.  
* Add a line chart of size 400 × 300 points.  
* Access the first data series of the chart.  
* Apply the format code `#,##0.00%` so the Y‑values appear as percentages.  

No external tools are required beyond the Aspose.Words NuGet package.

## Prerequisites

* .NET 6.0 SDK or later.  
* Visual Studio 2022 (or any C# IDE).  
* Aspose.Words for .NET 23.10 or newer – install via `dotnet add package Aspose.Words`.  

The code works on Windows, Linux, and macOS because Aspose.Words is platform‑agnostic.

## Create a Word document with Aspose.Words

The first step is to instantiate a `Document` object. This object represents the entire Word file in memory.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Why this matters*: `Document` is the entry point for all Word‑processing operations. Without it you cannot add paragraphs, tables, or charts.

## Insert line chart into the document

A `DocumentBuilder` writes content into the `Document`. Calling `InsertChart` creates a chart shape on the current page.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Why this matters*: `InsertChart` returns a `Chart` object that gives you full control over series, axes, and formatting. The size parameters are expressed in points (1 point = 1/72 inch).

## Access the first data series

Every chart contains one or more `ChartSeries`. The first series is at index 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Why this matters*: The `ChartSeries` object holds the Y‑values, X‑values, and formatting options for a single line in a line chart. Modifying this object changes the visual representation of the data.

## Apply a custom number format to the series

The `FormatCode` property controls how numeric values are displayed. Setting it to `#,##0.00%` tells Word to treat the values as percentages with two decimal places.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Why this matters*: Without a custom format, Word shows raw decimal numbers (e.g., `0.15`). The format code converts them to `15.00%`, which is often what business reports require.

## Save the document and verify the result

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

When you open `FormattedSeriesLineChart.docx` in Microsoft Word, you will see a line chart where the Y‑axis labels read `15.00%`, `30.00%`, `45.00%`, and `60.00%`. The chart size matches the dimensions supplied in `InsertChart`.

### Expected output screenshot

> *Image: A Word document page showing a line chart with percentage‑formatted Y‑axis values.*  
> *(Alt text: Screenshot of a Word document showing a line chart with percentage‑formatted Y‑axis values)*

## Common variations and edge cases

| Situation | Adjustment |
|-----------|------------|
| **Multiple series** | Loop through `chart.Series` and set `FormatCode` for each series. |
| **Different chart type** | Replace `ChartType.Line` with `ChartType.Column`, `ChartType.Pie`, etc. |
| **Locale‑specific separators** | Use `CultureInfo`‑aware format strings, e.g., `"# ##0,00 %"` for French locales. |
| **Dynamic data source** | Populate `series.YValues` from a database or CSV file before applying the format. |

**Pro tip:** Always apply the format **after** you have added the Y‑values. Changing the format first and then adding values works as well, but applying it later guarantees the format is applied to the final data set.

## Recap

You now know **how to format series** in a Word line chart using C#. The tutorial covered:

* Creating a Word document (`create word document`).  
* Inserting a line chart (`insert line chart`, `add chart to word`).  
* Accessing the chart’s first series.  
* Applying a custom number format (`apply custom number format`) to display percentages.

## Next steps

* Experiment with different `ChartType` values to see how other visualizations behave.  
* Add titles, axis labels, and legends using `chart.Title`, `chart.AxisX.Title`, and `chart.AxisY.Title`.  
* Export the chart as an image (`chart.Save` with `SaveFormat.Png`) for use in web reports.

Feel free to adapt this pattern to generate dashboards, financial reports, or any document that needs programmatic charting. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}