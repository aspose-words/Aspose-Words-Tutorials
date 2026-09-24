---
category: general
date: 2026-09-24
description: 学习如何使用 Java 在 Word 中创建图表，插入径向图表，并使用 Aspose.Words 将文档保存为 docx。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: zh
lastmod: 2026-09-24
og_description: 使用 Java 和 Aspose.Words 在 Word 中创建图表。本教程展示如何添加径向图表、定制数据并将文档保存为 docx。
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: 使用 Java 在 Word 中创建图表 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: 如何使用 Java 和 Aspose.Words 在 Word 中创建图表
url: /zh/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Java 和 Aspose.Words 在 Word 中创建图表

如果您需要从 Java 应用程序 **在 Word 中创建图表**，本指南将带您完整了解整个过程。您将看到如何添加径向图表，可选地填充其系列，最后使用 Aspose.Words for Java 库 **将文档保存为 docx**。

在 Word 文件中生成可视化数据是报告、开票或自动文档生成的常见需求。完成本教程后，您将能够创建 **create word document java** 项目，**add chart to Word** 文件而无需任何手动编辑。

## 前置条件

在开始之前，请确保您拥有：

* Java Development Kit (JDK) 8 或更高版本。
* 用于依赖管理的 Maven 或 Gradle。
* 如 IntelliJ IDEA、Eclipse 或 VS Code 等 IDE。
* 有效的 Aspose.Words for Java 许可证（免费试用可用于开发）。

这些工具为后续代码示例提供了基础。

## 第 1 步：设置 Maven 项目

创建一个新的 Maven 项目（或更新已有项目），并在 `pom.xml` 中添加 Aspose.Words 依赖：

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

运行 `mvn clean install` 将下载库，并使 `Document`、`DocumentBuilder`、`ChartType` 等类可在类路径中使用。

> **专业提示：** 保持库版本为最新。新版本会添加图表类型并提升渲染性能。

## 第 2 步：创建新的 Word 文档

**在 Word 中创建图表**的第一步是实例化一个空的 `Document`。该对象代表整个 `.docx` 包。

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` 的工作方式类似光标；它知道当前的插入点，并提供用于文本、表格和图表的方法。此时您已经 **created word document java** 风格——一个干净的画布，准备填充内容。

## 第 3 步：插入径向图表

Aspose.Words 支持多种图表类型。要 **insert radial chart**，请使用 `ChartType.RADIAL` 调用 `insertChart`。该方法还需要以点为单位的宽度和高度（1 点 ≈ 1/72 英寸）。

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

返回的 `Shape` 对象包含底层的图表对象。图表会自动为 24.9° 布局渲染刻度，这是 Word 中径向图表的默认设置。

### 为什么使用径向图表？

径向图表将数据环绕圆形展示，非常适合显示周期性模式（例如月度销售、时钟面度量）。相同的 API 也可以插入柱形图、饼图或折线图，但径向类型在无需额外样式代码的情况下提供了独特的外观。

## 第 4 步：（可选）填充图表系列数据

如果希望图表显示真实数值，需要添加系列和数据点。下面的代码片段添加了一个包含三个数据点的单一系列：

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

您可以根据需要重复 `add` 调用以添加更多点。Aspose.Words 会自动更新可视化表示，您会看到径向切片随新数值而调整。

> **常见问题：** *如果需要从数据库绑定数据怎么办？*  
> 检索行数据，在循环中调用 `series.getDataPoints().add(value, label)`。该 API 线程安全，适用于您提供的任何 `ResultSet`。

## 第 5 步：将文档保存为 DOCX

图表准备好后，最后一步是 **save document as docx**。`save` 方法会根据文件扩展名确定输出格式。

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

生成的文件包含一个完整可用的径向图表，可在 Microsoft Word、LibreOffice 或任何支持 DOCX 格式的查看器中打开。由于使用了 `.docx` 扩展名，Word 会以 Open XML 格式保存文件，这已成为 Word 文档的现代标准。

### 验证结果

在 Word 中打开 `RadialChartDemo.docx`：

1. 您应该看到一个页面，页面中心有一个径向图表。
2. 如果您添加了系列数据，图表会显示四个标记为 Q1‑Q4 的切片。
3. 右键单击图表 → **Edit Data** 以确认底层数据表。

如果图表显示为空白，请再次确认在添加系列之前已调用 `chart.getChart()`，并确保文档构建器的光标位于您希望插入图表的位置。

## 第 6 步：使用图表的高级技巧

| 提示 | 为什么重要 |
|-----|------------|
| **设置图表样式** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | 在不手动格式化每个元素的情况下提升视觉一致性。 |
| **插入后调整大小** – `chart.setWidth(500); chart.setHeight(350);` | 根据页面布局微调图表尺寸。 |
| **添加标题** – `chart.getChart().getTitle().setText("Revenue Overview");` | 为仅查看文档而未阅读上下文的读者提供说明。 |
| **导出为 PDF** – `doc.save("RadialChartDemo.pdf");` | 当需要不可编辑的分发版本时非常有用。 |
| **许可证处理** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | 防止生产构建中出现评估水印。 |

这些增强功能是可选的，但展示了在学习了 **add chart to Word** 之后，如何进一步自定义图表。

## 结论

您现在拥有一个完整的、独立的示例，展示了如何使用 Java **在 Word 中创建图表**、**插入径向图表**、可选地填充数据，并 **将文档保存为 docx**。相同的模式同样适用于其他图表类型，您可以根据需要将本教程扩展到柱形图、折线图或饼图。

接下来您可以探索：

* **create word document java** 项目，结合表格、图像和多个图表。
* 将 **save document as docx** 与 **save document as pdf** 结合使用，实现多格式报告。
* 将来自 REST API 或数据库的动态数据添加到图表中。

随意尝试样式选项、图表尺寸和数据源。祝编码愉快！

## 接下来该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，构建在本教程演示的技巧之上。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能，并在自己的项目中探索替代实现方案。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}