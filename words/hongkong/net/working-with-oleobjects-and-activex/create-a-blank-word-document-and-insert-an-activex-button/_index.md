---
category: general
date: 2026-11-18
description: 使用 C# 建立空白 Word 文件並插入 ActiveX 按鈕。學習如何新增控制項、設定按鈕文字，並儲存檔案。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: zh-hant
lastmod: 2026-11-18
og_description: 使用 C# 建立空白 Word 文件並插入 ActiveX 按鈕。請參考本完整教學，以加入控制項、設定按鈕標題，並儲存結果。
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: 建立空白 Word 文件並插入 ActiveX 按鈕 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: 建立空白 Word 文件並插入 ActiveX 按鈕
url: /zh-hant/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立一個空白的 Word 文件並插入 ActiveX 按鈕

如果您需要 **建立一個空白的 Word 文件** 並在其中放置互動式 ActiveX 按鈕，本指南將會完整示範如何使用 Aspose.Words for .NET 來達成。您將看到完整程式碼，了解每一行的意義，並學習如何 **設定按鈕標題**，讓控制項看起來已準備好供使用者互動。

除了主要目標外，我們還會說明 **如何插入 ActiveX**、**如何新增控制項** 到 Word 檔案的步驟，以及 **插入 ActiveX 按鈕** 並自訂標題的細節。完成後，您將擁有一套可重複使用的模式，適用於任何需要嵌入 UI 元素的文件自動化情境。

## 您將學習到

* 如何以程式方式 **建立一個空白的 Word 文件**。  
* 插入 **ActiveX 按鈕** 並設定其屬性所需的精確 API 呼叫。  
* 如何 **設定按鈕標題**，使控制項顯示所需文字。  
* 保存檔案至您指定位置的技巧，以及處理常見問題的方式。

### 前置條件

* .NET 6.0 或更新版本（此程式碼亦適用於 .NET Framework 4.6+）。  
* 已安裝 Aspose.Words for .NET（`Install-Package Aspose.Words`）。  
* 具備 C# 以及 Visual Studio 或任何相容 .NET 的 IDE 基本知識。

---

## 使用 Aspose.Words 建立空白的 Word 文件

第一步是實例化一個空的 `Document` 物件。此物件代表一個 Word 檔案，裡面在加入任何內容之前是沒有任何資料的。

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*為何重要*：空的 `Document` 為您提供一塊乾淨的畫布。之後您可以加入段落、表格或控制項，而不必擔心既有的格式設定。

---

## 初始化 DocumentBuilder 以操作文件

`DocumentBuilder` 是一個輔助類別，讓您能在目前游標位置插入內容。它會自動追蹤您在文件中的位置。

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*為何重要*：若沒有 `DocumentBuilder`，您必須手動操作低階的節點樹。使用 builder 可簡化文字、圖片與 ActiveX 控制項的插入。

---

## 如何插入 ActiveX 按鈕（insert activex button）

現在我們使用 `InsertForms2OleControl` 來嵌入 ActiveX 控制項。此方法需要三個參數：

1. 控制項類型 (`OleControlType.CommandButton`)。  
2. 控制項的內部名稱（供 VBA 或巨集程式碼使用）。  
3. 一個定義頁面上位置與大小的 `RectangleF`。

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*為何重要*：這是 **如何插入 activex** 到 Word 文件的核心。矩形的座標以點為單位（1 點 = 1/72 英吋）。調整這些值即可將按鈕放置在所需位置。

### 小技巧

如果您需要按鈕出現在特定頁面，請先移動 builder 的游標：

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## 如何設定按鈕標題（set button caption）

控制項放置完成後，您可以修改其屬性。最顯眼的屬性是 `Caption`，它決定按鈕上顯示的文字。

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*為何重要*：使用者看到的是標題，而非內部名稱。修改它可讓按鈕在最終文件中具有意義。

---

## 儲存包含按鈕的文件

最後，將文件寫入磁碟。您可以選擇任何支援的格式（`.docx`、`.pdf` 等）。此處我們以 Word 文件儲存。

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*為何重要*：將檔案持久化後，您可以在 Microsoft Word 中開啟並測試按鈕。文件開啟時，按鈕會顯示標題「Press」。

### 預期結果

在 Word 中開啟 `with_button.docx` 會看到一個空白頁面，頁面上有一個標示為 **Press** 的矩形按鈕。預設情況下點擊按鈕不會有任何動作，因為未附加 VBA 巨集，但此控制項已完整運作，之後可連結至程式碼。

---

## 如何將控制項加入特定段落（how to add control）

有時您希望按鈕位於特定段落內，例如在一些說明文字之後。使用 `MoveTo` 於插入控制項前定位 builder。

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*為何重要*：此範例示範了 **如何將控制項加入** 於特定情境中，確保文件版面保持合理。

---

## 常見陷阱與避免方法

| 問題 | 發生原因 | 解決方法 |
|-------|----------------|-----|
| 按鈕顯示在頁面外 | 矩形座標超出頁面邊界 | 使用 `builder.PageSetup` 取得頁面尺寸，並計算安全的 `RectangleF`。 |
| 標題未顯示 | `Caption` 在控制項完全初始化前設定 | 在 `InsertForms2OleControl` 呼叫之後 **設定** `Caption`，如第 4 步所示。 |
| 文件儲存時未包含按鈕 | 插入後 Builder 的游標被移動，且未提交變更 | 保持 Builder 在同一頁，或在儲存前呼叫 `builder.Document.UpdatePageLayout()`。 |

---

## 完整、可執行的範例

以下是完整的程式碼，您可以複製、貼上並執行。它會建立一個空白的 Word 檔案，插入 ActiveX 按鈕，設定其標題，並儲存結果。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**輸出**：執行程式後，於 Microsoft Word 開啟 `C:\Temp\with_button.docx`。您會看到單一頁面，顯示文字「Below is an ActiveX button created programmatically:」以及一個標示為 **Press** 的按鈕。

---

## 結論

您現在已了解如何使用 Aspose.Words for .NET **建立空白的 Word 文件**、**插入 ActiveX 按鈕**、**設定按鈕標題**，以及 **儲存** 結果。透過變更 `OleControlType`，相同模式亦可延伸至其他 ActiveX 控制項（核取方塊、清單方塊等）。  

接下來，您可以探索使用 VBA 來 **插入 ActiveX 按鈕** 事件，或 **將控制項加入** 已包含內容的現有文件。這兩個主題皆直接建立在本指南所討論的概念之上。

祝開發愉快，亦歡迎自行嘗試不同的尺寸、位置與標題，以符合您應用程式的 UI 需求！

## 接下來您可以學習什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [如何使用 C# 建立含 ActiveX 指令按鈕的 Word 文件](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [如何在 Word 文件中使用 Aspose.Words 新增 ActiveX 按鈕](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}