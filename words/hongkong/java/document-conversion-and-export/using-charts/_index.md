---
date: 2026-02-16
description: 了解如何在 Aspose.Words for Java 中向圖表添加多個系列、變更軸刻度標記、套用自訂數字格式，並產生包含折線圖與柱狀圖的圖表
  Word 文件。
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: 在 Aspose.Words for Java 中向圖表添加多個系列
url: /zh-hant/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中向圖表添加多個系列

## 在 Aspose.Words for Java 中使用圖表的簡介

在本教學中，您將學習 **如何向圖表添加多個系列**，以及為何自訂座標軸刻度標記和套用自訂數字格式很重要，並學會產生含圖表的 Word 文件。無論您需要用於財務資料的折線圖，或是用於銷售數據的柱狀圖，以下步驟將指導您以程式方式建立、樣式設定與微調圖表。

## 快速解答
- **如何添加多個系列？** 使用 `chart.getSeries().add(...)` 為每個想要顯示的系列新增。  
- **我可以更改座標軸刻度標記嗎？** 可以 – 在座標軸物件上使用 `setMajorTickMark()` 和 `setMinorTickMark()`。  
- **資料標籤可以套用什麼格式？** 任何 Excel 相容的數字格式，例如 `"$"#,##0.00` 或 `0.00%`。  
- **支援哪些圖表類型？** 折線圖、柱狀圖、面積圖、氣泡圖、散佈圖，以及透過 `ChartType` 支援的更多類型。  
- **生產環境是否需要授權？** 需要有效的 Aspose.Words for Java 授權才能完整使用所有功能。

## 什麼是圖表中的「添加多個系列」？

添加多個系列是指在同一圖表區域內插入多於一組資料集，讓您能夠並排比較不同的類別或時間段。每個系列會以自己的折線、柱狀或標記集合呈現，為讀者提供更豐富的視覺敘事。

## 為何使用 Aspose.Words for Java 產生圖表 Word 文件？

- **完整控制** 圖表類型、版面配置與樣式，無需手動開啟 Word。  
- **程式化產生** 可整合至自動化報告流程。  
- **跨平台** – 可在任何相容 Java 的環境中執行。  
- **豐富的 API** 可自訂座標軸、資料標籤與數字格式。

## 先決條件
- Java Development Kit (JDK) 8 或以上。  
- 已將 Aspose.Words for Java 函式庫加入專案（Maven/Gradle 或 JAR）。  
- 生產環境的有效 Aspose 授權（評估可選）。

## 步驟說明

### 步驟 1：建立折線圖並 **添加多個系列**
以下為核心程式碼，建立折線圖、清除預設系列，並加入三個具有自訂資料標籤的不同系列。

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

> **專業提示：** 依需求多次呼叫 `chart.getSeries().add(...)` 以 **添加多個系列** —— 每次呼叫都會在同一圖表上產生新的折線（或柱狀等）。

### 步驟 2：**建立柱狀圖**（create column chart java）
以下程式碼示範如何插入簡易柱狀圖，適合用於並排比較各類別。

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

### 步驟 3：**更改座標軸刻度標記**（change axis tick marks）
自訂 X 與 Y 軸可提升可讀性。以下程式碼示範如何變更刻度標記、反轉順序，以及設定自訂交叉點。

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

### 步驟 4：**套用自訂數字格式**（apply custom number format）
您可以使用 Excel 支援的任意模式格式化座標軸數字或資料標籤。以下為簡潔範例，將 Y 軸以千位分隔符號格式化。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### 步驟 5：產生最終的 Word 文件（generate chart word document）
在完成系列、座標軸與標籤設定後，只需如上段程式碼呼叫 `doc.save(...)`。產生的 `.docx` 檔案內含完整功能的圖表，可在 Microsoft Word 中開啟與編輯。

## 常見使用情境
- **財務儀表板** – 折線圖顯示收入、支出與利潤等多個系列。  
- **銷售報告** – 柱狀圖比較各區域的季度銷售。  
- **專案追蹤** – 面積圖或散佈圖呈現隨時間的進度。

## 其他圖表自訂
除基本功能外，您還可調整範圍、隱藏座標軸（`axis.setHidden(true)`）、變更顏色、加入圖例等。請參考 Aspose.Words for Java API 說明文件取得完整選項清單。

## 結論
本指南說明了如何 **添加多個系列** 至圖表、建立折線圖與柱狀圖、**更改座標軸刻度標記**、**套用自訂數字格式**，以及最終 **產生含圖表的 Word 文件**。使用 Aspose.Words for Java，您可透過程式碼方式將專業的資料視覺化直接嵌入文件，功能強大且彈性十足。

## 常見問與答

**Q: 如何向圖表添加多個系列？**  
A: 為每個想要顯示的系列呼叫 `chart.getSeries().add()`。每次呼叫都會產生一個新的資料集，顯示為自己的折線、柱狀或標記群組。

**Q: 如何使用自訂數字格式設定資料標籤？**  
A: 取得系列的 `DataLabels` 物件，並使用 `getNumberFormat().setFormatCode("your pattern")`。亦可透過 `isLinkedToSource(true)` 將格式連結至來源儲存格。

**Q: 如何更改座標軸刻度標記？**  
A: 在 `ChartAxis` 上使用 `setMajorTickMark()` 與 `setMinorTickMark()`。可選擇 `CROSS`、`INSIDE`、`OUTSIDE`、`NONE` 等。

**Q: 我可以建立其他圖表類型，例如散佈圖或面積圖嗎？**  
A: 可以 – 在呼叫 `builder.insertChart(...)` 時指定所需的 `ChartType`（例如 `ChartType.SCATTER`、`ChartType.AREA`）。

**Q: 如何隱藏不需要的座標軸？**  
A: 在想要隱藏的 `ChartAxis` 上呼叫 `axis.setHidden(true)`。

---

**最後更新：** 2026-02-16  
**測試環境：** Aspose.Words for Java 24.11  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}