---
category: general
date: 2026-09-18
description: 学习如何使用 Java 在 Word 文档中创建径向图表，添加图表数据标签，并通过完整的代码示例插入系列数据。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: zh
lastmod: 2026-09-18
og_description: 使用 Java 在 Word 文档中创建径向图表，添加图表数据标签，并在同一教程中插入系列数据。
og_image_alt: Radial chart displayed inside a generated Word document
og_title: 使用 Java 在 Word 中创建径向图表 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: 如何在 Word 文档中使用 Java 创建径向图
url: /zh/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Java 在 Word 文档中创建径向图表

如果您需要在 Word 文档中创建径向图表，本指南将为您展示完整步骤。您还将学习如何添加图表数据标签以及插入系列数据，使图表准备好用于展示。

以编程方式生成图表可以消除手动格式化的工作，并确保报告之间的一致性。本文假设您具备基本的 Java 知识，并已安装最新版本的 Aspose.Words for Java 库。

## 您需要的环境

* Java 17 或更高版本  
* Aspose.Words for Java（版本 23.12 或更高）  
* 能解析 Maven/Gradle 依赖的 IDE 或构建工具  

安装好这些前置条件后，您即可在无需额外配置的情况下运行示例。

## 如何在 Word 文档中创建径向图表

第一步是创建一个空白的 Word 文件，用来容纳图表。空白文档提供了干净的画布，避免意外的样式影响。

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 代表整个 .docx 文件，而 `DocumentBuilder` 提供插入段落、表格和图表等元素的方法。

## 如何插入图表

接下来插入图表本身。`insertChart` 方法会创建一个图表对象，并将其放置在 Builder 当前光标位置。

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

极坐标图（polar chart）将在中心轴周围呈现数据点，非常适合展示循环信息。尺寸以点（pt）为单位（1 pt ≈ 1/72 英寸）。

## 向图表添加系列数据

没有系列数据的图表是空的。您可以手动添加系列，或将其绑定到数据源。下面的示例为图表添加了一个包含三个数据点的单一系列。

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` 接收系列名称、类别标签列表以及对应的数值列表。您可以重复此代码块来添加更多系列（`addSeriesData`）。

## 为第一系列添加图表数据标签

数据标签使图表在不悬停的情况下也能阅读。下面的代码行会为第一系列打开数值标签。

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

将 `showValue` 设置为 `true` 可直接在图表上显示每个点的数值。您还可以通过同一个 `DataLabelFormat` 对象启用类别名称、百分比或引导线等。

## 保存 Word 文件

图表配置完成后，将文档写入磁盘。请选择您的应用程序能够访问的位置。

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

文件 `RadialChart.docx` 现在包含了一个带有数据标签的完整径向图表。

## 完整可运行示例

下面是一个独立的程序，您可以复制、编译并运行。它演示了从创建空白 Word 文档到保存带有数据标签的径向图表的完整工作流。

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**预期结果**

在 Microsoft Word 中打开 `output/RadialChart.docx`，您将看到标题为 *Quarterly Sales* 的径向图表。每个点旁边都会显示其数值（例如 “15000”）。

## 常见变体和边缘情况

| 情况 | 推荐的更改 |
|-----------|--------------------|
| 需要使用不同的图表类型 | 将 `ChartType.POLAR` 替换为其他 `ChartType` 枚举值（例如 `ChartType.COLUMN`）。 |
| 图表必须使用外部 Excel 区域 | 在创建图表并加载工作簿后，使用 `chart.setDataRange("Sheet1!A1:B5")`。 |
| 想隐藏图例 | `chart.getLegend().setVisible(false);` |
| 文档必须保存为 PDF | 调用 `doc.save("RadialChart.pdf");` – Aspose.Words 会自动转换图表。 |

这些调整在保持核心逻辑不变的前提下，能够满足特定需求。

## 专业技巧

* **复用 Builder** – 通过多次调用 `builder.insertChart`，您可以在同一文档中插入多个图表。  
* **性能** – 生成大量图表时，创建单个 `DocumentBuilder` 实例并复用，可降低对象分配开销。  
* **样式** – 图表外观（颜色、线条粗细）通过 `Chart` 对象的 `getSeries().get(i).getFormat()` 方法控制。尝试这些设置以匹配企业品牌形象。

## 结论

现在，您已经掌握了使用 Java 在 Word 文档中创建径向图表、添加系列数据以及图表数据标签的完整流程，并能够保存文件。完整示例可进一步扩展，以处理更多系列、定制样式或输出为其他格式。

探索相关主题，例如 **如何从外部数据源插入图表**、**使用预定义模板创建空白 Word 文档**，以及 **从数据库动态添加系列数据**。尝试不同的图表类型，发现最能传达您数据的可视化方式。

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您在项目中进一步使用这些技巧。每个资源都提供了完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并探索替代实现方案。

- [如何使用 Aspose.Words for Java 创建柱状图](/words/english/java/document-conversion-and-export/using-charts/)
- [Java 创建 Word 文档 – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [在图表中设置数据标签的默认选项](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}