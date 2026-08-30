---
category: general
date: 2026-07-29
description: 使用 Aspose.Words for Java 插入饼图，并学习如何生成环形图、格式化饼图、格式化 Word 图表以及自定义图表大小。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: zh
lastmod: 2026-07-29
og_description: 使用 Aspose.Words for Java 插入饼图，并快速学习生成环形图、格式化饼图、格式化 Word 图表以及自定义图表尺寸，以制作专业文档。
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: 在 Java 中插入饼图 – 完整的 Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: 使用 Aspose.Words 在 Java 中插入饼图 – 完整指南
url: /zh/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中使用 Aspose.Words 插入饼图 – 完整指南

是否曾想过如何 **在 Word 文档中插入饼图** 并通过 Java 代码实现？你并不是唯一遇到这个难题的开发者——很多人在需要快速、编程方式可视化数据时都会卡住。好消息是？使用 Aspose.Words for Java，你只需几行代码即可完成，而且还能 **生成环形图**、**格式化饼图**、**格式化 Word 中的图表**，以及 **自定义图表大小** 以匹配品牌风格。

在本教程中，我们将通过一个真实案例演示：创建空白文档、插入饼图、微调若干视觉属性，最后保存文件。完成后，你将拥有一段可直接粘贴到任何 Java 项目中的可复用代码片段，实现图表自动化。无需额外库，无需手动操作 Office 互操作——纯净的编译型 Java。

## 你需要准备的环境

- **Java 17**（或任意近期 JDK；API 向后兼容）
- **Aspose.Words for Java** 22.12 或更高版本——可通过 Maven 坐标或从 Aspose 官网下载 .jar。
- 一个轻量级 IDE（IntelliJ IDEA、Eclipse、VS Code…）——能够运行 `main` 方法即可。
- 可选：如果不想出现评估水印，请准备许可证文件。

只要准备好上述环境，即可直接进入代码实现。

## 第一步：使用 Aspose.Words 插入饼图

我们首先 **在新文档中插入饼图**。这一步为后续所有操作奠定基础，因为图表对象让我们能够访问系列、数据点以及各种视觉调整。

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **为什么重要：** `DocumentBuilder.insertChart` 不仅创建图表，还返回一个可供操作的 `Chart` 对象。宽度和高度参数让你在创建时就 **自定义图表大小**，无需后期再调整。

## 第二步：生成环形图（可选）

如果你的设计需要中间有空洞——比如经典的环形图——Aspose 只需一行代码即可实现。同一个 `Chart` 实例通过调整孔径大小即可从普通饼图切换为环形图。

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **小技巧：** 孔径大小仅在 `ChartType.DONUT` 时生效。如果保持类型为 `PIE`，该调用会被忽略，尽情尝试吧。

## 第三步：格式化饼图切片

良好的视觉效果常常会突出特定切片。这里我们 **格式化饼图**，将第一块切片向外弹出 20 点，吸引读者注意最重要的数据点。

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **专业提示：** 若有多个系列，可遍历 `pieChart.getSeries()` 并为每个系列单独设置颜色、边框或数据标签。这就是在 **Word 中格式化图表** 时实现丰富样式的方式。

## 第四步：向图表添加数据

没有数据的图表只是一种装饰。下面我们为其填充一组简单的数据——例如季度销售额。

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **这样做的原因：** 通过显式添加 `ChartPoint` 对象，确保图表准确反映业务逻辑。`setShowCategoryName` 与 `setShowValue` 的调用属于 **格式化饼图**，用于在切片上同时显示标签和数值。

## 第五步：微调外观（自定义图表大小与样式）

除了初始尺寸外，你可能还想调整图例、标题，甚至数据标签使用的字体。这些都属于 **自定义图表大小** 与整体格式化的范畴。

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **边缘情况：** 若后续将文档导出为 PDF，图表的矢量数据仍保持清晰，因为尺寸是以点（points）而非像素定义的。这对 **Word 中格式化图表** 以及后续格式转换都是优势。

## 第六步：保存并查看文档

最后一步只需调用 `doc.save`。这会生成一个 `.docx` 文件，可在 Microsoft Word、LibreOffice 或任何支持 OpenXML 的查看器中打开。

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **结果：** 打开 `PieChart.docx`，即可看到尺寸恰当的饼图（或环形图），带有弹出切片、标题和图例——全部在未触碰 UI 的情况下自动生成。

### 预期输出

| 元素 | 你将看到的内容 |
|------|----------------|
| 图表类型 | 饼图（若 `holeSize` > 0 则为环形图） |
| 切片弹出 | 第一块切片向外偏移 20 pt |
| 图例 | 位于右侧 |
| 标题 | “Quarterly Sales Distribution”，加粗 14 pt |
| 数据标签 | 每块切片显示类别名称和数值 |
| 文档 | 标准的 Word `.docx` 文件，可直接共享 |

## 常见问题与注意事项

- **需要许可证吗？**  
  评估版可用于测试，但会添加水印。将 `aspose.words.lic` 文件放入类路径即可获得无水印的输出。

- **可以在 Maven 中使用吗？**  
  当然可以。将以下依赖添加到 `pom.xml` 中：

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **如果有多个系列怎么办？**  
  遍历 `pieChart.getSeries()`，对每个系列分别调用 `setExplosion`、`setFillColor` 或其他格式化方法。这就是在 **格式化饼图** 时处理多维数据的方式。

- **生成的图表在 Word 中可编辑吗？**  
  可以——保存后打开文档，仍可手动调整颜色、字体，甚至将饼图转换为柱状图等。

## 小结

我们已经使用 Aspose.Words for Java **插入了饼图**，演示了 **生成环形图**、多种 **格式化饼图** 的方法，介绍了 **Word 中格式化图表** 的最佳实践，并学习了 **自定义图表大小** 以获得精致外观。上面的完整可运行示例可直接嵌入任意 Java 项目，实现无需 COM 互操作或 Office 安装的图表自动化。

接下来可以尝试：将数据源换成实时数据库、根据阈值设置条件颜色，或将同一文档导出为 PDF 以生成可打印报告。所有这些步骤都基于我们已经搭建的基础，转换过程会非常顺畅。

如果遇到问题或有进一步的改进想法——比如堆叠柱形图或折线图——欢迎在下方留言。祝图表创作愉快！

## 接下来你可以学习什么？

以下教程涵盖与本指南紧密相关的主题，帮助你在项目中进一步发挥 API 功能并探索其他实现思路。每篇资源均提供完整可运行的代码示例和逐步解释。

- [如何使用 Aspose.Words for Java 创建柱形图](/words/english/java/document-conversion-and-export/using-charts/)
- [在图表中格式化数据标签的数字](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [在图表坐标轴上设置数字格式](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}