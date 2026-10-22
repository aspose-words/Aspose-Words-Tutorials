---
category: general
date: 2026-08-07
description: Wie man ein Kuchenscheiben‑Explodieren in Java mit Aspose.Words durchführt.
  Erfahren Sie, wie Sie Führungs‑Linien zum Kreisdiagramm hinzufügen, ein Word‑Diagramm
  erstellen und die Segmente des Kreisdiagramms anpassen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: de
lastmod: 2026-08-07
og_description: Wie man ein Kuchenscheiben‑Explodieren in Java mit Aspose.Words umsetzt.
  Dieser Leitfaden zeigt, wie man Führungslinien zu einem Kreisdiagramm hinzufügt,
  Word‑Diagramme erstellt und die einzelnen Kuchenstücke im Diagramm anpasst, um eine
  klare visuelle Wirkung zu erzielen.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Wie man eine Kuchenscheibe in Java explodiert – Aspose.Words‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Wie man eine Kuchenscheibe in Java explodiert – Aspose.Words Diagrammtutorial
url: /de/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to explode pie slice in Java – Aspose.Words chart tutorial

If you need to know **how to explode pie slice** in a Word document using Java, this tutorial has you covered. We'll also show you **how to add leader lines to pie** charts, **java create word chart** objects, and **customize pie chart slices** for a polished result. By the end of this guide you’ll have a complete, runnable example that you can drop into any Java project.

![Wie man ein Kuchenscheibe in Java explodiert – Aspose.Words Diagramm](/images/pie-chart-exploded.png)

## Prerequisites

Before you start, make sure you have:

* Java Development Kit (JDK) 8 or higher.
* Maven or Gradle for dependency management.
* An Aspose.Words for Java license (the free evaluation works for learning purposes).
* Basic familiarity with Java syntax and object‑oriented concepts.

> **Pro tip:** Even though Aspose.Words offers a free trial, purchasing a license removes the evaluation watermark from generated documents.

## What this tutorial covers

* Creating a new Word document from scratch.  
* Inserting a **pie chart** using the `DocumentBuilder`.  
* **Exploding a pie slice** to highlight a data point.  
* **Adding leader lines to pie** for clearer labeling.  
* Customizing slice appearance, such as colors and borders.  
* Saving the document to disk and verifying the result.

---

## How to explode pie slice with Aspose.Words in Java

The first step is to set up the chart object and explode the desired slice. Aspose.Words exposes the chart through the `Shape` class, and each slice is a `ChartPoint`. By setting the `Explosion` property you control how far the slice moves outward.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Why it works:**  
`setExplosion(20)` tells the chart engine to offset the slice by 20 points from the chart’s center. The value is relative; larger numbers create a more dramatic effect. You can explode any slice by changing the index (`get(1)`, `get(2)`, …).

## Add leader lines to pie for clearer labels

Leader lines connect a slice’s label to its edge, which is especially useful when slices are exploded or when the chart contains many small sections. The `setLeaderLines(true)` call enables this feature for the whole series.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Why you need leader lines:**  
When a slice is exploded, the default label may overlap with other elements. Leader lines keep the label readable by drawing a short line from the slice to the text box.

## Java create Word chart – inserting data series

A chart without data isn’t very helpful. You must populate the series with categories and values. Below we add three categories representing market share.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Explanation:**  
`ChartSeries` holds both the categories (the slice names) and the numeric values. Enabling `ShowCategoryName` and `ShowPercentage` makes the chart self‑explanatory, which pairs nicely with the leader lines we added earlier.

## Customize pie chart slices beyond explosion

Beyond exploding a slice, you often want to adjust colors, borders, or even hide a slice entirely. The following snippet demonstrates three common customizations:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Why customize slices:**  
Custom colors make the chart align with corporate branding, while borders improve readability on printed pages. Hiding a slice is useful when you want to keep the data model intact but temporarily omit a category from visual output.

## Save the document and verify the result

Finally, write the document to disk. You can open the generated `.docx` in Microsoft Word, LibreOffice, or any viewer that supports the format.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Expected output:**  
When you open `PieChartDemo.docx`, you’ll see a pie chart where the first slice (Product A) is exploded outward, leader lines point from each slice to its label, and the slices appear in the custom green, blue, and orange colors. The hidden slice (Product C) will not be visible, but the percentages will still sum to 100 % because the data remains in the chart’s series.

---

## Full, runnable example

Below is the complete program you can copy, paste, and run after adding the Aspose.Words dependency to your project.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Abhängigkeit (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```


## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Wie man ein Säulendiagramm mit Aspose.Words für Java erstellt](/words/english/java/document-conversion-and-export/using-charts/)
- [Wie man Word-Dokumente mit Aspose.Words Java lädt: Umfassender Leitfaden](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Wie man Formularfelder erstellt und Inhalte mit DocumentBuilder in Aspose.Words für Java hinzufügt](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}