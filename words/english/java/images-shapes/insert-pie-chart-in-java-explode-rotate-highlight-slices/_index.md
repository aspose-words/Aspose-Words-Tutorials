---
category: general
date: 2026-07-20
description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
  slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
  slice.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: en
lastmod: 2026-07-20
og_description: Insert pie chart in Java and master how to explode slice, how to rotate
  pie chart, highlight pie chart slice, and customize pie chart slice for polished
  visual reports.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Insert Pie Chart in Java – Explode, Rotate & Highlight
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
url: /java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert Pie Chart in Java – Explode, Rotate & Highlight Slices

Ever needed to **insert pie chart** in a Java report but weren’t sure how to make a single slice pop out? You’re not the only one. Whether you’re building a dashboard, generating an invoice, or just visualizing survey results, a well‑styled pie chart can turn raw numbers into instantly understandable insight.

In this tutorial you’ll see a complete, ready‑to‑run example that shows you how to insert a pie chart, **how to explode slice**, **how to rotate pie chart**, and even **highlight pie chart slice** with custom colors. By the end you’ll have a reusable snippet you can drop into any Java project that uses the popular *JFreeChart* library (or any similar API).

## Prerequisites

- Java 17 or later (the code compiles with older versions, but we’ll use the modern `var` syntax for brevity).  
- Maven or Gradle to pull in the `org.jfree:jfreechart` dependency.  
- A basic understanding of Java classes and the concept of a chart builder.  

If you’ve never added a library to a Maven project, just pop this into your `pom.xml`:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

That’s it—no extra setup required.

## Step 1: Insert Pie Chart – Create the Builder and Chart Object

First things first: we need a *builder* (think of it as a factory) that knows how to produce charts. In JFreeChart the `ChartFactory` does the heavy lifting.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

Why do we start with the dataset? Because the chart itself is just a visual wrapper around the numbers. By **inserting pie chart** here we already have a 400 × 300 canvas (the size will be applied later when we render it to an image).

## Step 2: How to Explode Slice – Emphasize the First Segment

Now that the chart exists, let’s make the first slice stand out. Exploding a slice draws it slightly away from the circle, drawing the reader’s eye.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

Notice we use the **how to explode slice** phrase in the method name; that makes the intent crystal clear. The `setExplodePercent` method takes a key (the slice label) and a percentage, so you can adjust the “pop‑out” distance as needed.

## Step 3: How to Rotate Pie Chart – Change the Starting Angle

A default pie chart starts at the 12 o’clock position. Sometimes you want the first slice to begin elsewhere—maybe to align with a design mock‑up or to match another chart.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

Calling `rotateChart(chart, 45)` rotates the whole pie so the “Apples” slice begins at a 45‑degree angle, exactly what the **how to rotate pie chart** requirement asks for.

## Step 4: Highlight Pie Chart Slice – Custom Colors and Labels

Beyond exploding, you might want to give a slice a unique color or a bold label to truly **highlight pie chart slice**.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

Here we’ve **customize pie chart slice** by altering its paint and label style. Feel free to swap out the color or font to match your brand palette.

## Step 5: Render the Chart to an Image (Optional but Handy)

Most real‑world apps need the chart as a PNG, JPEG, or even a PDF. Below is a quick way to write the chart to a file.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

Running the full flow will produce a 400 × 300 PNG that looks something like this:

![Insert pie chart example](image.png){: alt="Insert pie chart example showing an exploded and rotated slice"}

## Full Working Example

Putting it all together, here’s a `main` method you can copy‑paste into a fresh Java class and execute:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### Expected Output

Running the program creates a file called **fruit-pie.png**. Open it and you’ll see:

- A 400 × 300 pie chart titled “Fruit Distribution”.  
- The “Apples” slice exploded outward by 15 %.  
- The entire chart rotated so “Apples” starts at the 45‑degree position.  
- The exploded


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Insert Scatter Chart](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Insert Area Chart](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}