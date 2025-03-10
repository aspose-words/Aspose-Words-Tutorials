---
title: 在 Aspose.Words for Java 中使用图表
linktitle: 使用图表
second_title: Aspose.Words Java 文档处理 API
description: 了解如何在 Aspose.Words for Java 中创建和自定义图表。探索数据可视化的图表类型、格式和轴属性。
weight: 12
url: /zh/java/document-conversion-and-export/using-charts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用图表


## Aspose.Words for Java 中图表的使用简介

在本教程中，我们将探索如何使用 Aspose.Words for Java 处理图表。您将学习如何创建各种类型的图表、自定义轴属性、格式化数据标签等。让我们开始吧！

## 创建折线图

要创建折线图，请使用以下代码：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

//删除默认生成的系列。
chart.getSeries().clear();

//添加包含数据和数据标签的系列。
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

//或者将格式代码链接到源单元格。
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## 创建其他类型的图表

您可以使用类似的技术创建不同类型的图表，如柱形图、面积图、气泡图、散点图等。以下是插入简单柱形图的示例：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

//删除默认生成的系列。
chart.getSeries().clear();

//创建类别并添加数据。
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## 自定义轴属性

您可以自定义轴属性，例如更改轴类型、设置刻度线、设置标签格式等。以下是定义 XY 轴属性的示例：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

//清除默认系列并添加您的数据。

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

//将 X 轴更改为类别而不是日期。
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); //以 Y 轴的显示单位（百）为单位。
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

## 格式化数据标签

您可以使用不同的数字格式来格式化数据标签。以下是示例：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

//清除默认系列并添加您的数据。

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## 额外的图表自定义

您可以通过调整边界、标签之间的间隔单位、隐藏图表轴等进一步自定义图表。探索提供的代码片段以了解有关这些选项的更多信息。

## 结论

在本教程中，我们探索了如何使用 Aspose.Words for Java 处理图表。您已经学习了如何创建各种类型的图表、自定义轴属性、格式化数据标签等。Aspose.Words for Java 提供了强大的工具，可用于将数据的可视化表示添加到您的文档中，从而增强您呈现信息的方式。

## 常见问题解答

### 如何向图表添加多个系列？

您可以使用`chart.getSeries().add()`方法。请确保指定系列名称、类别和数据值。

### 如何使用自定义数字格式来格式化数据标签？

您可以通过访问`DataLabels`系列的属性并使用设置所需的格式代码`getNumberFormat().setFormatCode()`.

### 如何自定义图表中的轴属性？

您可以通过访问`ChartAxis`像属性`setCategoryType()`, `setCrosses()`， 和`setMajorTickMark()`.

### 如何创建其他类型的图表，如散点图或面积图？

您可以通过指定适当的`ChartType`插入图表时使用`builder.insertChart(ChartType.TYPE, width, height)`.

### 如何隐藏图表轴？

您可以通过设置隐藏图表轴`setHidden(true)`轴的属性。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
