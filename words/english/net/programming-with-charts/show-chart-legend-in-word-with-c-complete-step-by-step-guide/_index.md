---
category: general
date: 2026-06-02
description: Show chart legend in a Word document using C#. Learn how to add legend,
  apply preset chart style, and customize Word chart visuals in minutes.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: en
og_description: Show chart legend in a Word document instantly. This guide walks you
  through adding a legend, applying preset chart style, and handling edge cases.
og_title: Show Chart Legend in Word – Full C# Tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
url: /net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide

Ever wondered **how to add legend** to a chart that lives inside a Word document? You're not the only one. In many reports, a missing legend makes the data look cryptic, and fixing it shouldn't be a headache.  

In this tutorial we’ll **show chart legend** in a Word file using Aspose.Words for .NET, apply a preset chart style, and make sure the legend appears exactly where you need it. By the end you’ll have a ready‑to‑run sample that you can drop into any C# project.

## What This Guide Covers

We'll walk through the entire workflow:

1. Load an existing *.docx* that already contains a chart.  
2. Retrieve the first chart (or any chart you target).  
3. **Apply preset chart style** to give the visual a professional look.  
4. **Show chart legend**, position it on the right, and handle special cases like Waterfall charts.  
5. Save the modified document.

No external tools, no manual fiddling with the UI—just pure code. The only prerequisite is a reference to the Aspose.Words NuGet package (version 23.10 or later) and a basic understanding of C#.

---

## Prerequisites

- .NET 6.0 or later (the sample works with .NET Framework 4.7.2 as well).  
- Aspose.Words for .NET library installed (`Install-Package Aspose.Words`).  
- A Word file (`input.docx`) that already contains at least one chart.  
- Visual Studio, Rider, or any IDE you prefer.

---

## Step 1: Set Up the Project and Load the Document

First, create a console app (or integrate the code into an existing project). Add the `using` directives and load the `.docx` file.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Why this matters:** Loading the document is the foundation. Without a `Document` instance you can't reach the chart objects that Aspose.Words exposes.

---

## Step 2: Retrieve the Target Chart

Charts are stored as nodes inside the document tree. The `GetChild` method performs a deep search, letting us fetch the first chart regardless of where it sits (header, body, footer, etc.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Tip:** If you have multiple charts, change the index `0` to `1`, `2`, … or iterate through `doc.GetChildNodes(NodeType.Chart, true)`.

---

## Step 3: Apply a Preset Visual Style

A good-looking chart often starts with a style. Aspose.Words ships with dozens of built‑in styles; `ChartStyle.Style12` is a clean, modern option.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **How it works:** The `Style` property maps to the built‑in Word chart styles you see in the UI. Choosing a preset saves you from manually setting colors, fonts, and markers.

---

## Step 4: Enable the Legend and Position It

Now for the star of the show—**show chart legend**. We turn the legend on, then dock it to the right side of the chart.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Why right?** Placing the legend on the right keeps the data area wide, which is especially helpful for bar or column charts.

---

## Step 5: Handle Waterfall Charts (Special Case)

Waterfall charts behave a bit differently; the legend can be hidden by default. The following guard clause ensures the legend is visible when the chart type is Waterfall.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Edge case note:** Some older Word versions ignore `HasLegend` for Waterfall charts, so explicitly setting `Legend.Show` guarantees visibility.

---

## Step 6: Save the Modified Document

Finally, write the changes back to disk. You can overwrite the original file or create a new one.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

Running the program will produce `output.docx` with a visible legend on the right, styled with `Style12`. Open the file in Word to verify the result.

---

## Full Working Example (All Steps Combined)

Below is the complete, ready‑to‑run code. Copy‑paste it into `Program.cs` (or any C# file) and adjust the file paths.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Expected output:** Opening `output.docx` shows the original chart with a right‑aligned legend, styled with the modern `Style12`. All data series are clearly labeled, making the chart instantly understandable.

---

## Frequently Asked Questions (FAQ)

### How to add legend to a specific chart (not the first one)?

Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based position of your target chart, or loop through all chart nodes:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Can I place the legend at the bottom instead of the right?

Absolutely. Just change the `LegendPosition` enum:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### What if the chart already has a legend but I want to hide it?

Set `HasLegend` to `false`:

```csharp
chart.HasLegend = false;
```

### Does this work with Word 2010, 2016, and later?

Yes. Aspose.Words abstracts the underlying Word version, so the same code works across all modern .docx files.

---

## Pro Tips & Common Pitfalls

- **Pro tip:** After applying a style, you can still tweak individual elements (colors, data labels) via the `Chart.Series` collection. The style gives you a solid baseline.
- **Watch out for:** If the chart is inside a table cell, the legend may appear cramped. Consider increasing the chart size (`chart.Width`, `chart.Height`) before positioning the legend.
- **Performance note:** Loading large documents (hundreds of MB) can be memory‑intensive. Use `LoadOptions` with `LoadFormat.Docx` to reduce overhead if you only need chart manipulation.

---

## Next Steps

Now that you know **how to add legend** and **apply preset chart style** in Word, you might explore:

- **Custom chart colors** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Data label formatting** (`chart.Series[i].HasDataLabel = true`).  
- **Exporting the chart as an image** (`chart.ToImage()`), useful for embedding elsewhere.  

Each of these topics builds on the same object model, so you’ll find the learning curve gentle.

---

## Conclusion

We’ve just demonstrated a clean, end‑to‑end solution for **show chart legend** in a Word document using C#. By loading the document, retrieving the chart, applying a preset style, enabling the legend, and handling Waterfall quirks, you get a polished chart ready for any business report.  

Feel free to experiment with other `ChartStyle` values or legend positions—your data visualizations deserve the best presentation. If you hit any snags, drop a comment below; happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}