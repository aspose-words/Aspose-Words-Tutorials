---
title: Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET
weight: 110
limit:
description: Learn to create a Word column chart and apply uniform data‑label font size and colour to all series with Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn to create a Word column chart and apply uniform data‑label font
    size and colour to all series with Aspose.Words for .NET.
  headline: Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET
  type: TechArticle
- description: Learn to create a Word column chart and apply uniform data‑label font
    size and colour to all series with Aspose.Words for .NET.
  name: Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET
  steps:
  - name: Create a new empty Word document and a DocumentBuilder to edit it.
    text: Create a new empty Word document and a DocumentBuilder to edit it.
  - name: Insert a 500×300 column chart into the document and obtain its Chart object.
    text: Insert a 500×300 column chart into the document and obtain its Chart object.
  - name: Remove the default sample series that Aspose.Words adds to a new chart.
    text: Remove the default sample series that Aspose.Words adds to a new chart.
  - name: Define category labels and add two data series (Item Alpha and Item Beta)
      with their values to the chart.
    text: Define category labels and add two data series (Item Alpha and Item Beta)
      with their values to the chart.
  - name: Set baseline font size and colour that will be applied to all data labels.
    text: Set baseline font size and colour that will be applied to all data labels.
  - name: Enable data labels for each series, show the numeric value, and apply the
      predefined font size and colour.
    text: Enable data labels for each series, show the numeric value, and apply the
      predefined font size and colour.
  - name: Save the document to a .docx file.
    text: Save the document to a .docx file.
  type: HowTo
- questions:
  - answer: '`InsertChart` creates a chart with a default sample series; clearing
      it removes that placeholder so the chart only displays the series you add (`Item
      Alpha` and `Item Beta`).'
    question: Why do I need to call `chart.Series.Clear()` before adding my own series?
  - answer: Replace `Color.White` with any `System.Drawing.Color` value, e.g., `Color.Black`
      or `Color.FromArgb(255, 30, 144, 255)`; the new colour is applied via `series.DataLabels.Font.Color`
      inside the loop.
    question: How can I change the data‑label colour to something other than white?
  - answer: The data labels will be hidden, so the font settings you applied become
      invisible; you must keep `HasDataLabels` set to `true` for the labels (and their
      styling) to appear.
    question: What happens if I set `series.HasDataLabels = false` after configuring
      the font size and colour?
  - answer: Yes—each `ChartSeries` has its own `DataLabels` object, so any series
      added after the initial loop must also have `HasDataLabels`, `ShowValue`, and
      the font properties set, either by looping again or by extracting the styling
      into a helper method.
    question: Do I need to loop through the series again if I add another series later
      in the code?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Apply Uniform Data Labels to a Word Chart
og_description: Quickly give every chart label the same font size and color with Aspose.Words for .NET.
og_image_alt: Guide showing a Word document with a column chart where all data labels share the same font size and color, created using Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Set Uniform Data Labels in a Column Chart Using Aspose.Words
This tutorial shows how to generate a Word document, insert a column chart, and add custom data series with Aspose.Words for .NET. It then demonstrates defining default data‑label font size and colour so that every series in the chart displays identical labels. By applying a single style you ensure consistent visual appearance across the whole chart.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Why do I need to call `chart.Series.Clear()` before adding my own series?**  
A: `InsertChart` creates a chart with a default sample series; clearing it removes that placeholder so the chart only displays the series you add (`Item Alpha` and `Item Beta`).

**Q: How can I change the data‑label colour to something other than white?**  
A: Replace `Color.White` with any `System.Drawing.Color` value, e.g., `Color.Black` or `Color.FromArgb(255, 30, 144, 255)`; the new colour is applied via `series.DataLabels.Font.Color` inside the loop.

**Q: What happens if I set `series.HasDataLabels = false` after configuring the font size and colour?**  
A: The data labels will be hidden, so the font settings you applied become invisible; you must keep `HasDataLabels` set to `true` for the labels (and their styling) to appear.

**Q: Do I need to loop through the series again if I add another series later in the code?**  
A: Yes—each `ChartSeries` has its own `DataLabels` object, so any series added after the initial loop must also have `HasDataLabels`, `ShowValue`, and the font properties set, either by looping again or by extracting the styling into a helper method.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}