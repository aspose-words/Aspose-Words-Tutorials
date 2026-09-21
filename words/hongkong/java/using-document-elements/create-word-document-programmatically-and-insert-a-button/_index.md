---
category: general
date: 2026-09-21
description: 以程式方式建立 Word 文件，並學習如何使用 DocumentBuilder 來儲存 Word 文件的按鈕、插入指令按鈕文字，以及設定指令按鈕標題。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: zh-hant
lastmod: 2026-09-21
og_description: 使用 Aspose.Words 程式化建立 Word 文件。了解如何儲存 Word 文件按鈕、插入指令按鈕、設定指令按鈕標題，並使用
  DocumentBuilder 建立互動式表單。
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: 以程式方式建立 Word 文件並加入按鈕
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: 以程式方式建立 Word 文件並插入按鈕
url: /zh-hant/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 以程式方式建立 Word 文件並插入按鈕

如果您需要**以程式方式建立 Word 文件**，Aspose.Words 提供了流暢的 API，讓您可以加入如 CommandButton 等互動控制項。本教學亦說明**如何使用 DocumentBuilder**、**如何儲存 Word 文件按鈕**，以及**如何設定指令按鈕標題**，使按鈕在 .docx 檔案中呈現如您所預期的樣子。

您將學會如何：

* 使用 `Document` 初始化空白文件。
* 使用 `DocumentBuilder` 編輯文件。
* 插入 **CommandButton**（`insert command button word`）。
* 設定按鈕的名稱與可見標題（`set command button caption`）。
* 將結果持久化至磁碟（`save word document button`）。

這些步驟針對使用 C# 的 .NET 開發人員，並以最新的 Aspose.Words for .NET (v24.10) 為例。除 Aspose.Words 外，無需其他 NuGet 套件。

---

## 開始之前您需要的條件

| 先決條件 | 原因 |
|--------------|--------|
| Visual Studio 2022（或任何 C# IDE） | 用於編譯與執行範例程式碼。 |
| .NET 6.0 SDK 或更新版本 | 提供範例所需的執行環境。 |
| Aspose.Words for .NET（v24.10 或更新版本） | 此函式庫可讓您**以程式方式建立 Word 文件**並操作表單控制項。 |
| 具備 C# 與物件導向程式設計概念的基本熟悉度 | 需要了解程式流程。 |

You can install Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## 以程式方式建立 Word 文件

第一步是實例化一個空的 `Document`。此物件在記憶體中代表整個 Word 檔案。

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

以程式方式建立文件可為您提供一個乾淨的畫布，您可以在其上加入段落、表格或互動控制項。  

---

## 如何使用 DocumentBuilder

`DocumentBuilder` 是編輯 `Document` 的主要類別。它提供插入文字、影像與表單欄位的方法。本教學中我們使用它來放置 CommandButton。

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

此建構器維持一個內部游標，指向目前的插入位置。預設情況下，它會從第一節的開頭開始，這對本範例而言非常合適。

---

## 插入指令按鈕

Aspose.Words 將 CommandButton 視為 ActiveX 控制項。`InsertForms2OleControl` 方法會建立一個通用的 OLE 控制項，之後我們再將其設定為按鈕。

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

此時控制項已存在於文件中，但在未定義其類型前不會有任何視覺呈現。

---

## 設定指令按鈕標題

現在我們告訴 OLE 控制項它應該以 CommandButton 的方式運作，並為其設定友善的標籤。

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

設定**指令按鈕標題**是必要的，因為 Word 會在按鈕表面顯示此文字。如果省略 `SetCaption`，按鈕將顯示為通用標籤。

---

## 儲存 Word 文件按鈕

最後，將文件持久化至磁碟。`Save` 方法會將整個 Word 套件（包括新插入的按鈕）寫入 .docx 檔案。

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

檔案 `CommandButton.docx` 現在包含一個標示為 **Submit** 的完整功能按鈕。使用者在 Microsoft Word 中開啟此檔案並點擊按鈕時，預設動作（您之後可透過 VBA 綁定）將被觸發。

---

## 完整範例程式

以下是完整的程式碼，您可以複製、貼上並執行。它示範了從建立文件到儲存按鈕的完整工作流程。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**預期結果**

* 一個名為 `CommandButton.docx`、位於您指定路徑的檔案。
* 在 Microsoft Word 中開啟該檔案時，第一頁會顯示一個 **Submit** 按鈕。
* 該按鈕可被選取、調整大小，或從 Word 的 **Developer** 索引標籤連結至巨集。

---

## 常見問題與邊緣案例處理

| 問題 | 答案 |
|----------|--------|
| *如果需要多個按鈕怎麼辦？* | 重複第 3–6 步，使用不同的名稱與標題。每個按鈕必須有唯一的 `SetName` 值。 |
| *我可以設定按鈕大小嗎？* | 可以。插入控制項後，您可以透過 `OleFormat` 物件修改其 `Width` 與 `Height` 屬性。 |
| *按鈕能在所有 Word 版本上運作嗎？* | ActiveX 控制項僅在 Windows 桌面版 Word 中受支援，於 Word Online 或 macOS 上不會呈現。 |
| *如何加入點擊事件處理程序？* | 您需要撰寫引用按鈕名稱（`btnSubmit`）的 VBA 程式碼。可使用 `doc.VbaProject` 將 VBA 巨集嵌入。 |
| *如果需要將按鈕插入表格儲存格該怎麼做？* | 在呼叫 `InsertForms2OleControl` 前，先將 builder 的游標移至目標儲存格（`builder.MoveTo(cell.FirstParagraph)`）。 |

---

## 進階技巧

* **進階提示：** 總是使用 `SetName` 設定有意義的名稱。這可簡化 VBA 自動化並使除錯更容易。
* **注意：** 別忘記呼叫 `SetControlType`。若未呼叫，OLE 物件會顯示為通用佔位符，而非可點擊的按鈕。
* **效能提示：** 若在迴圈中產生大量文件，請重複使用同一個 `DocumentBuilder` 實例，並在每次插入前呼叫 `builder.MoveToDocumentEnd()`，以避免不必要的游標重設。

---

## 下一步

既然您已了解如何**以程式方式建立 Word 文件**、**插入指令按鈕**、**設定指令按鈕標題**以及**儲存 Word 文件按鈕**，即可探索更進階的情境：

* 加入 **TextFormField** 控制項以供使用者輸入。
* 將按鈕與 **MacroButton** 欄位結合，以直接執行 VBA。
* 使用 **DocumentBuilder.InsertImage** 在按鈕上放置圖示。
* 與 ASP.NET 整合，以產生 Word 表單於

## 接下來您應該學習什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [建立新 Word 文件](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [使用 Aspose.Words for .NET 建立 Word 文件](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [在 Word 文件中插入內嵌影像](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}