---
category: general
date: 2026-09-24
description: 使用 Aspose.Words for Java 在 DOCX 中插入餅圖。學習設定內孔大小、分離餅圖切片、突顯餅圖切片，輕鬆打造 DOCX
  圖表。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: zh-hant
lastmod: 2026-09-24
og_description: 使用 Aspose.Words for Java 在 DOCX 中插入餅圖。精通設定洞口大小、分離餅片、突顯餅圖切片，並在數分鐘內建立
  DOCX 圖表。
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: 在 Java 中插入圓餅圖文字 – 步驟教學
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: 在 Java 中插入餅圖文字 – 完整指南
url: /zh-hant/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中插入圓餅圖文字 – 完整指南

如果您需要在 DOCX 檔案中 **insert pie chart word**，本教學將向您展示如何使用 Aspose.Words for Java 完成。您將看到從建立文件到自訂圖表的完整工作流程，包括將切片突出、將孔徑設為零，以及將切片加亮。

在 Word 文件中處理圖表常常感覺與一般文字處理是分開的，但 Aspose.Words 將兩者統合。在以下步驟中，您還會學習如何 **create docx chart** 檔案，這些檔案可直接在 Microsoft Word、Google Docs 或任何其他支援 DOCX 的檢視器中開啟。

## 您將完成的工作

* **Insert pie chart word** 到空白文件中  
* **Set hole size** 以將圖表變為完整圓餅（非甜甜圈）  
* **Explode pie slice** 以突出特定區段  
* **Highlight pie chart slice** 使用自訂格式  
* **Create docx chart** 可供分享或進一步編輯  

### 前置條件

* Java 17 或更新版本（程式碼亦可在 Java 8 上編譯）  
* Aspose.Words for Java 函式庫（版本 23.9 或更新）  
* 可解析 Aspose.Words 相依性的 IDE 或建置工具（Maven/Gradle）  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## 如何使用 Aspose.Words 在 DOCX 中 insert pie chart word

第一步是建立一個新的空白文件並取得 `DocumentBuilder`。此建構器讓您直接存取文件的內容串流，使得 **insert pie chart word** 變得非常簡單。

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### 為何這很重要
`Document` 代表整個 Word 檔案，而 `DocumentBuilder` 是高階 API，讓您可以插入段落、表格與圖表，而不必處理低階 XML。從空白文件開始可確保您新增的圖表是唯一內容，這對於學習或產生基於範本的報告非常適合。

## 設定孔徑以建立完整圓餅

預設情況下，當您請求圓餅圖時，Aspose.Words 會建立甜甜圈圖表。若要將圖表變為真正的圓形，必須將 **set hole size** 設為 `0`。這會移除內部孔徑，呈現傳統的圓餅外觀。

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### 實用提示
如果之後決定改為甜甜圈圖表，只需將 `holeSize` 值改為百分比（例如 `30`）。相同的 API 可同時適用於兩種圖表類型。

## 爆炸圓餅切片以突顯區段

將切片爆炸會使其在視覺上突出。**explode pie slice** 操作會將選取的切片向外移動，移動距離為圖表半徑的百分比。

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### 為何要爆炸？
爆炸的切片會將讀者的目光吸引至最重要的資料點——非常適合儀表板或執行摘要。數值 `20` 代表半徑的 20 %；您可以在 `0`（不爆炸）與 `100`（完全分離）之間調整。

## 使用自訂格式突顯圓餅圖切片

除了爆炸之外，您可能還想透過變更填色或邊框來 **highlight pie chart slice**。雖然示範程式碼著重於爆炸，但您可以如下擴充：

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### 專家提示
變更特定切片的填色需要存取 `DataPoint` 物件。若有多個系列，請遍歷 `series.getDataPoints()` 並依條件套用樣式。

## 儲存並驗證已建立的 docx 圖表

最後，您透過儲存 `Document` **create docx chart**。產生的檔案可在 Microsoft Word 中開啟，以檢視已格式化的圓餅圖。

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### 預期輸出
開啟 `PieChartFormatted.docx` 會顯示單一圓餅圖：

* 圖表佔用 400 × 300 pt 的區域。  
* 孔徑為 `0`，因此圖表為完整圓餅。  
* 第一個切片以 20 % 爆炸並呈紅色（若您加入了可選的格式設定）。  

您現在已擁有可 **create docx chart** 的檔案，可進行分發、嵌入電子郵件，或以程式方式進一步編輯。

---

## 常見變體與邊緣情況

| 情境 | 如何調整程式碼 |
|----------|----------------------|
| **Multiple series** | Loop over `pieChart.getChart().getSeries()` and set `Explosion` or `FillColor` per series. |
| **Dynamic data** | Populate the series with values from a database or CSV before calling `setExplosion`. |
| **Different chart size** | Change the width/height arguments in `insertChart(ChartType.PIE, width, height)`. |
| **Export to PDF** | After saving the DOCX, call `doc.save("output.pdf")` to produce a PDF version of the same chart. |
| **Localization** | Use `DocumentBuilder.insertChart` with a locale‑specific number format for labels. |

### 專業技巧
請務必在 `insertChart` 之 **後** 呼叫 `setHoleSize(0)`。若在插入前設定，Aspose.Words 會在圖表建立後恢復為預設的甜甜圈大小。

---

## 重點回顧

您現在已了解如何使用 Java **insert pie chart word** 到 Word 文件、如何 **set hole size** 以呈現完整圓餅、如何 **explode pie slice** 以突出重點，以及如何 **highlight pie chart slice** 以自訂顏色。完整範例亦示範了如何 **create docx chart** 可供分發的檔案。

---

## 往後步驟

* 使用 `ChartType` 探索其他圖表類型（`BAR`、`LINE`、`SCATTER`）。  
* 將圖表產生與郵件合併結合，以產出個人化報告。  
* 將產生的 DOCX 整合至即時回傳檔案的 Web 服務中。  

如果遇到問題，請確認您使用的 Aspose.Words 版本相容，且輸出目錄已存在且具寫入權限。

祝開發順利！

## 接下來應該學什麼？

以下教學涵蓋與本指南示範技術密切相關的主題。每個資源皆包含完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [如何使用 Aspose.Words for Java 建立柱狀圖](/words/english/java/document-conversion-and-export/using-charts/)
- [使用 Word Chart API](/words/english/net/programming-with-charts/)
- [在 Word 中使用 Aspose.Words for .NET 插入氣泡圖](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}