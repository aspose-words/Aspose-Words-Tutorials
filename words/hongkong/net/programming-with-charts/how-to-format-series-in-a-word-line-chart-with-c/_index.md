---
category: general
date: 2026-09-21
description: 如何使用 C# 為 Word 折線圖的資料系列設定格式。學習建立 Word 文件、插入折線圖，並套用自訂數字格式。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: zh-hant
lastmod: 2026-09-21
og_description: 如何使用 C# 在 Word 折線圖中設定系列格式。本教學將示範如何建立 Word 文件、插入折線圖，並套用自訂數字格式。
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: 如何使用 C# 在 Word 折線圖中格式化系列 – 步驟說明指南
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: 如何使用 C# 在 Word 折線圖中格式化系列
url: /zh-hant/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 折線圖中格式化系列（使用 C#）

如果你需要 **如何格式化系列** 在 Word 折線圖中，本指南提供完整、可直接執行的解決方案。你將會看到如何 **建立 Word 文件**、**插入折線圖**，以及 **對 Y 軸數值套用自訂數字格式**——全部使用 Aspose.Words for .NET。

只要了解圖表物件模型，Word 自動化就變得相當簡單。完成本教學後，你將得到一個 Word 檔案，內含折線圖，且資料系列以兩位小數的百分比顯示。

## 你將會達成的目標

* 以程式方式產生空白的 `.docx` 檔案。  
* 新增大小為 400 × 300 點的折線圖。  
* 取得圖表的第一個資料系列。  
* 套用格式碼 `#,##0.00%`，讓 Y 軸數值以百分比顯示。  

不需要任何外部工具，只要安裝 Aspose.Words NuGet 套件即可。

## 前置條件

* .NET 6.0 SDK 或更新版本。  
* Visual Studio 2022（或任何 C# IDE）。  
* Aspose.Words for .NET 23.10 或更新版本 – 透過 `dotnet add package Aspose.Words` 安裝。  

此程式碼可在 Windows、Linux 與 macOS 上執行，因為 Aspose.Words 為跨平台套件。

## 使用 Aspose.Words 建立 Word 文件

第一步是實例化 `Document` 物件。此物件代表整個 Word 檔案於記憶體中的表示。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*為什麼這很重要*：`Document` 是所有 Word 處理操作的入口點。沒有它，你無法加入段落、表格或圖表。

## 在文件中插入折線圖

`DocumentBuilder` 用來將內容寫入 `Document`。呼叫 `InsertChart` 會在目前頁面建立圖表形狀。

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*為什麼這很重要*：`InsertChart` 會回傳一個 `Chart` 物件，讓你完整控制系列、座標軸與格式。尺寸參數以點為單位（1 點 = 1/72 英吋）。

## 取得第一個資料系列

每個圖表都包含一個或多個 `ChartSeries`。第一個系列的索引為 0。

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*為什麼這很重要*：`ChartSeries` 物件保存了 Y 軸數值、X 軸數值以及單條折線的格式設定。修改此物件即可改變資料的視覺呈現。

## 為系列套用自訂數字格式

`FormatCode` 屬性決定數值的顯示方式。將其設定為 `#,##0.00%`，即可讓 Word 將數值視為保留兩位小數的百分比。

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*為什麼這很重要*：若未使用自訂格式，Word 只會顯示原始小數（例如 `0.15`）。此格式碼會將其轉換為 `15.00%`，這正是商業報表常見的需求。

## 儲存文件並驗證結果

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

當你在 Microsoft Word 中開啟 `FormattedSeriesLineChart.docx` 時，會看到折線圖的 Y 軸標籤分別為 `15.00%`、`30.00%`、`45.00%` 與 `60.00%`。圖表尺寸亦符合 `InsertChart` 所指定的大小。

### 預期輸出截圖

> *圖片：顯示折線圖且 Y 軸數值已以百分比格式化的 Word 文件頁面。*  
> *(替代文字：顯示折線圖且 Y 軸數值已以百分比格式化的 Word 文件截圖)*

## 常見變化與例外情況

| 情境 | 調整方式 |
|-----------|------------|
| **多個系列** | 迭代 `chart.Series`，為每個系列設定 `FormatCode`。 |
| **不同圖表類型** | 將 `ChartType.Line` 改為 `ChartType.Column`、`ChartType.Pie` 等。 |
| **在地化分隔符** | 使用 `CultureInfo` 感知的格式字串，例如法語地區的 `"# ##0,00 %"`。 |
| **動態資料來源** | 在套用格式前，先從資料庫或 CSV 檔案填入 `series.YValues`。 |

**小技巧**：請務必在加入 Y 軸數值之後再套用格式。先套用格式再加入數值亦可行，但稍後套用可確保格式套用至最終資料集。

## 重點回顧

你現在已掌握 **如何在 Word 折線圖中格式化系列**（使用 C#）。本教學涵蓋：

* 建立 Word 文件（`create word document`）。  
* 插入折線圖（`insert line chart`、`add chart to word`）。  
* 取得圖表的第一個系列。  
* 套用自訂數字格式（`apply custom number format`）以顯示百分比。

## 往後的步驟

* 嘗試不同的 `ChartType` 值，觀察其他視覺化效果。  
* 使用 `chart.Title`、`chart.AxisX.Title`、`chart.AxisY.Title` 加入標題、座標軸標籤與圖例。  
* 以 `chart.Save` 搭配 `SaveFormat.Png` 將圖表匯出為影像，供網頁報告使用。

歡迎將此模式套用於產生儀表板、財務報表或任何需要程式化圖表的文件。祝開發順利！

## 接下來該學什麼？

以下教學與本指南緊密相關，能進一步深化你所學的技巧。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你掌握更多 API 功能，並探索在專案中實作的其他方式。

- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}