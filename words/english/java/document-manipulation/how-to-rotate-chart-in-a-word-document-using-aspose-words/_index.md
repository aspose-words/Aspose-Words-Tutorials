---
category: general
date: 2026-10-10
description: Learn how to rotate chart in a Word file and modify chart in Word to
  change doughnut chart size with a complete Java example.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: en
lastmod: 2026-10-10
og_description: How to rotate chart in a Word file and modify chart in Word to change
  doughnut chart size using Aspose.Words for Java.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: How to rotate chart in a Word document – step‑by‑step Java guide
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: How to rotate chart in a Word document using Aspose.Words
url: /java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to rotate chart in a Word document using Aspose.Words

If you need to **how to rotate chart** inside a Microsoft Word file, this guide shows you the exact steps. You’ll also learn how to **modify chart in Word** to **change doughnut chart size** without leaving your Java code.

Word automation often feels like a series of disconnected API calls, but with Aspose.Words you can treat a chart as any other document node. By the end of this tutorial you will have a runnable program that loads an existing `.docx`, rotates a doughnut chart by 45°, reduces the hole to 50 % of the radius, and saves the result as a new file.

## Prerequisites

Before you start, make sure you have:

* Java 17 or newer installed.
* Maven (or Gradle) to manage dependencies.
* An input Word document (`input.docx`) that already contains a doughnut chart.
* A valid Aspose.Words for Java license (or use the evaluation mode).

## Step 1: Set up the Maven project

Create a new Maven project or add the following dependency to your existing `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Running `mvn clean install` will download the library and make the classes available on your classpath.

## Step 2: Load the Word document that contains a chart

The first operation is to open the existing document. The `Document` class represents the whole file.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Loading the file does **not** modify it; it simply creates an in‑memory representation that you can query and edit.

## Step 3: Create a DocumentBuilder for navigation

`DocumentBuilder` gives you a cursor‑like API to walk through the document tree. We’ll use it to locate the first chart shape.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

The builder starts at the beginning of the document, but you can move it to any node later if needed.

## Step 4: Retrieve the first chart shape

Charts are stored as `Shape` nodes. By filtering child nodes of type `NodeType.SHAPE` we can extract the chart object.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

If the document contains multiple charts, you can iterate over `getChildNodes` and check each `Shape` for `hasChart()` before casting.

## Step 5: Rotate the chart (how to rotate chart)

A doughnut chart is essentially a pie chart with a hole. Rotating it changes the start angle of the first slice.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

The `setStartAngle` method expects a double representing degrees. Positive values rotate clockwise, while negative values rotate counter‑clockwise.

## Step 6: Change the doughnut hole size (change doughnut chart size)

The hole size is expressed as a fraction of the chart radius. A value of `0.5` means the hole occupies 50 % of the total radius.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Tip:** The valid range is `0.0` (no hole, i.e., a regular pie) to `0.9` (very thin ring). Values outside this range will throw an `IllegalArgumentException`.

## Step 7: Save the modified document

Finally, write the changes back to disk.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

When you open `DoughnutFormatted.docx` in Microsoft Word, you’ll see the doughnut chart rotated 45° and the hole reduced to half its original size.

## Full, runnable example

Putting all the pieces together, here is the complete program you can copy‑paste into your IDE:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Expected output

Running the program prints:

```
Chart rotated and doughnut size changed successfully.
```

Opening `DoughnutFormatted.docx` shows a doughnut chart whose first slice starts at the 45° position and whose inner radius occupies half of the outer radius.

## Common variations and edge cases

| Situation | What to adjust | Why it matters |
|-----------|----------------|----------------|
| **Multiple charts** | Loop through `getChildNodes(NodeType.SHAPE, true)` and check `shape.hasChart()` for each | Guarantees you modify the intended chart rather than the first one |
| **Bar or line chart** | `setStartAngle` does not apply; use `chart.getSeries().get(0).setFillFormat(...)` for other visual tweaks | Not all chart types support rotation; doughnut/pie charts are the only ones with a start angle |
| **Chart without a doughnut hole** | Skip `setDoughnutHoleSize` or first convert the chart type to doughnut via `chart.setChartType(ChartType.DONUT)` | Changing hole size on a non‑doughnut chart throws an exception |
| **Large documents** | Use `DocumentBuilder.moveToDocumentStart()` and `builder.moveToNode(chartShape)` for targeted navigation | Improves performance by avoiding full traversal of unrelated nodes |

## Pro tips for reliable chart manipulation

* **Cache the chart reference** – If you plan to modify several properties, keep a local `Chart` variable rather than repeatedly calling `chartShape.getChart()`.
* **Validate input values** – Before calling `setStartAngle` or `setDoughnutHoleSize`, verify the range to avoid runtime errors.
* **Use a license** – Evaluation mode inserts a watermark on the first page. Applying a license (`License license = new License(); license.setLicense("Aspose.Words.lic");`) removes it.

## Next steps

Now that you know **how to rotate chart** and **change doughnut chart size**, you can explore other **modify chart in Word** scenarios:

* Change slice colors with `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* Add data labels by calling `chart.getSeries().get(0).setHasDataLabel(true)`.
* Export the chart as an image using `chart.toImage(300, 300, ImageType.PNG)`.

Each of these extensions follows the same pattern: obtain the `Chart` object, call the appropriate setter, and save the document.

---

**You’ve just mastered rotating and resizing doughnut charts in Word using Java.** Feel free to adapt the code for other chart types, integrate it into a larger document‑generation pipeline, or combine it with Aspose.Slides for PowerPoint automation. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}