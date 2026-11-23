---
category: general
date: 2026-11-22
description: Create pie chart in Java and learn how to set chart size, add data labels,
  show percentages, and rotate the first slice for clear visual impact.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: en
lastmod: 2026-11-22
og_description: Create pie chart in Java, then set chart size, show percentages on
  data labels, and rotate the first slice—all in a single, runnable example.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Create pie chart with custom size, labels, and rotation in Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Create pie chart with custom size, data labels, and rotation in Java
url: /java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create pie chart with custom size, data labels, and rotation in Java

If you need to **create pie chart** in Java, this guide walks you through the entire process. You’ll learn how to **set chart size**, enable **show percentages pie chart**, add **data labels pie chart**, and **rotate pie chart slice** so the first slice starts at a 45‑degree angle.

The example uses **Aspose.Slides for Java**, a widely‑used library for manipulating PowerPoint files. The same concepts apply to other charting libraries; just replace the API calls with the equivalents in your toolkit.

## Prerequisites

Before you start, make sure you have:

* Java 17 or later installed  
* Maven 3.8+ (or Gradle) for dependency management  
* A basic understanding of Java syntax  
* Access to the Aspose.Slides for Java binary (you can obtain a free trial from the official site)

Add the dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Create pie chart – full example

The following program creates a PowerPoint slide that contains a pie chart with a custom size, percentage data labels, and a rotated first slice.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Why each step matters

| Step | Purpose | How it relates to the keywords |
|------|---------|--------------------------------|
| **Insert chart** | **Create pie chart** – the core object that will render the visual. | Directly satisfies the *create pie chart* requirement. |
| **Set dimensions** | The `addChart(..., 400, 300)` call demonstrates **set chart size**. | Controls the width (400 px) and height (300 px). |
| **Show percentages** | `setShowPercentage(true)` makes the chart **show percentages pie chart** on each slice. | Users often need percentages instead of raw values. |
| **Add data labels** | The `DataLabelFormat` configuration adds **data labels pie chart** with the desired visibility. | Labels improve readability and are customizable. |
| **Rotate slice** | `setFirstSliceAngle(45)` rotates the chart so the first slice starts at a 45‑degree angle, fulfilling **rotate pie chart slice**. | Improves visual emphasis for a particular slice. |

## Step‑by‑step breakdown

### 1. Insert a pie chart and set chart size

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*The `addChart` method creates the chart and simultaneously **set chart size** to 400 × 300 points.*  
If you need a different size, adjust the last two arguments.

### 2. Populate the chart with data

The demo adds three categories and a single series. Replace the hard‑coded numbers with data from a database, CSV, or user input as needed.

### 3. Show percentages on each slice

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*Enabling `setShowPercentage(true)` ensures the chart **show percentages pie chart** automatically calculates each slice’s share of the total.*

### 4. Add detailed data labels

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

You can toggle other label options (`setShowValue`, `setShowSeriesName`, etc.) to tailor the **add data labels pie chart** experience.

### 5. Rotate the first slice

```java
chart.setFirstSliceAngle(45);
```

*Calling `setFirstSliceAngle(45)` **rotate pie chart slice** so the first segment begins at a 45‑degree angle, making it stand out.*

### 6. Save and view the result

Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint or any compatible viewer to see the final pie chart:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="Screenshot of a created pie chart with custom size, percentage labels, and a rotated first slice"}

The image above demonstrates the **create pie chart** outcome, confirming that the size, labels, percentages, and rotation are applied correctly.

## Common variations and edge cases

| Situation | Adjustment |
|-----------|------------|
| **Different chart dimensions** | Change the width/height parameters in `addChart`. |
| **Multiple series** | Add additional `IChartSeries` objects; each series can have its own label settings. |
| **Custom label format** | Use `series.getDataLabelFormat().setNumberFormat("0.0%")` to control decimal places. |
| **Rotating to another angle** | Pass any integer (0‑360) to `setFirstSliceAngle`. |
| **Export as image** | After saving, call `chart.writeAsSvg(outPath)` or `chart.writeAsPng(outPath)` for a raster version. |

> **Pro tip:** If you plan to generate many charts in a loop, reuse the same `Presentation` object and only replace the chart data. This reduces memory overhead and speeds up processing.

## Conclusion

You now know how to **create pie chart** in Java, **set chart size**, enable **show percentages pie chart**, **add data labels pie chart**, and **rotate pie chart slice** for better visual emphasis. The complete, runnable example demonstrates every step from initialization to saving the final PowerPoint file.

### What’s next?

* Explore other chart types (Bar, Line, Area) using the same `ChartType` enum.  
* Combine multiple charts on a single slide for dashboards.  
* Export charts to PNG or SVG for use in web applications.  

Feel free to experiment with colors, legends, and animation effects—your data visualizations are only limited by imagination. Happy charting!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [how to insert pie chart in Word – add data label percent](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Insert Pie Chart in Java – Explode, Rotate & Highlight Slices](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}