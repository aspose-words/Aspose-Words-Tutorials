---
category: general
date: 2026-10-07
description: 學習如何使用 Aspose.Words 在 C# 中建立 Word 文件並插入圓餅圖。此指南亦示範如何產生帶有自訂圖表標籤的 Word 檔案。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: zh-hant
lastmod: 2026-10-07
og_description: 在 C# 中建立 Word 文件並插入圓形圖表。請依照此一步一步的指南，產生具備完整自訂圖表標籤的 Word 檔案。
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: 在 C# 中建立帶有自訂圓餅圖的 Word 文件
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: 如何在 C# 中建立帶有自訂圓餅圖的 Word 文件
url: /zh-hant/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中建立自訂餅圖的 Word 文件

如果您需要以程式方式 **create word document**，本教學將示範如何使用 Aspose.Words for .NET **insert pie chart** 並自訂其資料標籤。您還將學習如何 **generate word file**，其中包含完整樣式的圖表，涵蓋從專案設定到儲存最終文件的全部步驟。

本指南會逐步說明加入圖表、調整標籤位置、啟用指引線，最後將結果儲存為 `.docx` 檔案的每個必要步驟。除了 Aspose.Words 函式庫外，無需其他外部工具，且提供完整原始碼，您可以直接複製、貼上並立即執行。

## 前置條件

在開始之前，請確保您已具備：

* 已安裝 .NET 6.0 SDK 或更新版本  
* 有效的 Aspose.Words for .NET 授權（或免費評估金鑰）  
* 如 Visual Studio 2022 或 Visual Studio Code 等開發環境  

您還需要將以下 NuGet 套件加入專案：

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

這些套件會公開 `Document`、`DocumentBuilder` 以及圖表相關的類別，供下列範例使用。

## 建立 Word 文件並加入圖表

第一步是 **create word document**，並取得可讓您插入內容的 `DocumentBuilder`。Builder 的運作方式類似位於文件內的游標。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` 物件代表整個 Word 檔案，而 `DocumentBuilder` 提供如 `InsertChart` 等方法，直接將物件插入文件流程中。

## 在文件中插入餅圖

現在 Builder 已就緒，您可以 **insert pie chart** 並指定特定大小。圖表會加入於 Builder 目前所在的位置。

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` 會回傳一個 `Chart` 物件，您可以進一步操作。範例資料會產生四個切片，代表季銷售額。

## 自訂餅圖資料標籤

為了提升圖表可讀性，通常需要 **customize pie chart** 標籤——將它們放置在切片外側並顯示指引線。此時 `ChartDataLabelCollection` 就派上用場。

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

將 `Position` 設為 `OutsideEnd` 會使每個標籤移至切片邊緣之外，而 `ShowLeaderLines` 會繪製連接標籤與切片的線條。可選的 `ShowValue` 與 `ShowPercentage` 旗標則同時提供原始數值與相對百分比。

**Pro tip:** 若需調整標籤字型，使用 `dataLabels.Font` 設定大小、顏色與樣式，確保圖表符合企業品牌形象。

## 儲存並產生 Word 文件

圖表設定完成後，您可以透過儲存 `Document` 實例至磁碟來 **generate word file**。建議使用 `.docx` 格式，以獲得與現代 Word 版本的最高相容性。

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

開啟 `CustomPieChart.docx` 後，您會看到一個包含四個切片的餅圖，每個切片的標籤皆位於外側，並以指引線連接，同時顯示數值與百分比。

![使用 C# 建立的自訂餅圖之 Word 文件截圖](image-placeholder.png)

*此圖片顯示 **create word document** 教學的最終結果。*

## 常見變體與邊緣情況

| 情境 | 如何調整程式碼 |
|----------|----------------------|
| **Multiple series** | 在 `pieChart.Series` 中加入額外的 `ChartSeries` 物件。每個系列都可以擁有自己的 `DataLabels` 集合，以進行獨立樣式設定。 |
| **Different chart size** | 修改 `InsertChart(width, height)` 的寬度與高度參數。數值單位為點 (1 pt ≈ 1/72 in)。 |
| **Chart title** | 使用 `pieChart.Title.Text = "Quarterly Sales"` 來加入說明性的圖表標題。 |
| **Export to PDF** | 在圖表建立完成後，呼叫 `document.Save("Report.pdf", SaveFormat.Pdf);` 以匯出 PDF。 |
| **License handling** | 將授權檔案 (`Aspose.Words.lic`) 放置於應用程式資料夾，並在建立文件前以 `new License().SetLicense("Aspose.Words.lic");` 載入。 |

這些變體讓您能在各種實務情境下回答 **how to add pie chart** 的需求，從簡易報表到複雜儀表板皆適用。

## 結論

現在您已了解如何使用 Aspose.Words for .NET **create word document**、**insert pie chart**，以及 **customize pie chart** 標籤。完整範例示範了清晰的工作流程：初始化文件、加入圖表、調整資料標籤位置、啟用指引線，最後 **generate word file**，即可與任何人分享。

試著擴充本教學，使用不同的圖表類型（`ChartType.Column`、`ChartType.Line`）或套用自訂色盤以符合品牌風格。若遇到問題，請參考 Aspose.Words 文件或探索相關主題，例如多系列與動態資料來源的 “how to add pie chart”。

祝開發順利，歡迎在留言區分享您的成果或提出後續問題！

## 接下來該學什麼？

以下教學涵蓋與本指南技術緊密相關的主題，並在此基礎上進一步延伸。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [在 Word 文件中插入直條圖](/words/english/net/programming-with-charts/insert-column-chart/)
- [在 Word 文件中插入面積圖](/words/english/net/programming-with-charts/insert-area-chart/)
- [在 Word 文件中插入散點圖](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}