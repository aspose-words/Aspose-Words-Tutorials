---
category: general
date: 2026-09-21
description: 學習如何使用 C# 建立 Word 文件，插入直條圖，設定標籤位置，並透過 Aspose.Words 以逐步教學顯示數值。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: zh-hant
lastmod: 2026-09-21
og_description: 使用 Aspose.Words 於 C# 建立 Word 文件。本教學示範如何插入直條圖、設定標籤位置以及顯示數值。
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: 使用 C# 建立 Word 文件 – 插入柱狀圖、設定標籤、顯示數值
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: 如何使用 C# 建立含柱狀圖與格式化標籤的 Word 文件
url: /zh-hant/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 建立含柱狀圖與格式化標籤的 Word 文件

如果您需要 **create Word document C#** 並包含圖表，本指南將完整說明如何操作。您將學習如何插入柱狀圖、定位資料標籤，以及顯示標籤的數值——全部使用 Aspose.Words for .NET。

產生含圖表的 Word 檔案過去需要在 Microsoft Word 中手動操作。透過此處說明的 **how to insert chart** 步驟，您可以從程式碼自動化整個流程，讓報表產生快速且可重複。本教學亦涵蓋 **how to set label** 屬性與 **how to display values**，使圖表可直接供最終使用者使用。

閱讀完本篇文章後，您將擁有一個完整且可執行的 C# 程式，能產生包含柱狀圖的 `.docx` 檔案，且資料標籤會顯示在每個柱形內部並呈現數值。

## 前置條件

* 已安裝 .NET 6.0 SDK 或更新版本  
* 取得 **Aspose.Words for .NET** 的授權版（免費試用版可用於測試）  
* 使用 Visual Studio 2022 或 Visual Studio Code 等開發環境  

除了 `Aspose.Words` 之外，無需其他 NuGet 套件。

## 步驟 1：設定專案並加入 Aspose.Words

建立一個新的主控台專案，並加入 Aspose.Words 套件：

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

`dotnet add package` 指令會取得最新的穩定版 **Aspose.Words**，其中包含在 **insert column chart word** 範例中使用的圖表 API。

## 步驟 2：建立新的空白 Word 文件

以下程式碼會建立一個空白文件，並產生可用來插入內容的 `DocumentBuilder`。這是 **create word document C#** 的基礎。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 代表整個 `.docx` 檔案，而 `DocumentBuilder` 提供如 `InsertParagraph`、`InsertImage`，以及本教學最關鍵的 `InsertChart` 等方法。

## 步驟 3：插入柱狀圖（how to insert chart）

現在我們插入一個 **column chart**。`InsertChart` 方法接受圖表類型、寬度與高度（單位為點）。

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

此時圖表已包含預設的資料系列與佔位值。若需自訂數字可替換系列資料，但為示範 **how to set label** 與 **how to display values**，預設資料已足夠。

## 步驟 4：將資料標籤定位於每個柱形內部（how to set label）

資料標籤是顯示在每個柱形上的文字。為了提升圖表可讀性，我們將標籤移至柱形內部，並啟用其數值顯示。

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` 會將標籤置於柱形頂端但仍在柱形形狀內，這是報表常見的視覺樣式。將 `ShowValue` 設為 `true` 即符合 **how to display values** 的需求。

## 步驟 5：儲存文件

最後，將文件寫入磁碟。此檔案可使用 Microsoft Word、LibreOffice，或任何支援 Open XML 格式的檢視器開啟。

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

執行程式後會產生 `output.docx`，其中的柱狀圖資料標籤已定位於每個柱形內部，且顯示其數值。

### 預期結果

開啟 `output.docx` 後，您應該會看到如以下圖片所示的單一柱狀圖。每個柱形的頂部（柱形內部）都有一個數值標籤，顯示系列的值。

![Chart in a Word document created with C#](/images/word-chart-example.png "Chart in a Word document created with C# – create word document C#")

*Alt text:* *使用 C# 建立的 Word 文件中的圖表，示範如何 insert column chart word 並顯示數值。*

## 常見變化與邊緣情況

### 為圖表加入自訂資料

如果需要取代佔位資料，可修改圖表的 `Series` 集合：

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### 更改標籤字型與顏色

您還可以進一步自訂標籤的外觀：

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### 插入多個圖表

`DocumentBuilder` 可以插入任意數量的圖表。只需在使用 `builder.Writeln()` 或 `builder.InsertParagraph()` 移動游標後，再次呼叫 `InsertChart` 即可。

## 專業提示

* **Pro tip:** 設定 `chart.HasTitle = true` 並指定 `chart.Title.Text`，為圖表加入描述性標題。這可提升螢幕閱讀器的可存取性。  
* **Watch out for:** 將檔案儲存至網路共享時，請確保應用程式具備寫入權限；否則 `doc.Save` 會拋出 `UnauthorizedAccessException`。  
* **Performance tip:** 在多次插入時重複使用同一個 `DocumentBuilder` 實例；為每個操作建立新 builder 會產生不必要的開銷。

## 結論

現在您已了解如何 **create Word document C#**，其中包含柱狀圖，並掌握 **insert chart** 元素、**set label** 位置以及在每個柱形內 **display values** 的方法。上述完整程式碼範例已可直接執行，您亦可自行加入自訂資料、樣式或其他圖表進行擴充。

接下來，您可以探索相關主題，例如 **how to insert picture**、**how to generate tables**，或 **how to apply document themes**，以讓自動化報表更加豐富。祝開發愉快！

## 接下來您可以學習什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [在 Word 中使用 Aspose.Words for .NET 插入柱狀圖](/words/english/net/working-with-charts/insert-column-chart/)
- [在 Word 中使用 Aspose.Words for .NET 插入簡易柱狀圖](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [在 Word 文件中插入區域圖 | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}