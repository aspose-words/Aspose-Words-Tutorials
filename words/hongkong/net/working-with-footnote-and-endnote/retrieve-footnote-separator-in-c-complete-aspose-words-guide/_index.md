---
category: general
date: 2026-08-07
description: 使用 Aspose.Words for .NET 取得腳註分隔線。了解如何提取腳註與尾註分隔線、檢查節點類型，並在 C# 中修改它們。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: zh-hant
lastmod: 2026-08-07
og_description: 使用 Aspose.Words for .NET 取得腳註分隔符。本指南示範如何提取腳註與尾註分隔符、檢查它們的節點類型，並儲存更改。
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: 在 C# 中取得腳註分隔線 – 逐步 Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: 在 C# 中取得腳註分隔符 – 完整 Aspose.Words 指南
url: /zh-hant/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中檢索腳註分隔符 – 完整 Aspose.Words 指南

如果您需要從 Word 文件中**檢索腳註分隔符**，本教學將向您展示如何使用 Aspose.Words for .NET 完成此操作。無論您是構建文件處理服務還是清理腳註格式，您都會看到一個完整、可執行的範例，提取腳註和尾註的分隔符。

在本指南中，您將學會如何載入 `.docx` 檔案、呼叫 `FootnoteSeparator` 與 `EndnoteSeparator` 屬性、檢查回傳的 `Node` 物件，並可選擇性地取代分隔線。無需額外文件說明——以下即提供全部所需內容。

## 前置條件

* .NET 6.0 或更新版本（程式碼亦相容於 .NET Framework 4.7.2）
* Aspose.Words for .NET NuGet 套件（版本 24.9 或更新）
* 包含腳註與/或尾註的 Word 文件（例如 `Footnotes.docx`）

您可以使用以下 CLI 指令加入 Aspose.Words 套件：

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## 步驟 1：設定專案並匯入命名空間

建立一個新的 Console 專案或將程式碼加入既有專案。以下列出所需的 `using` 指令。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

這些命名空間讓您能存取 `Document` 類別、`Node` 階層結構，以及執行**檢索腳註分隔符**操作所需的 `NodeType` 列舉。

## 步驟 2：載入包含腳註與尾註的文件

在任何 Aspose.Words 工作流程中，第一步都是載入來源檔案。將佔位路徑替換為實際的 `.docx` 位置。

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

載入檔案會建立內部的節點樹，這對於**檢索腳註分隔符**至關重要，因為分隔符節點位於該樹內。

## 步驟 3：檢索腳註分隔符節點

現在您可以透過存取 `Document` 物件的 `FootnoteSeparator` 屬性**檢索腳註分隔符**。此節點代表將腳註與正文分開的那條線。

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

對於標準的分隔線，`NodeType` 會是 `Paragraph`。了解節點類型有助於您決定是要修改分隔符還是完全取代它。

## 步驟 4：檢索尾註分隔符節點

同理，您可以使用 `EndnoteSeparator` 屬性**檢索尾註分隔符**。此節點負責將尾註與主要內容分開。

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

在大多數文件中，兩個分隔符節點皆使用相同的 `NodeType`（`Paragraph`），但它們可以獨立自訂。

## 步驟 5：檢查或修改分隔符內容（可選）

如果您需要變更分隔符的視覺外觀，例如將一串破折號換成細線，可直接編輯 `Paragraph` 節點。以下範例示範如何將預設分隔符文字替換為自訂字串。

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

編輯完節點後，儲存文件即可在 Word 中看到變更。

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## 預期的主控台輸出

執行程式並使用原始的 `Footnotes.docx` 時，您應該會看到類似以下的輸出：

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

若在 Microsoft Word 中開啟 `Footnotes_Updated.docx`，腳註與尾註的分隔符將顯示您插入的自訂文字。

## 常見問題與邊緣情況

**如果文件沒有腳註該怎麼辦？**  
`FootnoteSeparator` 屬性仍會回傳一個 `Paragraph` 節點，因為 Word 總會保留分隔符的佔位。此節點會是空的，您可以安全地加入內容或保持不變。

**我可以為特定章節檢索分隔符嗎？**  
腳註與尾註的分隔符是全文件層級的，並非章節專屬。若需章節層級的控制，必須改用 `Section.FootnoteOptions` 與 `Section.EndnoteOptions`，而非全域分隔符節點。

**這在 .NET Core 上可用嗎？**  
可以。Aspose.Words for .NET 為跨平台套件，同一段程式碼可在 Windows、Linux 與 macOS 上執行，前提是使用 .NET 6 以上版本。

**我應該預期什麼節點類型？**  
`FootnoteSeparator` 與 `EndnoteSeparator` 都會回傳 `Paragraph` 節點（`NodeType.Paragraph`）。若遇到其他類型，可能是文件損毀，建議重新載入或驗證來源檔案。

## 完整原始碼，方便複製貼上

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

將程式碼複製到 `Program.cs` 檔案，調整檔案路徑後執行 `dotnet run`。此程式示範了完整的**檢索腳註分隔符**工作流程，從載入文件到持久化變更。

## 結論

您現在已掌握如何使用 Aspose.Words for .NET **檢索腳註分隔符**與**檢索尾註分隔符**、檢查它們的 `document node type`，以及可選擇性地取代其內容。此技巧可協助您自動化腳註格式、產生自訂分隔線，或在任何 C# 應用程式中驗證文件結構。

接下來，您可以探索如 **C# 腳註抽取**（取得單一腳註文字）或學習如何使用 `FootnoteOptions` **修改腳註參考標記**等相關主題。這兩個概念皆直接建立在本篇所討論的節點樹基礎上。

祝編程愉快，歡迎嘗試不同的分隔符樣式，以符合您專案的品牌形象！

## 接下來該學什麼？

以下教學涵蓋與本指南技術緊密相關的主題，並提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [使用腳註與尾註的文字處理](/words/english/net/working-with-footnote-and-endnote/)
- [在 Aspose.Words for .NET 中使用 Document Builder 新增內容](/words/english/net/add-content-using-document-builder/)
- [使用腳註與尾註](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}