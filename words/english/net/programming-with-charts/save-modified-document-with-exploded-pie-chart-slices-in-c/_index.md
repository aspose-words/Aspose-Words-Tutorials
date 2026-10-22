---
category: general
date: 2026-10-13
description: 'Save modified document after customizing a pie chart: explode slices,
  change first slice angle, and show percentage labels in C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: en
lastmod: 2026-10-13
og_description: Save modified document after customizing a pie chart in C#. Learn
  how to explode pie chart slices, change first slice angle, and show percentage labels.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Save modified document with exploded pie chart slices – C# guide
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: Save modified document with exploded pie chart slices in C#
url: /net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Save modified document with exploded pie chart slices in C#

If you need to **save modified document** after tweaking a Word pie chart, this guide shows you exactly how. You’ll learn to explode pie chart slices, change the first slice angle, and show percentage labels—all with a few lines of C# code.

Customizing charts is a common requirement when generating reports, invoices, or dashboards programmatically. By the end of this tutorial you’ll be able to load a DOCX file, modify the chart appearance, and **save modified document** ready for distribution.

## Prerequisites

- .NET 6.0 or later (the code also works with .NET Framework 4.6+)
- Aspose.Words for .NET 23.10 or newer (free trial or licensed copy)
- A Word file (`input.docx`) that contains a single pie chart
- Visual Studio 2022 or any C# IDE

> **Tip:** The Aspose.Words NuGet package is added with `dotnet add package Aspose.Words`.

## Step 1: Load the Word document that contains the chart

The first step is to open the source DOCX file. The `Document` class represents the entire Word file in memory.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

Loading the document gives you full access to every node, including shapes that host charts.

## Step 2: Retrieve the first chart shape from the document

Charts are stored inside `Shape` nodes. You can locate the first chart with `GetChild`.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

If the document contains multiple charts, adjust the index (`0`) or iterate through the collection. This line ensures you have a reference to the `Chart` object you will modify.

## Step 3: Explode pie chart slices

Exploding a slice separates it from the rest of the pie, making the chart easier to read. The `Explode` property works for the whole series.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Setting `Explode` to `true` **explodes pie chart slices** for the entire series, which is useful when you want every slice to stand out.

## Step 4: Change the first slice angle

Sometimes you need the first slice to start at a custom angle, for example to align with a design guideline.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

The `FirstSliceAngle` property **changes first slice** orientation, rotating the whole pie so the first slice begins at 30 degrees.

## Step 5: Show percentage labels on the pie slices

Displaying the numeric contribution of each slice is often required in reports. The `DataLabel.ShowPercentage` flag turns on percentage values.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

This step **show percentage labels** directly on the chart, which also satisfies the **display percentages pie** requirement.

## Step 6: Save the modified document

After all customizations are applied, persist the changes to a new file. The `Save` method writes the updated DOCX to disk.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Now you have a **save modified document** that contains an exploded pie chart, a rotated first slice, and visible percentage labels.

![Save modified document showing exploded pie chart](/images/pie-chart-exploded.png "Save modified document with exploded pie chart slices and percentage labels")

*The screenshot illustrates the final output after the document is saved.*

## Full, runnable example

Putting the pieces together, here is the complete program you can copy‑paste into a console project:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Expected result

Opening `output.docx` will display a pie chart where:

- Every slice is slightly separated (**exploded pie chart slices**)
- The first slice starts at a 30‑degree offset (**change first slice**)
- Each slice shows its contribution as a percentage (**show percentage labels**, **display percentages pie**)
- The file has been **save modified document** without altering the original.

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **What if the document has no chart?** | The code checks for `null` after `GetChild`. If no chart exists, you can either add one programmatically or abort with a clear message. |
| **Can I explode only a single slice?** | Yes. Use `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` where `i` is the slice index. |
| **How do I change the label format (e.g., show value + %)?** | Set `chart.PieChart.DataLabel.ShowValue = true;` and optionally `chart.PieChart.DataLabel.ShowPercentage = true;` to combine both. |
| **Is the chart style preserved after saving?** | Aspose.Words retains all styling, including colors and fonts, when you **save modified document**. |
| **Can I process multiple charts in the same file?** | Loop through all `Shape` nodes with `NodeType.Shape` and filter by `shape.HasChart`. Apply the same steps to each chart. |

## Conclusion

You now know how to **save modified document** after programmatically customizing a pie chart in Word. The guide covered exploding pie chart slices, changing the first slice angle, and showing percentage labels—fulfilling the **show percentage labels**, **explode pie chart slices**, **display percentages pie**, and **change first slice** requirements.

Next, consider exploring:

- Adding data series dynamically (`chart.Series.Add(...)`)  
- Customizing legend placement and chart titles  
- Converting the DOCX to PDF while preserving chart styling  

Feel free to experiment with different angles, explosion settings, or label formats to match your reporting needs. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to Save Edited Document in C# with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}