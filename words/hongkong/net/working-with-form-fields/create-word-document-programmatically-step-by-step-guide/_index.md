---
category: general
date: 2026-08-04
description: 使用 C# 程式化建立 Word 文件。學習如何以程式方式在 Aspose.Words 中加入指令按鈕，只需幾個步驟。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: zh-hant
lastmod: 2026-08-04
og_description: 使用 Aspose.Words 程式化建立 Word 文件。本指南示範如何以程式方式加入指令按鈕、設定其屬性，並儲存檔案。
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: 以程式方式建立 Word 文件 – 完整 C# 教學
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 以程式方式建立 Word 文件 – 逐步指南
url: /zh-hant/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 程式化建立 Word 文件 – 完整 C# 教程

如果你需要 **程式化建立 Word 文件**，本指南會向你展示如何使用 Aspose.Words for .NET 完成。只需幾行 C# 程式碼，即可產生空白的 `.docx` 檔案，**程式化新增 command button** 控制項，設定其屬性，並儲存結果。  

以下步驟涵蓋從專案設定到處理邊緣案例的全部內容，讓你可以直接將程式碼複製到自己的應用程式中執行，且不需任何修改。

## 你將能達成的目標

完成本教學後，你將能夠：

* 在記憶體中全新初始化一個 Word 文件。  
* **程式化新增 command button** OLE 控制項，並可自行設定位置與大小。  
* 設定按鈕的說明文字、內部名稱以及其他 OLE 屬性。  
* 將產生的文件儲存至磁碟或串流，以便後續處理。

### 前置條件

* .NET 6.0 或更新版本（此程式碼亦相容 .NET Framework 4.6+）。  
* 有效的 Aspose.Words for .NET 授權（或免費評估版）。  
* 具備基本的 C# 與 Visual Studio（或任意你慣用的 IDE）知識。  

> **專業提示：** 若在未套用授權的情況下執行範例，Aspose.Words 會在第一頁加入小型評估浮水印。

## Step 1: 設定專案並匯入必要的命名空間

建立一個新的 Console App（或整合至既有服務），並加入 Aspose.Words NuGet 套件：

```bash
dotnet add package Aspose.Words
```

接著在 `.cs` 檔案的最上方加入必要的命名空間：

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

這些匯入讓你可以使用 `Document`、`DocumentBuilder`、`Forms2OleControl` 以及用於定位的 `RectangleF` 結構。

## Step 2: 初始化全新的 Word 文件

在任何 **程式化建立 Word 文件** 工作流程中，第一件事就是建立 `Document` 物件。此物件僅存在於記憶體中，直到你明確儲存為止。

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` 如同一支游標，會追蹤下一個元素要放置的位置。使用它可以讓程式碼更簡潔，也與直接在 Word 中輸入的感覺相近。

## Step 3: 插入 command button OLE 控制項

Aspose.Words 提供 `InsertForms2OleControl` 方法，可嵌入 OLE 物件（例如 command button、核取方塊或下拉式選單）。此方法需要三個參數：

1. `ControlType` 列舉值（此處為 `CommandButton`）。  
2. 定義控制項 X‑Y 位置與寬高的 `RectangleF`（單位為點，72 pt = 1 inch）。  
3. （可選）其他 OLE 屬性（基本按鈕不需要）。

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **為什麼這樣可行：** `InsertForms2OleControl` 會在文件中建立一個 OLE 容器，並回傳 `Forms2OleControl` 包裝物件。透過此包裝物件，你可以在不直接操作 COM 互操作的情況下，操控底層的 OLE 物件（即實際的按鈕）。

## Step 4: 設定按鈕的說明文字與內部名稱

插入之後，通常會為按鈕設定使用者可見的標籤以及供巨集或外掛參照的內部識別名稱。

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` 為按鈕在 Word 介面上顯示的文字。  
* `Name` 為 VBA 或外部自動化腳本使用的程式化識別名稱。

### 可選：為按鈕指派巨集

如果希望在按鈕被點擊時執行 VBA 巨集，可將巨集名稱附加上去：

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **邊緣案例：** 若目標文件在沒有安裝該巨集的機器上開啟，Word 會顯示安全性警告。請務必為巨集簽章，或事先告知使用者所需的設定。

## Step 5: 儲存文件

你可以將檔案寫入磁碟、`MemoryStream`，或直接回傳給 Web API 的回應物件。對於 Console 示範而言，最簡單的方式是儲存至本機資料夾：

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

產生的 `.docx` 於 Microsoft Word 開啟時，會出現一個功能正常的 command button，顯示文字「Click Me」。點擊按鈕會觸發已指派的巨集（若有），或僅顯示預設訊息。

## 完整範例程式

將以下程式碼貼入 `Program.cs` 並執行，即可看到完整的 **程式化建立 Word 文件** 流程，並包含錯誤處理。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**預期結果：** 在 Word 中開啟 `CommandButton.docx` 時，會看到標示為「Click Me」的按鈕。將滑鼠移到按鈕上時，屬性窗格會顯示名稱 `cmdClickMe`。

## 常見問題與除錯

| 問題 | 解答 |
|----------|--------|
| *我可以將按鈕加入到既有文件嗎？* | 可以。使用 `new Document("Existing.docx")` 載入檔案後，直接呼叫相同的 `InsertForms2OleControl` 即可。 |
| *`RectangleF` 使用什麼單位？* | 點 (Points)。1 inch = 72 pt。依需求調整數值即可精確定位按鈕。 |
| *按鈕在 Mac 版 Word 能正常運作嗎？* | OLE 控制項僅支援 Windows 版 Word。於 Mac 上會顯示為靜態圖片。 |
| *正式上線需要授權嗎？* | 商業授權會移除評估浮水印，並解鎖全部功能。 |
| *插入後要如何變更按鈕大小？* | 可修改 `commandButton.Width` 與 `commandButton.Height`，或以新的 `RectangleF` 重新插入。 |

## 延伸應用

既然已掌握 **程式化新增 command button** 控制項，你可以進一步探索以下相關主題：

* **插入其他表單控制項** – 使用 `ControlType.CheckBox`、`ControlType.OptionButton` 等（涵蓋次要關鍵字 *Aspose.Words InsertForms2OleControl*）。  
* **以動態資料填充文件** – 從資料庫合併資料至表格或郵件合併欄位。  
* **匯出為 PDF** – 在加入按鈕後，呼叫 `doc.Save("output.pdf", SaveFormat.Pdf)` 產生 PDF（與 *C# Word automation* 相關）。  

## 結論

現在你已擁有一套完整且可投入生產環境的 **程式化建立 Word 文件** 與 **程式化新增 command button** 解決方案，全部使用 Aspose.Words for .NET 完成。本文涵蓋了專案設定、文件初始化、OLE 按鈕插入、屬性設定與檔案儲存等步驟。未來可自行擴充插入其他表單控制項、附加巨集，或將此邏輯整合至 Web 服務或背景工作。

祝開發順利，盡情自動化你的 Word 文件吧！

## 接下來該學什麼？

以下教學與本篇內容密切相關，能幫助你進一步掌握 API 功能，並在專案中探索其他實作方式：

- [使用 Aspose.Words 建立 Word 文件 – 步驟教學](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [使用 Aspose.Words 以表格建立 Word 文件](/words/english/net/add-content-using-document-builder/build-table/)
- [使用 Aspose.Words for .NET 在 Word 文件中建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}