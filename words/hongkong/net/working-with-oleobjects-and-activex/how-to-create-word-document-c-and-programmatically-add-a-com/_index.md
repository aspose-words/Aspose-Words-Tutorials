---
category: general
date: 2026-09-11
description: 學習如何使用 C# 建立 Word 文件，並以程式方式使用 Aspose.Words 加入指令按鈕，只需幾個簡單步驟。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: zh-hant
lastmod: 2026-09-11
og_description: 使用 C# 建立 Word 文件，並以程式方式使用 Aspose.Words 加入指令按鈕。請參考此完整指南以獲得可行的解決方案。
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: 使用 C# 建立 Word 文件 – 程式化加入命令按鈕
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: 如何使用 C# 建立 Word 文件並以程式方式加入指令按鈕
url: /zh-hant/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 建立 Word 文件並以程式方式加入指令按鈕

如果您需要 **create word document c#** 並嵌入互動按鈕，本指南將完整說明如何操作。使用 Aspose.Words，您只需幾行程式碼即可以程式方式加入 command button，省去在 Word 中手動建立 UI 的步驟。

在本教學中，您將學會如何：

* 使用 C# 初始化空白的 Word 檔案。
* 插入 ActiveX **CommandButton** 控制項。
* 設定按鈕的屬性，如名稱與說明文字。
* 儲存文件，使按鈕在 Microsoft Word 開啟檔案時顯示。

除了 Aspose.Words for .NET 函式庫外，無需其他外部工具，且此步驟適用於 .NET 6+ 或 .NET Framework 4.6.2 及以上版本。

## 前置條件

| 需求 | 原因 |
|------------|--------|
| .NET 6 SDK (or .NET Framework 4.6.2+) | 提供 C# 專案的執行環境。 |
| Visual Studio 2022 (or any C# IDE) | 讓您能輕鬆編寫、建置與執行程式碼。 |
| Aspose.Words for .NET NuGet package | 提供範例中使用的 `Document`、`DocumentBuilder` 與 `Forms2OleControl` 類別。 |
| Basic knowledge of C# syntax | 讓您能無需額外學習曲線即可閱讀程式碼。 |

您可以透過 NuGet 主控台加入 Aspose.Words 套件：

```powershell
Install-Package Aspose.Words
```

## 步驟 1：建立新的 C# 主控台專案

建立一個會產生 Word 檔案的主控台應用程式。開啟終端機並執行以下指令：

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

產生的 `Program.cs` 檔案將承載以下步驟中示範的程式碼。

## 步驟 2：建立空白文件與 DocumentBuilder

第一步是實例化 `Document` 物件，它代表一個空的 `.docx` 檔案，並建立 `DocumentBuilder` 以編輯文件內容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**為何這很重要：**  
`Document` 是所有 Word 元素（段落、表格、控制項）的容器。`DocumentBuilder` 提供流暢的 API，讓您在目前游標位置插入物件，而不必處理低階節點集合。

## 步驟 3：插入 ActiveX CommandButton 控制項

Aspose.Words 支援透過 `InsertForms2OleControl` 方法插入傳統的 ActiveX 控制項。此方法需要指定控制項類型以及以點為單位的大小。

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**底層運作原理：**  
Word 將 ActiveX 控制項視為 OLE（Object Linking and Embedding）物件。`Forms2OleControl` 類別封裝 OLE 資料，並公開 `Name`、`Caption` 等屬性。

## 步驟 4：設定按鈕的名稱與說明文字

控制項放置後，您可以自訂其執行時屬性。設定有意義的 `Name` 有助於日後辨識按鈕，而 `Caption` 則決定按鈕上顯示的文字。

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**小技巧：**  
若您打算以 VBA 處理按鈕的點擊事件，`Name` 會成為您在巨集中引用的名稱，例如 `Sub btnSubmit_Click()`。

## 步驟 5：將文件儲存至磁碟

最後，將文件寫入 `.docx` 檔案。選擇您有寫入權限的資料夾；範例使用相對路徑，會解析至專案的輸出目錄。

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

執行程式會產生 `CommandButton.docx`。在 Microsoft Word 中開啟此檔案，即可看到可點擊的 **Submit** 按鈕：

![Word document with a Submit command button](/images/command-button.png "Screenshot of a Word document containing a Submit command button created with C#")

*圖片替代文字 (og_image_alt)：* `Screenshot of a Word document containing a Submit command button created with C#`

## 驗證結果

1. 開啟 Word 並開啟 `CommandButton.docx`。  
2. 您應該會在文件正文看到標示為 **Submit** 的按鈕。  
3. 將滑鼠懸停於按鈕上會在 **Properties** 面板（開發人員索引標籤 → Properties）顯示名稱 `btnSubmit`。  

如果按鈕未顯示，請確認 Word 已啟用 **Developer** 索引標籤（檔案 → 選項 → 自訂功能區 → 勾選 *Developer*）。未啟用時，ActiveX 控制項會被隱藏。

## 處理常見變化與例外情況

| 情況 | 建議調整 |
|-----------|------------------------|
| **不同的按鈕尺寸** | 在 `InsertForms2OleControl` 中變更寬度與高度參數。例如，`150, 40` 會產生較大的按鈕。 |
| **多個按鈕** | 重複呼叫 `InsertForms2OleControl`，在呼叫之間移動 builder 的游標（`builder.Writeln();`）。 |
| **無 ActiveX 的按鈕** | 若需相容阻止 ActiveX 的舊版 Word，可使用 `InsertFormField` 新增傳統表單欄位（例如核取方塊）。 |
| **跨平台使用** | ActiveX 控制項僅在 Windows 版 Word 可用。對於 Mac 或基於網頁的檢視器，可考慮插入樣式化為按鈕的超連結。 |
| **安全性警告** | 開啟含有 ActiveX 控制項的文件時，Word 可能會顯示安全性提示。使用受信任的憑證簽署文件可降低此阻礙。 |

## 完整、可執行的範例

以下是完整程式碼，您可直接複製貼上至 `Program.cs`。加入 Aspose.Words NuGet 套件後，即可編譯執行，無需其他修改。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**預期在主控台的輸出：**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

開啟產生的檔案即可看到已就緒的 **Submit** 按鈕，供互動使用。

## 結論

現在您已了解如何使用 Aspose.Words **create word document c#** 並 **programmatically add command button** 控制項。整個流程即是初始化 `Document`、插入 `Forms2OleControl`、設定其屬性，最後儲存檔案。接下來您可以：

* 透過變更 `ControlType`，加入更多控制項（例如核取方塊、文字欄位）。
* 將 VBA 巨集附加至按鈕，以實作自訂邏輯。
* 將此技巧與 Aspose.Words 其他功能（如合併列印或範本填充）結合使用。

請嘗試不同的尺寸、說明文字與多個按鈕，以符合您的自動化情境。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此技術為基礎。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [使用 Aspose.Words 建立含頁首與頁尾的 Word 文件](/words/english/net/header-footer-formatting/create-header-footer/)
- [使用 Aspose.Words for .NET 建立 Word 文件](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [使用 Aspose.Words for .NET 在 Word 文件中建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}