---
category: general
date: 2026-11-15
description: Learn how to create pie chart in a Word document and save docx as PDF
  using Java. This guide also covers convert word to pdf and how to add chart.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: en
lastmod: 2026-11-15
og_description: Create pie chart in a Word file and save docx as PDF with Java. Follow
  this step‑by‑step tutorial to convert word to pdf and add charts.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Create a pie chart in Word and save docx as PDF – Java guide
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: How to create pie chart in Word and save docx as PDF
url: /java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create pie chart in Word and save docx as PDF

If you need to **create pie chart** inside a Word document and then **save docx as PDF**, this tutorial shows you exactly how. You’ll see a complete, runnable example that converts a .docx file to a PDF while embedding a pie chart, so you can answer “how to add chart” without hunting for scattered snippets.

In this guide you’ll learn to:

* Load an existing *.docx* (or start from scratch)  
* Use Aspose.Words for Java to **create pie chart** and populate data  
* **Save docx as PDF** with the chart rendered correctly  
* Understand the nuances of **convert word to pdf** when charts are involved  

The steps work with Aspose.Words 2024‑x.x and Java 17, but the concepts apply to any library that supports Word chart manipulation.

## Prerequisites

Before you start, make sure you have:

| Requirement | Why it matters |
|-------------|----------------|
| Java 17 (or later) | Required by the latest Aspose.Words JAR |
| Maven or Gradle build tool | Simplifies dependency management |
| Aspose.Words for Java (latest version) | Provides `Document`, `Chart`, and `ChartType` classes |
| An input **.docx** file (or a blank document) | The chart will be inserted into this file |

Add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). Example for Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Step 1: Load the Word document (or create a new one)

The first action is to obtain a `Document` instance. If you already have a template, pass its path; otherwise create an empty document.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Why this step?* The `Document` object is the container for all Word content, including charts. Loading an existing file lets you preserve surrounding text and styles while adding a new visual element.

## Step 2: **Create pie chart** – the core of “how to create chart”

Now we instantiate a `Chart` object with `ChartType.PIE`. This automatically creates a pie chart placeholder that you can later fill with data.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Explanation*: `ChartType.PIE` tells Aspose.Words to use a pie‑chart template. The chart is added to the document’s body, so it appears where you need it. This satisfies the “how to add chart” requirement in a single call.

## Step 3: Populate the chart – answering “how to add chart” with data

A pie chart is meaningless without series data. Use the `Series` collection to add categories and values.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Why this matters*: Each call to `add` creates a slice of the pie. The first argument is the label, the second is the numeric value. You can replace these with dynamic data from a database or CSV file.

### Optional: Customize appearance (not required but useful)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

These tweaks illustrate how you can **how to create chart** with a professional look, without leaving the Java code.

## Step 4: **Save docx as PDF** – the final part of “convert word to pdf”

Once the chart is embedded, export the document to PDF. Aspose.Words renders the chart as a vector graphic, preserving quality.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Key point*: The `save` method automatically converts the Word file to PDF, handling chart rasterization, font embedding, and page layout. This fulfills the **save docx as pdf** goal and demonstrates a reliable way to **convert word to pdf** when charts are present.

### Expected output

Running the program produces `output.pdf` that contains:

* The original content of `input.docx` (if any)  
* A fully rendered pie chart titled *Sales Distribution Q1*  
* Accurate slice percentages matching the data (40 %, 30 %, 30 %)

Open the PDF in any viewer and you should see a crisp pie chart, identical to what you’d see in the Word file.

## Common pitfalls and how to avoid them

| Issue | Cause | Fix |
|-------|-------|-----|
| Chart appears blank in PDF | Font or chart rendering settings missing | Ensure you’re using the latest Aspose.Words version; it bundles required rendering libraries. |
| Data values are rounded incorrectly | Using integer values with large numbers | Provide `double` values or scale numbers before adding them to the series. |
| Output PDF is huge | Images embedded at high DPI | Set `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)` if you also embed images. |
| “convert word to pdf” throws `UnsupportedOperationException` | Using an older Java version (< 11) | Upgrade to Java 17 or later, which Aspose.Words 24.x requires. |

## Pro tip: Re‑use the chart creation logic

If you need to add multiple charts to the same document, extract the chart‑building code into a helper method:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Now you can call `doc.getFirstSection().getBody().appendChild(createPieChart(...));` for each dataset, keeping your code DRY (Don’t Repeat Yourself).

## Conclusion

You now know how to **create pie chart** inside a Word document, populate it with data, and **save docx as PDF** using Java. This end‑to‑end example covers the entire **convert word to pdf** workflow, answers **how to add chart**, and demonstrates **how to create chart** programmatically.  

From here you might explore:

* Adding bar or line charts (`ChartType.BAR`, `ChartType.LINE`) – another **how to create chart** scenario.  
* Exporting to other formats such as PNG or HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Dynamically generating the input document with tables or placeholders before inserting charts.

Feel free to experiment with different data sets, styling options, or even embedding multiple charts per page. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to save word as pdf and create accessible PDF in Java](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [How to create chart in Word with Java and Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}