---
category: general
date: 2026-09-18
description: 使用 C# 建立空白 Word 文件並設定佔位文字，然後儲存為 docx。學習插入純文字內容控制項並加入佔位名稱。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: zh-hant
lastmod: 2026-09-18
og_description: 使用 C# 建立空白 Word 文件。設定佔位文字、插入純文字內容控制項、加入佔位名稱，並將文件儲存為 docx。
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: 建立空白 Word 文件並加入佔位文字 – C# 指南
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 建立空白 Word 文件並插入純文字控制項
url: /zh-hant/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立空白 Word 文件並插入純文字內容控制項

如果您需要以程式方式 **create blank Word document**，本指南將示範如何使用 C# 完成。您將學會 **insert plain text control**、**set placeholder text**、**add placeholder name**，最後 **save document as docx**。這些步驟都是完整獨立的，您可以直接將程式碼複製到任何 .NET 專案並立即執行。

處理 Word 檔案時通常需要一個乾淨的起點——一個已包含使用者將填寫之控制項的空白文件。完成本教學後，您將得到一個 `.docx` 檔案，內含帶有說明性佔位文字的純文字內容控制項，並在其後有一般內容。

## 前置條件

- .NET 6.0 或更新版本（此程式碼亦可於 .NET Framework 4.6+ 使用）
- 對 **Aspose.Words for .NET** 函式庫的參考（可透過 NuGet `Install-Package Aspose.Words` 取得）
- 具備 C# 主控台應用程式的基本知識
- 對您在 `doc.save(...)` 中指定的輸出資料夾擁有寫入權限

## 您將建立的內容

最終的文件 (`SDT.docx`) 包含：

1. 一個空的 Word 檔案（您建立的 **blank Word document**）
2. 一個純文字內容控制項（**insert plain text control** 步驟）
3. 在控制項內顯示的佔位文字，直到使用者輸入內容（**set placeholder text** 步驟）
4. 一個可於之後程式化存取的佔位名稱（**add placeholder name** 步驟）
5. 控制項之後的一行普通文字，示範正常內容可以跟隨

## 步驟 1：建立空白 Word 文件

第一個操作是實例化一個空的 `Document` 物件。此物件在記憶體中代表一個全新的、**blank Word document**。

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*Why this matters:* 空的 `Document` 讓您能完全掌控所加入的每個元素，確保沒有隱藏的樣式或區段會干擾您稍後插入的內容控制項。

## 步驟 2：初始化 DocumentBuilder

`DocumentBuilder` 是協助您寫入 `Document` 的類別。它會追蹤目前的游標位置，並提供插入各種 Word 物件的方法。

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters:* 使用 `DocumentBuilder` 可簡化加入 **plain‑text control** 的流程，因為建構器知道確切的插入位置。

## 步驟 3：插入純文字控制項

現在我們加入一個 **plain‑text content control**（亦稱為 Structured Document Tag，簡稱 SDT）。控制項類型 `StructuredDocumentTagType.PLAIN_TEXT` 告訴 Word 將內容視為純文字，而非富格式。

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*Why this matters:* `InsertStructuredDocumentTag` 方法會建立控制項並回傳一個參考（`sdt`），您可以進一步設定，例如加入佔位文字或自訂名稱。

## 步驟 4：設定佔位文字並加入佔位名稱

佔位文字為使用者提供關於應輸入內容的視覺提示。**add placeholder name** 步驟會指派一個程式化的識別碼，您之後可使用 `doc.GetChildNodes` 或類似 API 進行查詢。

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*Why this matters:* `SetPlaceholderName` 控制顯示在內容控制項內的灰色提示文字。設定 `Tag`（即 **add placeholder name** 動作）可讓您在文件樹中定位控制項，而不必掃描整個檔案。

## 步驟 5：在控制項後加入一般內容

為證明文件在控制項之後仍能正常繼續，我們寫入一行簡單的文字。

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## 步驟 6：將文件儲存為 docx

最後，我們將記憶體中的文件寫入磁碟。這就是 **save document as docx** 的操作，會產生可在 Microsoft Word 開啟的檔案。

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*Why this matters:* 使用 `.docx` 格式可確保與現代版 Word、Google Docs 以及其他相容 Office 工具的最高相容性。

## 完整、可執行的範例

以下是完整程式碼，您可以將其複製到 console‑app 專案中。將 `YOUR_DIRECTORY` 替換為您機器上的實際資料夾路徑。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### 預期結果

- 在 Word 中開啟 `SDT.docx` 時，會看到一個空的灰色方框，內含文字 **Enter text…**。
- 該方框是一個純文字內容控制項；您可以直接在其中輸入。
- 方框下方，會出現文字 **After the tag.**，作為普通段落文字。

若佔位文字未顯示，請確認您使用的是較新版的 Aspose.Words（v23.1 或更新）且文件是以支援內容控制項的 Word 版本（Word 2007 以上）開啟。

## 常見變化與邊緣情況

| 情境 | 如何調整程式碼 |
|----------|-----------------------|
| **Multiple placeholders** | 再次呼叫 `InsertStructuredDocumentTag`，並使用不同的 tag ID 與佔位名稱。 |
| **Rich‑text control** | 改用 `StructuredDocumentTagType.RichText` 取代 `PlainText`。 |
| **Setting default text** | 插入後，指派 `sdt.Text = "Default value";` ——此文字會在文件載入時取代佔位文字。 |
| **Saving to a stream** | 將 `doc.Save(outputPath);` 改為 `doc.Save(stream, SaveFormat.Docx);` 以透過 HTTP 傳送檔案。 |
| **Changing placeholder color** | 使用 `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;`（需要 `using System.Drawing`）。 |

## 專業技巧

- **Reuse the tag ID**: 保持標籤 (`MyTag`) 在各文件中一致，可讓您稍後使用 `doc.Range.Replace` 或 `StructuredDocumentTagCollection` 自動填入資料。
- **Avoid hard‑coded paths**: 使用 `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` 以取得可攜式的輸出位置。
- **Performance**: 若需產生數千份文件，請先建立一個已包含 SDT 的 `Document` 範本，然後在每次迭代時使用 `doc.Clone()` 複製。

## 結論

現在您已了解如何使用 Aspose.Words for .NET **create blank Word document**、**insert plain text control**、**set placeholder text**、**add placeholder name**，以及 **save document as docx**。此模式是建立填寫表單的 Word 範本、自動化報告，或任何需要使用者可編輯佔位符的解決方案的基礎。

歡迎嘗試其他控制項類型、結合多個佔位符，或將此程式碼整合至回傳產生的 `.docx` 檔案給呼叫端的 Web API 中。下一步可探索 **populate a content control with data programmatically** 或使用 Aspose.Words 內建的轉換功能 **convert the generated Word file to PDF**。祝開發愉快！

## 接下來您可以學習什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此技術為基礎。每個資源皆包含完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}