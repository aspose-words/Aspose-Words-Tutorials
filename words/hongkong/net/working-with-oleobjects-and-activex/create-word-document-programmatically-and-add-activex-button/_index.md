---
category: general
date: 2026-08-10
description: 使用 Aspose.Words 程式化建立 Word 文件，然後加入 ActiveX 控制項按鈕。只需幾分鐘即可插入 ActiveX 命令按鈕。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: zh-hant
lastmod: 2026-08-10
og_description: 使用 Aspose.Words 程式化建立 Word 文件，然後加入 ActiveX 控制項按鈕。了解如何快速插入 ActiveX
  命令按鈕。
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: 以程式方式建立 Word 文件 – 在 C# 中加入 ActiveX 按鈕
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: 以程式方式建立 Word 文件並加入 ActiveX 按鈕
url: /zh-hant/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 以程式方式建立 Word 文件並加入 ActiveX 按鈕

如果您需要 **以程式方式建立 Word 文件**，本指南將帶您完整了解使用 Aspose.Words for .NET 的流程。您亦會學習如何 **加入 ActiveX 控制項** 元素以及 **插入 ActiveX 指令按鈕** 物件，全部示範於單一自足範例中。

透過程式產生 Word 檔案可省去手動開啟 Microsoft Word 的步驟，讓您自動建立報告、發票或資料驅動的合約。完成本教學後，您將擁有一個可直接執行的 C# 主控台應用程式，產生包含互動式 ActiveX CommandButton 的 `.docx` 檔案。

## 前置條件

* .NET 6.0 SDK 或更新版本（此程式碼亦可於 .NET Framework 4.6+ 執行）
* Visual Studio 2022 或任何支援 .NET 開發的 IDE
* 有效的 Aspose.Words for .NET 授權（可使用免費評估金鑰進行測試）
* 具備 C# 語法的基本知識以及 COM/ActiveX 控制項的概念

> **專業提示：** 若您打算將產生的文件分發給未安裝 Word 的使用者，請將 ActiveX 控制項的執行時檔案與 `.docx` 一同嵌入，或提供啟用巨集的範本。

## 以程式方式建立 Word 文件 – 初始設定

首先，將 Aspose.Words NuGet 套件加入您的專案中：

```bash
dotnet add package Aspose.Words
```

接著建立一個新的主控台專案（若尚未有專案的話）：

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

開啟產生的 `Program.cs` 檔案 – 我們將把內容替換為以下完整解決方案。

## 步驟 1：匯入命名空間並設定授權

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*為何重要*：匯入 `Aspose.Words.Drawing` 可取得 `Forms2OleControl`，此類別代表 Word 文件中的 ActiveX 控制項。提前設定授權可避免正式環境的執行時警告。

## 步驟 2：建立空白文件與 DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 物件是 `.docx` 檔案的記憶體表示。`DocumentBuilder` 如同游標，可在文件中移動以插入各種元素。

## 步驟 3：插入 ActiveX CommandButton 控制項

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` 會建立 Word 視為 ActiveX 控制項的 OLE 物件。座標系統使用點 (1 point = 1/72 吋)，與 Word 的版面配置引擎相同。

## 步驟 4：設定按鈕的標題與可選屬性

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

設定 `Caption` 屬性是標示按鈕最常見的方式。若需按鈕執行 VBA 巨集，請將巨集名稱指派給 `OnAction`。本教學著重於視覺部分；巨集整合則於「後續步驟」說明。

## 步驟 5：儲存文件

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

執行程式後，您會在主控台看到訊息，確認 `ActiveX_CommandButton.docx` 已寫入磁碟。

### 完整原始碼（可直接複製貼上）

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

執行此程式碼片段會產生一個包含可點擊 **ActiveX command button** 的 Word 檔案。於 Microsoft Word 開啟該檔，切換至 **Design Mode**（開發人員索引標籤 → Design Mode），即可看到按鈕正確顯示在您放置的位置。

## 步驟 6：驗證結果

1. 在 Microsoft Word 中開啟 `ActiveX_CommandButton.docx`。
2. 若未顯示 **Developer** 索引標籤，請啟用它（`File → Options → Customize Ribbon → check Developer`）。
3. 點選 **Design Mode**。按鈕應顯示標籤「Submit」。
4. 若您已加入 `OnAction` 巨集，請在關閉 Design Mode 時點擊按鈕以觸發巨集。

若按鈕未顯示，請確認 Word 的安全性設定允許 ActiveX 控制項（`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`）。

## 常見問題與邊緣情況

| 問題 | 答案 |
|----------|--------|
| **我可以插入其他 ActiveX 類型嗎？** | 可以。`Forms2OleControlType` 列舉包含 `CheckBox`、`OptionButton`、`ComboBox` 等。將 `CommandButton` 替換為您想要的列舉值。 |

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，進一步延伸所示技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [使用 Aspose.Words for .NET 在 Word 文件中建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words 建立含頁首與頁尾的 Word 文件](/words/english/net/header-footer-formatting/create-header-footer/)
- [使用 Aspose.Words 在 Word 文件中插入行內圖片](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}