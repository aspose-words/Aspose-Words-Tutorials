---
category: general
date: 2026-08-20
description: 學習如何建立 ActiveX 控制項、設定按鈕大小，並以完整的 C# 範例將按鈕加入 Word。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: zh-hant
lastmod: 2026-08-20
og_description: 使用 C# 在 Word 檔案中建立 ActiveX 控制項。本教學示範如何設定按鈕大小、將按鈕加入 Word，並製作可點擊的按鈕。
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: 在 Word 中建立 ActiveX 控制項 – 逐步 C# 教學
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: 如何使用 C# 在 Word 文件中建立 ActiveX 控制項
url: /zh-hant/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 在 Word 文件中建立 ActiveX 控制項

如果您需要在 Microsoft Word 檔案中 **建立 ActiveX 控制項**，本指南會精確說明操作步驟。您將會看到如何 **在 Word 中加入按鈕**、設定按鈕尺寸，以及讓控制項可點擊——全部透過一個簡短且獨立的 C# 程式完成。

在本教學中，您將會：

* 了解為何 ActiveX 控制項對於互動式 Word 文件很有用。  
* 學會設定 **按鈕尺寸** 並指定標題的完整程式碼。  
* 看到如何 **建立可點擊的按鈕**，之後可連結至巨集或外部邏輯。  

此步驟適用於 Aspose.Words .NET 23.12 或更新版本，且僅需 .NET 開發環境。

> **先決條件** – 您已擁有有效的 Aspose.Words 授權（或使用評估版），且已安裝 Visual Studio 2022 或任何 C# IDE。

---

## 如何在 Word 文件中建立 ActiveX 控制項

第一步是建立一個空的 `Document` 與 `DocumentBuilder`。`DocumentBuilder` 提供了高階 API，可用於插入諸如 ActiveX 控制項之類的物件。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

`InsertActiveXButton` 方法（下方定義）包含了 **如何插入按鈕** 以及設定它的邏輯。

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

執行程式會產生 **ActiveXButton.docx**。在 Word 中開啟此檔案會看到一個標示為 **Submit** 的按鈕。此控制項功能完整——點擊它會觸發標準的 `CommandButton_Click` 事件，您之後可以將其綁定至 VBA 巨集。

### 為什麼這樣做會有效

* `InsertForms2OleControl` 告訴 Word 嵌入一個類型為 **CommandButton** 的 OLE 物件，這是傳統的 ActiveX 按鈕類別。  
* 寬度與高度參數直接 **設定按鈕尺寸**；Word 會將數值從點（1 pt ≈ 1/72 in）轉換。  
* 為控制項命名 (`Name = "btnSubmit"`) 後，您可在 VBA 中輕鬆透過 `ActiveDocument.InlineShapes("btnSubmit")` 取得它。  

## 設定按鈕尺寸與標題

如果您需要不同的外觀，請調整 `InsertForms2OleControl` 呼叫中的數值參數。方法簽名如下：

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – ActiveX 類別的程式識別碼（標準按鈕為 `"CommandButton"`）。  
* **width / height** – 以點為單位的尺寸。例如要建立寬度為 2 cm 的按鈕，使用 `width = 56.7`（2 cm ≈ 56.7 pt）。  

您也可以在插入後修改標題：

```csharp
commandButton.Caption = "Send Request";
```

變更標題不會影響尺寸，但會改變使用者看到的視覺回饋。

### 小技巧

如果想要方形按鈕，將兩個尺寸設為相同的值：

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

## 將按鈕加入 Word 並使其可點擊

上述程式碼已 **將按鈕加入 Word**。若要讓按鈕執行動作，必須撰寫一段處理 `Click` 事件的 VBA 巨集。以下是一個最小範例，您可以貼到 Word VBA 編輯器（`Alt+F11` → Insert → Module）中：

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

因為控制項名稱為 `btnSubmit`，Word 會自動將 `Click` 事件對應到 `btnSubmit_Click`。這是 **建立可點擊按鈕** 功能的標準做法，無需外部函式庫。

> **注意：** Word 的巨集安全性設定可能會阻擋 ActiveX 控制項。請確保文件的安全性設定為「允許所有巨集」或「允許 VBA 巨集」，或在正式環境中為巨集加上數位簽章。

## 常見問題：如何插入按鈕與疑難排解

### 1. 若儲存後按鈕未出現，該怎麼辦？

* 確認您使用的 Aspose.Words 版本支援 `InsertForms2OleControl`。22.5 之前的版本不具備此功能。  
* 確認目標檔案格式為 `.docx` 或 `.doc`。較舊的格式如 `.rtf` 無法儲存 ActiveX 物件。

### 2. 我可以在特定書籤處插入按鈕嗎？

可以。在呼叫 `InsertForms2OleControl` 前，先將 builder 移動到書籤位置：

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. 如何根據文字長度動態 **設定按鈕尺寸**？

使用 `Graphics.MeasureString` 方法（來自 `System.Drawing`）計算所需寬度，並將像素轉換為點（`points = pixels * 72 / DPI`），再將計算出的寬度傳入 `InsertForms2OleControl`。

### 4. 有沒有辦法在迴圈中加入多個按鈕？

當然可以。將插入邏輯包在 `for` 迴圈中，並依序調整每次的 `Left` 與 `Top` 屬性：

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

## 預期輸出

執行程式並開啟 **ActiveXButton.docx** 後：

* 會在第一頁左上角出現一個 **Submit** 按鈕。  
* 按鈕尺寸符合您提供的尺寸（`100 pt × 30 pt`）。  
* 若您加入了 VBA 巨集，點擊按鈕會顯示訊息框：「You clicked the Submit button!」。

您現在已成功 **建立 ActiveX 控制項**、**設定按鈕尺寸**，以及 **將按鈕加入 Word**，同時也學會 **如何插入按鈕** 與 **建立可點擊按鈕**，可用於未來的自動化任務。

## 結論

在本教學中，您學會了如何使用 C# 在 Word 文件內 **建立 ActiveX 控制項**。依循步驟即可 **設定按鈕尺寸**、為控制項命名，並 **將按鈕加入 Word**，使其成為與 VBA 巨集連結的 **可點擊按鈕**。

接下來您可以探索：

* 將按鈕綁定至 .NET COM 加載項，而非 VBA。  
* 使用其他 ActiveX 類別，例如 `CheckBox` 或 `ComboBox`。  
* 自動化建立包含多個控制項的完整表單。

隨意嘗試不同的尺寸吧

## 接下來您可以學習什麼？

以下教學與本指南的技術緊密相關，能進一步深化您的應用。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索替代實作方式。

- [使用 .NET 建立帶浮動影像的 Word 文件](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [使用 Aspose.Words 建立帶頁首與頁尾的 Word 文件](/words/english/net/header-footer-formatting/create-header-footer/)
- [從 Word 建立符合無障礙標準的 PDF – 完整指南](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}