---
category: general
date: 2026-09-14
description: 使用 C# 在 Word 文件中建立 ActiveX 控制項。學習如何插入 ActiveX、加入互動按鈕，並以程式方式產生 .docx 檔案。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: zh-hant
lastmod: 2026-09-14
og_description: 使用 C# 在 Word 文件中建立 ActiveX 控制項。跟隨此完整範例，插入 ActiveX、加入互動按鈕，並儲存檔案。
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: 使用 C# 在 Word 中建立 ActiveX 控制項 – 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: 如何使用 C# 在 Word 文件中建立 ActiveX 控制項
url: /zh-hant/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 C# 建立 ActiveX 控制項

如果您需要在 Microsoft Word 檔案中 **建立 ActiveX 控制項**，本指南會提供完整、可直接執行的解決方案。您將會看到如何插入 ActiveX CommandButton、設定其屬性，並僅使用 C# 程式碼儲存產生的 `.docx` 檔案。

在 Word 文件中加入互動按鈕是常見需求，尤其當您希望最終使用者能直接從文件介面觸發巨集或自訂邏輯時。以下範例示範 **如何插入 ActiveX**，且不依賴第三方工具，同時也說明 **如何以程式方式建立 Word 文件**。

完成本教學後，您將能夠 **以程式碼建立按鈕**、自訂其標題，並產生可攜帶且保留 ActiveX 控制項的 Word 檔案。

## 前置條件

- .NET 6.0 或更新版本（Aspose.Words for .NET 函式庫支援 .NET Core 與 .NET Framework）
- 參考 `Aspose.Words` NuGet 套件  
  ```bash
  dotnet add package Aspose.Words
  ```
- 具備 C# 及物件導向程式設計的基本知識

## 步驟 1：設定專案並匯入命名空間

建立一個新的 Console 專案（或將程式碼整合至任何現有的 C# 應用程式）。匯入必要的命名空間，使編譯器能找到 Word 處理相關的類別。

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **為何此步驟重要** – `Aspose.Words` API 提供 `Document`、`DocumentBuilder` 與 `Forms2OleControl` 類別，讓您能在物件層級操作 Word 檔案。若缺少這些參考，其他程式碼將無法編譯。

## 步驟 2：建立新的 Word 文件與 DocumentBuilder

`Document` 物件代表整個 `.docx` 套件，而 `DocumentBuilder` 提供流暢的 API 以插入內容。

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **說明** – 建立全新的 `Document` 可獲得乾淨的畫布。Builder 的游標會位於第一個區段的開頭，隨時準備插入內容。

## 步驟 3：插入 ActiveX CommandButton

使用 `InsertForms2OleControl` 在指定位置放置 ActiveX 控制項。此方法需要控制項類型，並傳入定義 X/Y 座標與大小（以點為單位）的 `RectangleF`。

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **為何這樣可行** – `OleControlType.CommandButton` 告訴 API 建立標準的 Windows CommandButton。矩形會相對於頁面的左上角定位按鈕，讓您能在需要的位置 **加入互動按鈕**。

## 步驟 4：設定按鈕屬性

現在設定按鈕的顯示文字 (`Caption`) 與內部名稱 (`Name`)。這些屬性是使用者看到的文字，也是 VBA 程式碼之後可參照的名稱。

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **實用小技巧** – `Name` 必須在文件內唯一；否則 VBA 巨集可能會參照到錯誤的控制項。

## 步驟 5：儲存文件

最後，將檔案寫入磁碟。ActiveX 控制項會儲存在 Word 套件內，因此儲存的檔案在 Microsoft Word 中開啟時仍保有完整功能。

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **結果** – 在 Word 中開啟 `CommandButton.docx` 後會看到一個標示為「Click Me」的可點擊 CommandButton。可透過 Word 介面（`Developer → Design Mode → Properties`）將此控制項連結至巨集。

## 完整程式碼清單

將所有步驟整合即可得到一個可直接複製、貼上並執行的完整程式。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### 預期輸出

執行程式會在主控台印出確認訊息：

```
Document saved to C:\Temp\CommandButton.docx
```

當您在 Microsoft Word 中開啟產生的檔案時，會看到一個位於指定座標的 **CommandButton**。在設計模式下點擊會將其選取；在執行模式下則會像一般的 ActiveX 按鈕一樣運作。

## 常見變化與邊緣情況

| Scenario | Adjustment |
|----------|------------|
| **不同的控制項類型** | 將 `OleControlType.CommandButton` 替換為 `OleControlType.CheckBox`、`OleControlType.OptionButton` 等。 |
| **多個按鈕** | 重複呼叫 `InsertForms2OleControl`，並為每個新按鈕更新 `RectangleF` 座標。 |
| **動態尺寸** | 根據頁面大小（`builder.PageSetup.PageWidth`）計算矩形尺寸。 |
| **儲存至串流** | 當需要從 Web API 回傳檔案時，使用 `document.Save(stream, SaveFormat.Docx)`。 |
| **Word 97‑2003 格式** | 將儲存格式改為 `SaveFormat.Doc`，即可產生仍嵌入 ActiveX 控制項的 `.doc` 檔案。 |

> **專業提示**：務必在目標版本的 Word 上測試產生的文件，因為較舊的版本可能預設啟用安全設定，導致 ActiveX 控制項被停用。

## 常見問與答

**這能在 .NET Core 上運作嗎？**  
是的。Aspose.Words 函式庫是跨平台的，完全相容於 .NET Core 以及 .NET 5/6+。

**我能以程式方式為按鈕指派巨集嗎？**  
API 無法直接嵌入 VBA 程式碼。文件產生後，請在 Word 中開啟，啟用 Developer 標籤，然後錄製或撰寫參考 `btnClick` 的巨集。

**如果按鈕沒有顯示該怎麼辦？**  
請確認 Word 已啟用 `Developer` 標籤，且文件未以 **受保護檢視** 開啟。同時檢查矩形座標是否在頁面邊界內。

## 結論

您現在已掌握如何使用 C# 在 Word 檔案中 **建立 ActiveX 控制項**。本教學說明了 **如何插入 ActiveX**、示範了 **加入互動按鈕**、展示了 **從頭建立 Word 文件**，以及說明了 **以程式碼建立按鈕** 並在儲存後仍能保留。  

接下來，您可以探索其他 ActiveX 類型、將按鈕連結至 VBA 巨集，或將此邏輯嵌入更大的文件產生服務中。嘗試不同的尺寸、位置與控制項屬性，以符合您所需的使用者體驗。

---

## 接下來該學什麼？

以下教學涵蓋與本指南技術密切相關的主題，並以步驟說明與完整可執行的程式碼範例，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [建立新 Word 文件](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [在 Word 文件中建立 VBA 專案](/words/english/net/working-with-vba-macros/create-vba-project/)
- [在 Aspose.Words for .NET 中建立與樣式化 Word 文件](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}