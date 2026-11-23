---
category: general
date: 2026-11-22
description: 學習如何在 Word 中使用 C# 插入 Forms2Ole 控制項。此一步一步的指南涵蓋 DocumentBuilder、指令按鈕的放置，以及
  .docx 的儲存。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: zh-hant
lastmod: 2026-11-22
og_description: 使用 C# 在 Word 中插入 Forms2Ole 控制項。請參考本指南，使用 Aspose.Words 與 DocumentBuilder
  新增指令按鈕。
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: 使用 C# 在 Word 中插入 Forms2Ole 控制項 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 C# 與 Aspose.Words 在 Word 中插入 Forms2Ole 控制項
url: /zh-hant/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 C# 與 Aspose.Words 插入 Forms2Ole 控制項

如果您需要 **在 Word 中插入 Forms2Ole 控制項**，本教學將示範如何使用 C# 完成。無論是建立可填寫的範本或是自動化表單產生，以下解決方案都能讓您以程式方式加入指令按鈕。

您將學會如何建立空白文件、使用 `DocumentBuilder` 放置控制項，並將結果儲存為 `.docx`。本指南亦說明常見的陷阱，例如座標系統與舊版 Word 的相容性問題。

## 前置條件

開始之前，請確保您已具備：

* .NET 6.0 或更新版本（程式碼亦相容 .NET Framework 4.6+）
* Aspose.Words for .NET（NuGet 套件 `Aspose.Words`）
* 基本的 C# 與 Word 物件模型概念
* 如 Visual Studio 或 VS Code 等開發環境

## 步驟 1：建立專案並匯入命名空間

建立一個新的主控台應用程式，並加入 Aspose.Words 套件：

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

在 `Program.cs` 中匯入所需的命名空間：

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **小技巧：** 使用最新的 Aspose.Words 版本，可取得 `Forms2OleControl` API 的完整支援。

## 步驟 2：建立空白文件並初始化 DocumentBuilder

`Document` 類別代表 Word 檔案，而 `DocumentBuilder` 提供插入內容的方法。

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` 的運作方式類似游標；在這行程式碼之後，您即可在文件的任意位置放置元素。

## 步驟 3：定義按鈕的位置與大小

Word 以點 (pt) 為單位測量座標（1 pt ≈ 1/72 in）。`System.Drawing` 的 `Rectangle` 結構描述控制項的邊界。

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` 會將控制項放在目前頁面的左上角。
* 調整 `x` 與 `y` 即可將按鈕移至其他位置（例如 `new Rectangle(150, 200, 100, 30)`）。

## 步驟 4：插入 Forms2Ole 指令按鈕

現在使用 `InsertForms2OleControl` 來加入控制項。此方法需要控制項類型、名稱以及前述的邊界。

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

回傳的 `Forms2OleControl` 物件讓您可以修改屬性，例如 `Enabled`、`Visible`，或稍後再指定巨集名稱。

### 為什麼使用 Forms2Ole？

* **相容舊版** – Forms2Ole 控制項在 Word 97‑2003（`.doc`）以及較新的 `.docx` 檔案中皆可運作。
* **巨集支援** – 可觸發 VBA 巨集，適合製作互動式範本。
* **精確定位** – 與內容控制項不同，您可以自行決定確切座標。

## 步驟 5：儲存文件

最後，將檔案寫入磁碟。請選擇您有寫入權限的資料夾。

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

在 Microsoft Word 中開啟 `output.docx`。您會看到第一頁左上角出現標示為 **ClickMe** 的按鈕。此按鈕在 Word 中點擊不會有任何動作，除非您指派巨集，但控制項已完整可用。

## 處理常見邊緣案例

| 情境 | 處理方式 |
|-----------|-------------------|
| **按鈕出現在頁面之外** | 確認 `Rectangle` 座標落在頁面邊界內。可使用 `builder.PageSetup.PageWidth` 與 `PageHeight` 計算安全範圍。 |
| **舊版 Word 看不到控制項** | 將文件另存為 `.doc`（`doc.Save("output.doc", SaveFormat.Doc)`），即可保證 Forms2Ole 在 Word 97‑2003 中相容。 |
| **需要變更標題文字** | 插入後設定 `commandButton.Caption = "Submit";`。 |
| **指派巨集** | 設定 `commandButton.MacroName = "MyMacro"`；巨集必須已存在於文件的 VBA 專案中。 |
| **多個按鈕** | 以不同的 `Rectangle` 值與唯一名稱重複步驟 4。 |

## 完整可執行範例

將所有步驟整合後，以下是一個可直接複製、貼上並執行的完整程式：

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**預期結果：** 執行程式後，`output.docx` 於 Word 中開啟，會在第一頁左上角顯示一個標示為 *Click Me!* 的可點擊按鈕。

## 結論

現在您已掌握如何使用 C# 與 Aspose.Words **在 Word 中插入 Forms2Ole 控制項**。此流程包括建立 `Document`、定位 `Rectangle`，以及透過 `DocumentBuilder` 呼叫 `InsertForms2OleControl`。有了完整的程式碼範例與邊緣案例說明，您可以將指令按鈕整合至任何自動化的 Word 工作流程中。

### 往後的步驟

* 探索其他 `ControlType` 如 `CheckBox` 或 `OptionButton`。
* 結合 Forms2Ole 控制項與 VBA 巨集，打造互動式表單。
* 使用 `DocumentBuilder.MoveTo` 將按鈕放置於特定段落或表格內。
* 參閱 Aspose.Words 的 **Forms2Ole** 文件，了解進階屬性設定。

祝開發順利，盡情打造更豐富的 Word 文件！

## 接下來您可以學習什麼？

以下教學與本指南緊密相關，能在此基礎上延伸技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並探索在專案中實作的其他方式。

- [How to insert OLE command button in a Word document using C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [how to add activex control in Word with Aspose.Words – step‑by‑step guide](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}