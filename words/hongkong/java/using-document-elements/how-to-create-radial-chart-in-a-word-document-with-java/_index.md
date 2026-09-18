---
category: general
date: 2026-09-18
description: 學習如何使用 Java 在 Word 文件中建立徑向圖、加入圖表資料標籤，並插入系列資料，提供完整程式碼範例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: zh-hant
lastmod: 2026-09-18
og_description: 使用 Java 在 Word 文件中建立徑向圖表，加入圖表資料標籤，並在單一教學中插入系列資料。
og_image_alt: Radial chart displayed inside a generated Word document
og_title: 在 Word 中使用 Java 建立徑向圖表 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: 如何使用 Java 在 Word 文件中建立雷達圖
url: /zh-hant/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Java 在 Word 文件中建立徑向圖表

如果您需要在 Word 文件中建立徑向圖表，本指南將示範完整步驟。您還會學會如何加入圖表資料標籤以及插入系列資料，使圖表可直接用於簡報。

以程式方式產生圖表可省去手動格式設定的工作，並確保報表之間的一致性。本教學假設您具備基本的 Java 知識，且已安裝最新版本的 Aspose.Words for Java 程式庫。

## 您需要的環境

* Java 17 或更新版本  
* Aspose.Words for Java（版本 23.12 或更新）  
* 能解析 Maven/Gradle 相依性的 IDE 或建置工具  

具備上述前置條件即可直接執行範例，無需額外設定。

## 如何在 Word 文件中建立徑向圖表

第一步是建立一個空白的 Word 檔案，作為圖表的容器。空白文件提供乾淨的畫布，避免不必要的樣式干擾。

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 代表整個 .docx 檔案，而 `DocumentBuilder` 提供插入段落、表格與圖表等元素的方法。

## 如何插入圖表

接著插入圖表本身。`insertChart` 方法會建立圖表物件，並將其放置於 builder 目前的游標位置。

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

極座標圖會將資料點繞著中心軸排列，非常適合顯示週期性資訊。尺寸單位為點 (1 pt ≈ 1/72 英吋)。

## 為圖表加入系列資料

沒有系列資料的圖表是空的。您可以手動加入系列，或將其綁定至資料來源。以下範例加入一個包含三個資料點的單一系列。

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` 會接受系列名稱、類別標籤清單以及對應的數值清單。您可以重複此區塊以加入其他系列（`addSeriesData`）。

## 為第一個系列加入圖表資料標籤

資料標籤讓圖表即使不懸停也能閱讀。下列程式碼會為第一個系列開啟數值標籤。

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

將 `showValue` 設為 `true` 後，圖表會直接在每個點上顯示其數值。您亦可透過同一個 `DataLabelFormat` 物件啟用類別名稱、百分比或領導線等。

## 儲存 Word 檔案

圖表設定完成後，將文件寫入磁碟。請選擇應用程式可存取的路徑。

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

`RadialChart.docx` 現在已包含一個完整功能的徑向圖表，且帶有資料標籤。

## 完整可執行範例

以下是一個自包含的程式，您可以直接複製、編譯並執行。它示範了從建立空白 Word 文件到儲存帶資料標籤的徑向圖表的完整流程。

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**預期結果**

當您在 Microsoft Word 中開啟 `output/RadialChart.docx` 時，會看到一個標題為 *Quarterly Sales* 的徑向圖表。每個點旁都會顯示其數值（例如「15000」）。

## 常見變化與邊緣情況

| 情況 | 建議的更改 |
|-----------|--------------------|
| 需要不同的圖表類型 | 將 `ChartType.POLAR` 替換為其他 `ChartType` 列舉值（例如 `ChartType.COLUMN`）。 |
| 圖表必須使用外部 Excel 範圍 | 在建立圖表並載入工作簿後，使用 `chart.setDataRange("Sheet1!A1:B5")`。 |
| 想隱藏圖例 | `chart.getLegend().setVisible(false);` |
| 必須將文件儲存為 PDF | 呼叫 `doc.save("RadialChart.pdf");` – Aspose.Words 會自動轉換圖表。 |

這些調整不會改變核心邏輯，同時可因應特定需求調整輸出。

## 專業小技巧

* **重複使用 builder** – 透過多次呼叫 `builder.insertChart`，即可在同一文件中插入多個圖表。  
* **效能** – 若要產生大量圖表，建議只建立一個 `DocumentBuilder` 實例並重複使用，以減少物件分配開銷。  
* **樣式** – 圖表外觀（顏色、線條粗細）可透過 `Chart` 物件的 `getSeries().get(i).getFormat()` 方法控制。請多加實驗，以符合企業品牌形象。

## 結論

現在您已掌握如何使用 Java 在 Word 文件中建立徑向圖表、加入系列資料與圖表資料標籤，並將檔案儲存。完整範例亦可延伸以處理更多系列、客製樣式或其他輸出格式。

探索相關主題，例如 **如何從外部資料來源插入圖表**、**使用預先定義範本建立空白 Word 文件**，以及 **從資料庫動態加入系列資料**。嘗試不同的圖表類型，找出最能傳達您資料的視覺呈現方式。

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，進一步深化您在專案中運用 API 的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多功能並探索替代實作方式。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}