---
category: general
date: 2026-08-07
description: 快速在 C# 中建立圓餅圖。學習如何插入圓餅圖、加入資料標籤、顯示百分比圖表，並自訂圖表資料標籤。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: zh-hant
lastmod: 2026-08-07
og_description: 使用 Aspose.Words 在 C# 中建立圓餅圖。此教學示範如何插入圓餅圖、加入資料標籤、顯示百分比圖表，同時自訂圖表資料標籤。
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: 在 C# 中建立圓餅圖 – 完整教學
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: 使用 C# 在 Word 中建立圓餅圖 – 步驟指南
url: /zh-hant/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中建立圓餅圖 Word 文件 – 步驟說明指南

如果您需要在 C# 中 **create pie chart word** 文件，本指南提供完整、可直接執行的解決方案。您將會看到如何 **insert pie chart**、**add data labels pie**，以及 **show percentage chart**，同時 **customize chart data labels** 以獲得精緻的外觀。

以程式方式產生圖表可避免手動編輯，尤其在必須自動產出報表或儀表板時更為便利。以下各節將教您如何使用 Aspose.Words for .NET，將完整標註的圓餅圖嵌入 Word 檔案中。

## 前置條件與設定

在開始之前，請確保您已具備：

* 已安裝 .NET 6.0 SDK 或更新版本。  
* 有效的 Aspose.Words for .NET 授權（或暫時的評估金鑰）。  
* Visual Studio 2022（或任何支援 C# 的 IDE）。  

將 Aspose.Words NuGet 套件加入您的專案：

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** 若您計畫產生大量圖表，請啟用 **Free‑Form Drawing** 模式 (`DocumentBuilder.UseFreeFormDrawing = true`) 以提升效能。

## 使用 Aspose.Words 建立 pie chart word

第一個主要步驟是建立一個空白的 Word 文件與 `DocumentBuilder` 物件。此物件負責後續的所有插入動作。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters*: `Document` 代表整個 `.docx` 檔案，而 `DocumentBuilder` 提供流暢的 API 以加入段落、表格與圖表。從乾淨的文件開始，可避免隱藏格式干擾圖表版面。

## 在文件中插入圓餅圖

現在我們放置一個指定尺寸的圓餅圖。`InsertChart` 方法會回傳一個 `Chart` 物件，之後可進一步設定。

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Why this matters*: `ChartType.Pie` 旗標告訴 Aspose.Words 產生圓形圖表。寬度 (`400`) 與高度 (`300`) 以點為單位，讓您精確控制視覺佔用空間。

## 為圖表填入資料

圓餅圖至少需要一組數值系列。此處我們加入三個類別：「Apples」、「Bananas」與「Cherries」。

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Why this matters*: 每次呼叫 `AddCategory` 都會產生一個切片。數值決定切片大小，標籤則成為開啟資料標籤時顯示的類別名稱。

## 加入資料標籤圓餅圖並顯示百分比圖表

為了讓圖表資訊更完整，我們啟用資料標籤、將它們放在切片外側，並要求 Aspose.Words 同時顯示類別名稱與百分比。

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Why this matters*: 將 `Position` 設為 `OutsideEnd` 可提升可讀性，特別是切片較小時。啟用 `ShowCategoryName` 與 `ShowPercentage` 同時滿足 **show percentage chart** 的需求，也符合 **add data labels pie** 的目標。

## 進一步自訂圖表資料標籤（可選）

您可能想變更字型、加入指引線，或隱藏圖例。以下程式碼示範常見的自訂方式：

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Why this matters*: 調整標籤外觀可確保圖表符合文件的樣式指南。移除圖例可減少視覺雜訊，因為資料標籤已傳達相同資訊。

## 儲存含自訂圖表的文件

最後，將文件寫入磁碟。請選擇您具有寫入權限的路徑。

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

當您在 Microsoft Word 中開啟 `ChartWithCustomLabels.docx` 時，會看到一個圓餅圖，每個切片皆以類別名稱與百分比標示，且標籤位於切片外側，字型使用自訂設定。

### 預期輸出

| 切片   | 數值 | 百分比 | Word 中顯示的標籤 |
|--------|------|--------|-------------------|
| 蘋果   | 40   | 40 %   | 蘋果 – 40 %       |
| 香蕉   | 35   | 35 %   | 香蕉 – 35 %       |
| 櫻桃   | 25   | 25 %   | 櫻桃 – 25 %       |

圖表應與下方示意圖相似：

![Word 文件顯示每個切片外側帶百分比標籤的圓餅圖](pie-chart-word.png "建立圓餅圖 Word 範例")

*Image alt text includes the primary keyword for SEO.*

## 處理多系列與邊緣情況

基本範例使用單一系列，這是圓餅圖的常見做法。若需顯示多個系列（例如比較兩個年度），必須：

1. 為每個額外系列呼叫 `chart.Series.Add()`。  
2. 確保每個系列使用相同的類別；否則 Aspose.Words 會拋出 `ArgumentException`。  
3. （可選）設定 `labels.ShowSeriesName = true` 以區分切片。

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

當存在多個系列時，圖表會自動呈現為 **clustered pie**（亦稱「pie of pies」）。請檢查輸出，確保標籤仍然清晰可讀。

## 常見陷阱與避免方法

| 問題 | 原因 | 解決方式 |
|------|------|----------|
| 標籤與切片重疊 | 圖表區域太小或類別過多 | 增加圖表尺寸（`InsertChart(width, height)`）或改為 `InsideEnd` 位置。 |
| 百分比總和未達 100 % | 資料四捨五入誤差 | 使用 `labels.ShowPercentage = true`（Aspose.Words 會自動正規化）。 |
| 圖表在 Word 中顯示為空白 | 授權缺失或評估期限到期 | 確保在建立文件前已載入有效的 Aspose.Words 授權。 |
| 字型顏色與 Word 主題不符 | 程式碼中設定了自訂字型 | 移除自訂字型設定，或使用 Word 主題顏色（`System.Drawing.Color.Black`）。 |

## 完整原始碼（可執行）

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

執行程式後會產生 `ChartWithCustomLabels.docx`，其中包含一個符合本教學所有需求的 **create pie chart word** 範例。

## 結論

您現在已掌握如何使用 Aspose.Words 於 C# 中 **create pie chart word** 文件。本指南說明了插入圓餅圖、**add data labels pie**、**show percentage chart**，以及 **customize chart data labels**，讓您能產出專業且以資料驅動的 Word 檔案。  

接下來，您可以探索相關主題，例如將 **insert pie chart** 插入既有段落、產生 **bar** 或 **line** 圖表，或自動批次產生含不同資料集的報表。嘗試不同的標籤位置、字型樣式與多系列設定，以符合您的特定報告需求。

祝您製圖愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，或在自己的專案中探索替代實作方式。

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}