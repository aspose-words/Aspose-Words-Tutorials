---
category: general
date: 2026-09-21
description: 建立空白 Word 文件，學習如何使用 DocumentBuilder 在 Word 檔案中插入雷達圖——一步一步的指南。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: zh-hant
lastmod: 2026-09-21
og_description: 使用 Aspose.Words 建立空白 Word 文件並在其中插入雷達圖。遵循本教學，即可快速產生 Word 文件圖表。
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: 建立空白 Word 文件並加入雷達圖 – 完整 C# 教學
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: 如何在 C# 中建立空白 Word 文件並加入雷達圖
url: /zh-hant/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中建立空白 Word 文件並加入雷達圖表

如果您需要 **建立空白 Word 文件** 並嵌入雷達（徑向）圖表，本教學提供即用的解決方案。您將看到如何使用 Aspose.Words .NET 產生檔案、插入圖表，並儲存結果——只需幾個簡潔步驟。

空白文件提供了乾淨的畫布，適用於任何自動化報表情境；加入雷達圖表則能直接在 Word 中視覺化多維度資料。完成本指南後，您即可在不需手動編輯的情況下產生帶圖表的 Word 文件。

## 您將學會

* 如何使用 C# 程式化 **建立空白 Word 文件**。
* 使用 `DocumentBuilder` **插入雷達圖表** 的完整程式碼。
* 如何 **在 Word 檔案中插入圖表** 並自訂其大小。
* 如何 **產生 Word 文件圖表** 並驗證輸出。
* 關於 **在 Word 中加入徑向圖表** 檔案的技巧，包括常見陷阱。

### 前置條件

* .NET 6.0 或更新版本（程式碼亦相容 .NET Framework 4.6+）。
* Aspose.Words for .NET（NuGet 套件 `Aspose.Words` 版本 23.9 或更新）。
* 具備 C# 及 Visual Studio 或您偏好的 IDE 的基本知識。

## 使用 C# 建立空白 Word 文件

第一步是實例化一個空的 `Document` 物件。此物件代表一個完全空白的 `.docx` 檔案。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` 只會建立檔案結構，尚未包含任何章節或頁面。當您開始加入內容時，Aspose.Words 會自動新增預設章節，這也是為什麼接下來的步驟不需要額外設定即可運作。

## 如何在 Word 檔案中插入雷達圖表

雷達圖（亦稱徑向圖）會在從中心點放射出的軸上顯示資料點。Aspose.Words 提供 `DocumentBuilder.insertChart` 以完成此任務。

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` 會回傳一個 `Chart` 物件，您可以進一步設定。圖表會出現在空白文件的第一頁，因為建構器預設位於文件開頭。

## 在 Word 檔案中插入圖表 – 加入資料系列

沒有資料的圖表是不可見的。為雷達圖加入一個或多個系列，使其具備意義。

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

您可以依需求加入任意多的系列。每個系列可設定不同的名稱，會顯示在圖例中。資料點對應徑向軸；加入的順序決定它們在圓周上的位置。

## 產生 Word 文件圖表 – 儲存檔案

完成圖表建構後，將文件寫入磁碟。請選擇您具有寫入權限的路徑。

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

當您在 Microsoft Word 中開啟產生的 `.docx` 檔案時，會看到一個大小為 400 × 300 點的雷達圖表，已填入範例資料，且頁面為空白。

### 預期輸出

* 桌面上會產生一個 `RadialChartExample.docx` 檔案。
* 第一頁包含一個雷達圖表，內有五個資料點，標籤為 “Series 1”。
* 不會出現其他文字，因為文件是從空白開始的。

## 加入徑向圖表 – 處理常見邊緣情況

### 1. 插入後變更圖表大小

如果初始尺寸不符合版面需求，可這樣調整圖表大小：

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. 在特定位置插入圖表

在呼叫 `InsertChart` 前，您可以將建構器的游標移至書籤、表格儲存格或段落。

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. 自訂圖表外觀

Aspose.Words 釋出完整的圖表物件模型，讓您可以設定標題、軸標籤與顏色等屬性。

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. 處理缺少字型的情況

若目標環境缺少圖表使用的字型，Aspose.Words 會改用預設字型。為確保一致性，請將所需字型內嵌：

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. 匯出為其他格式

同一文件可直接另存為 PDF、HTML 或 PNG，無需額外程式碼變更：

```csharp
doc.Save("RadialChartExample.pdf");
```

## 完整可執行範例

將所有片段組合起來，即可得到一個可直接複製、貼上並執行的單一程式。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

執行此程式，開啟產生的檔案，您將看到一個專業的雷達圖表，已可供發佈使用。

## 結論

您現在已掌握如何 **建立空白 Word 文件**、**插入雷達圖表**，以及使用 Aspose.Words **產生 Word 文件圖表**。依照上述步驟，您亦可 **在 Word 中加入徑向圖表** 檔案至任何自動化報表流程，並自訂尺寸、樣式，甚至匯出為其他格式。

**Next steps**

* 探索其他圖表類型（`ChartType.Column`、`ChartType.Pie`），擴充您的報表工具箱。
* 透過多次呼叫 `InsertChart`，在同一頁面上結合多個圖表。
* 從資料庫或 CSV 檔案整合資料，動態填充系列。
* 查閱 Aspose.Words 文件，了解進階格式設定，如條件資料標籤與圖表範本。

歡迎自行實驗程式碼、調整尺寸，或以真實業務指標取代範例資料。祝開發愉快！

## 您接下來應該學習什麼？

以下教學涵蓋與本指南技術緊密相關的主題，並提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [在 Word 中使用 Aspose.Words for .NET 插入柱狀圖](/words/english/net/working-with-charts/insert-column-chart/)
- [使用 Aspose.Words for .NET 建立 Word 散點圖](/words/english/net/working-with-charts/insert-scatter-chart/)
- [在 Word 中使用 Aspose.Words for .NET 插入氣泡圖](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}