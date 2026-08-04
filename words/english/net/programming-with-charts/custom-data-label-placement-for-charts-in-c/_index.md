---
category: general
date: 2026-08-04
description: Custom Data‑Label Placement for Charts in C# lets you center labels on
  chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: en
lastmod: 2026-08-04
og_description: Custom Data‑Label Placement for Charts in C# shows you how to center
  all data labels on each slice of a Word chart. Master chart data label positioning
  with Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Custom Data‑Label Placement for Charts in C# – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: Custom Data‑Label Placement for Charts in C#
url: /net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Custom Data‑Label Placement for Charts in C#

**Custom Data‑Label Placement for Charts** lets you control exactly where each label appears on a chart inside a Word document. In this tutorial you’ll learn how to center all data labels on each slice using C# and the Aspose.Words chart API.

You’ll get a complete, runnable example that loads a `.docx` file, accesses the first chart shape, changes every label’s `Position` to `Center`, and saves the updated document. No external references are required—just the Aspose.Words for .NET library and a basic C# development environment.

**What you’ll learn**

* How to load a Word document that contains a chart.  
* How to locate the chart shape with the Aspose.Words chart API.  
* How to apply **chart data label positioning** to every series in the chart.  
* How to save the document so the centered labels appear in Word.  

**Prerequisites**

* .NET 6.0 (or later) installed.  
* Visual Studio 2022 (or any C# IDE).  
* A reference to the `Aspose.Words` NuGet package.  
* A Word file (`Chart.docx`) that contains at least one chart.

---

## Custom Data‑Label Placement for Charts – step 1: load the document

The first action is to open the Word file that holds the chart. `Document` is the entry point for any manipulation with Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Why this step matters*: Without loading the document you cannot reach the chart object. The validation ensures you receive a clear error if the file lacks a chart, preventing a null‑reference later.

---

## Using Aspose.Words chart API to access chart shapes

Aspose.Words treats a chart as a `Chart` object nested inside a `Shape`. You retrieve it by casting the appropriate child node.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Why this step matters*: Directly accessing `Chart` gives you full control over series, data points, and label properties. If the shape isn’t a chart, the code aborts early with an informative message.

---

## Setting chart data label positioning in C#

Now iterate through every series and every data label, setting the `Position` to `Center`. This is the core of **Custom Data‑Label Placement for Charts**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Pro tip**: If you need a different placement (e.g., `InsideEnd` for a column chart), change the enum value accordingly. The `ChartDataLabelPosition` enum covers all standard positions supported by Word.

*Why this step matters*: Changing `label.Position` updates the underlying OOXML representation, so the label appears centered when the document is opened in Microsoft Word.

---

## Saving the Word document with updated labels

After modifying the chart, persist the changes back to a file. You can overwrite the original or create a new copy.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Why this step matters*: Saving writes the updated OOXML to disk. Opening `ChartLabelsCentered.docx` in Word will show every slice label centered, confirming that **Custom Data‑Label Placement for Charts** succeeded.

---

## Edge cases and variations

| Situation | How to handle |
|-----------|---------------|
| **Multiple charts** in the same document | Loop over `doc.GetChildNodes(NodeType.Shape, true)` and check `shape.HasChart` for each shape. |
| **Different chart types** (pie, doughnut, bar) | The same `ChartDataLabelPosition.Center` works for pie‑type charts. For bar/column charts you may prefer `InsideEnd` or `OutsideEnd`. |
| **Label text needs formatting** | Access `label.TextProperties` to set font size, color, or boldness. |
| **Running on .NET Core** | Ensure you reference the .NET Standard version of Aspose.Words; the API is identical. |

---

## Complete working example

Below is the full program you can copy‑paste into a console application. It includes all necessary `using` directives and error handling.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Expected result**: Open `ChartLabelsCentered.docx` in Microsoft Word. Each slice of the chart now displays its data label directly in the center of the slice, providing a cleaner visual appearance.

---

## Conclusion

You now have a complete **Custom Data‑Label Placement for Charts** solution in C#. By loading the document, accessing the chart via the Aspose.Words chart API, setting `ChartDataLabelPosition.Center` for every label, and saving the file, you can automate label positioning for any Word‑based chart.

Next, explore other **chart data label positioning** options such as `InsideEnd` or `OutsideEnd`, or experiment with **C# chart manipulation** to change colors, add legends, or generate charts from scratch. These extensions build directly on the techniques covered here and broaden your Word document chart automation skills. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}