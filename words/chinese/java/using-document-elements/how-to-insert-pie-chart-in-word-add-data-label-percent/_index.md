---
category: general
date: 2026-07-20
description: 如何使用 Aspose.Words 在 Word 中插入饼图。学习添加数据标签百分比并在图表上显示百分比，以制作专业文档。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: zh
lastmod: 2026-07-20
og_description: 如何使用 Aspose.Words 在 Word 中插入饼图。本指南展示了如何在几行代码内添加数据标签百分比并在图表上显示百分比。
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: 如何在 Word 中插入饼图 – 快速指南
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: 如何在 Word 中插入饼图 – 添加数据标签百分比
url: /zh/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中插入饼图 – 添加数据标签百分比

Ever wondered **how to insert pie chart** into a Word document without wrestling with the UI? You’re not alone. In many reporting scenarios you need to *add pie chart to Word* and, more importantly, **show percent on pie chart** so readers instantly grasp the data distribution.

在本教程中，我们将使用 Aspose.Words for Java 逐步演示完整过程。完成后，你将准确了解如何 **add data label percent**、**display percentages on chart**，并获得一个一次就正确的精美饼图。无需额外插件，无需手动调整——只需干净的代码即可直接嵌入任何项目。

---

## 前提条件

- Java 17（或更高）– Aspose.Words 支持的当前 LTS 版本。
- Aspose.Words for Java 24.x（撰写时的最新版本，2026 年 7 月）。
- 基本的 Maven 或 Gradle 设置以获取库。
- 你喜欢的 IDE（IntelliJ IDEA、Eclipse、VS Code……任意一种均可）。

如果你已经具备这些，太好了——让我们开始吧。

---

## 步骤 1：设置项目并导入库

首先，将 Aspose.Words 依赖添加到你的 `pom.xml`（Maven）或 `build.gradle`（Gradle）中。这将使你能够访问 `Document`、`DocumentBuilder` 和图表类。

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** 保持版本号为最新；较新的发布通常会添加图表相关的修复，使 **display percentages on chart** 更加可靠。

---

## 步骤 2：创建新的 Word 文档并获取 builder

builder 是你插入内容的瑞士军刀。在这里我们创建一个全新的文档并将 `DocumentBuilder` 附加到它上。

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

为什么需要 builder？它抽象了底层的 OpenXML 结构，让我们专注于 *what*（我们想要的东西）——比如 **add pie chart to word**——而不是 *how*（XML 的具体形式）。

---

## 步骤 3：插入饼图

现在进入 **how to insert pie chart** 的核心。我们让 builder 插入一个特定尺寸的饼图。尺寸单位为点（1 pt ≈ 1/72 英寸）。

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

此时图表为空，但占位符已经在文档中。你已经通过代码 **add pie chart to word**。

---

## 步骤 4：为图表填充数据

饼图至少需要一组数值。我们来提供一些代表市场份额的示例数据。

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

如果需要多个系列（堆叠饼图、环形图等），可以调用 `pieChart.getSeries().add()` 并重复上述步骤。当你想要为每个切片 **display percentages on chart** 时，同样的逻辑适用。

---

## 步骤 5：**add data label percent** – 在切片上显示百分比

这是大多数开发者容易忽略的部分：配置数据标签以显示百分比。如果不这样做，图表只会显示原始数字，可能会产生歧义。

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

`setShowPercent(true)` 调用告诉 Aspose.Words 将标签渲染为 “30 %”、 “45 %” 等。这正是你在 **show percent on pie chart** 时无需额外格式化的方式。

---

## 步骤 6：保存文档

最后，将文档写入磁盘。你可以选择 `.docx`、`.pdf`，甚至 `.html`。本指南中我们使用现代的 `.docx` 格式。

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

运行程序，打开 `PieChartDemo.docx`，你将看到每个切片上都有百分比标签的精美饼图。

---

## 预期输出

下面是生成的 Word 文件的截图。请注意每个切片都以百分比显示其份额——这正是我们在设置 **add data label percent** 时想要的效果。

![包含 pie chart 百分比标签的 Word 文档截图](/images/pie-chart-percent.png){.center width=600px alt="展示如何在 Word 中插入带百分比标签的 pie chart 的截图"}

*alt 文本包含主要关键词，兼顾 SEO 与可访问性。*

---

## 常见问题与边缘情况处理

| Question | Answer |
|----------|--------|
| **我可以更改百分比标签的字体吗？** | 可以。启用 `setShowPercent(true)` 后，获取 `DataLabel` 对象并调整其 `Font` 属性（`dataLabel.getFont().setSize(10);`）。 |
| **如果我需要环形图而不是饼图怎么办？** | 在 `insertChart` 调用中将 `ChartType.PIE` 替换为 `ChartType.DOUGHNUT`。相同的 **add data label percent** 逻辑仍然适用。 |
| **旧版 Word（2007‑2010）能正确显示百分比吗？** | Aspose.Words 以版本无关的方式写入底层 XML，因此在任何支持图表的 Word（2007 及以上）中，百分比都会正确显示。 |
| **如何为图表添加标题？** | 在保存之前使用 `pieChart.getTitle().setText("Market Share");`。 |
| **我可以将图表插入到特定段落或表格单元格吗？** | 完全可以。在调用 `insertChart` 之前，将 `DocumentBuilder` 移动到目标位置（`builder.moveToParagraph(index, true);` 或 `builder.moveToCell(table, row, column, true);`）。 |

---

## 实战技巧与窍门

- **Pro tip:** 如果计划在循环中生成大量图表，请复用同一个 `DocumentBuilder` 实例；这可以减少内存消耗。
- **Watch out for:** 非常小的切片（< 2 %）。Aspose.Words 可能会省略标签以避免杂乱；你可以使用 `dataLabel.setShowLabel(true);` 强制显示。
- **Performance note:** 图表渲染耗费 CPU。进行批量报告生成时，可考虑多线程，但要确保每个线程使用各自的 `Document` 实例。
- **Version check:** `setShowPercent` 方法在 Aspose.Words 22.8 中引入。如果使用的版本较旧，请升级或手动计算百分比并将其设为自定义标签。

---

## 小结

我们已经介绍了使用 Aspose.Words 在 Word 文档中 **how to insert pie chart** 的方法，展示了如何 **add data label percent**，并演示了最简便的 **display percentages on chart** 方式。只需几行 Java 代码，你就可以 **add pie chart to word** 并 **show percent on pie chart**，将原始数字转化为一目了然的可视化。

---

## 接下来做什么？

- 尝试其他图表类型（`BAR`、`LINE`、`AREA`），观察相同的 **add data label percent** 逻辑如何适用。
- 将图表与表格结合，生成更丰富的报告——Aspose.Words 能轻松将图表放置在数据表旁边。
- 尝试将同一文档导出为 PDF 或 HTML，查看百分比在不同格式中的渲染效果。

随意调整尺寸、颜色或数据源（例如数据库查询），让你的 Word 报告栩栩如生。如果遇到问题，欢迎在下方留言——祝你绘图愉快！

## 接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，构建在本教程演示的技巧之上。每篇资源都提供完整的可运行代码示例和逐步说明，帮助你掌握更多 API 功能并在项目中探索替代实现方案。

- [在 Word 中使用 Aspose.Words for .NET 插入柱形图](/words/english/net/working-with-charts/insert-column-chart/)
- [在 Word 文档中插入面积图 | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [在 Word 中使用 Aspose.Words for .NET 插入气泡图](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}