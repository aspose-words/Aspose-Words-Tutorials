---
category: general
date: 2026-08-07
description: 學習如何使用 C# 在 Word 文件中加入 ActiveX 控制項。內容包括將巨集與按鈕關聯以及新增可點擊的按鈕範例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: zh-hant
lastmod: 2026-08-07
og_description: 如何使用 Aspose.Words 在 Word 文件中加入 ActiveX 控制項。請參考本指南，插入按鈕、將巨集與按鈕關聯，並新增可點擊的按鈕文字。
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: 如何在 Word 中加入 ActiveX 控制項 – 完整 C# 教學
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 Aspose.Words 在 Word 中加入 ActiveX 控制項 – 步驟指南
url: /zh-hant/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 Aspose.Words 添加 ActiveX 控制項

如果您需要以程式方式在 Microsoft Word 檔案中 **how to add activex control**，本教學將示範使用 Aspose.Words for .NET 的完整步驟。您將看到如何插入指令按鈕、設定其標題，並 **associate macro with button**，讓控制項在使用者點擊時產生反應。完成後，您將擁有一個含有完整功能按鈕的巨集啟用 `.docm` 檔案。

在建立互動式範本（例如貸款申請、員工入職表單或自動化報告）時，加入 ActiveX 按鈕是常見需求。本指南會逐行說明程式碼，解釋 **why** 每一步的重要性，並說明可能遇到的常見陷阱。

## 前置條件

在開始之前，請確保您已具備：

* 已安裝 .NET 6（或 .NET Core 3.1 / .NET Framework 4.8）。
* 有效的 Aspose.Words for .NET 授權或臨時評估金鑰。
* Visual Studio 2022（或任何支援 C# 的 IDE）。
* 基本的 Word 巨集（VBA）知識，若您打算編寫按鈕觸發的巨集。

> **Pro tip:** 執行範例時，請將輸出儲存至您具有寫入權限的資料夾，否則 `doc.Save` 會拋出例外。

## 如何使用 Aspose.Words 在 Word 文件中加入 ActiveX 控制項

此解決方案的核心是一段簡短的 C# 程式，會建立新文件、插入 ActiveX **CommandButton** 控制項，並將檔案儲存為巨集啟用文件（`.docm`）。程式碼完整，可直接複製貼上使用。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### 為何每一行都很重要

| 行號 | 目的 |
|------|------|
| `Document doc = new Document();` | 在記憶體中建立一個全新的 Word 套件實例。 |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | 提供流暢的 API 用於插入內容，包括 ActiveX 控制項。 |
| `InsertForms2OleControl` | 唯一的 Aspose.Words 方法可建立 ActiveX 控制項；您需要指定控制項類型（`CommandButton`）及其幾何尺寸。 |
| `commandButton.Caption = "Click Me";` | 設定最終使用者看到的 **add clickable button word**。若未設定標題，按鈕將顯示為空白。 |
| `commandButton.OnAction = "MyMacro";` | **associate macro with button** – 告訴 Word 在控制項被點擊時執行哪個 VBA 巨集。 |
| `doc.Save("CommandButton.docm");` | 將文件保存為巨集啟用檔案；若使用一般的 `.docx` 會移除控制項與巨集。 |

> **Note:** 座標（左、上）以點為單位測量 (1 pt ≈ 1/72 in)。請調整它們以將按鈕放置在頁面所需位置。

## 如何將巨集關聯至按鈕

`OnAction` 屬性會將按鈕連結至名為 `MyMacro` 的 VBA 巨集。您仍需在 Word 檔案內建立該巨集，無論是手動新增或以程式方式注入 VBA 程式碼（Aspose.Words 不會寫入 VBA 程式碼）。以下是一段可在 Word 的 **Developer → Visual Basic** 編輯器中加入的最小巨集範例：

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

當使用者開啟 `CommandButton.docm` 並點擊按鈕時，Word 會執行 `MyMacro` 並顯示訊息方塊。若巨集安全性設定為 **Disable all macros without notification**，按鈕將顯示為停用狀態。請建議使用者為此文件啟用巨集，或使用受信任的憑證簽署巨集。

### 關聯巨集時的常見陷阱

* **Macro security settings** – 若文件在安全政策嚴格的機器上開啟，巨集可能會被阻擋。請提供降低安全等級或簽署巨集的說明。
* **Naming conflicts** – 巨集名稱必須在文件的 VBA 專案中唯一，否則 Word 會拋出「duplicate procedure name」錯誤。
* **64‑bit vs 32‑bit Word** – ActiveX 控制項的功能相同，但 VBA 編輯器可能根據 Office 版本顯示不同的警告訊息。

## 如何在 Word 表單中加入可點擊的按鈕文字

`Caption` 屬性即使用者在按鈕上看到的文字。您可以進一步自訂它：

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

若需根據使用者輸入動態變更標題，可稍後透過 Word 物件模型存取該控制項：

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### 邊緣情況：長標題

Word 會截斷超出按鈕寬度的標題。為避免裁切，請在 `InsertForms2OleControl` 中增大寬度參數或縮短文字。建議使用不同語系（例如德文或日文）測試，因為字元寬度會有所差異。

## 如何為表單自動化加入指令按鈕文字

除了視覺上的標題外，**add command button word** 概念還涵蓋控制項的程式名稱。Aspose.Words 並未公開直接的 `Name` 屬性給 ActiveX 控制項，但您可以設定 `AltText` 欄位，Word 會將其視為控制項的識別碼：

```csharp
commandButton.AltText = "SubmitButton";
```

之後在 VBA 中，您可以透過其 `AltText` 值來引用該按鈕：

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

此技巧在您有多個按鈕且需要以程式方式區分它們時非常有用。

## 完整可執行範例

以下是完整程式碼，您可以將其編譯為主控台應用程式並執行。程式碼包含可選的樣式設定、巨集關聯，以及說明每一步的註解區塊。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Expected result:** 開啟 `SubmitForm.docm` 後，Microsoft Word 會顯示一個藍色邊框、標示為 *Submit Form* 的按鈕。點擊該按鈕會觸發 VBA 巨集 `SubmitMacro`（前提是您已將巨集加入文件）。此按鈕可使用相同的 `Forms2OleControl` 物件進一步移動、調整大小或套用樣式。

## 測試解決方案

1. 建置並執行 C# 主控台應用程式。  
2. 在 Word 中開啟產生的 `SubmitForm.docm`。  
3. 若出現提示，請啟用巨集。  
4. 點擊 *Submit Form* 按鈕 – 您應會看到 `SubmitMacro` 中定義的訊息方塊。

如果按鈕出現但沒有任何反應，請再次確認巨集名稱完全相同（`SubmitMacro`），且巨集安全性未阻止執行。

## 常見問題

| 問題 | 答案 |
|------|------|
| *我可以加入超過一個 ActiveX 按鈕嗎？* | 可以。多次呼叫 `InsertForms2OleControl` 並使用不同座標。使用不同的 `OnAction` 與 `AltText` 值以區分它們。 |
| *ActiveX 控制項在 Word Online 中可見嗎？* | 不行。 |

## 接下來該學什麼？

以下教學與本指南所示技術密切相關，能幫助您進一步掌握 API 功能並探索其他實作方式：

- [使用 Document Builder 新增內容於 Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words Shape Shadow 教學 – 在 C# 中為 Word Shape 加入陰影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [為 Word 文件新增章節 | Aspose.Words for .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}