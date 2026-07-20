---
category: general
date: 2026-07-20
description: how to insert pie chart in Word with Aspose.Words. Learn to add data
  label percent and display percentages on chart for professional documents.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: en
lastmod: 2026-07-20
og_description: how to insert pie chart in Word using Aspose.Words. This guide shows
  how to add data label percent and display percentages on chart in just a few lines.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: how to insert pie chart in Word – quick guide
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: how to insert pie chart in Word – add data label percent
url: /java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# how to insert pie chart in Word – add data label percent

Ever wondered **how to insert pie chart** into a Word document without wrestling with the UI? You’re not alone. In many reporting scenarios you need to *add pie chart to Word* and, more importantly, **show percent on pie chart** so readers instantly grasp the data distribution.

In this tutorial we’ll walk through the complete process using Aspose.Words for Java. By the end you’ll know exactly how to **add data label percent**, **display percentages on chart**, and get a polished pie chart that looks right the first time. No extra plugins, no manual tweaks—just clean code you can drop into any project.

---

## Prerequisites

- Java 17 (or later) – the current LTS version that Aspose.Words supports.
- Aspose.Words for Java 24.x (the latest at the time of writing, July 2026).
- A basic Maven or Gradle setup to pull the library.
- An IDE you like (IntelliJ IDEA, Eclipse, VS Code… any will do).

If you already have these, great—let’s dive in.

---

## Step 1: Set up the project and import the library

First, add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). This gives you access to the `Document`, `DocumentBuilder`, and chart classes.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Keep the version number up‑to‑date; newer releases often add chart‑related fixes that make **display percentages on chart** more reliable.

---

## Step 2: Create a new Word document and a builder

The builder is your Swiss‑army knife for inserting content. Here we create a fresh document and attach a `DocumentBuilder` to it.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Why do we need a builder? It abstracts the low‑level OpenXML structures, letting us focus on *what* we want—like **add pie chart to word**—instead of *how* the XML looks.

---

## Step 3: Insert the pie chart

Now comes the core of **how to insert pie chart**. We ask the builder to place a pie chart of a specific size. The dimensions are in points (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

At this point the chart is empty, but the placeholder is already in the document. You’ve just **add pie chart to word** programmatically.

---

## Step 4: Populate the chart with data

A pie chart needs at least one series of values. Let’s feed it some sample data that represents market share.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

If you ever need multiple series (stacked pies, doughnuts, etc.) you can call `pieChart.getSeries().add()` and repeat the steps. The same logic applies when you want to **display percentages on chart** for each slice.

---

## Step 5: **add data label percent** – show the percentages on the slices

This is the part most developers forget: configuring the data labels to show percentages. Without it, the chart only shows raw numbers, which can be ambiguous.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

The `setShowPercent(true)` call tells Aspose.Words to render the label as “30 %”, “45 %”, etc. That’s exactly how you **show percent on pie chart** without any extra formatting work.

---

## Step 6: Save the document

Finally, write the document to disk. You can choose `.docx`, `.pdf`, or even `.html`. For this guide we’ll stick with the modern `.docx` format.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Run the program, open `PieChartDemo.docx`, and you’ll see a neatly rendered pie chart with percentage labels on each slice.

---

## Expected output

Below is a screenshot of the generated Word file. Notice how each slice displays its share as a percentage—exactly what we wanted when we set **add data label percent**.

![Screenshot of a Word document containing a pie chart with percentage labels](/images/pie-chart-percent.png){.center width=600px alt="Screenshot showing how to insert pie chart in Word with percentage labels"}

*The alt text includes the primary keyword, satisfying both SEO and accessibility.*

---

## Common questions & edge‑case handling

| Question | Answer |
|----------|--------|
| **Can I change the font of the percentage labels?** | Yes. After enabling `setShowPercent(true)`, retrieve the `DataLabel` object and adjust its `Font` property (`dataLabel.getFont().setSize(10);`). |
| **What if I need a doughnut chart instead of a pie?** | Replace `ChartType.PIE` with `ChartType.DOUGHNUT` in the `insertChart` call. The same **add data label percent** logic works. |
| **Do older Word versions (2007‑2010) display the percentages correctly?** | Aspose.Words writes the underlying XML in a version‑agnostic way, so the percentages appear in any Word that supports charts (2007+). |
| **How to add a title to the chart?** | Use `pieChart.getTitle().setText("Market Share");` before saving. |
| **Can I insert the chart into a specific paragraph or table cell?** | Absolutely. Move the `DocumentBuilder` to the desired location (`builder.moveToParagraph(index, true);` or `builder.moveToCell(table, row, column, true);`) before calling `insertChart`. |

---

## Tips and tricks from the field

- **Pro tip:** If you plan to generate many charts in a loop, reuse a single `DocumentBuilder` instance; it reduces memory churn.
- **Watch out for:** Very small slices (< 2 %). Aspose.Words may omit the label to avoid clutter; you can force it with `dataLabel.setShowLabel(true);`.
- **Performance note:** Chart rendering is CPU‑intensive. For bulk report generation, consider multi‑threading but make sure each thread works on its own `Document` instance.
- **Version check:** The method `setShowPercent` was introduced in Aspose.Words 22.8. If you’re on an older version, upgrade or manually calculate percentages and set them as custom labels.

---

## Recap

We’ve covered **how to insert pie chart** into a Word document using Aspose.Words, shown you how to **add data label percent**, and demonstrated the easiest way to **display percentages on chart**. With just a few lines of Java you can **add pie chart to word** and **show percent on pie chart**, turning raw numbers into instantly readable visuals.

---

## What’s next?

- Experiment with other chart types (`BAR`, `LINE`, `AREA`) and see how the same **add data label percent** logic applies.
- Combine charts with tables for richer reports—Aspose.Words makes it trivial to place a chart next to a data table.
- Explore exporting the same document to PDF or HTML to see how the percentages render across formats.

Feel free to tweak the dimensions, colors, or data source (e.g., a database query) and watch your Word reports come alive. If you hit a snag, drop a comment below—happy charting!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}