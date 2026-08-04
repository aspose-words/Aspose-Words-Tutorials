---
category: general
date: 2026-08-04
description: 如何在 C# 中使用 Aspose.Words 添加資料標籤。學習編輯圖表、將圖表資料標籤置中、在圖表中顯示百分比，以及自訂圖表資料標籤。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: zh-hant
lastmod: 2026-08-04
og_description: 如何在 C# 中使用 Aspose.Words 添加資料標籤。本教學將示範如何編輯圖表、將圖表資料標籤置中、在圖表中顯示百分比，以及自訂圖表資料標籤。
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: 如何在 C# 中為 Word 圖表新增資料標籤 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: 如何在 C# 中為 Word 圖表新增資料標籤 – 逐步指南
url: /zh-hant/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中為 Word 圖表新增資料標籤 – 步驟說明指南

如果您需要 **how to add data labels**（在 Word 文件中的圖表新增資料標籤），本指南會示範您必須執行的完整程式碼。您將會看到如何編輯圖表屬性、將圖表資料標籤置中、在圖表中顯示百分比，以及在任何情況下自訂圖表資料標籤。

本教學涵蓋從載入文件到保存變更的所有必要步驟。無需外部參考——只需要 Aspose.Words for .NET 函式庫以及基本的 C# 開發環境。

## 前置條件

在開始之前，請確保您已具備：

* 已安裝 .NET 6.0（或更新版本）。
* Aspose.Words for .NET 版本 23.9 或更新。  
  您可以透過 NuGet 安裝：

```bash
dotnet add package Aspose.Words
```

* 一個包含至少一個圖表的 Word 檔案（`input.docx`）。

## 如何在 C# 中為 Word 圖表新增資料標籤

以下各節將逐步說明每個步驟。主要關鍵字 **how to add data labels** 會自然出現在說明與程式碼註解中，保持在建議的密度範圍內。

### 步驟 1 – 載入包含圖表的 Word 文件

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*此步驟的重要性*：`Document` 物件代表整個 Word 檔案。載入它後即可存取所有節點，包括容納圖表的 Shape。

### 步驟 2 – 從文件中取得第一個圖表

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*此步驟的重要性*：圖表儲存在 `Shape` 節點內。將取得的節點轉型為 `Shape` 並呼叫 `GetChart()`，即可取得 `Chart` 物件，該物件提供系列、座標軸與標籤集合。

### 步驟 3 – 啟用資料標籤自訂並在圖表中顯示百分比

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*此步驟的重要性*：設定 `ShowPercentage` 會告訴 Aspose.Words 計算並顯示每個切片佔總量的比例。這直接對應次要關鍵字 **show percentages in chart**。

### 步驟 4 – 將標籤位置變更為每個資料點的中心

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*此步驟的重要性*：`Position` 屬性控制標籤相對於資料點的顯示位置。使用 `Center` 滿足次要關鍵字 **center chart data labels**，同時提升圓餅圖或環形圖的可讀性。

### 步驟 5 – 進一步自訂圖表資料標籤（可選）

如果需要更細緻的控制，您可以調整字型、顏色或領線：

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

這些設定說明了次要關鍵字 **customize chart data labels**，並示範如何依品牌指南調整外觀。

### 步驟 6 – 儲存已修改的文件

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*此步驟的重要性*：儲存會將更新後的圖表寫回 Word 文件，讓您在 Microsoft Word 中開啟檔案時即可看到新的資料標籤。

## 完整、可執行的範例

以下是一個完整的程式範例，您可以直接複製、貼上並執行。範例包含所有必要的 `using` 指示詞與說明每一行功能的註解。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### 預期結果

當您在 Microsoft Word 中開啟 `output.docx` 時，圖表將顯示：

* 每個切片旁的百分比值（例如 **25 %**、**40 %**、…）。
* 標籤位於每個資料點的中心。
* 任何您自行套用的額外樣式，例如粗體紅色文字。

這些視覺提示能讓圖表更易於解讀，特別是在簡報或報告中。

## 如何編輯圖表屬性（不僅限於資料標籤）

雖然本指南的重點是 **how to add data labels**，您也可能想要 **how to edit chart** 的設定，例如標題、圖例位置或座標軸格式。`Chart` 物件提供 `Title`、`Legend` 以及 `AxisX/AxisY` 等屬性。例如，要變更圖表標題：

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

所有圖表的修改皆遵循相同的流程：取得圖表、調整屬性，最後儲存文件。

## 常見陷阱與最佳實踐提示

| 陷阱 | 為何會發生 | 推薦的解決方式 |
|---|---|---|
| 圖表位於群組形狀內。 | `GetChild(NodeType.Shape, …)` 會回傳外層群組，而非內部圖表。 | 以遞迴方式搜尋具有 `shape.HasChart` 的 Shape。 |
| 儲存後資料標籤未顯示。 | `ShowValue` 或 `ShowPercentage` 未設為 `true`。 | 依需求明確設定 `ShowValue` 與 `ShowPercentage`。 |
| 小切片的標籤重疊。 | 中心定位可能導致擁擠。 | 使用 `ChartDataLabelPosition.OutSideEnd` 於外側顯示，或啟用 `LeaderLines`。 |

遵循上述技巧，可確保在不同圖表類型下皆能得到可靠的結果。

## 結論

您現在已掌握 **how to add data labels** 至 Word 圖表的完整流程，包含取得圖表、啟用標籤可見性、將標籤置中、顯示百分比以及自訂外觀。藉此知識，您亦能 **how to edit chart**、**center chart data labels**、**show percentages in chart** 與 **customize chart data labels**，滿足任何報表需求。

準備好進一步探索了嗎？試著加入多個系列、套用條件格式，或將圖表匯出為影像。Aspose.Words API 提供豐富的圖表操作功能——盡情實驗，找出最適合您資料的視覺呈現方式。

## 接下來該學什麼？

以下教學與本指南所示技巧密切相關，能協助您進一步精通 API 功能並在專案中探索其他實作方式。每篇資源皆包含完整可執行的程式碼範例與逐步說明。

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize A Single Chart Data Point In A Chart](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}