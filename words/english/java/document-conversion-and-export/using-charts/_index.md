---
title: How to create column chart using Aspose.Words for Java
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
description: Learn how to create column chart and format chart data labels with Aspose.Words for Java. Explore adding multiple series, changing axis type, and hide chart axis.
weight: 12
url: /java/document-conversion-and-export/using-charts/
date: 2025-12-13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# How to create column chart using Aspose.Words for Java

In this tutorial you’ll **create column chart** visualizations directly inside Word documents using Aspose.Words for Java. We’ll walk through creating different chart types, adding multiple series, formatting chart data labels, changing axis type, and even hiding a chart axis when you need a cleaner look. By the end you’ll have a solid, production‑ready approach for embedding rich charts in your documents.

## Quick Answers
- **What is the primary class to build a chart?** `DocumentBuilder` with `insertChart`.
- **Which method adds a new series?** `chart.getSeries().add(...)`.
- **How do I format chart data labels?** Use `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **Can I hide an axis?** Yes, call `setHidden(true)` on the axis object.
- **Do I need a license for Aspose.Words?** A license is required for production use; a free trial is available.

## What is a column chart and why use it?

A column chart displays categorical data as vertical bars, making it ideal for comparing values across groups (sales per region, monthly expenses, etc.). In Java applications, generating a column chart with Aspose.Words lets you embed these visuals directly into Word / DOCX files without needing Excel or external tools.

## How to create a column chart

Below is a straightforward example that creates a simple column chart. The code is identical to the original snippet – we’ve only added explanatory comments to make it easier to follow.

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

### Add multiple series

You can **add multiple series** to a column chart by calling `chart.getSeries().add(...)` repeatedly, as shown above. Each series can have its own set of categories and values, allowing you to compare several data sets side‑by‑side.

## How to create a line chart with custom data labels

If you need a line chart instead of a column chart, the same pattern applies. This example also demonstrates **format chart data labels** with different number formats.

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

### Add data labels

The call `series1.hasDataLabels(true)` **adds data labels** to the series, while `setShowValue(true)` makes the actual values visible on the chart.

## How to change axis type and customize axis properties

Changing the axis type (e.g., from date to category) lets you control how data points are plotted. This snippet also shows how to **hide chart axis** if you prefer a minimalist design.

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

### Change axis type

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **changes axis type** from a date‑based axis to a categorical one, giving you full control over label placement.

## How to format chart data labels (number formats)

You can apply number formatting directly to the axis or data labels. This example formats the Y‑axis numbers with a thousands separator.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Additional chart customizations

Beyond the basics, you can adjust bounds, set interval units between labels, hide specific axes, and more. Refer to the Aspose.Words for Java API documentation for a full list of properties.

## Frequently Asked Questions

**Q: How can I add multiple series to a chart?**  
A: Use `chart.getSeries().add()` for each series you want to display. Each call can provide a unique name, category array, and value array.

**Q: How do I format chart data labels with custom number formats?**  
A: Access a series’ `DataLabels` object and call `getNumberFormat().setFormatCode("your format")`. You can also link the format to a source cell with `isLinkedToSource(true)`.

**Q: How can I hide a chart axis?**  
A: Call `setHidden(true)` on the `ChartAxis` you want to hide (e.g., `chart.getAxisY().setHidden(true)`).

**Q: What is the best way to change axis type?**  
A: Use `setCategoryType(AxisCategoryType.CATEGORY)` for categorical axes or `AxisCategoryType.DATE` for date axes.

**Q: How do I add data labels to a series?**  
A: Enable them with `series.hasDataLabels(true)` and then configure visibility using `series.getDataLabels().setShowValue(true)`.

## Conclusion

We’ve covered everything you need to **create column chart** visualizations with Aspose.Words for Java—from inserting basic charts and adding multiple series, to formatting chart data labels, changing axis type, and hiding chart axes for a clean look. Incorporate these techniques into your reporting or document‑generation pipelines to deliver professional, data‑driven Word documents.

---

**Last Updated:** 2025-12-13  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}