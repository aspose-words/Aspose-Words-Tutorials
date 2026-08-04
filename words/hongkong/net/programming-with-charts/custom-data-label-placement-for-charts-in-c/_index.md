---
category: general
date: 2026-08-04
description: 在 C# 中的圖表自訂資料標籤放置可讓您將標籤置中於圖表切片。請遵循此逐步指南，使用 Aspose.Words 圖表 API。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: zh-hant
lastmod: 2026-08-04
og_description: C# 中的自訂圖表資料標籤位置示範如何將 Word 圖表的每個切片的資料標籤置中。使用 Aspose.Words 精通圖表資料標籤的定位。
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: C# 圖表自訂資料標籤放置 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: C# 圖表的自訂資料標籤放置
url: /zh-hant/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# 中的圖表自訂資料標籤位置

**Custom Data‑Label Placement for Charts** 讓您可以精確控制 Word 文件內圖表中每個標籤的顯示位置。於本教學中，您將學會如何使用 C# 以及 Aspose.Words 圖表 API，將每個切片的資料標籤置中。

您將獲得一個完整、可執行的範例，示範如何載入 `.docx` 檔案、取得第一個圖表 Shape、將每個標籤的 `Position` 設為 `Center`，並儲存更新後的文件。此範例不需額外參考，只需 Aspose.Words for .NET 套件與基本的 C# 開發環境。

**您將學習到**

* 如何載入包含圖表的 Word 文件。  
* 如何使用 Aspose.Words 圖表 API 找到圖表 Shape。  
* 如何對圖表中的每個系列套用 **圖表資料標籤位置**。  
* 如何儲存文件，使置中的標籤在 Word 中正確顯示。  

**先備條件**

* 已安裝 .NET 6.0（或更新版本）。  
* Visual Studio 2022（或任何 C# IDE）。  
* 已加入 `Aspose.Words` NuGet 套件的參考。  
* 一個包含至少一個圖表的 Word 檔案（`Chart.docx`）。

---

## 自訂圖表資料標籤位置 – 步驟 1：載入文件

首先必須開啟包含圖表的 Word 檔案。`Document` 是使用 Aspose.Words 進行任何操作的入口點。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*為什麼此步驟重要*：若未載入文件就無法取得圖表物件。此驗證會在檔案未包含圖表時拋出明確錯誤，避免之後出現 null 參考例外。

---

## 使用 Aspose.Words 圖表 API 取得圖表 Shape

Aspose.Words 將圖表視為嵌入於 `Shape` 內的 `Chart` 物件。您可以透過將相應的子節點轉型取得它。

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*為什麼此步驟重要*：直接存取 `Chart` 可讓您完整控制系列、資料點與標籤屬性。若該 Shape 不是圖表，程式會提前中止並顯示說明訊息。

---

## 在 C# 中設定圖表資料標籤位置

接著遍歷每個系列與每個資料標籤，將 `Position` 設為 `Center`。這就是 **Custom Data‑Label Placement for Charts** 的核心。

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**專業提示**：若需要其他位置（例如柱狀圖的 `InsideEnd`），只要將列舉值改成相應的項目即可。`ChartDataLabelPosition` 列舉包含 Word 所支援的所有標準位置。

*為什麼此步驟重要*：變更 `label.Position` 會更新底層的 OOXML 表示，文件在 Microsoft Word 中開啟時，標籤即會置中顯示。

---

## 儲存已更新標籤的 Word 文件

修改完圖表後，將變更寫回檔案。您可以覆寫原檔或另存新檔。

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*為什麼此步驟重要*：儲存會把更新後的 OOXML 寫入磁碟。開啟 `ChartLabelsCentered.docx` 後，您會看到每個切片的標籤已置中，證明 **Custom Data‑Label Placement for Charts** 已成功執行。

---

## 邊緣情況與變體

| 情況 | 處理方式 |
|-----------|---------------|
| **同一文件中有多個圖表** | 迭代 `doc.GetChildNodes(NodeType.Shape, true)`，並檢查每個 `shape.HasChart` 是否為 true。 |
| **不同圖表類型**（圓餅圖、環形圖、長條圖） | `ChartDataLabelPosition.Center` 適用於圓餅類圖表。對於長條/柱狀圖，您可能會偏好 `InsideEnd` 或 `OutsideEnd`。 |
| **標籤文字需要格式化** | 取得 `label.TextProperties` 後即可設定字型大小、顏色或粗體等屬性。 |
| **在 .NET Core 上執行** | 確認引用的是 .NET Standard 版的 Aspose.Words；API 完全相同。 |

---

## 完整可執行範例

以下程式碼可直接貼到 Console 應用程式中執行，已包含所有必要的 `using` 指令與錯誤處理。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**預期結果**：在 Microsoft Word 中開啟 `ChartLabelsCentered.docx`，每個圖表切片的資料標籤都會顯示在切片中心，呈現更清晰的視覺效果。

---

## 結論

您現在已掌握在 C# 中實作 **Custom Data‑Label Placement for Charts** 的完整解決方案。透過載入文件、使用 Aspose.Words 圖表 API 取得圖表、將 `ChartDataLabelPosition.Center` 套用至每個標籤，最後儲存檔案，即可自動化任何 Word 圖表的標籤位置。

接下來，您可以探索其他 **圖表資料標籤位置** 選項，如 `InsideEnd` 或 `OutsideEnd`，或嘗試 **C# 圖表操作**，例如變更顏色、加入圖例，或從頭產生圖表。這些延伸功能直接建立在本教學的技巧之上，能進一步提升您在 Word 文件中處理圖表的自動化能力。祝開發順利！

## 接下來您可以學習什麼？

以下教學與本指南的技術緊密相關，提供完整的程式碼範例與逐步說明，協助您掌握更多 API 功能或探索其他實作方式。

- [自訂圖表資料標籤](/words/english/net/programming-with-charts/chart-data-label/)
- [格式化圖表資料標籤的數字](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [圖表資料標籤](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}