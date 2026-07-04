---
category: general
date: 2026-06-02
description: 使用 C# 在 Word 文件中顯示圖表圖例。學習如何加入圖例、套用預設圖表樣式，並在幾分鐘內自訂 Word 圖表的視覺效果。
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: zh-hant
og_description: 即時在 Word 文件中顯示圖表圖例。本指南將逐步說明如何加入圖例、套用預設圖表樣式，以及處理例外情況。
og_title: 在 Word 中顯示圖表圖例 – 完整 C# 教學
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: 使用 C# 在 Word 中顯示圖表圖例 – 完整逐步指南
url: /zh-hant/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中顯示圖表圖例（C#） – 完整步驟指南

有沒有想過 **如何在 Word 文件中的圖表加入圖例**？你並不是唯一的疑問者。在許多報告中，缺少圖例會讓資料看起來難以理解，而解決這個問題不應該是個頭痛的事。  

在本教學中，我們將使用 Aspose.Words for .NET **在 Word 檔案中顯示圖表圖例**，套用預設圖表樣式，並確保圖例出現在您需要的位置。完成後，您將擁有一個可直接執行的範例，隨時可放入任何 C# 專案中。

## 本指南涵蓋內容

我們將逐步說明整個工作流程：

1. 載入已包含圖表的現有 *.docx* 檔案。  
2. 取得第一個圖表（或您想要的任何圖表）。  
3. **套用預設圖表樣式**，讓視覺效果更具專業感。  
4. **顯示圖表圖例**，將其定位於右側，並處理如 Waterfall 圖表等特殊情況。  
5. 儲存已修改的文件。

不需要外部工具，也不必手動操作 UI——只需純程式碼。唯一的先決條件是參考 Aspose.Words NuGet 套件（版本 23.10 或更新）以及對 C# 的基本了解。

## 前置條件

- .NET 6.0 或更新版本（此範例亦支援 .NET Framework 4.7.2）。  
- 已安裝 Aspose.Words for .NET 函式庫（`Install-Package Aspose.Words`）。  
- 一個已包含至少一個圖表的 Word 檔案（`input.docx`）。  
- Visual Studio、Rider，或您偏好的任何 IDE。

## 步驟 1：設定專案並載入文件

首先，建立一個 console 應用程式（或將程式碼整合到現有專案中）。加入 `using` 指令並載入 `.docx` 檔案。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **為何重要：** 載入文件是基礎。若沒有 `Document` 實例，就無法存取 Aspose.Words 所提供的圖表物件。

## 步驟 2：取得目標圖表

圖表以節點形式儲存在文件樹中。`GetChild` 方法會進行深度搜尋，讓我們能取得第一個圖表，無論它位於頁首、正文、頁腳等位置。

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **提示：** 若有多個圖表，請將索引 `0` 改為 `1`、`2`…，或遍歷 `doc.GetChildNodes(NodeType.Chart, true)`。

## 步驟 3：套用預設視覺樣式

美觀的圖表通常從樣式開始。Aspose.Words 內建數十種樣式；`ChartStyle.Style12` 是一個簡潔、現代的選擇。

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **運作方式：** `Style` 屬性對應於 UI 中可見的內建 Word 圖表樣式。選擇預設樣式可免除手動設定顏色、字型與標記的工作。

## 步驟 4：啟用圖例並設定位置

現在來到重點——**顯示圖表圖例**。我們先開啟圖例，然後將其停靠在圖表的右側。

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **為何放右側？** 將圖例放在右側可保留較寬的資料區域，對於長條圖或柱狀圖特別有幫助。

## 步驟 5：處理瀑布圖（特殊情況）

瀑布圖的行為稍有不同；圖例預設可能被隱藏。以下的防護條件可確保當圖表類型為 Waterfall 時圖例會顯示。

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **邊緣案例說明：** 某些較舊的 Word 版本會忽略 Waterfall 圖表的 `HasLegend`，因此明確設定 `Legend.Show` 可保證圖例可見。

## 步驟 6：儲存已修改的文件

最後，將變更寫回磁碟。您可以覆寫原始檔案或建立新檔案。

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

執行程式後會產生 `output.docx`，其右側顯示圖例，且使用 `Style12` 風格。請在 Word 中開啟檔案以驗證結果。

## 完整範例（結合所有步驟）

以下是完整、可直接執行的程式碼。將其複製貼上至 `Program.cs`（或任何 C# 檔案），並調整檔案路徑。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**預期輸出：** 開啟 `output.docx` 後，您會看到原始圖表帶有右對齊的圖例，使用現代的 `Style12` 風格。所有資料系列均清楚標示，使圖表一目了然。

## 常見問題 (FAQ)

### 如何為特定圖表（而非第一個）加入圖例？

將 `GetChild(NodeType.Chart, 0, true)` 中的 `0` 索引改為目標圖表的零基位置，或遍歷所有圖表節點：

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### 可以將圖例放在底部而非右側嗎？

當然可以。只要變更 `LegendPosition` 列舉即可：

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### 如果圖表已經有圖例，但我想隱藏它該怎麼辦？

將 `HasLegend` 設為 `false`：

```csharp
chart.HasLegend = false;
```

### 這在 Word 2010、2016 以及之後的版本都適用嗎？

是的。Aspose.Words 抽象化了底層的 Word 版本，因此相同程式碼可在所有現代 .docx 檔案中運作。

## 專業提示與常見陷阱

- **專業提示：** 套用樣式後，仍可透過 `Chart.Series` 集合微調個別元素（顏色、資料標籤）。樣式提供了堅實的基礎。  
- **注意事項：** 若圖表位於表格儲存格內，圖例可能會顯得擁擠。建議在定位圖例前先增大圖表尺寸（`chart.Width`、`chart.Height`）。  
- **效能說明：** 載入大型文件（數百 MB）可能佔用大量記憶體。若僅需操作圖表，可使用 `LoadOptions` 搭配 `LoadFormat.Docx` 以降低開銷。

## 往後步驟

既然您已了解如何 **在 Word 中加入圖例** 以及 **套用預設圖表樣式**，接下來可以探索：

- **自訂圖表顏色**（`chart.Series[i].Format.Fill.ForeColor`）。  
- **資料標籤格式化**（`chart.Series[i].HasDataLabel = true`）。  
- **將圖表匯出為影像**（`chart.ToImage()`），便於在其他地方嵌入。  

上述主題皆基於相同的物件模型，學習曲線相當平緩。

## 結論

我們剛剛示範了一個完整、乾淨的解決方案，使用 C# 在 Word 文件中 **顯示圖表圖例**。透過載入文件、取得圖表、套用預設樣式、啟用圖例，並處理 Waterfall 的特殊情況，您即可得到一個已完成美化的圖表，適用於任何商業報告。  

隨意嘗試其他 `ChartStyle` 值或圖例位置——您的資料視覺化值得最佳呈現。如遇任何問題，歡迎在下方留言；祝編程愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南技術密切相關的主題，並以完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}