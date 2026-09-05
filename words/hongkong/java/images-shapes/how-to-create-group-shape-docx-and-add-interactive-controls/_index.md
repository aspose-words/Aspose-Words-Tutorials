---
category: general
date: 2026-09-05
description: 學習如何建立群組形狀的 docx、插入 ActiveX 命令按鈕，並以完整的 C# 範例將 Markdown 載入 Word 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: zh-hant
lastmod: 2026-09-05
og_description: 建立群組形狀的 docx 檔案，插入 ActiveX 指令按鈕，並使用 C# 將 Markdown 載入 Word 文件。跟隨此一步一步的教學。
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: 建立群組形狀的 docx 並嵌入 ActiveX 控制項 – C# 指南
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: 如何在 C# 中建立群組形狀 docx 並加入互動控制項
url: /zh-hant/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中建立群組形狀 docx 並加入互動控制項

如果您需要以程式方式 **create group shape docx** 檔案，本指南會完整說明如何操作。您還會看到如何 **insert ActiveX command button** 控制項以及 **load Markdown into a Word document**，且不會失去底線格式。完成本教學後，您將擁有一個結合向量圖形、互動 UI 元素與 markdown 為基礎內容的完整功能 `.docx`。

本教學假設您已具備基本的 C# 開發環境，且已安裝 Aspose.Words for .NET 套件。無需額外工具——所有程式皆在標準的 .NET 主控台或桌面應用程式中執行。

## 前置條件

- .NET 6.0 SDK 或更新版本（程式碼亦相容 .NET Framework 4.7+）
- Aspose.Words for .NET（NuGet 套件 `Aspose.Words`）
- 若要測試簽署步驟，需一組有效的 X.509 憑證（`.pfx`）
- 一張圖片檔（例如 `logo.png`）與一個 markdown 檔（`sample.md`），放置於已知資料夾中

> **專業提示：** 將所有輸入檔案統一放在單一 *resources* 資料夾，可簡化相對路徑的使用。

## 第 1 步：設定專案並匯入命名空間

建立新的主控台專案，並加入必要的 `using` 指令。此區塊同時示範如何參考稍後會使用的 Aspose.Words 類別。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

`using` 陳述式讓您直接存取 `Document`、`DocumentBuilder`、`GroupShape`、`Forms2OleControl` 等在整個教學中會用到的型別。

## 第 2 步：**Create group shape docx** – 新增包含子元素的群組形狀

*群組形狀* 讓您將多個繪圖物件視為單一單元，便於一起移動或調整大小。

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**為什麼要使用群組形狀？**  
將矩形與橢圓群組後，使用者在 Word 中拖曳時可保持對齊。亦能簡化之後的操作，例如一次套用共同邊框或以程式方式搬移整個圖形。

## 第 3 步：插入純文字內容控制項（作為使用者輸入的佔位符）

內容控制項提供最終使用者一個結構化的文字輸入區域。佔位文字會在使用者開始輸入時消失。

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

`PlaceholderName` 屬性即 Word 以淡灰色顯示的提示文字。使用者可自行替換，底層 XML 仍保持良好結構。

## 第 4 步：**Insert ActiveX command button** – 為文件加入互動 UI

ActiveX 控制項仍受現代 Word 檔案支援，可觸發巨集或外部自動化。以下程式碼加入一個 *command button* 並設定其標題。

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**何時使用 ActiveX 按鈕？**  
若文件在依賴 VBA 巨集的企業環境中流通，ActiveX 按鈕可啟動巨集或外部應用程式。若需要純 HTML 互動，建議改用 *content controls* 搭配 *Office.js*。

## 第 5 步：插入隱藏圖片（例如商標）以供品牌或後續腳本存取

隱藏形狀不會在列印文件中顯示，但仍保留於 XML 中，讓您日後以程式方式取得。

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## 第 6 步：**Load markdown into a Word document** 同時保留底線格式

Aspose.Words 可直接匯入 Markdown。啟用 `ImportUnderlineFormatting` 後，markdown 底線（`<u>` 或 `__text__`）會轉為 Word 的底線樣式，而非純文字。

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**特殊情況：** 若 markdown 檔案包含表格，會自動轉換為 Word 表格。若需自訂表格樣式，可在插入後使用 `DocumentBuilder` 進行調整。

## 第 7 步：使用 XAdES‑EPES 簽署文件（可選的安全步驟）

數位簽章可保證文件完整性。以下程式碼使用 XAdES‑EPES 設定簽署 **create group shape docx** 檔案。

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **安全說明：** 請將憑證密碼排除於原始碼管理之外。於正式環境建議使用環境變數或安全保管庫。

## 完整可執行範例

將所有步驟整合，即可得到一個單一、獨立的程式。將檔案儲存為 `Program.cs`，於命令列執行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

執行程式後會產生 `CompleteGroupShape.docx`，內容包括：

- 一組矩形 + 橢圓（**create group shape docx** 的核心）
- 含佔位文字的純文字內容控制項
- 標示為「Click Me」的 **insert ActiveX command button**
- 隱藏的商標圖片
- 保留底線的 Markdown 內容
- 若提供憑證，則加入 XAdES‑EPES 數位簽章

## 常見問題與故障排除

| 問題 | 解答 |
|---|---|
| **ActiveX 按鈕在 macOS 版 Word 能使用嗎？** | macOS 版 Word 不支援 ActiveX 控制項，按鈕會顯示為靜態圖片。建議改用搭配 Office.js 的內容控制項，以達跨平台互動。 |
| **如果 markdown 檔案包含自訂 CSS 該怎麼辦？** | Aspose.Words 會忽略 CSS，只會處理標準的 markdown 語法。需在匯入後自行將 CSS 樣式轉換為 Word 樣式。 |
| **之後可以再向同一個群組加入更多形狀嗎？** | 可以。透過名稱或索引取得 `GroupShape`，再呼叫 `AppendChild(newShape)`。修改後別忘了重新儲存文件。 |
| **如何變更簽章演算法？** | 在呼叫 `Sign` 前設定 `signature.SignatureAlgorithm`。預設為 SHA‑256，已符合大多數合規需求。 |
| **隱藏圖片在 Word 介面中會顯示嗎？** | 不會，但可在 Word 選項中開啟 *Show hidden text* 以顯示。此功能常用於儲存不影響版面配置的中繼資料。 |

## 後續步驟

現在您已能 **create group shape docx**、**insert ActiveX command button**，以及 **load markdown into a Word document**，接下來可以探索以下方向：

- **嵌入 VBA 巨集**，讓其回應 ActiveX 按鈕點擊事件。  
- **套用自訂樣式** 至 markdown 產生的段落。  
- 使用 `doc.Save("output.pdf", SaveFormat.Pdf)` **產生 PDF**。  
- **自動化批次處理** 多個 markdown 檔，合併成單一報告文件。

透過這些延伸，您可以構建完整自動化的文件流水線，結合豐富圖形、互動控制項與 markdown 為基礎的撰寫，全部由 C# 完成。

---

*祝編程愉快！如果您覺得本教學

## 接下來該學什麼？

以下教學與本指南所示技術緊密相關，能進一步深化您的應用。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在自己的專案中探索替代實作方式。

- [使用 Aspose.Words for .NET 在 Word 文件中建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 C# 建立 Word 矩形形狀 – 步驟教學](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [從 Word 產生 markdown – 完整 C# 教學](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}