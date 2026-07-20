---
category: general
date: 2026-07-20
description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
  pie chart labels, show percentage labels, and update chart series labels quickly.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: en
lastmod: 2026-07-20
og_description: Add pie chart labels in C# with Aspose.Words. Master changing pie
  chart labels, showing percentage labels, and updating chart series labels in just
  a few steps.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Add pie chart labels in C# – Aspose.Words Full Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Add pie chart labels in C# using Aspose.Words – Complete Guide
url: /net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Add pie chart labels in C# using Aspose.Words – Complete Guide

Need to **add pie chart labels** to a Word document using C#? With Aspose.Words you can effortlessly **change pie chart labels** and **display pie chart percentages** right inside the file—no manual tweaking in Word required.  

In this tutorial we’ll walk through the exact steps to **show percentage labels**, reposition them, and even **update chart series labels** for dynamic data. By the end you’ll have a reusable snippet that you can drop into any .NET project.

> **Quick preview:** After following the guide, opening the saved `.docx` will reveal a pie chart where each slice is labeled with its percentage, positioned outside the slice for maximum readability.

---

## What You’ll Need

- **Aspose.Words for .NET** (the latest version as of 2026). You can grab it from NuGet: `Install-Package Aspose.Words`.
- A **Word document** that already contains a pie or doughnut chart (we’ll call it `Chart.docx`).
- Basic familiarity with **C#** and Visual Studio (or your favorite IDE).

That’s it—no extra libraries, no COM interop, just pure managed code.

---

## Add pie chart labels – Full Implementation

Below is a **complete, runnable** C# console program that loads a document, modifies the first pie chart, and saves the result. Every line is commented so you’ll understand **why** we’re doing what we’re doing, not just **what**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Expected Result

Open `ChartWithCustomLabels.docx` in Microsoft Word. You should see the pie chart **with percentage labels positioned outside each slice**. The labels look something like “35 %”, “20 %”, etc., making the chart instantly understandable.

---

## Change pie chart labels: positioning and formatting

If you only need to **change pie chart labels** without showing percentages, you can adjust the `Position` property to one of the following:

| Position Enum | Visual Effect |
|---------------|---------------|
| `InsideEnd`   | Labels sit inside the slice, right at the edge. |
| `Center`      | Labels appear in the middle of the slice (good for small pies). |
| `OutsideEnd`  | Labels are outside the slice, connected with a leader line (our default). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Pro tip:** `OutsideEnd` works best when the chart has many slices; it prevents overlapping text.

---

## Show percentage labels on a pie chart

The property `ShowPercentage` is a **boolean flag**. Setting it to `true` tells Aspose.Words to calculate each slice’s contribution based on the underlying data source.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

You can also combine it with `ShowValue` if you need both raw numbers **and** percentages:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

When both flags are enabled, the label looks like “45 % (120)”.

---

## Update chart series labels for dynamic data

Often you’ll generate charts on the fly—think monthly sales or survey results. To **update chart series labels** programmatically, modify the `Series` collection before you touch the data labels:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

This snippet demonstrates how to **update chart series labels** for any series, not just the first one. It’s handy when you’re building reports that combine actual vs. forecast data.

---

## Edge Cases & Common Pitfalls

| Situation | What to Watch For | Fix |
|-----------|-------------------|-----|
| **Chart isn’t a pie/doughnut** | `Position` may have no visual effect. | Verify `chart.Type` is `ChartType.Pie` or `ChartType.Doughnut`. |
| **No chart found** | `GetChild` returns `null`. | Add a guard clause (see code) and log a helpful message. |
| **Older Word version** | Some label features are ignored. | Save as `.docx` (the modern format) to guarantee full support. |
| **Large number of slices** | Labels can overlap even with `OutsideEnd`. | Consider reducing slice count or increasing chart size. |

---

## Full Working Example (Copy‑Paste)

Below is the **entire program** you can copy into a new console project. Just replace `YOUR_DIRECTORY` with the folder that holds `Chart.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // Grab the first chart (assumed to be a pie chart).
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null) { Console.WriteLine("No chart found."); return; }

            // Access the first series' data labels.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // Position labels outside and show percentages.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;
            dataLabels.ShowPercentage = true;

            // (Optional) Show raw values as well.
            // dataLabels.ShowValue = true;

            // Save the modified


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize Single Chart Series In A Chart](/words/english/net/programming-with-charts/single-chart-series/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}