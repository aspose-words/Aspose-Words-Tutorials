---
category: general
date: 2026-08-14
description: 使用 Java 及 Aspose.Words 在 Word 中建立圓餅圖。學習如何向圖表加入系列資料，並僅用幾行程式碼即可旋轉圓餅圖切片。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: zh-hant
lastmod: 2026-08-14
og_description: 使用 Aspose.Words 於 Word 中以 Java 建立圓餅圖。本教學示範如何快速加入系列資料至圖表，並旋轉圓餅圖切片。
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: 在 Word 中使用 Java 建立圓餅圖 – 完整程式碼指南
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: 使用 Java 在 Word 中建立圓餅圖 – 逐步指南
url: /zh-hant/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 Java 建立圓餅圖 – 步驟指南

如果您需要以程式方式 **在 Word 中建立圓餅圖**，本指南將向您展示如何使用 Java 和 Aspose.Words 完成。您將學習完整的工作流程，從插入圖表、加入資料點到旋轉第一個切片。

直接在 `.docx` 檔案中產生圖表可省去手動複製貼上的步驟，讓您能自動化報告、發票或儀表板。在此過程中，我們亦會說明 **如何將系列資料加入圖表** 以及 **如何旋轉圓餅圖切片** 以加強視覺強調。

## 在 Word 中建立圓餅圖 – 概觀

Aspose.Words for Java 提供流暢的 `DocumentBuilder` API，可將圖表物件插入 Word 文件。您選擇的圖表類型決定預設版面，且您可以自訂系列、顏色、角度，甚至只需一次方法呼叫即可切換為甜甜圈形狀。

### 為何使用 Aspose.Words？

* **No Microsoft Office required** – 此函式庫可在任何伺服器或 CI 環境中運作。  
* **Full .docx fidelity** – 產生的圖表與手動在 Word 中建立的完全相同。  
* **Single‑file dependency** – 只需加入 JAR 檔，即可使用。

## 如何將系列資料加入圖表

沒有資料的圖表僅是佔位符。`Chart` 物件提供 `Series` 集合；每個系列包含一系列數值，對應到切片（圓餅圖）或點（折線圖）。加入資料相當簡單：

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**程式碼功能說明：**  
* `chart.getSeries()` 會回傳 `List<ChartSeries>`。  
* `get(0)` 取得第一個系列，因為圓餅圖依定義僅有一個系列。  
* `add(double)` 會加入一個資料點。這些值會自動轉換為百分比，且在圖表呈現時總和為 100 %。  

> **專業提示：** 若資料來源包含超過三個類別，請以相同方式持續加入值。Aspose.Words 會自動產生額外的切片。

## 旋轉圓餅圖切片

有時您希望特定切片從特定角度開始，以便最重要的區段面向觀眾。`setFirstSliceAngle(double)` 方法會旋轉整個圖表，實際上是移動第一個切片的起始位置：

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

角度以順時針方向、相對於垂直軸的度數來測量。將其設為 `0`（預設值）會將第一個切片置於頂部。調整此值即可突顯特定切片或符合設計指引。

> **常見問題：** *旋轉會影響資料順序嗎？*  
> 不會。資料順序保持不變，僅視覺上的起始位置會改變。

## 完整 Java 範例

以下是一個完整、可直接執行的程式，會建立含圓餅圖的 Word 文件、加入系列資料、旋轉切片，並儲存檔案。已列出所有必要的匯入，您可將程式碼複製到任何 IDE 中使用。

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### 預期輸出

* 於 `output` 資料夾中產生名為 **PieChart.docx** 的檔案。  
* 在 Microsoft Word 中開啟該檔案，可看到一個彩色圓餅圖，包含三個切片（40 %、30 %、30 %）。  
* 圖表順時針旋轉 45°，因此第一個切片略微位於垂直軸的右側。

## 常見陷阱與最佳實踐

| 問題 | 發生原因 | 解決方法 |
|-------|----------------|-----|
| **圖表顯示空白** | 文件在圖表完全呈現之前就已儲存。 | 在所有圖表修改之後再呼叫 `doc.save()`。 |
| **切片值未加總至 100 %** | 加入未代表百分比的原始數字可能導致比例異常。 | 提供能合理代表整體比例的數值，或讓 Aspose.Words 自動計算百分比。 |
| **旋轉無效** | 使用 `ChartType.DOUGHNUT` 且未設定 `holeSize` 可能會隱藏旋轉效果。 | 將圖表保留為 `PIE`，或在設定角度後調整 `holeSize`。 |
| **檔案路徑錯誤** | 相對路徑在 Windows 與 Linux 上的解析方式可能不同。 | 在正式程式碼中使用 `Paths.get("output", "PieChart.docx").toString()` 或絕對路徑。 |

### 生產環境使用技巧

* **重複使用 `DocumentBuilder`** – 只要重複呼叫 `insertChart`，即可在同一文件中插入多個圖表。  
* **樣式設定** – 使用 `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` 可直接在圖表上顯示百分比。  
* **效能** – 若需在多處使用相同圖表，可先產生一次後使用 `chart.deepClone()` 進行複製。  

## 旋轉圓餅圖切片 – 進階情境

* **動態角度** – 根據資料計算角度（例如，讓最大切片從頂部開始）。  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **多系列** – 雖然圓餅圖通常只有一個系列，Aspose.Words 允許您加入更多系列以形成堆疊圓餅圖。旋轉仍僅套用於第一個系列。

## 結論

現在您已了解如何使用 Java **在 Word 中建立圓餅圖**、如何 **將系列資料加入圖表**，以及如何 **旋轉圓餅圖切片** 以加強視覺效果。完整範例示範了整個工作流程——從文件初始化到儲存最終的 `.docx` 檔案——讓您能將圖表產生整合至任何自動化報告流程中。

### 接下來該做什麼？

* 探索其他圖表類型（`ChartType.BAR`、`ChartType.LINE`），以擴充自動化工具箱。  
* 結合圖表產生與 **mail merge**，為每位收件者產生個人化報告。  
* 深入了解 **Styling API**（`ChartFormat`、`DataLabel`、`ChartTitle`），以符合企業品牌形象。

歡迎嘗試不同的資料集、角度與圖表樣式。祝開發愉快！

## 接下來應該學什麼？

以下教學涵蓋與本指南技術密切相關的主題，並在此基礎上延伸。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [如何使用 Aspose.Words for Java 建立柱狀圖](/words/english/java/document-conversion-and-export/using-charts/)
- [如何使用 DocumentBuilder 在 Aspose.Words for Java 中建立表單欄位並加入內容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [如何使用 Aspose.Words for Java 將 Word 轉換為 PDF](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}