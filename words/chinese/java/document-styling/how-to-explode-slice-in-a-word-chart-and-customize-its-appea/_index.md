---
category: general
date: 2026-10-04
description: 通过一步步的 Java 示例，学习如何在 Word 图表中突出显示切片、在饼图中突出显示切片以及更改环形图的大小。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: zh
lastmod: 2026-10-04
og_description: 如何在 Word 图表中突出切片并使用 Java 自定义饼图或环形图。请参考完整示例以在 Word 中修改图表。
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: 如何在 Word 图表中分离切片 – 完整 Java 指南
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: 如何在 Word 图表中将切片分离并自定义其外观
url: /zh/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 图表中炸开切片并自定义外观

如果您需要在 Word 图表中 **how to explode slice**，本指南将为您提供完整步骤。无论是准备销售演示还是财务报告，炸开饼图切片或调整环形图孔径都能让最重要的数据脱颖而出。在接下来的章节中，您还将学习如何 **modify chart in Word**、**explode pie chart slice**、**change doughnut chart size**，以及使用 Aspose.Words for Java **customize pie chart word** 文档。

完成本教程后，您将获得一个完整的、可直接运行的 Java 程序，该程序加载 `.docx` 文件，炸开饼图的第一块切片，修改环形图孔径大小，并保存结果。无需外部脚本或手动编辑。

## 前置条件

- 在开发机器上安装 Java 17 或更高版本。  
- 安装 Maven 3.6+（或 Gradle）以管理依赖。  
- Aspose.Words for Java 库（免费试用版可用于开发）。  
- 包含至少一个图表（饼图或环形图）的 Word 文档（`input.docx`）。

## 步骤 1：将 Aspose.Words 添加到项目中

如果使用 Maven，请在 `pom.xml` 中添加以下依赖：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

对于 Gradle，请将以下内容放入 `build.gradle`：

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **专业提示：** 请保持库版本为最新；新版本会增加对更多图表类型的支持并提升性能。

## 步骤 2：加载包含图表的 Word 文档

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**为什么重要：** 加载文档会在内存中创建一个表示，Aspose.Words 可以遍历该表示。没有此对象，您将无法访问图表节点。

## 步骤 3：检索文档中的第一个图表

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **说明：** `NodeType.SHAPE` 包含所有绘图对象，包括图表。`true` 参数指示 Aspose 递归搜索，确保即使图表嵌套在表格中也能找到第一个图表。

## 步骤 4：炸开饼图的第一块切片

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**工作原理：** `setExplosion` 方法接受一个数值，用于决定切片离中心的距离。`20` 的值在视觉上足够明显且不会破坏图表布局。

## 步骤 5：调整环形图的孔径大小

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**为何有帮助：** 当数据点较多时，较大的环形孔径可以提升可读性。`setDoughnutHoleSize` 方法接受百分比（0‑100）。

## 步骤 6：保存修改后的文档

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### 预期输出

- 第一个饼图的第一块切片向外偏移，突出显示。  
- 若图表为环形图，中心孔径扩大至图表半径的 40 %。  
- 生成的文件 `PieChart.docx` 可在 Microsoft Word、LibreOffice 或任何兼容的查看器中打开，展示您通过代码实现的视觉更改。

## 完整可运行示例

下面是一整段程序代码。将其复制到 `ChartExploder.java`，根据需要调整文件路径，然后使用 `mvn compile exec:java`（或 IDE 的运行配置）执行。

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

运行此代码将 **modify chart in Word**、**explode pie chart slice**，并 **change doughnut chart size** 自动完成。

## 常见问题与边缘情况

| 问题 | 答案 |
|----------|--------|
| *如果文档包含多个图表怎么办？* | 示例代码定位 **第一个** 图表 (`NodeType.SHAPE, 0`)。若需操作其他图表，可更改索引或遍历 `doc.getChildNodes(NodeType.SHAPE, true)` 并通过 `shape.getChart() != null` 进行过滤。 |
| *能炸开除第一块之外的切片吗？* | 可以。通过 `chart.getSeries().get(seriesIndex)` 获取目标系列，然后调用 `setExplosion(value)`。索引从零开始。 |
| *此方法适用于 Word 2007‑2021 文件吗？* | Aspose.Words 支持 `.doc`, `.docx`, `.dot`, `.dotx`。相同代码跨版本均可运行，因为库对文件格式进行了抽象。 |
| *如果图表是柱形图或折线图会怎样？* | `setExplosion` 和 `setDoughnutHoleSize` 仅适用于饼图类图表。当图表类型不同，代码会安全跳过这些操作。 |
| *使用 Aspose.Words 是否需要许可证？* | 免费评估许可证可去除 30 天限制，但会添加水印。生产环境请购买许可证以去除水印并解锁全部功能。 |

## 结论

现在，您已经掌握了在 Word 图表中 **how to explode slice**、**modify chart in Word**，以及使用 Aspose.Words for Java **change doughnut chart size** 的方法。完整示例展示了从加载文档、定位图表、应用视觉调整到保存结果的完整工作流，帮助您将这些步骤集成到任何报告或文档生成流水线中。

**后续步骤**

- 探索其他图表自定义功能，如更改颜色、添加数据标签或切换图表类型（`chart.setChartType(ChartType.BAR_CLUSTERED)`）。  
- 将此逻辑与 Aspose.PDF 结合，生成相同报告的 PDF 版本。  
- 通过遍历目录中的文件，实现批量文档的自动化处理。

欢迎尝试不同的炸开值或环形孔径百分比，以符合您的设计规范。祝编码愉快！


## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。

- [使用 Aspose.Words for Java 创建柱形图](/words/english/java/document-conversion-and-export/using-charts/)
- [在 Word 文档中隐藏图表坐标轴](/words/english/net/programming-with-charts/hide-chart-axis/)
- [在 Word 文档中插入气泡图](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}