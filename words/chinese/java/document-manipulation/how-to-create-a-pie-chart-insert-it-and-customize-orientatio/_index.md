---
category: general
date: 2026-11-25
description: 学习如何在 Java 中创建饼图，将饼图插入 Word 文档，拆分饼图切片并更改图表方向，并提供清晰的代码示例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: zh
lastmod: 2026-11-25
og_description: 在 Java 中创建饼图，将饼图插入文档，突出显示饼块并通过逐步代码更改图表方向。
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: 在 Java 中创建饼图 – 插入、突出切片并旋转
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: 如何在 Java 中创建饼图、插入并自定义方向
url: /zh/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中创建饼图、插入并自定义方向

如果您需要在 Word 文档中 **创建饼图**，本指南将一步步展示具体操作。您将学习如何 **插入饼图**、为突出显示而 **炸开切片**，以及通过简单旋转 **更改图表方向**。

本教程涵盖了从设置 Aspose.Words for Java 库到生成最终 `.docx` 文件并显示旋转、炸开的饼图的全部步骤。无需外部文档，只需按照步骤执行并运行代码即可。

## 前置条件

在开始之前，请确保您拥有：

* 已安装 Java 17 或更高版本。
* 用于管理依赖的 Maven 或 Gradle。
* 有效的 Aspose.Words for Java 许可证（或使用免费评估模式）。

在 `pom.xml`（Maven）或 `build.gradle`（Gradle）中添加 Aspose.Words 依赖。以下为 Maven 示例：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **专业提示：** 请保持库版本为最新；截至撰写本文时的最新版本（24.10）已修复图表渲染相关的 bug。

## 第一步：创建饼图并插入文档

第一步是 **创建饼图** 对象并将其嵌入 Word 文件。下面的代码构建了一个简单文档，添加图表占位符，并插入大小为 400 × 300 像素的饼图。

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**为什么重要：** `builder.insertChart` 会创建一个图表占位符，Aspose.Words 在保存文档时会自动将其转换为 OOXML 图表。`ChartType.PIE` 参数指示库渲染饼图，满足 **插入饼图** 的需求。

## 第二步：炸开饼图切片以突出显示

炸开切片可以突出某个数据点。下面的代码将第一个切片（索引 0）炸开 10 个点：

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

您可以更改索引以定位其他切片，或调节炸开距离以获得更柔和的效果。炸开切片是 Aspose.Words 中实现 **炸开饼图切片** 的标准方式。

## 第三步：通过旋转更改图表方向

旋转图表可以提供全新的视觉视角。使用 `setRotationAngle` 将整个图表顺时针旋转（角度以度为单位）。

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

上述调用满足 **旋转饼图** 与 **更改图表方向** 的需求。接受的角度范围为 0 至 360 度。

## 完整可运行示例

将所有步骤整合后，下面是一个完整的、独立的程序示例，可创建饼图、炸开切片并旋转图表。您可以在 IDE 中运行，或使用 `java -cp <classpath> PieChartDemo` 从命令行执行。

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### 预期输出

* 工作目录中会生成名为 **CreatePieChartDemo.docx** 的文件。
* 在 Microsoft Word 中打开该文件，可看到 400 × 300 像素的饼图。
* 第一个切片（Q1）向外偏移 10 点，形成 **炸开饼图切片** 效果。
* 整个图表倾斜 45 度，演示了 **更改图表方向** 与 **旋转饼图**。

## 常见变体与边缘情况

| 情况 | 如何调整代码 |
|-----------|-----------------------|
| **不同的图表尺寸** | 在 `insertChart` 中将 `400, 300` 参数改为所需尺寸。 |
| **多系列数据** | 向 `chart.getSeries()` 添加更多 `ChartSeries` 对象。 |
| **炸开其他切片** | 使用 `setExplode(sliceIndex, distance)`，将 `sliceIndex` 设置为目标切片的索引。 |
| **不需要旋转** | 删除 `setRotationAngle` 调用或将角度设为 `0`。 |
| **导出为 PDF 而非 DOCX** | 构建文档后，调用 `doc.save("output.pdf")` 并指定 PDF 格式。 |

> **注意：** 使用负数的炸开距离会抛出 `IllegalArgumentException`。请始终提供非负值。

## 性能提示

如果在循环中生成大量图表，建议复用同一个 `DocumentBuilder`，并仅在每次迭代时调用 `insertChart`。这样可以降低内存开销并提升处理速度。

## 结论

现在，您已经掌握了使用 Aspose.Words for Java **创建饼图**、**插入饼图**、**炸开饼图切片** 与 **旋转饼图** 的完整流程。完整示例展示了从初始化文档到保存可视化旋转、炸开的饼图文件的全部步骤。

接下来，您可以进一步探索 **更改图表方向** 的 3D 效果，或尝试其他图表类型，如 **Bar** 或 **Line**。相同的 API 模式适用于这些场景，扩展本教程非常简便。

欢迎根据自己的报告需求修改数据、切片索引或旋转角度，并将成果分享给社区！

## 接下来该学习什么？

以下教程涵盖了与本指南密切相关的主题，帮助您在项目中进一步运用这些技术。每篇资源均提供完整可运行的代码示例和逐步解释，助您掌握更多 API 功能并探索替代实现方案。

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}