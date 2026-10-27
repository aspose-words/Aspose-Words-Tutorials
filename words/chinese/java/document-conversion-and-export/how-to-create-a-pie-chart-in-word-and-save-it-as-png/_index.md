---
category: general
date: 2026-10-07
description: 学习如何在 Word 中创建饼图、添加数据系列，并使用 Java 将图表保存为 PNG。按照一步一步的指南快速获得结果。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: zh
lastmod: 2026-10-07
og_description: 快速在 Word 中创建饼图：本教程展示如何添加数据系列、生成图表，并将 Word 图表保存为图片（PNG）。请参照完整代码示例。
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: 在 Word 中创建饼图并导出为 PNG – 指南
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: 如何在 Word 中创建饼图并保存为 PNG
url: /zh/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中创建饼图并保存为 PNG

如果您需要在 Microsoft Word 文件中 **创建饼图** 对象，本指南将向您展示如何使用 Java 完成此操作。您还将学习如何 **添加数据系列** 到图表以及 **将图表保存为 PNG**，以便在 Word 之外重复使用该可视化。

直接在文档中生成图表可以避免将数据导出到单独的图形工具。完成本教程后，您将拥有一个包含饼图的完整 Word 文件，以及磁盘上对应的 PNG 图像。

## 前置条件

开始之前，请确保您具备以下条件：

* 已安装 Java 17 或更高版本。
* **GroupDocs.Viewer for Java**（或提供 `Document`、`Chart`、`ChartType`、`ImageSaveOptions` 类的兼容库）。
* 可以添加库依赖的 Maven 或 Gradle 项目。
* 位于可从代码引用的文件夹中的输入 Word 文档（`input.docx`）。

如果您使用 Maven，请添加依赖（将 `VERSION` 替换为最新版本）：

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## 如何在 Word 中创建饼图

该解决方案的核心围绕三个操作：

1. 加载源 `.docx` 文件。
2. **添加数据系列** 到类型为 `PIE` 的新 `Chart` 对象。
3. **将图表保存为 PNG**，以便在 Word 文档旁边获得图像文件。

下面将逐步详细说明每一步，并提供所需的完整 Java 代码。

### 步骤 1：加载源文档

您必须打开将承载图表的 Word 文件。`Document` 类会将 `.docx` 内容读取到内存中。

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*为什么重要*：加载文档会创建一个可变模型。随后所有图表操作都修改该内存表示，最后再持久化回磁盘。

### 步骤 2：向图表添加数据系列

创建 **饼图** 从 `Chart` 实例开始。构造函数接收父 `Document` 和图表类型 (`ChartType.PIE`)。图表对象创建后，您即可填充数值和可选标签。

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*为什么重要*：`add` 方法 **添加数据系列** 到图表。`values` 中的每个条目都会成为饼图的一块，而 `categories` 提供图例标签。您可以提供任意数量的点，库会自动计算切片角度。

### 步骤 3：将图表保存为 PNG

图表已嵌入文档后，您可以导出其可视化表示。底层图表对象的 `save` 方法会将 PNG 文件写入文件系统。

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*为什么重要*：将图表保存为 PNG 可得到光栅图像，您可以将其嵌入网页、电子邮件或报告中，而无需原始 Word 文件。`ImageSaveOptions` 对象允许您控制格式、分辨率等导出设置。

## 在 Word 中生成饼图 – 自定义外观

除了基本步骤，您可能想自定义颜色、标题或数据标签。大多数库会暴露 `ChartOptions` 或类似对象。下面示例演示如何添加标题并更改切片颜色：

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

这些自定义是可选的，但展示了如何 **在 Word 中生成饼图** 以匹配您的品牌风格。

## 将 Word 图表保存为图像 – 替代方法

如果您只需要图像而不需要将图表插入文档，可以在创建图表后直接调用 `save` 方法，而省略将图表形状添加到 Word 正文的步骤。代码保持不变，只是跳过了向文档主体添加图表的步骤。

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

此技巧在批量生成大量图表且只关心 PNG 输出时非常有用。

## 完整可运行示例

将以下类复制到项目中，调整文件路径后运行。程序将：

1. 加载 `input.docx`。
2. **创建饼图**、**添加数据系列**，并将其嵌入文档。
3. **将图表保存为 PNG**（`radial.png`）。
4. 将修改后的 Word 文件持久化为 `output.docx`。



## 接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方案。每个资源均提供完整可运行的代码示例和逐步说明。

- [如何使用 Aspose.Words for Java 创建柱状图](/words/english/java/document-conversion-and-export/using-charts/)
- [使用 Aspose.Words for .NET 创建 Word 散点图](/words/english/net/working-with-charts/insert-scatter-chart/)
- [在 Word 中使用 Aspose.Words for .NET 插入柱状图](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}