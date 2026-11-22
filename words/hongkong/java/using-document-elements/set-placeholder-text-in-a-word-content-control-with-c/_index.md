---
category: general
date: 2026-11-22
description: 使用 C# 在 Word 內容控制項中設定佔位文字。了解如何建立自訂標籤、插入純文字控制項，並使用 Aspose.Words 為標籤加入佔位文字。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: zh-hant
lastmod: 2026-11-22
og_description: 使用 C# 在 Word 內容控制項中設定佔位文字。本教學將示範如何建立自訂標籤、插入純文字控制項，並為標籤加入佔位文字，以提升文件互動性。
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: 在 Word 內容控制項中設定佔位文字 – C# 指南
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: 使用 C# 為 Word 內容控制項設定佔位文字
url: /zh-hant/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 在 Word 內容控制項中設定佔位文字

如果您需要以程式方式在 Word 文件中 **設定佔位文字**，本指南會精確說明如何操作。使用 Aspose.Words for .NET，您可以建立自訂標籤、插入純文字控制項，並將佔位文字加入標籤，讓文件已準備好供使用者輸入。

在本教學中，您將學習如何 **建立自訂標籤**、**插入內容控制項**，以及 **將佔位文字加入標籤**，同時保持程式碼簡潔且可投入生產使用。無需任何外部工具——只需要一個 .NET 專案與 Aspose.Words 函式庫。

## 前置條件

在開始之前，請確保您已具備：

* 已安裝 .NET 6.0 SDK 或更新版本  
* 有效的 Aspose.Words for .NET 授權（或免費評估金鑰）  
* 基本熟悉 C# 與 Visual Studio（或您偏好的任何 IDE）  

以下章節假設您已建立一個名為 `WordPlaceholderDemo` 的主控台專案。

## 步驟 1：安裝 Aspose.Words

將 NuGet 套件加入您的專案：

```bash
dotnet add package Aspose.Words
```

> **專業提示：** 使用 `--version` 參數將套件鎖定在最新的穩定版（例如 `Aspose.Words.NET 24.9`）。

## 步驟 2：載入來源文件並建立 `DocumentBuilder`

首先，您需要載入現有的 `.docx` 檔案（或建立一個全新的空白文件），並實例化 `DocumentBuilder`。此建構器提供流暢的 API 以插入控制項與文字。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

此程式碼 **為插入內容控制項做好準備**。`DocumentBuilder` 直接作用於 `doc` 物件，因此您所做的任何變更都會自動反映。

## 步驟 3：建立自訂標籤（StructuredDocumentTag）

Word 中的 *自訂標籤* 稱為 **StructuredDocumentTag (SDT)**。它可視為帶有唯一識別碼的內容控制項。建立此標籤即是 **建立自訂標籤** 步驟的核心。

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

`InsertStructuredDocumentTag` 方法接受兩個參數：

1. 控制項類型（此例為 `PlainText`）。  
2. 唯一識別此標籤的字串（`"MyTag"`）。

透過使用 **自訂標籤**，您之後可以以程式方式定位或操作該控制項。

## 步驟 4：設定可存取性標題

標題可提升可存取性，並讓使用者在 Word 介面中更容易找到該控制項。

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

`Title` 屬性為可選，但在 **將佔位文字加入標籤** 時加入它是提升使用者體驗的最佳實踐。

## 步驟 5：將佔位文字加入標籤

現在進入主要目標：**設定佔位文字**。當控制項為空時，會顯示此文字，引導使用者輸入內容。

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

`PlaceholderText` 屬性正是您在 **將佔位文字加入標籤** 時所需要的。它的行為類似於現代表單欄位中的灰色提示文字。

## 步驟 6：儲存已修改的文件

設定完控制項後，將文件寫回磁碟。

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

當您在 Microsoft Word 中開啟 `output.docx` 時，會看到一個標示為「CustomerName」的純文字內容控制項，佔位文字為「Enter name…」。點擊控制項內部即會移除佔位文字，讓使用者可以輸入。

### 預期輸出

* 一個 Word 檔案（`output.docx`），內含單一純文字內容控制項。  
* 該控制項會顯示佔位文字「Enter name…」，直到使用者輸入內容。  
* 控制項的標籤識別碼為 `MyTag`，您可稍後使用 `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` 進行查詢。

## 步驟 7：在其他位置插入內容控制項（進階）

如果您需要在特定位置 **插入內容控制項**——例如在某段落之後——請在插入標籤前使用 `MoveTo` 方法：

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

此程式碼片段示範了在同一文件中多次 **插入純文字控制項**。

## 常見陷阱與避免方法

| 問題 | 發生原因 | 解決方式 |
|------|----------|----------|
| 佔位文字未顯示 | 控制項已包含文字（即使是空格） | 在設定 `PlaceholderText` 前，確保 `sdt.Text` 為空。 |
| 標籤識別碼衝突 | 在同一文件中重複使用相同的標籤名稱（`MyTag`） | 為每個 `StructuredDocumentTag` 使用唯一的識別碼。 |
| 授權例外 | 未使用有效的 Aspose.Words 授權執行 | 在 `Main` 開頭套用授權檔案（`license.SetLicense("Aspose.Words.lic")`）。 |
| 文件未儲存 | 忘記呼叫 `doc.Save` 或使用唯讀路徑 | 確認輸出路徑可寫入，並呼叫 `doc.Save`。 |

## 完整範例程式

以下是完整的程式碼，您可以直接複製貼上至 `Program.cs`。它包含所有步驟——**建立自訂標籤**、**插入內容控制項**、**將佔位文字加入標籤**，以及 **插入純文字控制項**——形成一個連貫的流程。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

使用 `dotnet run` 執行程式。執行完畢後，開啟 `output.docx` 以驗證兩個控制項均顯示各自的佔位文字。

## 往後步驟

* **自訂外觀** – 使用 `sdt.Font` 變更控制項內的字型大小、顏色或樣式。  
* **綁定至 XML 資料** – 若需要控制項映射，請探索 `sdt.XmlMapping`。

## 接下來該學什麼？

以下教學涵蓋與本指南技術密切相關的主題。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [以程式方式建立 Word 文件 – 新增內容控制項與佔位文字](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [在 Aspose.Words 中設定佔位文字 – 完整 C# 指南](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [建立新 Word 文件並在 C# 中插入內容控制項](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}