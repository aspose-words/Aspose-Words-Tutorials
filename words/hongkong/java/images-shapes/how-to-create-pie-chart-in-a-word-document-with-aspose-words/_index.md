---
category: general
date: 2026-10-20
description: 使用 Aspose.Words 在 Word 文件中建立圓餅圖 – 步驟教學，說明如何設定顏色、將切片分離，並儲存 Word 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: zh-hant
lastmod: 2026-10-20
og_description: 使用 Aspose.Words 在 Word 文件中建立圓餅圖。了解如何設定顏色、分離切片，並在單一可執行範例中儲存 Word 文件。
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: 在 Word 文件中建立圓餅圖 – 完整 C# 指南
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: 如何在 Word 文件中使用 Aspose.Words 建立圓餅圖
url: /zh-hant/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 Aspose.Words 建立圓餅圖

如果您需要 **在 Word 檔案中建立圓餅圖**，本教學將一步步示範如何操作。您將學會設定自訂顏色、將切片「爆炸」以強調重點，最後 **儲存含圖表的 Word 文件**。

以程式方式產生圖表可省去手動開啟 Word、插入圖表、調整外觀的步驟。完成本教學後，您將擁有一個完整、可執行的 C# 主控台應用程式，能建立圓餅圖、客製化外觀，並將結果寫入磁碟。

## 前置條件

在開始之前，請確保您已具備：

* 已安裝 .NET 6.0 SDK 或更新版本  
* 有效的 Aspose.Words for .NET 授權（或免費評估金鑰）  
* 如 Visual Studio 2022 或 VS Code 等開發環境  

除 `Aspose.Words` 之外，無需額外的 NuGet 套件。

## 如何在 Word 文件中建立圓餅圖

第一步是實例化 `Document` 與 `DocumentBuilder`。Builder 可讓您存取高階的 Word 功能，包括插入圖表。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

此時文件已包含一個基本的圓餅圖。以下章節將說明 **如何爆炸切片**、**如何設定顏色**，以及 **如何儲存 Word 文件**。

## 如何爆炸切片以強調

將切片「爆炸」可使其與其他部分分離，吸引讀者目光。Aspose.Words API 允許您以點 (points) 為單位指定爆炸距離。

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

為什麼要爆炸切片？在報表中突顯特定類別（例如「熱銷商品」）時，視覺上的分離能讓該資料點立即被辨識。

## 如何為圖表切片設定顏色

自訂顏色有助於品牌一致性與可讀性。您可以將任意 `System.Drawing.Color` 指派給特定資料點。

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

您不必受限於預設顏色；亦可使用 `Color.FromArgb` 產生精確的色階。

## 如何儲存含圖表的 Word 文件

圖表完成後，將檔案寫入磁碟相當簡單。`Document.Save` 方法會依您指定的格式寫出文件——此處使用預設的 `.docx`。

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

執行程式後會產生 `PieChart.docx`。在 Microsoft Word 中開啟該檔案，即可看到第一個切片已被爆炸且填滿紅色，正如程式碼所指定。

### 預期結果

* 在 `C:\Temp` 產生名為 **PieChart.docx** 的 Word 檔案。  
* 文件內僅有一個圓餅圖，尺寸為 400 × 300 點。  
* 第 0 個切片偏移 20 點並填滿紅色，其餘切片保留預設顏色。  

您可以在 Word 中選取圖表，檢查切片屬性，以驗證爆炸與顏色設定是否正確。

## 專業技巧與常見陷阱

* **專業技巧：** 若需變更圖表標題或圖例，可在儲存前使用 `pieChart.Title.Text` 與 `pieChart.Legend` 屬性。  
* **注意事項：** 忘記清除預設資料點會導致多餘的切片出現。加入自訂資料前，務必呼叫 `Series[0].DataPoints.Clear()`。  
* **效能建議：** 處理大型文件時，重複使用同一個 `DocumentBuilder` 實例，而非不斷建立新 Builder，可降低記憶體開銷。

## 使用 Aspose.Words 建立圖表的其他說明

`InsertChart` 方法支援多種圖表類型，除圓餅圖外，還有柱狀圖、折線圖與區域圖等。若要切換圖表類型，只需將 `ChartType.Pie` 改為相應的列舉值，例如 `ChartType.Column`。其餘客製化步驟（爆炸切片、設定顏色）皆遵循相同模式，但並非所有圖表類型都提供「爆炸」屬性。

## 在其他圖表類型中爆炸切片

只有圓餅圖類型提供 `SetExplosion` 方法。若在長條圖上呼叫此方法，API 會拋出 `ArgumentException`。此時可考慮使用資料標籤或說明線來突顯特定長條。

## 為整個系列設定顏色，而非單一切片

若希望系列中的所有切片共享相同顏色，可遍歷資料點：

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

此做法在需要為多個圖表套用統一配色時相當便利。

## 以其他格式儲存 Word 文件

Aspose.Words 可匯出為 PDF、HTML 及其他多種格式。只需在 `Save` 時更改副檔名，並視需要傳入 `SaveOptions` 物件：

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

圖表渲染引擎會自動將圖表轉換為目標格式，保留顏色與爆炸設定。

## 結論

您現在已掌握 **在 Word 文件中建立圓餅圖**、透過 **爆炸切片** 與 **設定顏色** 進行外觀客製化，並最終 **儲存含圖表的 Word 文件**。此端對端範例為自動化報表產生、儀表板或任何需要程式化插入視覺化資料的情境奠定了堅實基礎。

### 後續步驟

* 探索其他圖表類型（`ChartType.Column`、`ChartType.Line`），擴充您的報表工具箱。  
* 在同一文件中結合多個圖表，打造完整的儀表板。  
* 嘗試使用 `ChartDataLabel` 直接在切片上顯示百分比或數值。  

歡迎將程式碼套用到自己的資料來源——無論是資料庫、API 或 CSV 檔案，皆可使用相同的 Aspose.Words 工作流程。祝您圖表製作順利！

## 接下來該學什麼？

以下教學與本指南緊密相關，能進一步深化您對 API 的運用，並提供其他實作方式的範例：

- [Explode Pie Chart Slice in C# with Aspose.Words – Full Guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Insert Custom Column Chart in Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}