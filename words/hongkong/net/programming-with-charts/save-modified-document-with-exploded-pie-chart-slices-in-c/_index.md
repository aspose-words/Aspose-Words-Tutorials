---
category: general
date: 2026-10-13
description: 在 C# 中自訂圓餅圖：將切片分離、變更第一切片角度，並顯示百分比標籤後，儲存已修改的文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: zh-hant
lastmod: 2026-10-13
og_description: 在 C# 中自訂圓餅圖後儲存已修改的文件。了解如何將圓餅圖切片分離、變更首個切片的角度，以及顯示百分比標籤。
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: 儲存已修改的文件（含分離的圓餅圖切片）– C# 指南
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: 在 C# 中儲存已修改的文件，包含已分離的圓餅圖切片
url: /zh-hant/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中儲存已修改的文件（含分離的圓餅圖切片）

如果您需要在調整 Word 圓餅圖後 **儲存已修改的文件**，本指南將一步步說明。您將學會分離圓餅圖切片、變更第一切片角度，以及顯示百分比標籤——只需幾行 C# 程式碼。

自訂圖表是程式化產生報告、發票或儀表板時的常見需求。完成本教學後，您將能載入 DOCX 檔案、修改圖表外觀，並 **儲存已修改的文件** 以供分發。

## 前置條件

- .NET 6.0 或更新版本（此程式碼亦相容 .NET Framework 4.6+）
- Aspose.Words for .NET 23.10 或更新版本（免費試用版或正式授權版）
- 含有單一圓餅圖的 Word 檔案（`input.docx`）
- Visual Studio 2022 或任何 C# IDE

> **提示：** 可使用 `dotnet add package Aspose.Words` 來加入 Aspose.Words NuGet 套件。

## 步驟 1：載入包含圖表的 Word 文件

第一步是開啟來源 DOCX 檔案。`Document` 類別代表整個 Word 檔案於記憶體中的模型。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

載入文件後，您即可完整存取每個節點，包括承載圖表的 Shape。

## 步驟 2：從文件中取得第一個圖表 Shape

圖表儲存在 `Shape` 節點內。您可以使用 `GetChild` 取得第一個圖表。

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

若文件中有多個圖表，請調整索引 (`0`) 或遍歷整個集合。此行確保您取得要修改的 `Chart` 物件參考。

## 步驟 3：分離圓餅圖切片

分離切片會讓它從圓餅的其餘部分脫離，使圖表更易閱讀。`Explode` 屬性適用於整個系列。

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

將 `Explode` 設為 `true` **分離圓餅圖切片**，適合希望每個切片都突顯的情況。

## 步驟 4：變更第一切片的角度

有時需要讓第一切片從自訂角度開始，例如配合設計指引。

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

`FirstSliceAngle` 屬性 **變更第一切片** 的方向，將整個圓餅旋轉，使第一切片從 30 度開始。

## 步驟 5：在圓餅切片上顯示百分比標籤

在報表中常需要顯示每個切片的數值貢獻。`DataLabel.ShowPercentage` 旗標會開啟百分比顯示。

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

此步驟 **顯示百分比標籤** 於圖表上，同時滿足 **顯示百分比圓餅圖** 的需求。

## 步驟 6：儲存已修改的文件

完成所有自訂後，將變更寫入新檔案。`Save` 方法會將更新後的 DOCX 寫入磁碟。

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

現在您已擁有一個 **儲存已修改的文件**，其中包含分離的圓餅圖、旋轉的第一切片，以及可見的百分比標籤。

![儲存已修改的文件，顯示分離的圓餅圖切片](/images/pie-chart-exploded.png "儲存已修改的文件，顯示分離的圓餅圖切片與百分比標籤")

*此螢幕截圖說明文件儲存後的最終輸出。*

## 完整可執行範例

將上述片段組合起來，即成為您可以直接貼到 Console 專案的完整程式：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### 預期結果

開啟 `output.docx` 後，圓餅圖會呈現：

- 每個切片皆略為分離（**分離圓餅圖切片**）
- 第一切片從 30 度的偏移開始（**變更第一切片**）
- 每個切片顯示其百分比貢獻（**顯示百分比標籤**、**顯示百分比圓餅圖**）
- 檔案已 **儲存已修改的文件**，且未改動原始檔案。

## 常見問題與邊緣情況

| 問題 | 解答 |
|----------|--------|
| **如果文件中沒有圖表怎麼辦？** | 程式碼會在 `GetChild` 後檢查是否為 `null`。若不存在圖表，您可以自行程式化新增圖表，或以清晰訊息中止。 |
| **能只分離單一切片嗎？** | 可以。使用 `chart.PieChart.Series[0].DataPoints[i].Explosion = true;`，其中 `i` 為切片索引。 |
| **如何同時顯示數值與百分比？** | 設定 `chart.PieChart.DataLabel.ShowValue = true;`，並視需要同時保留 `chart.PieChart.DataLabel.ShowPercentage = true;`。 |
| **儲存後圖表樣式會保持嗎？** | Aspose.Words 會保留所有樣式，包括顏色與字型，當您 **儲存已修改的文件** 時不會遺失。 |
| **可以一次處理同一檔案中的多個圖表嗎？** | 可以。使用 `NodeType.Shape` 迭代所有 `Shape` 節點，並以 `shape.HasChart` 篩選，對每個圖表套用相同步驟。 |

## 結論

現在您已掌握在程式化自訂 Word 圓餅圖後 **儲存已修改的文件** 的完整流程。本文涵蓋了分離圓餅圖切片、變更第一切片角度以及顯示百分比標籤，滿足 **顯示百分比標籤**、**分離圓餅圖切片**、**顯示百分比圓餅圖** 與 **變更第一切片** 等需求。

接下來，您可以探索：

- 動態新增資料系列 (`chart.Series.Add(...)`)  
- 自訂圖例位置與圖表標題  
- 在保留圖表樣式的前提下將 DOCX 轉為 PDF  

歡迎嘗試不同的角度、分離設定或標籤格式，以符合您的報表需求。祝開發順利！

## 接下來該學什麼？

以下教學與本指南的技術緊密相關，能進一步深化您對 API 的掌握，並提供其他實作方式的範例。

- [如何在 C# 中使用 Aspose.Words 儲存已編輯的文件 – 步驟說明](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [使用 Aspose.Words for .NET 在 Word 文件中更新圖表系列資料](/words/english/net/programming-with-charts/modify-chart-series/)
- [在 Word 文件中插入直條圖](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}