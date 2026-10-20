---
category: general
date: 2026-09-11
description: Save Word document after editing a doughnut chart with Aspose.Words for
  Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit doughnut
  chart properties.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: en
lastmod: 2026-09-11
og_description: Save Word document after editing a doughnut chart using Aspose.Words
  for Java. This tutorial shows how to change the doughnut hole size, rotate the doughnut
  chart, and customize chart appearance.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Save Word document after editing doughnut chart – Java guide
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Save Word document after editing doughnut chart in Java
url: /java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Save Word document after editing doughnut chart in Java

If you need to **save Word document** that contains a customized doughnut chart, this guide shows you exactly how. In just a few lines of Java you can change the doughnut hole, rotate the doughnut chart, and then write the result back to disk.

You’ll see a complete, runnable example that uses Aspose.Words for Java, plus tips for handling multiple charts, verifying node types, and avoiding common pitfalls. No external references are required—everything you need is included.

## Prerequisites

Before you start, make sure you have:

- Java 17 or newer installed
- Maven or Gradle to manage dependencies
- Aspose.Words for Java (version 23.9 or later) added to your project  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- A Word file (`input.docx`) that contains a single doughnut chart

## Step 1: Load the Word document

The first step is to open the source file. This step is essential because every subsequent operation works on the in‑memory `Document` object.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Why?** Loading the document creates a DOM representation that lets you traverse shapes, tables, and charts. If the file cannot be opened, Aspose.Words throws an exception, so you know immediately that the path is wrong.

## Step 2: Locate the doughnut chart shape

A chart is stored inside a `Shape` node. We retrieve the first shape that hosts a chart and cast its renderer to `Chart`.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Why?** Checking `isChart()` prevents a `ClassCastException` when the document contains images or other shapes before the chart. This makes the code robust for documents with mixed content.

## Step 3: Change doughnut hole size  

Now we edit the doughnut hole. The `setHoleSize` method expects a percentage of the chart radius (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Why?** Changing the doughnut hole (`change doughnut hole` / `change chart hole size`) lets you emphasize or de‑emphasize the central area. Values outside 10‑90 % are ignored by the API.

## Step 4: Rotate the doughnut chart  

To control where the first slice starts, set the first‑slice angle. This effectively **rotate doughnut chart**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Why?** Rotating the chart is useful when you want a particular slice to appear at the top or to match a design specification.

## Step 5: Save the updated document  

Finally, write the changes back to a new file. This is the moment where you **save Word document** with the edited chart.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Expected result:** `output.docx` contains the original content, but the doughnut chart now has a 30 % hole and its first slice begins at 45 °. Opening the file in Microsoft Word will display the transformed chart.

## Full working example

Below is the complete program you can copy‑paste into your IDE. It includes all imports and error handling needed to **edit doughnut chart** and **save Word document** safely.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Expected output

When you open `output.docx`:

- The doughnut chart’s central hole occupies roughly one‑third of the chart radius.  
- The first slice begins at the 45‑degree position, shifting the whole chart clockwise.  

Both visual changes are reflected instantly in Word.

## Common variations and edge cases

| Situation | How to handle |
|-----------|----------------|
| **Multiple charts** | Iterate through `doc.getChildNodes(NodeType.SHAPE, true)` and filter `shape.isChart()`; apply `setHoleSize` / `setFirstSliceAngle` to each `Chart`. |
| **Chart is not a doughnut** | Check `chart.getType()`; only call `setHoleSize` when `chart.getType() == ChartType.DOUGHNUT`. |
| **Need to change hole size dynamically** | Compute the desired percentage based on data values, then call `setHoleSize(computedValue)`. |
| **Saving to a stream** | Use


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Save Word with Password using Aspose.Words for Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}