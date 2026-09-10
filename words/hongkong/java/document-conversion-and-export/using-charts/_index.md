---
date: 2025-12-13
description: 學習如何使用 Aspose.Words for Java 建立柱狀圖並設定圖表資料標籤。探索加入多個系列、變更軸類型以及隱藏圖表軸。
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 建立柱形圖
url: /zh-hant/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 建立柱狀圖

在本教學中，您將使用 Aspose.Words for Java 直接在 Word 文件中 **建立柱狀圖** 可視化。我們將逐步說明如何建立不同類型的圖表、加入多個資料系列、格式化圖表資料標籤、變更座標軸類型，甚至在需要更簡潔外觀時隱藏圖表座標軸。完成後，您將掌握一套穩固、可投入生產環境的方式，將豐富圖表嵌入文件中。

## 快速答覆
- **建立圖表的主要類別是什麼？** `DocumentBuilder` 搭配 `insertChart`。
- **哪個方法可加入新系列？** `chart.getSeries().add(...)`。
- **如何格式化圖表資料標籤？** 使用 `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`。
- **我可以隱藏座標軸嗎？** 可以，對座標軸物件呼叫 `setHidden(true)`。
- **使用 Aspose.Words 是否需要授權？** 生產環境必須購買授權；亦提供免費試用版。

## 什麼是柱狀圖，為什麼要使用它？

柱狀圖以垂直長條顯示類別資料，非常適合比較不同群組的數值（例如各區域銷售額、每月支出等）。在 Java 應用程式中，使用 Aspose.Words 產生柱狀圖，可直接將這些視覺化圖表嵌入 Word / DOCX 檔案，無需 Excel 或其他外部工具。

## 如何建立柱狀圖

以下是一個簡單的範例，建立一個基本的柱狀圖。程式碼與原始片段完全相同，我們僅加入說明性註解以便於閱讀。

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

### 加入多個系列

您可以透過重複呼叫 `chart.getSeries().add(...)`，如上例所示，**加入多個系列** 到柱狀圖中。每個系列可擁有自己的類別與數值，讓您能夠並排比較多組資料。

## 如何建立帶自訂資料標籤的折線圖

若需要折線圖而非柱狀圖，使用方式相同。此範例同時示範如何以不同的數字格式 **格式化圖表資料標籤**。

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

### 加入資料標籤

呼叫 `series1.hasDataLabels(true)` **為系列加入資料標籤**，而 `setShowValue(true)` 則會在圖表上顯示實際數值。

## 如何變更座標軸類型與自訂座標軸屬性

變更座標軸類型（例如由日期軸改為類別軸）可控制資料點的繪製方式。此程式碼片段亦示範若想要極簡設計，如何 **隱藏圖表座標軸**。

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

### 變更座標軸類型

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **將座標軸類型** 從日期軸變更為類別軸，讓您完全掌控標籤的放置方式。

## 如何格式化圖表資料標籤（數字格式）

您可以直接對座標軸或資料標籤套用數字格式。此範例將 Y 軸的數字以千位分隔符號顯示。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## 其他圖表自訂功能

除基本功能外，您還可以調整範圍、設定標籤之間的間隔單位、隱藏特定座標軸等。請參閱 Aspose.Words for Java API 文件，以取得完整屬性清單。

## 常見問題

**Q: 如何在圖表中加入多個系列？**  
A: 對每個欲顯示的系列呼叫 `chart.getSeries().add()`。每次呼叫可提供唯一的名稱、類別陣列與數值陣列。

**Q: 如何使用自訂數字格式來格式化圖表資料標籤？**  
A: 取得系列的 `DataLabels` 物件，並呼叫 `getNumberFormat().setFormatCode("your format")`。亦可使用 `isLinkedToSource(true)` 將格式連結至來源儲存格。

**Q: 如何隱藏圖表座標軸？**  
A: 在欲隱藏的 `ChartAxis` 上呼叫 `setHidden(true)`（例如 `chart.getAxisY().setHidden(true)`）。

**Q: 變更座標軸類型的最佳方式是什麼？**  
A: 對類別座標軸使用 `setCategoryType(AxisCategoryType.CATEGORY)`，對日期座標軸使用 `AxisCategoryType.DATE`。

**Q: 如何為系列加入資料標籤？**  
A: 使用 `series.hasDataLabels(true)` 啟用，然後透過 `series.getDataLabels().setShowValue(true)` 設定可見性。

## 結論

我們已說明如何使用 Aspose.Words for Java **建立柱狀圖** 可視化——從插入基本圖表、加入多個系列、格式化圖表資料標籤、變更座標軸類型，到隱藏圖表座標軸以獲得簡潔外觀。將這些技巧整合至您的報表或文件產生流程，即可交付專業且以資料驅動的 Word 文件。

---

**最後更新：** 2025-12-13  
**測試環境：** Aspose.Words for Java 24.12 (latest)  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}