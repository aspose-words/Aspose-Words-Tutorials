---
category: general
date: 2026-09-24
description: 使用 Aspose.Words for Java 在 DOCX 中插入饼图。学习设置孔径大小、炸裂饼块、突出显示饼图切片，以及轻松创建 docx
  图表。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: zh
lastmod: 2026-09-24
og_description: 使用 Aspose.Words for Java 在 DOCX 中插入饼图。轻松设置孔径大小、炸裂饼块、突出显示饼图块，并在几分钟内创建
  DOCX 图表。
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: 在 Java 中插入饼图文字 – 分步教程
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: 在 Java 中插入饼图文字——完整指南
url: /zh/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中插入饼图文字 – 完整指南

如果您需要在 DOCX 文件中 **插入饼图文字**，本教程将向您展示如何使用 Aspose.Words for Java 完成此操作。您将看到从创建文档到自定义图表的完整工作流程，包括将切片炸开、将孔大小设置为零以及突出显示切片。

在 Word 文档中处理图表常常感觉与常规文本处理是两个独立的关注点，但 Aspose.Words 将两者统一。在下面的步骤中，您还将学习如何 **创建 docx 图表** 文件，这些文件可以在 Microsoft Word、Google Docs 或任何其他兼容 DOCX 的查看器中打开。

## 您将完成的工作

* **插入饼图文字** 到空白文档中  
* **设置孔大小** 以将图表变为完整饼图（无环形）  
* **炸开饼图切片** 以突出显示特定段  
* **突出显示饼图切片** 并使用自定义格式  
* **创建 docx 图表**，可共享或进一步编辑  

### 前置条件

* Java 17 或更高（代码也可在 Java 8 上编译）  
* Aspose.Words for Java 库（版本 23.9 或更高）  
* 能解析 Aspose.Words 依赖的 IDE 或构建工具（Maven/Gradle）  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## 使用 Aspose.Words 在 DOCX 中插入饼图文字的方法

第一步是创建一个新的空白文档并获取 `DocumentBuilder`。构建器让您直接访问文档的内容流，使得 **插入饼图文字** 变得非常简单。

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### 为什么这很重要
`Document` 代表整个 Word 文件，而 `DocumentBuilder` 是高级 API，允许您插入段落、表格和图表，而无需处理底层 XML。从空白文档开始可确保您添加的图表是唯一内容，这对于学习或生成基于模板的报告非常理想。

## 设置孔大小以创建完整饼图

默认情况下，当您请求饼图时，Aspose.Words 会创建环形图。要使图表成为真正的圆形，必须 **设置孔大小** 为 `0`。这会去除内部孔洞，呈现经典的饼图外观。

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### 实用技巧
如果以后决定切换为环形图，只需将 `holeSize` 值改为百分比（例如 `30`）。相同的 API 适用于两种图表类型。

## 炸开饼图切片以突出显示某段

炸开切片可以在视觉上突出显示它。**炸开饼图切片** 操作会将选定的切片向外移动一定比例的图表半径。

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### 为什么要炸开？
炸开的切片会将读者的视线引向最重要的数据点——非常适合仪表盘或执行摘要。数值 `20` 表示半径的 20%；您可以在 `0`（不炸开）和 `100`（完全分离）之间进行调整。

## 使用自定义格式突出显示饼图切片

除了炸开之外，您可能希望通过更改填充颜色或边框来 **突出显示饼图切片**。虽然演示代码侧重于炸开，但您可以按如下方式扩展：

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### 专家提示
更改特定切片的填充颜色需要访问 `DataPoint` 对象。如果有多个系列，请遍历 `series.getDataPoints()` 并有条件地应用样式。

## 保存并验证创建的 docx 图表

最后，您通过保存 `Document` 来 **创建 docx 图表**。生成的文件可在 Microsoft Word 中打开，以查看格式化的饼图。

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### 预期输出
打开 `PieChartFormatted.docx` 会显示一个饼图：

* 图表占据 400 × 300 pt 区域。  
* 孔大小为 `0`，因此图表为完整饼图。  
* 第一个切片被炸开 20 %，并被染成红色（如果您添加了可选的格式化）。  

现在您已经拥有一个可以分发、嵌入电子邮件或通过程序进一步编辑的 **创建 docx 图表**。

---

## 常见变体和边缘情况

| 场景 | 如何调整代码 |
|----------|----------------------|
| **Multiple series** | Loop over `pieChart.getChart().getSeries()` and set `Explosion` or `FillColor` per series. |
| **Dynamic data** | Populate the series with values from a database or CSV before calling `setExplosion`. |
| **Different chart size** | Change the width/height arguments in `insertChart(ChartType.PIE, width, height)`. |
| **Export to PDF** | After saving the DOCX, call `doc.save("output.pdf")` to produce a PDF version of the same chart. |
| **Localization** | Use `DocumentBuilder.insertChart` with a locale‑specific number format for labels. |

### 专业技巧
始终在 `insertChart` **之后** 调用 `setHoleSize(0)`。如果在插入之前设置，Aspose.Words 在创建图表后会恢复为默认的环形大小。

---

## 回顾

您现在已经了解如何使用 Java **插入饼图文字** 到 Word 文档，如何 **设置孔大小** 以实现完整饼图外观，如何 **炸开饼图切片** 以吸引注意，以及如何使用自定义颜色 **突出显示饼图切片**。完整示例还演示了如何 **创建 docx 图表** 文件，以便分发。

---

## 下一步

- 使用 `ChartType` 探索其他图表类型（`BAR`、`LINE`、`SCATTER`）。  
- 将图表生成与邮件合并相结合，以生成个性化报告。  
- 将生成的 DOCX 集成到按需返回文件的 Web 服务中。  

如果遇到问题，请确保您使用的是兼容的 Aspose.Words 版本，并且输出目录存在且可写。

祝编码愉快！

## 您接下来应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在自己的项目中探索替代实现方法。

- [如何使用 Aspose.Words for Java 创建柱状图](/words/english/java/document-conversion-and-export/using-charts/)
- [使用 Word Chart API](/words/english/net/programming-with-charts/)
- [在 Word 中使用 Aspose.Words for .NET 插入气泡图](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}