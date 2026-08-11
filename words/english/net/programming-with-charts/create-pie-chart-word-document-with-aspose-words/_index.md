---
category: general
date: 2026-08-10
description: Create pie chart Word document using Aspose.Words. Learn how to insert
  chart, customize pie chart colors, and change pie slice color in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: en
lastmod: 2026-08-10
og_description: Create pie chart Word document with Aspose.Words. This guide explains
  how to insert chart, customize pie chart colors, and change pie slice color in a
  C# application.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Create pie chart Word document – Aspose.Words guide
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Create pie chart Word document with Aspose.Words
url: /net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create pie chart Word document with Aspose.Words

If you need to **create pie chart Word document** programmatically, this tutorial shows you exactly how. We'll walk through inserting a chart, **customizing pie chart colors**, and **changing pie slice color** using Aspose.Words for .NET.

You’ll see a complete, runnable example that you can copy into Visual Studio, run, and immediately open the generated *.docx* to verify the styled pie chart. No external documentation is required—everything you need is in this guide.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK or later installed  
* A valid Aspose.Words for .NET license (or a temporary evaluation key)  
* Visual Studio 2022 (or any C# IDE)  

The code uses only the `Aspose.Words` and `Aspose.Words.Drawing.Charts` namespaces, so no additional NuGet packages are required beyond the Aspose.Words library.

## Create pie chart Word document – full example

The following C# program creates a new Word document, inserts a pie chart, styles the first two slices, and saves the file. Each step is explained in detail.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Explanation of each step

| Step | What it does | Why it matters |
|------|--------------|----------------|
| **1** | Creates a new `Document` and a `DocumentBuilder`. | The `DocumentBuilder` provides fluent methods for inserting content, such as charts, into the Word file. |
| **2** | Calls `InsertChart` with `ChartType.Pie` and a fixed size. | `InsertChart` is the **how to insert chart** method; specifying width/height ensures the chart fits nicely on the page. |
| **3** | Adds a data series with three categories and numeric values. | A pie chart without data is invisible; populating it demonstrates the styling steps. |
| **4** | Sets `Explosion` on the first point. | Exploding a slice draws attention to a particular segment—useful for highlighting key data. |
| **5** | Sets `ForeColor` for the first two points. | This is the core of **customize pie chart colors**; you can use any `System.Drawing.Color`. |
| **6** | Shows how to **change pie slice color** for additional slices. | Demonstrates that styling is not limited to the first two slices; you can color every slice individually. |
| **7** | Saves the document as `PieChartStyled.docx`. | The final output can be opened in Microsoft Word, Google Docs, or any compatible viewer. |

#### Expected output

Opening `PieChartStyled.docx` displays a single page with a 400 × 300 pt pie chart:

* Slice 1 (orange) is exploded outward.  
* Slice 2 (green) appears adjacent to the exploded slice.  
* Slice 3 (steel‑blue) fills the remaining segment.

The chart reflects the data values (30, 45, 25) and the custom colors you defined.

## How to style pie – additional tips

* **Use theme colors** – instead of hard‑coding `Color.Orange`, you can pull colors from the document theme:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Add data labels** – if you want percentages shown on the chart:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Resize dynamically** – calculate the chart size based on page margins:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

These variations demonstrate the flexibility of **how to style pie** beyond the basic example.

## Common questions answered

**Q: Does this work with .NET Core?**  
A: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET 6, and later. Just reference the same NuGet package.

**Q: What if I need a donut chart instead of a pie?**  
A: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs (`Explosion`, `ForeColor`) apply.

**Q: Can I insert the chart into an existing document?**  
A: Open the existing file with `new Document("Existing.docx")`, create a `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor position.

**Q: How do I handle large datasets?**  
A: Pie charts are best for a limited number of categories (typically < 10). For many categories, consider a bar or column chart instead.

## Full source code recap

Below is the complete program in one block for easy copy‑paste:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

Running this code produces the styled pie chart Word document described earlier.

## Conclusion

You now know how to **create pie chart Word** documents using Aspose.Words, **customize pie chart colors**, and **change pie slice color** programmatically. The guide covered inserting the chart, populating data, exploding a slice, applying custom colors, and saving the result.  

From here you can explore related topics such as **how to insert chart** types other than pie, adding legends, or generating multi‑page reports with multiple charts. Experiment with different color schemes and data sets to fit your reporting needs.

Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}