---
category: general
date: 2026-07-26
description: 使用 Aspose.Words 在 Word 文件中插入餅圖。只需幾個步驟，即可學會如何加入圖表、將切片分離以及顯示百分比。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: zh-hant
lastmod: 2026-07-26
og_description: 使用 Aspose.Words 在 Word 檔案中插入圓餅圖。遵循本指南，即可快速學習如何新增圖表、分離切片及顯示百分比。
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: 在 Word 中插入圓餅圖 – Aspose.Words 逐步教學
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: 使用 Aspose.Words 在 Word 中插入圓餅圖 – 完整指南
url: /zh-hant/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中插入圓形圖表 – 完整指南

有沒有曾經需要 **插入圓形圖表** 到 Word 報告中，但不知從何下手？你並不孤單。在許多商業應用程式中，圓形圖表的視覺衝擊能讓資料即時易於理解，而 Aspose.Words 只需幾行程式碼即可實現這一點。

在本教學中，我們將逐步說明如何 **將圖表加入 Word**、將切片「爆炸」以強調重點，並在資料標籤上顯示百分比。完成後，你將擁有一個可直接執行的範例，能夠放入任何 .NET 專案中。

---

## 前置條件

- .NET 6.0 或更新版本（此程式碼同時適用於 .NET Core 與 .NET Framework）
- 已安裝 Aspose.Words for .NET NuGet 套件  
  ```bash
  dotnet add package Aspose.Words
  ```
- 具備基本的 C# 語法概念——不需要進階知識
- 任意你喜好的 IDE（Visual Studio、Rider 或 VS Code）

就這樣。讓我們動手實作吧。

---

## 在 Word 文件中插入圓形圖表

我們首先需要一個全新的 `Document` 物件以及一個 `DocumentBuilder`。可以把 Builder 想像成直接在 Word 畫布上書寫的筆。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **為什麼這很重要：** `Document` 代表整個 .docx 檔案，而 `DocumentBuilder` 為我們提供了便利的 API，可插入圖表、表格與文字等元素。這是每個 **如何加入圖表** 操作的基礎。

---

## 如何將圖表加入 Word

既然已有 Builder，我們現在可以實際 **插入圓形圖表**。`insertChart` 方法接受圖表類型以及以點 (point) 為單位的尺寸（1 點 = 1/72 英吋）。

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **提示：** 若需要不同尺寸，只要調整寬度與高度的數值即可。圖表會自動縮放以符合頁面邊界。

---

## 如何將切片「爆炸」以強調

常見的視覺調整是「爆炸」某個切片，使其從圓形中凸顯出來，從而吸引讀者注意最重要的區段。

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **為什麼要爆炸切片？** 當你想突顯特定類別——例如財務報告中的「第一季營收」——將切片爆炸即可立即引起注意，無需額外文字說明。

---

## 如何在資料標籤上顯示百分比

大多數圓形圖表在每個切片顯示其百分比時更具可讀性。Aspose.Words 只需透過單一屬性即可開啟此功能。

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **快速說明：** `ShowPercentage` 旗標會套用於系列中的所有資料點，無需對每個切片分別設定。

---

## 儲存包含圖表的文件

最後，我們將文件寫入磁碟。選擇任意資料夾即可，只要確保路徑已存在。

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

當你在 Microsoft Word 中開啟 `PieChart.docx` 時，會看到一個完美呈現的圓形圖表，第一個切片已被爆炸，且顯示百分比——正是精緻商業報告所應有的效果。

---

## 完整可執行範例

以下是完整、可直接複製貼上的程式碼。以主控台應用程式執行，並驗證輸出檔案。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**預期結果：** 開啟產生的 `PieChart.docx`。你會看到一個三切片的圓形圖表，標題為「Sales Q1」，第一個切片被拉出，且每個切片分別標示「30 %」、「45 %」與「25 %」。視覺效果與我們提供的資料相符。

---

## 常見問題與邊緣情況

- **如果需要多於一個系列呢？**  
  只要向 `chart.Series` 新增額外的 `ChartSeries` 物件即可。每個系列可擁有自己的資料集、顏色與爆炸設定。

- **我可以更改圖表的顏色嗎？**  
  可以。每個 `ChartPoint` 都有 `Format.Fill.ForeColor` 屬性，你可以將其設定為任意 `System.Drawing.Color`。

- **其他圖表類型呢？**  
  `ChartType` 列舉包含長條圖、折線圖、環形圖等多種。只要將 `ChartType.Pie` 替換為你需要的圖表類型即可。

- **插入後圖表在 Word 中可編輯嗎？**  
  當然可以。Word 會將圖表視為原生 Office 圖表，使用者只要雙擊即可開啟內建的圖表編輯器。

---

## 結論

現在你已完全掌握如何使用 Aspose.Words **插入圓形圖表** 到 Word 文件、**將圖表加入 Word**、**爆炸切片**，以及 **在資料標籤上顯示百分比**。上述完整範例已可直接執行，你亦可依需求加入自訂資料、樣式或額外系列。

準備好進一步了嗎？試著將圓形圖表換成環形圖，或自動產生一批使用不同資料集的報告。如果你對其他視覺化圖表感興趣，請參考我們關於 **如何加入圖表**（條形圖與折線圖）的指南，或探索 **將圖表加入 Word** 的 API 參考文件，以進行更深入的客製化。

祝程式開發愉快，願你的文件如同完美切割的圓形圖表般清晰明瞭！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [在 Word 中插入直條圖（使用 Aspose.Words for .NET）](/words/english/net/working-with-charts/insert-column-chart/)
- [在 Word 文件中插入區域圖表 | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [使用 Aspose.Words for .NET 建立 Word 散佈圖](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}