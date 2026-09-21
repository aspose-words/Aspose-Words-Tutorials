---
category: general
date: 2026-09-21
description: 學習如何使用 Aspose.Words 建立圓餅圖並將圖表插入 Word、為圓餅圖加入資料標籤，以及在圓餅圖上顯示百分比，只需幾個步驟。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: zh-hant
lastmod: 2026-09-21
og_description: 使用 Aspose.Words 在 Word 中建立圓餅圖、將圖表插入 Word、為圓餅圖新增資料標籤，並在圓餅圖上顯示百分比——全部提供清晰的程式碼範例。
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: 使用 Aspose.Words 在 Word 中建立圓餅圖 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: 如何使用 Aspose.Words 在 Word 文件中建立圓餅圖
url: /zh-hant/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 Aspose.Words 建立餅圖

如果您需要 **程式化建立餅圖**，Aspose.Words 讓這個過程變得簡單。在本教學中，您將會看到如何 **在 Word 中插入圖表**、設定系列、**為餅圖新增資料標籤**，以及最後 **在餅圖上顯示百分比**，讓視覺效果能傳達精確數值。完成後，您將擁有一個完整、可執行的範例，能直接放入任何 .NET 專案中使用。

本指南涵蓋您需要了解的所有內容：必要的 NuGet 套件、完整的 C# 原始碼、每個 API 呼叫的重要性說明，以及自訂圖表的技巧。無需參考外部文件——只要複製、執行、再依需求調整即可。

## 前置條件

開始之前，請確保您已具備以下環境：

* 已安裝 .NET 6.0 SDK 或更新版本。  
* Visual Studio 2022（或任何支援 .NET 的 IDE）。  
* Aspose.Words for .NET 授權（免費試用版可用於測試）。  
* 具備 C# 基礎知識與 Word 文件結構的概念。

如果您已滿足上述條件，請直接進入程式碼部分。

## 第一步：建立專案並匯入 Aspose.Words

建立一個新的 Console 專案，並加入 Aspose.Words NuGet 套件：

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

此套件包含 `Aspose.Words.Drawing.Charts` 命名空間，裡面有我們將使用的 `Chart` 與 `ChartSeries` 類別。

> **專業提示：** 將授權檔 (`Aspose.Words.lic`) 放在專案根目錄，並在程式啟動時載入，以避免評估水印。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## 第二步：建立空白文件與 DocumentBuilder

`Document` 代表 Word 檔案，而 `DocumentBuilder` 提供流暢的 API 以插入內容。

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**為什麼這很重要：** `DocumentBuilder` 會維持目前的插入點，確保圖表正確出現在文件流程中的預期位置。

## 第三步：在 Word 文件中插入餅圖

現在我們 **在 Word 中插入圖表**。`InsertChart` 方法接受圖表類型、寬度與高度（以點為單位）。

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

此時圖表已包含一個預設資料系列，佔位值為 (25, 25, 25, 25)。之後您可以自行替換。

## 第四步：存取第一個系列並自訂資料標籤

餅圖通常只有一個系列。為了 **為餅圖新增資料標籤**，我們先取得該系列，並啟用百分比顯示。

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**為什麼要設定 `ShowPercentage`：** 此旗標會指示 Aspose.Words 計算每個切片的比例，並以百分比方式呈現。`Position` 屬性則確保標籤不會與切片重疊，提升可讀性——尤其在切片較小時更為重要。

## 第五步：（可選）取代佔位資料

若您想使用特定數值，只需替換預設的點：

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

顯示的百分比會自動根據新數值重新計算。

## 第六步：儲存文件

最後，將文件寫入磁碟。副檔名會決定檔案格式；`.docx` 會產生現代的 Word 檔案。

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

執行程式後，會在輸出資料夾產生名為 **PieChart.docx** 的檔案。使用 Microsoft Word 開啟後，您會看到每個切片都以百分比標示，且標籤位於切片外側。

### 預期輸出

開啟產生的文件時，您應該會看到：

* 一個尺寸為 400 × 300 pt 的單一餅圖。  
* 四個切片（或您自行加入的點數）。  
* 如「40 %」、「30 %」等百分比標籤，顯示於每個切片外側。

如果標籤出現在切片內部，請再次確認已正確設定 `ChartDataLabelPosition.OutsideEnd`。

## 第七步：常見變形與例外情況

### 為圖表加入標題

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### 更改切片顏色

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### 處理空的系列

若資料來源可能為空，請避免 `IndexOutOfRangeException`：

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### 匯出為 PDF 而非 Word

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

圖表繪製邏輯相同；Aspose.Words 會自動將 Word 版面轉換為 PDF。

## 完整原始碼清單

以下是完整、可直接執行的程式碼。將其複製到 `Program.cs`，然後執行 `dotnet run`。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## 結論

現在您已掌握如何使用 Aspose.Words **在 Word 檔案中建立餅圖**、**插入圖表**、**為餅圖新增資料標籤**，以及 **在餅圖上顯示百分比**。此範例示範了從專案設定到最終文件的完整工作流程，讓您能將其套用於儀表板、報告或自動化發票產生等情境。

接下來，您可以探索相關主題，例如 **在圖例中顯示百分比**、自訂圖表顏色，或將 Word 文件轉換為 PDF 以便分發。嘗試使用相同的 `InsertChart` 方法建立其他圖表類型（長條圖、折線圖），擴展您的自動化能力。

祝您圖表製作愉快！


## 接下來該學什麼？

以下教學與本指南緊密相關，能在此基礎上進一步深化技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索不同的實作方式。

- [在 Word 中使用 Aspose.Words for .NET 插入直條圖](/words/english/net/working-with-charts/insert-column-chart/)
- [使用 Aspose.Words for .NET 建立 Word 散點圖](/words/english/net/working-with-charts/insert-scatter-chart/)
- [在 Word 文件中插入區域圖 | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}