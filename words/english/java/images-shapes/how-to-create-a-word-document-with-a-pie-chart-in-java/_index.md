---
category: general
date: 2026-09-18
description: Learn to create a Word document and insert pie chart using Aspose.Words
  for Java. Includes rotate pie chart and generate Word file steps.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: en
lastmod: 2026-09-18
og_description: Create a Word document and insert a pie chart using Java. Follow this
  guide to rotate pie chart, explode slices, and generate a Word file.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Create a Word document with a pie chart – step‑by‑step Java guide
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: How to create a Word document with a pie chart in Java
url: /java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create a Word document with a pie chart in Java

If you need to **create a Word document** that visualizes data, this guide shows you how to do it with Aspose.Words for Java. You’ll learn to insert a pie chart, explode a slice, rotate the chart, and finally **generate a Word file** that you can open in Microsoft Word.

Building reports that combine text and charts doesn’t require a separate graphics tool. By the end of this tutorial you will have a complete, runnable program that creates a .docx file containing a fully configured pie chart.

## Prerequisites

- Java 17 or later (the code compiles with Java 8+ as well)
- Maven or Gradle for dependency management
- Aspose.Words for Java license (the free trial works for this example)
- Basic familiarity with Java syntax

## Step 1: Set up the Maven project

Create a new Maven project and add the Aspose.Words dependency to `pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Keep the version number up to date; newer releases add chart‑type improvements and bug fixes.

## Step 2: Create a new Word document

The first operation when you **create a Word document** programmatically is to instantiate a `Document` object. This object represents the entire .docx file in memory.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

The `Document` class is the entry point for all Word‑processing features. No file is written to disk at this point; everything happens in RAM until you call `save`.

## Step 3: How to insert a pie chart

A `DocumentBuilder` lets you add content to the document. With `insertChart` you can **insert pie chart** objects directly.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` tells Aspose.Words to create a pie chart. The dimensions are expressed in points (1 pt ≈ 1/72 in). After this call the chart appears on a new paragraph.

## Step 4: Populate the chart with data

A pie chart needs a series of values. Here we add three categories: “Apples”, “Bananas”, and “Cherries”.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

The `add` method builds the series and automatically creates legend entries. You can reuse this pattern for any numeric dataset.

## Step 5: Emphasize the first slice

Exploding a slice draws attention to a particular value. The first slice (index 0) is exploded by 20 points.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Setting `explode` on the series affects the entire chart, so only the first data point is offset.

## Step 6: How to rotate a pie chart

Rotating the chart improves visual balance, especially when the largest slice is not at the top. The `setRotationAngle` method expects degrees.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

A 45° rotation moves the start angle clockwise, making the chart easier to read in many layouts.

## Step 7: Save the document and generate a Word file

Finally, write the document to disk. This step **generate word file** that can be opened with Microsoft Word, LibreOffice, or any compatible viewer.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

The `save` method automatically detects the .docx extension and writes a Word‑compatible package. The folder `output` must exist or you can create it programmatically.

### Expected output

After running the program, open `output/PieChart.docx`. You should see:

- A single page containing a 400 × 300 pt pie chart.
- The “Apples” slice exploded outward by 20 pt.
- The entire chart rotated 45° clockwise.
- A legend matching the three fruit categories.

## Common variations and edge cases

### Inserting multiple charts

If you need more than one chart, call `builder.insertChart` again after moving the cursor:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Changing chart colors

You can customize slice colors via the series' `getPoints()` collection:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Handling large datasets

For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`) to keep the visual clear.

## Conclusion

You now know how to **create a Word document**, **insert pie chart**, **rotate pie chart**, and **generate a Word file** using Aspose.Words for Java. The complete solution demonstrates the full workflow from document initialization to final file output, covering both the “how” and the “why” behind each step.

Next, explore related topics such as **how to create pie chart** data from a database, adding data labels, or exporting the chart as an image. Experiment with different chart types (bar, line, doughnut) to broaden your Word‑automation toolkit.


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}