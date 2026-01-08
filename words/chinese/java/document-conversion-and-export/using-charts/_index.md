---
date: 2025-12-13
description: 学习如何使用 Aspose.Words for Java 创建柱形图并格式化图表数据标签。探索添加多个系列、更改坐标轴类型以及隐藏坐标轴。
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 创建柱状图
url: /zh/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 创建柱状图

在本教程中，您将 **创建柱状图** 可视化，直接嵌入 Word 文档，使用 Aspose.Words for Java。我们将演示如何创建不同类型的图表、添加多个系列、格式化图表数据标签、更改坐标轴类型，甚至在需要更简洁外观时隐藏坐标轴。完成后，您将掌握在文档中嵌入丰富图表的完整、可投入生产的方案。

## 快速答疑
- **构建图表的主要类是什么？** 使用 `DocumentBuilder` 的 `insertChart`。
- **哪个方法用于添加新系列？** `chart.getSeries().add(...)`。
- **如何格式化图表数据标签？** 使用 `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`。
- **可以隐藏坐标轴吗？** 可以，对坐标轴对象调用 `setHidden(true)`。
- **使用 Aspose.Words 是否需要许可证？** 生产环境需要许可证；提供免费试用版。

## 什么是柱状图，为什么使用它？

柱状图将分类数据以垂直柱形展示，适合比较不同组别的数值（如各地区销售额、月度支出等）。在 Java 应用中，使用 Aspose.Words 生成柱状图可以直接将这些可视化嵌入 Word / DOCX 文件，无需 Excel 或其他外部工具。

## 如何创建柱状图

下面是一个创建简单柱状图的直接示例。代码与原始片段完全相同——我们仅添加了解释性注释，便于阅读。

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

### 添加多个系列

通过重复调用 `chart.getSeries().add(...)`，您可以 **向柱状图添加多个系列**，如上所示。每个系列可以拥有自己的类别和数值，从而实现多组数据的并列比较。

## 如何创建带自定义数据标签的折线图

如果需要折线图而非柱状图，使用相同的模式即可。此示例还演示了如何 **使用不同的数字格式格式化图表数据标签**。

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

### 添加数据标签

调用 `series1.hasDataLabels(true)` **为系列添加数据标签**，而 `setShowValue(true)` 则使实际数值在图表上可见。

## 如何更改坐标轴类型并自定义坐标轴属性

更改坐标轴类型（例如从日期轴改为类别轴）可控制数据点的绘制方式。此代码片段还展示了如果您偏好极简设计，**如何隐藏图表坐标轴**。

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

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### 更改坐标轴类型

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **将坐标轴类型** 从基于日期的轴改为类别轴，让您完全掌控标签的放置方式。

## 如何格式化图表数据标签（数字格式）

您可以直接对坐标轴或数据标签应用数字格式。本示例对 Y 轴的数字使用千位分隔符进行格式化。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## 其他图表自定义

除基础功能外，您还可以调整图表边界、设置标签之间的间隔单位、隐藏特定坐标轴等。完整属性列表请参阅 Aspose.Words for Java API 文档。

## 常见问题

**问：如何向图表添加多个系列？**  
答：对每个需要显示的系列调用 `chart.getSeries().add()`。每次调用可提供唯一的名称、类别数组和数值数组。

**问：如何使用自定义数字格式格式化图表数据标签？**  
答：获取系列的 `DataLabels` 对象，调用 `getNumberFormat().setFormatCode("your format")`。也可以通过 `isLinkedToSource(true)` 将格式链接到源单元格。

**问：如何隐藏图表坐标轴？**  
答：对要隐藏的 `ChartAxis` 调用 `setHidden(true)`（例如 `chart.getAxisY().setHidden(true)`）。

**问：更改坐标轴类型的最佳方式是什么？**  
答：对类别坐标轴使用 `setCategoryType(AxisCategoryType.CATEGORY)`，对日期坐标轴使用 `AxisCategoryType.DATE`。

**问：如何为系列添加数据标签？**  
答：通过 `series.hasDataLabels(true)` 启用，然后使用 `series.getDataLabels().setShowValue(true)` 配置可见性。

## 结论

我们已经覆盖了使用 Aspose.Words for Java **创建柱状图** 可视化的全部要点——从插入基础图表、添加多个系列，到格式化图表数据标签、更改坐标轴类型以及隐藏坐标轴以获得简洁外观。将这些技术融入您的报表或文档生成流程，即可交付专业、数据驱动的 Word 文档。

---

**最后更新：** 2025-12-13  
**测试环境：** Aspose.Words for Java 24.12（最新）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}