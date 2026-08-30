---
category: general
date: 2026-08-07
description: 如何在 Java 中使用 Aspose.Words 爆炸饼图切片。学习向饼图添加引导线、创建 Word 图表以及自定义饼图切片。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: zh
lastmod: 2026-08-07
og_description: 如何在 Java 中使用 Aspose.Words 爆炸饼图切片。本指南展示了如何向饼图添加引导线、创建 Word 图表以及自定义饼图切片，以实现清晰的视觉效果。
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: 在 Java 中如何将饼图切片分离 – Aspose.Words 指南
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
title: 如何在 Java 中突出显示饼图切片 – Aspose.Words 图表教程
url: /zh/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中实现饼图扇形突出显示 – Aspose.Words 图表教程

如果您需要了解 **如何在 Word 文档中使用 Java 突出显示饼图扇形**，本教程将为您提供完整方案。我们还将演示 **如何为饼图添加引导线**、**java 创建 Word 图表** 对象，以及 **自定义饼图扇形** 的方法，以获得精美效果。阅读完本指南后，您将拥有一个完整、可运行的示例，能够直接嵌入任何 Java 项目中。

![How to explode pie slice in Java – Aspose.Words chart](/images/pie-chart-exploded.png)

## 前置条件

开始之前，请确保您已具备：

* Java Development Kit (JDK) 8 或更高版本。  
* 用于依赖管理的 Maven 或 Gradle。  
* Aspose.Words for Java 许可证（免费评估版可用于学习）。  
* 对 Java 语法和面向对象概念的基本了解。

> **专业提示：** 虽然 Aspose.Words 提供免费试用，但购买许可证后生成的文档将不再带有评估水印。

## 本教程涵盖内容

* 从零创建一个新的 Word 文档。  
* 使用 `DocumentBuilder` 插入 **饼图**。  
* **突出显示饼图扇形** 以强调数据点。  
* **为饼图添加引导线**，实现更清晰的标签。  
* 自定义扇形外观，如颜色和边框。  
* 将文档保存到磁盘并验证结果。

---

## 使用 Aspose.Words 在 Java 中突出显示饼图扇形

第一步是设置图表对象并突出显示目标扇形。Aspose.Words 通过 `Shape` 类公开图表，每个扇形对应一个 `ChartPoint`。通过设置 `Explosion` 属性即可控制扇形向外移动的距离。

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

**工作原理：**  
`setExplosion(20)` 告诉图表引擎将扇形从图表中心向外偏移 20 个点。该值是相对的，数值越大效果越显著。您可以通过更改索引（`get(1)`、`get(2)`、…）来突出任意扇形。

## 为饼图添加引导线以实现更清晰的标签

引导线将扇形的标签与其边缘相连，尤其在扇形被突出或图表包含大量小块时非常有用。`setLeaderLines(true)` 调用会为整条系列启用此功能。

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**为何需要引导线：**  
当扇形被突出时，默认标签可能会与其他元素重叠。引导线通过从扇形绘制一条短线到文本框，保持标签的可读性。

## Java 创建 Word 图表 – 插入数据系列

没有数据的图表几乎没有意义。您必须为系列填充类别和数值。下面我们添加三个代表市场份额的类别。

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

**说明：**  
`ChartSeries` 同时保存类别（扇形名称）和数值。启用 `ShowCategoryName` 和 `ShowPercentage` 可使图表自解释，这与前面添加的引导线相得益彰。

## 在突出显示之外自定义饼图扇形

除了突出显示扇形，您通常还想调整颜色、边框，甚至完全隐藏某个扇形。下面的代码片段演示了三种常见的自定义方式：

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

**为何要自定义扇形：**  
自定义颜色可以让图表符合企业品牌，边框则提升打印版的可读性。隐藏扇形在您希望保留数据模型但暂时不在视觉输出中显示某个类别时非常有用。

## 保存文档并验证结果

最后，将文档写入磁盘。您可以使用 Microsoft Word、LibreOffice 或任何支持 `.docx` 格式的查看器打开生成的文件。

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**预期输出：**  
打开 `PieChartDemo.docx` 后，您会看到一个饼图，其中第一块（Product A）被向外突出显示，引导线从每个扇形指向其标签，且各扇形分别呈现自定义的绿色、蓝色和橙色。被隐藏的扇形（Product C）在图表中不可见，但百分比仍然累计为 100 %，因为数据仍保留在系列中。

---

## 完整可运行示例

下面是完整的程序代码，您可以复制、粘贴并在项目中添加 Aspose.Words 依赖后直接运行。

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

**依赖（Maven）**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```


## 接下来您可以学习什么？

以下教程涉及与本指南技术密切相关的主题，帮助您进一步掌握 API 功能并探索在实际项目中的替代实现方式。每篇资源均提供完整的可运行代码示例和逐步解释。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}