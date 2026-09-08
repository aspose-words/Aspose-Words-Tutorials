---
category: general
date: 2026-09-08
description: 使用 C# 設定標籤名稱並在 Word 文件中建立內容控制項（SDT）。了解如何新增 SDT、向標籤寫入文字以及修改文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: zh-hant
lastmod: 2026-09-08
og_description: 使用 C# 設定標籤名稱並在 Word 文件中建立內容控制項（SDT）。請依照此逐步指南新增 SDT、將文字寫入標籤，並修改文件。
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: 設定標籤名稱並在 Word 文件中加入 SDT – C# 指南
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 C# 設定標籤名稱並在 Word 文件中加入 SDT
url: /zh-hant/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 C# 設定標籤名稱並新增 SDT

如果您需要在處理 Word 檔案時 **設定標籤名稱** 給 StructuredDocumentTag (SDT)，本指南將完整說明做法。您將看到一個完整且可執行的範例，**建立內容控制項**、將文字寫入標籤，並 **端對端修改 Word 文件**。

開發人員常會問，*「如何將 sdt 加入現有的 .docx，然後 *寫入文字到標籤*？」*——答案就在於使用 Aspose.Words for .NET API。完成本教學後，您將能開啟 Word 檔案、插入純文字 SDT、設定其標籤名稱、填入內容，並儲存變更而不留下任何未釋放的資源。

## 前置條件

* 已安裝 .NET 6.0 或更新版本。
* 有效的 Aspose.Words for .NET 授權（或使用評估版）。
* Visual Studio 2022（或任何支援 C# 的 IDE）。
* 一個放在可於程式碼中參考之資料夾的輸入 Word 文件（`input.docx`）。

## 步驟 1：設定專案並匯入命名空間

建立一個新的 Console App 專案，並加入 Aspose.Words NuGet 套件：

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

接著，在 `Program.cs` 的頂部加入必要的 `using` 指令：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

這些命名空間讓您能使用 `Document`、`DocumentBuilder` 與 `StructuredDocumentTag` 類別，這些都是 **修改 Word 文件** 所必需的。

## 步驟 2：載入現有的 Word 文件

第一步是載入您想編輯的檔案。此步驟在每個 **modify word document** 內容的情境下皆為必要。

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **為什麼要先載入文件** – `Document` 物件在記憶體中代表整個 .docx 套件。只有在載入之後，才能安全地插入如 SDT 等新節點。

## 步驟 3：插入 StructuredDocumentTag (SDT) 並設定其標籤名稱

現在來回答核心問題：**how to add sdt** 與 **set tag name**。我們使用 `DocumentBuilder.InsertStructuredDocumentTag` 搭配 `SdtType.PlainText`。第二個參數即為標籤名稱，您之後可以在程式碼或 Word 介面中引用它。

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **說明** – `InsertStructuredDocumentTag` 會回傳一個 `StructuredDocumentTag` 實例。透過傳入 `"MyTag"`，我們在建立時即 **設定標籤名稱**。若日後需要變更，可將新值指派給 `sdt.Tag`。

## 步驟 4：將文字寫入新建立的標籤

SDT 建立後，通常會想 **write text to tag**，讓最終使用者看到預設或佔位文字。`SetText` 方法正是執行此操作。

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **為什麼使用 SetText** – 直接對 `Text` 屬性賦值會取代整個節點層級。`SetText` 能安全地更新內容控制項的內部文字，同時保留其結構。

## 步驟 5：儲存已修改的文件

最後，將變更寫入新檔案。這樣就完成了 **modify word document** 工作流程。

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

當您在 Microsoft Word 中開啟 `output.docx` 時，會看到一個標示為 **MyTag** 的純文字內容控制項，內含文字「Sample content」。此控制項可手動編輯，且標籤名稱仍可透過 Word 的開發者工具存取。

## 完整原始碼

以下為完整、獨立的程式。將其複製到 `Program.cs` 後執行；不需要其他程式碼片段。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### 預期在主控台的輸出

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### 產生的 Word 檔案長什麼樣子

![顯示名為 MyTag、文字為「Sample content」的內容控制項的 Word 文件](/images/word-sdt-example.png){: .img-fluid alt="在 Word 文件中設定標籤名稱的範例"}

*此螢幕截圖說明了 SDT，其 **tag name** 設為 *MyTag*，且可見嵌入的文字。*

## 常見變化與邊緣情況

| 情況 | 處理方式 |
|-----------|------------------|
| **建立富文字 SDT** | 使用 `SdtType.RichText` 取代 `PlainText`。 |
| **在插入後設定不同的標籤名稱** | `sdt.Tag = "NewTag";` – 您可以隨時重新指派標籤名稱。 |
| **在特定段落內加入 SDT** | 在呼叫 `InsertStructuredDocumentTag` 前，先移動 builder 的游標 (`builder.MoveToParagraph(index)`)。 |
| **同一文件中有多個 SDT** | 對每個控制項重複步驟 3‑4；每個都可以有唯一的標籤名稱。 |
| **處理受保護的文件** | 在插入 SDT 前，確保文件已解除保護 (`doc.Unprotect()`)。 |

## 專業提示：打造穩健的 Word 自動化

* **盡早授權** – 在 `Main` 開頭呼叫 `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` 以避免評估水印。
* **釋放物件** – 若目標為 .NET Framework，將 `Document` 包在 `using` 區塊中，以確保檔案句柄被釋放。
* **驗證標籤是否存在** – 之後讀取文件時，使用 `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` 依 `Tag` 屬性定位標籤。
* **效能** – 對於大型文件，使用 `LoadOptions` 搭配 `LoadFormat.Docx` 與 `LoadFormat.Auto` 僅載入必要的區段。

## 結論

您現在已了解如何使用 C# **設定標籤名稱**、**建立內容控制項**、**寫入文字到標籤**，以及 **修改 Word 文件**。完整範例展示了 **how to add sdt** 的標準做法，並安全地保存變更。  

從此開始

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並在此基礎上延伸。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [使用 Document Builder 新增內容於 Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Word 文件 - 如何移除內容](/words/english/net/remove-content/)
- [使用 Aspose.Words 建立 Word 文件 – 步驟說明指南](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}