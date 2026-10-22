---
category: general
date: 2026-10-13
description: Aspose.Words radial chart example that shows how to enable graduations
  on a radial chart using C# and Aspose.Words 24.9+.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: en
lastmod: 2026-10-13
og_description: Aspose.Words radial chart example that demonstrates enabling graduations
  on a radial chart with C# and the latest 24.9+ library.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Aspose.Words radial chart example – enable graduations in C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Aspose.Words radial chart example: enable graduations in C#'
url: /net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words radial chart example: enable graduations in C#

If you are looking for an **aspose.words radial chart example**, you have landed in the right place. This tutorial walks you through the exact steps to turn on graduations for a radial chart using the Aspose.Words for .NET API.

Radial charts are useful for visualizing cyclic data such as time‑of‑day metrics or seasonal trends. By default the graduations (the tick marks around the circular axis) are hidden, which can make the chart harder to read. Enabling them is a single‑line change, but you need to know the correct object model and the version that supports the feature.

In this guide you will learn how to:

* Load a Word document that already contains a radial chart.  
* Access the chart shape via the Aspose.Words chart API.  
* Turn on **graduations visibility** (available from **Aspose.Words version 24.9**).  
* Save the modified document and verify the result.

The complete, runnable code is included, so you can copy‑paste it into a new console project and see the effect immediately.

![Aspose.Words radial chart example with graduations](https://example.com/images/radial-chart-graduations.png "Aspose.Words radial chart example showing graduations enabled")

## Prerequisites

Before you start, make sure you have:

| Requirement | Why it matters |
|-------------|----------------|
| .NET 6.0 or later | Aspose.Words for .NET 24.9+ targets .NET Standard 2.0 and works on .NET 6+. |
| Aspose.Words for .NET **24.9** or newer | The `IsGraduationsVisible` property was introduced in version 24.9. Older releases will throw a `MissingMemberException`. |
| A Word document (`RadialChart.docx`) that contains a radial chart | The example manipulates an existing chart; creating one from scratch is a separate topic. |
| A C# IDE (Visual Studio, Rider, VS Code) | Any IDE that can compile .NET projects will work. |
| NuGet package `Aspose.Words` | Install via `dotnet add package Aspose.Words --version 24.9.0` (or later). |

> **Pro tip:** If you cannot upgrade to 24.9, you can still modify other chart properties, but graduations will remain hidden because the API did not expose that flag.

## Aspose.Words radial chart example – step‑by‑step guide

The following sections break the process into discrete, easy‑to‑follow steps. Each step includes the exact code you need and a short explanation of *why* the step exists.

### Step 1: Load the document that contains a radial chart

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Why this matters:**  
`Document` is the entry point of the **Aspose.Words chart API**. It loads the DOCX file into memory, giving you access to every node—paragraphs, tables, and chart shapes. If the file cannot be found, `Document` throws a `FileNotFoundException`, which you should handle in production code.

### Step 2: Retrieve the first chart shape from the document

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Why this matters:**  
Charts are stored as `Shape` nodes. The `GetChild` method with `NodeType.Shape` walks the DOM and returns the first matching shape. Casting to `Chart` gives you access to chart‑specific properties such as `RadialChart`. The null‑check ensures you get a clear error if the document does not contain a chart, which is a common edge case when reusing templates.

### Step 3: Enable graduations on the radial chart

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Why this matters:**  
`IsGraduationsVisible` controls the tick marks around the circular axis. When set to `true`, the chart renders graduations, improving readability for viewers who need to gauge values precisely. The property lives under `RadialChart`, which is a sub‑type of `Chart`. If you try this on a non‑radial chart (e.g., a bar chart), the `RadialChart` property will be `null`, so you should verify the chart type first in more complex scenarios.

#### Handling non‑radial charts (optional)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

This guard makes the code robust when the source document might contain different chart types.

### Step 4: Save the modified document

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Why this matters:**  
Calling `Save` writes the in‑memory DOM back to a .docx file, persisting the change you made to the chart. The output file can be opened in Microsoft Word, LibreOffice, or any viewer that supports DOCX. You will see the radial chart with visible graduations.

## Full, runnable example

Below is the complete program you can paste into `Program.cs` of a .NET console project.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Expected output

When you open `RadialChart_Graduations.docx` in Word, the radial chart will display tick marks (graduations) around the circular axis, similar to the screenshot shown earlier. The rest of the chart (data series, legend, title) remains unchanged.

## Common variations and edge cases

| Situation | Solution |
|-----------|----------|
| **Older Aspose.Words version (< 24.9)** | Upgrade to the latest NuGet package. The `IsGraduationsVisible` property does not exist in earlier releases. |
| **Multiple charts in the same document** | Use `doc.GetChild(NodeType.Shape, index, true)` with the appropriate `index` or iterate over `doc.GetChildNodes(NodeType.Shape, true)` and filter by `ChartType.Radial`. |
| **Chart created programmatically** | Use `DocumentBuilder` to insert a chart, then set `RadialChart.IsGraduationsVisible` on the


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Remove a Chart Series from a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Hide Plot Area Border in a Column Chart with Aspose.Words for .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}