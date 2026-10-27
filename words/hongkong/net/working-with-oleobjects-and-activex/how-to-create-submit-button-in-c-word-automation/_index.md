---
category: general
date: 2026-08-23
description: 在 C# Word 自動化中建立提交按鈕。學習如何以程式方式加入 ActiveX 按鈕，設定按鈕名稱、標題及文字。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: zh-hant
lastmod: 2026-08-23
og_description: 在 C# Word 自動化中建立提交按鈕。本指南說明如何使用 Aspose.Words 新增 ActiveX 按鈕，並設定其名稱、標題與文字。
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: 在 C# Word 自動化中建立提交按鈕
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: 如何在 C# Word 自動化中建立送出按鈕
url: /zh-hant/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# Word 自動化中建立提交按鈕

如果您需要在使用 C# 的 Word 文件中 **create submit button**，本指南將帶您完成整個流程。您將會看到如何加入 ActiveX 按鈕、指派程式化名稱，並設定按鈕標題，使其看起來像一般的 *Submit* 控制項。

自動化 Word 中的表單控制項可以取代手動排版工作，並確保數百份文件的一致性。以下步驟中，您還會學習如何 **set button text**、**set button name** 以及 **set button caption**——這些在按鈕參與宏驅動工作流程時都是必須的。

## 前置條件

* 已安裝 .NET 6.0（或更新版本）。
* 參考 **Aspose.Words for .NET**（提供 `DocumentBuilder.InsertForms2OleControl` 的函式庫）。
* 具備 C# 與 Word ActiveX 表單控制項的基本知識。

您可以透過 NuGet 安裝 Aspose.Words：

```bash
dotnet add package Aspose.Words
```

> **專業提示：** 使用最新的穩定版 Aspose.Words，以獲得錯誤修正與與 ActiveX 控制項相關的新功能。

## 解決方案概覽

本教學分為三個清晰的步驟：

1. **Add ActiveX button** – 使用 `InsertForms2OleControl` 方法在文件中放置指令按鈕。  
2. **Set button name** – 以 `Name` 屬性指派唯一的程式化識別碼。  
3. **Set button caption** – 透過 `Caption` 屬性定義按鈕上可見的文字（同時控制您在 UI 中看到的 **set button text**）。

完成本指南後，您將擁有一個完整可用的 **create submit button** 程式，能在任何 Word 自動化專案中重複使用。

## 步驟 1：在文件中加入 ActiveX 按鈕

第一個任務是 **add activex button** 到 Word 檔案中。Aspose.Words 為此提供了 `Forms2OleControlType.CommandButton` 列舉。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**此步驟的重要性：**  
ActiveX 控制項是唯一能執行 VBA 巨集或與外部程式碼互動的 Word 表單元素。加入控制項會建立一個占位符，供後續步驟進行設定。

> **特殊情況：** 若文件已包含同名的控制項，Word 會自動重新命名新控制項（例如 `CommandButton1`）。在下一步明確設定名稱即可避免此類衝突。

## 步驟 2：設定按鈕名稱

可靠的 **set button name** 在需要從 VBA 或 C# 程式碼的其他部分引用控制項時至關重要。`Name` 屬性為按鈕提供程式化的識別碼。

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**為何需要設定名稱：**  
文件開啟時，VBA 可透過 `ActiveDocument.InlineShapes("btnSubmit")` 取得按鈕。像 `btnSubmit` 這樣具意義的名稱在檢查文件 XML 時也能說明用途。

> **專業提示：** 保持名稱簡短、僅使用英數字，且以字母開頭，以符合 VBA 命名規則。

## 步驟 3：設定按鈕標題（可見文字）

使用者在按鈕上看到的文字由 **set button caption** 屬性控制。在 Word UI 中，這會顯示為按鈕的標籤，也是您想要呈現的 **set button text**。

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**此標題的重要性：**  
標題是面向使用者的標籤。之後變更它不會影響按鈕名稱，因而可以在不破壞依賴 `btnSubmit` 的程式碼的情況下本地化 UI。

> **常見問題：** *我可以同時設定 Caption 與 Value 嗎？*  
> 對於 `CommandButton`，`Caption` 控制標籤，而 `Value` 不會被使用。若需要隱藏值，請改存於自訂文件屬性中。

## 完整範例

將上述三個步驟結合，即可得到一個完整的程式，您可以將其放入任何 Console 或 Windows 應用程式中：

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
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### 預期輸出

執行程式會產生 `SubmitButton.docx`。在 Microsoft Word 中開啟此檔案時：

* 會在指定位置出現一個 **Submit** 按鈕。
* 按鈕的名稱為 `btnSubmit`（可於 *Developer → Design Mode → Properties* 中檢查）。
* 在設計模式下點擊按鈕會顯示標題 *Submit*。

您現在擁有一個可重複使用的組件，可用於任何以表單為主的 Word 解決方案。

## 其他考量

### 處理名稱衝突

若在同一文件上多次執行此程式，Word 可能會自動重新命名重複的控制項。為確保唯一性，您可以在名稱前加上 GUID：

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### 本地化按鈕標題

針對多語系文件，請將標題存於資源檔，並於執行時指派：

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### 回應按鈕點擊

按鈕本身在 C# 中不包含點擊邏輯。通常會附加 VBA 巨集：

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

因為您已將 **set button name** 設為 `btnSubmit`，巨集名稱會自動遵循 `<Name>_Click` 的慣例。

## 疑難排解 FAQ

| Question | Answer |
|----------|--------|
| **為何按鈕顯示為空白？** | 請確保已設定 `Caption` 屬性；若未設定，按鈕將不會顯示文字。 |
| **我可以使用其他 ActiveX 控制項嗎？** | 可以。將 `Forms2OleControlType.CommandButton` 替換為 `CheckBox`、`OptionButton` 等，但其屬性會有所不同。 |
| **這與 .NET Core 相容嗎？** | Aspose.Words for .NET 支援 .NET 6 以上版本，因此相同程式碼可在 .NET Core 與 .NET Framework 上執行。 |
| **如果文件已經有按鈕該怎麼辦？** | 使用唯一的 `Name`（例如在名稱後加上 GUID）以避免衝突。 |

## 結論

您現在已了解如何使用 C# 在 Word 文件中以程式方式 **create submit button**。遵循這三個步驟——**add activex button**、**set button name** 與 **set button caption**——即可可靠地 **set button text**、**set button name** 與 **set button caption**，用於任何自動化表單解決方案。  

接下來您可以探索：

* 加入回應 **submit button** 點擊的 VBA 巨集。
* 透過底層 XML 為按鈕套用自訂字型或顏色樣式。
* 在迴圈中產生多個按鈕，以支援動態表單。

歡迎自行嘗試不同的標題、名稱與位置，以符合您的工作流程。祝自動化順利！

## 接下來該學什麼？

以下教學涵蓋與本指南技術密切相關的主題，並在此基礎上延伸。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [使用 Aspose.Words for .NET 在 Word 文件中建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words for .NET 在 Word 中建立折線圖](/words/english/net/working-with-charts/create-chart-using-shape/)
- [使用 Aspose.Words 建立含頁首與頁尾的 Word 文件](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}