---
category: general
date: 2026-09-21
description: 學習如何使用 Aspose.Words 及 C# 在 Word 文件中建立 ActiveX 命令按鈕。一步步指南涵蓋插入、定位及儲存。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: zh-hant
lastmod: 2026-09-21
og_description: 使用 C# 與 Aspose.Words 在 Word 文件中建立 ActiveX 指令按鈕。遵循本完整教學，程式化地插入、定位及儲存按鈕。
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: 使用 C# 在 Word 中建立 ActiveX 指令按鈕 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: 如何使用 C# 在 Word 中建立 ActiveX 指令按鈕
url: /zh-hant/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 在 Word 中建立 ActiveX 命令按鈕

如果您需要在 Word 檔案中 **建立 ActiveX 命令按鈕**，本指南會向您展示完整步驟。使用 Aspose.Words for .NET，您可以完全透過 C# 程式碼新增、定位與設定按鈕。

以程式方式插入 ActiveX 按鈕可省去手動 UI 操作，並能自動產生表單、報告或互動範本等文件。在本教學中，您將學會使用 **DocumentBuilder**、**InsertForms2OleControl** 方法以及相關屬性，打造功能完整的按鈕。

## 需要的環境

在開始之前，請確保您已具備：

* .NET 6.0 SDK 或更新版本（程式碼亦相容 .NET Framework 4.7 以上）
* Aspose.Words for .NET（NuGet 套件 `Aspose.Words`）
* 如 Visual Studio 2022 或 VS Code 等 IDE
* 基本的 C# 與 Word 文件概念

不需要額外安裝 Office，因為 Aspose.Words 可獨立於 Microsoft Word 運作。

## Step 1: 設定 C# 專案

建立一個新的主控台專案，並加入 Aspose.Words 套件。

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

`Aspose.Words` 函式庫提供 **DocumentBuilder** 類別，我們將使用它來操作文件。

## Step 2: 初始化文件與 Builder

第一段程式碼會建立空白文件與 `DocumentBuilder` 實例。此物件是所有 Word 處理操作的入口點。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**為什麼重要：** `DocumentBuilder` 會保留目前的游標位置，因此之後的任何插入都會精確出現在您設定的游標位置。

## Step 3: 插入 ActiveX 命令按鈕

**InsertForms2OleControl** 方法會建立指定類型的 ActiveX 控制項。此處我們要求建立 `CommandButton`，並以點 (pt) 為單位指定尺寸 (200 × 30 pt)。

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**說明：**  
* `OleControlType.CommandButton` 告訴 Aspose.Words 建立按鈕，而非其他控制項。  
* 此方法會回傳 `Forms2OleControl` 物件，提供定位與屬性欄位。

## Step 4: 定位按鈕並設定屬性

插入後，您可以將按鈕移動到頁面上的任意位置，並為其設定程式名稱與可見的標題。

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**小技巧：** 座標系統的原點位於頁面的左上角。調整 `Left` 與 `Top` 即可使按鈕與其他表單欄位對齊。

## Step 5: 儲存文件

最後，將文件寫入磁碟。檔案將包含 ActiveX 按鈕，開啟於 Microsoft Word 時即可互動。

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

當您在 Word 中開啟 `ActiveXCommandButton.docx`，會看到一個標示為 **Submit** 的按鈕出現在指定位置。點擊該按鈕會觸發預設的命令按鈕行為（您日後可透過 VBA 或 Word 外掛自訂）。

## 完整、可執行的範例

將所有程式碼組合起來，即可得到一個可直接複製、貼上並執行的自包含程式。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**預期輸出：** 主控台會印出 *“Document created successfully.”*，且資料夾中會出現 `ActiveXCommandButton.docx`。在 Microsoft Word 開啟該檔案時，會看到一個可點擊的 **Submit** 按鈕，左邊距離 100 pt、上邊距離 150 pt。

## 常見問題與避免方式

| 問題 | 為什麼會發生 | 解決方式 |
|------|--------------|----------|
| 按鈕出現在頁面外 | `Left`/`Top` 數值超過頁面尺寸 | 使用 `doc.FirstSection.PageSetup.PageWidth` 與 `PageHeight` 來計算安全座標 |
| 按鈕在 Word 中不可見 | 文件被儲存為會剝除 ActiveX 控制項的格式（例如 `.txt`） | 請始終儲存為 `.docx` 或 `.doc` |
| 執行時錯誤 `ArgumentOutOfRangeException` | 寬度或高度設定為零或負值 | 確保傳遞給 `InsertForms2OleControl` 的尺寸參數為正數 |

## 擴充解決方案

您可以透過設定 `Enabled`、`Visible` 等額外屬性，或以 VBA 附加巨集，進一步自訂按鈕。**Forms2OleControl** 類別同時支援插入其他 ActiveX 控制項，例如核取方塊 (`OleControlType.CheckBox`) 或下拉式方塊 (`OleControlType.ComboBox`)。

若需在迴圈中產生多個按鈕，可將插入邏輯封裝於輔助方法中：

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## 結論

現在您已掌握如何使用 C# 與 Aspose.Words 在 Word 文件中 **建立 ActiveX 命令按鈕**。本教學說明了專案設定、使用 `InsertForms2OleControl` 插入按鈕、定位以及儲存最終檔案的完整流程。憑藉此基礎，您可以自動化複雜表單、嵌入互動控制項，並將 Word 文件整合至更大的 .NET 解決方案中。

接下來，您可以探索相關主題，例如 **Aspose.Words ActiveX** 表單欄位、**C# DocumentBuilder** 進階樣式，或以程式方式在 Word 中加入核取方塊與下拉式清單的 **ActiveX control**。嘗試不同的座標與尺寸，以符合您的版面需求。祝開發順利！

## 您接下來可以學習什麼？

以下教學與本指南所示技巧密切相關，能協助您進一步掌握 API 功能並探索其他實作方式：

- [使用 Aspose.Words for .NET 建立 Word 文件](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [使用 Aspose.Words 在 Word 中建立矩形形狀 – 步驟指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [使用 Aspose.Words 建立含表格的 Word 文件](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}