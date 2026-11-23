---
category: general
date: 2026-11-22
description: 在 Java 中建立圓餅圖，學習如何設定圖表大小、加入資料標籤、顯示百分比，並旋轉第一塊以獲得清晰的視覺效果。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: zh-hant
lastmod: 2026-11-22
og_description: 在 Java 中建立餅圖，然後設定圖表大小、在資料標籤上顯示百分比，並旋轉第一個切片——全部於一個可執行的範例中完成。
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: 在 Java 中建立自訂大小、標籤與旋轉的圓餅圖
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: 在 Java 中建立自訂大小、資料標籤與旋轉的圓餅圖
url: /zh-hant/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中建立自訂大小、資料標籤與旋轉的圓餅圖

如果您需要在 Java 中 **create pie chart**，本指南將一步步帶您完成整個流程。您將學會如何 **set chart size**、啟用 **show percentages pie chart**、加入 **data labels pie chart**，以及 **rotate pie chart slice**，讓第一片以 45 度角開始。

本範例使用 **Aspose.Slides for Java**，這是一套廣泛使用的 PowerPoint 檔案操作函式庫。相同概念亦適用於其他圖表函式庫，只要將 API 呼叫換成您工具組中的等價方法即可。

## Prerequisites

開始之前，請確保您已具備：

* 已安裝 Java 17 或更新版本  
* Maven 3.8+（或 Gradle）用於相依管理  
* 基本的 Java 語法概念  
* 取得 Aspose.Slides for Java 的二進位檔（可從官方網站取得免費試用版）

將相依加入您的 `pom.xml`：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Create pie chart – full example

以下程式會建立一個 PowerPoint 投影片，內含自訂大小、顯示百分比資料標籤，且第一片已旋轉的圓餅圖。

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### 為何每一步都很重要

| Step | Purpose | How it relates to the keywords |
|------|---------|--------------------------------|
| **Insert chart** | **Create pie chart** – 產生將呈現視覺效果的核心物件。 | 直接滿足 *create pie chart* 的需求。 |
| **Set dimensions** | `addChart(..., 400, 300)` 呼叫示範 **set chart size**。 | 控制寬度 (400 px) 與高度 (300 px)。 |
| **Show percentages** | `setShowPercentage(true)` 讓圖表 **show percentages pie chart** 在每一片上。 | 使用者常需要百分比而非原始數值。 |
| **Add data labels** | `DataLabelFormat` 設定加入 **data labels pie chart**，並可自行決定可見度。 | 標籤提升可讀性，且可自訂。 |
| **Rotate slice** | `setFirstSliceAngle(45)` 旋轉圖表，使第一片以 45 度角開始，符合 **rotate pie chart slice**。 | 為特定片段提供視覺強調。 |

## Step‑by‑step breakdown

### 1. Insert a pie chart and set chart size

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*`addChart` 方法同時建立圖表並 **set chart size** 為 400 × 300 點。*  
若需其他尺寸，只要調整最後兩個參數即可。

### 2. Populate the chart with data

此示範加入三個類別與單一系列。您可以將硬編碼的數字換成資料庫、CSV 或使用者輸入的資料。

### 3. Show percentages on each slice

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*啟用 `setShowPercentage(true)` 可確保圖表 **show percentages pie chart** 自動計算每片佔總和的比例。*

### 4. Add detailed data labels

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

您可以切換其他標籤選項（`setShowValue`、`setShowSeriesName` 等）以客製 **add data labels pie chart** 的體驗。

### 5. Rotate the first slice

```java
chart.setFirstSliceAngle(45);
```

*呼叫 `setFirstSliceAngle(45)` **rotate pie chart slice**，使第一段以 45 度角開始，突顯該片段。*

### 6. Save and view the result

執行程式後會產生 `output/PieChartDemo.pptx`。在 PowerPoint 或任何相容檢視器開啟，即可看到最終的圓餅圖：

![Create pie chart example](images/pie_chart_example.png){.align-center alt="Screenshot of a created pie chart with custom size, percentage labels, and a rotated first slice"}

上圖展示 **create pie chart** 的結果，證明尺寸、標籤、百分比與旋轉皆正確套用。

## Common variations and edge cases

| Situation | Adjustment |
|-----------|------------|
| **Different chart dimensions** | 在 `addChart` 中變更寬度/高度參數。 |
| **Multiple series** | 新增額外的 `IChartSeries` 物件；每個系列可擁有自己的標籤設定。 |
| **Custom label format** | 使用 `series.getDataLabelFormat().setNumberFormat("0.0%")` 來控制小數位數。 |
| **Rotating to another angle** | 將任意整數 (0‑360) 傳入 `setFirstSliceAngle`。 |
| **Export as image** | 儲存後呼叫 `chart.writeAsSvg(outPath)` 或 `chart.writeAsPng(outPath)` 取得點陣圖版本。 |

> **Pro tip:** 若需在迴圈中產生大量圖表，請重複使用同一個 `Presentation` 物件，僅替換圖表資料。這樣可減少記憶體開銷並提升處理速度。

## Conclusion

現在您已掌握在 Java 中 **create pie chart**、**set chart size**、啟用 **show percentages pie chart**、加入 **data labels pie chart**，以及 **rotate pie chart slice** 以加強視覺重點。完整、可執行的範例示範了從初始化到儲存最終 PowerPoint 檔案的每一步。

### What’s next?

* 探索其他圖表類型（Bar、Line、Area），使用相同的 `ChartType` 列舉。  
* 在單一投影片上結合多個圖表，打造儀表板。  
* 將圖表匯出為 PNG 或 SVG，以供網頁應用程式使用。  

歡迎自行嘗試顏色、圖例與動畫效果——您的資料視覺化僅受想像力限制。祝您圖表製作愉快！

## What Should You Learn Next?

以下教學與本指南緊密相關，能進一步深化您所學的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在自己的專案中探索替代實作方式。

- [how to insert pie chart in Word – add data label percent](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Insert Pie Chart in Java – Explode, Rotate & Highlight Slices](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}