---
category: general
date: 2026-08-14
description: 使用 Aspose.Words 在 Word 文件中加入 ActiveX 按鈕 – 學習如何建立空白 Word 文件並以程式方式插入 ActiveX
  按鈕。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: zh-hant
lastmod: 2026-08-14
og_description: 如何使用 Aspose.Words 在 Word 文件中加入 ActiveX 按鈕。本教學示範如何建立空白 Word 文件、插入 ActiveX
  按鈕，並儲存結果。
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: 如何在 Word 中加入 ActiveX 按鈕 – Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: 如何使用 Aspose.Words 在 Word 文件中加入 ActiveX 按鈕
url: /zh-hant/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 Aspose.Words 添加 ActiveX 按鈕

如果您需要在產生的 Word 檔案中 **how to add ActiveX** 控制項，本指南將向您展示完整步驟。您將學會以程式方式 **insert ActiveX button**，從 **create empty Word document** 開始，最終得到可在 Microsoft Word 中開啟的已儲存檔案。

在自動化報表產生器、表單範本或互動合約中，加入執行 VBA 程式碼或觸發巨集的按鈕是常見需求。使用 Aspose.Words for .NET 可在不啟動 Office 的情況下建立文件，讓流程快速且適合伺服器環境。

## 前置條件

* 已安裝 .NET 6.0（或更新）SDK。
* 已安裝 Visual Studio 2022 或任何相容 C# 的 IDE。
* Aspose.Words for .NET NuGet 套件（`Aspose.Words` 版本 24.9 或更新）。  
  使用以下方式安裝：
  ```bash
  dotnet add package Aspose.Words
  ```
* 若要測試 ActiveX 按鈕，需在 Windows 環境下執行，因為 ActiveX 控制項需要 Windows 版的 Microsoft Word。

## 步驟 1：建立空白 Word 文件

第一個任務是於記憶體中 **create empty Word document**。Aspose.Words 提供 `Document` 類別以完成此目的。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` 代表整個 .docx 檔案。此時文件尚未有任何頁面，但您可以立即開始加入內容。

## 步驟 2：初始化 DocumentBuilder

`DocumentBuilder` 是協助工具，可讓您在文件中插入文字、影像及其他物件。它作用於您剛建立的 `Document` 實例。

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

建構器會維持游標位置；在此行之後插入的任何內容都會出現在第一頁的開頭。

## 步驟 3：插入 ActiveX CommandButton 控制項

Aspose.Words 提供 `InsertForms2OleControl` 方法，以加入舊版表單控制項，包括 ActiveX。此方法需要指定控制項類型及其以點 (points) 為單位的大小。

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

回傳的 `Forms2OleControl` 物件允許您設定屬性，例如控制項的名稱與標題。

## 步驟 4：設定按鈕屬性

設定有意義的 `Name` 可讓您之後在 VBA 程式碼中引用該控制項。`Caption` 則是使用者在按鈕上看到的文字。

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **專業提示：** 請保持名稱簡短且僅使用英數字元；Word 會拒絕包含空格或特殊字元的名稱。

## 步驟 5：儲存文件

最後，將文件寫入磁碟。使用 `.docx` 副檔名以保存現代 Word 檔案；ActiveX 按鈕在 `.doc` 檔案中同樣可用，但 `.docx` 為新專案的首選格式。

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

當您在 Microsoft Word 中開啟 `ActiveXButton.docx` 時，會看到一個可點擊的 **Submit** 按鈕。若啟用巨集，您可將 VBA 程式碼附加至 `btnSubmit_Click`，讓使用者點擊按鈕時執行。

## 完整、可執行範例

將所有步驟組合起來，即可得到一個可自行複製、貼上與執行的完整程式。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**預期輸出** – 執行程式後，主控台會顯示儲存位置；在 Word 中開啟產生的檔案時，會看到位於第一頁頂部、標示為 **Submit** 的按鈕。

## 處理常見問題與邊緣情況

### 按鈕能在所有 Word 版本中運作嗎？

ActiveX 控制項僅在 Windows 桌面版的 Word 中受支援。它們不會在 Word Online、macOS 版 Word 或行動裝置客戶端中呈現。若需跨平台互動，建議改用內容控制項或基於 HTML 的解決方案。

### 如果需要不同的大小或位置該怎麼辦？

`InsertForms2OleControl` 會將控制項放置於目前建構器的游標位置。若要移動它，可在插入前使用 `builder.MoveTo` 調整游標，或在建立後修改控制項的 `Left` 與 `Top` 屬性：

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### 我可以加入其他類型的 ActiveX 嗎？

可以。`Forms2OleControlType` 列舉包含 `CheckBox`、`OptionButton`、`ListBox` 等。將 `CommandButton` 替換為所需的列舉值，並相應調整屬性即可。

### 按鈕需要巨集才能執行動作嗎？

按鈕本身不會執行任何動作，除非您附加 VBA 程式碼。在 Word 中，按 **Alt+F11** 開啟 VBA 編輯器，找到 `btnSubmit_Click` 並撰寫所需的邏輯。若使用 **SaveFormat.Doc**（舊版 `.doc`）格式，產生的文件會保留 VBA 專案；但 `.docx` 檔案無法儲存 VBA 巨集。如需內嵌 VBA，請使用 `.doc` 格式。

## 結論

現在您已了解如何使用 Aspose.Words 在 Word 檔案中 **how to add ActiveX** 控制項。依循 **create empty Word document**、初始化 `DocumentBuilder`、**insert ActiveX button**、設定屬性並儲存檔案的步驟，即可直接從 .NET 程式碼產生互動式 Word 範本。

接下來，您可以探索相關主題，例如 **insert ActiveX button** 事件處理、加入 **create word document aspose** 以建立表格或影像，以及為企業部署保護含巨集的文件。嘗試不同的控制項類型與版面配置，以符合應用程式的使用者體驗需求。

祝開發順利！

## 接下來該學什麼？

以下教學涵蓋與本指南技術緊密相關的主題。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [使用 Aspose.Words 建立含頁首與頁尾的 Word 文件](/words/english/net/header-footer-formatting/create-header-footer/)
- [使用 Aspose.Words for .NET 在 Word 文件中建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words 建立含表格的 Word 文件](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}