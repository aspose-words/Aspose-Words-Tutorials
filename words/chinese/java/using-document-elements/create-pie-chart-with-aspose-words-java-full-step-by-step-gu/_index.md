---
category: general
date: 2026-07-16
description: 使用 Aspose.Words 在 Java 中创建饼图。学习如何添加引线、显示图例以及在单个教程中实现扇区突出显示。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: zh
lastmod: 2026-07-16
og_description: 使用 Aspose.Words 在 Java 中创建饼图。本指南展示了如何添加引线、显示图例以及突出切片，让您在几分钟内获得精美的可视化效果。
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: 使用 Aspose.Words Java 创建饼图 – 完整格式化教程
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: 使用 Aspose.Words Java 创建饼图 – 完整分步指南
url: /zh/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words Java 创建饼图 – 完整分步指南

是否曾想过在 Java 中以编程方式 **创建饼图**，而不必与底层绘图 API 纠缠？你并非唯一有此需求的开发者。许多开发者需要快速的报告、仪表盘或自动化文档可视化，于是他们选择 Aspose.Words，因为它承担了繁重的工作。  

在本教程中，我们将演示一个完整、可直接运行的示例，不仅 **创建饼图**，还展示如何 **添加引导线**、**显示图例**，甚至 **炸开切片** 以突出重点。完成后，你将得到一个 `.docx` 文件，外观足以让客户印象深刻。

> **快速收获：** 以下代码片段可直接在 Aspose.Words for Java 23.9（或更高版本）上运行。无需额外依赖，仅需 JAR 包。

## 您将学习的内容

- 使用 `DocumentBuilder` 设置一个空白 Word 文档。
- 插入自定义尺寸的 **饼图**。
- 使用 **explode slice** 功能突出显示数据点。
- 启用 **leader lines**，使被炸开的切片仍与标签相连。
- 打开 **chart legend**，让读者能够立即识别每个切片。
- 将结果保存为 `.docx` 文件，可在 Microsoft Word 或 LibreOffice 中打开。

**先决条件** – 你需要：

1. 已安装 Java 17（或更高版本）。
2. 在类路径中加入 Aspose.Words for Java JAR。
3. 一个基本的 IDE 或文本编辑器——IntelliJ IDEA、Eclipse、VS Code，或你喜欢的任何工具。

现在，让我们开始吧。

## 第一步：初始化 Document 和 Builder – 为 **创建饼图** 做准备

首先，我们需要一个干净的文档画布。`Document` 表示整个 Word 文件，而 `DocumentBuilder` 是帮助我们添加内容的工具。

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **为什么重要：** 从一个全新的 `Document` 开始，可确保没有隐藏的样式或残留对象干扰图表渲染。

## 第二步：插入 **饼图** – 大小很重要

Aspose.Words 让图表插入只需一行代码。这里我们请求一个 400 × 300 点的饼图——在普通屏幕上约为 5.5 × 4.2 英寸。

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **专业提示：** 如需不同尺寸，只需更改这两个数值参数。API 使用点作为单位，72 点 = 1 英寸。

## 第三步：**如何炸开切片** – 突出关键数据点

炸开切片会将其从饼图其余部分拉出，吸引读者视线。`setExplosion` 方法接受一个表示距离（点数）的整数。

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **如果有多个系列怎么办？** 你可以在任意系列索引上调用 `setExplosion`（`get(1)`、`get(2)` …）来炸开不同的切片。

## 第四步：**添加引导线** 并 **显示图例** – 连接各要素

当切片被炸开时，标签可能会漂离。引导线保持标签与切片相连，保证可读性。同时，图例为所有切片提供快速键。

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **为什么要启用引导线？** 没有引导线，标签可能会漂浮，导致用户不清楚它属于哪个切片。  
> **需要自定义图例位置？** 使用 `chart.getLegend().setPosition(LegendPosition.TOP)` 或其他枚举值。

## 第五步：保存文档 – 最终的 **创建饼图** 步骤

最后，我们将文档持久化到磁盘。请将路径调整为你有写入权限的文件夹。

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

运行程序，打开生成的 `PieChartDemo.docx`，你应该会看到一个格式良好的饼图，第一块切片已炸开，带有引导线和可见的图例。

![Pie chart example showing exploded slice and legend](pie-chart-example.png){: .center-image alt="创建饼图示例，展示炸开的切片、引导线和图例"}

### 预期输出

打开 Word 文件后，图表大致如下：

- 一个 400 × 300 pt 的饼图。
- 第一块切片偏移了 10 pt。
- 一条细的引导线将炸开的切片连接到其标签。
- 图表下方的图例列出每个系列的名称。

如果没有看到引导线，请再次确认 `setLeaderLines(true)` 已在炸开设置 *之后* 调用——顺序很重要。

## 常见问题及避免方法

| 问题 | 出现原因 | 解决办法 |
|------|----------|----------|
| **未出现图例** | `setShowLegend(true)` 被遗漏或在错误的图表对象上调用。 | 确保在从形状获取 `Chart` 后 **调用** `chart.setShowLegend(true)`。 |
| **缺少引导线** | 切片未炸开，或图表类型不支持引导线。 | 仅 `ChartType.PIE`（或 `PIE_3D`）支持引导线。先调用 `setExplosion`，再调用 `setLeaderLines(true)`。 |
| **切片未移动** | 炸开值太低（0‑2 pt）。 | 增大整数值，例如 `setExplosion(10)` 或更高，以获得更明显的效果。 |
| **图表变形** | 使用非正方形尺寸（宽度 ≠ 高度）会压扁饼图。 | 保持宽高相等或接近；400 × 300 可用，但 400 × 400 能得到完美圆形。 |

## 高级调整（可选）

如果想超越基础功能，可考虑：

- **自定义颜色**：`chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **数据标签**：`chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **3D 效果**：将 `ChartType.PIE` 替换为 `ChartType.PIE_3D`。

这些选项让你能够微调视觉效果，以符合企业品牌指南。

## 回顾 – 我们实现了什么

我们从一个空白 Word 文档开始，**创建了饼图**，**炸开了第一块切片**，**添加了引导线**，并 **显示了图例**。整个流程浓缩在一个简洁的 `main` 方法中，便于嵌入更大的报告流水线。

## 下一步

- **添加更多系列**：从数据库或 CSV 中填充真实数据到图表。
- **导出为 PDF**：使用 `doc.save("output.pdf", SaveFormat.PDF);` 生成 PDF 版本。
- **与其他形状组合**：插入表格、图片或额外图表，完成完整报告。

如果你对其他图表类型——柱状图、条形图、折线图——感兴趣，只需将 `ChartType.PIE` 替换为相应的枚举，并遵循相同的格式化步骤。

---

*祝图表绘制愉快！* 如有任何未如预期工作的地方，欢迎留言或分享你自定义图例位置的经验。你的反馈帮助大家一起构建更好的自动化文档。

## 接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助你进一步掌握 API 功能并在项目中探索替代实现方式。每个资源都提供完整可运行的代码示例和逐步解释。

- [如何使用 Aspose.Words for Java 创建柱状图](/words/english/java/document-conversion-and-export/using-charts/)
- [如何使用 Aspose.Words for Java 创建 PDF 文档 | Document Processing API](/words/english/java/)
- [如何使用 Aspose.Words for Java 为文档添加水印](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}