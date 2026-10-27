---
category: general
date: 2026-10-13
description: 在 C# 中建立新的 Word 文件並插入帶有佔位文字的內容控制項。學習如何設定佔位文字以及有效率地儲存 Word 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert content control
- set placeholder text
- how to create sdt
- save word document c#
language: zh-hant
lastmod: 2026-10-13
og_description: 使用 C# 及 Aspose.Words 建立新 Word 文件，插入內容控制項、設定佔位文字，並儲存 Word 文件——一次完整教學。
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: 在 C# 中建立新的 Word 文件並插入內容控制項
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  headline: Create new Word document and insert content control in C#
  type: TechArticle
- description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  name: Create new Word document and insert content control in C#
  steps:
  - name: Run the console app.
    text: Run the console app.
  - name: Open `output.docx` in Microsoft Word.
    text: Open `output.docx` in Microsoft Word.
  - name: Verify that the placeholder text appears inside a gray‑shaded box.
    text: Verify that the placeholder text appears inside a gray‑shaded box.
  - name: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
    text: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: 在 C# 中建立新的 Word 文件並插入內容控制項
url: /zh-hant/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中建立新 Word 文件並插入內容控制項

如果您需要以程式方式 **建立新 Word 文件**，本指南將示範如何使用 Aspose.Words for .NET 完成。您將學會 **插入內容控制項**、設定 **佔位文字**，以及最終 **儲存 Word 文件 C#** 的程式碼，您可以將其複製到您的專案中。

本教學逐步說明每個步驟，解釋每個 API 呼叫的重要性，並涵蓋常見的變化，例如加入 rich‑text SDT 或處理現有文件。完成後，您將擁有一個完整、可執行的範例，可用於發票、合約或任何模板化的 Word 輸出。

## 前置條件

* .NET 6.0 或更新版本（程式碼亦可在 .NET Framework 4.7+ 上執行）
* Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）
* 如 Visual Studio 2022 或 Visual Studio Code 等 IDE

不需要其他額外的函式庫。

## 使用 Aspose.Words 建立新 Word 文件

第一步是實例化 `Document` 物件。此物件代表記憶體中的空白 Word 檔案。

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new, empty document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` 為您提供流暢的 API，以在目前游標位置插入元素。由於文件是空的，游標會位於第一（也是唯一）節的開頭。

## 插入內容控制項（StructuredDocumentTag）

Word 中的 **內容控制項** 稱為 Structured Document Tag（SDT）。以下程式碼會建立純文字 SDT、設定其標題，並定義使用者開啟檔案時顯示的佔位文字。

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Title is used for identification in the document outline
    Title = "CustomerName",
    // Placeholder text is visible until the user types a value
    PlaceholderName = "Enter name here"
};

// Step 3: Insert the SDT at the builder's current insertion point
builder.InsertNode(sdt);
```

**為何重要：**  
* `SdtType.PlainText` 限制內容只能為單行純文字，適合姓名或電子郵件等簡單欄位。  
* 設定 `PlaceholderName` 可提供視覺提示（`Enter name here`），引導最終使用者。

如果您需要更豐富的欄位（例如多行文字或日期選擇器），請將 `SdtType.PlainText` 替換為 `SdtType.RichText` 或 `SdtType.Date`。

## 新增可選的前後文字

大多數模板會在內容控制項前加入標籤。您可以使用相同的 `DocumentBuilder` 實例來新增它：

```csharp
// Optional: add a label before the content control
builder.Writeln("Customer Name:");
builder.InsertNode(sdt);   // Re‑insert the SDT after the label
```

產生的 Word 檔案會顯示：

```
Customer Name: [Enter name here]
```

## 以 C# 方式儲存 Word 文件

最後，將文件寫入磁碟。Aspose.Words 會自動根據檔案副檔名判斷格式。

```csharp
// Step 4: Save the document to verify the result
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

當您在 Microsoft Word 中開啟 `output.docx` 時，會看到佔位文字位於灰色陰影的內容控制項內。使用者可以點擊該控制項，將佔位文字替換為自己的值。

## 完整、可執行的範例

以下是一個獨立的主控台程式，將所有步驟整合在一起。將程式碼複製到新的主控台專案中並執行。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Add a descriptive label
            builder.Writeln("Customer Name:");

            // Create and configure a plain‑text content control (SDT)
            StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
            {
                Title = "CustomerName",
                PlaceholderName = "Enter name here"
            };

            // Insert the SDT after the label
            builder.InsertNode(sdt);

            // Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**預期輸出**（主控台）：

```
Document saved to C:\YourProject\bin\Debug\net6.0\output.docx
```

開啟 `output.docx` 後會看到一行文字，標籤為 *Customer Name:*，其後接著一個顯示 *Enter name here* 的內容控制項。

## 常見變化與邊緣情況

| Scenario | Code change | Reason |
|----------|-------------|--------|
| **Rich‑text 欄位** | `new StructuredDocumentTag(doc, SdtType.RichText, true)` | 允許多行輸入及基本格式設定。 |
| **唯讀控制項** | `sdt.LockContentControl = true;` | 防止使用者編輯控制項內容。 |
| **預先填入資料** | `sdt.AppendChild(new Run(doc, "John Doe"));` | 插入預設值，覆寫佔位文字。 |
| **加入至現有文件** | Load with `new Document("template.docx")` instead of an empty `Document` | 支援在預先設計的版面中放置控制項的模板化情境。 |
| **多個控制項** | Repeat the creation block with different titles and placeholders | 適用於收集多項資訊的表單。 |

### 專業提示

產生大型文件時，請重複使用同一個 `DocumentBuilder` 實例，而非為每個控制項建立新實例。這可減少記憶體開銷並提升效能。

## 測試結果

1. 執行主控台應用程式。  
2. 在 Microsoft Word 中開啟 `output.docx`。  
3. 確認佔位文字出現在灰色陰影的方框內。  
4. 點擊該方框，輸入姓名，然後儲存檔案。輸入的文字會取代佔位文字。

如果佔位文字未出現，請確認您使用的是 Aspose.Words 版本 23.9 或更新版本，因為較舊的版本在純文字 SDT 上的 `PlaceholderName` 會有錯誤。

## 結論

現在您已了解如何使用 Aspose.Words **建立新 Word 文件**、**插入內容控制項**、**設定佔位文字**，以及 **以 C# 儲存 Word 文件**。完整範例展示了標準模式，而變化表則說明如何將解決方案套用於更豐富的情境。

接下來，您可能想探索：

* **插入日期內容控制項** – 使用 `SdtType.Date` 列舉。  
* **以資料填充模板** – 結合 `StructuredDocumentTag` 與合併列印欄位。  
* **匯出為 PDF** – 在加入控制項後呼叫 `doc.Save("output.pdf")`。

歡迎嘗試不同的 SDT 類型、鎖定設定與樣式，以符合您的專案需求。祝開發順利！

## 接下來您應該學習什麼？

以下教學涵蓋與本指南緊密相關的主題，建立在所示技術之上。每個資源皆提供完整可運作的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [建立新 Word 文件](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [在 Word 文件中插入文字輸入表單欄位](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [使用 Aspose.Words for .NET 建立 Word 文件](/words/english/net/add-content-using-documentbuilder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}