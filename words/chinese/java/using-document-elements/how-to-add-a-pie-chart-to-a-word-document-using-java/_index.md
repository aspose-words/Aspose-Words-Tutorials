---
category: general
date: 2026-11-15
description: 学习如何使用 Aspose.Words for Java 将饼图添加到 Word 文档中。包括环形图转换、炸裂切片以及完整代码示例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: zh
lastmod: 2026-11-15
og_description: 使用 Aspose.Words for Java 在 Word 文档中添加饼图。本教程展示如何将切片突出显示并将图表转换为环形图。
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: 使用 Java 向 Word 文档添加饼图 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: 如何使用 Java 向 Word 文档添加饼图
url: /zh/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将饼图添加到 Word 文档 – 完整的 Java 指南

如果您需要以编程方式**将饼图添加到 Word 文档**，本教程将向您展示如何使用 Aspose.Words for Java 完成此操作。您将看到完整的工作流程：加载 DOCX、创建饼图、突出显示第一块切片，以及通过设置孔径将图表转换为环形图。

本指南还涵盖了常见的变体——例如添加多个系列、定制颜色以及处理已包含图表的文档——帮助您将代码应用于自动化报告或动态演示等实际项目。

## 前置条件

* Java 17 或更高（代码也可在 JDK 11+ 上编译）
* Maven 3.6+ 或 Gradle 用于依赖管理
* Aspose.Words for Java 许可证（免费试用可用于测试）
* 对 Java 语法和 Maven 项目结构的基本了解

## 步骤 1：设置 Maven 项目并导入 Aspose.Words

创建一个新的 Maven 项目（或在现有项目中添加），并包含 Aspose.Words 依赖：

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **技巧提示：** 如果您使用 Gradle，等效的条目是 `implementation 'com.aspose:aspose-words:24.9'`。

此依赖会引入您操作图表所需的 `Document`、`Chart` 和 `ChartType` 类。

## 步骤 2：加载目标文档

您可以从现有的 `.docx` 文件开始，或创建一个新的空白文档。下面的示例加载位于 `src/main/resources` 文件夹中的名为 `input.docx` 的模板。

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

如果文件不存在，Aspose.Words 在您调用不带文件名的 `new Document()` 时会自动创建一个新的空文档。

## 步骤 3：创建饼图并插入文档

Aspose.Words 将图表视为一种形状，可放置在段落出现的任何位置。以下代码创建一个**饼图**，添加单个数据系列，并将图表插入到第一段之后。

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**此步骤的重要性：**  
* `ChartType.PIE` 告诉 Aspose.Words 渲染传统的饼图。  
* 添加同时包含类别标签和数值的系列会自动填充切片。  
* 将图表作为 `Paragraph` 的子对象插入，可保持文档的流畅性。

## 步骤 4：突出显示第一块切片

*突出切片* 可以突出显示特定的数据点。API 在 `ChartSeries` 对象上提供 `setExplode(boolean)` 方法。将其设置在第一个系列（索引 0）上即可使第一块切片弹出。

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **常见问题：** *如果我有多个系列怎么办？*  
> 您可以通过索引定位特定系列，例如对第二个系列使用 `pieChart.getSeries().get(1).setExplode(true)`。

## 步骤 5：通过设置孔径将饼图转换为环形图

环形图本质上是中心为空的饼图。Aspose.Words 允许您将孔径定义为图表半径的百分比。

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

`setHoleSize` 方法接受 **0**（普通饼图）到 **100**（完全空心）的值。约 **30‑40** 的数值可得到视觉上平衡的环形图。

## 步骤 6：保存并验证结果

完成所有修改后，保存文档。下面的代码行将文件写入 `output` 文件夹。

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### 预期输出

在 Microsoft Word 中打开 `final-pie-doughnut.docx`：

* 环形图出现在第一段的位置。  
* “Apples” 切片被突出显示（略微与其他切片分离）。  
* 图表显示四个切片，分别标记为 *Apples*、*Bananas*、*Cherries*、*Dates*，并显示您提供的百分比。

如果您更喜欢 PDF 输出，请将 `SaveFormat` 更改为 `SaveFormat.PDF`。

## 处理边缘情况和变体

### 添加多个系列

如果您需要多个系列（例如堆叠环形图），请按顺序添加它们：

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### 自定义颜色

您可以通过 `ChartDataPoint.setFillFormat().setSolidFillColor()` 为每个切片分配颜色：

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### 处理已有图表

如果文档中已经包含图表且您只想修改它，请定位图表形状：

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### 许可证处理

Aspose.Words 在生产环境中需要许可证。将您的 `Aspose.Words.lic` 文件放在类路径中，并在应用启动时加载：

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

未设置许可证会在生成的文档中添加水印。

## 完整、可运行的示例

下面是完整的 Java 类，包含所有讨论的步骤。将其复制到 `src/main/java/com/example/AddPieChart.java` 并运行 `mvn compile exec:java`。

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

运行程序会生成前面描述的环形图。根据您的数据调整 `categories`、`values` 或 `holeSize`。

## 结论

现在您已经了解如何使用 Java 和 Aspose.Words **将饼图添加到 Word 文档**。本教程涵盖了加载文档、创建饼图、突出切片、将图表转换为环形图，以及处理常见变体，如多个系列、自定义颜色和已有图表。凭借此基础，您可以构建自动化报告工具、生成动态演示，或直接在 Word 文件中嵌入丰富的可视化内容。

### 接下来可以探索的内容

* **add bar chart to Word document** – 类似步骤，但使用 `ChartType.BAR`。  
* **customize chart legends and titles** – 使用 `pieChart.getTitle().setText("...")` 和 `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`。  
* **export the Word document as PDF** – 将 `SaveFormat` 更改为 `PDF` 以生成可分发的文件。  
* **populate chart data from a database** – 用 JDBC 查询结果替换静态数组。

随意尝试不同的图表类型、数据源和样式选项。祝编码愉快！

## 接下来应该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方法。

- [如何在 Java 中突出饼图切片 – Aspose.Words 图表教程](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [使用 Aspose.Words Java 创建饼图 – 完整分步指南](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}