---
category: general
date: 2026-07-23
description: 使用 Aspose.Words 建立 Word 文件按鈕 – 步驟教學：將 ActiveX CommandButton 插入 .docx
  檔案。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: zh-hant
lastmod: 2026-07-23
og_description: 使用 Aspose.Words 建立 Word 檔案按鈕：快速學習如何在數分鐘內將 ActiveX 命令按鈕嵌入 Word 檔案。
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: 建立 Word 文件按鈕 – Aspose.Words 完整指南
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: 使用 Aspose.Words 建立 Word 文件按鈕 – 完整程式碼範例
url: /zh-hant/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words 建立 Word 文件按鈕 – 完整程式設計指南

是否曾經需要 **create word document button**，卻不確定該使用哪個 API？你並不孤單——大多數開發者在嘗試將互動控制項嵌入 .docx 檔案時都會卡關。好消息是？使用 Aspose.Words for .NET，你只需幾行程式碼就能在 Word 文件中插入一個完整功能的 ActiveX CommandButton。

在本教學中，我們將逐步說明整個流程：從設定專案、初始化 `DocumentBuilder`、使用 `InsertForms2OleControl` 插入按鈕，到最後儲存檔案讓 Word 能辨識此控制項。完成後，你將擁有一個可直接使用、內含可點擊按鈕的 Word 檔案——不需要任何 COM interop 的繁雜操作。

## 所需條件

- **.NET 6.0** 或更新版本（程式碼同樣支援 .NET Framework 4.6 以上）。  
- **Aspose.Words for .NET** NuGet 套件（版本 23.9 或更新）。  
- 具備基本的 C# 知識（我們會保持語法對初學者友好）。  
- Visual Studio 2022 或任何你偏好的 IDE。  

就這樣——不需要額外的 COM 參考、不需要 Office interop，僅使用純受管理的程式碼。

---

## 步驟 1：設定 Aspose.Words 以 **create word document button**

首先，將 Aspose.Words 套件加入你的專案：

```bash
dotnet add package Aspose.Words
```

或者，若你使用 Visual Studio NuGet UI，搜尋 “Aspose.Words” 並點選 **Install**。這一行指令即可讓你取得 `Document`、`DocumentBuilder` 以及稍後會用到的 `InsertForms2OleControl` 方法。

> **小技巧：** 請保持 NuGet 套件為最新版本；較新的發行版常會包含針對 ActiveX 處理的錯誤修正。

---

## 步驟 2：初始化 **DocumentBuilder** 以建立 **ActiveX CommandButton**

現在我們建立一個全新的 Word 文件，並啟動 `DocumentBuilder`。可以把 `DocumentBuilder` 想像成畫筆，讓你在畫布上繪製內容。

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

請注意我們匯入了 `System.Drawing`——`Rectangle` 結構用來定義按鈕的位置與大小。這就是 **ActiveX CommandButton** 所在的地方。

---

## 步驟 3：使用 **InsertForms2OleControl** 來 **add a CommandButton**

以下是本教學的核心：插入按鈕本身。`InsertForms2OleControl` 方法接受三個參數——控制項類型、一個 `Rectangle`，以及可選的名稱。我們將使用 `OleControlType.CommandButton` 來指定我們想要的控制項。

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

這一次呼叫會完成多項工作：

1. **Creates** 在 Word 檔案內建立 OLE 物件。  
2. **Registers** 將其註冊為 ActiveX CommandButton，Word 會將其呈現為可點擊的 UI 元件。  
3. **Positions** 依照我們提供的矩形定位它。  

如果需要變更按鈕的標題或其他屬性，可在插入後透過存取底層的 `OleFormat` 來調整。對於大多數情況，預設標題（“CommandButton1”）已足夠。

---

## 步驟 4：儲存包含 **CommandButton** 的 Word 文件

儲存相當簡單——只要指向一個你有寫入權限的資料夾。檔案副檔名必須為 `.docx`，才能讓按鈕在往返過程中保留下來。

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

當你在 Microsoft Word 中開啟 `CommandButton.docx` 時，會在首頁左上角看到一個小按鈕。直接點擊它不會有任何動作（那需要 VBA），但此控制項已完整功能，之後可再加以連接。

> **為什麼這樣可行：** Aspose.Words 直接將 OLE 串流寫入 DOCX 套件，省去 Word 在執行時產生控制項的需求。這確保按鈕會精確出現在你放置的位置。

---

## 步驟 5：在 Word 中驗證按鈕

開啟產生的檔案：

1. 啟動 Microsoft Word。  
2. 前往 **File → Open** 並選取 `CommandButton.docx`。  
3. 你應該會看到一個標示為 “CommandButton1” 的矩形按鈕。  

若未看到按鈕，請確認已啟用 **Design Mode**（開發人員 → Design Mode）。此模式會切換 ActiveX 控制項的視覺呈現。

---

## 步驟 6：進階選項 – 自訂 **ActiveX CommandButton**

以下提供幾個快速調整，可能對你有幫助：

| 目標 | 程式碼片段 |
|------|--------------|
| 變更標題 | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| 設定巨集名稱（需要 Word 巨集支援） | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| 插入後調整大小 | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

這些程式碼片段展示了 `InsertForms2OleControl` 的彈性。你甚至可以透過切換 `OleControlType` 列舉，嵌入其他 ActiveX 控制項，例如 `CheckBox` 或 `ListBox`。

---

## 完整範例程式

以下是完整、可直接複製貼上的程式，從頭開始 **creates a word document button**：

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**執行程式後的預期輸出：**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

開啟產生的檔案，你會看到按鈕正好位於程式碼指定的位置。

---

## 常見陷阱與避免方法

- **Missing `System.Drawing` reference** – `Rectangle` 結構位於該命名空間；若缺少會導致編譯器報錯。  
- **Using an older Aspose.Words version** – 早期版本未完整支援 `InsertForms2OleControl`。請升級至最新穩定版套件。  
- **Saving as `.doc` instead of `.docx`** – 舊的二進位格式會剝除 OLE 串流，導致按鈕消失。  
- **Running on a headless server without Word installed** – 按鈕仍會寫入檔案，但若未安裝 Word 則無法預覽。對於自動化產生流程而言這是可以接受的。

---

## 後續步驟 – 擴充 **create word document button** 工作流程

既然你已掌握基礎，請考慮以下進階想法：

- **Attach VBA macros**：為按鈕附加 VBA 巨集以實現自訂業務邏輯。  
- **Generate multiple buttons**：在迴圈中產生多個按鈕以建立動態表單。  
- **Combine with Aspose.PDF**：將相同文件匯出為 PDF，同時保留視覺版面（按鈕在 PDF 中會變成靜態影像）。  
- **

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [使用 Aspose.Words for .NET 建立 Word 文件](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [使用 Aspose.Words 在 Word 中建立矩形形狀 – 步驟教學](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [使用 Aspose.Words 在 Word 文件中插入內嵌圖片](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}