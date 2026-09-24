---
category: general
date: 2026-09-24
description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn to
  set hole size, explode pie slice, highlight pie chart slice, and create docx chart
  effortlessly.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: en
lastmod: 2026-09-24
og_description: Insert pie chart word in a DOCX with Aspose.Words for Java. Master
  set hole size, explode pie slice, highlight pie chart slice, and create docx chart
  in minutes.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Insert pie chart word in Java – step‑by‑step tutorial
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Insert pie chart word in Java – complete guide
url: /java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert pie chart word in Java – complete guide

If you need to **insert pie chart word** in a DOCX file, this tutorial shows you exactly how to do it with Aspose.Words for Java. You’ll see the full workflow from creating the document to customizing the chart so that the slice is exploded, the hole size is set to zero, and the slice is highlighted.

Working with charts in Word documents often feels like a separate concern from regular text processing, but Aspose.Words unifies both. In the steps below you’ll also learn how to **create docx chart** files that are ready to be opened in Microsoft Word, Google Docs, or any other DOCX‑compatible viewer.

## What you’ll accomplish

* **Insert pie chart word** into a blank document  
* **Set hole size** to turn the chart into a full pie (no doughnut)  
* **Explode pie slice** to draw attention to a specific segment  
* **Highlight pie chart slice** with custom formatting  
* **Create docx chart** that can be shared or further edited  

### Prerequisites

* Java 17 or later (the code compiles with Java 8 as well)  
* Aspose.Words for Java library (version 23.9 or newer)  
* An IDE or build tool (Maven/Gradle) that can resolve the Aspose.Words dependency  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## How to insert pie chart word in a DOCX using Aspose.Words

The first step is to create a new blank document and obtain a `DocumentBuilder`. The builder gives you direct access to the document’s content stream, making it trivial to **insert pie chart word**.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Why this matters
`Document` represents the whole Word file, while `DocumentBuilder` is the high‑level API that lets you insert paragraphs, tables, and charts without dealing with low‑level XML. Starting with a clean document ensures that the chart you add is the only content, which is perfect for learning or for generating template‑based reports.

## Set hole size to create a full pie

By default, Aspose.Words creates a doughnut chart when you request a pie chart. To make the chart a true circle, you must **set hole size** to `0`. This removes the inner hole and yields a classic pie appearance.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Practical tip
If you later decide to switch to a doughnut chart, simply change the `holeSize` value to a percentage (e.g., `30`). The same API works for both chart types.

## Explode pie slice to highlight a segment

Exploding a slice makes it stand out visually. The **explode pie slice** operation moves the chosen slice outward by a percentage of the chart radius.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Why explode?
An exploded slice draws the reader’s eye to the most important data point—perfect for dashboards or executive summaries. The value `20` means 20 % of the radius; you can adjust it between `0` (no explosion) and `100` (fully detached).

## Highlight pie chart slice with custom formatting

Beyond exploding, you might want to **highlight pie chart slice** by changing its fill color or border. While the demo code focuses on explosion, you can extend it as follows:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Expert note
Changing the fill color of a specific slice requires accessing the `DataPoint` object. If you have multiple series, iterate through `series.getDataPoints()` and apply styles conditionally.

## Save and verify the created docx chart

Finally, you **create docx chart** by saving the `Document`. The resulting file can be opened in Microsoft Word to see the formatted pie chart.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Expected output
Opening `PieChartFormatted.docx` shows a single pie chart:

* The chart occupies a 400 × 300 pt area.  
* The hole size is `0`, so the chart is a full pie.  
* The first slice is exploded by 20 % and colored red (if you added the optional formatting).  

You now have a **create docx chart** that can be distributed, embedded in emails, or further edited programmatically.

---

## Common variations and edge cases

| Scenario | How to adapt the code |
|----------|----------------------|
| **Multiple series** | Loop over `pieChart.getChart().getSeries()` and set `Explosion` or `FillColor` per series. |
| **Dynamic data** | Populate the series with values from a database or CSV before calling `setExplosion`. |
| **Different chart size** | Change the width/height arguments in `insertChart(ChartType.PIE, width, height)`. |
| **Export to PDF** | After saving the DOCX, call `doc.save("output.pdf")` to produce a PDF version of the same chart. |
| **Localization** | Use `DocumentBuilder.insertChart` with a locale‑specific number format for labels. |

### Pro tip
Always call `setHoleSize(0)` **after** `insertChart`. If you set it before insertion, Aspose.Words will revert to the default doughnut size once the chart is created.

---

## Recap

You now know how to **insert pie chart word** into a Word document using Java, how to **set hole size** for a full‑pie look, how to **explode pie slice** to draw attention, and how to **highlight pie chart slice** with custom colors. The complete example also demonstrates how to **create docx chart** files that are ready for distribution.

---

## Next steps

* Explore other chart types (`BAR`, `LINE`, `SCATTER`) with `ChartType`.  
* Combine chart generation with mail merge to produce personalized reports.  
* Integrate the generated DOCX into a web service that returns the file on demand.  

If you run into issues, remember to verify that you’re using a compatible version of Aspose.Words and that the output directory exists and is writable.

Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}