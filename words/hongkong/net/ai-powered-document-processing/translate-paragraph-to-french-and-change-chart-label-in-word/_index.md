---
category: general
date: 2026-10-10
description: 將段落翻譯成法文，並學習如何變更圖表資料標籤、自訂圖表資料標籤，以及使用 Aspose.Words AI 儲存編輯過的 docx 檔案。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: zh-hant
lastmod: 2026-10-10
og_description: 將段落翻譯成法文，並學習如何變更圖表資料標籤、客製化圖表資料標籤，以及使用 Aspose.Words AI 儲存編輯過的 docx
  檔案。
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: 將段落翻譯成法文並在 Word 中更改圖表標籤
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: 將段落翻譯成法文並在 Word 中更改圖表標籤
url: /zh-hant/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將段落翻譯成法文並在 Word 中更改圖表標籤

如果您需要 **將段落翻譯成法文** 同時在同一個 Word 文件中更新圖表，本指南將一步步說明如何操作。使用 Aspose.Words AI，您可以自動翻譯文字，接著修改圖表的資料標籤，最後儲存編輯後的 `.docx` 檔案——只需簡單幾個步驟。

本教學涵蓋從載入來源檔案到持久化變更的全部流程。完成後，您將能翻譯任何段落、客製化圖表資料標籤，並產生可供發佈的新 Word 檔案。無需外部腳本；整個工作流程皆在單一 C# 程式中完成。

## 前置條件

- .NET 6.0 或更新版本（程式碼亦可在 .NET Framework 4.7+ 上執行）
- Aspose.Words for .NET 授權（或免費評估金鑰）
- 需要網際網路連線以使用 Google AI 翻譯器（`Translator` 類別在底層使用 Google 的 API）
- 一個包含至少一個段落與一個圖表的 Word 文件（`input.docx`）

## 步驟 1：設定專案並匯入命名空間

建立一個新的主控台應用程式，並加入 Aspose.Words NuGet 套件：

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

現在在 `Program.cs` 的頂部加入必要的命名空間：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

這些匯入讓您可以存取文件載入、AI 翻譯以及圖表編輯功能。

## 步驟 2：載入來源 Word 文件

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

載入檔案會建立一個記憶體中的表示，您可以在不觸碰磁碟上原始檔案的情況下查詢與修改它。

## 步驟 3：將第一段落翻譯成法文

第一段落通常是標題或簡介句子，是翻譯的好目標。`Translator` 類別抽象了對 Google AI 模型的呼叫。

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**為什麼這樣做有效：**  
`paragraph.Runs.Clear()` 會移除所有現有的文字執行序，確保新翻譯不會與舊內容串接。`new Run(document, translatedText)` 會建立一個繼承段落格式的新執行序。

## 步驟 4：定位第一個圖表並自訂其資料標籤

圖表以 `Shape` 節點（類型為 `NodeType.Shape`）儲存。第一個圖表可以透過 `GetChild` 取得。

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**關鍵步驟說明：**

- `GetChild(NodeType.Shape, 0, true)` 進行深度優先搜尋，回傳第一個形狀，在本例中即為圖表。
- `ChartSeries` 代表資料點集合；第一個系列 (`Series[0]`) 通常對應主要資料集。
- `ChartDataLabelPosition.OutsideEnd` 將標籤移至長條圖末端之外，提高可讀性。
- 將 `dataLabel.Text` 設為法文字串，使標籤與已翻譯的段落保持一致。

## 步驟 5：儲存含有翻譯段落的文件

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

此時文件已包含法文段落，但仍保留原始的圖表設定。

## 步驟 6：儲存已更新圖表的文件

您可以直接重複使用同一個 `Document` 實例——無需重新載入——因為圖表的修改已在記憶體中完成。

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

兩個檔案現在皆可供發佈：

- **`translated.docx`** – 包含法文段落。
- **`chart-updated.docx`** – 包含法文段落 *以及* 已自訂的圖表標籤。

## 完整、可執行的範例

以下是完整程式碼，您可以直接複製貼上到 `Program.cs`。只要將 `YOUR_DIRECTORY` 替換為實際的資料夾路徑，即可編譯並執行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

namespace WordAiDemo
{
    class Program
    {
        static void Main()
        {
            // ---------- Load the source document ----------
            string inputPath = @"YOUR_DIRECTORY/input.docx";
            Document document = new Document(inputPath);
            Console.WriteLine("Document loaded.");

            // ---------- Translate the first paragraph ----------
            Paragraph paragraph = document.FirstSection.Body.FirstParagraph;
            string original = paragraph.GetText();
            string translated = Translator.Translate(original, Language.French);
            Console.WriteLine


## 接下來該學什麼？

以下教學涵蓋與本指南技術緊密相關的主題，並在此基礎上進一步延伸。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [自訂圖表資料標籤](/words/english/net/programming-with-charts/chart-data-label/)
- [格式化圖表資料標籤的數字](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [圖表資料標籤](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}