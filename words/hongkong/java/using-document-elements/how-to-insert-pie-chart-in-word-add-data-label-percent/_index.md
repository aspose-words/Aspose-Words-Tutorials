---
category: general
date: 2026-07-20
description: 如何在 Word 中使用 Aspose.Words 插入圓餅圖。學習如何加入資料標籤百分比，並在圖表上顯示百分比，以製作專業文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: zh-hant
lastmod: 2026-07-20
og_description: 如何使用 Aspose.Words 在 Word 中插入圓餅圖。本指南示範如何加入資料標籤百分比，僅用幾行程式碼即可在圖表上顯示百分比。
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: 如何在 Word 中插入餅圖 – 快速指南
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: 如何在 Word 中插入圓餅圖 – 加上資料標籤百分比
url: /zh-hant/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中插入圓餅圖 – 添加資料標籤百分比

有沒有想過 **如何在 Word 中插入圓餅圖**，卻不想與繁雜的 UI 纏鬥？你並不孤單。在許多報表情境下，你需要 *將圓餅圖加入 Word*，更重要的是 **在圓餅圖上顯示百分比**，讓讀者能立即掌握資料分佈。

在本教學中，我們將使用 Aspose.Words for Java 完整示範整個流程。完成後，你將清楚知道如何 **添加資料標籤百分比**、**在圖表上顯示百分比**，並一次產出外觀正確的圓餅圖。無需額外外掛、無需手動調整——只要簡潔的程式碼即可直接套用於任何專案。

---

## 前置條件

- Java 17（或更新版本）——Aspose.Words 支援的目前 LTS 版。
- Aspose.Words for Java 24.x（撰寫本文時的最新版本，2026 年 7 月）。
- 能夠透過 Maven 或 Gradle 取得套件的基本環境。
- 你慣用的 IDE（IntelliJ IDEA、Eclipse、VS Code… 任一皆可）。

如果這些都已備妥，太好了——讓我們開始吧。

---

## 步驟 1：設定專案並匯入函式庫

首先，將 Aspose.Words 相依性加入 `pom.xml`（Maven）或 `build.gradle`（Gradle）。如此即可使用 `Document`、`DocumentBuilder` 以及圖表相關類別。

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **專業小技巧：** 請保持版本號為最新；較新的發行版常會加入圖表相關的修正，使 **在圖表上顯示百分比** 更加可靠。

---

## 步驟 2：建立新 Word 文件與 Builder

Builder 是插入內容的萬能工具。我們先建立一個空白文件，然後將 `DocumentBuilder` 附加於其上。

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

為什麼需要 Builder？它抽象化了底層的 OpenXML 結構，讓我們只關注 *想要做什麼*——例如 **將圓餅圖加入 Word**——而不必在意 XML 的細節。

---

## 步驟 3：插入圓餅圖

接下來就是 **如何在 Word 中插入圓餅圖** 的核心。我們請 Builder 放置一個指定尺寸的圓餅圖。尺寸單位為點（1 pt ≈ 1/72 in）。

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

此時圖表尚未有資料，但佔位已經寫入文件。你已成功 **將圓餅圖加入 Word**，且全程程式化。

---

## 步驟 4：為圖表填入資料

圓餅圖至少需要一組數值。以下示範將一些代表市場佔有率的樣本資料寫入圖表。

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

若日後需要多組系列（堆疊圓餅、甜甜圈等），只要呼叫 `pieChart.getSeries().add()` 並重複上述步驟。相同的邏輯同樣適用於 **在圖表上顯示百分比** 的設定。

---

## 步驟 5：**add data label percent** – 在切片上顯示百分比

這是大多數開發者容易遺忘的環節：設定資料標籤顯示百分比。若不這麼做，圖表只會顯示原始數字，容易產生歧義。

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

`setShowPercent(true)` 會指示 Aspose.Words 把標籤渲染為「30 %」、「45 %」等。這正是 **在圓餅圖上顯示百分比** 而不需額外格式化的方式。

---

## 步驟 6：儲存文件

最後，將文件寫入磁碟。你可以選擇 `.docx`、`.pdf`，甚至 `.html`。本教學以現代的 `.docx` 為例。

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

執行程式後，開啟 `PieChartDemo.docx`，即可看到每個切片都帶有百分比標籤的精美圓餅圖。

---

## 預期輸出

以下為產生的 Word 檔案截圖。可見每個切片皆以百分比顯示——正是我們在設定 **add data label percent** 時所期待的結果。

![Screenshot of a Word document containing a pie chart with percentage labels](/images/pie-chart-percent.png){.center width=600px alt="顯示如何在 Word 中插入圓餅圖並加上百分比標籤的螢幕截圖"}

*Alt 文字已包含主要關鍵字，兼顧 SEO 與可及性。*

---

## 常見問題與特殊情境處理

| 問題 | 解答 |
|----------|--------|
| **可以變更百分比標籤的字型嗎？** | 可以。啟用 `setShowPercent(true)` 後，取得 `DataLabel` 物件並調整其 `Font` 屬性（例如 `dataLabel.getFont().setSize(10);`）。 |
| **如果需要甜甜圈圖而不是圓餅圖，該怎麼做？** | 在 `insertChart` 呼叫中將 `ChartType.PIE` 改為 `ChartType.DOUGHNUT`。相同的 **add data label percent** 邏輯仍然適用。 |
| **舊版 Word（2007‑2010）會正確顯示百分比嗎？** | Aspose.Words 以版本無關的方式寫入底層 XML，凡支援圖表的 Word（2007 以上）皆會正確顯示百分比。 |
| **如何為圖表加入標題？** | 在儲存前呼叫 `pieChart.getTitle().setText("Market Share");` 即可。 |
| **能否將圖表插入特定段落或表格儲存格？** | 完全可以。於呼叫 `insertChart` 前，先將 `DocumentBuilder` 移至目標位置（`builder.moveToParagraph(index, true);` 或 `builder.moveToCell(table, row, column, true);`）。 |

---

## 現場技巧與小竅門

- **專業小技巧：** 若需在迴圈中大量產生圖表，請重複使用同一個 `DocumentBuilder` 實例，可減少記憶體開銷。
- **注意事項：** 切片過小（< 2 %）時，Aspose.Words 可能會自動隱藏標籤以免雜亂；可透過 `dataLabel.setShowLabel(true);` 強制顯示。
- **效能說明：** 圖表渲染相當耗 CPU。大量報表產生時，可考慮多執行緒，但每個執行緒必須使用獨立的 `Document` 實例。
- **版本檢查：** `setShowPercent` 方法於 Aspose.Words 22.8 版首次推出。若使用較舊版本，請升級或自行計算百分比並以自訂標籤方式設定。

---

## 重點回顧

我們已說明 **如何在 Word 中插入圓餅圖**，示範了 **add data label percent** 的設定，並展示了 **在圖表上顯示百分比** 的最簡單做法。只要幾行 Java 程式碼，即可 **將圓餅圖加入 Word** 並 **在圓餅圖上顯示百分比**，讓原始數字瞬間變成易讀的視覺資訊。

---

## 接下來可以做什麼？

- 嘗試其他圖表類型（`BAR`、`LINE`、`AREA`），觀察相同的 **add data label percent** 邏輯如何套用。
- 將圖表與表格結合，打造更豐富的報表——Aspose.Words 讓圖表與資料表的佈局變得輕而易舉。
- 試著將同一份文件匯出為 PDF 或 HTML，觀察百分比在不同格式下的呈現效果。

隨意調整尺寸、顏色或資料來源（例如資料庫查詢），讓你的 Word 報表活起來。若遇到問題，歡迎在下方留言——祝你圖表順利！

## 接下來該學什麼？

以下教學與本篇內容緊密相關，能進一步深化你對 API 的掌握，並探索在專案中實作的其他方式。

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}