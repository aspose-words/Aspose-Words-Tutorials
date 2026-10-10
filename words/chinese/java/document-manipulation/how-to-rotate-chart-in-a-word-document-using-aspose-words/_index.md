---
category: general
date: 2026-10-10
description: 学习如何在 Word 文件中旋转图表，并在 Word 中修改图表以更改环形图的大小，附带完整的 Java 示例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: zh
lastmod: 2026-10-10
og_description: 如何在 Word 文件中旋转图表，并使用 Aspose.Words for Java 修改 Word 中的图表以更改环形图大小。
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: 如何在 Word 文档中旋转图表——一步一步的 Java 指南
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: 如何使用 Aspose.Words 在 Word 文档中旋转图表
url: /zh/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文档中使用 Aspose.Words 旋转图表

如果您需要 **how to rotate chart**（在 Microsoft Word 文件中旋转图表），本指南将为您展示完整步骤。您还将学习如何 **modify chart in Word**（在 Word 中修改图表），以 **change doughnut chart size**（更改环形图大小）而无需离开 Java 代码。

Word 自动化常常感觉像是一系列不相关的 API 调用，但使用 Aspose.Words，您可以像处理其他文档节点一样处理图表。完成本教程后，您将拥有一个可运行的程序，能够加载已有的 `.docx`，将环形图旋转 45°，将环孔半径缩小至 50%，并将结果保存为新文件。

## 前置条件

开始之前，请确保您具备以下条件：

* 已安装 Java 17 或更高版本。
* 已安装 Maven（或 Gradle）用于管理依赖。
* 已有一个包含环形图的输入 Word 文档（`input.docx`）。
* 有效的 Aspose.Words for Java 许可证（或使用评估模式）。

## 第 1 步：设置 Maven 项目

创建一个新的 Maven 项目，或在现有的 `pom.xml` 中添加以下依赖：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

运行 `mvn clean install` 将下载库并将类添加到您的类路径中。

## 第 2 步：加载包含图表的 Word 文档

第一步是打开已有的文档。`Document` 类代表整个文件。

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

加载文件 **不会** 修改它；它仅在内存中创建一个可供查询和编辑的表示。

## 第 3 步：创建用于导航的 DocumentBuilder

`DocumentBuilder` 为您提供类似光标的 API，以遍历文档树。我们将使用它定位第一个图表形状。

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

构建器默认位于文档开头，但您可以在需要时将其移动到任意节点。

## 第 4 步：获取第一个图表形状

图表以 `Shape` 节点的形式存储。通过过滤 `NodeType.SHAPE` 类型的子节点，我们可以提取图表对象。

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

如果文档中包含多个图表，您可以遍历 `getChildNodes`，并在强制转换前检查每个 `Shape` 的 `hasChart()`。

## 第 5 步：旋转图表（how to rotate chart）

环形图本质上是带孔的饼图。旋转它会改变第一块切片的起始角度。

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

`setStartAngle` 方法接受表示角度的 double 值。正值顺时针旋转，负值逆时针旋转。

## 第 6 步：更改环形孔大小（change doughnut chart size）

孔的大小以图表半径的比例表示。`0.5` 表示孔占总半径的 50%。

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**提示：** 有效范围为 `0.0`（无孔，即普通饼图）到 `0.9`（极细环）。超出此范围的值会抛出 `IllegalArgumentException`。

## 第 7 步：保存修改后的文档

最后，将更改写回磁盘。

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

当您在 Microsoft Word 中打开 `DoughnutFormatted.docx` 时，会看到环形图已旋转 45°，且孔的大小已缩小至原来的一半。

## 完整、可运行的示例

将所有代码片段组合在一起，以下是您可以直接复制粘贴到 IDE 中的完整程序：

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### 预期输出

运行程序后会打印：

```
Chart rotated and doughnut size changed successfully.
```

打开 `DoughnutFormatted.docx` 可看到环形图的第一块切片起始于 45° 位置，且内部半径占外部半径的一半。

## 常见变体和边缘情况

| 情况 | 需要调整的内容 | 重要原因 |
|-----------|----------------|----------------|
| **多个图表** | 循环 `getChildNodes(NodeType.SHAPE, true)` 并对每个 `shape.hasChart()` 进行检查 | 确保修改的是目标图表，而不是第一个图表 |
| **柱形图或折线图** | `setStartAngle` 不适用；可使用 `chart.getSeries().get(0).setFillFormat(...)` 进行其他视觉调整 | 并非所有图表类型都支持旋转，只有环形/饼图拥有起始角度属性 |
| **没有环形孔的图表** | 跳过 `setDoughnutHoleSize`，或先通过 `chart.setChartType(ChartType.DONUT)` 将图表类型转换为环形图 | 在非环形图上修改孔大小会抛出异常 |
| **大型文档** | 使用 `DocumentBuilder.moveToDocumentStart()` 并 `builder.moveToNode(chartShape)` 进行定位导航 | 通过避免遍历无关节点提升性能 |

## 稳定操作图表的专业技巧

* **缓存图表引用** – 若需修改多个属性，建议将 `Chart` 对象保存到本地变量，而不是反复调用 `chartShape.getChart()`。
* **验证输入值** – 在调用 `setStartAngle` 或 `setDoughnutHoleSize` 前，先检查数值范围，以避免运行时错误。
* **使用许可证** – 评估模式会在首页添加水印。通过以下代码应用许可证可去除水印：`License license = new License(); license.setLicense("Aspose.Words.lic");`。

## 后续步骤

现在您已经掌握了 **how to rotate chart** 和 **change doughnut chart size**，可以进一步探索其他 **modify chart in Word** 场景：

* 使用 `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())` 更改切片颜色。
* 通过调用 `chart.getSeries().get(0).setHasDataLabel(true)` 添加数据标签。
* 使用 `chart.toImage(300, 300, ImageType.PNG)` 将图表导出为图片。

这些扩展均遵循相同模式：获取 `Chart` 对象，调用相应的 setter，最后保存文档。

---

**您已经掌握了使用 Java 在 Word 中旋转和调整环形图的技巧。** 欢迎将代码适配到其他图表类型，集成到更大的文档生成流水线，或与 Aspose.Slides 结合实现 PowerPoint 自动化。祝编码愉快！


## 接下来该学习什么？

以下教程涵盖与本指南紧密相关的主题，帮助您在已有技术基础上进一步深入。每篇资源均提供完整可运行的代码示例和逐步解释，助您掌握更多 API 功能并探索不同实现方式。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}