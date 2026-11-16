---
category: general
date: 2026-11-15
description: Learn how to add a pie chart to a Word document with Aspose.Words for
  Java. Includes doughnut conversion, exploded slice, and full code sample.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: en
lastmod: 2026-11-15
og_description: Add a pie chart to a Word document using Aspose.Words for Java. This
  tutorial shows how to explode a slice and turn the chart into a doughnut.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Add a pie chart to a Word document with Java – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: How to add a pie chart to a Word document using Java
url: /java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Add a pie chart to a Word document – complete Java guide

If you need to **add a pie chart to a Word document** programmatically, this tutorial shows you exactly how to do it with Aspose.Words for Java. You’ll see the full workflow: loading a DOCX, creating a pie chart, exploding the first slice, and converting the chart into a doughnut by setting a hole size.

The guide also covers common variations—such as adding multiple series, customizing colors, and handling documents that already contain charts—so you can adapt the code to real‑world projects like automated reporting or dynamic presentations.

## Prerequisites

Before you start, make sure you have:

* Java 17 or later (the code compiles with JDK 11+ as well)
* Maven 3.6+ or Gradle for dependency management
* An Aspose.Words for Java license (the free trial works for testing)
* A basic understanding of Java syntax and Maven project structure

## Step 1: Set up the Maven project and import Aspose.Words

Create a new Maven project (or add to an existing one) and include the Aspose.Words dependency:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** If you use Gradle, the equivalent entry is `implementation 'com.aspose:aspose-words:24.9'`.

The dependency brings in the `Document`, `Chart`, and `ChartType` classes you’ll need to manipulate charts.

## Step 2: Load the target document

You can start from an existing `.docx` file or create a new blank document. The example below loads a template called `input.docx` located in the `src/main/resources` folder.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

If the file does not exist, Aspose.Words will create a new empty document automatically when you call `new Document()` without a file name.

## Step 3: Create a pie chart and insert it into the document

Aspose.Words treats a chart as a shape that can be placed anywhere a paragraph can appear. The following code creates a **pie chart**, adds a single data series, and inserts the chart after the first paragraph.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Why this step matters:**  
* `ChartType.PIE` tells Aspose.Words to render a traditional pie chart.  
* Adding a series with both category labels and numeric values populates the slices automatically.  
* Inserting the chart as a child of a `Paragraph` keeps the document’s flow intact.

## Step 4: Explode the first slice to highlight it

An *exploded slice* draws attention to a particular data point. The API exposes `setExplode(boolean)` on a `ChartSeries` object. Setting it on the first series (index 0) makes the first slice pop out.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Common question:** *What if I have multiple series?*  
> You can target a specific series by its index, e.g., `pieChart.getSeries().get(1).setExplode(true)` for the second series.

## Step 5: Convert the pie chart into a doughnut by setting a hole size

A doughnut chart is essentially a pie chart with a hollow center. Aspose.Words lets you define the hole size as a percentage of the chart’s radius.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

The `setHoleSize` method accepts values from **0** (regular pie) to **100** (completely empty). A value around **30‑40** yields a visually balanced doughnut.

## Step 6: Save and verify the result

After all modifications, save the document. The following line writes the file to the `output` folder.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Expected output

Open `final-pie-doughnut.docx` in Microsoft Word:

* A doughnut chart appears where the first paragraph was.
* The “Apples” slice is exploded (slightly separated from the rest).
* The chart shows four slices labeled *Apples*, *Bananas*, *Cherries*, *Dates* with the percentages you supplied.

If you prefer PDF output, change the `SaveFormat` to `SaveFormat.PDF`.

## Handling edge cases and variations

### Adding multiple series

If you need several series (e.g., stacked doughnut), add them sequentially:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Custom colors

You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Working with an existing chart

If the document already contains a chart and you only want to modify it, locate the chart shape:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### License handling

Aspose.Words requires a license for production use. Place your `Aspose.Words.lic` file in the classpath and load it at application start:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

Failing to set a license will add a watermark to the generated document.

## Full, runnable example

Below is the complete Java class that incorporates every step discussed. Copy it into `src/main/java/com/example/AddPieChart.java` and run `mvn compile exec:java`.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

Running the program produces the doughnut chart described earlier. Adjust the `categories`, `values`, or `holeSize` to suit your data.

## Conclusion

You now know how to **add a pie chart to a Word document** using Java and Aspose.Words. The tutorial covered loading a document, creating a pie chart, exploding a slice, turning the chart into a doughnut, and handling common variations such as multiple series, custom colors, and existing charts. With this foundation you can build automated reporting tools, generate dynamic presentations, or embed rich visualizations directly into Word files.

### What to explore next

* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
* **customize chart legends and titles** – use `pieChart.getTitle().setText("...")` and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`.
* **export the Word document as PDF** – change the `SaveFormat` to `PDF` for distribution‑ready files.
* **populate chart data from a database** – replace the static arrays with JDBC query results.

Feel free to experiment with different chart types, data sources, and styling options. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}