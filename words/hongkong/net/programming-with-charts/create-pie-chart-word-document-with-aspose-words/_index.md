---
category: general
date: 2026-08-10
description: 使用 Aspose.Words 建立含圓餅圖的 Word 文件。學習如何插入圖表、客製化圓餅圖顏色，以及在 C# 中更改圓餅切片顏色。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: zh-hant
lastmod: 2026-08-10
og_description: 使用 Aspose.Words 建立圓餅圖 Word 文件。本指南說明如何在 C# 應用程式中插入圖表、客製化圓餅圖顏色，以及變更圓餅切片顏色。
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: 建立餅圖 Word 文件 – Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: 使用 Aspose.Words 建立含圓餅圖的 Word 文件
url: /zh-hant/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words 建立餅圖 Word 文件

如果您需要以程式方式 **create pie chart Word document**，本教學將會一步步示範。我們會說明如何插入圖表、**customize pie chart colors**，以及使用 Aspose.Words for .NET **change pie slice color**。

您將會看到一個完整、可執行的範例，您只要將它複製到 Visual Studio、執行，即可立即開啟產生的 *.docx* 以驗證已樣式化的餅圖。無需額外文件——本指南已提供所有必要資訊。

## 前置條件

在開始之前，請確保您已具備：

* 已安裝 .NET 6.0 SDK 或更新版本  
* 有效的 Aspose.Words for .NET 授權（或暫時的評估金鑰）  
* Visual Studio 2022（或任何 C# IDE）  

程式碼僅使用 `Aspose.Words` 與 `Aspose.Words.Drawing.Charts` 命名空間，除 Aspose.Words 套件外不需其他 NuGet 套件。

## 建立餅圖 Word 文件 – 完整範例

以下 C# 程式會建立新的 Word 文件、插入餅圖、為前兩個切片設定樣式，並儲存檔案。每一步都會詳細說明。

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 各步驟說明

| 步驟 | 功能說明 | 為什麼重要 |
|------|----------|------------|
| **1** | 建立新的 `Document` 與 `DocumentBuilder`。 | `DocumentBuilder` 提供流暢的插入內容方法，例如將圖表插入 Word 檔案。 |
| **2** | 使用 `ChartType.Pie` 以及固定尺寸呼叫 `InsertChart`。 | `InsertChart` 是 **how to insert chart** 的方法；指定寬高可確保圖表在頁面上呈現得恰當。 |
| **3** | 新增包含三個類別與數值的資料序列。 | 沒有資料的餅圖是看不見的；填入資料才能示範樣式設定步驟。 |
| **4** | 為第一個點設定 `Explosion`。 | 爆炸切片可突顯特定區段，適合強調關鍵資料。 |
| **5** | 為前兩個點設定 `ForeColor`。 | 這是 **customize pie chart colors** 的核心；您可以使用任意 `System.Drawing.Color`。 |
| **6** | 示範如何為其他切片 **change pie slice color**。 | 證明樣式不僅限於前兩個切片，您可以為每個切片單獨著色。 |
| **7** | 將文件儲存為 `PieChartStyled.docx`。 | 最終產出可在 Microsoft Word、Google Docs 或任何相容檢視器中開啟。 |

#### 預期輸出

開啟 `PieChartStyled.docx` 後會看到單頁、尺寸為 400 × 300 pt 的餅圖：

* 切片 1（橙色）向外爆炸。  
* 切片 2（綠色）緊鄰爆炸的切片。  
* 切片 3（鋼藍色）填滿剩餘區段。

圖表會依據資料值 (30, 45, 25) 以及您自訂的顏色顯示。

## 如何樣式化餅圖 – 其他技巧

* **使用主題顏色** – 可不必硬寫 `Color.Orange`，改為從文件主題取得顏色：  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **加入資料標籤** – 若想在圖表上顯示百分比：  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **動態調整大小** – 可根據頁面邊距計算圖表尺寸：  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

這些變化展示了 **how to style pie** 超越基本範例的彈性。

## 常見問題解答

**Q: 這能在 .NET Core 上執行嗎？**  
A: 能。Aspose.Words for .NET 相容於 .NET Core、.NET 5、.NET 6 以及更高版本。只要引用相同的 NuGet 套件即可。

**Q: 如果想要甜甜圈圖而不是餅圖，該怎麼做？**  
A: 將 `ChartType.Pie` 改為 `ChartType.Doughnut`。相同的樣式 API（`Explosion`、`ForeColor`）仍然適用。

**Q: 我可以把圖表插入到既有文件嗎？**  
A: 使用 `new Document("Existing.docx")` 開啟既有檔案，為該文件建立 `DocumentBuilder`，然後在所需的游標位置呼叫 `InsertChart`。

**Q: 若資料量很大該怎麼處理？**  
A: 餅圖最適合類別數量有限（通常 < 10）。若類別過多，建議改用長條圖或柱狀圖。

## 完整原始程式碼回顧

以下提供完整程式碼，方便直接複製貼上：

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

執行此程式即會產生前述已樣式化的餅圖 Word 文件。

## 結論

您現在已掌握如何使用 Aspose.Words **create pie chart Word** 文件、**customize pie chart colors**，以及以程式方式 **change pie slice color**。本指南涵蓋了插入圖表、填入資料、爆炸切片、套用自訂顏色與儲存結果的全部步驟。

接下來您可以探索相關主題，例如 **how to insert chart** 的其他類型、加入圖例，或產生多頁含多個圖表的報告。試著使用不同的配色方案與資料集，以符合您的報表需求。

祝開發順利！

## 接下來您可以學習什麼？

以下教學與本指南所示技巧密切相關，能進一步深化您的應用。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索替代實作方式。

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}