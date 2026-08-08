---
category: general
date: 2026-08-07
description: 如何在 C# 中使用 Aspose.Words 建立內容控制項 – 學習如何新增 SDT、設定佔位符、寫入預設文字，以及插入純文字內容控制項。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create content control
- how to add sdt
- how to set placeholder
- how to write default text
- insert plain text control
language: zh-hant
lastmod: 2026-08-07
og_description: 如何在 C# 中使用 Aspose.Words 建立內容控制項。本教學示範如何新增 SDT、設定佔位符、寫入預設文字，以及插入純文字控制項。
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: 如何在 C# 中建立內容控制項 – 完整 Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  headline: How to create content control in C# with Aspose.Words
  type: TechArticle
- description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  name: How to create content control in C# with Aspose.Words
  steps:
  - name: Expected output
    text: '- A `.docx` file on the desktop named `CustomerNameControl.docx`. - Inside
      the file, a single content control containing the text **John Doe**. - The placeholder
      text appears in light gray until the user types a new value.'
  - name: Adding multiple content controls
    text: You can repeat the **how to add sdt** steps to insert several controls in
      the same document. Just create a new `StructuredDocumentTag` for each field
      and move the builder accordingly.
  - name: Reading a placeholder programmatically
    text: 'If you need to verify that a placeholder was set correctly, inspect the
      `PlaceholderName` property:'
  - name: Using other SDT types
    text: Aspose.Words supports dropdown lists, date pickers, and rich‑text controls.
      Replace `SdtType.PlainText` with `SdtType.DropDownList` or `SdtType.RichText`
      to change the control type.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- SDT
title: 如何在 C# 中使用 Aspose.Words 建立內容控制項
url: /zh-hant/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用 Aspose.Words 建立內容控制項

如果你需要以程式方式在 Word 文件中 **how to create content control**，本指南會完整示範。你將看到如何加入 SDT、設定佔位符、寫入預設文字，以及插入純文字控制項——全部使用 Aspose.Words for .NET。

本教學涵蓋從專案設定到儲存最終 `.docx` 檔案的每一步。完成後，你將能產生包含完整設定內容控制項的文件，供後續處理或使用者互動使用。

## 前置條件

- .NET 6.0 或更新版本（程式碼亦相容於 .NET Framework 4.7 以上）
- Aspose.Words for .NET 授權或暫時評估金鑰
- Visual Studio 2022（或任何支援 C# 的 IDE）
- 具備基本的 C# 語法知識

除了 `Aspose.Words` 之外，無需其他 NuGet 套件。

## 如何建立內容控制項 – 步驟 1：設定專案

建立一個新的主控台應用程式，並加入 Aspose.Words 套件：

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

**how to create content control** 的流程從一個全新的 `Document` 物件開始。此物件代表你即將操作的 Word 檔案。

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **專業提示：** 請讓 `DocumentBuilder` 實例在整個文件生命週期內保持存活；不必要的重新建立會增加額外負擔。

## 如何加入 SDT – 步驟 2：插入純文字 Structured Document Tag

SDT（Structured Document Tag）是內容控制項的技術名稱。若要 **how to add sdt**，請以所需類型實例化 `StructuredDocumentTag`。

```csharp
        // Create a plain‑text SDT (content control)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document,
            SdtType.PlainText,   // Plain‑text control
            true);               // Is it a repeating section? false for single use

        // Give the control a title – this is how you reference it later
        sdt.Title = "CustomerName";

        // Insert the SDT at the current cursor position
        builder.InsertNode(sdt);
```

`SdtType.PlainText` 選項會建立一個使用者可編輯的簡易文字方塊。設定 `Title` 可在之後需要取得或修改內容時，協助你定位該控制項。

## 如何設定佔位符 – 步驟 3：配置佔位文字

佔位符會在使用者輸入前顯示範例文字，以指引最終使用者。若要 **how to set placeholder**，請指派 `PlaceholderName` 屬性。

```csharp
        // Define the placeholder that appears when the control is empty
        sdt.PlaceholderName = "Enter name here";
```

當文件在 Microsoft Word 中開啟時，灰色的佔位文字會顯示在控制項內，直至使用者輸入值為止。

## 如何寫入預設文字 – 步驟 4：在 SDT 內加入初始內容

若希望控制項內含有預先定義的內容，必須將 builder 移至 SDT 內部再寫入文字。此範例示範 **how to write default text**。

```csharp
        // Position the builder inside the SDT so we can add content
        builder.MoveTo(sdt);

        // Write the default text that will be visible initially
        builder.Write("John Doe");
```

`MoveTo` 呼叫會將游標位置移至 SDT 內部。執行 `Write` 後，控制項會顯示「John Doe」作為初始值。

## 插入純文字控制項 – 步驟 5：儲存文件

最後，將文件寫入磁碟。這樣即可完成 **insert plain text control** 的操作。

```csharp
        // Save the document with the content control embedded
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CustomerNameControl.docx");

        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

當你在 Word 中開啟 `CustomerNameControl.docx` 時，會看到一個標題為 **CustomerName** 的純文字內容控制項，顯示佔位文字「Enter name here」以及預設文字「John Doe」。

### 預期輸出

- 桌面上名為 `CustomerNameControl.docx` 的 `.docx` 檔案。
- 檔案內部包含一個內容控制項，內含文字 **John Doe**。
- 佔位文字以淡灰色顯示，直至使用者輸入新值。

## 其他變化與邊緣情況

### 新增多個內容控制項

你可以重複 **how to add sdt** 的步驟，在同一文件中插入多個控制項。只需為每個欄位建立新的 `StructuredDocumentTag`，並相應地移動 builder 即可。

```csharp
// Example: add a second control for "OrderNumber"
StructuredDocumentTag orderTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
orderTag.Title = "OrderNumber";
orderTag.PlaceholderName = "Enter order #";
builder.InsertNode(orderTag);
builder.MoveTo(orderTag);
builder.Write("12345");
```

### 程式化讀取佔位符

若需驗證佔位符是否正確設定，請檢查 `PlaceholderName` 屬性：

```csharp
string placeholder = sdt.PlaceholderName; // returns "Enter name here"
```

### 使用其他 SDT 類型

Aspose.Words 支援下拉清單、日期選擇器與富文字控制項。將 `SdtType.PlainText` 替換為 `SdtType.DropDownList` 或 `SdtType.RichText` 即可變更控制項類型。

## 常見陷阱與避免方法

| 症狀 | 原因 | 解決方式 |
|---------|-------|-----|
| 佔位符未出現 | 文件在設定佔位符前已儲存 | 確保在呼叫 `Save` 之前已設定 `PlaceholderName`。 |
| 預設文字缺失 | Builder 未移至 SDT 內部 | 在 `builder.Write` 之前呼叫 `builder.MoveTo(sdt)`。 |
| 控制項標題為空 | 未設定 `Title` 屬性 | 一定要為 `Title` 指派有意義的值，以便之後取得。 |

## 結論

現在你已了解如何在 C# 中使用 Aspose.Words **how to create content control**，包括 **how to add sdt**、**how to set placeholder**、**how to write default text** 以及 **insert plain text control**。完整範例會編譯成可直接使用的 Word 檔案，示範上述每個概念。

接下來，你可以探索更進階的情境，例如將內容控制項繫結至 XML 資料、處理重複區段，或在轉換為 PDF 時保留控制項。這些主題皆直接建立在本教學所涵蓋的基礎之上。

祝開發順利！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [Rich Text Box Content Control](/words/hindi/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/hongkong/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/spanish/net/programming-with-sdt/rich-text-box-content-control/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}