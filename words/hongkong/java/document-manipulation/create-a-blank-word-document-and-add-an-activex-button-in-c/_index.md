---
category: general
date: 2026-10-23
description: 使用 C# 建立空白 Word 文件，並學習如何使用 Aspose.Words 插入 ActiveX 控制項（包括按鈕）。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: zh-hant
lastmod: 2026-10-23
og_description: 使用 C# 建立空白 Word 文件，並學習如何使用 Aspose.Words 插入 ActiveX 控制項（包括按鈕）。
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: 建立空白 Word 文件，並在 C# 中加入 ActiveX 按鈕
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: 在 C# 中建立空白 Word 文件並加入 ActiveX 按鈕
url: /zh-hant/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中建立空白 Word 文件並加入 ActiveX 按鈕

如果您需要以程式方式 **create blank Word document**，本指南會完整說明操作步驟。您將看到一個完整、可執行的範例，該範例會建立新文件、插入 ActiveX CommandButton，並儲存檔案——全部使用 Aspose.Words for .NET。

處理 Word 檔案時常需要超越純文字的功能。加入 **ActiveX button** 可嵌入互動功能，供含巨集的範本或僅限 Windows 的解決方案使用。完成本教學後，您將能插入任何 ActiveX 控制項，但我們聚焦於最常見的情境：一個 **word document activex button** 用於提交表單。

## 前置條件

* .NET 6.0 或更新版本（程式碼亦支援 .NET Framework 4.7+）
* Visual Studio 2022（或任何 C# IDE）
* **Aspose.Words for .NET** NuGet 套件  
  ```bash
  dotnet add package Aspose.Words
  ```
* 基本熟悉 C# 語法

> **專業提示：** Aspose.Words 為商業套件，但提供免費的暫時授權供測試使用。請盡早安裝授權，以避免評估水印。

## 步驟 1：使用 Aspose.Words 建立空白 Word 文件

第一步是實例化 `Document` 物件。它代表記憶體中的空白 `.docx` 檔案。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` 起始時沒有任何節、頁面或內容。這是您在 **create blank word document** 情境（例如從頭產生報告）所需的全新白板。

## 步驟 2：取得 DocumentBuilder 以編輯文件

`DocumentBuilder` 提供便利的 API 用於加入文字、影像與控制項。我們將使用它來定位 ActiveX 控制項。

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

建構器會自動新增預設節與第一頁，讓您可以立即開始插入物件。

## 步驟 3：如何在文件中插入 ActiveX 控制項

Aspose.Words 提供 `InsertForms2OleControl` 以嵌入 OLE/ActiveX 物件。此方法需要指定控制項類型、寬度與高度（以點為單位）。以下我們插入 **CommandButton**——在舊版 Word 範本中常見的表單按鈕。

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **為什麼這樣有效：** `Forms2OleControlType.COMMANDBUTTON` 告訴 Word 建立一個按鈕，當文件在支援 ActiveX 的 Windows 環境中開啟時，可回應點擊事件。

## 步驟 4：建立 ActiveX 控制項 – 設定屬性

現在我們為按鈕設定程式名稱與可見的標題。這是 **create activex control** 中開發者常忽略的部分。

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` 為您在 VBA 巨集中引用的識別名稱（`ActiveDocument.InlineShapes("btnSubmit")`）。
* `Caption` 為顯示於按鈕本身的標籤。

## 步驟 5：儲存含 ActiveX 按鈕的 Word 文件

最後，將文件寫入磁碟。檔案副檔名必須為 `.docx`（若稍後要加入巨集則使用 `.docm`）。範例會儲存至佔位資料夾——請自行替換為您的路徑。

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

當您在 Microsoft Word（僅限 Windows）中開啟產生的檔案時，會看到一個可運作的 **word document activex button**，可連結至 VBA 程式碼。

## 完整範例程式

以下是完整程式碼，您可以直接複製貼上至新的主控台專案中。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**執行程式時的預期輸出**

```
Document saved to C:\Temp\ActiveXButton.docx
```

在 Word 中開啟產生的 `ActiveXButton.docx`，您會看到一個標示為 **Submit** 的按鈕，位於第一頁的頂部。

## 邊緣情況與常見陷阱

| 情況 | 需留意的事項 | 建議 |
|-----------|-------------------|----------------|
| 在 macOS 或 Linux 上執行 | ActiveX 為 Windows 專屬技術，按鈕會顯示為佔位符。 | 僅將本教學用於針對 Windows 的範本。 |
| 文件在 Word Online 中開啟 | 瀏覽器檢視不支援 ActiveX 控制項。 | 提供備援 UI，或指示使用者在桌面版客戶端開啟檔案。 |
| 需要巨集啟用的檔案 | `.docx` 檔案無法儲存 VBA 程式碼。 | 儲存為 `.docm`（`document.Save("MyFile.docm", SaveFormat.Docm)`），並另行加入巨集。 |
| 控制項尺寸不匹配 | 寬度/高度值以點為單位（1 pt ≈ 1/72 英吋）。 | 調整數值以取得想要的視覺尺寸。 |

## 常見問題

**如何插入除按鈕之外的 ActiveX 控制項？**  
使用相同的 `InsertForms2OleControl` 方法，但傳入不同的 `Forms2OleControlType` 列舉值，例如 `COMBOBOX` 或 `LISTBOX`。

**我可以更改按鈕的字型或顏色嗎？**  
ActiveX 按鈕的外觀由主機應用程式（Word）及底層 Windows 主題決定。您可在文件開啟後透過 VBA 修改 `ForeColor`、`BackColor` 等屬性。

**能否直接在 C# 中加入點擊事件處理程式？**  
不能。點擊事件必須由 VBA 或 Word 外掛處理，因為按鈕在 Word 程序內執行，而非您的 .NET 應用程式。

## 結論

您現在已了解如何以程式方式 **create blank Word document**，並使用 Aspose.Words for .NET 嵌入 **ActiveX button**。涵蓋的步驟如下：

1. 實例化 `Document`。
2. 使用 `DocumentBuilder` 來操作檔案。
3. 呼叫 `InsertForms2OleControl` 以 **how to insert activex** 控制項。
4. 設定控制項的屬性（**create activex control**）。
5. 儲存檔案，產生可供 VBA 整合的 **word document activex button**。

從此您可以探索加入其他控制項類型、串接 VBA 巨集，或在保留按鈕（作為靜態影像）的情況下將文件轉換為 PDF。試驗不同的尺寸、標題與名稱。

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎延伸技術。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [如何在 Word 文件中加入 ActiveX 按鈕（使用 Aspose.Words）](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [使用 C# 建立含 ActiveX 按鈕的 Word 文件 – 教學](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}