---
category: general
date: 2026-10-04
description: Learn how to explode slice in a Word chart, explode pie chart slice and
  change doughnut chart size with a step‑by‑step Java example.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: en
lastmod: 2026-10-04
og_description: How to explode slice in a Word chart and customize pie or doughnut
  charts with Java. Follow the complete example to modify chart in Word.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: How to explode slice in a Word chart – full Java guide
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: How to explode slice in a Word chart and customize its appearance
url: /java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to explode slice in a Word chart and customize its appearance

If you need to **how to explode slice** in a Word chart, this guide shows you exactly how. Whether you’re preparing a sales presentation or a financial report, exploding a pie‑chart slice or adjusting a doughnut hole can make the most important data stand out. In the following sections you’ll also learn how to **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size**, and **customize pie chart word** documents using Aspose.Words for Java.

You’ll finish this tutorial with a complete, ready‑to‑run Java program that loads a `.docx` file, explodes the first slice of a pie chart, changes the doughnut hole size, and saves the result. No external scripts or manual editing are required.

## Prerequisites

- Java 17 or later installed on your development machine.  
- Maven 3.6+ (or Gradle) to manage dependencies.  
- Aspose.Words for Java library (the free trial works for development).  
- A Word document (`input.docx`) that contains at least one chart (pie or doughnut).

## Step 1: Add Aspose.Words to your project

If you use Maven, add the following dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

For Gradle, place this in `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Keep your library version up to date; newer releases add support for additional chart types and improve performance.

## Step 2: Load the Word document that contains a chart

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Why this matters:** Loading the document creates an in‑memory representation that Aspose.Words can traverse. Without this object you cannot access the chart nodes.

## Step 3: Retrieve the first chart in the document

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Explanation:** `NodeType.SHAPE` covers all drawing objects, including charts. The `true` argument tells Aspose to search recursively, ensuring the first chart is found even if it’s nested inside a table.

## Step 4: Explode the first slice of a pie chart

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**How it works:** The `setExplosion` method takes a numeric value that determines how far the slice moves away from the centre. A value of `20` is visually noticeable without breaking the chart layout.

## Step 5: Adjust the doughnut hole size for a doughnut chart

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Why this helps:** A larger doughnut hole can improve readability when you have many data points. The `setDoughnutHoleSize` method expects a percentage (0‑100).

## Step 6: Save the modified document

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Expected output

- The first slice of the first pie chart is offset outward, making it stand out.
- If the chart is a doughnut, the central hole expands to 40 % of the chart radius.
- The resulting file `PieChart.docx` can be opened in Microsoft Word, LibreOffice, or any compatible viewer, showing the visual changes you applied programmatically.

## Full, runnable example

Below is the entire program in one block. Copy it into `ChartExploder.java`, adjust the file paths, and run it with `mvn compile exec:java` (or your IDE’s run configuration).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

Running this code will **modify chart in Word**, **explode pie chart slice**, and **change doughnut chart size** automatically.

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| *What if the document contains multiple charts?* | The sample targets the **first** chart (`NodeType.SHAPE, 0`). To work with other charts, change the index or iterate through `doc.getChildNodes(NodeType.SHAPE, true)` and filter by `shape.getChart() != null`. |
| *Can I explode a slice other than the first one?* | Yes. Access the desired series via `chart.getSeries().get(seriesIndex)` and call `setExplosion(value)`. Indexes are zero‑based. |
| *Does this work with Word 2007‑2021 files?* | Aspose.Words supports `.doc`, `.docx`, `.dot`, and `.dotx`. The same code works across versions because the library abstracts the file format. |
| *What if the chart is a bar or line chart?* | `setExplosion` and `setDoughnutHoleSize` are only applicable to pie‑type charts. The code safely skips those operations when the chart type differs. |
| *Do I need a license for Aspose.Words?* | A free evaluation license removes the 30‑day limit but adds a watermark. For production, purchase a license to remove the watermark and unlock full functionality. |

## Conclusion

You now know **how to explode slice** in a Word chart, how to **modify chart in Word**, and how to **change doughnut chart size** using Aspose.Words for Java. The complete example demonstrates the full workflow—from loading a document, locating the chart, applying visual tweaks, to saving the result—so you can integrate these steps into any reporting or document‑generation pipeline.

**Next steps**

- Explore other chart customizations such as changing colors, adding data labels, or switching chart types (`chart.setChartType(ChartType.BAR_CLUSTERED)`).  
- Combine this logic with Aspose.PDF to generate a PDF version of the same report.  
- Automate the process for a batch of documents by looping over files in a directory.

Feel free to experiment with different explosion values or doughnut hole percentages to match your design guidelines. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}