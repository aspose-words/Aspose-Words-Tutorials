---
category: general
date: 2026-10-10
description: 使用 Aspose.Words 在 C# 中設定按鈕文字並加入 ActiveX 按鈕。了解如何插入按鈕、建立按鈕控制項，以及在 Word
  文件中自訂說明文字。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: zh-hant
lastmod: 2026-10-10
og_description: 在 C# 中使用 Aspose.Words 設定按鈕文字並加入 ActiveX 按鈕。請依照本步驟指南插入按鈕、建立按鈕控制項，並自訂其說明文字。
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: 在 C# 中設定按鈕文字並新增 ActiveX 按鈕 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: 設定按鈕文字並在 C# 中加入 ActiveX 按鈕
url: /zh-hant/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 設定按鈕文字並在 C# 中加入 ActiveX 按鈕

如果您需要在 Word 文件中的 ActiveX 按鈕上 **設定按鈕文字**，本教學將一步步示範。完成本教學後，您將能 **插入按鈕**、建立 **按鈕控制項**，並僅用幾行 C# 程式碼自訂其標題。

在 Word 中使用 ActiveX 控制項是建立互動式表單的常見做法——無論是合約範本、問卷調查，或是內部工具。本範例使用 Aspose.Words for .NET，這是一套不需要安裝 Microsoft Office 即可操作 Word 檔案的函式庫。

## 前置條件

開始之前，請確保您已具備：

* .NET 6.0 SDK 或更新版本  
* Visual Studio 2022（或任何支援 C# 的 IDE）  
* Aspose.Words for .NET 授權（免費評估版足以學習使用）  

同時需要在專案中加入 `Aspose.Words` NuGet 套件的參考：

```bash
dotnet add package Aspose.Words
```

## 如何在 Word 文件中插入按鈕

第一步是建立新的 `Document` 與 `DocumentBuilder`。`DocumentBuilder` 是加入內容（包括 ActiveX 控制項）的入口。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**為什麼這很重要：**`Document` 代表整個 .docx 檔案，而 `DocumentBuilder` 提供高階方法，如 `InsertParagraph` 與 `InsertFormField`。從空白文件開始，可確保按鈕出現在您指定的位置。

## 使用 Forms2OleControl 建立按鈕控制項

接下來建立實際的按鈕控制項。`Forms2OleControl` 是 Aspose.Words 用來處理所有 ActiveX 物件的類別，而 `COMMANDBUTTON` 類型會在 Word 中呈現為可點擊的按鈕。

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**說明：**  
* `InsertForms2OleControl` 會依您提供的座標精確放置控制項。  
* 大小以點 (point) 為單位（1 point = 1/72 吋）。請依版面需求調整這些數值。

## 加入 ActiveX 控制項並為其指定唯一名稱

每個 ActiveX 物件都應有唯一名稱，以便日後（例如在 VBA 中處理事件）引用。

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**小技巧：**名稱請避免使用空格或特殊字元；Word 會將名稱視為內部表單模型的識別子。

## 在 ActiveX 按鈕上設定按鈕文字（Caption）

這裡正是 **設定按鈕文字** 的關鍵。`Caption` 屬性決定使用者在按鈕上看到的標籤。

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

您可以在儲存文件之前隨時變更 Caption。若日後需要本地化介面，只要再次呼叫 `SetCaption` 並傳入不同字串即可。

## 儲存文件並驗證結果

最後，將文件寫入磁碟。以 Microsoft Word 開啟檔案，即可看到帶有自訂標題的按鈕。

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**預期結果：**當您在 Word 中開啟 *ActiveXButton.docx* 時，會看到一個位於指定座標、標示為 **Click Me** 的按鈕。點擊該按鈕會觸發 Word 預設的命令按鈕行為（您日後可透過 VBA 自訂）。

![Set button text example](https://example.com/activex-button.png){alt="設定按鈕文字範例"}

## 加入 ActiveX 按鈕並處理事件（可選）

若需要按鈕執行自訂動作，可加入回應 `Click` 事件的 VBA 巨集。巨集可以以程式方式注入，但超出本教學範圍。重要的是按鈕已經存在且 Caption 已設定好，隨時可供您自行實作事件處理。

## 常見問題與避免方式

| 問題 | 為什麼會發生 | 解決方式 |
|------|--------------|----------|
| 按鈕位置錯位 | 座標使用點 (point) 而非像素 | 將像素值轉換為點 (`points = pixels * 72 / DPI`) |
| 儲存後 Caption 未變更 | `SetCaption` 在 `Save` 之後呼叫 | 必須在呼叫 `doc.Save` **之前** 設定 Caption |
| 舊版 Word 看不到控制項 | 某些舊版 Word 缺乏完整的 ActiveX 支援 | 在目標 Word 版本上測試；必要時改用 `CheckBox` 或 `DropDownList` 作為備援 |
| 輸出時出現授權警告 | 使用評估授權已過期 | 透過 `License license = new License(); license.SetLicense("Aspose.Words.lic");` 套用正式授權 |

## 完整可執行範例

以下是完整程式碼，您可以直接複製、貼上並執行。程式碼已包含所有必要的 `using` 指示，示範從建立文件到儲存的完整流程。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

使用 `dotnet run` 執行程式。執行完畢後，開啟 *ActiveXButton.docx*，確認按鈕的 Caption 為 **Click Me**。

## 本章重點回顧

* 您學會了如何使用 Aspose.Words 在 ActiveX 按鈕上 **設定按鈕文字**。  
* 您掌握了 **插入按鈕**、**建立按鈕控制項**、以及 **加入 ActiveX 控制項** 的完整步驟。  
* 您現在擁有可重複使用的程式碼片段，能套用於任何以表單為基礎的 Word 自動化專案。

## 往後的學習方向

* 探索其他 `Forms2OleControlType` 如 `CHECKBOX`、`LISTBOX`，打造更豐富的表單。  
* 結合 VBA 巨集讓按鈕執行計算或資料驗證。  
* 使用 Aspose.Words 的 `FormField` API 讀取使用者填寫的內容。

歡迎自行調整大小、位置與 Caption，以符合您的設計需求。若遇到問題，請參考 Aspose.Words 文件，裡面對本教學中使用的每個類別都有詳細說明。

祝開發順利！


## 接下來該學什麼？

以下教學與本篇內容緊密相關，能進一步深化您所學的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索不同的實作方式。

- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}