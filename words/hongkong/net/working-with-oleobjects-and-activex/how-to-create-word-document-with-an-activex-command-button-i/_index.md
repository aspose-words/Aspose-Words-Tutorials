---
category: general
date: 2026-09-05
description: 使用 Aspose.Words C# 建立 Word 文件，並學習如何插入 ActiveX 命令按鈕、設定按鈕大小以及加入互動按鈕功能。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: zh-hant
lastmod: 2026-09-05
og_description: 在 C# 中建立 Word 文件並插入 ActiveX 命令按鈕。本教學示範如何設定按鈕大小及加入互動功能。
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: 使用 C# 建立含 ActiveX 命令按鈕的 Word 文件 – 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: 如何在 C# 中建立帶有 ActiveX 命令按鈕的 Word 文件
url: /zh-hant/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用 ActiveX 命令按鈕建立 Word 文件

如果您需要以程式方式 **建立 Word 文件** 並嵌入可點擊的 UI 元素，本指南將逐步說明。使用 Aspose.Words for .NET，您可以 **建立 Word 文件**、**新增命令按鈕**，並控制其外觀——全部不需開啟 Microsoft Word。

您將學會 **如何插入 ActiveX** 控制項、**設定按鈕大小**，以及讓按鈕如同互動式 UI 元件般運作。無需事先具備 COM 或 VBA 經驗；只要有 .NET 開發環境與 Aspose.Words 函式庫即可。

## 您將達成的目標

完成本教學後，您將能：

* **使用 C# 從頭建立 Word 文件**。
* **插入 ActiveX 命令按鈕**（經典的「Click Me」控制項）。
* **精確設定按鈕大小** 與位置。
* 可選地加入簡單的 **互動按鈕** 邏輯（例如宏佔位符）。
* 將檔案儲存為 `.docx`，可在 Microsoft Word 或任何相容檢視器中開啟。

### 前置條件

| 需求 | 原因 |
|-------------|--------|
| .NET 6.0 或更新版本 | 提供執行 C# 程式碼的執行環境。 |
| Aspose.Words for .NET（最新版本） | 提供範例中使用的 `Document`、`DocumentBuilder` 與 `Forms2OleControl` API。 |
| Visual Studio 2022（或任何 C# IDE） | 讓編譯與執行範例變得簡單。 |
| 基本的 C# 知識 | 需要了解程式流程。 |

> **專業提示：** 若您使用 Aspose.Words 試用版，請務必在執行程式碼前設定授權，以避免出現評估浮水印。

## 如何建立 Word 文件 – 整體工作流程

此流程分為四個邏輯步驟：

1. **初始化新文件** 並建立 `DocumentBuilder` 以編輯它。  
2. **使用 `InsertForms2OleControl` 插入 ActiveX 命令按鈕**。  
3. **設定按鈕**——標題、大小與位置。  
4. **儲存** 文件至磁碟。

每個步驟在下方各自說明。

![包含 ActiveX 按鈕的 Word 文件](/images/activex-button.png "使用 C# 建立的、包含 ActiveX 命令按鈕的 Word 文件螢幕截圖")

## 如何插入 ActiveX 命令按鈕

**插入 ActiveX** 部分從 `InsertForms2OleControl` 方法開始。此方法會建立一個 COM 為基礎的控制項，Word 會將其視為 ActiveX 物件。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**為什麼這樣可行：** `OleControlType.CommandButton` 告訴 Aspose.Words 建立經典的 VB 風格按鈕。大小與位置以點 (point) 為單位表示 (1 點 = 1/72 英吋)，可精確控制版面配置。

## 如何新增命令按鈕並設定按鈕大小

控制項插入後，您可以調整其視覺屬性。**新增命令按鈕** 步驟同時說明 **設定按鈕大小**。

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**說明：**  

* `Caption` 為顯示在按鈕上的文字標籤。  
* `Width` 與 `Height` 讓您在首次插入後 **設定按鈕大小**——當大小取決於執行時資料時很有用。  
* `Left` 與 `Top` 重新定位控制項，無需重新建立文件。

> **常見陷阱：** 若忘記使用點而非像素，按鈕會顯示過小或過大。若以螢幕測量值為基礎，請務必將像素值換算為點 (`px * 72 / DPI`)。

## 如何新增互動按鈕（可選）

ActiveX 按鈕在點擊時可以執行宏，但從 C# 嵌入 VBA 程式碼超出純 Aspose.Words 工作流程的範疇。相反地，您可以加入一個佔位屬性，讓 Word 辨識為宏名稱。

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

當使用者在 Word 中開啟產生的 `.docx` 時，點擊按鈕會嘗試執行 `MyMacroName`。若該宏不存在，Word 會提示使用者建立它。

**為什麼會使用此方式：** 在企業表單中，若宏負責填寫欄位，C# 程式碼只需放置按鈕；宏的邏輯則存於文件的 VBA 專案中。

## 儲存文件並驗證結果

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**預期輸出：** 在 Microsoft Word 中開啟 `CommandButton.docx` 時，會看到一個標示為 **Click Me** 的按鈕，距左邊距 100 點、距上邊距 120 點。按鈕尺寸為 **200 點 × 80 點**。點擊按鈕會觸發宏佔位符（若有設定）。

## 完整範例程式

以下是完整、可執行的程式碼，將所有步驟整合。將它複製到新的 Console App 專案中，加入 Aspose.Words NuGet 套件，然後執行。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

執行程式後，開啟產生的檔案。您會看到 **互動按鈕** 已就緒，可進一步自訂。

## 常見問題

| 問題 | 答案 |
|----------|--------|
| **這能在 .NET Core 上運作嗎？** | 可以。Aspose.Words 支援 .NET Standard，故相同程式碼可在 .NET 5/6/7 上執行。 |
| **我可以使用其他 ActiveX 控制項（例如 CheckBox）嗎？** | 當然可以。將 `OleControlType.CommandButton` 替換為 `OleControlType.CheckBox`、`OleControlType.OptionButton` 等即可。 |
| **如果在橫向頁面上需要更大的按鈕該怎麼辦？** | 按比例調整 `Width`、`Height`、`Left` 與 `Top` 屬性。請記得點數在不同頁面方向下皆相同。 |
| **按鈕要可點擊是否必須有宏？** | 不需要。按鈕作為 UI 元素已可正常運作；宏僅在點擊時提供自訂行為。 |

## 結論

現在您已了解如何使用 Aspose.Words **建立 Word 文件**、**新增命令按鈕**、**設定按鈕大小**，以及可選地將按鈕連結至宏以實現 **互動按鈕** 行為。此方法可讓您自動化表單建立、產生動態報告，或直接從 C# 建構基於 Word 的 UI 原型。

接下來您可能想探索：

* **如何插入 ActiveX 核取方塊** 以用於調查表單。  
* **如何使用 `DocumentBuilder` 在按鈕周圍加入富文字內容**。  
* **如何保護文件** 同時保持按鈕功能。  

歡迎嘗試不同的控制項類型、尺寸與宏名稱，以符合您的具體情境。祝開發愉快！

## 接下來您應該學習什麼？

以下教學涵蓋與本指南技術密切相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [使用 Aspose.Words for .NET 建立 Word 文件](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [使用 Aspose.Words 在 Word 文件中插入行內圖片](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [使用 Aspose.Words 建立含表格的 Word 文件](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}