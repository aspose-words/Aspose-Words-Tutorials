---
category: general
date: 2026-07-29
description: Insert pie chart using Aspose.Words for Java and learn how to generate
  doughnut chart, format pie chart, format chart Word, and customize chart size.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: en
lastmod: 2026-07-29
og_description: Insert pie chart with Aspose.Words for Java and quickly learn to generate
  doughnut chart, format pie chart, format chart Word, and customize chart size for
  professional documents.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Insert pie chart in Java – Complete Aspose.Words Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Insert pie chart in Java with Aspose.Words – Full Guide
url: /java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert pie chart in Java with Aspose.Words – Complete Guide

Ever wondered how to **insert pie chart** into a Word document from Java code? You’re not the only one—many developers hit this roadblock when they need a quick, programmatic way to visualise data. The good news? With Aspose.Words for Java you can do it in just a handful of lines, and while you’re at it you can also **generate doughnut chart**, **format pie chart**, **format chart Word**, and **customize chart size** to match your branding.

In this tutorial we’ll walk through a real‑world example that starts by creating a blank document, drops in a pie chart, tweaks a few visual properties, and finally saves the file. By the end you’ll have a reusable snippet you can paste into any Java project that needs chart automation. No extra libraries, no manual fiddling with Office interop—just clean, compiled Java.

## What You’ll Need

- **Java 17** (or any recent JDK; the API is backward compatible)
- **Aspose.Words for Java** 22.12 or newer – you can grab the Maven artifact or the .jar from the Aspose site.
- A modest IDE (IntelliJ IDEA, Eclipse, VS Code…) – anything that lets you run a `main` method.
- Optional: a license file if you don’t want the evaluation watermark.

If you’ve got those, we can jump straight into the code.

## Step 1: Insert pie chart with Aspose.Words

The first thing we do is **insert pie chart** into a fresh document. This step sets the stage for everything else, because the chart object gives us access to series, data points, and visual tweaks.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Why this matters:** `DocumentBuilder.insertChart` not only creates the chart but also returns a `Chart` object that we can manipulate. The width and height arguments let you **customize chart size** right at creation time, so you don’t need to resize later.

## Step 2: Generate doughnut chart (optional)

If your design calls for a hole in the middle—think of a classic doughnut chart—Aspose makes that a one‑liner. The same `Chart` instance can be switched from a regular pie to a doughnut by adjusting the hole size.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Tip:** The hole size only takes effect for `ChartType.DONUT`. If you keep the type as `PIE`, the call is ignored, so feel free to experiment.

## Step 3: Format pie chart slices

A good visual often highlights a particular slice. Here we **format pie chart** by exploding the first slice 20 points outward. This draws the reader’s eye to the most important data point.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro tip:** You can loop through `pieChart.getSeries()` if you have multiple series and set individual colors, borders, or data labels. That’s the way to **format chart Word** documents with rich styling.

## Step 4: Add data to the chart

A chart without data is just a decorative shape. Let’s feed it a simple data set—say, quarterly sales numbers.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Why we do this:** By explicitly adding `ChartPoint` objects we guarantee the chart reflects our business logic. The `setShowCategoryName` and `setShowValue` calls are part of **formatting the pie chart** to show both labels and numbers.

## Step 5: Fine‑tune appearance (customize chart size & style)

Beyond the initial dimensions, you might want to tweak the chart’s legend, title, or even the font used for data labels. All of these fall under **customize chart size** and overall formatting.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Edge case:** If you later decide to export the document to PDF, the chart’s vector data stays crisp because the size is defined in points, not pixels. That’s a win for **format chart Word** and downstream formats.

## Step 6: Save and view the document

The final step is as simple as calling `doc.save`. This writes a `.docx` file that you can open in Microsoft Word, LibreOffice, or any viewer that supports the OpenXML format.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Result:** Open `PieChart.docx` and you’ll see a neatly sized pie (or doughnut) chart with an exploded slice, a title, and a legend—all generated without ever touching the UI.

### Expected Output

| Element | What you’ll see |
|---------|-----------------|
| Chart type | Pie chart (or doughnut if `holeSize` > 0) |
| Slice explosion | First slice offset by 20 pts |
| Legend | Positioned on the right |
| Title | “Quarterly Sales Distribution” in bold 14 pt |
| Data labels | Category name and value shown on each slice |
| Document | A standard Word `.docx` file ready for sharing |

## Common Questions & Gotchas

- **Do I need a license?**  
  The evaluation version works fine for testing, but it adds a watermark. Drop your `aspose.words.lic` file in the classpath for a clean output.

- **Can I use this with Maven?**  
  Absolutely. Add the following dependency to your `pom.xml`:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **What if I have more than one series?**  
  Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`, or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional data.

- **Is the chart editable in Word after generation?**  
  Yes—once saved, you can open the document and manually adjust colors, fonts, or even convert the pie to a bar chart if you need to.

## Wrap‑Up

We’ve just **inserted pie chart** into a Word document using Aspose.Words for Java, shown how to **generate doughnut chart**, demonstrated multiple ways to **format pie chart**, covered **format chart Word** best practices, and learned how to **customize chart size** for a polished look. The complete, runnable example above can be dropped into any Java project, giving you instant chart automation without the overhead of COM interop or Office installations.

What’s next? Try swapping the data source for a live database, add conditional colors based on thresholds, or export the same document to PDF for a print‑ready report. Each of those steps builds on the foundation we’ve laid out, so you’ll find the transition smooth.

If you hit any snags or have ideas for further enhancements—maybe a stacked bar or a line chart—drop a comment below. Happy charting!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}