---
category: general
date: 2026-11-15
description: 学习如何在 Word 文档中创建饼图并使用 Java 将 docx 保存为 PDF。本指南还涵盖将 Word 转换为 PDF 以及如何添加图表。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: zh
lastmod: 2026-11-15
og_description: 在 Word 文件中创建饼图并将 docx 保存为 PDF，使用 Java。请按照本分步教程将 Word 转换为 PDF 并添加图表。
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: 在 Word 中创建饼图并将 docx 保存为 PDF – Java 指南
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: 如何在 Word 中创建饼图并将 docx 保存为 PDF
url: /zh/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中创建饼图并将 docx 保存为 PDF

如果您需要在 Word 文档中**创建饼图**并随后**将 docx 保存为 PDF**，本教程将准确演示操作步骤。您将看到一个完整、可运行的示例，它在嵌入饼图的同时将 .docx 文件转换为 PDF，从而无需搜索零散代码片段即可回答“如何添加图表”。

在本指南中，您将学习：

* 加载已有的 *.docx*（或从头开始）  
* 使用 Aspose.Words for Java **创建饼图** 并填充数据  
* **将 docx 保存为 PDF**，并确保图表正确渲染  
* 了解在涉及图表时 **convert word to pdf** 的细微差别  

这些步骤适用于 Aspose.Words 2024‑x.x 和 Java 17，但其概念同样适用于任何支持 Word 图表操作的库。

## 前提条件

在开始之前，请确保您具备以下条件：

| 要求 | 原因 |
|------|------|
| Java 17（或更高） | 最新的 Aspose.Words JAR 所需 |
| Maven 或 Gradle 构建工具 | 简化依赖管理 |
| Aspose.Words for Java（最新版本） | 提供 `Document`、`Chart` 和 `ChartType` 类 |
| 一个输入的 **.docx** 文件（或空白文档） | 图表将插入该文件中 |

将 Aspose.Words 依赖添加到您的 `pom.xml`（Maven）或 `build.gradle`（Gradle）中。以下是 Maven 示例：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## 步骤 1：加载 Word 文档（或创建新文档）

第一步是获取一个 `Document` 实例。如果您已有模板，传入其路径；否则创建一个空文档。

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*为什么需要这一步？* `Document` 对象是所有 Word 内容的容器，包括图表。加载已有文件可以在添加新可视元素的同时保留周围的文本和样式。

## 步骤 2：**创建饼图** – “how to create chart”的核心

现在我们使用 `ChartType.PIE` 实例化一个 `Chart` 对象。这会自动创建一个饼图占位符，随后可以填充数据。

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*解释*：`ChartType.PIE` 告诉 Aspose.Words 使用饼图模板。图表被添加到文档的主体中，因此会出现在您需要的位置。这一调用即可满足“how to add chart”的需求。

## 步骤 3：填充图表 – 用数据回答 “how to add chart”

没有系列数据的饼图是没有意义的。使用 `Series` 集合来添加类别和数值。

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*为什么重要*：每次调用 `add` 都会创建饼图的一块切片。第一个参数是标签，第二个参数是数值。您可以将其替换为来自数据库或 CSV 文件的动态数据。

### 可选：自定义外观（非必需但有用）

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

这些微调展示了如何在不离开 Java 代码的情况下，以专业外观 **how to create chart**。

## 步骤 4：**将 docx 保存为 PDF** – “convert word to pdf”的最后一步

图表嵌入后，将文档导出为 PDF。Aspose.Words 将图表渲染为矢量图形，保持质量。

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*关键点*：`save` 方法会自动将 Word 文件转换为 PDF，处理图表光栅化、字体嵌入和页面布局。这实现了 **save docx as pdf** 的目标，并展示了在存在图表时可靠的 **convert word to pdf** 方法。

### 预期输出

运行程序会生成包含以下内容的 `output.pdf`：

* `input.docx` 的原始内容（如果有）  
* 一个完整渲染的饼图，标题为 *Sales Distribution Q1*  
* 与数据匹配的准确切片百分比（40 %，30 %，30 %）

在任意 PDF 查看器中打开，您应能看到清晰的饼图，效果与 Word 文件中看到的一致。

## 常见陷阱及避免方法

| 问题 | 原因 | 解决方案 |
|------|------|----------|
| PDF 中图表显示为空白 | 缺少字体或图表渲染设置 | 确保使用最新的 Aspose.Words 版本；它已捆绑所需的渲染库。 |
| 数据值四舍五入不正确 | 使用了大整数值 | 提供 `double` 类型的值或在添加到系列之前对数字进行缩放。 |
| 输出的 PDF 文件过大 | 图像以高 DPI 嵌入 | 如果也嵌入图像，请设置 `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)`。 |
| “convert word to pdf” 抛出 `UnsupportedOperationException` | 使用了旧版 Java（< 11） | 升级到 Java 17 或更高版本，Aspose.Words 24.x 需要此版本。 |

## 专业技巧：复用图表创建逻辑

如果需要在同一文档中添加多个图表，请将图表构建代码提取到辅助方法中：

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

现在，您可以对每个数据集调用 `doc.getFirstSection().getBody().appendChild(createPieChart(...));`，保持代码 DRY（不要重复自己）。

## 结论

现在您已经了解如何在 Word 文档中 **创建饼图**、填充数据，并使用 Java **将 docx 保存为 PDF**。此端到端示例涵盖了完整的 **convert word to pdf** 工作流，回答了 **how to add chart**，并演示了以编程方式 **how to create chart**。

接下来您可以探索：

* 添加柱状图或折线图（`ChartType.BAR`、`ChartType.LINE`）– 另一个 **how to create chart** 场景。  
* 导出为其他格式，如 PNG 或 HTML（`SaveFormat.PNG`、`SaveFormat.HTML`）。  
* 在插入图表之前，使用表格或占位符动态生成输入文档。

欢迎尝试不同的数据集、样式选项，甚至在每页嵌入多个图表。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南紧密相关的主题，基于所示技术进行扩展。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [如何使用 Java 在 Word 文档中插入饼图](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [如何在 Java 中将 Word 保存为 PDF 并创建可访问的 PDF](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [如何使用 Java 和 Aspose.Words 在 Word 中创建图表](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}