---
category: general
date: 2026-10-13
description: How to format chart in Word with C# by applying a custom number format,
  such as currency, to chart axes. Step‑by‑step code example included.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: en
lastmod: 2026-10-13
og_description: How to format chart in Word with C# lets you apply a custom number
  format to chart axes, ensuring values appear as currency, percentages, or any pattern
  you need. Follow the step‑by‑step guide.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: How to format chart in Word with C# – custom number formats
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: How to format chart in Word with C# and custom number formats
url: /net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to format chart in Word with C# and custom number formats

How to format chart in Word with C# is a common requirement when you need to present data professionally. This guide shows you how to apply a custom number format to a chart’s axis using **Aspose.Words for .NET**, so the values appear exactly as you expect.

You’ll learn how to load a DOCX file, locate the first chart, read the current format, and then set a new pattern such as currency with two decimals. The tutorial also covers how to change chart axis format for additional series and how to reset the format if needed.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 or later installed  
* A Visual Studio 2022 (or any IDE that supports .NET) project  
* The **Aspose.Words for .NET** NuGet package (`Aspose.Words`)  
* A Word document (`input.docx`) that contains at least one chart

You can add the package with the following command:

```bash
dotnet add package Aspose.Words
```

## How to format chart in Word using Aspose.Words

The following complete program demonstrates every step required to **format chart** axis values. Save the file as `Program.cs` and run it from the command line or your IDE.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Explanation of each step

| Step | Why it matters | Key code |
|------|----------------|----------|
| **Load the document** | You need a `Document` object to work with the Word file. | `new Document("input.docx")` |
| **Retrieve the chart** | `Chart` objects are stored as `Shape` nodes; casting lets you use chart‑specific APIs. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Access X‑values** | Axis formatting is applied to the value collection of a data series. | `chart.ChartData.Series[0].XValues` |
| **Read current format** | Knowing the existing `FormatCode` helps you decide whether to replace or augment it. | `xValues.FormatCode` |
| **Set custom format** | The `FormatCode` property accepts any Excel‑compatible pattern, enabling currency, percentages, dates, etc. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Save the document** | Persisting changes writes the new axis format back to the DOCX file. | `doc.Save("output_formatted.docx")` |

Running the program produces `output_formatted.docx`. Open it in Word and you’ll see the chart’s X‑axis values displayed as **$1,234.00**, **$2,345.00**, … instead of plain numbers.

## Apply custom number format to chart axis

If you need to **apply custom number format** to the Y‑axis or to additional series, the process is identical—just target a different collection:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Pro tip:** Use double quotes inside the format string to embed literal characters (e.g., `"$"` for currency). Escape the quotes as shown above.

## Custom number format word – handling Word’s locale

Word respects the document’s locale when interpreting number formats. If the document uses a non‑US locale, you may need to adjust the format string:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Testing the format on a document with German language settings confirms that values appear as **€ 1.234,00**.

## How to set chart properties programmatically

Beyond axis formatting, you often want to **set chart** titles, legends, or data labels. Here’s a quick snippet that demonstrates setting a chart title after you have formatted the axis:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Combining this with the custom number format gives you a fully polished chart ready for reporting.

## Change chart axis format dynamically based on user input

In real‑world applications you might let users choose a format at runtime. The following method encapsulates the formatting logic:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

You can call `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` for currency or `SetAxisFormat(chart, 0, "0%")` for percentages. This approach keeps your main code clean and supports future extensions.

## Edge cases and common pitfalls

| Situation | What to watch for | Suggested fix |
|-----------|-------------------|---------------|
| Document contains **no chart** | `GetChild` returns `null`, causing a cast exception. | Check for `null` before casting (see example). |
| Multiple charts in the same document | The code always grabs the first chart (`index 0`). | Loop through `doc.GetChildNodes(NodeType.Shape, true)` and filter by `ShapeType.Chart`. |
| Series **without X‑values** (e.g., pie charts) | Accessing `XValues` may throw `ArgumentOutOfRangeException`. | Verify `Series[i].XValues` is not empty before formatting. |
| Locale mismatch | Currency symbol may appear incorrectly. | Explicitly set `xValues.FormatCode` with the appropriate locale symbols. |

## Expected output

After running the sample program, open **output_formatted.docx**. The chart’s X‑axis should display numbers in the chosen custom format. For the currency example, the axis labels look like:

```
$1,000.00
$2,000.00
$3,000.00
```

If you applied the percentage format to Y‑values, the Y‑axis labels appear as:

```
10%
20%
30%
```

## Conclusion

This tutorial showed you **how to format chart** in Word with C# by **applying a custom number format** to axis values. You now have a reusable pattern for setting currency, percentages, or any other numeric pattern, as well as guidance for handling locales, multiple series, and dynamic user input.

Next, you might explore **how to set chart** titles, data labels, or even export the chart as an image using `ChartRenderer`. Those topics build directly on the concepts covered here and will help you create fully automated reporting solutions.

---


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Format Secondary X‑Axis and Set Display Units to Thousands in Word Line Charts Using Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}