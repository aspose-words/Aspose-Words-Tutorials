---
category: general
date: 2026-07-20
description: 在 Java 中插入饼图并提供一步一步的指南。了解如何将切片炸开、如何旋转饼图、如何突出显示饼图切片以及如何自定义饼图切片。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: zh
lastmod: 2026-07-20
og_description: 在 Java 中插入饼图，并掌握如何炸裂切片、如何旋转饼图、如何突出显示饼图切片，以及如何自定义饼图切片，以实现精美的可视化报告。
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: 在 Java 中插入饼图 – 爆炸、旋转与高亮
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: 在 Java 中插入饼图——爆炸、旋转与高亮切片
url: /zh/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中插入饼图 – 爆炸、旋转和高亮切片

是否曾经需要在 Java 报告中 **insert pie chart**，但不确定如何让单个切片突出显示？你并不是唯一遇到这种情况的人。无论是构建仪表盘、生成发票，还是仅仅可视化调查结果，一个精美的饼图都能将原始数据转化为一目了然的洞察。

在本教程中，你将看到一个完整、可直接运行的示例，展示如何 **insert pie chart**、**how to explode slice**、**how to rotate pie chart**，甚至使用自定义颜色 **highlight pie chart slice**。完成后，你将拥有一个可复用的代码片段，能够直接放入任何使用流行 *JFreeChart* 库（或其他类似 API）的 Java 项目中。

## Prerequisites

- Java 17 或更高（代码在旧版本也能编译，但我们将使用现代的 `var` 语法以简化代码）。
- Maven 或 Gradle 用于引入 `org.jfree:jfreechart` 依赖。
- 对 Java 类以及图表构建器概念有基本了解。

如果你从未向 Maven 项目添加过库，只需将以下内容放入你的 `pom.xml`：

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

就这样——无需额外设置。

## 第一步：插入饼图 – 创建构建器和图表对象

首先，我们需要一个 *builder*（可以把它想象成工厂），它知道如何生成图表。在 JFreeChart 中，`ChartFactory` 承担了大部分工作。

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

为什么要先创建数据集？因为图表本身只是数字的可视化包装。通过 **inserting pie chart** 这里我们已经拥有了一个 400 × 300 的画布（尺寸将在稍后渲染为图像时应用）。

## 第二步：如何爆炸切片 – 突出显示第一个片段

图表已经创建好后，让我们让第一块切片突出显示。爆炸切片会将其稍微移离圆心，从而吸引读者的视线。

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

请注意我们在方法名中使用了 **how to explode slice** 这一短语，这让意图一目了然。`setExplodePercent` 方法接受一个键（切片标签）和一个百分比，你可以根据需要调整“弹出”距离。

## 第三步：如何旋转饼图 – 更改起始角度

默认的饼图从 12 点位置开始。有时你希望第一块切片从其他位置开始——可能是为了与设计稿对齐，或与其他图表保持一致。

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

调用 `rotateChart(chart, 45)` 会将整个饼图旋转，使 “Apples” 切片从 45 度角开始，这正是 **how to rotate pie chart** 所要求的效果。

## 第四步：高亮饼图切片 – 自定义颜色和标签

除了爆炸之外，你可能还想为某个切片设置独特的颜色或加粗的标签，以真正 **highlight pie chart slice**。

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

这里我们通过修改切片的 paint 和标签样式实现了 **customize pie chart slice**。随意更换颜色或字体，以匹配你的品牌配色。

## 第五步：将图表渲染为图像（可选但实用）

大多数实际应用都需要将图表保存为 PNG、JPEG，甚至 PDF。下面是一种快速将图表写入文件的方法。

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

运行完整流程将生成一个 400 × 300 的 PNG，效果大致如下：

![Insert pie chart example](image.png){: alt="插入饼图示例，展示已爆炸和旋转的切片"}

## 完整工作示例

将所有步骤组合起来，下面是一个可以直接复制粘贴到新建 Java 类并执行的 `main` 方法：

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### 预期输出

运行程序会生成一个名为 **fruit-pie.png** 的文件。打开后你会看到：

- 一个 400 × 300 的饼图，标题为 “Fruit Distribution”。  
- “Apples” 切片向外爆炸 15%。  
- 整个图表已旋转，使 “Apples” 从 45 度位置开始。  
- 已爆炸的切片（此处原文未完，保持原样）

## 接下来应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助你在已有技巧的基础上进一步深入。每个资源都提供完整的可运行代码示例，并配有逐步解释，帮助你掌握更多 API 功能并在自己的项目中探索替代实现方案。

- [如何使用 Aspose.Words for Java 创建柱状图](/words/english/java/document-conversion-and-export/using-charts/)
- [插入散点图](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [插入面积图](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}