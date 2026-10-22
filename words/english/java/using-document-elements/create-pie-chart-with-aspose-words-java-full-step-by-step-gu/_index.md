---
category: general
date: 2026-07-16
description: Create pie chart in Java using Aspose.Words. Learn how to add leader
  lines, show chart legend, and explode a slice in a single tutorial.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: en
lastmod: 2026-07-16
og_description: Create pie chart in Java using Aspose.Words. This guide shows how
  to add leader lines, show chart legend, and explode a slice, giving you a polished
  visual in minutes.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Create Pie Chart with Aspose.Words Java – Complete Formatting Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
url: /java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide

Ever wondered how to **create pie chart** programmatically in Java without wrestling with low‑level drawing APIs? You're not the only one. Many developers need a quick visual for reports, dashboards, or automated documents, and they reach for Aspose.Words because it handles the heavy lifting.  

In this tutorial we’ll walk through a complete, ready‑to‑run example that not only **creates a pie chart** but also shows you how to **add leader lines**, **show chart legend**, and even **explode a slice** for emphasis. By the end you’ll have a `.docx` file that looks polished enough to impress a client.

> **Quick win:** The code snippet below works out‑of‑the‑box with Aspose.Words for Java 23.9 (or any newer version). No extra dependencies, just the JAR.

## What You’ll Learn

- Set up a blank Word document with `DocumentBuilder`.
- Insert a **pie chart** of a custom size.
- Use the **explode slice** feature to highlight a data point.
- Enable **leader lines** so the exploded slice stays connected to the label.
- Turn on the **chart legend** so readers can instantly identify each slice.
- Save the result to a `.docx` file you can open in Microsoft Word or LibreOffice.

**Prerequisites** – You’ll need:

1. Java 17 (or later) installed.
2. Aspose.Words for Java JAR on your classpath.
3. A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you prefer.

Now, let’s dive in.

## Step 1: Initialize the Document and Builder – Preparing to **create pie chart**

First, we need a clean document canvas. `Document` represents the whole Word file, while `DocumentBuilder` is the helper that lets us add content.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Why this matters:** Starting with a fresh `Document` guarantees no hidden styles or leftover objects that could interfere with chart rendering.

## Step 2: Insert the **pie chart** – Size matters

Aspose.Words makes chart insertion a one‑liner. Here we ask for a pie chart that’s 400 × 300 points—roughly 5.5 × 4.2 inches on a typical screen.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Pro tip:** If you need a different size, just change the two numeric arguments. The API works in points, where 72 points = 1 inch.

## Step 3: **How to explode slice** – Emphasizing a key data point

Exploding a slice pulls it out from the rest of the pie, drawing the reader’s eye. The `setExplosion` method takes an integer representing the distance in points.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **What if you have multiple series?** You can call `setExplosion` on any series index (`get(1)`, `get(2)`, …) to explode different slices.

## Step 4: **Add leader lines** and **show chart legend** – Connecting the dots

When a slice is exploded, the label can drift away. Leader lines keep the label tethered, preserving readability. At the same time, a legend offers a quick key for all slices.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Why enable leader lines?** Without them, the label might appear floating, confusing users about which slice it belongs to.  
> **Need a custom legend position?** Use `chart.getLegend().setPosition(LegendPosition.TOP)` or any other enum value.

## Step 5: Save the Document – The final **create pie chart** step

Finally, we persist the document to disk. Adjust the path to a folder you have write access to.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Run the program, open the generated `PieChartDemo.docx`, and you should see a nicely formatted pie chart with an exploded first slice, leader lines, and a visible legend.

![Pie chart example showing exploded slice and legend](pie-chart-example.png){: .center-image alt="Create pie chart example with exploded slice, leader lines, and legend"}

### Expected Output

When you open the Word file, the chart looks roughly like this:

- A 400 × 300 pt pie chart.
- The first slice is offset by 10 pt.
- A thin leader line connects the exploded slice to its label.
- A legend under the chart lists each series name.

If you don’t see the leader line, double‑check that `setLeaderLines(true)` is called *after* the explosion setting—order matters.

## Common Pitfalls and How to Avoid Them

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **No legend appears** | `setShowLegend(true)` was omitted or called on the wrong chart object. | Ensure you call `chart.setShowLegend(true)` **after** retrieving the `Chart` from the shape. |
| **Leader line missing** | The slice wasn’t exploded, or the chart type doesn’t support leader lines. | Only `ChartType.PIE` (or `PIE_3D`) supports leader lines. Call `setExplosion` first, then `setLeaderLines(true)`. |
| **Slice doesn’t move** | Explosion value too low (0‑2 pt). | Increase the integer, e.g., `setExplosion(10)` or higher for a more dramatic effect. |
| **Chart looks distorted** | Using a non‑square size (width ≠ height) can squash the pie. | Keep width and height equal or close; 400 × 300 works but 400 × 400 gives a perfect circle. |

## Advanced Tweaks (Optional)

If you want to go beyond the basics, consider:

- **Custom colors**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Data labels**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **3‑D effect**: Replace `ChartType.PIE` with `ChartType.PIE_3D`.

These options let you fine‑tune the visual to match corporate branding guidelines.

## Recap – What We Achieved

We started with a blank Word document, **created a pie chart**, **exploded the first slice**, **added leader lines**, and **showed the chart legend**. The entire flow fits into a concise `main` method, making it easy to embed into larger reporting pipelines.

## Next Steps

- **Add more series**: Populate the chart with real data from a database or CSV.
- **Export to PDF**: Use `doc.save("output.pdf", SaveFormat.PDF);` to generate a PDF version.
- **Combine with other shapes**: Insert tables, images, or additional charts for a full report.

If you’re curious about other chart types—column, bar, line—just replace `ChartType.PIE` with the appropriate enum and follow the same formatting steps.

---

*Happy charting!* Feel free to drop a comment if something didn’t work as expected, or share how you customized the legend position. Your feedback helps us all build better automated documents.


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)
- [How to Add Watermark to Documents Using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}