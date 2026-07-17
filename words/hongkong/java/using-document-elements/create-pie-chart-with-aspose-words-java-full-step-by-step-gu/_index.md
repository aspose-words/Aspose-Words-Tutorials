---
category: general
date: 2026-07-16
description: 使用 Aspose.Words 在 Java 中建立圓餅圖。學習如何加入指示線、顯示圖例，以及在單一教學中將切片突出顯示。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: zh-hant
lastmod: 2026-07-16
og_description: 使用 Aspose.Words 在 Java 中建立圓餅圖。本指南示範如何加入指示線、顯示圖例以及將切片分離，讓您在數分鐘內即可獲得精緻的視覺效果。
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: 使用 Aspose.Words Java 建立圓餅圖 – 完整格式化教學
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: 使用 Aspose.Words Java 建立圓餅圖 – 完整逐步指南
url: /zh-hant/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words Java 建立圓餅圖 – 完整逐步指南

有沒有想過在 Java 中 **程式化建立圓餅圖**，卻不想與低階繪圖 API 纏鬥？你並不是唯一有這個需求的人。許多開發者需要快速的視覺報表、儀表板或自動化文件，而他們會選擇 Aspose.Words，因為它已幫你處理好繁雜的工作。

在本教學中，我們將一步步示範一個完整、可直接執行的範例，不僅 **建立圓餅圖**，還會示範如何 **加入引線**、**顯示圖例**，甚至 **將切片突出顯示** 以強調重點。完成後，你會得到一個 `.docx` 檔案，外觀足以讓客戶印象深刻。

> **快速上手：** 以下程式碼片段可直接在 Aspose.Words for Java 23.9（或更新版本）上執行。無需額外相依，只要加入 JAR 即可。

## 你將學到

- 使用 `DocumentBuilder` 建立空白 Word 文件。
- 插入自訂尺寸的 **圓餅圖**。
- 使用 **突出切片** 功能強調特定資料點。
- 啟用 **引線**，讓突出切片仍與標籤相連。
- 開啟 **圖例**，讓讀者立即辨識每一切片。
- 將結果儲存為 `.docx`，可於 Microsoft Word 或 LibreOffice 開啟。

**先備條件** – 你需要：

1. 已安裝 Java 17（或更新版本）。
2. 將 Aspose.Words for Java JAR 加入 classpath。
3. 任一基本 IDE 或文字編輯器——IntelliJ IDEA、Eclipse、VS Code，隨你喜好。

現在，讓我們開始吧。

## 第一步：初始化 Document 與 Builder – 準備 **建立圓餅圖**

首先，我們需要一個乾淨的文件畫布。`Document` 代表整個 Word 檔案，而 `DocumentBuilder` 則是協助我們加入內容的工具。

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **為什麼重要：** 從全新 `Document` 開始，可保證沒有隱藏樣式或遺留物件干擾圖表渲染。

## 第二步：插入 **圓餅圖** – 大小很重要

Aspose.Words 只需一行程式碼即可插入圖表。這裡我們要求的圓餅圖尺寸為 400 × 300 點——大約相當於 5.5 × 4.2 吋的螢幕顯示大小。

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **小技巧：** 若需要不同尺寸，只要更改兩個數字參數即可。API 使用點作單位，1 英吋 = 72 點。

## 第三步：**如何突出切片** – 強調關鍵資料點

將切片突出會把它從餅圖中拉出，吸引讀者目光。`setExplosion` 方法接受一個整數，代表以點為單位的距離。

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **如果有多個系列呢？** 只要在任意系列索引（`get(1)`、`get(2)` …）上呼叫 `setExplosion`，即可突出不同切片。

## 第四步：**加入引線** 與 **顯示圖例** – 連接資訊

當切片被突出時，標籤可能會漂離。引線可將標籤固定，保持可讀性。同時，圖例提供所有切片的快速對照鍵。

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **為什麼要啟用引線？** 若未啟用，引線可能會缺失，導致使用者不清楚標籤屬於哪個切片。  
> **需要自訂圖例位置？** 使用 `chart.getLegend().setPosition(LegendPosition.TOP)` 或其他 enum 值即可。

## 第五步：儲存文件 – 最後的 **建立圓餅圖** 步驟

最後，我們將文件寫入磁碟。請自行調整路徑至有寫入權限的資料夾。

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

執行程式後，開啟產生的 `PieChartDemo.docx`，你應該會看到一個格式良好的圓餅圖，第一切片已被突出，且帶有引線與可見圖例。

![顯示突出切片與圖例的圓餅圖範例](pie-chart-example.png){: .center-image alt="建立圓餅圖範例（含突出切片、引線與圖例）"}

### 預期輸出

開啟 Word 檔案時，圖表大致呈現如下：

- 400 × 300 點的圓餅圖。
- 第一切片偏移 10 點。
- 細線引線連接突出切片與其標籤。
- 圖例位於圖表下方，列出每個系列名稱。

若未看到引線，請再次確認 `setLeaderLines(true)` 已在 **設定突出** 之後呼叫——呼叫順序很重要。

## 常見問題與避免方式

| 問題 | 為何會發生 | 解決方式 |
|------|------------|----------|
| **圖例未出現** | 忘記呼叫 `setShowLegend(true)`，或在錯誤的圖表物件上呼叫。 | 確保在取得 `Chart` 後 **呼叫** `chart.setShowLegend(true)` **且在最後**。 |
| **引線缺失** | 切片未被突出，或圖表類型不支援引線。 | 只有 `ChartType.PIE`（或 `PIE_3D`）支援引線。先呼叫 `setExplosion`，再呼叫 `setLeaderLines(true)`。 |
| **切片未移動** | 爆炸值太小（0‑2 點）。 | 增加整數值，例如 `setExplosion(10)` 或更大，以取得更明顯效果。 |
| **圖表變形** | 使用非正方形尺寸（寬度 ≠ 高度）會壓扁圓餅。 | 盡量保持寬高相等或相近；400 × 300 可用，但 400 × 400 會得到完美圓形。 |

## 進階調整（可選）

若想更進一步，考慮以下做法：

- **自訂顏色**：`chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **資料標籤**：`chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **3‑D 效果**：將 `ChartType.PIE` 改為 `ChartType.PIE_3D`。

這些選項讓你能依企業品牌指南微調視覺效果。

## 重點回顧 – 我們完成了什麼

我們從空白 Word 文件開始，**建立圓餅圖**、**突出第一切片**、**加入引線**，並 **顯示圖例**。整段流程濃縮於簡潔的 `main` 方法，方便嵌入更大的報表產生流程中。

## 後續建議

- **加入更多系列**：從資料庫或 CSV 讀取真實資料填入圖表。
- **匯出為 PDF**：使用 `doc.save("output.pdf", SaveFormat.PDF);` 產生 PDF 版本。
- **結合其他圖形**：插入表格、圖片或額外圖表，打造完整報告。

如果你對其他圖表類型（柱狀圖、條形圖、折線圖）感興趣，只要將 `ChartType.PIE` 替換為相應的 enum，即可沿用相同步驟。

---

*祝圖表製作愉快！* 如有任何問題或想分享自訂圖例位置的做法，歡迎留言。你的回饋能幫助大家一起打造更好的自動化文件。

## 接下來該學什麼？

以下教學與本篇內容緊密相關，能進一步深化你在本指南中學到的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助你掌握更多 API 功能，並探索在專案中的其他實作方式。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)
- [How to Add Watermark to Documents Using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}