---
category: general
date: 2026-09-24
description: Learn how to create chart in Word using Java, insert a radial chart,
  and save document as docx with Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: en
lastmod: 2026-09-24
og_description: Create chart in Word with Java and Aspose.Words. This tutorial shows
  you how to add a radial chart, customize data, and save document as docx.
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: Create chart in Word with Java – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: How to create chart in Word with Java and Aspose.Words
url: /java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create chart in Word with Java and Aspose.Words

If you need to **create chart in Word** from a Java application, this guide walks you through the complete process. You’ll see how to add a radial chart, optionally populate its series, and finally **save document as docx** using the Aspose.Words for Java library.

Generating visual data inside a Word file is a common requirement for reporting, invoicing, or automated document generation. By the end of this tutorial you will be able to **create word document java** projects that **add chart to Word** files without any manual editing.

## Prerequisites

Before you start, make sure you have:

* Java Development Kit (JDK) 8 or newer.
* Maven or Gradle for dependency management.
* An IDE such as IntelliJ IDEA, Eclipse, or VS Code.
* A valid Aspose.Words for Java license (the free trial works for development).

These tools provide the foundation for the code examples that follow.

## Step 1: Set up the Maven project

Create a new Maven project (or update an existing one) and add the Aspose.Words dependency to your `pom.xml`:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

Running `mvn clean install` downloads the library and makes the classes such as `Document`, `DocumentBuilder`, and `ChartType` available on the classpath.

> **Pro tip:** Keep the library version up‑to‑date. New releases add chart types and improve rendering performance.

## Step 2: Create a new Word document

The first programmatic step to **create chart in Word** is to instantiate an empty `Document`. This object represents the entire `.docx` package.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` works like a cursor; it knows the current insertion point and provides methods for text, tables, and charts. At this point you have **created word document java** style – a clean canvas ready for content.

## Step 3: Insert a radial chart

Aspose.Words supports many chart types. To **insert radial chart**, call `insertChart` with `ChartType.RADIAL`. The method also requires the width and height in points (1 point ≈ 1/72 inch).

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

The returned `Shape` object contains the underlying chart object. The chart automatically renders graduations for a 24.9° layout, which is the default for radial charts in Word.

### Why use a radial chart?

A radial chart visualizes data that wraps around a circle, making it ideal for showing cyclical patterns (e.g., monthly sales, clock‑face metrics). The same API can insert bar, pie, or line charts, but the radial type adds a distinctive look without extra styling code.

## Step 4: (Optional) Populate the chart’s series data

If you want the chart to display real values, you need to add series and points. The following snippet adds a single series with three data points:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

You can repeat the `add` calls for as many points as needed. Aspose.Words automatically updates the visual representation, so you see the radial slices adjust to the new values.

> **Common question:** *What if I need to bind data from a database?*  
> Retrieve the rows, loop through them, and call `series.getDataPoints().add(value, label)` inside the loop. The API is thread‑safe and works with any `ResultSet` you provide.

## Step 5: Save the document as DOCX

When the chart is ready, the final step is to **save document as docx**. The `save` method determines the output format from the file extension.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

The generated file contains a fully functional radial chart that can be opened in Microsoft Word, LibreOffice, or any viewer that supports the DOCX format. Because we used the `.docx` extension, Word saves the file in the Open XML format, which is the modern standard for Word documents.

### Verifying the result

Open `RadialChartDemo.docx` in Word:

1. You should see a single page with a centered radial chart.
2. If you added series data, the chart displays four slices labeled Q1‑Q4.
3. Right‑click the chart → **Edit Data** to confirm the underlying data table.

If the chart appears blank, double‑check that you called `chart.getChart()` before adding series, and ensure the document builder’s cursor is positioned where you want the chart.

## Step 6: Advanced tips for working with charts

| Tip | Why it matters |
|-----|----------------|
| **Set chart style** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | Improves visual consistency without manually formatting each element. |
| **Resize after insertion** – `chart.setWidth(500); chart.setHeight(350);` | Allows you to fine‑tune the chart size based on page layout. |
| **Add a title** – `chart.getChart().getTitle().setText("Revenue Overview");` | Gives context to readers who view the document without the surrounding text. |
| **Export to PDF** – `doc.save("RadialChartDemo.pdf");` | Useful when you need a non‑editable version for distribution. |
| **License handling** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | Prevents the evaluation watermark in production builds. |

These enhancements are optional but demonstrate how you can further customize the chart after you have learned to **add chart to Word**.

## Conclusion

You now have a complete, self‑contained example that shows how to **create chart in Word** using Java, **insert radial chart**, optionally fill it with data, and **save document as docx**. The same pattern works for other chart types, so you can extend this tutorial to bar, line, or pie charts as needed.

Next you might explore:

* **create word document java** projects that combine tables, images, and multiple charts.
* Using **save document as docx** together with **save document as pdf** for multi‑format reporting.
* Adding dynamic data from REST APIs or databases to your charts.

Feel free to experiment with the styling options, chart dimensions, and data sources. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}