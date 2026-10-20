---
title: Customize X Axis Gridlines in a Column Chart Using Aspose.Words for .NET
weight: 610
limit:
description: Learn to add and color‑customize major X‑axis gridlines in a Word column chart with Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, column chart, customize x axis gridlines, word chart gridlines, primary x axis gridlines, chart formatting .NET]
url: /net/programming-with-charts/customize-x-axis-gridlines/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn to add and color‑customize major X‑axis gridlines in a Word column
    chart with Aspose.Words for .NET.
  headline: Customize X Axis Gridlines in a Column Chart Using Aspose.Words for .NET
  type: TechArticle
- description: Learn to add and color‑customize major X‑axis gridlines in a Word column
    chart with Aspose.Words for .NET.
  name: Customize X Axis Gridlines in a Column Chart Using Aspose.Words for .NET
  steps:
  - name: Create a new Word document and a DocumentBuilder to edit it.
    text: Create a new Word document and a DocumentBuilder to edit it.
  - name: Insert a 432×252 column chart into the document and obtain its Chart object.
    text: Insert a 432×252 column chart into the document and obtain its Chart object.
  - name: Remove the default series and add a custom series with three groups and
      values.
    text: Remove the default series and add a custom series with three groups and
      values.
  - name: Get a reference to the chart's primary horizontal (X) axis.
    text: Get a reference to the chart's primary horizontal (X) axis.
  - name: Enable the display of major gridlines on the primary X axis.
    text: Enable the display of major gridlines on the primary X axis.
  - name: Set the gridlines' color to blue and their weight to 2 points.
    text: Set the gridlines' color to blue and their weight to 2 points.
  - name: Save the document to a .docx file.
    text: Save the document to a .docx file.
  type: HowTo
- questions:
  - answer: 'Set the same axis property to false: `horizontalAxis.HasMajorGridlines
      = false;` toggles the visibility of the X‑axis major gridlines.'
    question: How do I hide the major gridlines again after enabling them?
  - answer: No, the `Format.Stroke` settings apply only to the axis you modify; to
      style the Y‑axis gridlines you must adjust `chart.AxisY.Format.Stroke` separately.
    question: Will changing `horizontalAxis.Format.Stroke.Color` also affect the Y‑axis
      gridlines?
  - answer: Use `horizontalAxis.Format.Stroke.Weight` and assign a double value (e.g.,
      `0.5`) to make the gridlines thinner.
    question: Which property controls the thickness of the X‑axis major gridlines?
  - answer: Yes, set `horizontalAxis.Format.Stroke.DashStyle` to a `DashStyle` enum
      value such as `DashStyle.Dash` or `DashStyle.Dot`.
    question: Can I change the dash pattern of the X‑axis major gridlines?
  type: FAQPage
images:
- /net/programming-with-charts/customize-x-axis-gridlines/og-image.png
og_title: Style X‑Axis Gridlines in a Word Column Chart
og_description: Turn on and color‑customize the primary X‑axis gridlines of a Word chart with Aspose.Words for .NET.
og_image_alt: Guide showing a Word document with a column chart where the primary X‑axis major gridlines are highlighted in a custom color using Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Customize X Axis Gridlines in a Column Chart Using Aspose.Words
In this tutorial you’ll learn how to create a Word document, insert a column chart, replace its default data, and then enable the major gridlines on the primary X axis. You’ll also see how to change the gridlines’ line color to match your design. Follow the step‑by‑step code to get precise control over X‑axis gridline visibility and styling.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/customize-x-axis-gridlines" >}}


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

**Q: How do I hide the major gridlines again after enabling them?**  
A: Set the same axis property to false: `horizontalAxis.HasMajorGridlines = false;` toggles the visibility of the X‑axis major gridlines.

**Q: Will changing `horizontalAxis.Format.Stroke.Color` also affect the Y‑axis gridlines?**  
A: No, the `Format.Stroke` settings apply only to the axis you modify; to style the Y‑axis gridlines you must adjust `chart.AxisY.Format.Stroke` separately.

**Q: Which property controls the thickness of the X‑axis major gridlines?**  
A: Use `horizontalAxis.Format.Stroke.Weight` and assign a double value (e.g., `0.5`) to make the gridlines thinner.

**Q: Can I change the dash pattern of the X‑axis major gridlines?**  
A: Yes, set `horizontalAxis.Format.Stroke.DashStyle` to a `DashStyle` enum value such as `DashStyle.Dash` or `DashStyle.Dot`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}