---
category: general
date: 2026-10-10
description: 使用 Aspose.Words 程式化建立 Word 文件並插入純文字內容控制項 – .NET 開發者的逐步指南
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- insert plain text content control
language: zh-hant
lastmod: 2026-10-10
og_description: 以程式方式使用 Aspose.Words 建立 Word 文件，並加入顯示佔位文字的純文字內容控制項，讓 .docx 檔案具備動態表單欄位功能。
og_image_alt: Screenshot of a Word document displaying a plain text content control
  placeholder
og_title: 以程式方式建立 Word 文件並加入純文字內容控制項
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create word document programmatically with Aspose.Words and insert
    plain text content control – a step‑by‑step guide for .NET developers.
  headline: How to create word document programmatically and insert plain text content
    control
  type: TechArticle
tags:
- word
- document automation
- content control
- Aspose.Words
- C#
title: 如何以程式方式建立 Word 文件並插入純文字內容控制項
url: /zh-hant/java/document-manipulation/how-to-create-word-document-programmatically-and-insert-plai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何以程式方式建立 Word 文件並插入純文字內容控制項

如果您需要 **以程式方式建立 Word 文件**，本教學將示範如何使用 Aspose.Words for .NET 完成。只需幾行程式碼，即可學會 **插入純文字內容控制項**（亦稱結構化文件標記），讓文件具備可填寫的表單功能。

您將會一步步走過完整流程——從初始化 `Document` 物件到儲存最終的 .docx 檔案。無需外部工具，範例支援 .NET 6、.NET 7 或任何近期的 .NET 執行環境。

## 前置條件

開始之前，請確認您已具備：

* 有效的 Aspose.Words for .NET 授權（或使用免費評估模式）。  
* 已安裝 .NET 6+ SDK。  
* 具備 Visual Studio 2022、Rider 或 VS Code 等開發環境。  

如果尚未安裝 Aspose.Words NuGet 套件，請執行：

```bash
dotnet add package Aspose.Words
```

## 步驟 1：以程式方式建立 Word 文件

第一步是建立空白的 `Document` 與 `DocumentBuilder`。Builder 提供便利的 API 來加入內容、頁面以及結構化文件標記（SDT）。

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;
using Aspose.Words.Markup;

// Create an empty document and a builder attached to it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

**為什麼重要** – `Document` 代表整個 .docx 檔案於記憶體中。以程式方式建立可避免開啟範本檔案的開銷，適合產生報表、發票或任何即時文件。

## 步驟 2：插入純文字內容控制項

**純文字內容控制項**（SDT）允許使用者在預先定義的區域內輸入文字，亦支援在控制項為空時顯示的佔位文字。

```csharp
// Insert a plain‑text Structured Document Tag (SDT) with an identifier "MyTag"
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Set placeholder text that shows inside the control when it is empty
plainTextTag.PlaceholderName = "Enter name";
```

**說明** – `InsertStructuredDocumentTag` 會在 `DocumentBuilder` 目前的游標位置建立 SDT。`StructuredDocumentTagType.PlainText` 列舉值告訴 Aspose.Words 產生純文字方塊，而非下拉選單或日期挑選器。`PlaceholderName` 屬性提供使用者的視覺提示，類似現代 Word 表單中的灰色提示文字。

### 常見變化

| 變化類型 | 實作方式 |
|-----------|-------------------|
| **Rich‑text 內容控制項** | 使用 `StructuredDocumentTagType.RichText` 取代 `PlainText`。 |
| **重複區段** | 使用 `StructuredDocumentTagType.Group`，並在其中巢狀其他標記。 |
| **自訂 XML 對應** | 建立 `XmlPart` 後呼叫 `plainTextTag.SetXmlMapping(xmlPart, xpath, false)`。 |

## 步驟 3：加入其他文件內容（可選）

您可以在內容控制項前後加入普通段落、表格或圖片。以下示範加入標題與段落的快速範例：

```csharp
// Add a heading above the content control
builder.Font.Size = 16;
builder.Font.Bold = true;
builder.Writeln("Employee Information");

// Move the cursor back to the placeholder location (already set by InsertStructuredDocumentTag)
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Writeln(); // Adds a line break after the control
```

**小技巧** – Builder 的游標會自動移至已插入 SDT 的結尾，因此後續的 `Writeln` 呼叫會出現在控制項之後。

## 步驟 4：儲存含有內容控制項的文件

最後，將文件寫入磁碟。您可以選擇任何支援的格式（`.docx`、`.pdf`、`.html` 等）。本教學以 Word 檔案為例。

```csharp
// Save the document to the specified path
string outputPath = Path.Combine(Environment.CurrentDirectory, "SdtExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### 預期結果

在 Microsoft Word 開啟 *SdtExample.docx* 時，您會看到：

1. 標題 **Employee Information**。  
2. 帶有灰色佔位文字 **Enter name** 的純文字內容控制項。  

點擊控制項內部時，佔位文字會消失，您即可輸入任意文字。控制項的標籤識別碼 (`MyTag`) 之後可透過程式碼存取，以進行資料擷取或驗證。

## 完整可執行範例

以下是一個自包含的 Console 應用程式，將所有步驟整合在一起。將程式碼複製到新的 .NET Console 專案並執行。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text content control (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // 3️⃣ Set placeholder text that appears when the control is empty
            sdt.PlaceholderName = "Enter name";

            // Optional: add a heading above the control
            builder.MoveToDocumentStart(); // Ensure heading appears before the control
            builder.Font.Size = 16;
            builder.Font.Bold = true;
            builder.Writeln("Employee Information");

            // Move back to the end of the control to continue writing
            builder.MoveToDocumentEnd();
            builder.Font.Size = 12;
            builder.Font.Bold = false;
            builder.Writeln(); // Adds a line break after the control

            // 4️⃣ Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "SdtExample.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

執行程式後會列印產生檔案的完整路徑。於 Word 開啟該檔案，即可驗證 **純文字內容控制項** 與其佔位文字是否正確顯示。

## 疑難排解與邊緣情況

| 問題 | 原因 | 解決方式 |
|-------|-------|-----|
| 佔位文字未顯示 | 控制項已被填入文字，或文件以隱藏佔位文字的模式開啟。 | 確保 SDT 在儲存前為空，或設定 `sdt.IsShowingPlaceholder = true`（較新版本的 Aspose.Words 提供）。 |
| 內容控制項在另存為 PDF 後消失 | PDF 匯出預設不保留互動式表單欄位。 | 使用 `PdfSaveOptions` 搭配 `SaveFormat.Pdf`，並設定 `ExportDocumentStructure = true`。 |
| 後續處理時找不到標籤識別碼 | 標籤名稱拼寫錯誤或被覆寫。 | 確認傳入 `InsertStructuredDocumentTag` 的識別碼與之後查詢時使用的名稱 (`MyTag`) 完全相同。 |

## 建立 Word 文件的最佳實踐

* **每個文件僅使用一個 `DocumentBuilder`**，以避免不必要的記憶體分配。  
* **寫入文字前先設定字型與樣式**；內容加入後再變更可能導致格式不一致。  
* **使用 `using` 陳述式釋放大型物件**（例如將文件寫入 `MemoryStream` 時）。  
* **在儲存前以 `doc.UpdateFields()` 與 `doc.UpdatePageLayout()` 進行文件驗證**，特別是加入表格或圖片時。  

## 結論

現在您已掌握如何使用 Aspose.Words for .NET **以程式方式建立 Word 文件** 並 **插入純文字內容控制項**。完整範例示範了文件初始化、帶佔位文字的 SDT 插入、可選的額外內容，以及儲存為 .docx 檔案的全流程。

接下來您可以：

* 將純文字控制項換成 **rich‑text** 或 **date picker** 控制項。  
* 從資料庫填入文件資料，之後使用 `StructuredDocumentTag.GetText()` 取得使用者輸入的值。  
* 將同一份文件匯出為 PDF、HTML 或 OpenXML 格式，同時保留表單欄位。

多嘗試不同的標籤類型，深入探索 Aspose.Words API，打造可填寫且與 .NET 應用程式無縫整合的高階 Word 範本。祝您開發順利！

## 接下來該學什麼？

以下教學與本指南緊密相關，能進一步擴展您的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能並探索替代實作方式。

- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}