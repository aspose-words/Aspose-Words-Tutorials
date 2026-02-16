---
date: 2026-02-16
description: 学习如何在 Aspose.Words for Java 中向图表添加多个系列、更改坐标轴刻度、应用自定义数字格式，并生成包含折线图和柱状图的图表
  Word 文档。
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: 在 Aspose.Words for Java 中向图表添加多个系列
url: /zh/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中向图表添加多个系列

## Aspose.Words for Java 中使用图表的简介

在本教程中，您将学习 **如何向图表添加多个系列**，了解自定义坐标轴刻度线和应用自定义数字格式的重要性，以及如何生成包含丰富图表的 Word 文档。无论您需要用于财务数据的折线图，还是用于销售数据的柱形图，下面的步骤都将指导您以编程方式创建、样式化和微调图表。

## 快速答疑
- **如何添加多个系列？** 对每个需要显示的系列使用 `chart.getSeries().add(...)`。  
- **可以更改坐标轴刻度线吗？** 可以——在坐标轴对象上使用 `setMajorTickMark()` 和 `setMinorTickMark()`。  
- **数据标签可以使用什么格式？** 任意 Excel 兼容的数字格式，例如 `"$"#,##0.00` 或 `0.00%`。  
- **支持哪些图表类型？** 通过 `ChartType` 支持折线图、柱形图、面积图、气泡图、散点图等多种类型。  
- **生产环境需要许可证吗？** 需要有效的 Aspose.Words for Java 许可证才能获得完整功能。

## 什么是图表中的“添加多个系列”？
添加多个系列是指在同一图表区域中插入多个数据集，以便并排比较不同的类别或时间段。每个系列都会以独立的折线、柱形或标记集合呈现，为读者提供更丰富的可视化信息。

## 为什么使用 Aspose.Words for Java 生成带图表的 Word 文档？
- **完全控制** 图表类型、布局和样式，无需手动打开 Word。  
- **编程生成** 便于集成到自动化报表流水线。  
- **跨平台** ——适用于任何支持 Java 的环境。  
- **丰富的 API** 可自定义坐标轴、数据标签和数字格式。

## 前置条件
- Java Development Kit (JDK) 8 或更高版本。  
- 已将 Aspose.Words for Java 库添加到项目中（Maven/Gradle 或 JAR）。  
- 生产环境下的有效 Aspose 许可证（评估时可选）。

## 步骤指南

### 步骤 1：创建折线图并 **添加多个系列**
下面的核心代码创建了折线图，清除默认系列，然后添加了三个具有自定义数据标签的不同系列。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

> **技巧提示：** 多次调用 `chart.getSeries().add(...)` 即可 **添加多个系列**——每次调用都会在同一图表上生成一条新的折线（或柱形等）。

### 步骤 2：**创建柱形图**（create column chart java）
以下代码片段演示如何插入一个简单的柱形图，适用于并排比较不同类别。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### 步骤 3：**更改坐标轴刻度线**（change axis tick marks）
自定义 X 轴和 Y 轴可以提升可读性。下面的代码展示了如何更改刻度线、反转顺序以及设置自定义交叉点。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### 步骤 4：**应用自定义数字格式**（apply custom number format）
您可以使用 Excel 支持的任意模式格式化坐标轴数字或数据标签。下面的示例将 Y 轴格式化为千位分隔符模式。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### 步骤 5：生成最终的 Word 文档（generate chart word document）
在配置完系列、坐标轴和标签后，只需按上述代码片段调用 `doc.save(...)`。生成的 `.docx` 文件包含可在 Microsoft Word 中打开和编辑的完整功能图表。

## 常见使用场景
- **财务仪表盘**——使用多系列折线图展示收入、支出和利润。  
- **销售报告**——使用柱形图比较各地区的季度销售额。  
- **项目跟踪**——使用面积图或散点图可视化进度随时间的变化。  

## 其他图表自定义
除了基础功能外，您还可以调整坐标轴范围、隐藏坐标轴（`axis.setHidden(true)`）、更改颜色、添加图例等。完整选项请参考 Aspose.Words for Java API 文档。

## 结论
本指南介绍了如何 **向图表添加多个系列**、创建折线图和柱形图、**更改坐标轴刻度线**、**应用自定义数字格式**，以及最终 **生成带图表的 Word 文档**。借助 Aspose.Words for Java，您可以以代码优先的方式将专业的数据可视化直接嵌入文档中。

## 常见问题

**问：如何向图表添加多个系列？**  
答：对每个需要显示的系列调用 `chart.getSeries().add()`。每次调用都会创建一个新的数据集，以独立的折线、柱形或标记组形式出现。

**问：如何使用自定义数字格式对数据标签进行格式化？**  
答：获取系列的 `DataLabels` 对象，使用 `getNumberFormat().setFormatCode("your pattern")`。也可以通过 `isLinkedToSource(true)` 将格式链接到源单元格。

**问：如何更改坐标轴刻度线？**  
答：在 `ChartAxis` 上使用 `setMajorTickMark()` 和 `setMinorTickMark()`。可选项包括 `CROSS`、`INSIDE`、`OUTSIDE` 和 `NONE`。

**问：我可以创建散点图或面积图等其他图表类型吗？**  
答：可以——在调用 `builder.insertChart(...)` 时指定所需的 `ChartType`（例如 `ChartType.SCATTER`、`ChartType.AREA`）。

**问：如何隐藏不需要的坐标轴？**  
答：对想要隐藏的 `ChartAxis` 调用 `axis.setHidden(true)`。

---

**最后更新：** 2026-02-16  
**测试环境：** Aspose.Words for Java 24.11  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}