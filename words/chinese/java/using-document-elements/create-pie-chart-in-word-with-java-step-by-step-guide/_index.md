---
category: general
date: 2026-08-14
description: 使用 Aspose.Words 在 Word 中通过 Java 创建饼图。学习如何向图表添加系列数据并仅用几行代码旋转饼图切片。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: zh
lastmod: 2026-08-14
og_description: 使用 Aspose.Words 在 Word 中使用 Java 创建饼图。本教程展示了如何向图表添加系列数据并快速旋转饼图切片。
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: 使用 Java 在 Word 中创建饼图 – 完整编码指南
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: 使用 Java 在 Word 中创建饼图 – 步骤指南
url: /zh/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 Java 创建饼图 – 步骤指南

如果您需要以编程方式**在 Word 中创建饼图**，本指南将向您展示如何使用 Java 和 Aspose.Words 完成此操作。您将学习完整的工作流程，从插入图表到添加数据点以及旋转第一块切片。

直接在 `.docx` 文件中生成图表可以省去手动复制‑粘贴的步骤，并让您能够自动化报告、发票或仪表板。在此过程中，我们还将介绍**如何向图表添加系列数据**以及**如何旋转饼图切片**以获得更好的视觉强调。

## 在 Word 中创建饼图 – 概览

Aspose.Words for Java 提供了流式的 `DocumentBuilder` API，能够将图表对象插入到 Word 文档中。您选择的图表类型决定了默认布局，您还可以自定义系列、颜色、角度，甚至只需一次方法调用就切换为环形图（doughnut）形状。

### 为什么使用 Aspose.Words？

* **无需 Microsoft Office** – 该库可在任何服务器或 CI 环境中运行。  
* **完整的 .docx 保真度** – 生成的图表与手动在 Word 中创建的图表外观完全相同。  
* **单文件依赖** – 只需添加 JAR 包，即可开始使用。

## 如何向图表添加系列数据

没有数据的图表只是一个占位符。`Chart` 对象公开了 `Series` 集合；每个系列保存一组数值，这些数值映射到切片（饼图）或点（折线图）。添加数据非常直接：

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**代码功能说明：**  
* `chart.getSeries()` 返回一个 `List<ChartSeries>`。  
* `get(0)` 选取第一个系列，因为饼图在定义上只能包含一个系列。  
* `add(double)` 向系列中追加一个数据点。数值会自动转换为百分比，渲染时总和为 100 %。  

> **小贴士：** 如果您的数据源包含超过三个类别，请以相同方式继续添加数值。Aspose.Words 会自动创建额外的切片。

## 旋转饼图切片

有时您希望特定的切片从某个特定角度开始，以便最重要的部分面向观看者。`setFirstSliceAngle(double)` 方法会旋转整个图表，从而移动第一块切片的起始位置：

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

角度以顺时针方向、相对于垂直轴的度数来衡量。将其设为 `0`（默认值）时，第一块切片位于顶部。调整该值即可突出显示某块切片或符合设计规范。

> **常见问题：** *旋转会影响数据顺序吗？*  
> 不会。数据顺序保持不变，只有视觉上的起始位置会改变。

## 完整 Java 示例

下面是一段完整的、可直接运行的程序示例，演示如何创建包含饼图的 Word 文档、添加系列数据、旋转切片并保存文件。所有必需的 import 已列出，您可以将代码复制到任意 IDE 中使用。

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### 预期输出

* 在 `output` 文件夹中会生成一个名为 **PieChart.docx** 的文件。  
* 使用 Microsoft Word 打开该文件，可看到一个彩色饼图，包含三块切片（40 %，30 %，30 %）。  
* 图表顺时针旋转了 45°，因此第一块切片略微偏离垂直轴向右侧开始。

## 常见陷阱与最佳实践

| 问题 | 产生原因 | 解决方案 |
|-------|----------------|-----|
| **图表显示为空白** | 文档在图表完全渲染之前已被保存。 | 在完成所有图表修改后再调用 `doc.save()` **之后** 保存。 |
| **切片数值总和不等于 100 %** | 添加的原始数字未表示百分比，导致比例异常。 | 提供能够代表整体比例的数值，或让 Aspose.Words 自动计算百分比。 |
| **旋转无效** | 使用 `ChartType.DOUGHNUT` 且未设置 `holeSize`，可能会隐藏旋转效果。 | 保持图表类型为 `PIE`，或在设置角度后再调整 `holeSize`。 |
| **文件路径错误** | 相对路径在 Windows 与 Linux 上的解析方式不同。 | 使用 `Paths.get("output", "PieChart.docx").toString()` 或在生产代码中使用绝对路径。 |

### 生产环境使用技巧

* **复用 `DocumentBuilder`** – 通过多次调用 `insertChart`，可以在同一文档中插入多个图表。  
* **样式设置** – 使用 `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` 直接在图表上显示百分比。  
* **性能优化** – 若需要在多个位置使用相同图表，可先生成一次后通过 `chart.deepClone()` 进行克隆。

## 旋转饼图切片 – 高级场景

* **动态角度** – 根据数据计算角度（例如让最大切片从顶部开始）。  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **多系列** – 虽然饼图通常只有一个系列，Aspose.Words 仍允许添加更多系列以实现堆叠饼图。旋转仍仅作用于第一个系列。

## 结论

现在您已经掌握了使用 Java **在 Word 中创建饼图**、**向图表添加系列数据**以及**旋转饼图切片**以实现视觉强调的完整方法。完整示例展示了从文档初始化到保存最终 `.docx` 文件的全部工作流，帮助您将图表生成集成到任何自动化报告管道中。

### 接下来该做什么？

* 探索其他图表类型（`ChartType.BAR`、`ChartType.LINE`），扩展您的自动化工具箱。  
* 将图表生成与 **mail merge** 结合，为每位收件人生成个性化报告。  
* 深入了解 **Styling API**（`ChartFormat`、`DataLabel`、`ChartTitle`），实现企业品牌化的外观。

欢迎尝试不同的数据集、角度和图表样式。祝编码愉快！

## 您接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您在已有技巧的基础上进一步提升。每个资源都提供完整的可运行代码示例以及逐步解释，助您掌握更多 API 功能并在项目中探索替代实现方案。

- [如何使用 Aspose.Words for Java 创建柱形图](/words/english/java/document-conversion-and-export/using-charts/)
- [如何使用 DocumentBuilder 在 Aspose.Words for Java 中创建表单域并添加内容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [如何使用 Aspose.Words for Java 将 Word 转换为 PDF](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}