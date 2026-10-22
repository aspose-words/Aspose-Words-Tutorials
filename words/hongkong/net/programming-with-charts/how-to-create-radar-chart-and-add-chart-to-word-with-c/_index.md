---
category: general
date: 2026-09-05
description: 使用 C# 在 Word 中建立雷達圖。快速學習產生空白 Word 文件、加入雷達圖、設定圖表大小，並啟用刻度線。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: zh-hant
lastmod: 2026-09-05
og_description: 使用 C# 在 Word 中建立雷達圖。本指南將示範如何產生空白 Word 文件、加入雷達圖、設定圖表大小，並啟用刻度線——只需數分鐘。
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: 在 Word 中建立雷達圖 – C# 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: 如何使用 C# 建立雷達圖並將圖表加入 Word
url: /zh-hant/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 建立雷達圖並將圖表加入 Word

如果您需要在 Word 檔案中 **建立雷達圖**，本教學將一步步帶您完成整個流程。您將學會如何 **產生空白 Word 文件**、插入雷達圖、**設定圖表大小於 Word**，以及啟用軸刻度——全部只需幾行 C# 程式碼。

在報告中加入視覺化資料是常見需求，使用 Aspose.Words 可讓此工作變得簡單。以下步驟同時說明如何 **以程式方式將圖表加入 Word**，讓您能自動化儀表板、財務摘要或任何資料驅動的內容。

## 前置條件

在開始之前，請確保您已具備：

* 已安裝 .NET 6.0 或更新版本  
* Aspose.Words for .NET 授權（或免費試用版）——本教學使用的 `Document`、`DocumentBuilder` 與圖表 API 均來自此函式庫  
* Visual Studio 2022（或任何 C# IDE）  

> **小技巧：** 若您在測試階段，可將 Aspose.Words DLL 放入專案的 `bin` 資料夾，並透過 NuGet 參考（`Install-Package Aspose.Words`）。

## 如何在 Word 文件中建立雷達圖

第一步是 **產生空白 Word 文件**，作為圖表的容器。這樣可提供乾淨的畫布，並讓您在加入任何內容前先設定文件的中繼資料。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*為什麼這很重要：* 空的 `Document` 物件可確保沒有隱藏的樣式或區段會影響圖表版面，同時也方便日後設定文件屬性（作者、標題）等。

## 如何使用 Aspose.Words 將圖表加入 Word

接下來，建立 `DocumentBuilder`。Builder 是讓您在文件中插入文字、圖片與圖表的主要工具。

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

現在您可以在游標所在位置 **直接加入雷達圖**。`InsertChart` 方法接受 `ChartType` 列舉、寬度與高度（以點為單位）。

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*為什麼使用 400 × 300？* 這個尺寸在標準 A4 頁面上能呈現清晰、易讀的圖表。若版面需要不同的長寬比，可在 **設定圖表大小於 Word** 步驟中再調整。

## 在 Word 中設定圖表大小

若需在插入後微調尺寸，可修改圖表的 `Width` 與 `Height` 屬性。當周圍文字或頁邊距要求不同的視覺平衡時，這非常實用。

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **注意：** `InsertChart` 的重載已經設定了尺寸，上述程式碼屬於可選項目，僅為完整性示範。

## 在徑向軸上啟用刻度

雷達圖在徑向軸顯示清晰的刻度時最具可讀性。以下設定會開啟刻度並將間隔設為 30 度，符合一般羅盤式雷達圖的顯示方式。

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*為什麼這很重要：* 刻度能協助讀者在每個角度上判斷數值，提升對不熟悉資料的利害關係人的可讀性。

## 儲存含圖表的文件

最後，將文件寫入磁碟。您可以自行決定儲存資料夾，只要確保路徑已存在即可。

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

當您在 Microsoft Word 中開啟 `RadialChart.docx`，即可看到一個完整呈現、置中於頁面的雷達圖，尺寸符合先前設定，且每 30 度都有刻度。

### 預期輸出

* 一個名為 **RadialChart.docx** 的 `.docx` 檔案  
* 第一頁包含尺寸為 400 × 300 點的雷達圖  
* X 軸（徑向軸）在 0°、30°、60°、…、330° 處顯示刻度  

您現在可以透過存取 `radarChart.Series` 來替換佔位資料系列，然而這已超出本 **加入雷達圖** 基礎教學的範圍。

## 常見變化與邊緣案例

| 情境 | 調整方式 |
|----------|------------|
| **不同的圖表類型** | 將 `ChartType.Radar` 改為 `ChartType.Column`、`ChartType.Pie` 等 |
| **多個圖表** | 重複呼叫 `InsertChart`；每次呼叫會將新圖表放在前一個圖表之後 |
| **大型資料集** | 使用 `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` 來加入大量資料點 |
| **另存為 PDF** | 在加入圖表後呼叫 `document.Save("RadialChart.pdf", SaveFormat.Pdf);` |
| **在 .NET Core 上執行** | 確認引用 `Aspose.Words.NETCore` 套件；API 用法相同 |

## 完整可執行範例

以下程式碼為完整範例，您可直接複製貼上至主控台應用程式。它包含所有步驟、可選的尺寸調整，以及說明性註解。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

執行程式後，開啟產生的檔案，即可看到如說明中所示的雷達圖。

## 結論

現在您已掌握如何使用 C# **建立雷達圖** 並 **將圖表加入 Word**。本教學涵蓋了產生 **空白 Word 文件**、插入雷達圖、**設定圖表大小於 Word**，以及啟用軸刻度。以此為基礎，您可以延伸至多圖表、客製化資料系列，或匯出為 PDF。

### 後續步驟

* 探索 `ChartType` 的其他圖表類型（例如 `Bar`、`Line`）——請參考 **加入雷達圖** 關鍵字的相關範例。

## 接下來您應該學習什麼？

以下教學與本指南緊密相關，能進一步深化您所學的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索替代實作方式。

- [在 Word 文件中插入散佈圖](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [使用 Aspose.Words for .NET 在 Word 中插入直條圖](/words/english/net/working-with-charts/insert-column-chart/)
- [在 Word 文件中隱藏圖表軸](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}