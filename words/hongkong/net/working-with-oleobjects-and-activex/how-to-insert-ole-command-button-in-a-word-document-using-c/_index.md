---
category: general
date: 2026-10-07
description: 學習如何使用 Aspose.Words C# 在 Word 文件中插入 OLE 命令按鈕。逐步說明涵蓋 DocumentBuilder、屬性以及檔案儲存。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: zh-hant
lastmod: 2026-10-07
og_description: 使用 C# 在 Word 文件中插入 OLE 命令按鈕。遵循本簡潔教學，新增、設定並儲存具功能的 CommandButton（使用
  Aspose.Words）。
og_image_alt: Insert OLE command button example in Word document
og_title: 使用 C# 在 Word 中插入 OLE 指令按鈕 – 完整 Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: 如何使用 C# 在 Word 文件中插入 OLE 命令按鈕
url: /zh-hant/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 C# 插入 OLE 命令按鈕

如果您需要以程式方式 **插入 OLE 命令按鈕** 到 Word 檔案，本教學將示範如何使用 Aspose.Words for .NET 完成。無論是建立填寫式報告，或是自動化需要使用者互動的範本，以下步驟提供完整可執行的解決方案。

您將學會如何建立空白文件、使用 `DocumentBuilder` 放置 `Forms2OleControl`、設定按鈕的說明文字與名稱，最後儲存為 `.docx`。除了 Aspose.Words 套件外，無需其他外部工具。

## 前置條件

開始之前，請確保您已具備：

* .NET 6.0 或更新版本（此程式碼亦相容 .NET Framework 4.7 以上）
* 有效的 Aspose.Words for .NET 授權或免費評估金鑰
* Visual Studio 2022（或您慣用的 C# IDE）
* 基本的 C# 語法與 Word OLE 概念

> **小技巧：** 若使用免費評估版，產生的文件會帶有小水印。授權版會自動移除水印。

## 第一步：安裝 Aspose.Words

透過 NuGet 將 Aspose.Words 套件加入您的專案：

```bash
dotnet add package Aspose.Words
```

此套件包含 `Aspose.Words.Drawing` 與 `Aspose.Words.Drawing.Ole` 命名空間，為使用 OLE 控制項所必需。

## 第二步：使用 DocumentBuilder 插入 OLE 命令按鈕

教學的核心是 `InsertForms2OleControl` 方法。它會在指定位置與尺寸建立 **Forms2 OLE CommandButton**。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### 為什麼這樣寫會有效

* `DocumentBuilder` 是以程式方式建立 Word 文件的主要 API。  
* `InsertForms2OleControl` 告訴 Aspose.Words 嵌入 **Forms2 OLE 控制項**，這是支援命令按鈕、核取方塊等的舊版 Word 表單技術。  
* `OleControlType.CommandButton` 列舉值指定插入的控制項類型為 **command button**——也就是您想要 **插入 OLE 命令按鈕** 的確切類型。  
* `Rectangle` 決定視覺上的放置位置。您可調整 X/Y 座標或寬高，以符合版面需求。

## 第三步：儲存文件

設定完按鈕後，將文件寫入磁碟。您可以選擇 Aspose.Words 支援的任何格式（`.docx`、`.pdf`、`.odt`…）。本教學以 Word 文件為例。

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

當您在 Microsoft Word 中開啟 `CommandButton.docx` 時，會看到一個標示為 **Click Me** 的可點擊按鈕。點擊該按鈕會觸發預設的「執行巨集」對話框，因為此按鈕屬於 OLE 表單控制項；日後您可自行附加巨集或 VBA 程式碼。

## 第四步：驗證結果（預期輸出）

開啟產生的檔案：

1. 按鈕會出現在您指定的座標（大約距左、上邊界 1.4 英吋）。  
2. 說明文字為 **Click Me**。  
3. 名稱屬性 (`cmdSubmit`) 可在 Word 的 **開發人員 → 屬性** 面板中看到，方便在 VBA 中引用此控制項。

![Insert OLE command button example in Word document](insert-ole-button.png)

*Image alt text*: **Insert OLE command button example in Word document** (includes primary keyword for accessibility and SEO).

## 邊緣情況與常見問題

### 1. 按鈕未出現在預期位置，該怎麼辦？

* Word 使用「點」(points) 而非像素。請將螢幕像素轉換為點數 (`points = pixels * 72 / DPI`)。  
* 確認矩形不與頁邊距相交，否則 Word 可能會自行移動控制項。

### 2. 可以將按鈕插入到已有的文件嗎？

可以。使用 `new Document("Existing.docx")` 載入文件，然後沿用相同的 `DocumentBuilder` 流程。只要在呼叫 `InsertForms2OleControl` 前，先將 Builder 游標移至適當位置（例如 `builder.MoveToDocumentEnd()`、`builder.MoveToBookmark("myBookmark")` 等）。

### 3. 要如何為按鈕附加巨集？

Aspose.Words 本身不會產生 VBA 程式碼，但您可以在文件產生後嵌入巨集：

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. 在 Linux 上的 .NET Core 能使用嗎？

OLE 控制項是 Windows 專屬功能，因為它依賴 COM。於 Linux 環境下按鈕仍會被插入，但會以靜態圖片呈現，無互動行為。若需跨平台互動表單，建議改用內容控制項 (`StructuredDocumentTag`)。

### 5. 若需要不同尺寸或多個按鈕該怎麼做？

建立多個具有不同座標的 `Rectangle` 物件，重複呼叫 `InsertForms2OleControl`。每個按鈕皆可設定獨立的 `Caption` 與 `Name`。

## 完整範例程式

以下提供可直接貼到 Console 應用程式的完整程式碼，包含所有必要的 `using` 指示、錯誤處理與註解。

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

執行程式後，開啟產生的 `CommandButton.docx`，即可看到已就緒的 **Click Me** 按鈕，供您進一步客製化。

## 結論

現在您已掌握如何使用 C# 與 Aspose.Words **插入 OLE 命令按鈕** 到 Word 文件。本教學涵蓋：

* 安裝 Aspose.Words 套件  
* 使用 `DocumentBuilder.InsertForms2OleControl` 搭配 `OleControlType.CommandButton`  
* 設定按鈕屬性（`Caption`、`Name`）  
* 儲存並驗證輸出  

接下來您可以探索 **Aspose.Words OLE 控制項** 用於核取方塊、下拉式清單，或嵌入整個 Excel 工作表的應用。若需在大型範本中自動化 **Word OLE 命令按鈕**，或改用現代的 **內容控制項** 以提升跨平台相容性，也都是不錯的方向。

歡迎自行調整矩形數值、加入多個按鈕，或附加 VBA 巨集，以符合您的應用需求。祝開發順利！

## 接下來該學什麼？

以下教學與本篇內容密切相關，能進一步擴展您的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能與替代實作方式。

- [Insert Ole Object In Word Document](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Insert Ole Object In Word Document As Icon](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Insert Ole Object In Word With Ole Package](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}