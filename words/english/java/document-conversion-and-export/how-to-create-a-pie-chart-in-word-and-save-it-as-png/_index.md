---
category: general
date: 2026-10-07
description: Learn how to create a pie chart in Word, add data series, and save the
  chart as PNG using Java. Follow the step‑by‑step guide for quick results.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: en
lastmod: 2026-10-07
og_description: 'Create pie chart in Word quickly: this tutorial shows how to add
  data series, generate the chart, and save the Word chart as an image (PNG). Follow
  the complete code example.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Create a pie chart in Word and export as PNG – guide
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: How to create a pie chart in Word and save it as PNG
url: /java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create a pie chart in Word and save it as PNG

If you need to **create pie chart** objects inside a Microsoft Word file, this guide shows you exactly how to do it with Java. You’ll also learn how to **add data series** to the chart and **save chart as PNG** so the visual can be reused outside of Word.

Generating a chart directly in a document saves you from exporting data to a separate graphics tool. By the end of this tutorial you’ll have a fully functional Word file that contains a pie chart and a matching PNG image on disk.

## Prerequisites

Before you start, make sure you have:

* Java 17 or later installed.
* The **GroupDocs.Viewer for Java** (or a compatible library that provides `Document`, `Chart`, `ChartType`, and `ImageSaveOptions` classes).
* A Maven or Gradle project where you can add the library dependency.
* An input Word document (`input.docx`) located in a folder you can reference from code.

If you’re using Maven, add the dependency (replace `VERSION` with the latest release):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## How to create pie chart in Word

The core of the solution revolves around three actions:

1. Load the source `.docx` file.
2. **Add data series** to a new `Chart` object of type `PIE`.
3. **Save chart as PNG** so you obtain an image file next to the Word document.

Below each step is explained in detail, followed by the exact Java code you need.

### Step 1: Load the source document

You must open the Word file that will host the chart. The `Document` class reads the `.docx` content into memory.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Why this matters*: Loading the document creates a mutable model. All subsequent chart operations modify this in‑memory representation, which you later persist back to disk.

### Step 2: Add data series to the chart

Creating a **pie chart** starts with a `Chart` instance. The constructor receives the parent `Document` and the chart type (`ChartType.PIE`). After the chart object exists, you populate it with numeric values and optional labels.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Why this matters*: The `add` method **adds data series** to the chart. Each entry in `values` becomes a slice of the pie, while `categories` provide the legend labels. You can supply any number of points; the library will automatically calculate slice angles.

### Step 3: Save chart as PNG

Once the chart is part of the document, you can export the visual representation. The `save` method on the underlying chart object writes a PNG file to the file system.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Why this matters*: Saving the chart as PNG gives you a raster image that can be embedded in web pages, emails, or reports without requiring the original Word file. The `ImageSaveOptions` object lets you control format, resolution, and other export settings.

## Generate pie chart in Word – customizing the look

Beyond the basic steps, you might want to customize colors, titles, or data labels. Most libraries expose a `ChartOptions` or similar object. Here’s a quick example that adds a title and changes the slice colors:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

These customizations are optional but illustrate how you can **generate pie chart in Word** that matches your branding.

## Save Word chart as image – alternative approaches

If you only need the image and not the chart inside the document, you can skip inserting the chart shape into the Word file and directly call the `save` method after creating the chart. The code remains the same; you simply omit any steps that add the chart to the document’s body.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

This technique is useful when you generate many charts in a batch process and only care about the PNG output.

## Full runnable example

Copy the following class into your project, adjust the file paths, and run it. The program will:

1. Load `input.docx`.
2. **Create a pie chart**, **add data series**, and embed it into the document.
3. **Save the chart as PNG** (`radial.png`).
4. Persist the modified Word file as `output.docx`.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.Chart;
import com.groupdocs.viewer.ChartType;
import com.groupdocs.viewer.options.ImageSaveOptions;
import com.groupdocs.viewer.options.SaveFormat;

public class PieChartGenerator {

    public static void main(String[] args) {
        // Adjust these paths for your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}