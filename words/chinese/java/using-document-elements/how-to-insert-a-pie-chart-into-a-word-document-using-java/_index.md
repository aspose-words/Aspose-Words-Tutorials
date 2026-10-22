---
category: general
date: 2026-09-27
description: 学习如何使用 Java 将饼图插入 Word 文档，创建 Word 中的饼图，并在饼图上显示百分比，以获得清晰的数据洞察。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: zh
lastmod: 2026-09-27
og_description: 如何使用 Java 将饼图插入 Word 文档。本指南展示了如何在 Word 中创建饼图、在饼图上显示百分比以及添加引线。
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: 如何使用 Java 将饼图插入 Word 文档
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: 如何使用 Java 将饼图插入 Word 文档
url: /zh/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Java 在 Word 文档中插入饼图

如果您需要 **how to insert pie chart** 到 Word 文件中，本指南将带您完整了解整个过程。您将看到如何 **create pie chart in Word**，在每个切片上显示百分比，并添加引线以获得精致的外观。

Word 自动化通常感觉笨重，但使用 Aspose.Words for Java，您可以以编程方式生成完整格式化的文档。完成本教程后，您将拥有一个可运行的 Java 代码片段，生成包含样式化饼图的 Word 文档。

## 前提条件

在开始之前，请确保您已具备：

- 已安装 Java 17 或更高版本
- 用于管理依赖的 Maven 或 Gradle
- 已在项目中添加 Aspose.Words for Java（版本 23.11 或更高）
- 对 Java 语法有基本了解

您无需具备任何图表 API 的先前经验；以下步骤涵盖了从项目设置到最终输出的全部内容。

## 步骤 1：设置 Maven 依赖

将 Aspose.Words 库添加到您的 `pom.xml` 中。此单一依赖即可让您使用 `Document`、`DocumentBuilder` 和图表类。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

如果您使用 Gradle，则等价写法如下：

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **技巧提示：** 使用最新的稳定版本，以获得错误修复和新图表功能的好处。

## 步骤 2：创建新文档和构建器

`Document` 对象代表 Word 文件，而 `DocumentBuilder` 允许您插入内容。这是 **add chart to word document** 的基础。

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

构建器现在已准备好在文档的任何位置放置对象。

## 步骤 3：插入饼图

Aspose.Words 支持多种图表类型；这里我们选择 `ChartType.PIE`。尺寸以磅为单位表示（1 磅 = 1/72 英寸）。

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

此时图表包含一个带有占位值的默认数据系列。如有需要，您可以稍后替换这些值。

## 步骤 4：访问图表系列

饼图只有一个系列，用于保存切片的数值。获取该系列以进行格式化。

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## 步骤 5：突出显示第一块切片

将切片“炸开”可突出显示特定数据点。当您想要强调关键指标时，这是一种常见的视觉提示。

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## 步骤 6：在每个切片上显示百分比

在图表上直接显示百分比可提升数据洞察力。这满足了 **show percentages on pie chart** 的需求。

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## 步骤 7：添加引线以获得更清晰的标签

引线将切片标签连接到对应的区域，消除歧义。这实现了 **how to add leader lines**。

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## 步骤 8：保存文档

最后，将文档写入磁盘。您可以选择任意有写入权限的文件夹。

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

运行程序后会生成 `output/PieFormatted.docx`。在 Microsoft Word 中打开该文件，您将看到一个饼图，其中：

- 第一块切片被突出显示。
- 每块切片显示其百分比值。
- 引线从百分比指向对应的切片。

### 预期输出

![Word 中的格式化饼图](/images/pie-formatted.png){: .center-image alt="已插入 Word 文档的格式化饼图"}

该截图（alt 文本使用了主要关键词）展示了最终效果：一个简洁、数据驱动的饼图，可用于报告、提案或仪表板。

## 常见变体和边缘情况

### 更改切片数值

如果需要自定义数据，请替换默认系列的数值：

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### 多系列（环形图）

虽然简单的饼图只有一个系列，Aspose.Words 也支持具有多个系列的环形图。将 `ChartType.PIE` 切换为 `ChartType.DONUT` 并重复系列配置步骤。

### 导出为 PDF

如果后续工作流需要 PDF，请在构建图表后调用 `doc.save("output/PieFormatted.pdf");`。视觉布局保持一致。

## 完整源码列表

下面是完整的、可直接复制粘贴到 IDE 中的 Java 文件。

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

使用 `mvn compile exec:java -Dexec.mainClass=PieChartExample`（或等价的 Gradle 命令）编译并运行程序。生成的 Word 文件将包含完整格式化的饼图。

## 结论

您现在已经了解了如何使用 Java **how to insert pie chart** 到 Word 文档，如何 **create pie chart in Word**，如何 **show percentages on pie chart**，以及如何使用引线 **add chart to word document**。完整示例演示了每一步，解释了代码编写原因，并提供了自定义提示。

接下来，您可以探索：

- 使用自定义字体添加数据标签（**show percentages on pie chart** 变体）
- 在单个文档中组合多个图表（**add chart to word document** 用例）
- 将表格和图表一起自动化生成报告

欢迎尝试不同的颜色、切片顺序或导出为 PDF。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南紧密相关的主题，基于所示技术进行深入。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能，并在自己的项目中探索替代实现方案。

- [如何使用 Aspose.Words for Java 创建柱状图](/words/english/java/document-conversion-and-export/using-charts/)
- [在 Word 文档中隐藏图表坐标轴](/words/english/net/programming-with-charts/hide-chart-axis/)
- [使用 Aspose.Words for .NET 在 Word 中创建折线图](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}