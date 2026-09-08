---
category: general
date: 2026-09-08
description: 如何在 C# 中插入 ActiveX 控制項時保存 docx。請參考此逐步指南，以程式方式新增指令按鈕。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: zh-hant
lastmod: 2026-09-08
og_description: 如何在 C# 中插入 ActiveX 控制項時儲存 docx。此教學一步一步指導您以程式方式建立 Word 文件、加入指令按鈕，並持久化檔案。
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: 如何在 C# 中儲存 docx 並嵌入 ActiveX 按鈕
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: 如何使用 C# 儲存 docx 並插入 ActiveX 按鈕
url: /zh-hant/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 儲存 docx 並插入 ActiveX 按鈕

如果你需要以程式方式建立 Word 文件，然後以互動按鈕的方式儲存為 docx，本指南將教你如何完成。你將學習如何插入 ActiveX 控制項、加入 ActiveX 按鈕，並使用 C# 以及 Aspose.Words 函式庫儲存產生的 .docx 檔案。

本教學涵蓋了完成 **create word document programmatically**、嵌入 **command button**，以及將檔案持久化至磁碟的每一步。無需先前的 COM 物件經驗，但你應具備基本的 C# 知識並已安裝 Visual Studio。

## 前置條件

* .NET 6.0 SDK 或更新版本  
* Visual Studio 2022（或任何 C# IDE）  
* Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）  
* 了解 C# 專案結構  

上述項目可確保程式碼能順利編譯與執行，且不需額外設定。

## 步驟 1：建立新的 C# 主控台專案

建立一個主控台應用程式，用來承載 Word 自動化的邏輯。

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

上述指令會建立名為 **WordActiveXDemo** 的資料夾、加入 Aspose.Words 參考，並為編譯做好專案設定。

## 步驟 2：以程式方式建立 Word 文件

開啟產生的 `Program.cs` 檔案，並加入必要的 `using` 指示詞。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

現在建立一個空白的 `Document` 物件。此物件在記憶體中代表整個 Word 檔案。

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

`Document` 類別是所有 Word 處理操作的入口點。目前文件尚未包含任何頁面，但當你加入內容時，Aspose.Words 會自動建立預設的節。

## 步驟 3：插入 ActiveX 控制項 – 新增 activex 按鈕

`**Forms2OleControl**` 物件允許你在 Word 段落中嵌入 ActiveX 控制項。以下程式碼會插入一個寬度 150 pt、高度 30 pt 的 **CommandButton**。

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` 會建立控制項並回傳一個強型別的 `Forms2OleControl` 實例，你可以進一步設定。此方法會自動新增段落以容納控制項，無需手動管理段落物件。

## 步驟 4：設定指令按鈕 – 如何加入 command button 屬性

設定按鈕的 **Name** 與 **Caption** 屬性，使其在執行時可辨識，且在使用者介面上友好。

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

`Name` 屬性在之後透過 VBA 或 Word 巨集處理按鈕點擊事件時很有用。`Caption` 則是最終使用者在按鈕表面看到的文字。

### 小技巧
如果你打算從 C# 自動化處理點擊事件，可嵌入參考 `cmdSubmit` 的 VBA 巨集。文件開啟時，Word 會提示使用者啟用巨集，這是 ActiveX 控制項的標準安全行為。

## 步驟 5：如何儲存 docx

控制項就位後，將文件持久化為 .docx 檔案。`Save` 方法會根據檔案副檔名自動選擇相應的格式。

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

儲存檔案即完成 **how to save docx** 工作流程。產生的檔案可於 Microsoft Word 開啟，ActiveX 按鈕會出現在第一頁。點擊按鈕時，除非已附加巨集，否則 Word 只會顯示佔位訊息。

## 步驟 6：執行程式並驗證結果

編譯並執行主控台應用程式：

```bash
dotnet run
```

程式執行完畢後，於 Microsoft Word 開啟 `C:\Temp\CommandButton.docx`：

* 文件僅有單一頁面，且在頁面上方附近有一個 **Submit** 按鈕。  
* 將滑鼠移至按鈕上會顯示名稱為 `cmdSubmit` 的工具提示。  
* 內容未遺失，且檔案大小與一般空白 .docx 相當。

若按鈕未出現，請確認以下事項：

1. Word 的 **Trust Center** 設定允許 ActiveX 控制項。  
2. 檔案已以 `.docx` 副檔名儲存（而非 `.doc`）。

## 邊緣情況與常見變化

| 情況 | 建議調整 |
|-----------|------------------------|
| 需要不同的按鈕尺寸 | 在 `InsertForms2OleControl` 中變更寬度與高度參數。 |
| 想將按鈕放在特定頁面 | 在加入頁面後使用 `builder.MoveToDocumentEnd();`，或在控制項前插入分頁符。 |
| 必須支援沒有 Aspose.Words 的環境 | 使用 Open XML SDK 插入 `w:object` 元素，但程式碼會變得相當複雜。 |
| 需要啟用巨集的文件 | 以 `.docm` 副檔名儲存 (`document.Save("MyDoc.docm");`) 並嵌入處理 `cmdSubmit_Click` 的 VBA 模組。 |

## 完整原始碼

以下是完整、獨立的程式碼，你可以直接複製到 `Program.cs`，並在不做任何修改（輸出路徑除外）的情況下執行。

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
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 預期的主控台輸出

```
Document saved to C:\Temp\CommandButton.docx
```

在 Word 中開啟檔案會顯示標示為 **Submit** 的按鈕。點擊該按鈕會觸發預設的 ActiveX 行為（顯示訊息框，指出未附加巨集）。

## 結論

本教學示範了在嵌入 **ActiveX control**（特別是作為指令按鈕的 **add activex button**）的同時 **how to save docx**。現在你已了解如何 **create word document programmatically**、設定按鈕屬性，並將檔案持久化供最終使用者互動。

接下來，你可以探索：

* 加入 VBA 巨集以處理 `cmdSubmit_Click`。  
* 插入其他 ActiveX 控制項，例如核取方塊或下拉式方塊。  
* 產生包含多個互動元素的多頁文件。  

嘗試不同的控制項類型與版面配置，打造功能豐富、互動式的 Word 範本，以簡化你的業務流程。

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [Aspose.Words – 將 docx 儲存為 txt 並將 Word 方程式匯出為 LaTeX – 完整指南](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [如何復原 docx – C# 針對損毀 Word 檔案的指南](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [如何將 Word 儲存為 Markdown – 完整 C# 指南](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}