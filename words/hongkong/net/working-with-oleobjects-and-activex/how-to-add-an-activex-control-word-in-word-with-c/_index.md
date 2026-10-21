---
category: general
date: 2026-09-30
description: 使用 C# 在 Word 文件中加入 ActiveX 控制項。學習如何插入 ActiveX 按鈕、加入指令按鈕，並使其可點擊。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: zh-hant
lastmod: 2026-09-30
og_description: 使用 C# 為 Word 文件新增 ActiveX 控制項。請參考本完整指南，了解如何插入 ActiveX 按鈕、加入命令按鈕，並使其可點擊。
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: 在 Word 文件中加入 ActiveX 控制項 – 逐步 C# 指南
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: 如何使用 C# 在 Word 中加入 ActiveX 控制項
url: /zh-hant/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 C# 添加 ActiveX 控制項字元

如果您需要在 Microsoft Word 檔案中嵌入 **ActiveX 控制項字元**，本教學將一步一步示範完整作法。您將看到一個可直接執行的範例，會插入可點擊的按鈕、儲存文件，且相容最新的 Aspose.Words for .NET。

加入 ActiveX 控制項字元可讓您建立互動式表單、自訂對話框，或類似原生 Word 控制項的簡易 UI 元件。無論是需要使用者互動的合約範本，或是需要「執行」按鈕的報告，以下步驟都能滿足需求。

## 前置條件

在開始之前，請確保您已具備：

* .NET 6.0 SDK 或更新版本（程式碼亦可在 .NET Framework 4.8 上執行）
* Visual Studio 2022（或任何支援 C# 的 IDE）
* 已安裝 Aspose.Words for .NET（`dotnet add package Aspose.Words`）
* 基本的 C# 與 Word 文件結構概念

> **專業提示：** `InsertForms2OleControl` 方法僅支援傳統的 “Forms 2.0” 控制項，也就是 Word 用於表單欄位的 ActiveX 控制項。即使目標是較新版的 Office，該控制項仍會在桌面客戶端正確呈現。

## 第一步：建立專案並匯入命名空間

建立一個新的 Console 專案，並加入必要的 `using` 陳述式。這樣編譯器才能找到 `Document`、`DocumentBuilder` 與 `OleControlType` 類別。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

`Aspose.Words` 命名空間提供高階的 Word 處理 API，而 `Aspose.Words.Drawing` 則包含用於指定 ActiveX 控制項類型的 `OleControlType` 列舉。

## 第二步：載入來源 Word 文件

必須先取得要修改的 Word 檔案。以下程式碼會從您指定的資料夾載入 `input.docx`。

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

如果檔案不存在，Aspose.Words 會拋出 `FileNotFoundException`。如需更優雅的錯誤處理，可將呼叫包在 `try/catch` 區塊中。

## 第三步：建立 DocumentBuilder 以編輯文件

`DocumentBuilder` 是插入文字、影像與控制項的主要工具。它會維持一個游標，指向下一個元素將被放置的位置。

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

預設情況下，builder 的游標位於第一個節的開頭。您可以使用 `MoveToDocumentEnd()` 或 `MoveToParagraph(index)` 等方法將游標移至其他位置，以便把按鈕放在想要的地方。

## 第四步：插入 ActiveX CommandButton 控制項

以下是本教學的核心：插入一個 **ActiveX 控制項字元**，呈現為可點擊的按鈕。`InsertForms2OleControl` 方法接受兩個參數——控制項類型與顯示文字（或名稱）。

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **為什麼使用 `OleControlType.CommandButton`？**  
  它告訴 Word 建立傳統的 Forms 2.0 命令按鈕，會顯示標題，之後可連結至巨集或 VBA 程式碼。

* **標題的作用是什麼？**  
  字串 `"ClickMe"` 會成為按鈕的可見文字。您可以依需求自行更改為任何 UI 文字。

### 在特定位置插入按鈕

如果需要在某段文字之後插入按鈕，先將 builder 移動到該段落：

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## 第五步：儲存已修改的文件

插入控制項後，將變更寫入新檔（或覆寫原檔）。

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

當您在桌面版 Word 中開啟 `output.docx` 時，會看到標示為 **ClickMe**（或 **Submit**，取決於您設定的標題）的按鈕。預設情況下，設計模式下點擊按鈕不會執行任何動作；您可以稍後透過 Word 的「開發人員」索引標籤指派巨集。

## 完整可執行範例

以下是一個獨立的程式，示範完整工作流程。將程式碼複製到新 Console 專案的 `Program.cs`，然後執行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### 預期輸出

* 主控台會印出成功訊息與輸出路徑。
* 開啟 `output.docx` 後，可在 builder 插入的位置看到 **ClickMe** 按鈕。
* 透過 Word 的 **開發人員 → 設計模式**，您可以選取、調整大小或指派巨集給該按鈕。

## 常見問題與邊緣案例處理

| 問題 | 解答 |
|----------|--------|
| **如何在頁首/頁尾插入 ActiveX 按鈕？** | 在呼叫 `InsertForms2OleControl` 前，使用 `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` 將 builder 移至頁首/頁尾。 |
| **如果需要勾選框而不是按鈕該怎麼做？** | 使用 `OleControlType.CheckBox`，並提供類似 `"Agree"` 的標題。 |
| **按鈕會在 Word Online 中運作嗎？** | 不會。Word Online 不支援傳統的 Forms 2.0 ActiveX 控制項，按鈕僅在桌面客戶端顯示。 |
| **可以程式化設定按鈕大小嗎？** | 插入後，可透過 `builder.CurrentParagraph.Runs[0].GetShape()` 取得 `Shape` 物件，並調整 `Width`／`Height`。 |
| **有辦法從程式碼指派巨集嗎？** | Aspose.Words 不提供巨集編輯功能。您必須在 Word 中手動附加巨集，或改用 Office Interop API。 |

## 生產環境使用小技巧

* **避免硬編碼路徑** ─ 使用 `Path.Combine` 及設定檔管理路徑。
* **釋放 Document** ─ 若處理大型檔案，建議以 `using` 包裹，以便及時釋放記憶體。
* **驗證輸出** ─ 以程式方式檢查文件是否包含 `OleControl` 類型的 Shape，方法是遍歷 `doc.GetChildNodes(NodeType.Shape, true)`。
* **安全性說明** ─ ActiveX 控制項會在客戶端執行程式碼，僅向受信任使用者分發文件，並考慮使用數位簽章。

## 結論

現在您已掌握如何使用 C# 在 Word 文件中加入 **ActiveX 控制項字元**。透過載入文件、建立 `DocumentBuilder`、使用 `InsertForms2OleControl` 插入指令按鈕，最後儲存檔案，即可自動產生互動式 Word 表單。您可以嘗試其他 `OleControlType`、將控制項放入頁首或表格，並結合巨集打造更豐富的使用者體驗。

---

*下一步*：探索 **插入其他類型的 ActiveX 控制項**、學習 **透過 VBA 為指令按鈕加入事件處理程序**，以及閱讀 **插入 ActiveX 按鈕的跨平台最佳實踐**。

## 接下來該學什麼？

以下教學與本指南的技巧密切相關，能進一步擴充您的應用。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您熟悉更多 API 功能，並在專案中嘗試不同的實作方式。

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}