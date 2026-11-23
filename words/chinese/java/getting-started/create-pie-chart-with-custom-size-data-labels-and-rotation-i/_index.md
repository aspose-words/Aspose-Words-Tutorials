---
category: general
date: 2026-11-22
description: 在 Java 中创建饼图，并学习如何设置图表大小、添加数据标签、显示百分比，以及旋转第一块切片以获得清晰的视觉效果。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: zh
lastmod: 2026-11-22
og_description: 在 Java 中创建饼图，然后设置图表大小，在数据标签上显示百分比，并旋转第一块——全部在一个可运行的示例中完成。
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: 在 Java 中创建自定义尺寸、标签和旋转的饼图
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: 在 Java 中创建自定义尺寸、数据标签和旋转的饼图
url: /zh/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中创建自定义尺寸、数据标签和旋转的饼图

如果您需要 **创建饼图**（create pie chart）在 Java 中，本指南将带您完成整个过程。您将学习如何 **设置图表尺寸**（set chart size）、启用 **显示百分比的饼图**（show percentages pie chart）、添加 **饼图数据标签**（data labels pie chart），以及 **旋转饼图切片**（rotate pie chart slice），使第一块切片从 45 度角开始。

示例使用 **Aspose.Slides for Java**，这是一个广泛使用的 PowerPoint 文件操作库。相同的概念同样适用于其他制图库，只需将 API 调用替换为您工具包中的等价方法即可。

## 前置条件

在开始之前，请确保您具备：

* 已安装 Java 17 或更高版本  
* Maven 3.8+（或 Gradle）用于依赖管理  
* 基本的 Java 语法了解  
* 获取 Aspose.Slides for Java 二进制文件的权限（可从官方网站获取免费试用版）

在 `pom.xml` 中添加依赖：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## 创建饼图 – 完整示例

下面的程序会创建一个包含自定义尺寸、百分比数据标签以及旋转首块切片的饼图的 PowerPoint 幻灯片。

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### 为什么每一步都很重要

| 步骤 | 目的 | 与关键词的关联 |
|------|------|----------------|
| **插入图表** | **创建饼图**（create pie chart） – 渲染可视化的核心对象。 | 直接满足 *create pie chart* 的需求。 |
| **设置尺寸** | `addChart(..., 400, 300)` 调用演示了 **设置图表尺寸**（set chart size）。 | 控制宽度（400 px）和高度（300 px）。 |
| **显示百分比** | `setShowPercentage(true)` 使图表 **显示百分比的饼图**（show percentages pie chart）在每个切片上。 | 用户常需要百分比而非原始数值。 |
| **添加数据标签** | `DataLabelFormat` 配置添加了 **饼图数据标签**（data labels pie chart）并设置可见性。 | 标签提升可读性且可自定义。 |
| **旋转切片** | `setFirstSliceAngle(45)` 旋转图表，使第一块切片从 45 度角开始，满足 **旋转饼图切片**（rotate pie chart slice）。 | 突出特定切片的视觉效果。 |

## 步骤拆解

### 1. 插入饼图并设置图表尺寸

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*`addChart` 方法创建图表的同时 **设置图表尺寸** 为 400 × 300 点。*  
如果需要其他尺寸，请调整最后两个参数。

### 2. 为图表填充数据

示例添加了三个类别和一个系列。根据需要将硬编码的数字替换为数据库、CSV 或用户输入的数据。

### 3. 在每个切片上显示百分比

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*启用 `setShowPercentage(true)` 可确保图表 **显示百分比的饼图** 自动计算每个切片占总数的比例。*

### 4. 添加详细的数据标签

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

您可以切换其他标签选项（`setShowValue`、`setShowSeriesName` 等）以定制 **添加数据标签的饼图** 体验。

### 5. 旋转第一块切片

```java
chart.setFirstSliceAngle(45);
```

*调用 `setFirstSliceAngle(45)` **旋转饼图切片**，使第一段从 45 度角开始，从而突出显示。*

### 6. 保存并查看结果

运行程序后会生成 `output/PieChartDemo.pptx`。在 PowerPoint 或任何兼容的查看器中打开，即可看到最终的饼图：

![Create pie chart example](images/pie_chart_example.png){.align-center alt="创建的饼图截图，具有自定义尺寸、百分比标签和旋转的第一块切片"}

上述图片展示了 **创建饼图** 的效果，确认了尺寸、标签、百分比和旋转均已正确应用。

## 常见变体和边缘情况

| 情形 | 调整方式 |
|------|----------|
| **不同的图表尺寸** | 更改 `addChart` 中的宽度/高度参数。 |
| **多个系列** | 添加额外的 `IChartSeries` 对象；每个系列可以拥有自己的标签设置。 |
| **自定义标签格式** | 使用 `series.getDataLabelFormat().setNumberFormat("0.0%")` 控制小数位数。 |
| **旋转到其他角度** | 向 `setFirstSliceAngle` 传入任意整数（0‑360）。 |
| **导出为图片** | 保存后调用 `chart.writeAsSvg(outPath)` 或 `chart.writeAsPng(outPath)` 获取光栅版。 |

> **专业提示：** 如果计划在循环中生成大量图表，复用同一个 `Presentation` 对象并仅替换图表数据。这可以降低内存开销并加快处理速度。

## 结论

现在您已经掌握了在 Java 中 **创建饼图**、**设置图表尺寸**、启用 **显示百分比的饼图**、**添加饼图数据标签**，以及 **旋转饼图切片** 以获得更好的视觉强调。完整、可运行的示例展示了从初始化到保存最终 PowerPoint 文件的每一步。

### 接下来做什么？

* 使用相同的 `ChartType` 枚举探索其他图表类型（柱形图、折线图、面积图）。  
* 在单个幻灯片上组合多个图表，构建仪表盘。  
* 将图表导出为 PNG 或 SVG，以在 Web 应用中使用。  

随意尝试颜色、图例和动画效果——您的数据可视化仅受想象力的限制。祝您绘图愉快！

## 接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。每个资源都包含完整的可运行代码示例和逐步解释。

- [how to insert pie chart in Word – add data label percent](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Insert Pie Chart in Java – Explode, Rotate & Highlight Slices](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}