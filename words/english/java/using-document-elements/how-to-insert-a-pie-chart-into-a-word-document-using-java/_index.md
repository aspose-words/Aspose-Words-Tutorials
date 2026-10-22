---
category: general
date: 2026-09-27
description: Learn how to insert pie chart into a Word document with Java, create
  pie chart in Word, and show percentages on pie chart for clear data insight.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: en
lastmod: 2026-09-27
og_description: How to insert pie chart into a Word document with Java. This guide
  shows you how to create pie chart in Word, show percentages on pie chart, and add
  leader lines.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: How to insert a pie chart into a Word document using Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: How to insert a pie chart into a Word document using Java
url: /java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to insert a pie chart into a Word document using Java

If you need to **how to insert pie chart** into a Word file, this guide walks you through the complete process. You’ll see how to **create pie chart in Word**, display percentages on each slice, and add leader lines for a polished look.

Word automation often feels heavyweight, but with Aspose.Words for Java you can generate fully formatted documents programmatically. By the end of this tutorial you will have a runnable Java snippet that produces a Word document containing a styled pie chart.

## Prerequisites

Before you start, make sure you have:

- Java 17 or later installed
- Maven or Gradle to manage dependencies
- Aspose.Words for Java (version 23.11 or newer) added to your project
- Basic familiarity with Java syntax

You do not need any prior experience with chart APIs; the steps below cover everything from project setup to final output.

## Step 1: Set up the Maven dependency

Add the Aspose.Words library to your `pom.xml`. This single dependency gives you access to `Document`, `DocumentBuilder`, and chart classes.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

If you use Gradle, the equivalent is:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Pro tip:** Use the latest stable version to benefit from bug fixes and new chart features.

## Step 2: Create a new document and a builder

The `Document` object represents the Word file, while `DocumentBuilder` lets you insert content. This is the foundation for **add chart to word document**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

The builder is now ready to place objects anywhere in the document.

## Step 3: Insert a pie chart

Aspose.Words supports several chart types; we choose `ChartType.PIE`. The size is expressed in points (1 point = 1/72 inch).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

At this stage the chart contains a default data series with placeholder values. You can replace those values later if needed.

## Step 4: Access the chart series

A pie chart has a single series that holds the slice values. Retrieve it to apply formatting.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Step 5: Explode the first slice

Exploding a slice draws attention to a particular data point. This is a common visual cue when you want to highlight a key metric.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Step 6: Show percentages on each slice

Displaying percentages directly on the chart improves data insight. This satisfies the **show percentages on pie chart** requirement.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Step 7: Add leader lines for clearer labels

Leader lines connect slice labels to their corresponding sections, eliminating ambiguity. This fulfills **how to add leader lines**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Step 8: Save the document

Finally, write the document to disk. You can choose any folder you have write access to.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

Running the program creates `output/PieFormatted.docx`. Open the file in Microsoft Word, and you’ll see a pie chart where:

- The first slice is exploded.
- Each slice shows its percentage value.
- Leader lines point from percentages to the corresponding slices.

### Expected output

![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image alt="Formatted pie chart inserted into a Word document"}

The screenshot (alt text uses the primary keyword) illustrates the final appearance: a clean, data‑driven pie chart ready for reports, proposals, or dashboards.

## Common variations and edge cases

### Changing slice values

If you need custom data, replace the default series values:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Multiple series (donut chart)

While a simple pie chart has one series, Aspose.Words also supports donut charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and repeat the series‑configuration steps.

### Exporting to PDF

If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");` after the chart is built. The visual layout remains identical.

## Full source listing

Below is the complete, self‑contained Java file you can copy‑paste into your IDE.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Compile and run the program with `mvn compile exec:java -Dexec.mainClass=PieChartExample` (or the equivalent Gradle command). The generated Word file will contain the fully formatted pie chart.

## Conclusion

You now know **how to insert pie chart** into a Word document using Java, how to **create pie chart in Word**, how to **show percentages on pie chart**, and how to **add chart to word document** with leader lines. The complete example demonstrates each step, explains why the code is written that way, and provides tips for customization.

Next, you might explore:

- Adding data labels with custom fonts (**show percentages on pie chart** variations)
- Combining multiple charts in a single document (**add chart to word document** use case)
- Automating report generation with tables and charts together

Feel free to experiment with colors, slice ordering, or exporting to PDF. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}