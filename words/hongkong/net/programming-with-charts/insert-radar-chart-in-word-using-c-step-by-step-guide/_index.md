---
category: general
date: 2026-09-14
description: 使用 C# 在 Word 中插入雷達圖。學習如何設定圖表標題、加入多個系列，並僅用幾行程式碼以程式方式建立圖表。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert radar chart
- set chart title
- create radar chart word
- multiple series radar chart
- create chart programmatically
language: zh-hant
lastmod: 2026-09-14
og_description: 使用 C# 在 Word 中插入雷達圖。本教學示範如何設定圖表標題、加入多個系列，並以程式方式建立圖表。
og_image_alt: Screenshot of a Word document displaying a radar chart with sales data
og_title: 使用 C# 在 Word 中插入雷達圖 – 快速程式設計指南
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Insert radar chart in Word with C#. Learn how to set chart title, add
    multiple series, and create the chart programmatically in just a few lines.
  headline: Insert radar chart in Word using C# – step‑by‑step guide
  type: TechArticle
tags:
- radar chart
- C#
- Aspose.Words
title: 使用 C# 在 Word 中插入雷達圖 – 逐步指南
url: /zh-hant/net/programming-with-charts/insert-radar-chart-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 C# 插入雷達圖 – 步驟指南

如果您需要 **在 Word 文件中插入雷達圖**，本指南將教您如何使用 C# 程式化地完成此操作。您還會學會 **設定圖表標題**、加入 **多系列雷達圖**，以及在不離開 IDE 的情況下儲存檔案。

本教學涵蓋從專案設定到最終 `doc.Save` 呼叫的全部步驟，您可以直接複製貼上完整範例並立即執行。無需查閱額外文件。

## 前置條件

在開始之前，請確保您已具備：

* 已安裝 .NET 6（或更新版本）。
* 有效的 Aspose.Words for .NET 授權（或臨時評估金鑰）。
* Visual Studio 2022 或您偏好的任何 C# IDE。

> **專業提示：** 若使用免費試用版，請務必在第一次建立 `Document` 之前設定授權，以免出現評估浮水印。

## 步驟 1：在 Word 文件中插入雷達圖

第一步是建立新的 `Document` 與 `DocumentBuilder`。Builder 讓您存取文件內容，並能將 **雷達圖** 精確放置在需要的位置。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank Word document.
Document doc = new Document();

// DocumentBuilder provides methods to insert content.
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a radar (radial) chart at the current cursor position.
Chart chart = builder.InsertChart(ChartType.Radar);
```

*此步驟的重要性：* `InsertChart` 會建立一個圖表物件，您可以在文件儲存前完整設定。使用 `ChartType.Radar` 會告訴 Word 以徑向圖表方式呈現，而非柱狀圖或折線圖。

## 步驟 2：設定圖表標題與座標軸刻度

沒有標題的圖表會讓人感到困惑。此處我們 **設定圖表標題** 為「Sales Radar」，並在兩個座標軸上啟用刻度（自 Aspose.Words 24.9 起支援）。

```csharp
// Give the chart a meaningful title.
chart.Title.Text = "Sales Radar";

// Enable graduations (grid lines) on both X and Y axes.
chart.AxisX.HasGraduations = true;
chart.AxisY.HasGraduations = true;
```

*此步驟的重要性：* 標題為讀者提供上下文，刻度則透過顯示每個資料點所在的比例，提高可讀性。

## 步驟 3：為雷達圖建立多系列

**多系列雷達圖** 讓您能夠將不同期間的資料並排比較。以下範例加入兩個系列——Q1 與 Q2——各自包含三個資料點。

```csharp
// Series 1: Q1 data.
chart.Series.Add(
    "Q1",                                 // Series name
    new[] { "Jan", "Feb", "Mar" },        // Category labels
    new[] { 10, 20, 30 }                  // Values
);

// Series 2: Q2 data.
chart.Series.Add(
    "Q2",
    new[] { "Jan", "Feb", "Mar" },
    new[] { 15, 25, 35 }
);
```

*此步驟的重要性：* 加入多個系列示範了如何在同一雷達圖上比較資料集，這在銷售、績效或調查結果的分析中相當常見。

## 步驟 4：以程式方式儲存 Word 文件

最後，您 **以程式方式建立圖表** 並將文件寫入磁碟。`Save` 方法會產生一個 `.docx` 檔，可於 Microsoft Word 中開啟。

```csharp
// Define the output path. Adjust the directory as needed.
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "RadialGraduations.docx"
);

// Save the document containing the radar chart.
doc.Save(outputPath);
```

當您開啟 `RadialGraduations.docx` 時，會看到一個標題為「Sales Radar」的雷達圖，圖中包含兩個系列（Q1 與 Q2），資料對應至 1 月至 3 月。

### 預期輸出

![Radar chart in Word](https://example.com/radar-chart.png){: .align-center alt="顯示兩個資料系列的雷達圖之 Word 文件"}

此螢幕截圖（或實際檔案）證實圖表已正確插入、設定標題並填入資料。

## 完整可執行範例

將所有步驟整合後，以下是一個可自行編譯執行的完整程式：

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a radar chart.
        Chart chart = builder.InsertChart(ChartType.Radar);

        // 3. Set chart title and enable axis graduations.
        chart.Title.Text = "Sales Radar";
        chart.AxisX.HasGraduations = true;
        chart.AxisY.HasGraduations = true;

        // 4. Add two data series.
        chart.Series.Add("Q1", new[] { "Jan", "Feb", "Mar" }, new[] { 10, 20, 30 });
        chart.Series.Add("Q2", new[] { "Jan", "Feb", "Mar" }, new[] { 15, 25, 35 });

        // 5. Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialGraduations.docx"
        );
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

執行程式、開啟產生的檔案，即可驗證 **插入雷達圖** 的操作是否成功。

## 常見問題與邊緣情況

| Question | Answer |
|----------|--------|
| **Can I change the chart type after insertion?** | Yes. After `InsertChart`, assign a new `ChartType` to `chart.Type`. However, creating the chart with the correct type from the start is more efficient. |
| **What if I need more than two series?** | Call `chart.Series.Add` for each additional series. The chart will automatically adjust the legend and colors. |
| **How do I customize colors or markers?** | Use `chart.Series[i].Format.Fill.ForeColor` for fill colors and `chart.Series[i].Marker` for marker styles. |
| **Is the API compatible with .NET Framework?** | The same code works with .NET Framework 4.7+; just reference the appropriate Aspose.Words DLL. |
| **What if I’m using an older Aspose.Words version?** | Graduations (`HasGraduations`) were introduced in 24.9. For older versions, you can manually add grid lines using `chart.AxisX.MajorGridLines` and `chart.AxisY.MajorGridLines`. |

## 結論

現在您已掌握如何使用 C# **在 Word 中插入雷達圖**、**設定圖表標題**、加入 **多系列雷達圖**，以及 **以程式方式建立圖表**。此端到端解決方案可協助您自動化報表、儀表板或任何需要類別視覺比較的情境。

接下來，您可以探索以下相關主題，如 **自訂圖表顏色**、**將圖表匯出為影像**，或 **在 PDF 檔案中嵌入圖表**。嘗試不同的資料集，觀察雷達視覺化的變化。

祝開發順利！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並提供完整可執行的程式碼範例與逐步說明，協助您在專案中深入掌握更多 API 功能與替代實作方式。

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}