---
title: Format Secondary X‑Axis and Set Display Units to Thousands in Word Line Charts Using Aspose.Words for .NET
weight: 710
limit:
description: Create a Word line chart, add a secondary X‑axis, set its display unit to thousands, and apply a custom numeric format with Aspose.Words for .NET.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create a Word line chart, add a secondary X‑axis, set its display unit
    to thousands, and apply a custom numeric format with Aspose.Words for .NET.
  headline: Format Secondary X‑Axis and Set Display Units to Thousands in Word Line
    Charts Using Aspose.Words for .NET
  type: TechArticle
- description: Create a Word line chart, add a secondary X‑axis, set its display unit
    to thousands, and apply a custom numeric format with Aspose.Words for .NET.
  name: Format Secondary X‑Axis and Set Display Units to Thousands in Word Line Charts
    Using Aspose.Words for .NET
  steps:
  - name: Create a new Document and a DocumentBuilder to start building the Word file.
    text: Create a new Document and a DocumentBuilder to start building the Word file.
  - name: Insert a line chart of size 500×300 into the document and obtain the Chart
      object.
    text: Insert a line chart of size 500×300 into the document and obtain the Chart
      object.
  - name: Remove the default demo series that Aspose.Words adds automatically.
    text: Remove the default demo series that Aspose.Words adds automatically.
  - name: Define an array of category labels that will be used for the X‑axis.
    text: Define an array of category labels that will be used for the X‑axis.
  - name: Add the primary data series named "Main Data" using the labels and values.
    text: Add the primary data series named "Main Data" using the labels and values.
  - name: Create a secondary series group of type Line and assign it to the secondary
      axis group.
    text: Create a secondary series group of type Line and assign it to the secondary
      axis group.
  - name: Set the secondary X‑axis display unit to thousands so values are shown in
      K.
    text: Set the secondary X‑axis display unit to thousands so values are shown in
      K.
  - name: Apply a custom numeric format "#,##0.0" to the secondary X‑axis tick labels.
    text: Apply a custom numeric format "#,##0.0" to the secondary X‑axis tick labels.
  - name: Optionally add an auxiliary data series to the secondary group.
    text: Optionally add an auxiliary data series to the secondary group.
  - name: Save the document to a .docx file.
    text: Save the document to a .docx file.
  type: HowTo
- questions:
  - answer: No – the `AxisX` settings belong to the `ChartSeriesGroup`, so you can
      set `secondaryGroup.AxisX.DisplayUnit.Unit` and `secondaryGroup.AxisX.NumberFormat.FormatCode`
      before or after adding series; the configuration will apply to the group’s axis
      either way.
    question: Do I have to add the secondary series before setting the display unit
      and number format on the secondary X‑axis?
  - answer: Yes – assign any `AxisBuiltInUnit` value, e.g. `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;` to show the axis values in millions instead of
      thousands.
    question: Can I use a different built‑in unit, such as millions, for the secondary
      X‑axis?
  - answer: No – the format code is applied only to the axis you modify (`secondaryGroup.AxisX.NumberFormat.FormatCode`),
      so the primary X‑axis retains its default formatting.
    question: Will the custom format `"#,##0.0"` affect the primary X‑axis labels?
  - answer: The chart will contain the default demo series in addition to the ones
      you add, which can lead to extra lines and mismatched categories; clearing the
      collection ensures only your intended data appears.
    question: What happens if I forget to clear the demo series with `lineChart.Series.Clear();`?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Format Secondary X‑Axis and Set Units to Thousands
og_description: Add a secondary X‑axis to a Word line chart and format its labels in thousands with a custom pattern.
og_image_alt: Guide showing how to add a secondary X‑axis to a Word line chart and format its labels to display units in thousands using Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Format Secondary X‑Axis and Set Display Units to Thousands in Word Line Charts Using Aspose.Words
This tutorial walks you through creating a Word document that contains a line chart, adding a secondary X‑axis, and configuring that axis to show values in thousands. You’ll also learn how to apply a custom numeric format to the secondary axis labels, giving you precise control over how data is presented. Follow the steps to enhance the readability of multi‑axis charts in your Word reports.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: Do I have to add the secondary series before setting the display unit and number format on the secondary X‑axis?**  
A: No – the `AxisX` settings belong to the `ChartSeriesGroup`, so you can set `secondaryGroup.AxisX.DisplayUnit.Unit` and `secondaryGroup.AxisX.NumberFormat.FormatCode` before or after adding series; the configuration will apply to the group’s axis either way.

**Q: Can I use a different built‑in unit, such as millions, for the secondary X‑axis?**  
A: Yes – assign any `AxisBuiltInUnit` value, e.g. `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` to show the axis values in millions instead of thousands.

**Q: Will the custom format `"#,##0.0"` affect the primary X‑axis labels?**  
A: No – the format code is applied only to the axis you modify (`secondaryGroup.AxisX.NumberFormat.FormatCode`), so the primary X‑axis retains its default formatting.

**Q: What happens if I forget to clear the demo series with `lineChart.Series.Clear();`?**  
A: The chart will contain the default demo series in addition to the ones you add, which can lead to extra lines and mismatched categories; clearing the collection ensures only your intended data appears.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}