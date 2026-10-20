---
category: general
date: 2026-08-04
description: 使用 C# 程式自動建立 Word 文件。學習如何在 Word 中加入內容控制項，並設定佔位文字以製作動態範本。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add content control to word
- set placeholder text word
- Aspose.Words content control
- dynamic Word template C#
language: zh-hant
lastmod: 2026-08-04
og_description: 使用 C# 程式化建立 Word 文件。本指南說明如何在 Word 中加入內容控制項，並設定佔位文字，以製作可重複使用的範本。
og_image_alt: Screenshot of a Word document with a highlighted content control placeholder
og_title: 以程式方式建立 Word 文件 – 加入內容控制項與佔位符
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to add content
    control to word and set placeholder text word for dynamic templates.
  headline: Create word document programmatically – add content control and placeholder
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word automation
title: 以程式方式建立 Word 文件 – 新增內容控制項與佔位符
url: /zh-hant/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 以程式方式建立 Word 文件 – 新增內容控制項與佔位文字

如果您需要 **create word document programmatically**，本教學會提供一個完整、可直接執行的解決方案。您將會看到如何 **add content control to word**、為它設定有意義的標題，並 **set placeholder text word**，讓最終使用者之後可以填入資料。

本指南會逐行說明程式碼，解釋每一步的重要性，並指出常見的陷阱。完成後，您將擁有一個可重複使用的 .docx 檔案，可作為發票、合約或任何表單文件的範本。

## Prerequisites

開始之前，請先確定您已具備以下環境：

* 已安裝 .NET 6.0（或更新版本）── 程式碼使用最新的 C# 語言功能。  
* 取得 Aspose.Words for .NET 授權（開發階段可使用免費試用版）。  
* Visual Studio 2022 或任何能編譯 .NET 專案的 IDE。  
* 具備 C# 基礎知識，並了解 Structured Document Tags（SDTs）的概念。

> **Pro tip:** 若在未套用授權的情況下執行範例，Aspose.Words 會在儲存的檔案上加上一個小浮水印。請在程式一開始就載入授權，以避免浮水印出現。

## Step 1: Set up the project and import namespaces

建立一個新的 Console 專案，並加入 Aspose.Words NuGet 套件。

```bash
dotnet new console -n WordTemplateDemo
cd WordTemplateDemo
dotnet add package Aspose.Words
```

接著在 `Program.cs` 中匯入必要的命名空間：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

這些命名空間讓您可以使用 `Document`、`DocumentBuilder` 與 `StructuredDocumentTag` 等類別，這些都是 **create word document programmatically** 所必需的。

## Step 2: Initialize a blank document and a builder

`Document` 類別代表整個 .docx 檔案，而 `DocumentBuilder` 則讓您在指定的游標位置插入內容。

```csharp
// Step 2: Create an empty Word document
Document document = new Document();

// Step 2b: Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters*: 從空的 `Document` 開始，可確保您對每個插入的元素都擁有完整的控制權。`DocumentBuilder` 內部維持一個游標，讓您能精確地在需要的位置插入節點。

## Step 3: Create a plain‑text Structured Document Tag (SDT)

Structured Document Tag 是 Word 中 **content control** 的技術名稱。我們將建立一個內嵌的純文字標籤，讓它的行為類似佔位欄位。

```csharp
// Step 3: Create a plain‑text Structured Document Tag (content control)
StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
    document,
    StructuredDocumentTagType.PlainText,   // plain‑text content control
    MarkupLevel.Inline);                    // appears inside a paragraph
```

*Why this matters*: 使用 `StructuredDocumentTagType.PlainText` 會告訴 Word 此控制項只能接受純文字。`MarkupLevel.Inline` 使控制項在段落內表現得像一般文字，這對表單欄位而言最為理想。

## Step 4: Assign a title and placeholder text

**title** 是應用程式日後可以查詢的內部識別碼。**placeholder** 則是在使用者尚未輸入任何內容前，顯示的灰色提示文字。

```csharp
// Step 4: Set a title and placeholder text for the content control
plainTextTag.Title = "CustomerName";          // internal name used by code
plainTextTag.PlaceholderName = "Enter name here"; // visible hint in the UI
```

此處我們 **set placeholder text word** 為「Enter name here」。當文件在 Microsoft Word 中開啟時，佔位文字會以淡灰色顯示，直到使用者輸入值為止。

## Step 5: Insert the content control at the current cursor position

`DocumentBuilder.InsertNode` 會把 SDT 插入到 builder 游標所在的確切位置。預設情況下，游標位於第一段落的開頭。

```csharp
// Step 5: Insert the content control into the document at the builder's current position
builder.InsertNode(plainTextTag);
```

若需將控制項插入特定段落，請先移動游標：

```csharp
builder.Writeln("Please provide the customer name:");
builder.InsertNode(plainTextTag);
```

此範例示範了如何 **add content control to word**，同時保留周圍文字的完整性。

## Step 6: Save the document

最後，將檔案寫入磁碟。您可以自行決定儲存資料夾，只要確保程式有寫入權限即可。

```csharp
// Step 6: Save the document with the content control
string outputPath = @"YOUR_DIRECTORY\SDT.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

當您在 Microsoft Word 中開啟 `SDT.docx`，會看到「Enter name here」的佔位文字以淡灰色方框呈現。使用者只要點擊方框，即可將提示文字取代為實際的客戶名稱。

## Full, runnable example

以下是完整的程式碼範例，您可以直接複製、貼上並執行（唯一需要調整的是輸出路徑）。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Optional: apply your Aspose.Words license here
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new empty document
        Document document = new Document();

        // 2. Initialize a DocumentBuilder for editing the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3. Write a brief instruction line (optional)
        builder.Writeln("Please enter the customer's name below:");

        // 4. Create a plain‑text Structured Document Tag (content control)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
            document,
            StructuredDocumentTagType.PlainText,
            MarkupLevel.Inline);

        // 5. Set a title and placeholder text for the content control
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // 6. Insert the content control at the current cursor position
        builder.InsertNode(plainTextTag);

        // 7. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected output** – 執行程式後，主控台會印出檔案路徑，產生的 Word 檔案則會包含一行文字，後方緊跟著顯示「Enter name here」的灰色佔位框。

## Common variations and edge cases

| Scenario | How to adapt the code |
|----------|-----------------------|
| **Multi‑line placeholder** | 使用 `StructuredDocumentTagType.RichText` 取代 `PlainText`，並設定 `plainTextTag.MultipleLines = true;`。 |
| **Repeating the same control** | 以 `plainTextTag.Clone(true)` 複製標籤，然後在需要的地方插入複製品。 |
| **Binding to data source** | 使用者填寫完文件後，可透過 `document.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().First(t => t.Title == "CustomerName").GetText();` 取得值。 |
| **Locking the control** | 設定 `plainTextTag.LockContentControl = true;` 以防止使用者刪除控制項。 |
| **Changing placeholder color** | SDK 未提供佔位文字樣式的設定，需手動編輯範本或使用 Word 巨集完成。 |

透過上述變化，您可以在更複雜的情境（例如可重複的表格或受保護的區段）中 **add content control to word**。

## Best practices and troubleshooting

* **Always set a title** – 若未設定 title，日後定位控制項會相當困難。  
* **Avoid empty placeholders** – 若 `ShowPlaceholderText` 屬性為 false，Word 會隱藏空的佔位文字。請保持為 true，以提升使用者體驗。  
* **Validate the output path** – 若 `document.Save` 拋出 `UnauthorizedAccessException`，請確認資料夾已存在且程式有寫入權限。  
* **License early** – 在建立任何 Aspose.Words 物件之前先載入授權碼，可避免出現試用浮水印。

## Conclusion

現在您已掌握 **create word document programmatically**、**add content control to word** 與 **set placeholder text word** 的完整流程，並以 Aspose.Words for .NET 完成範例。此範例示範了從初始化文件到儲存可供最終使用者填寫的範本的每一步。

接下來，您可以探索：

* 為表格新增 **repeating content controls**（次要關鍵字：add content control to word）。  
* 從資料庫填入佔位文字（次要關鍵字：set placeholder text word）。  
* 將產生的 .docx 轉換為 PDF 或 HTML，以供後續處理。

歡迎嘗試不同的標籤類型、樣式與資料繫結技巧。祝開發順利！

## What Should You Learn Next?

以下教學與本篇內容密切相關，能進一步深化您的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能或探索其他實作方式。

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}