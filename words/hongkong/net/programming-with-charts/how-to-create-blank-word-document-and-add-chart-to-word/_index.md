---
category: general
date: 2026-09-08
description: 使用 Aspose.Words 建立空白 Word 文件並加入圖表。了解如何插入雷達圖、啟用刻度，並儲存檔案。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: zh-hant
lastmod: 2026-09-08
og_description: 使用 Aspose.Words 建立空白 Word 文件並加入圖表。本教學示範如何插入雷達圖、設定坐標軸，並儲存文件。
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: 建立空白 Word 文件並新增雷達圖 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: 如何建立空白 Word 文件並在 Word 中加入圖表
url: /zh-hant/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何建立空白 Word 文件並在 Word 中加入圖表

如果您需要 **create blank Word document** 來製作報告、範本或自動合併，此指南將以 C# 及 Aspose.Words 帶您完成整個流程。您還會學習如何 **add chart to Word**，特別是 **insert radar chart**，開啟 graduations，並將結果儲存為 .docx 檔案。

本教學涵蓋從專案設定到最終驗證的所有步驟。完成後，您將擁有可直接嵌入任何 .NET 應用程式的可重用程式碼片段。無需事先具備 Aspose.Words 的使用經驗，但您應具備基本的 C# 知識並已安裝最新的 .NET SDK。

## 前置條件

- .NET 6.0 SDK 或更新版本  
- Aspose.Words for .NET（NuGet 套件 `Aspose.Words`）  
- 如 Visual Studio 2022 或 VS Code 等 IDE  
- 具有寫入文件將被儲存之資料夾的權限  

您可以使用以下指令安裝此函式庫：

```bash
dotnet add package Aspose.Words
```

## 步驟 1：建立空白 Word 文件

第一步是在記憶體中 **create blank Word document**。`Document` 類別代表整個檔案，而 `DocumentBuilder` 提供用於加入內容的流暢 API。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` 起始為空白，因此您擁有一個乾淨的畫布可放置圖表。此階段保持文件空白，可輕鬆將相同程式碼重複使用於不同範本。

## 步驟 2：在 Word 中加入圖表

接著，我們透過呼叫 `InsertChart` **add chart to Word**。此方法需要圖表類型以及以點 (point) 為單位的尺寸 (1 point = 1/72 吋)。

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` 告訴 Aspose.Words 產生徑向圖表，適合以圓形佈局呈現多變量資料。尺寸值 (400 × 300) 適用於大多數直向頁面，您亦可依需求調整。

## 步驟 3：插入雷達圖表並設定 graduations

現在我們 **insert radar chart**，並在類別 (X) 與數值 (Y) 軸上啟用 graduations（刻度）。graduations 透過顯示每個資料點的精確位置提升可讀性。

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

將 `HasGraduations` 設為 `true` 會在軸上繪製刻度線。可選的 `GraduationStep` 控制徑向軸上刻度之間的間距；設定為 10 表示每 10 度一個刻度。

### 小技巧
若需顯示資料標籤，可呼叫 `radarChart.Series[0].HasDataLabel = true;`。此設定會在每個點旁顯示數值，對簡報相當有幫助。

## 步驟 4：以範例資料填充圖表（可選）

沒有資料的雷達圖表不會顯示。以下提供快速加入一系列範例值的方法。您可以將此區塊替換為自己的資料來源。

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

每次呼叫 `Add` 皆會將一個點加入系列。點的順序對應圓周上的角度位置。

## 步驟 5：儲存包含圖表的文件

最後，將文件寫入磁碟。`Save` 方法會自動產生 .docx 檔，保留圖表及所有格式設定。

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

執行程式會產生一個 **blank Word document**，其中已包含完整功能的雷達圖表。於 Microsoft Word 開啟檔案即可查看結果。

![Radar chart in Word document](radar_chart.png){alt="雷達圖表已插入空白 Word 文件"}

## 常見變化與例外情況

| 情況 | 需要變更的項目 |
|-----------|----------------|
| **不同的圖表尺寸** | 調整 `InsertChart` 的寬度/高度參數。 |
| **其他圖表類型** | 將 `ChartType.Radar` 替換為 `ChartType.Column`、`ChartType.Pie` 等，並保留相同的 graduation 邏輯。 |
| **儲存至串流** | 使用 `document.Save(Stream, SaveFormat.Docx)` |

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並在此基礎上延伸技巧。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [在 Word 文件中插入區域圖表 | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [使用 Aspose.Words for .NET 建立 Word 散點圖表](/words/english/net/working-with-charts/insert-scatter-chart/)
- [在 Word 中使用 Aspose.Words for .NET 插入直條圖表](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}