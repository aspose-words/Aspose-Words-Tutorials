---
category: general
date: 2026-10-13
description: 學習如何使用 Aspose.Words 以程式方式加入指令按鈕。本指南亦示範如何使用完整的 C# 程式碼建立 Word 文件按鈕。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: zh-hant
lastmod: 2026-10-13
og_description: 使用 Aspose.Words 以程式方式在 Word 文件中加入指令按鈕。遵循此完整教學，使用 C# 建立 Word 文件按鈕。
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: 以程式方式在 Word 文件中加入指令按鈕 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 如何以程式方式在 Word 文件中新增指令按鈕
url: /zh-hant/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何以程式方式在 Word 文件中加入指令按鈕  

如果您需要 **以程式方式加入指令按鈕**，Aspose.Words 提供了簡潔的 API，讓您直接在 .docx 檔案中嵌入 OLE 表單控制項。本教學將逐步說明如何 **建立 Word 文件按鈕**，使其在 Microsoft Word 開啟時行為如同一般的表單按鈕。  

您將學會如何設定開發環境、插入按鈕、配置屬性，並驗證結果。整個流程不需要任何外部工具——只要一個 .NET 專案與 Aspose.Words for .NET 函式庫即可。  

## 前置條件  

開始之前，請確保您已具備以下條件：  

* 已安裝 .NET 6.0 SDK 或更新版本。  
* 已安裝最新的 Aspose.Words for .NET（範例使用 23.12，任何 22.x 以上的版本皆可）。  
* 具備 Visual Studio 2022 或 Visual Studio Code 等 IDE。  

Aspose.Words 為跨平台套件，程式碼可在 Windows、macOS 與 Linux 上執行。  

## 步驟 1：建立專案並參考 Aspose.Words  

1. 建立新的 console 專案：  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. 新增 Aspose.Words NuGet 套件：  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. 開啟 **Program.cs**，將內容替換為下一步驟所示的範本。  

以此方式設定專案，可讓編譯器找到 `Aspose.Words` 與 `Aspose.Words.Drawing.Forms` 命名空間，這兩者是使用表單控制項所必需的。  

## 步驟 2：初始化空白文件與 DocumentBuilder  

`Document` 類別代表整個 Word 檔案，而 `DocumentBuilder` 提供流暢的 API 以加入內容。  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*此步驟的重要性* – 若沒有 `DocumentBuilder`，您無法精確定位按鈕於頁面上的位置。Builder 會遵循目前的游標位置，讓日後插入多個控制項變得更簡單。  

## 步驟 3：插入指令按鈕 OLE 控制項  

Aspose.Words 將指令按鈕視為 `ControlType.CommandButton` 類型的 OLE 控制項。您需要使用以點 (1 point = 1/72 吋) 為單位的 `RectangleF` 來定義其位置與大小。  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**重點說明**  

* 矩形的原點 (X, Y) 以頁面左上角為基準。  
* 調整 `Width` 或 `Height` 會改變按鈕的視覺尺寸。  
* `InsertForms2OleControl` 會回傳 `Forms2OleControl` 物件，您可以進一步設定。  

## 步驟 4：設定按鈕的名稱與標題  

**名稱** 供 Word 的巨集引擎辨識控制項；**標題** 則是使用者看到的文字。  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

若您之後會加入 VBA 巨集，請使用具描述性的名稱，因為 Word 的巨集錄製器會參照此屬性。  

## 步驟 5：（可選）儲存文件並驗證結果  

將檔案儲存後即可在 Microsoft Word 中開啟，確認按鈕是否正確顯示與運作。  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

當您在 Word 中開啟 *CommandButtonDemo.docx* 時，應看到一個標示為 **Submit** 的按鈕，約位於左邊距 1.4 吋、上邊距 2.1 吋處。預設情況下點擊按鈕不會執行任何動作，因為尚未附加巨集，但視覺控制項已完整可用。  

## 步驟 6：邊緣情況與常見陷阱  

| 情境 | 需注意的地方 | 建議的解決方式 |
|-----------|-------------------|-----------------|
| **按鈕與現有文字重疊** | 矩形可能與段落相交，導致版面配置問題。 | 在呼叫 `builder.Writeln()` 後插入按鈕，使游標移至新行，或調整 `Y` 座標。 |
| **文件開啟時出現警告** | 某些 Word 版本會標示缺少連結程式的 OLE 控制項。 | 確認控制項類型為 `CommandButton`；Word 會將其視為標準表單元素，無需外部程式。 |
| **在 Linux 無頭環境執行** | 無法啟動 Word 來測試 UI，但檔案仍然有效。 | 使用單元測試讀取控制項屬性（`commandButton.Name`、`commandButton.Caption`），驗證設定是否正確。 |
| **需要多個按鈕** | 重複使用同一個 `DocumentBuilder` 而未移動游標，會把新按鈕疊在舊按鈕上。 | 呼叫 `builder.MoveToDocumentEnd()` 或在每次插入前調整矩形的 `Y` 值。 |

提前處理這些邊緣情況，可在將解決方案擴展至包含數十個控制項的完整表單時節省大量時間。  

## 步驟 7：完整、可執行的範例  

以下程式碼為自包含範例，您只要複製、貼上並執行（除 NuGet 還原外無需其他修改）。  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**預期輸出**  

執行程式後會印出類似以下的路徑：  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

開啟產生的 *CommandButtonDemo.docx*，即可看到一個位於程式碼中定義座標的 **Submit** 按鈕。未出現其他 UI 元素，代表 **以程式方式加入指令按鈕** 的流程已成功。  

## 結論  

您現在已掌握如何使用 Aspose.Words **以程式方式加入指令按鈕** 到 Word 文件，同時也了解如何 **建立 Word 文件按鈕**，以便日後連結 VBA 巨集或外部自動化工具。整個流程包括：初始化文件、插入 OLE `CommandButton` 控制項、設定屬性，最後儲存檔案。  

接下來您可以：  

* 透過重複步驟 3，使用不同的 `ControlType` 值，加入更多控制項（核取方塊、文字欄位）。  
* 為按鈕附加 VBA 巨集，以執行儲存表單或寄送電子郵件等動作。  
* 以迴圈遍歷資料驅動的欄位定義集合，動態產生整套表單。  

請自行調整矩形座標與按鈕標題，以符合您的 UI 設計。祝開發順利！  


## 接下來您可以學習什麼？  


以下教學與本指南的技巧密切相關，提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}