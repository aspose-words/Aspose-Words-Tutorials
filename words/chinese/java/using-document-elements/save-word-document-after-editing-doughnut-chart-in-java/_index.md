---
category: general
date: 2026-09-11
description: 使用 Aspose.Words for Java 编辑环形图后保存 Word 文档。了解如何更改环形图孔径大小、旋转环形图以及编辑环形图属性。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: zh
lastmod: 2026-09-11
og_description: 使用 Aspose.Words for Java 编辑环形图后保存 Word 文档。本教程展示如何更改环形孔大小、旋转环形图以及自定义图表外观。
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: 编辑环形图后保存 Word 文档 – Java 指南
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: 在 Java 中编辑环形图后保存 Word 文档
url: /zh/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中编辑环形图后保存 Word 文档

如果您需要 **保存 Word 文档**，且文档中包含自定义的环形图，本指南将手把手教您如何实现。只需几行 Java 代码，即可修改环形孔大小、旋转环形图，然后将结果写回磁盘。

您将看到一个完整、可运行的示例，使用 Aspose.Words for Java，并提供处理多个图表、验证节点类型以及避免常见陷阱的技巧。无需外部引用——所有必需内容已包含。

## 前置条件

开始之前，请确保您已具备：

- 已安装 Java 17 或更高版本
- 用于管理依赖的 Maven 或 Gradle
- 已在项目中添加 Aspose.Words for Java（版本 23.9 或更高）  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- 一个包含单个环形图的 Word 文件（`input.docx`）

## 步骤 1：加载 Word 文档

第一步是打开源文件。此步骤至关重要，因为后续所有操作都基于内存中的 `Document` 对象。

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **为什么？** 加载文档会创建一个 DOM 表示，便于遍历形状、表格和图表。如果文件无法打开，Aspose.Words 会抛出异常，您即可立即知道路径错误。

## 步骤 2：定位环形图形状

图表存放在 `Shape` 节点中。我们检索第一个包含图表的形状，并将其渲染器强制转换为 `Chart`。

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **为什么？** 检查 `isChart()` 可防止在文档中图表前出现图片或其他形状时触发 `ClassCastException`。这使代码在混合内容的文档中更具鲁棒性。

## 步骤 3：更改环形孔大小  

现在编辑环形孔。`setHoleSize` 方法接受图表半径的百分比（10 – 90）。

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **为什么？** 调整环形孔（即 **change doughnut hole** / **change chart hole size**）可以突出或弱化中心区域。API 会忽略 10‑90 % 之外的值。

## 步骤 4：旋转环形图  

要控制第一块起始位置，设置第一块角度。这实际上 **rotate doughnut chart**。

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **为什么？** 旋转图表在您希望特定切片位于顶部或符合设计规范时非常有用。

## 步骤 5：保存更新后的文档  

最后，将更改写入新文件。这就是 **save Word document** 并带有编辑后图表的时刻。

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **预期结果：** `output.docx` 包含原始内容，但环形图的孔大小为 30 %，且第一块从 45 ° 开始。使用 Microsoft Word 打开文件即可看到已转换的图表。

## 完整工作示例

下面是完整程序，您可以直接复制粘贴到 IDE 中。它包含所有导入和错误处理，能够安全地 **edit doughnut chart** 并 **save Word document**。

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### 预期输出

打开 `output.docx` 时：

- 环形图的中心孔大约占图表半径的三分之一。  
- 第一块从 45 度位置开始，整个图表顺时针移动。  

这两项视觉变化会立即在 Word 中呈现。

## 常见变体和边缘情况

| 情况 | 处理方式 |
|-----------|----------------|
| **多个图表** | 遍历 `doc.getChildNodes(NodeType.SHAPE, true)` 并过滤 `shape.isChart()`；对每个 `Chart` 调用 `setHoleSize` / `setFirstSliceAngle`。 |
| **图表不是环形图** | 检查 `chart.getType()`；仅当 `chart.getType() == ChartType.DOUGHNUT` 时才调用 `setHoleSize`。 |
| **需要动态更改孔大小** | 根据数据值计算所需百分比，然后调用 `setHoleSize(computedValue)`。 |
| **保存到流** | 使用 …（此处省略具体实现） |

## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。每个资源均提供完整的可运行代码示例和逐步解释。

- [如何使用 Aspose.Words for Java 创建柱形图](/words/english/java/document-conversion-and-export/using-charts/)
- [如何使用 Aspose.Words for Java 将文档保存为 PDF](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [使用 Aspose.Words for Java 为 Word 文档设置密码](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}