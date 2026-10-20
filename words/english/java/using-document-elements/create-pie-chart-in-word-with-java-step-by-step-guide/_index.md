---
category: general
date: 2026-08-14
description: Create pie chart in Word with Java using Aspose.Words. Learn how to add
  series data to chart and rotate pie chart slice in just a few lines.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: en
lastmod: 2026-08-14
og_description: Create pie chart in Word with Java using Aspose.Words. This tutorial
  shows how to add series data to chart and rotate pie chart slice quickly.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Create pie chart in Word with Java – complete coding guide
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Create pie chart in Word with Java – step-by-step guide
url: /java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create pie chart in Word with Java – step‑by‑step guide

If you need to **create pie chart in Word** programmatically, this guide shows you exactly how to do it with Java and Aspose.Words. You’ll learn the complete workflow, from inserting the chart to adding data points and rotating the first slice.

Generating a chart directly in a `.docx` file removes the manual copy‑paste step and lets you automate reports, invoices, or dashboards. Along the way we’ll also cover **how to add series data to chart** and how to **rotate pie chart slice** for better visual emphasis.

## Create pie chart in Word – overview

Aspose.Words for Java provides a fluent `DocumentBuilder` API that can insert a chart object into a Word document. The chart type you choose determines the default layout, and you can customize the series, colors, angles, and even switch to a doughnut shape with a single method call.

### Why use Aspose.Words?

* **No Microsoft Office required** – the library works on any server or CI environment.  
* **Full .docx fidelity** – the generated chart looks identical to one created manually in Word.  
* **Single‑file dependency** – just add the JAR and you’re ready to go.

## How to add series data to chart

A chart without data is just a placeholder. The `Chart` object exposes a `Series` collection; each series holds a list of numeric values that map to slices (for a pie) or points (for a line). Adding data is straightforward:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**What the code does:**  
* `chart.getSeries()` returns a `List<ChartSeries>`.  
* `get(0)` selects the first series because a pie chart contains only one series by definition.  
* `add(double)` appends a data point. The values are automatically converted to percentages that sum to 100 % when the chart renders.

> **Pro tip:** If your data source contains more than three categories, keep adding values in the same way. Aspose.Words will automatically create additional slices.

## Rotate pie chart slice

Sometimes you want a particular slice to start at a specific angle so that the most important segment faces the viewer. The `setFirstSliceAngle(double)` method rotates the whole chart, effectively moving the start of the first slice:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

The angle is measured in degrees clockwise from the vertical axis. Setting it to `0` (the default) places the first slice at the top. Adjust the value to highlight a slice or to match a design guideline.

> **Common question:** *Does rotating affect the data order?*  
> No. The data order stays the same; only the visual starting position changes.

## Full Java example

Below is a complete, ready‑to‑run program that creates a Word document with a pie chart, adds series data, rotates the slice, and saves the file. All required imports are listed, so you can copy the code into any IDE.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Expected output

* A file named **PieChart.docx** appears in the `output` folder.  
* Opening the file in Microsoft Word shows a colorful pie chart with three slices (40 %, 30 %, 30 %).  
* The chart is rotated 45° clockwise, so the first slice starts slightly to the right of the vertical axis.

## Common pitfalls and best practices

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| **Chart appears blank** | The document was saved before the chart was fully rendered. | Call `doc.save()` **after** all chart modifications. |
| **Slice values don’t sum to 100 %** | Adding raw numbers that don’t represent percentages can lead to unexpected scaling. | Provide values that logically represent portions of a whole, or let Aspose.Words calculate percentages automatically. |
| **Rotation has no effect** | Using `ChartType.DOUGHNUT` without setting `holeSize` may hide the rotation effect. | Keep the chart as `PIE` or adjust `holeSize` after setting the angle. |
| **File path errors** | Relative paths may resolve differently on Windows vs. Linux. | Use `Paths.get("output", "PieChart.docx").toString()` or an absolute path for production code. |

### Tips for production use

* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the same document by calling `insertChart` repeatedly.  
* **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` to display percentages directly on the chart.  
* **Performance** – generate the chart once and clone it (`chart.deepClone()`) if you need identical charts in multiple places.

## Rotate pie chart slice – advanced scenarios

* **Dynamic angle** – calculate the angle based on data (e.g., make the largest slice start at the top).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Multiple series** – while a pie chart normally has one series, Aspose.Words lets you add more for stacked pies. The rotation still applies to the first series only.

## Conclusion

You now know how to **create pie chart in Word** using Java, how to **add series data to chart**, and how to **rotate pie chart slice** for visual emphasis. The complete example demonstrates the entire workflow—from document initialization to saving the final `.docx` file—so you can integrate chart generation into any automated reporting pipeline.

### What’s next?

* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden your automation toolkit.  
* Combine chart generation with **mail merge** to produce personalized reports for each recipient.  
* Dive into the **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`) to match your corporate branding.

Feel free to experiment with different data sets, angles, and chart styles. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}