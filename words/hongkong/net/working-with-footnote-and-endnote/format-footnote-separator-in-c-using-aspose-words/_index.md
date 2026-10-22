---
category: general
date: 2026-08-10
description: 使用 Aspose.Words 於 C# 格式化腳註分隔線，以自訂腳註與尾註的線條。數分鐘內學會 C# 腳註格式設定。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: zh-hant
lastmod: 2026-08-10
og_description: 使用 Aspose.Words 在 C# 中格式化腳註分隔線。遵循本教學快速且可靠地設定腳註與尾註分隔線的樣式。
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: 在 C# 中格式化腳註分隔線 – 完整 Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: 使用 Aspose.Words 在 C# 中格式化腳註分隔符
url: /zh-hant/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words 在 C# 中格式化腳註分隔線

如果您需要在 Word 文件中 **格式化腳註分隔線**，本指南將示範如何使用 Aspose.Words for .NET 來完成。您將看到一個完整且可執行的範例，該範例會變更分隔段落的對齊方式與顏色，並學會將相同技巧套用於尾註分隔線。

本教學涵蓋每一步——從載入來源檔案到儲存修改後的文件——讓您可以直接複製貼上程式碼到自己的專案，無需額外研究。

## 您需要的條件

* .NET 6.0 或更新版本（此程式碼亦可於 .NET Framework 4.6+ 執行）
* 有效的 Aspose.Words for .NET 授權（免費試用版可用於評估）
* 包含至少一個腳註或尾註的 Word 檔案（例如 `Footnotes.docx`）
* Visual Studio 2022 或您偏好的任何 C# IDE

準備好上述項目後，您即可專注於 **C# 腳註格式化** 的邏輯，而不必擔心環境設定。

## 步驟 1：載入包含腳註與尾註的文件

第一步是建立指向來源檔案的 `Document` 物件。Aspose.Words 會將整個 DOCX 套件讀入記憶體，讓您完整存取腳註與尾註節點。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*為何重要*：載入文件是任何操作的前提。如果檔案路徑錯誤，Aspose.Words 會拋出 `FileNotFoundException`，因此請在繼續之前確認路徑正確。

## 步驟 2：取得分隔線與持續分隔線節點

腳註與尾註的分隔線以特殊節點儲存在 `Footnotes` 與 `Endnotes` 集合中。每個集合皆提供 `Separator` 與 `ContinuationSeparator` 屬性，回傳 `Node` 參考。

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*為何重要*：`Separator` 節點代表視覺上將主文字與腳註區塊分隔的線。取得該參考後，您可以修改其段落格式、字型，甚至完全取代該節點。

## 步驟 3：變更腳註分隔線的視覺樣式

在大多數 Word 文件中，分隔線是一個包含破折號或星號的單一段落。以下程式碼會檢查分隔線是否為 `Paragraph`，若是則將其置中並將文字顏色改為灰色。

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### 為持續分隔線設定樣式（可選）

當腳註跨越多頁時，會出現持續分隔線。您可以以類似方式設定其樣式：

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*為何重要*：對齊分隔線可提升可讀性，變更顏色則能使其與一般段落文字區分。您可以將 `ParagraphAlignment.Center` 替換為 `Left` 或 `Right`，以符合文件的設計指南。

## 步驟 4：儲存修改後的文件

套用所需樣式後，將文件寫回磁碟。您可以覆寫原始檔案或建立新版本。

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

當您在 Microsoft Word 中開啟 `Footnotes_Styled.docx` 時，腳註分隔線會置中且呈灰色，正如程式碼所指定的那樣。

## 進階變化

### 格式化尾註分隔線

如果您的文件同時使用尾註，您可以將相同的邏輯套用到 `Endnotes` 集合：

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### 使用自訂字串作為分隔線

有時您希望分隔線使用一串星號（`***`）。可將現有的 runs 替換為新的 run：

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### 處理沒有分隔線節點的文件

罕見的邊緣情況是文件省略了分隔線節點（例如作者刪除時）。此時 `document.Footnotes.Separator` 會回傳 `null`，需加以防護：

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## 常見陷阱與避免方法

| 問題 | 發生原因 | 解決方式 |
|---------|----------------|-----|
| **分隔線不是 `Paragraph`** | 某些 Word 範本使用 `Table` 或 `Shape` 作為分隔線。 | 在轉型前使用 `is Paragraph` 檢查節點類型。 |
| **`Runs` 集合為空** | 分隔線可能是空的段落。 | 在存取 `Runs[0]` 前確認 `Runs.Count > 0`。 |
| **未套用授權** | 若未授權，Aspose.Words 會插入浮水印且可能限制 API 使用。 | 在程式開始時呼叫 `License license = new License(); license.SetLicense("Aspose.Words.lic");`。 |
| **儲存至唯讀資料夾** | `Save` 方法會拋出 `UnauthorizedAccessException`。 | 確保目標目錄具有寫入權限。 |

提前處理這些問題可避免執行時例外，確保順利的 **修改腳註分隔線** 體驗。

## 完整、可執行的範例

以下是一個獨立的主控台應用程式，示範上述所有步驟。將程式碼複製到新的 .NET 主控台專案，替換檔案路徑後執行即可。

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**預期結果**  

當您開啟 `Footnotes_Styled.docx` 時：

* 腳註分隔線位於主文字下方且置中。  
* 其顏色為淡灰色，視覺上與一般文字區分。  
* 若文件包含尾註，其分隔線亦會置中並呈灰色（或石板色）。

## 接下來您可以學習什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可運作的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [使用腳註與尾註的文字處理](/words/english/net/working-with-footnote-and-endnote/)
- [設定腳註與尾註位置](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [使用腳註與尾註](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}