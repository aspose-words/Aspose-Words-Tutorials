---
category: general
date: 2026-07-20
description: 使用 Aspose.Words for .NET 添加圓餅圖標籤。了解如何更改圓餅圖標籤、顯示百分比標籤，以及快速更新圖表系列標籤。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: zh-hant
lastmod: 2026-07-20
og_description: 在 C# 中使用 Aspose.Words 添加餅圖標籤。只需幾個步驟即可熟練更改餅圖標籤、顯示百分比標籤以及更新圖表系列標籤。
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: 在 C# 中加入餅圖標籤 – Aspose.Words 完整教學
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: 使用 Aspose.Words 在 C# 中添加餅圖標籤 – 完整指南
url: /zh-hant/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中使用 Aspose.Words 為圓餅圖添加標籤 – 完整指南

需要在 Word 文件中使用 C# **添加圓餅圖標籤** 嗎？使用 Aspose.Words，您可以輕鬆 **變更圓餅圖標籤** 並 **在檔案內直接顯示圓餅圖百分比**——無需在 Word 中手動調整。  

本教學將逐步說明 **顯示百分比標籤**、重新定位標籤，甚至 **更新圖表系列標籤** 以因應動態資料的確切步驟。完成後，您將擁有一段可重複使用的程式碼片段，隨時可嵌入任何 .NET 專案。

> **快速預覽：** 按照本指南操作後，開啟已儲存的 `.docx` 檔案，即可看到圓餅圖的每個切片都以百分比標籤顯示，且標籤位於切片外側，便於閱讀。

---

## 您需要的條件

- **Aspose.Words for .NET**（截至 2026 年的最新版本）。您可以從 NuGet 取得：`Install-Package Aspose.Words`。
- 一份已包含圓餅圖或環形圖的 **Word 文件**（我們稱之為 `Chart.docx`）。
- 具備 **C#** 與 Visual Studio（或您慣用的 IDE）的基本知識。

就這樣——不需要額外的函式庫、也不需要 COM interop，純粹使用受管理的程式碼。

---

## 添加圓餅圖標籤 – 完整實作

以下是一個 **完整且可執行** 的 C# 主控台程式，會載入文件、修改第一個圓餅圖，並儲存結果。每一行皆有註解，讓您了解 **為何** 這樣做，而不僅是 **做了什麼**。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### 預期結果

在 Microsoft Word 中開啟 `ChartWithCustomLabels.docx`。您應該會看到圓餅圖 **每個切片外側都有百分比標籤**。標籤類似於 “35 %”、 “20 %” 等，讓圖表一目了然。

---

## 變更圓餅圖標籤：位置與格式

如果您只需要 **變更圓餅圖標籤** 而不顯示百分比，可將 `Position` 屬性調整為以下任一值：

| Position Enum | Visual Effect |
|---------------|---------------|
| `InsideEnd`   | 標籤位於切片內部，緊貼邊緣。 |
| `Center`      | 標籤顯示在切片的中間（適用於小型圓餅圖）。 |
| `OutsideEnd`  | 標籤位於切片外側，並以引線連接（預設設定）。 |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**小技巧：** `OutsideEnd` 在切片較多的圖表中效果最佳；可避免文字重疊。

---

## 在圓餅圖上顯示百分比標籤

`ShowPercentage` 屬性是一個 **布林旗標**。將其設為 `true` 後，Aspose.Words 會根據底層資料來源計算每個切片的比例。

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

如果同時需要原始數值 **以及** 百分比，亦可將其與 `ShowValue` 結合使用：

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

當兩個旗標皆啟用時，標籤會顯示為 “45 % (120)” 的形式。

---

## 為動態資料更新圖表系列標籤

通常會即時產生圖表——例如每月銷售或調查結果。若要以程式方式 **更新圖表系列標籤**，請在處理資料標籤之前先修改 `Series` 集合：

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

此程式碼片段示範了如何為任意系列（不僅是第一個） **更新圖表系列標籤**。在建立結合實際與預測資料的報表時相當實用。

---

## 邊緣情況與常見陷阱

| Situation | What to Watch For | Fix |
|-----------|-------------------|-----|
| **圖表不是圓餅圖/環形圖** | `Position` 可能不會產生任何視覺效果。 | 確認 `chart.Type` 為 `ChartType.Pie` 或 `ChartType.Doughnut`。 |
| **未找到圖表** | `GetChild` 回傳 `null`。 | 加入防護判斷（參見程式碼）並記錄有用的訊息。 |
| **較舊的 Word 版本** | 某些標籤功能會被忽略。 | 儲存為 `.docx`（現代格式）以確保完整支援。 |
| **切片數量過多** | 即使使用 `OutsideEnd`，標籤仍可能重疊。 | 考慮減少切片數量或放大圖表尺寸。 |

---

## 完整可執行範例（複製貼上）

以下是您可以直接複製到新主控台專案的 **完整程式**。只需將 `YOUR_DIRECTORY` 替換為存放 `Chart.docx` 的資料夾路徑即可。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // Grab the first chart (assumed to be a pie chart).
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null) { Console.WriteLine("No chart found."); return; }

            // Access the first series' data labels.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // Position labels outside and show percentages.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;
            dataLabels.ShowPercentage = true;

            // (Optional) Show raw values as also.
            // dataLabels.ShowValue = true;

            // Save the modified


## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並在此基礎上延伸。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [設定圖表資料標籤的預設選項](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [自訂圖表中的單一系列](/words/english/net/programming-with-charts/single-chart-series/)
- [使用 Aspose.Words for .NET 在 Word 中插入直條圖](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}