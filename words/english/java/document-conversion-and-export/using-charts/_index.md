---
title: Using Charts in Aspose.Words for Java
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
description: Learn how to create and customize charts in Aspose.Words for Java. Explore chart types, formatting, and axis properties for data visualization.
weight: 12
url: /java/document-conversion-and-export/using-charts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Using Charts in Aspose.Words for Java


## Introduction to Using Charts in Aspose.Words for Java

In this tutorial, we'll explore how to work with charts using Aspose.Words for Java. You'll learn how to create various types of charts, customize axis properties, format data labels, and more. Let's dive in!

## Creating a Line Chart

To create a line chart, use the following code:

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

## Creating Other Types of Charts

You can create different types of charts like column, area, bubble, scatter, and more using similar techniques. Here's an example of inserting a simple column chart:

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

## Customizing Axis Properties

You can customize axis properties, such as changing the axis type, setting tick marks, formatting labels, and more. Here's an example of defining XY axis properties:

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

## Formatting Data Labels

You can format data labels with different number formats. Here's an example:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Additional Chart Customizations

You can further customize your charts by adjusting bounds, interval units between labels, hiding chart axes, and more. Explore the provided code snippets to learn more about these options.

## Conclusion

In this tutorial, we've explored how to work with charts using Aspose.Words for Java. You've learned how to create various types of charts, customize axis properties, format data labels, and more. Aspose.Words for Java provides powerful tools for adding visual representations of data to your documents, enhancing the way you present information.

## FAQ's

### How can I add multiple series to a chart?

You can add multiple series to a chart using the `chart.getSeries().add()` method. Make sure to specify the series name, categories, and data values.

### How can I format data labels with custom number formats?

You can format data labels by accessing the `DataLabels` properties of a series and setting the desired format code using `getNumberFormat().setFormatCode()`.

### How do I customize axis properties in a chart?

You can customize axis properties such as type, tick marks, labels, and more by accessing the `ChartAxis` properties like `setCategoryType()`, `setCrosses()`, and `setMajorTickMark()`.

### How can I create other types of charts like scatter or area charts?

You can create various chart types by specifying the appropriate `ChartType` when inserting the chart using `builder.insertChart(ChartType.TYPE, width, height)`.

### How can I hide a chart axis?

You can hide a chart axis by setting the `setHidden(true)` property of the axis.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
