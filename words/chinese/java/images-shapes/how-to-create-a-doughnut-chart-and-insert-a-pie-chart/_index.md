---
category: general
date: 2026-10-26
description: 在 Java 中创建环形图并插入饼图，提供逐步代码。学习完整的工作流程，实现灵活的图表可视化。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: zh
lastmod: 2026-10-26
og_description: 使用本指南在 Java 中创建环形图，并展示如何插入饼图以实现灵活的可视化。
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: 创建环形图并插入饼图 – Java指南
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: 如何创建环形图并插入饼图
url: /zh/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何创建环形图并插入饼图

如果您需要在 Java 中 **创建环形图**，本教程将逐步指导您完成整个过程。我们还将展示如何使用相同的 builder API **插入饼图**，以便您能够轻松在两种视觉样式之间切换。完成本指南后，您将拥有一个完整的可运行程序，能够生成这两种图表并演示常见的自定义设置。

本教程包括：

* 初始化所选库提供的图表构建器。  
* 创建环形图并配置孔径大小。  
* 插入饼图并对切片进行爆炸以突出显示。  
* 处理缺失系列或不支持的图表类型等边缘情况的技巧。

您只需准备一个近期的 JDK（8 或更高）以及 classpath 中的图表库 JAR。无需任何外部服务。

---

## 前置条件

| 项目 | 原因 |
|------|--------|
| Java Development Kit (JDK) 8+ | 需要用于编译和运行示例。 |
| Chart library (e.g., **Aspose.Cells for Java** or **JFreeChart**) | 提供代码中使用的 `ChartBuilder`、`ChartType` 和系列操作方法。 |
| An IDE or a text editor | 用于编写和执行 Java 源文件。 |

确保将库 JAR 添加到项目的构建路径中。如果使用 Maven，请添加相应的依赖；否则，将 JAR 放置在 `libs` 文件夹中，并在编译时引用它。

---

## 步骤 1：设置图表构建器

第一步是创建一个 `ChartBuilder`（或等效）实例，用于生成图表对象。该对象充当工厂，并持有图表将要放置的工作表或画布。

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**为什么这很重要：**  
构建器将图表绑定到特定的工作表，确保所有后续图表对象共享同一绘图表面。跳过此步骤会导致没有可放置可视元素的目标位置。

---

## 步骤 2：**创建环形图**

现在我们生成一个具有定义大小的环形图。孔径大小决定图表中心有多少空白，将普通饼图转换为环形图。

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**说明：**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` 创建图表对象并在工作表上预留空间。  
* `setHoleSize(30)` 将饼图转换为中心空白 30% 的环形图。  
* `add("{10, 20, 30, 40}", true)` 提供四个数据点；`true` 标志告诉库将这些值视为单个系列。  

**边缘情况：** 如果所选图表类型不支持孔（例如柱形图），调用 `getDoughnutChart()` 会抛出异常。调整孔径大小前请务必验证图表类型。

---

## 步骤 3：**插入饼图**

环形图准备好后，我们演示如何使用相同的构建器 **插入饼图**。此步骤突出两种图表类型的相似性，并展示如何强调某个切片。

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**说明：**  

* `ChartType.PIE` 告诉构建器创建经典的饼图。  
* `setExplode(10)` 将第一块切片偏移半径的 10%，这是一种常用的突出关键数据点的技巧。  

**提示：** `setExplode` 方法仅在饼图的第一个系列上有效。如果有多个系列，需要定位到正确的索引进行设置。

---

## 步骤 4：保存工作簿

最后，将工作簿写入文件，以便在 Excel 或任何兼容的查看器中查看图表。

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**为什么现在保存：**  
持久化工作簿会完成所有绘图操作。未保存就尝试查看文件会导致文档为空或不完整。

**结果：** 打开 *DoughnutAndPieChart.xlsx* 可看到左侧的 30% 孔径环形图和右侧带有爆炸第一切片的饼图。

---

## 步骤 5：常见变体和故障排除

| 情况 | 调整 |
|-----------|------------|
| **不同的图表尺寸** | 在 `insertChart` 中更改宽度和高度参数。 |
| **多个数据系列** | 多次调用 `add`，或传入二维数组字符串。 |
| **动态孔径大小** | 根据数据范围计算孔径大小，然后调用 `setHoleSize`。 |
| **多个切片爆炸** | 对每个需要偏移的切片，循环调用 `chart.getSeries().get(i).setExplode(percent)`。 |
| **库不支持环形图** | 使用饼图并手动绘制白色圆形覆盖层，尽管精度较低。 |

**专业提示：** 在处理大型工作簿时，插入图表后始终调用 `builder.flush()`（如果可用）。这会释放内部缓冲区，防止内存泄漏。

![Java 代码创建环形图并插入饼图](https://example.com/images/doughnut-pie-java.png "Java 中创建环形图示例")

*该图片展示了最终工作簿的布局，两个图表并排显示。*

---

## 结论

您现在已经掌握了如何使用流式 builder API 在 Java 中 **创建环形图** 和 **插入饼图**。完整示例涵盖了初始化、尺寸配置、孔径设置、切片爆炸以及文件输出。从这里您可以进一步探索颜色、图例和数据标签等自定义功能，以满足报告需求。

**下一步**

* 试验 **chart customization Java** 功能，如渐变填充和数据标签。  
* 将图表生成集成到按需返回工作簿的 Web 服务中。  
* 将 builder 方法与其他库（如 JFreeChart）进行比较，选择最适合您项目的方案。

祝您绘图愉快！

## 接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您在此基础上进一步掌握 API 功能并探索替代实现方式，每篇资源均提供完整可运行的代码示例和逐步说明。

- [如何在 Word 文档中使用 Java 创建环形图](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [在 Java 中编辑环形图后保存 Word 文档](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [在 Java 中插入饼图 – 爆炸、旋转与突出切片](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}