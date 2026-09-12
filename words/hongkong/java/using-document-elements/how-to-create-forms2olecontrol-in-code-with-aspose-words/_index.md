---
category: general
date: 2026-09-11
description: 學習如何使用 Aspose.Words DocumentBuilder 在程式碼中建立 forms2olecontrol。此一步一步的指南涵蓋
  ActiveX 命令按鈕插入、setOleClassName 的使用以及尺寸設定。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: zh-hant
lastmod: 2026-09-11
og_description: 在程式碼中使用 Aspose.Words 建立 forms2olecontrol。請依照本指南插入 ActiveX 指令按鈕、設定其類別名稱，並調整其大小。
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: 在程式碼中建立 forms2olecontrol – 完整的 Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: 如何在程式碼中使用 Aspose.Words 建立 forms2olecontrol
url: /zh-hant/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在程式碼中使用 Aspose.Words 建立 forms2olecontrol

如果您需要 **在程式碼中建立 forms2olecontrol**，本指南將向您展示如何使用 Aspose.Words .NET API 完成此操作。無論您是要自動化需要 ActiveX 命令按鈕的範本，或只是想以程式方式豐富 Word 文件，以下步驟皆涵蓋從插入控制項到設定外觀的全部內容。

在本教學中，您將學會如何使用 **Aspose.Words DocumentBuilder** 插入 **ActiveX command button**、使用 **setOleClassName method** 設定其類別，並調整 **Forms2OleControl size**。不需要任何外部工具——只要有 .NET 開發環境與 Aspose.Words 程式庫即可。

## 前置條件

開始之前，請確保您已具備：

* 已安裝 .NET 6.0 或更新版本（此程式碼亦相容 .NET Framework 4.7+）
* 最近版本的 Aspose.Words for .NET NuGet 套件
* 基本的 C# 使用經驗，以及了解 Word 文件中 ActiveX 控制項的概念

若缺少上述任一項，請使用以下指令安裝 NuGet 套件：

```bash
dotnet add package Aspose.Words
```

## 本教學涵蓋內容

* 建立 `DocumentBuilder` 實例
* 插入 `Forms2OleControl`（ActiveX 命令按鈕的底層物件）
* 使用 `setOleClassName` 指定正確的類別名稱
* 使用 **Forms2OleControl size** 屬性設定視覺寬度與高度
* 儲存文件並驗證結果

完成本教學後，您將擁有一個可點擊的按鈕，能進一步自訂或綁定至 VBA 巨集。

---

## 如何在程式碼中建立 forms2olecontrol – 步驟說明

### 步驟 1：初始化 DocumentBuilder

`DocumentBuilder` 類別是 Aspose.Words 大多數文件產生工作流程的入口點。它提供了加入文字、圖片、表格，以及本教學最關鍵的 OLE 控制項的方法。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**為何重要：**  
`DocumentBuilder` 會維持文件內目前的游標位置。提前建立它，可確保之後的任何插入（例如 **ActiveX command button**）正好出現在您想要的位置。

### 步驟 2：插入 Forms2OleControl

`insertForms2OleControl` 方法會回傳一個 `Forms2OleControl` 物件。此物件代表 Word 會以 ActiveX 按鈕形式呈現的 OLE 控制項佔位符。

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**為何重要：**  
若未呼叫此方法，您將無法操作控制項的屬性。回傳的 `Forms2OleControl` 讓您完整存取 **setOleClassName method**、大小屬性以及其他 OLE 專屬設定。

### 步驟 3：使用 setOleClassName 指定 ActiveX 類別

Word 必須知道要呈現哪種類型的 ActiveX 控制項。標準命令按鈕的類別名稱為 `"Forms.CommandButton.1"`。

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**為何重要：**  
`setOleClassName` 方法是將通用 OLE 佔位符轉換為具體 **ActiveX command button** 的橋樑。若類別名稱錯誤，文件開啟時會出現空白物件或執行時錯誤。

### 步驟 4：調整 Forms2OleControl 大小

按鈕過小或過大都會顯得不專業。您可以使用 `setWidth` 與 `setHeight` 來控制其尺寸。

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**為何重要：**  
這些屬性構成 **Forms2OleControl size**。它們影響按鈕在 Word UI 中的顯示方式，並確保任何附加的巨集都有足夠的點擊區域。

### 步驟 5：儲存文件並測試

設定完控制項後，將文件儲存至您指定的位置。

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

在 Microsoft Word 中開啟 `ActiveXButton.docx`。您應該會看到一個標示為 “CommandButton1”（預設標題）的按鈕。若未加入 VBA 巨集，點擊它不會有任何動作，但控制項本身已完全可用。

**預期輸出：**  

![插入 ActiveX 命令按鈕的 Word 文件](/images/activeX-button.png "顯示透過程式碼插入新建 ActiveX 命令按鈕的 Word 文件截圖")

*此圖片的 alt 文字包含主要關鍵字，以提升可及性與 SEO。*

## 了解 ActiveX Forms2OleControl 類別

`Forms2OleControl` 類別封裝了 Word 用於 ActiveX 元素的低階 OLE 基礎設施。它繼承自 `Shape`，因此您亦可對其套用一般圖形的格式設定（例如邊框、旋轉）如有需要。

* **ActiveX command button** – 最常見的使用情境；可透過 Word 開發者工具將其綁定至巨集。
* **setOleClassName method** – 決定 Word 載入哪個 COM 類別；其他有效值包括 `"Forms.TextBox.1"` 與 `"Forms.ComboBox.1"`。
* **Forms2OleControl size** – 透過 `SetWidth`/`SetHeight` 控制。這些方法接受點數（1 pt = 1/72 in）。

### 何時使用 Forms2OleControl 與 Content Controls 的比較

如果您只需要簡單的資料輸入（例如純文字欄位），Word 內建的 content controls 較為輕量。當您需要完整的 ActiveX 功能，如事件處理或自訂 VBA 互動時，請使用 `Forms2OleControl`。

---

## 設定其他屬性（可選）

雖然核心步驟已足以 **在程式碼中建立 forms2olecontrol**，但您通常會想微調按鈕的外觀或行為。

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**為何重要：**  
`SetOleData` 允許您直接將任意屬性值寫入 OLE 串流。這是自訂 **ActiveX command button** 而不必依賴 VBA 的最彈性方式。

## 常見問題與故障排除

| 症狀 | 可能原因 | 解決方法 |
|--------|--------------|-----|
| 按鈕顯示為灰色方框 | `setOleClassName` 傳入了錯誤的類別名稱 | 確認字串正好為 `"Forms.CommandButton.1"`（區分大小寫） |
| 大小未變更 | 在插入控制項之前設定了寬度/高度 | 請務必在 `InsertForms2OleControl` **之後** 呼叫 `SetWidth`/`SetHeight` |
| 文件開啟時拋出 “OLE object not found” 錯誤 | 缺少 Aspose.Words 授權（評估版可能限制 OLE） | 套用有效授權或使用具完整 OLE 支援的免費試用版 |
| 按鈕標題仍為 “CommandButton1” | 未使用 `SetOleData` 或巨集未讀取該屬性 | 使用 VBA 巨集讀取 `"Caption"` 屬性，或透過 Word UI 設定標題 |

## 完整、可執行的範例

以下是一個完整的主控台應用程式範例，您可以直接複製、貼上並執行。它示範了本教學中提及的所有步驟。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**各段落說明**

* **Using directives** – 載入 Aspose.Words 命名空間，以使用 `Document`、`DocumentBuilder` 與 `Forms2OleControl`。
* **Document creation** – 建立一個空的 Word 檔案。
* **InsertForms2OleControl** – 將 OLE 控制項放置於 builder 目前的游標位置。
* **SetOleClassName** – 告訴 Word 此控制項為 **ActiveX command button**。
* **SetWidth / SetHeight** – 調整 **Forms2OleControl size**，讓外觀更專業。
* **SetOleData (optional)** – 示範如何寫入額外屬性（例如標題）。
* **Save** – 將最終的 `.docx` 檔寫入磁碟。

執行程式 (`dotnet run`) 後開啟 `ActiveXButton.docx`，您應該會看到一個日後可連結至巨集的按鈕。

## 結論

您現在已掌握如何使用 Aspose.Words **在程式碼中建立 forms2olecontrol**，從初始化 `DocumentBuilder`、設定 **ActiveX command button** 的 `setOleClassName`，到控制其 **Forms2OleControl size**。此方法讓您能自動化複雜的 Word 文件、嵌入互動式 UI 元件，並將所有邏輯保留在程式內

## 接下來該學什麼？

以下教學與本指南示範的技巧密切相關，能進一步擴充您的 API 應用與實作方式。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您在專案中掌握更多功能。

- [如何使用 Aspose.Words for Java 的 DocumentBuilder 建立表單欄位並加入內容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [在 Word 文件中使用 Aspose.Words for .NET 建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words 在 Word 中建立矩形圖形 – 步驟說明指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}