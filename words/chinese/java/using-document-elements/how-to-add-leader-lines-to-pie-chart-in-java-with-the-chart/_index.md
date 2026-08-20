---
category: general
date: 2026-08-20
description: 在 Java 中快速为饼图添加引线。学习使用 Chart API 插入、突出、重新着色和标注切片。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: zh
lastmod: 2026-08-20
og_description: 在 Java 中为饼图添加指示线，示例简洁。按照本指南使用 Chart API 插入、突出、重新着色并标注切片。
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: 在 Java 中为饼图添加引线 – 步骤式 Chart API 指南
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: 如何在 Java 中使用 Chart API 为饼图添加引导线
url: /zh/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中使用 Chart API 为饼图添加引线

如果您需要在 Java 中**为饼图添加引线**，本指南将带您完成整个过程。您将看到如何插入饼图、为突出显示而炸裂切片、更改其颜色，最后启用将炸裂切片标记的引线。

示例使用了许多 Java 报表库中提供的标准 Chart API。无需外部工具，代码可在任何 JDK 8+ 环境下运行。

## 您将实现的目标

* 创建一个类型为 `ChartType.PIE`、自定义尺寸的 `Chart`。  
* 炸裂第一块切片以吸引注意。  
* 将炸裂切片的扇区颜色设置为蓝色。  
* **为饼图添加引线**，使切片标签清晰连接。

您应该已经在类路径中拥有 Chart 库的 Java 项目。如果使用 Maven，请在前置条件部分添加所示的依赖。

## 前置条件

* 已安装 JDK 8 或更高版本。  
* Chart 库（例如 `com.example.chart:chart-api:2.5.0`）。  
* 对 Java 类和方法调用有基本了解。

---

## 如何为饼图添加引线

下面是一个完整、可运行的程序，演示每一步。代码特意保持自包含，您可以复制、粘贴并直接运行，无需修改。

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### 每一步的说明

| 步骤 | 代码作用 | 重要原因 |
|------|----------|----------|
| **1️⃣ 插入饼图** | `builder.insertChart(ChartType.PIE, 400, 300)` 创建一个 400 × 300 像素的饼图。 | 建立图表容器并定义其尺寸，这会影响标签放置和引线长度。 |
| **2️⃣ 炸裂第一块切片** | `setExplosion(20)` 将切片偏移半径的 20 %。 | 炸裂的切片能够吸引观众注意，并使引线可见。 |
| **3️⃣ 设置扇区颜色** | `setSectorColor(Color.BLUE)` 将切片填充颜色改为蓝色。 | 颜色对比度提升可读性，尤其在切片被突出显示时。 |
| **4️⃣ 启用引线** | `setLeaderLines(true)` 打开将切片与其标签相连的连接线。 | 引线确保即使切片向外移动，标签仍保持可读。 |

`saveAsPng` 调用是可选的，但有助于验证视觉结果。运行程序后，您应看到如下图所示的图片。

![为饼图添加引线](https://example.com/assets/pie-leader-lines.png "为饼图添加引线 – 炸裂切片为蓝色并带有引线")

*图示：一个饼图，第一块切片被炸裂，颜色为蓝色，并通过引线连接到其标签。*

## 自定义引线（高级）

基本的 `setLeaderLines(true)` 调用使用库的默认样式。您可以进一步控制外观：

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

当需要匹配企业品牌或提升可访问性时，这些选项非常实用。

### 处理多个系列

如果您的饼图包含多个系列，您可能只想为特定切片启用引线。使用系列索引来定位正确的元素：

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

当切片未被炸裂时，引线通常会自动隐藏，但您可以使用 `setLeaderLineEnabled(true)` 强制显示。

## 常见陷阱及避免方法

| 陷阱 | 症状 | 解决办法 |
|------|------|----------|
| **引线不可见** | 图表渲染时没有连接线。 | 确保切片已炸裂（`setExplosion` > 0）或在切片上显式启用引线。 |
| **标签重叠** | 标签相互碰撞。 | 增大图表尺寸或设置 `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`。 |
| **颜色未应用** | 切片仍为默认颜色。 | 确认您定位了正确的系列索引（`getSeries().get(0)`）。 |
| **图片未保存** | `saveAsPng` 抛出异常。 | 检查输出目录的写入权限，并确认库支持 PNG 导出。 |

提前解决这些问题可避免运行时意外，并生成精美的图表。

## 完整源码列表

为方便起见，这里再次提供完整的源文件，包括导入和注释：

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

运行此程序会生成 `pie-with-leader-lines.png`，该图显示了一个炸裂的蓝色切片以及指向切片标签的清晰引线的饼图。

## 结论

您现在已经了解如何在 Java 中使用 Chart API **为饼图添加引线**。该过程包括插入 `ChartType.PIE`、炸裂所需切片、定制其颜色以及启用引线。通过可选的样式设置，您可以微调线条颜色、粗细和标签位置，以满足任何视觉需求。

接下来，您可以探索相关主题，如 **pie chart explosion Java**、**set sector color Chart API** 和 **builder.insertChart usage**，以创建更复杂的可视化，例如环形图、堆叠饼图或交互式仪表板。

欢迎尝试不同的切片索引、颜色和引线样式——您的图表将随着每次微调变得更具信息量且更具视觉吸引力。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方法。

- [如何使用 Aspose.Words for Java 创建柱状图](/words/english/java/document-conversion-and-export/using-charts/)
- [向图表坐标轴添加日期时间值](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [使用 Aspose.Words for .NET 在 Word 中插入柱状图](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}