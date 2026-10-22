---
category: general
date: 2026-09-21
description: 如何使用 Aspose.Words 在 Word 中建立直方圖。了解如何設定直方圖分箱及配置分箱，以實現精準的數據視覺化。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create histogram in word
- how to set histogram bins
- configure histogram bins
language: zh-hant
lastmod: 2026-09-21
og_description: 如何使用 Aspose.Words 在 Word 中建立直方圖。本教學將示範如何設定直方圖分箱以及配置分箱，以獲得精確的圖表。
og_image_alt: Screenshot of a Word document showing a histogram chart created with
  Aspose.Words
og_title: 使用 Aspose.Words 在 Word 中建立直方圖 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  headline: How to create histogram in Word with Aspose.Words
  type: TechArticle
- description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  name: How to create histogram in Word with Aspose.Words
  steps:
  - name: Prepare the development environment.
    text: Prepare the development environment.
  - name: Build a blank Word document and obtain a `DocumentBuilder`.
    text: Build a blank Word document and obtain a `DocumentBuilder`.
  - name: Insert a histogram chart and adjust its properties.
    text: Insert a histogram chart and adjust its properties.
  - name: Save the document and verify the result.
    text: Save the document and verify the result.
  type: HowTo
tags:
- histogram
- Aspose.Words
- C#
- Word automation
title: 如何使用 Aspose.Words 在 Word 中建立直方圖
url: /zh-hant/net/programming-with-charts/how-to-create-histogram-in-word-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words 在 Word 中建立直方圖

如果您需要在 Word 中建立直方圖，Aspose.Words 讓此過程變得簡單。 本指南將逐步說明從設定專案到配置直方圖分箱以清晰呈現資料的每個步驟。 您亦會看到如何設定直方圖分箱以及如何配置分箱以符合報告需求。

## 如何在 Word 中建立直方圖 – 整體工作流程

整體工作流程包含四個邏輯階段：

1. 準備開發環境。  
2. 建立空白 Word 文件並取得 `DocumentBuilder`。  
3. 插入直方圖圖表並調整其屬性。  
4. 儲存文件並驗證結果。

每個階段在下方都有詳細說明，完整原始碼則放在文章結尾。

## 設定開發環境

在撰寫任何程式碼之前，請確保您具備以下前置條件：

| 前置條件 | 原因 |
|--------------|--------|
| .NET 6.0 or later | 提供 C# 專案的執行環境。 |
| Visual Studio 2022（或任何支援 .NET 的 IDE） | 讓您能編譯並偵錯範例。 |
| Aspose.Words for .NET NuGet package | 提供 `Document`、`DocumentBuilder` 以及圖表類別。 |

您可以使用 NuGet CLI 加入 Aspose.Words 套件：

```bash
dotnet add package Aspose.Words
```

> **專業提示：** 在正式環境中使用固定版本（例如 `23.9.0`），以避免意外的破壞性變更。

## 插入直方圖圖表

環境就緒後，建立一個新的主控台專案並開啟 `Program.cs` 檔案。前兩行程式碼會實例化一個空白文件與一個可操作文件的 `DocumentBuilder`：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank document and a DocumentBuilder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

接著，呼叫 `InsertChart` 以加入直方圖。此方法需要圖表類型、寬度與高度（以點為單位）：

```csharp
// Insert a histogram chart with a specific size (400x300 points)
Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);
```

此時文件已包含一個空的直方圖佔位符。開啟產生的 *.docx* 檔案時，您會看到一個灰色的圖表區域，已準備好接受資料。

![Histogram placeholder in Word document](/images/histogram-placeholder.png){: .img-fluid alt="使用 Aspose.Words 建立的 Word 文件中顯示直方圖圖表佔位符的螢幕截圖"}

## 如何設定直方圖分箱

直方圖透過將數值資料分組為 *分箱* 來視覺化分佈。`HistogramBins` 屬性控制圖表顯示的分箱數量。於加入資料前先設定此屬性，可確保圖表保留正確的條形數量。

```csharp
// Set the number of bins (bars) in the histogram
histogram.HistogramBins = 10;
```

您可以調整分箱數以符合資料集的粒度。例如，資料範圍為 0 至 100，分箱數為 10 時，會產生每 10 單位的區間 (0‑9、10‑19、…、90‑100)。

> **為何重要：** 選擇過少的分箱會隱藏重要模式，而過多的分箱可能產生雜訊圖表。測試幾個不同的值，以找出最適合您資料的分箱數量。

## 配置直方圖分箱以提升可讀性

除了分箱數量外，您通常也會想為每個分箱加上標籤，讓讀者能看到確切的計數。`ShowBinLabels` 屬性可切換這些標籤的可見性：

```csharp
// Display the value of each bin on the chart
histogram.ShowBinLabels = true;
```

當 `ShowBinLabels` 設為 `true` 時，Word 會在每條柱子上方顯示數字標籤。這個小設定步驟大幅提升圖表的可解讀性，特別是在讀者可能無法取得原始資料集的報告中。

您亦可透過 `HistogramLabel` 物件（在較新版本的 Aspose.Words 中提供）自訂標籤外觀，例如字型大小或顏色。以下程式碼示範常見的調整：

```csharp
// Optional: make bin labels bold and increase font size
histogram.HistogramLabel.Font.Size = 10;
histogram.HistogramLabel.Font.Bold = true;
```

> **邊緣情況：** 若將 `HistogramBins` 設為大於不同資料點數量的值，某些分箱會顯示為空。圖表仍會正確呈現，但視覺上可能顯得稀疏。此時請考慮減少分箱數量。

## 為直方圖加入資料系列

直方圖需要單一資料系列來代表底層的數值。您可以使用陣列、`List<double>` 或任何可列舉的集合來填充系列。以下是一個簡潔範例，加入隨機資料集：

```csharp
// Create a data series for the histogram
ChartSeries series = histogram.Series[0];
double[] sampleData = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
series.DataPoints.AddRange(sampleData);
```

`AddRange` 方法會依先前定義的 `HistogramBins` 將每個值轉換為相應的分箱。完成此步驟後，圖表即會顯示完整的直方圖。

## 儲存並檢視產生的文件

最後，將文件寫入磁碟。您可以選擇任何應用程式可存取的位置。以下程式碼將檔案儲存為 `output.docx`：

```csharp
// Save the document so you can view the chart
doc.Save("output.docx");
```

在 Microsoft Word 中開啟 `output.docx`，即可看到一個包含十個分箱、帶標籤值以及您提供的樣本資料的直方圖。圖表外觀如下圖所示：

![Completed histogram in Word](/images/histogram-complete.png){: .img-fluid alt="Word 文件顯示完成的直方圖圖表，包含十個分箱與標籤"}

## 完整、可執行的範例

將所有片段組合起來，以下是一個可直接複製、貼上並執行的自包含程式：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a histogram chart (400×300 points)
        Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);

        // 3️⃣ Configure the histogram
        histogram.HistogramBins = 10;          // How to set histogram bins
        histogram.ShowBinLabels = true;       // Configure histogram bins to show labels
        histogram.HistogramLabel.Font.Size = 10;
        histogram.HistogramLabel.Font.Bold = true;

        // 4️⃣ Add a data series
        ChartSeries series = histogram.Series[0];
        double[] data = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
        series.DataPoints.AddRange(data);

        // 5️⃣ Save the document
        doc.Save("output.docx");
    }
}
```

**預期輸出：** 開啟 `output.docx` 後會顯示一個包含十條等距條形、每條都有標示計數的直方圖。圖表反映 `data` 陣列的分布，使趨勢一目了然。

## 常見問題與疑難排解

| 問題 | 答案 |
|----------|--------|
| *如果需要多於一個資料系列怎麼辦？* | 直方圖通常只代表單一分布。如果需要多個系列，請考慮改用柱狀圖。 |
| *插入後可以變更圖表大小嗎？* | 可以。調整 `histogram.Width` 與 `histogram.Height` 屬性，或再次呼叫 `builder.InsertChart` 並提供不同尺寸。 |
| *這能在 .NET Framework 4.8 上運作嗎？* | 當然可以。Aspose.Words 支援 .NET Framework 4.5 及以上版本，程式碼可直接執行。 |
| *如何將圖表匯出為影像？* | 使用 `histogram.ToImage()` 取得 `System.Drawing.Image`，再以 `image.Save("chart.png")` 儲存。 |

## 結論

現在您已了解如何使用 Aspose.Words 在 Word 中建立直方圖、如何設定直方圖分箱，以及如何配置分箱以獲得清晰且帶標籤的輸出。完整範例展示了可直接投入生產的做法，您可將其套用於任何資料驅動的報告情境。  

接下來，您可以探索相關主題，例如 **如何在 Word 中建立圓餅圖**、**自訂圖表顏色** 與 **嵌入 Excel 資料來源**。這些皆基於相同的 `DocumentBuilder` 工作流程，讓您能以最小的努力擴充解決方案。

祝您圖表製作愉快！

## 您接下來應該學習什麼？

以下教學涵蓋與本指南技術緊密相關的主題，皆建立在本篇示範的技巧之上。每個資源都包含完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [如何使用 Aspose.Words for Java 建立柱狀圖](/words/english/java/document-conversion-and-export/using-charts/)
- [如何從 Word 建立 PDF – 完整 C# 指南](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [如何使用 Aspose.Words LoadOptions 載入 Word 文件](/words/english/net/programming-with-loadoptions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}