---
category: general
date: 2026-07-29
description: 使用 Aspose.Words 在 Word 文件中新增指令按鈕。學習如何設定 ActiveX 控制項屬性以及設定指令按鈕的標題，只需簡單幾步。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: zh-hant
lastmod: 2026-07-29
og_description: 使用 Aspose.Words 在 Word 文件中新增指令按鈕。本教學示範如何快速設定 ActiveX 控制項屬性及指令按鈕的標題。
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: 在 Word 文件中新增指令按鈕 – Aspose.Words 逐步教學
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: 使用 Aspose.Words 為 Word 文件新增指令按鈕 – 完整指南
url: /zh-hant/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文件中新增指令按鈕 – 完整程式教學

有沒有曾經需要 **在 Word 文件中新增指令按鈕** 但不確定要使用哪個 API 呼叫？你並不孤單；許多開發者在首次嘗試在 DOCX 檔案中嵌入互動控制項時都會碰到這個問題。好消息是 Aspose.Words 讓這個過程出奇地簡單。在本指南中，我們將一步步說明如何建立 CommandButton ActiveX 控制項、**set activex control properties**，以及**set command button caption**——全部使用您現在就能直接複製貼上的乾淨 C# 程式碼。

完成本教學後，您將擁有一個完整功能的 Word 檔案，內含可點擊的「Submit」按鈕，隨時可以在 Microsoft Word 中開啟。無需外部 VBA 腳本，亦不必手動調整 UI——全程以程式方式控制。

## 您將學會

* 如何建立空白 Word 文件與 `DocumentBuilder`。
* 使用 Aspose.Words **在 Word 文件中新增指令按鈕** 的確切方法呼叫。
* 如何 **set activex control properties**（如尺寸、位置、名稱） 的各種方式。
* 正確的 **set command button caption** 技巧，讓按鈕顯示您想要的文字。
* 處理不同按鈕類型、DPI 縮放與 Word 版本相容性的實用技巧。

> **先決條件：** 已安裝 Aspose.Words for .NET（NuGet 套件 `Aspose.Words`）的 Visual Studio（或任何 C# IDE）。不需要事先了解 ActiveX。

---

## 步驟 1：設定專案並匯入命名空間

在 **在 Word 文件中新增指令按鈕** 之前，我們需要一個參考 Aspose.Words 的 C# 專案。建立一個新的 .NET 主控台應用程式，然後加入 NuGet 套件：

```bash
dotnet add package Aspose.Words
```

接著在來源檔案中加入必要的命名空間：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

這三個 `using` 指令讓您可以存取 `Document`、`DocumentBuilder` 與 `Forms2OleControl` 這些用於插入 ActiveX 控制項的類別。

*小技巧：* 若您使用 Visual Studio，IDE 會在您輸入類別名稱時自動建議加入這些 `using`。

---

## 步驟 2：建立空白文件與 Builder

全新的 `Document` 物件代表一個空的 Word 檔案。`DocumentBuilder` 則是我們的「筆」——可以繪圖、插入文字，且最關鍵的是放置 ActiveX 控制項。

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

此時文件僅是一張空白畫布——想像成一張等待您放置指令按鈕的白紙。

---

## 步驟 3：插入 CommandButton ActiveX 控制項

現在我們終於 **在 Word 文件中新增指令按鈕**。Aspose.Words 提供 `InsertForms2OleControl` 方法，接受控制項類型與尺寸。我們使用 `Forms2OleControlType.CommandButton`，寬度 150 點，高度 30 點，尺寸相當舒適。

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

此方法會回傳一個 `Forms2OleControl` 實例，接下來我們將利用它 **set activex control properties**。

---

## 步驟 4：設定控制項 – 名稱、標題與位置

### 設定標題

標題即顯示在按鈕上的文字。要 **set command button caption**，只需將字串指派給 `Caption` 屬性：

```csharp
commandButton.Caption = "Submit";
```

您可以將 `"Submit"` 改成任何文字——「Save」「Export」「Launch」等，Word 會顯示完全相同的文字。

### 命名控制項

為控制項設定具意義的名稱，可在之後（例如自動化 Word 巨集）更容易引用。我們設定 `Name` 屬性：

```csharp
commandButton.Name = "btnSubmit";
```

### 在頁面上的定位

Word 以點（1/72 吋）作為版面單位。調整 `Left` 與 `Top` 屬性即可將按鈕放置在需要的位置：

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

若需相對於段落對齊按鈕，可先移動 Builder 的游標，再插入控制項；座標會以該位置為基準。

*邊緣案例：* 在高 DPI 螢幕上，Word 中的視覺大小可能略有差異。若要在不同裝置上保持實體尺寸一致，可依目標 DPI（Word 預設 96 DPI）計算點數。

---

## 步驟 5：儲存文件

控制項全部設定完成後，只要一行程式碼即可寫入檔案：

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

產生的 `CommandButton.docx` 包含一個完整功能的 ActiveX 按鈕。用 Microsoft Word 開啟，即可看到「Submit」按鈕正好位於您指定的位置。

### 預期結果

1. Word 文件開啟後只有一頁。
2. 在您指定的座標出現一個標示為 **Submit** 的矩形按鈕。
3. 若右鍵點擊該按鈕並選擇 **Properties**，會看到名稱 `btnSubmit` 以及您先前設定的其他屬性。

---

## 步驟 6：進階變形與常見陷阱

### 插入其他 ActiveX 類型

`InsertForms2OleControl` 方法不限於指令按鈕。您也可以嵌入核取方塊、選項按鈕，甚至自訂的 ActiveX 物件：

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

相同的 **set activex control properties** 模式仍然適用——只要換掉列舉型別即可。

### 處理不同 Word 版本

較舊的 Word 版本（2007 之前）使用二進位 `.doc` 格式，ActiveX 控制項的儲存方式不同。Aspose.Words 會在您以 `.doc` 儲存時自動轉換控制項，但某些屬性（例如精確定位）可能會有位移。若目標為舊版格式，請在相應的 Word 版本中測試輸出結果。

### 安全性設定

在安全性較嚴格的機器上，Word 可能會停用 ActiveX 控制項。為避免出現「安全性警告」對話框，可考慮：

* 使用受信任的憑證簽署文件。
* 指示使用者在該檔案位置啟用 ActiveX 內容。
* 若安全性是主要顧慮，可改用無巨集的替代方案（例如純內容控制項）。

---

## 步驟 7：完整範例程式

以下是結合所有步驟的完整可執行程式碼。將它貼到 `Program.cs`，視需要調整輸出路徑，然後執行 **Run**。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**程式碼說明：**

* 從全新文件開始。
* 插入指令按鈕，**set activex control properties**，並 **set command button caption**。
* 加入一段簡短說明文字。
* 將檔案儲存為 `CommandButton.docx`。

執行程式後，開啟產生的檔案，即可看到按鈕位於說明文字下方。

---

## 結論

我們已示範如何使用 Aspose.Words **在 Word 文件中新增指令按鈕**、如何 **set activex control properties**，以及如何 **set command button caption**——全部以簡潔、可直接投入生產環境的 C# 程式碼完成。此方法具備可擴充性：只要更換控制項類型、調整尺寸，或在迴圈中依資料來源自動插入多個按鈕。

想更進一步嗎？試試以下方向：

* 將按鈕綁定至觸發資料匯出的巨集。
* 使用 `Picture` 屬性在按鈕內加入圖像或自訂圖示。
* 建立包含多種 ActiveX 控制項（文字方塊、下拉式選單等）的完整表單。

多加實驗是精通 Word 自動化的最佳方式。若遇到問題，請再次檢查 DPI 計算與 Word 安全性設定。祝開發順利，讓您的文件變得更具互動性！

## 接下來該學什麼？

以下教學與本指南所示技巧密切相關，能幫助您進一步掌握 API 功能並探索其他實作方式：

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}