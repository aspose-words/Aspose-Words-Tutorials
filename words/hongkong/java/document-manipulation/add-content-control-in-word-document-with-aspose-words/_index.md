---
category: general
date: 2026-09-11
description: 使用 Aspose.Words 在 Word 文件中新增內容控制項。請依照此逐步指南，以程式方式插入純文字結構化文件標記（SDT）。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control in word document
- StructuredDocumentTag
- DocumentBuilder
- Aspose.Words
- plain‑text SDT
- word automation
language: zh-hant
lastmod: 2026-09-11
og_description: 使用 Aspose.Words 在 Word 文件中新增內容控制項。本指南示範如何以程式方式插入純文字結構化文件標記 (SDT) 並自訂它。
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: 在 Word 文件中新增內容控制項 – 完整 Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Add content control in Word document using Aspose.Words. Follow this
    step‑by‑step guide to insert a plain‑text Structured Document Tag (SDT) programmatically.
  headline: Add content control in Word document with Aspose.Words
  type: TechArticle
tags:
- word
- content‑control
- csharp
- aspose
title: 使用 Aspose.Words 在 Word 文件中新增內容控制項
url: /zh-hant/java/document-manipulation/add-content-control-in-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文件中使用 Aspose.Words 添加內容控制項

如果您需要以程式方式 **在 Word 文件中添加內容控制項**，本教學將會示範如何使用 Aspose.Words for .NET 完成。無論您是建立文件產生服務或是自動化表單建立，都會學會插入純文字的 Structured Document Tag (SDT) 並賦予有意義的標題。

在本指南中，您將看到一個完整且可執行的範例，涵蓋所有必要的匯入、說明每個 API 呼叫的意義，並示範如何驗證結果。無需任何外部參考——只要複製程式碼、執行，然後開啟產生的 *.docx* 檔案。

## 前置條件

* .NET 6.0 SDK 或更新版本已安裝  
* Visual Studio 2022（或任何 C# IDE）  
* Aspose.Words for .NET 23.5 或更新版本 – 您可以取得免費試用的 NuGet 套件  

這些項目構成使用 Aspose.Words 進行 **word automation** 的最小設定。

## 步驟 1：設定專案並匯入命名空間

建立一個新的 console 專案並加入 Aspose.Words 套件：

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

現在開啟 `Program.cs`，並加入所需的 `using` 指令：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;
```

這些命名空間讓您能存取 `DocumentBuilder`、`StructuredDocumentTag` 以及其他用於 **在 Word 文件中添加內容控制項** 的核心類型。

## 步驟 2：建立新文件與 DocumentBuilder

`DocumentBuilder` 是建立 Word 檔案的主要入口。它持有一個游標，用於追蹤下一個元素將插入的位置。

```csharp
// Step 2: Initialize a new blank document and a builder
Document doc = new Document();                 // creates an empty .docx
DocumentBuilder builder = new DocumentBuilder(doc);
```

*為什麼這很重要*：`Document` 物件代表整個 Word 檔案，而 `DocumentBuilder` 簡化了段落、表格以及 **content controls**（例如 Structured Document Tags）的插入。

## 步驟 3：插入純文字 Structured Document Tag (SDT)

我們解決方案的核心是 `insertStructuredDocumentTag` 方法。它會建立一個可以容納純文字、日期、下拉選單等的 **content control**。此處我們使用 `SdtType.PLAIN_TEXT` 列舉值。

```csharp
// Step 3: Insert a plain‑text SDT at the current cursor position
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText,   // the type of control – plain‑text here
    true);               // true = the tag is shown as a placeholder in the UI
```

*為什麼這很重要*：將 `true` 設定為占位符，使控制項顯示為淡灰色，提示最終使用者需填寫此欄位。

## 步驟 4：為 SDT 設定標題以便之後辨識

標題（或標籤）讓您之後能定位此控制項，例如在需要以程式方式取代其內容時。

```csharp
// Step 4: Assign a title so you can find the control later
sdt.Title = "CustomerName";
```

此標題不會顯示在文件 UI 中，但會儲存在底層 XML，並可透過 Aspose.Words API 進行查詢。

## 步驟 5：在 SDT 內加入占位文字

為了讓控制項更友善，插入一個預設的 run，告訴使用者應輸入什麼內容。

```csharp
// Step 5: Add placeholder text inside the SDT
Run placeholder = new Run(builder.Document, "Enter name here");
sdt.AppendChild(placeholder);
```

*為什麼這很重要*：`Run` 物件代表一段文字。將它附加到 SDT 後，即會產生一個可見的提示，使用者開始輸入時即會消失。

## 步驟 6：儲存文件

最後，將文件寫入磁碟，以便在 Microsoft Word 中開啟。

```csharp
// Step 6: Save the finished document
string outPath = "ContentControlExample.docx";
doc.Save(outPath);
Console.WriteLine($"Document saved to {outPath}");
```

當您開啟 `ContentControlExample.docx` 時，會看到一個灰色陰影的內容控制項，標題為 **CustomerName**，占位文字為 *Enter name here*。

## 完整可執行範例

以下是完整程式碼，您可以直接複製貼上至 `Program.cs`。它包含所有步驟、註解以及必要的錯誤處理。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;

namespace ContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document
            Document doc = new Document();

            // Initialize the DocumentBuilder – this controls where we insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text Structured Document Tag (SDT)
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,   // type of content control
                true);               // show as placeholder

            // Assign a title for later lookup (not visible in the UI)
            sdt.Title = "CustomerName";

            // Add placeholder text that instructs the user
            Run placeholder = new Run(builder.Document, "Enter name here");
            sdt.AppendChild(placeholder);

            // Save the document to the file system
            string outPath = "ContentControlExample.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### 預期輸出

執行程式會輸出：

```
Document saved to ContentControlExample.docx
```

在 Word 中開啟產生的檔案會看到一個帶有灰色占位文字 **Enter name here** 的單一內容控制項。此控制項可編輯、刪除，或日後以其標題 *CustomerName* 透過程式方式存取。

## 常見變化與邊緣情況

| 情境 | 如何調整程式碼 |
|----------|----------------------|
| **Multiple content controls** | 呼叫 `InsertStructuredDocumentTag` 多次，並為每次指定唯一的 `Title`。 |
| **Rich‑text content control** | 使用 `SdtType.RichText` 取代 `PlainText`。 |
| **Date picker control** | 使用 `SdtType.Date`，並可選擇設定 `sdt.DateDisplayFormat`。 |
| **Locking the control** | 設定 `sdt.LockContentControl = true` 以防止使用者移除控制項。 |
| **Finding a control later** | 使用 `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` 並依 `Title` 篩選。 |

這些變化說明了 **Aspose.Words** 在需要 **在 Word 文件中添加內容控制項** 以應對不同表單填寫情境時的彈性。

## 專業提示

* **Performance** – 如果您在迴圈中產生大量文件，請重複使用單一 `DocumentBuilder` 實例，並於每次迭代呼叫 `doc.Clone()`，以避免重複建立物件。  
* **Styling** – 您可以對占位 `Run` 套用 `ParagraphFormat` 或 `Font`，以符合文件的視覺主題。  
* **Validation** – 插入控制項後，您可以檢查 `sdt.IsShowingPlaceholderText` 以確認占位文字正確顯示。  

## 結論

您現在已了解如何使用 Aspose.Words **在 Word 文件中添加內容控制項**，從建立 `DocumentBuilder`、插入純文字 `StructuredDocumentTag`、設定標題，到加入占位文字。完整範例可延伸至其他 SDT 類型、多個控制項，以及進階的鎖定或樣式選項。

Ready to go further? Explore these related topics:

* **在內容控制項內使用表格** – 在 SDT 後使用 `DocumentBuilder.InsertTable`。  
* **從已填寫的控制項擷取資料** – 依標題取得 `Sdt` 節點並讀取其 `Text` 屬性。  
* **使用 OpenXML SDK** – 若您偏好免費且受 Microsoft 支援的函式庫，可採用此替代方案。

請嘗試此程式碼，將其套用於您自己的表單產生工作流程，體驗程式化 Word 自動化的強大功能。

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，建立在此處示範的技巧之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在自己的專案中探索替代實作方式。

- [在 Aspose.Words for .NET 中使用 Document Builder 添加內容](/words/english/net/add-content-using-document-builder/)
- [在 Word 文件中使用 Aspose.Words 插入行內圖片](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [使用 Aspose.Words 建立帶表格的 Word 文件](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}