---
category: general
date: 2026-08-04
description: 使用 Aspose.Words 建立空白 Word 文件並插入指令按鈕。學習設定按鈕大小以及在 C# 中加入可點擊的按鈕。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: zh-hant
lastmod: 2026-08-04
og_description: 使用 Aspose.Words 建立空白 Word 文件並插入指令按鈕。本指南說明如何設定按鈕大小、加入可點擊的按鈕，以及儲存檔案。
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: 建立空白 Word 文件並加入指令按鈕 – 完整 C# 教學
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 使用指令按鈕建立空白 Word 文件 – 逐步指南
url: /zh-hant/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立空白 Word 文件並加入指令按鈕 – 步驟指南

如果您需要 **建立空白 Word 文件** 並包含互動按鈕，本教學將向您展示如何使用 Aspose.Words for .NET 完成。您將學會 **插入指令按鈕**、調整外觀以及使其可點擊——只需幾行 C# 程式碼。

本指南涵蓋從專案設定到儲存最終檔案的全部步驟，讓您可以直接將完整解決方案複製貼上到自己的應用程式中。過程中我們也會說明如何以程式方式 **新增可點擊按鈕**、**設定按鈕大小**，以及 **建立指令按鈕**。

## 前置條件

* 已安裝 .NET 6.0 SDK 或更新版本。  
* Visual Studio 2022（或任何支援 .NET 的 IDE）。  
* Aspose.Words for .NET NuGet 套件（`Aspose.Words` 版本 23.12 或更新）。  
* 具備 C# 及物件導向程式設計的基本知識。  

不需要額外的 Office Interop 組件，因為 Aspose.Words 完全獨立於 Microsoft Word 工作。

## 步驟 1：設定 .NET 專案

建立一個主控 Word 自動化程式碼的主控台應用程式。

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

此指令會建立一個名為 `WordButtonDemo` 的新資料夾，內含可直接執行的 `Program.cs`，並加入 Aspose.Words 程式庫。

## 步驟 2：建立空白 Word 文件

第一步是 **建立空白 Word 文件**。Aspose.Words 提供的 `Document` 類別可直接代表一個空的 Word 檔案。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

建立空白文件可為您提供一個乾淨的畫布，您可以在其上加入段落、表格，或在本例中加入 OLE 指令按鈕。

## 步驟 3：初始化 DocumentBuilder

`DocumentBuilder` 是協助您向文件插入內容的工具。您需要將它與剛剛建立的文件關聯起來。

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

建構器會維持目前的游標位置，因此之後的任何插入都會精確發生在您指定的位置。

## 步驟 4：插入指令按鈕

現在我們要 **插入指令按鈕**（OLE `Forms2OleControl`）到文件中。`InsertForms2OleControl` 方法需要三個參數：

1. OLE 控制項的 ProgID —— 標準按鈕使用 `"CommandButton"`。  
2. 定義 **設定按鈕大小** 及位置的 `Rectangle`。  
3. 按鈕上顯示的標題文字。  

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

當文件在 Word 中開啟時，該按鈕的行為與任何原生表單控制項相同——您可以點擊它，Word 會觸發相關的巨集（若有的話）。這滿足了 **新增可點擊按鈕** 的需求。

### 為何使用 Forms2OleControl？

`Forms2OleControl` 直接將 OLE 物件嵌入 DOCX 檔案，保留控制項的屬性且不需 Word Interop 組件。這是 **建立指令按鈕** 並在各版本 Word 中皆能正常運作的最可靠方式。

## 步驟 5：自訂按鈕（可選）

您可能想更精確地 **設定按鈕大小**，或變更其他屬性，例如字型或背景顏色。Aspose.Words 會公開底層的 OLE 物件，讓您進一步調整。

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

若需要不同尺寸，只要在步驟 4 中調整 `Rectangle` 的數值即可。座標以點 (pt) 為單位 (1 pt = 1/72 英吋)，因此 `120` 大約等於 1.67 英吋寬。

## 步驟 6：儲存文件

最後，將文件寫入磁碟。產生的檔案是一個包含完整功能指令按鈕的 **空白 Word 文件**。

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

當您在 Microsoft Word 中開啟 `CommandButtonDemo.docx` 時，會看到一個標示為「Click Me」的按鈕。點擊該按鈕會顯示預設的巨集對話框，除非您自行附加自訂巨集。

## 完整原始碼

以下是完整程式碼，您可以直接複製到 `Program.cs`。它包含上述所有步驟，且可直接編譯執行。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### 預期結果

執行程式會產生 `CommandButtonDemo.docx`。在 Word 中開啟該檔案會看到：

* 單一頁面，內含標示為 **Click Me** 的按鈕。  
* 按鈕遵循 **設定按鈕大小**（120 × 30 點）。  
* 點擊按鈕會觸發 Word 的預設指令按鈕行為，證實 **新增可點擊按鈕** 操作成功。

## 常見問題與邊緣案例

| Question | Answer |
|----------|--------|
| **這能在 .doc 檔案中使用嗎？** | 可以。將 `doc.Save("file.doc")` 的檔案副檔名改為 .doc 即可。OLE 控制項同樣會儲存在舊版的二進位格式中。 |
| **如果需要多個按鈕該怎麼辦？** | 重複呼叫 `InsertForms2OleControl`，並為每個新按鈕調整 `Rectangle` 以避免重疊。 |
| **我可以為按鈕附加巨集嗎？** | 按鈕本身不包含巨集程式碼。您必須手動或透過 `Document` 物件的 `Modules` 集合將 VBA 巨集加入文件中。 |
| **在匯出為 PDF 時按鈕會顯示嗎？** | 使用 Aspose.Words 將 DOCX 匯出為 PDF 時，按鈕會被渲染為靜態影像，並非互動式控制項。 |
| **支援哪些版本的 Word？** | OLE 指令按鈕在 Word 2007 及之後的版本皆可使用，因為它遵循標準的 Forms2.0 規範。 |

## 結論

現在您已了解如何使用 Aspose.Words for .NET **建立空白 Word 文件**、**插入指令按鈕**、**新增可點擊按鈕**，以及 **設定按鈕大小**。完整範例展示了從頭到尾的 **建立指令按鈕** 工作流程，為您進一步的 Word 自動化任務奠定了堅實基礎。

## 後續步驟

* 透過變更 `InsertForms2OleControl` 中的 ProgID，探索其他 OLE 控制項（例如 `CheckBox`、`ListBox`）。  
* 將按鈕與 VBA 巨集結合，讓使用者點擊時執行自訂動作。  
* 使用 Aspose.Words 的 `DocumentBuilder` 在插入按鈕前加入額外內容，如表格、圖片或註腳。  
* 嘗試不同的 **設定按鈕大小** 數值，以符合文件版面配置的需求。  

祝開發順利，盡情打造具互動控制項的更豐富 Word 文件吧！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}