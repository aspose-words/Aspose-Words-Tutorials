---
category: general
date: 2026-08-17
description: 使用 Aspose.Words 在 Word 中插入 OleControlType.CommandButton 範例。了解如何以程式方式向
  Word 文件中加入表單控制項。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: zh-hant
lastmod: 2026-08-17
og_description: 使用 Aspose.Words 在 Word 中插入 OleControlType.CommandButton 範例。請參考本指南，將表單控制項加入
  Word 文件。
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: 在 Word 中插入 OleControlType.CommandButton 範例
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: 於 Word 中插入 OleControlType.CommandButton 範例
url: /zh-hant/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中插入 OleControlType.CommandButton 範例

如果您需要在 Word 檔案中 **insert OleControlType.CommandButton example**，本指南將向您展示如何操作。您將學習使用 Aspose.Words **how to add form controls to a Word document**，並提供完整可執行的 C# 程式。

ActiveX 按鈕等表單控制項讓您能建立互動式 Word 範本——適用於合約、問卷或內部工具。以下步驟涵蓋從專案設定到驗證已儲存的 `.docx` 檔案中按鈕正確顯示的全部內容。

## 前置條件

- .NET 6.0 SDK 或更新版本已安裝  
- Visual Studio 2022（或任何 C# IDE）  
- Aspose.Words for .NET 授權或免費暫時授權  
- 具備 C# 與 Word 檔案概念的基本知識  

> **小技巧：** 如果您使用免費試用版，請將授權檔案放在與可執行檔相同的資料夾，並在 `Main` 開始時載入它。

## 步驟 1：建立新控制台專案並加入 Aspose.Words

在終端機中執行以下指令：

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

此指令會建立一個乾淨的專案，並取得最新的 Aspose.Words 套件，該套件提供執行 **insert OleControlType.CommandButton example** 所需的 `Document`、`DocumentBuilder` 與 `InsertForms2OleControl` API。

## 步驟 2：撰寫完整程式

建立或取代 `Program.cs`，內容如下。它包含所有必要的 `using` 指令、授權載入，以及原始範例中顯示的四步工作流程。

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### 為何每一行都很重要

* **License loading** – 確保您不會受到評估版限制。  
* **`Document doc = new Document();`** – 建立容納所有 Word 內容的容器；這是 **insert OleControlType.CommandButton example** 的基礎。  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – 提供流暢的 API 以加入文字、圖片與控制項。  
* **`InsertForms2OleControl`** – 實作 **how to add form controls to a Word document** 的核心方法。`OleControlType.CommandButton` 列舉值告訴 Aspose.Words 建立 ActiveX 按鈕。  
* **`new Rectangle(100, 100, 80, 30)`** – 將按鈕定位於左、上邊距各 100 點，寬 80 點、高 30 點。可依版面需求調整這些數值。  
* **`doc.Save`** – 將 .docx 檔寫入磁碟；檔案現在包含嵌入的按鈕。

## 步驟 3：建置並執行程式

在專案資料夾中執行以下指令：

```bash
dotnet run
```

您應該會看到以下主控台訊息：

```
Document saved to ActiveXButton.docx
```

在 Microsoft Word 中開啟 `ActiveXButton.docx`。您會看到一個標示為 **ClickMe** 的按鈕，大致位於頁面中央。點擊該按鈕會觸發預設的 ActiveX 行為（除非您附加巨集，否則通常不會執行任何操作）。

![插入 olecontroltype.commandbutton 範例](/images/activex-button.png "已在 Word 文件中插入 ActiveX CommandButton")

*圖片說明文字:* insert olecontroltype.commandbutton example – 在 Word 文件中顯示的 ActiveX CommandButton。

## 步驟 4：自訂按鈕（可選）

基本的 **insert OleControlType.CommandButton example** 會建立預設按鈕。您可以透過編輯底層 OLE 物件來修改其標題、字型，甚至附加巨集。以下示範在插入後變更按鈕標題的簡潔方法：

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **注意：** 直接操作 OLE 屬性需要了解底層 COM 介面。對於大多數情況，預設標題已足夠。

## 步驟 5：常見問題與避免方法

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| 按鈕未在 Word 中顯示 | 文件已儲存為 `.docx`，但在會剝除 OLE 控制項的檢視器中開啟（例如 Google Docs）。 | 使用 Microsoft Word 或具編輯權限的 Word Online 開啟檔案。 |
| 執行時錯誤 `ArgumentOutOfRangeException` | `Rectangle` 座標超出頁面邊距。 | 使用頁面尺寸內的數值（例如 A4 的 0‑500）。 |
| 授權例外 | 試用授權在 30 天後過期。 | 載入有效的授權檔案，或向 Aspose 申請延長試用。 |

## 步驟 6：此範例在大型自動化專案中的應用

當您需要在大規模上 **how to add form controls to Word document**（例如產生數百份合約範本）時，請將插入邏輯封裝成可重複使用的方法：

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

之後您可以在處理資料列的迴圈中呼叫 `AddCommandButton`，確保每個產生的文件都包含唯一命名的按鈕（例如 `Approve_001`、`Approve_002`）。

## 結論

您現在已擁有完整的 **insert OleControlType.CommandButton example**，示範如何使用 Aspose.Words for .NET **how to add form controls to a Word document**。本教學涵蓋了專案設定、完整原始碼、自訂技巧以及常見故障排除步驟。

接下來您可以探索：

- 加入其他控制項類型，例如 **CheckBox** 或 **ComboBox**（`OleControlType.CheckBox`、`OleControlType.ComboBox`）。  
- 將按鈕綁定至 VBA 巨集，以獲得更豐富的互動性。  
- 從相同文件產生 PDF，同時保留表單欄位。

嘗試不同的尺寸、位置與控制項名稱，以符合您的特定使用情境。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可運作的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [在 Word 文件中插入下拉式方塊表單欄位](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [在 Word 文件中插入核取方塊表單欄位](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [在 Word 文件中插入文字輸入表單欄位](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}