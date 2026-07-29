---
category: general
date: 2026-07-29
description: 如何在 Word 文件中編輯圖表——學習更改圖表標籤位置、調整長條圖標籤、修改圖表資料標籤，以及更改圖表標籤字型。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: zh-hant
lastmod: 2026-07-29
og_description: 快速編輯 Word 圖表。精通更改圖表標籤位置、調整長條圖標籤、修改圖表資料標籤以及更改圖表標籤字型。
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: 如何在 Word 中編輯圖表 – 更改標籤與字型
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 如何在 Word 中編輯圖表：更改標籤位置、字型及其他
url: /zh-hant/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中編輯圖表：變更標籤位置、字型與其他設定

在 Word 文件中編輯圖表是常見需求，尤其當你想讓報告看起來更專業時。是否曾為了 **變更圖表標籤位置** 或讓標籤易於閱讀而在無盡的選單中苦苦尋找？你並不孤單——大多數開發者在自動化報告產生時都會遇到這個問題。本指南將示範一個完整、可執行的範例，教你如何使用 C# 與 Aspose.Words 套件 **調整長條圖標籤**、**修改圖表資料標籤**，以及 **變更圖表標籤字型**。

## 你將學到

- 載入已包含長條圖的 .docx 檔案。  
- 取得第一個圖表 Shape 並存取其資料標籤集合。  
- **變更圖表標籤位置**，讓長條看起來更整潔。  
- **調整長條圖標籤** 的字型大小，以提升可讀性。  
- 將修改後的文件儲存回磁碟。  

不需要外部工具，也不需要手動 UI 操作——只要純程式碼即可直接放入任何 .NET 專案。完成後，你將擁有一套可在多個文件中重複使用的完整解決方案。

> **先決條件**  
> - .NET 6.0 或更新版本（此程式碼亦相容於 .NET Framework 4.7+）。  
> - Aspose.Words for .NET（可透過 NuGet 取得）。  
> - 一個已包含長條圖的 Word 檔案（`BarChart.docx`）。  

如果缺少上述任一項，請立即取得最新的 Aspose.Words 套件：

```bash
dotnet add package Aspose.Words
```

---

## 如何編輯圖表：從 Word 文件中取得圖表

在 **如何編輯圖表** 之前的第一步是載入文件並定位圖表 Shape。Aspose.Words 將圖表視為 `Shape` 節點，因此我們可以使用 `GetChild` 搭配 `NodeType.Shape` 來取得第一個遇到的圖表。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **為什麼這很重要：**  
> 直接存取 `Chart` 物件，可避免在 Word 中手動開啟檔案並逐一調整標籤的額外開銷。這是任何 **修改圖表資料標籤** 自動化的基礎。

## 調整長條圖標籤：變更圖表標籤位置

取得 `Chart` 實例後，讓我們遍歷其 `DataLabelCollection`。目標是 **變更圖表標籤位置**，使每個標籤都能整齊地位於長條底部，而不是尷尬地漂浮在上方。

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **小技巧：**  
> `InsideBase` 適用於垂直長條圖。若處理水平長條圖，請改用 `InsideEnd`。只要重新執行程式並開啟儲存的文件，即可快速測試不同位置。

## 變更圖表標籤字型：調整可讀性字型大小

過小的字型是報告可讀性的大敵。要 **變更圖表標籤字型**，只需在每個 `ChartDataLabel` 上設定 `Font.Size` 屬性。我們將字型調整至 9 pt，這是大多數列印報告的理想大小。

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **為什麼要這麼做：**  
> 調整字型大小是 **修改圖表資料標籤** 的最佳實踐之一。較大的字型提升可及性，減少手動後處理的需求。

## 儲存更新後的文件

完成位置與字型的調整後，**如何編輯圖表** 的最後一步就是將變更寫回檔案。Aspose.Words 只需要一行程式碼即可完成。

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

開啟 `BarChartCustomLabels.docx`，你會看到標籤已緊貼長條內部，且以清晰的 9 pt 字型呈現。再也不必為微小的數字而眯眼。

---

## 完整範例（一步到位）

以下是一個完整、可直接執行的 Console 程式，示範從載入文件到儲存更新版本的整個流程。將程式碼貼到新的 .NET Console 專案中，按 **F5** 即可執行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**執行結果**（程式執行後的輸出）：

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

開啟產生的檔案，你會看到 **調整長條圖標籤** 已置於長條內部，且字型大小舒適。

---

## 常見問題與特殊情況

### 文件中有多個圖表怎麼辦？

上述程式碼僅抓取 *第一個* 圖表（`GetChild(NodeType.Shape, 0, true)`）。若要編輯全部圖表，請將單一取得改為迴圈：

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### 如何只為特定系列 **變更圖表標籤字型**？

每個 `ChartSeries` 都有自己的 `DataLabelCollection`。可依索引定位系列：

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### 這個方法能用於圓餅圖或折線圖嗎？

可以——`ChartDataLabelPosition` 支援 `InsideEnd`、`OutsideEnd`、`BestFit` 等值。對於圓餅圖，建議使用 `OutsideEnd` 以確保標籤易讀。

### 若需本地化（例如不同的小數點分隔符）該怎麼處理？

Aspose.Words 會遵循文件的語系設定。若需強制特定格式，可在儲存前調整 `label.NumberFormat`。

---

## 重點回顧與後續步驟

我們已完整說明 **如何編輯圖表** 物件的全流程：載入文件、取得圖表、**變更圖表標籤位置**、**調整長條圖標籤**、**修改圖表資料標籤**，最後 **變更圖表標籤字型** 後儲存。完整範例已具備生產環境可用性，能直接嵌入任何自動化管線。

想更進一步嗎？以下是可延伸的想法：

- **新增資料標籤顏色**（`dataLabel.Font.Color = Color.Blue;`）。  
- **以百分比顯示數值**（`dataLabel.NumberFormat = "0%";`）。  
- **程式化建立圖表**，而非載入既有圖表。  

上述功能皆基於本次使用的相同 API，讓你能快速上手。

若在實作過程中遇到問題，歡迎在下方留言，或參考 Aspose.Words 官方文件以取得更深入的圖表自訂說明。祝開發順利，享受美觀的圖表標籤吧！

## 接下來該學什麼？

以下教學與本篇內容緊密相關，能幫助你進一步掌握 API 功能，並在專案中探索其他實作方式。

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}