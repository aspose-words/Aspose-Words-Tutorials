---
category: general
date: 2026-09-27
description: Create radial chart in Java and insert chart into Word. Learn how to
  set chart size, add data series, and generate a blank Word document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: en
lastmod: 2026-09-27
og_description: Create radial chart in Java, then insert chart into Word. This guide
  shows how to set chart size, add data series, and create a blank Word document.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Create radial chart and insert chart into Word with Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Create radial chart and insert chart into Word with Java
url: /java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create radial chart and insert chart into Word with Java

If you need to **create radial chart** in a Word file using Java, this tutorial shows you exactly how. You’ll see how to **insert chart into Word**, set the chart’s dimensions, and build a **blank Word document** from scratch.

We’ll walk through every required step, from initializing the document to adding a data series and saving the final `.docx`. By the end you’ll have a fully functional Word file containing a radial chart, and you’ll understand **how to set chart size** and **add data series chart** for future customizations.

## Prerequisites

* Java 17 or later (the code compiles with any modern JDK)
* Aspose.Words for Java 24.9 or newer – the `setShowGraduations` method is only available from this version
* An IDE or build tool (Maven/Gradle) that can include the Aspose.Words JAR
* Basic familiarity with Java syntax and Maven/Gradle dependency management

> **Pro tip:** If you’re using Maven, add the following to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Step 1: Create a blank Word document

A blank document is the canvas on which the chart will be placed. The `Document` class represents the entire `.docx` file.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Creating a blank document ensures no pre‑existing content interferes with the chart layout.

## Step 2: Initialise a DocumentBuilder

`DocumentBuilder` provides convenient methods for inserting objects, text, and other elements into the document.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

The builder will later be used to **insert chart into Word**.

## Step 3: Build the radial chart

Aspose.Words supports many chart types; `ChartType.RADIAL` creates a radial (polar) chart.

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

At this point the chart exists but has no data, size, or visual options.

## Step 4: Add a data series to the chart

A chart without a data series is empty. The `add` method takes a series name and an array of values.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

You can add multiple series by calling `add` repeatedly. This satisfies the **add data series chart** requirement.

## Step 5: Enable graduations (optional)

Graduations are the radial grid lines that improve readability. They are only available from version 24.9.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

If you use an older Aspose.Words version, this line will throw an exception—so verify your library version first.

## Step 6: Set the chart’s dimensions

Controlling the chart size lets you fit it nicely within the page margins. This addresses **how to set chart size**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

You can adjust the width and height values to match your layout needs. Remember that 1 point ≈ 1/72 inch.

## Step 7: Insert the chart into the Word document

Now the chart is ready to be placed. The `insertChart` method of `DocumentBuilder` handles the insertion.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

This is the core of the **insert chart into word** operation.

## Step 8: Save the document

Finally, write the document to disk. The file will contain the radial chart you just created.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Running the program produces `RadialChart.docx` in the project’s working directory. Opening the file in Microsoft Word shows a radial chart with three data points and visible graduations.

### Expected output

* A Word file named `RadialChart.docx`
* Inside the file, a single page containing a radial chart sized 400 × 300 points
* The chart displays one series titled **Series 1** with values **10, 20, 30**
* Graduations (radial grid lines) are visible around the chart

## Common variations and edge cases

| Situation | What to change | Reason |
|-----------|----------------|--------|
| **Multiple series** | Call `chart.getSeries().add(...)` for each series | Allows comparative data visualisation |
| **Different chart type** | Replace `ChartType.RADIAL` with `ChartType.COLUMN` (or any other) | Use the chart type that best represents your data |
| **Custom colors** | Access `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | Improves visual branding |
| **Older Aspose.Words version** | Omit the `setShowGraduations` line or upgrade the library | Prevents `NoSuchMethodError` |
| **Saving to a different format** | Use `doc.save("RadialChart.pdf", SaveFormat.PDF)` | Generates a PDF instead of a DOCX |

## Full runnable example

Below is the complete, self‑contained Java program. Copy it into a file named `RadialChartExample.java`, add the Aspose.Words dependency, and run it.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Conclusion

You now know how to **create radial chart** programmatically, **add data series chart**, control **how to set chart size**, and **insert chart into Word** while starting from a **blank Word document**. The example uses Aspose.Words for Java 24.9, but the same concepts apply to other chart libraries that expose a similar API.

### Next steps

* Explore other chart types (`ChartType.PIE`, `ChartType.LINE`, etc.) – this ties back to the secondary keyword **insert chart into word**.
* Customize axis labels, legends, and colors to match your brand guidelines.
* Generate charts dynamically from database queries or CSV files.
* Convert the resulting `.docx` to PDF for distribution (`doc.save("output.pdf", SaveFormat.PDF)`).

Feel free to experiment with the dimensions, series data, and styling options to create the exact visual you need. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}