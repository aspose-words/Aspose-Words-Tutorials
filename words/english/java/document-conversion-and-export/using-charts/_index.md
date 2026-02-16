---
title: Add Multiple Series to Charts in Aspose.Words for Java
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
description: Learn how to add multiple series to charts in Aspose.Words for Java, change axis tick marks, apply custom number format, and generate chart Word documents with line and column charts.
weight: 12
url: /java/document-conversion-and-export/using-charts/
date: 2026-02-16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Add Multiple Series to Charts in Aspose.Words for Java

## Introduction to Using Charts in Aspose.Words for Java

In this tutorial you’ll learn **how to add multiple series** to a chart using Aspose.Words for Java, why customizing axis tick marks and applying a custom number format matters, and how to generate a chart‑rich Word document. Whether you need a line chart for financial data or a column chart for sales figures, the steps below will guide you through creating, styling, and fine‑tuning charts programmatically.

## Quick Answers
- **How do I add multiple series?** Use `chart.getSeries().add(...)` for each series you want to display.  
- **Can I change axis tick marks?** Yes – use `setMajorTickMark()` and `setMinorTickMark()` on the axis objects.  
- **What format can I apply to data labels?** Any Excel‑compatible number format, e.g., `"$"#,##0.00` or `0.00%`.  
- **Which chart types are supported?** Line, column, area, bubble, scatter, and many more via `ChartType`.  
- **Is a license required for production?** A valid Aspose.Words for Java license is needed for full functionality.

## What is “add multiple series” in a chart?
Adding multiple series means inserting more than one data set into the same chart area, allowing you to compare different categories or time periods side‑by‑side. Each series appears as its own line, column, or marker set, giving readers a richer visual story.

## Why use Aspose.Words for Java to generate chart Word documents?
- **Full control** over chart type, layout, and styling without opening Word manually.  
- **Programmatic generation** fits into automated reporting pipelines.  
- **Cross‑platform** – works on any Java‑compatible environment.  
- **Rich API** for customizing axis, data labels, and number formats.

## Prerequisites
- Java Development Kit (JDK) 8 or higher.  
- Aspose.Words for Java library added to your project (Maven/Gradle or JAR).  
- A valid Aspose license for production (optional for evaluation).

## Step‑by‑Step Guide

### Step 1: Create a line chart and **add multiple series**
Below is the core code that creates a line chart, clears the default series, and then adds three distinct series with custom data labels.

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

> **Pro tip:** Call `chart.getSeries().add(...)` as many times as needed to **add multiple series** – each call creates a new line (or column, etc.) on the same chart.

### Step 2: **Create a column chart** (create column chart java)
The next snippet shows how to insert a simple column chart, which is useful for comparing categories side‑by‑side.

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

### Step 3: **Change axis tick marks** (change axis tick marks)
Customizing the X‑ and Y‑axis improves readability. The following code demonstrates how to change tick marks, reverse order, and set custom crossing points.

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

### Step 4: **Apply a custom number format** (apply custom number format)
You can format axis numbers or data labels with any pattern supported by Excel. Below is a concise example that formats the Y‑axis with a thousand‑separator pattern.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Step 5: Generate the final Word document (generate chart word document)
After configuring series, axes, and labels, simply call `doc.save(...)` as shown in the snippets above. The resulting `.docx` file contains fully functional charts that can be opened and edited in Microsoft Word.

## Common Use Cases
- **Financial dashboards** – line charts with multiple series for revenue, expenses, and profit.  
- **Sales reports** – column charts comparing quarterly sales across regions.  
- **Project tracking** – area or scatter charts visualizing progress over time.  

## Additional Chart Customizations
Beyond the basics, you can adjust bounds, hide axes (`axis.setHidden(true)`), change colors, add legends, and more. Refer to the Aspose.Words for Java API reference for the full list of options.

## Conclusion
In this guide we covered how to **add multiple series** to charts, create both line and column charts, **change axis tick marks**, **apply custom number formats**, and finally **generate a chart‑rich Word document**. With Aspose.Words for Java you have a powerful, code‑first way to embed professional data visualizations directly into your documents.

## Frequently Asked Questions

**Q: How can I add multiple series to a chart?**  
A: Call `chart.getSeries().add()` for each series you want to display. Each call creates a new data set that appears as its own line, column, or marker group.

**Q: How do I format data labels with a custom number format?**  
A: Access the series’ `DataLabels` object and use `getNumberFormat().setFormatCode("your pattern")`. You can also link the format to a source cell with `isLinkedToSource(true)`.

**Q: How can I change axis tick marks?**  
A: Use `setMajorTickMark()` and `setMinorTickMark()` on `ChartAxis`. Options include `CROSS`, `INSIDE`, `OUTSIDE`, and `NONE`.

**Q: Can I create other chart types like scatter or area charts?**  
A: Yes – specify the desired `ChartType` (e.g., `ChartType.SCATTER`, `ChartType.AREA`) when calling `builder.insertChart(...)`.

**Q: How do I hide an axis I don’t need?**  
A: Call `axis.setHidden(true)` on the `ChartAxis` you wish to hide.

---

**Last Updated:** 2026-02-16  
**Tested With:** Aspose.Words for Java 24.11  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}