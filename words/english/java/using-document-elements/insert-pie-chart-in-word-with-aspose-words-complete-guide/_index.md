---
category: general
date: 2026-07-26
description: Insert pie chart into a Word document using Aspose.Words. Learn how to
  add chart, explode slice, and show percentages in just a few steps.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: en
lastmod: 2026-07-26
og_description: Insert pie chart into a Word file with Aspose.Words. Follow this guide
  to learn how to add chart, explode slice, and show percentages quickly.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Insert Pie Chart in Word – Step-by-Step Aspose.Words Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Insert Pie Chart in Word with Aspose.Words – Complete Guide
url: /java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert Pie Chart in Word with Aspose.Words – Complete Guide

Ever needed to **insert pie chart** into a Word report but weren’t sure where to begin? You’re not alone. In many business apps the visual punch of a pie chart makes data instantly digestible, and Aspose.Words makes that possible with just a few lines of code.

In this tutorial we’ll walk through the exact steps to **add chart to Word**, explode a slice for emphasis, and show percentages on the data labels. By the end you’ll have a ready‑to‑run example that you can drop into any .NET project.

---

## Prerequisites

Before we dive in, make sure you have:

- .NET 6.0 or later (the code works with .NET Core and .NET Framework alike)
- The Aspose.Words for .NET NuGet package installed  
  ```bash
  dotnet add package Aspose.Words
  ```
- A basic understanding of C# syntax—nothing fancy required
- An IDE of your choice (Visual Studio, Rider, or VS Code)

That’s it. Let’s get our hands dirty.

---

## Insert Pie Chart into a Word Document

The first thing we need is a fresh `Document` object and a `DocumentBuilder`. Think of the builder as a pen that writes directly onto the Word canvas.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** The `Document` represents the entire .docx file, while the `DocumentBuilder` gives us a convenient API to insert elements like charts, tables, and text. This is the foundation for every **how to add chart** operation.

---

## How to Add Chart to Word

Now that we have a builder, we can actually **insert pie chart**. The `insertChart` method takes the chart type and the desired dimensions in points (1 point = 1/72 inch).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Tip:** If you need a different size, just tweak the width and height values. The chart will automatically scale to fit the page margins.

---

## How to Explode Slice for Emphasis

A common visual tweak is to “explode” a slice so it pops out of the circle. This draws the reader’s eye to the most important segment.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Why explode a slice?** When you want to highlight a particular category—say, “Q1 revenue” in a financial report—exploding the slice makes it instantly noticeable without extra text.

---

## How to Show Percentages on Data Labels

Most pie charts look better when each slice displays its percentage. Aspose.Words lets us turn this on with a single property.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Quick note:** The `ShowPercentage` flag works for all points in the series, so you don’t need to set it per slice.

---

## Save the Document Containing the Chart

Finally, we write the document to disk. Choose any folder you like; just make sure the path exists.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

When you open `PieChart.docx` in Microsoft Word you’ll see a perfectly rendered pie chart with the first slice exploded and percentages displayed—exactly what you’d expect from a polished business report.

---

## Full Working Example

Below is the complete, copy‑and‑paste‑ready program. Run it as a console app and verify the output file.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected result:** Open the generated `PieChart.docx`. You’ll see a three‑slice pie chart titled “Sales Q1”, with the first slice pulled out and each slice labeled “30 %”, “45 %”, and “25 %”. The visual matches the data we fed in.

---

## Common Questions & Edge Cases

- **What if I need more than one series?**  
  Just add additional `ChartSeries` objects to `chart.Series`. Each series can have its own data set, colors, and explode settings.

- **Can I change the chart’s colors?**  
  Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can set to any `System.Drawing.Color`.

- **What about different chart types?**  
  The `ChartType` enum includes bar, line, doughnut, and many more. Swap `ChartType.Pie` for whichever visual you need.

- **Is the chart editable in Word after insertion?**  
  Absolutely. Word treats the chart as a native Office chart, so users can double‑click it to open the built‑in chart editor.

---

## Conclusion

You now know exactly how to **insert pie chart** into a Word document using Aspose.Words, **how to add chart to word**, **how to explode slice**, and **how to show percentages** on the data labels. The full example above is ready to run, and you can extend it with custom data, styling, or additional series.

Ready for the next step? Try swapping the pie for a doughnut chart, or generate a batch of reports with different data sets automatically. If you’re curious about other visualizations, check out our guides on **how to add chart** for bar and line graphs, or explore the **add chart to word** API reference for deeper customizations.

Happy coding, and may your documents always be as clear as a perfectly sliced pie!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}