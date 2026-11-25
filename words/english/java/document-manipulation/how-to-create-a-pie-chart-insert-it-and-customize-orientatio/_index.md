---
category: general
date: 2026-11-25
description: Learn how to create a pie chart in Java, insert pie chart into a Word
  document, explode pie slice and change chart orientation with clear code examples.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: en
lastmod: 2026-11-25
og_description: Create a pie chart in Java, insert pie chart into a document, explode
  pie slice and change chart orientation with step‑by‑step code.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Create a pie chart in Java – insert, explode slice, and rotate
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: How to create a pie chart, insert it, and customize orientation in Java
url: /java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create a pie chart, insert it, and customize orientation in Java

If you need to **create a pie chart** inside a Word document, this guide shows you exactly how to do it. You’ll see how to **insert pie chart**, explode a slice for emphasis, and **change chart orientation** with a simple rotation.

The tutorial covers everything you need—from setting up the Aspose.Words for Java library to producing a final `.docx` file that displays a rotated, exploded pie chart. No external documentation is required; just follow the steps and run the code.

## Prerequisites

Before you start, make sure you have:

* Java 17 or newer installed.
* Maven or Gradle to manage dependencies.
* A valid Aspose.Words for Java license (or use the free evaluation mode).

Add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). Example for Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Pro tip:** Keep the library version up‑to‑date; the latest release (24.10 at the time of writing) includes bug fixes for chart rendering.

## Step 1: Create pie chart and insert it into the document

The first step is to **create pie chart** objects and embed them in a Word file. The code below builds a simple document, adds a chart placeholder, and inserts a pie chart of size 400 × 300 pixels.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Why this matters:** `builder.insertChart` creates a chart placeholder that Aspose.Words automatically converts to an OOXML chart when the document is saved. The `ChartType.PIE` argument tells the library to render a pie chart, satisfying the **insert pie chart** requirement.

## Step 2: Explode pie slice to highlight a segment

Exploding a slice draws attention to a particular data point. The following line explodes the first slice (index 0) by 10 points:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

You can change the index to target a different slice, or adjust the explode distance for a subtler effect. Exploding a slice is the standard way to **explode pie slice** in Aspose.Words.

## Step 3: Change chart orientation by rotating it

Rotating the chart gives a fresh visual perspective. Use `setRotationAngle` to rotate the whole chart clockwise (the angle is measured in degrees).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

The call above satisfies the **rotate pie chart** and **change chart orientation** requirements. Any angle between 0 and 360 degrees is accepted.

## Full runnable example

Putting everything together, here is a complete, self‑contained program that creates a pie chart, explodes a slice, and rotates the chart. Run it from your IDE or from the command line with `java -cp <classpath> PieChartDemo`.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Expected output

* A file named **CreatePieChartDemo.docx** appears in the working directory.
* Opening the file in Microsoft Word shows a 400 × 300 pixel pie chart.
* The first slice (Q1) is offset outward by 10 points, creating an **explode pie slice** effect.
* The whole chart is tilted 45 degrees, demonstrating **change chart orientation** and **rotate pie chart**.

## Common variations and edge cases

| Situation | How to adapt the code |
|-----------|-----------------------|
| **Different chart size** | Change the `400, 300` arguments in `insertChart`. |
| **Multiple series** | Add more `ChartSeries` objects to `chart.getSeries()`. |
| **Explode a different slice** | Use `setExplode(sliceIndex, distance)` with the desired `sliceIndex`. |
| **No rotation needed** | Omit the `setRotationAngle` call or set the angle to `0`. |
| **Export to PDF instead of DOCX** | After building the document, call `doc.save("output.pdf")` with the PDF format. |

> **Watch out for:** Using a negative explode distance throws `IllegalArgumentException`. Always provide a non‑negative value.

## Performance tip

If you generate many charts in a loop, reuse a single `DocumentBuilder` and only call `insertChart` for each iteration. This reduces memory overhead and speeds up processing.

## Conclusion

You now know how to **create pie chart**, **insert pie chart**, **explode pie slice**, and **rotate pie chart** using Aspose.Words for Java. The complete example demonstrates the full workflow—from initializing the document to saving a file that visualizes a rotated, exploded pie chart.

Next, you might explore **changing chart orientation** further by applying 3‑D effects, or experiment with other chart types such as **Bar** or **Line**. The same API patterns apply, so extending this tutorial is straightforward.

Feel free to modify the data, slice index, or rotation angle to match your own reporting needs, and share your results with the community!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}