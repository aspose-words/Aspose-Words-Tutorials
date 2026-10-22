---
category: general
date: 2026-09-27
description: 在 Java 中创建径向图并将图表插入 Word。学习如何设置图表大小、添加数据系列以及生成空白 Word 文档。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: zh
lastmod: 2026-09-27
og_description: 在 Java 中创建径向图，然后将图表插入 Word。本指南展示了如何设置图表大小、添加数据系列以及创建空白 Word 文档。
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: 使用 Java 创建径向图并将其插入 Word
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: 使用 Java 创建径向图并将图表插入 Word
url: /zh/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Java 创建径向图表并插入到 Word 中

如果您需要在 Word 文件中 **使用 Java 创建径向图表**，本教程将一步步演示完整过程。您将了解如何 **将图表插入 Word**、设置图表尺寸，以及从头构建一个 **空白 Word 文档**。

我们将逐步讲解每个必需的步骤，从初始化文档到添加数据系列并保存最终的 `.docx`。完成后，您将拥有一个包含径向图表的完整 Word 文件，并掌握 **如何设置图表大小** 与 **添加数据系列图表** 的方法，以便后续自定义。

## 前置条件

* Java 17 或更高（代码可在任何现代 JDK 上编译）
* Aspose.Words for Java 24.9 或更新版本 – `setShowGraduations` 方法仅在该版本及以上可用
* 能够引入 Aspose.Words JAR 的 IDE 或构建工具（Maven/Gradle）
* 基本的 Java 语法和 Maven/Gradle 依赖管理知识

> **专业提示：** 如果您使用 Maven，请在 `pom.xml` 中添加以下内容：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## 第一步：创建空白 Word 文档

空白文档是放置图表的画布。`Document` 类代表整个 `.docx` 文件。

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

创建空白文档可确保没有已有内容干扰图表布局。

## 第二步：初始化 DocumentBuilder

`DocumentBuilder` 提供了便捷的方法，用于向文档中插入对象、文本和其他元素。

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

稍后将使用该构建器 **将图表插入 Word**。

## 第三步：构建径向图表

Aspose.Words 支持多种图表类型；`ChartType.RADIAL` 用于创建径向（极坐标）图表。

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

此时图表已存在，但尚未设置数据、尺寸或可视化选项。

## 第四步：向图表添加数据系列

没有数据系列的图表是空的。`add` 方法接受系列名称和数值数组。

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

您可以多次调用 `add` 来添加多个系列。这满足了 **添加数据系列图表** 的需求。

## 第五步：启用刻度线（可选）

刻度线是提升可读性的径向网格线，仅在 24.9 版本及以上可用。

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

如果使用的是旧版 Aspose.Words，此行会抛出异常——请先确认库的版本。

## 第六步：设置图表尺寸

控制图表大小可以让其在页面边距内恰当地显示。这对应 **如何设置图表大小** 的需求。

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

您可以根据布局需求调整宽度和高度的数值。记住 1 point ≈ 1/72 inch。

## 第七步：将图表插入 Word 文档

现在图表已准备就绪，`DocumentBuilder` 的 `insertChart` 方法负责实际插入。

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

这就是 **将图表插入 Word** 操作的核心。

## 第八步：保存文档

最后，将文档写入磁盘。生成的文件将包含您刚创建的径向图表。

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

运行程序后，会在项目工作目录生成 `RadialChart.docx`。在 Microsoft Word 中打开该文件，即可看到包含三个数据点且显示刻度线的径向图表。

### 预期输出

* 一个名为 `RadialChart.docx` 的 Word 文件
* 文件内部为单页，图表尺寸为 400 × 300 points
* 图表显示一个名为 **Series 1** 的系列，数值为 **10, 20, 30**
* 图表周围可见刻度线（径向网格线）

## 常见变体和边缘情况

| 情况 | 需要更改的内容 | 原因 |
|-----------|----------------|--------|
| **多个系列** | 对每个系列调用 `chart.getSeries().add(...)` | 实现对比数据可视化 |
| **不同的图表类型** | 将 `ChartType.RADIAL` 替换为 `ChartType.COLUMN`（或其他） | 使用最适合数据的图表类型 |
| **自定义颜色** | 通过 `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` 设置 | 提升视觉品牌一致性 |
| **旧版 Aspose.Words** | 删除 `setShowGraduations` 行或升级库 | 防止出现 `NoSuchMethodError` |
| **保存为其他格式** | 使用 `doc.save("RadialChart.pdf", SaveFormat.PDF)` | 生成 PDF 而非 DOCX |

## 完整可运行示例

下面是完整的、独立的 Java 程序。将其复制到名为 `RadialChartExample.java` 的文件中，添加 Aspose.Words 依赖后运行。

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## 结论

现在您已经掌握了如何以编程方式 **创建径向图表**、**添加数据系列图表**、控制 **如何设置图表大小**，以及 **将图表插入 Word**，并且从 **空白 Word 文档** 开始。示例使用的是 Aspose.Words for Java 24.9，但相同的概念同样适用于其他提供类似 API 的图表库。

### 后续步骤

* 探索其他图表类型（`ChartType.PIE`、`ChartType.LINE` 等）——这与次要关键词 **insert chart into word** 相关联。  
* 自定义坐标轴标签、图例和颜色，以符合品牌指南。  
* 从数据库查询或 CSV 文件动态生成图表。  
* 将生成的 `.docx` 转换为 PDF 以便分发（`doc.save("output.pdf", SaveFormat.PDF)`）。

欢迎尝试不同的尺寸、系列数据和样式选项，打造符合您需求的精确可视化。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南紧密相关的主题，帮助您在项目中进一步运用这些技术。每篇资源都提供完整的可运行代码示例和逐步解释，助您掌握更多 API 功能并探索替代实现方案。

- [使用 Aspose.Words for Java 创建柱状图](/words/english/java/document-conversion-and-export/using-charts/)
- [Java 创建 Word 文档 – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [在 Word 文档中插入面积图](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}