---
category: general
date: 2026-11-25
description: 學習如何建立 Word 文件、加入矩形形狀、使用 AI 摘要文件、使用 AI 翻譯文字，並使用 Aspose.Words 將文件儲存為 DOCX。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: zh-hant
lastmod: 2026-11-25
og_description: 建立 Word 文件、加入矩形形狀、使用 AI 摘要文件、使用 AI 翻譯文字，並將文件儲存為 DOCX——全部於單一 C# 教學中完成。
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: 使用 C# 建立包含圖形、AI 摘要與翻譯的 Word 文件
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: 如何在 C# 中建立包含形狀、AI 摘要與翻譯的 Word 文件
url: /zh-hant/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中建立帶有圖形、AI 摘要與翻譯的 Word 文件

如果你需要 **程式化建立 Word 文件**，本教學將一步一步示範。使用 Aspose.Words for .NET，你將學會 **加入矩形圖形**、呼叫 AI 服務 **以 AI 摘要文件**、使用 **AI 翻譯文字**，最後 **將文件儲存為 DOCX**。

許多開發者在將文件自動化與現代 AI 功能結合時會遇到困難。完成本教學後，你將擁有一個完整、獨立的 C# 專案，能產生格式完整的 *.docx* 檔案，內含視覺圖形、AI 產生的摘要與多語言內容。

## 前置條件

在開始之前，請確保你已具備：

- .NET 6.0 SDK 或更新版本  
- Visual Studio 2022（或任何 C# IDE）  
- Aspose.Words for .NET 授權（或免費評估金鑰）  
- 用於 AI 摘要與翻譯呼叫的網路連線  

除 `Aspose.Words` 與 `Aspose.Words.AI` 之外，無需其他 NuGet 套件。

## 步驟 1：建立專案並加入必要的套件

建立一個新的 Console 專案，並引用 Aspose.Words 函式庫。

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **專業提示：** 若使用評估模式，請在 `Main` 方法開頭呼叫 `Aspose.Words.License.SetLicense("Aspose.Words.lic");` 以避免浮水印。

## 步驟 2：初始化文件 – **create word document** 的核心

第一行可執行的程式碼會建立一個全新的 **Word 文件** 物件。此物件是之後所有操作的畫布。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` 簡化了插入文字、圖形與控制項的流程，無需手動處理低階節點樹。

## 步驟 3：**Add rectangle shape** 至文件

矩形圖形可作為視覺佔位、標籤背景或簡易圖形。我們先建立 `GroupShape`，再在其中插入 `Rectangle`。

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

此矩形寬 100 點、高 50 點。因為它位於 `GroupShape` 內，之後可再加入其他元素（例如文字方塊），而不必擔心版面衝突。

## 步驟 4：插入純文字 StructuredDocumentTag (SDT)

StructuredDocumentTag 物件適用於日後可綁定資料來源的內容控制項。

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

`true` 參數將標記此標籤為 **重複** 控制項，對模板非常實用。

## 步驟 5：加入 ActiveX CommandButton 控制項（可選 UI）

若產生的文件會在支援 ActiveX 的環境中使用，你可以嵌入一個按鈕。

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

此步驟為可選項目；若你的目標讀者不會在 Windows 環境下與文件互動，可直接移除。

## 步驟 6：**Summarize document with AI**

Aspose.Words.AI 為大型語言模型服務提供便利的封裝。我們在此呼叫 `DocumentSummarizer.Summarize`，使用 OpenAI 後端。

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

此方法會分析目前的節點樹，擷取最相關的句子，並回傳簡潔的段落。這就是 **summarize document with AI** 功能的核心。

## 步驟 7：**Translate text using AI**

接著示範如何將範例字串從英文翻譯成法文。`Translator.Translate` 內部會呼叫 Google AI 模型。

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

你可以將 `Language.French` 替換為任何支援的語言列舉值，即時產生多語言文件。

## 步驟 8：**Save document as DOCX**

最後，將編輯好的文件寫入磁碟。指定 `.docx` 副檔名時，`Save` 方法會自動產生 *.docx* 檔案。

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

`Result.docx` 現在包含：

- 位於群組圖形內的矩形圖形  
- 純文字內容控制項 (SDT)  
- ActiveX CommandButton（若保留了步驟 5）  
- AI 產生的摘要段落  
- 「Hello world」的法文翻譯  

你可以在 Microsoft Word 中開啟此檔案，驗證每個元素是否正確。

## 完整原始碼

以下是完整、可直接執行的程式。將內容複製到 `Program.cs`，然後執行 `dotnet run`。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### 預期輸出

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

開啟 `Result.docx` 後，你會看到位於文件上方的矩形圖形、SDT 佔位、按鈕、摘要段落，以及以純文字插入的法文翻譯。

## 結論

現在你已掌握如何 **create a Word document**、**add rectangle shape**、**summarize document with AI**、**translate text using AI**，以及 **save document as DOCX**——全部只需幾行簡潔的 C# 程式碼。此模式具備可擴充性：你可以將硬編碼字串換成動態資料、加入更多圖形或圖表，甚至透過調整 `SummarizerOptions` 或 `Translator` 參數切換 AI 供應商。

### 接下來可以做什麼？

- 探索 **add rectangle shape** 的變化：更改填色、線條樣式，或在圖形內加入文字。  
- 在較大的文件上使用 **summarize document with AI**，自動產生執行摘要。  
- 擴充 **translate text using AI**，批次處理整段文字或表格，以產生多語言報告。  
- 結合 Aspose.Words 的圖表 API，將資料視覺化與 AI 產生的洞見一起嵌入文件。  

盡情實驗，並在評論或 GitHub 上分享你的成果。祝開發愉快！

## 接下來該學什麼？

以下教學與本指南的技巧密切相關，能協助你進一步掌握 API 功能並探索其他實作方式。

- [Create a blank word document and add a rectangle shape](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Text Watermark in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}