---
category: general
date: 2026-10-26
description: Create doughnut chart and insert pie chart in Java with step‑by‑step
  code. Learn the full workflow for flexible chart visualizations.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: en
lastmod: 2026-10-26
og_description: Create doughnut chart in Java with this guide that also shows how
  to insert pie chart for flexible visualizations.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Create doughnut chart and insert pie chart – Java guide
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Create a doughnut chart and insert a pie chart using Aspose.Cells for Java
url: /java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create a doughnut chart and insert a pie chart

If you need to **create doughnut chart** in Java, this tutorial walks you through the exact steps. We'll also show how to **insert pie chart** using the same builder API, so you can switch between visual styles effortlessly. By the end of the guide you will have a complete, runnable program that produces both chart types and demonstrates common customizations.

The tutorial covers:

* Initializing the chart builder provided by the chosen library.  
* Creating a doughnut chart and configuring the hole size.  
* Inserting a pie chart and exploding a slice for emphasis.  
* Tips for handling edge cases such as missing series or unsupported chart types.

You only need a recent JDK (8 or later) and the chart library JAR on your classpath. No external services are required.

---

## Prerequisites

| Item | Reason |
|------|--------|
| Java Development Kit (JDK) 8+ | Required to compile and run the example. |
| Chart library (e.g., **Aspose.Cells for Java** or **JFreeChart**) | Provides `ChartBuilder`, `ChartType`, and series manipulation methods used in the code. |
| An IDE or a text editor | To write and execute the Java source file. |

Make sure the library JAR is added to your project's build path. If you use Maven, add the appropriate dependency; otherwise, place the JAR in the `libs` folder and reference it during compilation.

---

## Step 1: Set up the chart builder

The first step is to create a `ChartBuilder` (or equivalent) instance that will generate the chart objects. This object acts as a factory and holds the worksheet or canvas where the chart will be placed.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Why this matters:**  
The builder ties the chart to a specific worksheet, ensuring that all subsequent chart objects share the same drawing surface. Skipping this step would leave you without a target location for the visual elements.

---

## Step 2: **Create doughnut chart**

Now we generate a doughnut chart with a defined size. The hole size determines how much of the chart’s center is empty, turning a regular pie into a doughnut.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Explanation:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` creates the chart object and reserves space on the worksheet.  
* `setHoleSize(30)` converts the pie into a doughnut with a 30 % empty center.  
* `add("{10, 20, 30, 40}", true)` supplies four data points; the `true` flag tells the library to treat the values as a single series.

**Edge case:** If the selected chart type does not support a hole (e.g., a bar chart), calling `getDoughnutChart()` throws an exception. Always verify the chart type before adjusting the hole size.

---

## Step 3: **Insert pie chart**

After the doughnut is ready, we demonstrate how to **insert pie chart** using the same builder. This step highlights the similarity between the two chart types and shows how to emphasize a slice.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Explanation:**  

* `ChartType.PIE` tells the builder to create a classic pie chart.  
* `setExplode(10)` offsets the first slice by 10 % of the radius, a common technique to highlight a key data point.  

**Tip:** The `setExplode` method works only on the first series of a pie chart. If you have multiple series, you must target the correct index.

---

## Step 4: Save the workbook

Finally, write the workbook to a file so you can view the charts in Excel or any compatible viewer.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Why save now:** Persisting the workbook finalizes all drawing operations. Attempting to view the file before saving results in an empty or incomplete document.

**Result:** Opening *DoughnutAndPieChart.xlsx* shows a 30 % hole doughnut chart on the left and a pie chart with an exploded first slice on the right.

---

## Step 5: Common variations and troubleshooting

| Situation | Adjustment |
|-----------|------------|
| **Different chart dimensions** | Change the width and height arguments in `insertChart`. |
| **Multiple data series** | Call `add` multiple times or pass a 2‑D array string. |
| **Dynamic hole size** | Compute the hole size based on data range, then call `setHoleSize`. |
| **Explode multiple slices** | Loop through `chart.getSeries().get(i).setExplode(percent)` for each slice you want to offset. |
| **Library not supporting doughnut** | Use a pie chart and manually draw a white circle overlay, though this is less precise. |

**Pro tip:** Always call `builder.flush()` (if available) after inserting charts when working with large workbooks. This releases internal buffers and prevents memory leaks.

---

![Java code creating a doughnut chart and inserting a pie chart](https://example.com/images/doughnut-pie-java.png "create doughnut chart example in Java")

*The image illustrates the final workbook layout with both charts side by side.*

---

## Conclusion

You now know how to **create doughnut chart** and **insert pie chart** in Java using a fluent builder API. The full example covers initialization, size configuration, hole sizing, slice explosion, and file output. From here you can explore additional customizations such as colors, legends, and data labels to match your reporting requirements.

**Next steps**

* Experiment with **chart customization Java** features like gradient fills and data labels.  
* Integrate the chart generation into a web service that returns the workbook on demand.  
* Compare the builder approach with other libraries (e.g., JFreeChart) to choose the best fit for your project.

Happy charting!


## What should you learn next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- {{< relref "words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/" >}}Create doughnut chart in a Word document with Java{{< /relref >}}
- {{< relref "words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/" >}}Save Word document after editing doughnut chart in Java{{< /relref >}}
- {{< relref "words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/" >}}Insert Pie Chart in Java – Explode, Rotate & Highlight Slices{{< /relref >}}

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}