---
category: general
date: 2026-07-19
description: 使用 Aspose.Words C# 建立 Word 文件，學習如何加入 ActiveX 命令按鈕、設定按鈕大小，以及以程式方式插入按鈕。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: zh-hant
lastmod: 2026-07-19
og_description: 使用 Aspose.Words C# 建立 Word 文件，瞬間嵌入 ActiveX 命令按鈕。按照一步一步的教學，輕鬆設定按鈕大小並插入按鈕。
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: 使用 ActiveX 按鈕建立 Word 文件 – C# 教學
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: 使用 ActiveX 按鈕建立 Word 文件 – C# 指南
url: /zh-hant/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 ActiveX 按鈕建立 Word 文件 – 完整 C# 指南

有沒有想過如何 **create word document**，其中包含可運作的 ActiveX 按鈕？也許你正在自動化報告，需要在檔案內直接放置一個可點擊的「批准」控制項。在本教學中，我們將一步步示範——使用 Aspose.Words for .NET 新增 ActiveX 指令按鈕、設定尺寸，並將其插入到需要的位置。  

如果你曾經想過 *how to add activex* 控制項而不必手動開啟 Word，這裡正是你要的地方。完成後，你將擁有可執行的範例、每一步的清晰說明，以及處理常見問題的技巧。

## 你將學到什麼

- 如何在 C# 專案中設定 Aspose.Words  
- 完整程式碼，可 **create word document** 並嵌入 ActiveX 指令按鈕  
- 如何 **set button size** 以及自訂按鈕的說明文字與名稱  
- 正確的 **insert command button** 方法，以及 **how to insert button** 在文件任意位置的技巧  
- 邊緣案例考量（Word 版本、平台限制、安全警告）

### 前置條件

- .NET 6.0 或更新版本（程式碼亦可於 .NET Framework 4.7+ 上執行）。  
- 有效的 Aspose.Words for .NET 授權（或免費評估金鑰）。  
- Visual Studio 2022（或任何你喜歡的 IDE）。  
- 基本熟悉 C# 與物件導向程式設計。

不需要其他第三方函式庫。

---

## 步驟 1：建立 Word 文件 – 專案設定

在我們能夠 **insert command button** 之前，需要先有一個空白的 Word 檔案可供使用。此步驟同時示範使用 Aspose.Words 的經典 “create word document” 範本。

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** `Document` 代表整個 .docx 檔案，而 `DocumentBuilder` 追蹤目前的游標位置。所有後續的插入（包括我們的 ActiveX 控制項）皆相對於此 builder 進行。

## 步驟 2：如何加入 ActiveX – 建立 CommandButton 控制項

既然文件已存在，讓我們來處理 **how to add activex** 的部分。Aspose.Words 提供 `Forms2OleControl` 類別以操作 ActiveX 物件。此處我們將建立一個指令按鈕並設定其屬性，包含 **set button size** 的需求。

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Pro tip:** 大小以點 (point) 為單位測量 (1 point = 1/72 吋)。請依版面需求調整數值；對於一般工具列按鈕，120 × 30 會相當合適。

## 步驟 3：插入指令按鈕 – **Insert Command Button** 的核心

控制項已備妥，我們現在在 builder 目前位置 **insert command button** 到文件中。你可以在呼叫此方法前將 builder 移動到任意位置（例如段落之後）。

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

如果你需要 **how to insert button** 到特定書籤，只需先將 builder 移動即可：

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **What happens behind the scenes?** Aspose.Words 會將必要的 OLE 物件串流寫入 .docx 套件，讓 Word 能在不需要額外巨集的情況下呈現按鈕。

## 步驟 4：儲存文件 – 完成 **Create Word Document** 流程

最後一步相當簡單：將檔案寫入磁碟。這樣就完成了 **create word document**、嵌入 ActiveX 並儲存的完整流程。

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

在 Microsoft Word（僅限 Windows）中開啟產生的檔案。你應該會看到一個標示為「Click Me」的可點擊按鈕。點擊它會觸發 CommandButton 的預設動作——除非你附加 VBA 程式碼，否則不會有任何反應，但控制項已完整可用。

> **Expected output:** 一個單頁的 .docx 檔案，按鈕位於插入點置中，尺寸為 120 × 30 pt，標題為「Click Me」。  
> ![ActiveX button inserted into a Word document](placeholder-image.png)  
> *Image alt text:* **ActiveX button inserted into a Word document using C#** (matches `og_image_alt`).

## 步驟 5：邊緣案例、安全性與最佳實踐

### 平台限制
- ActiveX 控制項僅能在 Windows 版的 Word 上執行。若讀者使用 macOS 或 Word Online，按鈕將顯示為靜態圖片。  
- 某些企業環境會因安全考量停用 ActiveX；你可能需要為文件簽章或告知使用者啟用內容。

### VBA 互動（可選）
如果你想讓按鈕執行巨集，必須在儲存後為文件加入 VBA 專案。Aspose.Words 不會自動產生 VBA 程式碼，但你可以使用 `Document.VbaProject` API 進行注入。

### 命名衝突
務必為每個控制項指定唯一的 `Name`。重複使用相同名稱可能導致 Word 在解析控制項時發生執行時錯誤。

### 效能提示
插入大量控制項時，請重複使用同一個 `DocumentBuilder` 實例，並避免在迴圈內呼叫 `doc.Save`。將插入動作批次處理，最後一次儲存即可。

## 完整範例程式

將所有步驟整合起來，以下是一個完整、可直接複製貼上的程式範例：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

執行程式，開啟已儲存的檔案，你會看到按鈕正好位於 builder 所在的位置。

## 結論

我們剛剛從頭 **created word document**，透過設定 `Forms2OleControl` 學會了 **how to add activex**，掌握了 **set button size** 屬性，並示範了在文件任意位置正確使用 **insert command button** 與 **how to insert button** 的方法。  

從這個單一程式碼範例，你現在擁有了打造更豐富 Word 自動化的堅實基礎——無論是建立含互動表單的範本、產生需要使用者確認的合約，或只是於報告中點綴幾個實用的控制項。

### 接下來可以做什麼？

- **Style the button** – 更改字型、顏色，或加入圖片背景。  
- **Attach VBA macros** – 讓按鈕執行計算或啟動外部程式。  
- **Combine with other controls** – 結合核取方塊、清單方塊，甚至嵌入 Excel 工作表。  

隨意嘗試，如果遇到問題，歡迎在下方留言。祝編程愉快，盡情使用 Aspose.Words 自動化 Word！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎延伸。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [使用 Aspose.Words for .NET 建立 Word 文件](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [使用 Aspose.Words for .NET 在 Word 文件中建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words 在 Word 文件中插入行內圖片](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}