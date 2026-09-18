---
category: general
date: 2026-09-18
description: 学习使用 Aspose.Words for Java 创建 Word 文档并插入饼图。包括旋转饼图和生成 Word 文件的步骤。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: zh
lastmod: 2026-09-18
og_description: 使用 Java 创建 Word 文档并插入饼图。按照本指南旋转饼图、突出切片并生成 Word 文件。
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: 使用 Java 分步指南创建包含饼图的 Word 文档
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: 如何在 Java 中创建带有饼图的 Word 文档
url: /zh/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中创建包含饼图的 Word 文档

如果您需要 **创建一个 Word 文档** 来可视化数据，本指南将向您展示如何使用 Aspose.Words for Java 实现。您将学习插入饼图、突出显示切片、旋转图表，最后 **生成一个 Word 文件**，可以在 Microsoft Word 中打开。

构建结合文本和图表的报告并不需要额外的图形工具。完成本教程后，您将拥有一个完整的可运行程序，能够创建包含完整配置饼图的 .docx 文件。

## 前置条件

- Java 17 或更高版本（代码同样可以在 Java 8+ 上编译）
- 用于依赖管理的 Maven 或 Gradle
- Aspose.Words for Java 许可证（免费试用版可用于本示例）
- 对 Java 语法的基本了解

## 步骤 1：设置 Maven 项目

创建一个新的 Maven 项目，并在 `pom.xml` 中添加 Aspose.Words 依赖：

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **小技巧：** 保持版本号为最新；新版本会加入图表类型的改进和错误修复。

## 步骤 2：创建新的 Word 文档

以编程方式 **创建一个 Word 文档** 的第一步是实例化一个 `Document` 对象。该对象在内存中表示整个 .docx 文件。

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

`Document` 类是所有 Word 处理功能的入口点。此时尚未向磁盘写入任何文件；所有操作都在 RAM 中进行，直至调用 `save`。

## 步骤 3：插入饼图

`DocumentBuilder` 允许您向文档添加内容。使用 `insertChart` 可以直接 **插入饼图** 对象。

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` 告诉 Aspose.Words 创建一个饼图。尺寸以点为单位（1 pt ≈ 1/72 in）。调用后，图表会出现在一个新段落中。

## 步骤 4：为图表填充数据

饼图需要一系列数值。这里我们添加三个类别：“Apples”、 “Bananas” 和 “Cherries”。

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

`add` 方法构建系列并自动创建图例条目。您可以对任何数值数据集复用此模式。

## 步骤 5：强调第一块切片

突出显示切片可以将注意力集中在特定数值上。第一块切片（索引 0）被向外突出 20 points。

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

在系列上设置 `explode` 会影响整个图表，因此只有第一个数据点被偏移。

## 步骤 6：旋转饼图

旋转图表可以提升视觉平衡，尤其是当最大切片不在顶部时。`setRotationAngle` 方法接受角度值（度）。

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

45° 的旋转会顺时针移动起始角度，使图表在多数布局中更易阅读。

## 步骤 7：保存文档并生成 Word 文件

最后，将文档写入磁盘。此步骤 **生成 Word 文件**，可使用 Microsoft Word、LibreOffice 或任何兼容的查看器打开。

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`save` 方法会自动识别 .docx 扩展名并写入兼容的 Word 包。文件夹 `output` 必须已存在，或可通过代码创建。

### 预期输出

运行程序后，打开 `output/PieChart.docx`，您应看到：

- 单页包含一个 400 × 300 pt 的饼图。
- “Apples” 切片向外突出 20 pt。
- 整个图表顺时针旋转 45°。
- 与三种水果类别对应的图例。

## 常见变体和边缘情况

### 插入多个图表

如果需要插入多于一个的图表，可在移动光标后再次调用 `builder.insertChart`：

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### 更改图表颜色

可以通过系列的 `getPoints()` 集合自定义切片颜色：

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### 处理大型数据集

对于超过 10 块切片的数据集，考虑使用环形图（`ChartType.DOUGHNUT`）以保持视觉清晰。

## 结论

现在您已经掌握了使用 Aspose.Words for Java **创建 Word 文档**、**插入饼图**、**旋转饼图** 并 **生成 Word 文件** 的完整流程。完整示例展示了从文档初始化到最终文件输出的全套工作流，涵盖了每一步的 “如何做” 与 “为何如此”。

接下来，您可以探索诸如 **如何从数据库创建饼图数据**、添加数据标签或将图表导出为图像等相关主题。尝试不同的图表类型（柱形、折线、环形），以拓宽您的 Word 自动化工具箱。

## 接下来您应该学习什么？

以下教程涵盖与本指南紧密相关的主题，帮助您进一步掌握 API 功能并在项目中尝试替代实现方式，每个资源均提供完整的可运行代码示例和逐步解释。

- [如何使用 Aspose.Words for Java 创建柱状图](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [使用 Aspose.Words Java 跟踪 Word 文档更改：文档修订完整指南](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}