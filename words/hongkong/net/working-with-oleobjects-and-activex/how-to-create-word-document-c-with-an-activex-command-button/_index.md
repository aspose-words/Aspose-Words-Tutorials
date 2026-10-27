---
category: general
date: 2026-10-26
description: 學習如何使用 C# 建立 Word 檔案，並以程式方式加入 ActiveX 按鈕。本分步指南涵蓋插入命令按鈕、於設計時隱藏按鈕，以及儲存檔案。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: zh-hant
lastmod: 2026-10-26
og_description: 使用 C# 建立 Word 文件，並以程式方式加入 ActiveX 按鈕。請參考此完整教學，嵌入僅在執行時顯示的指令按鈕。
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: 使用 C# 建立 Word 文件與 ActiveX 命令按鈕 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: 如何在 C# 中建立帶有 ActiveX 命令按鈕的 Word 文件
url: /zh-hant/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 ActiveX 命令按鈕在 C# 中建立 Word 文件

如果你需要 **create Word document C#** 並在其中加入互動按鈕，本指南將一步步說明。閱讀前兩句即可了解整體做法，接下來的步驟會帶你走過每一行必寫的程式碼。

你將學會如何加入 ActiveX 按鈕、在設計階段隱藏它，並僅在使用者開啟檔案時顯示。教學亦涵蓋常見的安全警告與版本相容性問題，讓你能交付可靠的文件。

## 前置條件

開始之前，請確保你已具備：

* 已安裝 .NET 6.0 或更新版本  
* 取得 **Aspose.Words for .NET** 的授權版（免費試用版可用於實驗）  
* 具備 C# 與 Visual Studio（任何支援 .NET 的 IDE） 的基本概念  

除 `Aspose.Words` 之外，無需額外的 NuGet 套件。

## 步驟 1：建立 Word 文件 C# 並初始化 DocumentBuilder

第一步是建立 `Document` 物件與 `DocumentBuilder`。`Document` 代表整個 .docx 檔案，而 `DocumentBuilder` 提供流暢的方式加入內容。

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**為什麼重要：** 若沒有 `DocumentBuilder`，你必須手動操作 OpenXML DOM，容易出錯且難以閱讀。Builder 抽象化這些細節，保證產生結構正確的 Word 檔案。

## 步驟 2：加入 ActiveX 按鈕 – 插入 CommandButton 控制項

現在在特定位置插入 **CommandButton ActiveX 控制項**。矩形 (Rectangle) 定義按鈕的座標 (X、Y) 與尺寸 (寬度、高度)，單位為點 (points)。

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**為什麼重要：** `InsertForms2OleControl` 是唯一的 Aspose.Words 方法可建立真正的 ActiveX OLE 物件。`Forms2OleControlType.CommandButton` 列舉值告訴 Word 嵌入可點擊的按鈕，而非一般的 OLE 容器。

## 步驟 3：以程式方式加入命令按鈕 – 在執行前隱藏

Word 預設會將任何插入的圖形設為可見。為了在設計模板時不顯示按鈕，請對剛建立的圖形設定 `Hidden` 屬性。

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**為什麼重要：** 設定 `Hidden = true` 可避免按鈕在設計檢視中佔據空間。當文件在 Word 中開啟時，執行環境會自動顯示該控制項，保留預期的使用者體驗。

## 步驟 4：儲存檔案 – 建立 command button word document

最後，將文件寫入磁碟。選擇應用程式有寫入權限的路徑，並使用 `.docx` 副檔名以確保現代相容性。

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**為什麼重要：** 以 `.docx` 儲存可確保嵌入的 ActiveX 控制項符合 Office Open XML 標準，支援 Word 2007 及之後版本。若需相容舊版 `.doc`，只要改副檔名並使用 `SaveFormat.Doc` 即可。

## 完整範例

以下為完整程式碼，可直接複製、貼上並執行：

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**預期結果：** 執行程式後，於 Microsoft Word 開啟 `C:\Temp\ActiveX.docx`。你會看到空白文件，設計模式下按鈕不會顯示。按 **Alt + F9** 切換欄位代碼，然後點擊按鈕區域——Word 會呈現 ActiveX 控制項，且可互動（例如雙擊檢視屬性）。

## 邊緣情況與最佳實踐技巧

| 情境 | 需要留意的地方 | 推薦解決方式 |
|-----------|-------------------|-----------------|
| **使用者停用 ActiveX** | Word 可能顯示安全警告或封鎖控制項。 | 指示最終使用者在「信任中心」啟用「ActiveX 控制項」，或提供已簽署的巨集替代方案。 |
| **文件在 Word Online 開啟** | Word Online 不支援 ActiveX，按鈕會被省略。 | 若需雲端相容性，可改用超連結或內容控制項作為備援。 |
| **不同 DPI 設定** | 矩形尺寸在高 DPI 顯示器上可能變大或變小。 | 使用 `GraphicsUnit.Point`（預設），並在常見 DPI（96 dpi、120 dpi）下測試。 |
| **多個按鈕** | `GetChildNodes(NodeType.Shape, true)[0]` 只會取得第一個圖形。 | 迭代 `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)`，為每個新增的圖形設定 `Hidden`。 |
| **舊版 .doc 格式** | 儲存為 `.doc` 時部分 ActiveX 屬性會遺失。 | 除非有嚴格的舊版需求，否則建議使用 `.docx`。 |

**小技巧：** 插入按鈕後，可透過 Word UI 為其 `OnAction` 屬性指派巨集，讓你在不寫額外 C# 程式碼的情況下自訂點擊行為。

## 常見問答

* **這能在 .NET Core 上運作嗎？**  
  可以。Aspose.Words for .NET 完全相容 .NET 5、.NET 6 以及更新版本，只要引用相同的 NuGet 套件即可。

* **產生文件後，我可以變更按鈕文字嗎？**  
  `InsertForms2OleControl` 設定的文字是設計時的預設標題。使用者可在 Word 中自行編輯，亦可透過 `Shape.OleFormat` API 以程式方式更新 OLE 物件的屬性。

* **如果需要不同大小的按鈕該怎麼做？**  
  調整 `RectangleF` 的數值。前兩個參數是 X、Y 座標，後兩個是寬度與高度（單位為點，1 pt = 1/72 英吋）。

## 結論

現在你已掌握如何 **create Word document C#** 並使用 Aspose.Words **programmatically add command button**。本教學說明了文件初始化、插入 ActiveX 按鈕、在執行前隱藏以及最終儲存的完整流程。利用這些基礎，你可以在任何自動產生的 Word 範本中嵌入互動控制項。

接下來，可進一步探索 **how to add ActiveX button** 事件處理、**create command button word** 的 VBA 樣式設定，以及 **programmatically add command button** 到既有文件的技巧。將此模式延伸至核取方塊、下拉式選單或自訂 OLE 物件，只需更換 `Forms2OleControlType` 列舉值即可。

開始實驗吧：改變標題、調整位置，或串接多個控制項。練習越多，你就能更流暢地從 C# 產出豐富、互動的 Word 文件。祝開發順利！

## 接下來該學什麼？

以下教學與本指南的技術緊密相關，能幫助你進一步掌握 API 功能並探索其他實作方式：

- [How to add a command button programmatically in a Word document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}