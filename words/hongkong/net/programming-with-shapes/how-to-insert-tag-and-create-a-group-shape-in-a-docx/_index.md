---
category: general
date: 2026-09-14
description: 學習如何在 C# 中使用 Aspose.Words 插入標籤、加入形狀、建立群組，並將文件另存為 DOCX。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert tag
- save document as docx
- how to create group
- how to add shapes
- how to save docx
language: zh-hant
lastmod: 2026-09-14
og_description: 如何使用 Aspose.Words 插入標籤、加入圖形、建立群組，並將文件另存為 DOCX。請參考逐步指南。
og_image_alt: Diagram showing how to insert tag inside a grouped shape before saving
  as DOCX
og_title: 如何在 DOCX 中使用 C# 插入標籤並建立群組形狀
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to insert tag, add shapes, create a group, and save document
    as DOCX using Aspose.Words in C#.
  headline: How to insert tag and create a group shape in a DOCX
  type: TechArticle
tags:
- Aspose.Words
- C#
- DOCX manipulation
title: 如何在 DOCX 中插入標籤並建立群組圖形
url: /zh-hant/net/programming-with-shapes/how-to-insert-tag-and-create-a-group-shape-in-a-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 DOCX 中插入標籤並建立群組圖形

如果您需要了解 **如何插入標籤** 以建立複雜版面，本指南提供完整、可執行的解決方案。您將看到如何加入圖形、建立群組，最後使用 Aspose.Words for .NET **將文件另存為 DOCX**。

文件產生常常需要將文字標籤與圖形元素混合。本教學將教您 **如何插入標籤**、**如何加入圖形**、**如何建立群組**，以及正確的 **保存 docx** 方式，確保檔案在 Word 中開啟時不失真。

## 前置條件

- .NET 6.0 或更新版本（程式碼同樣支援 .NET Framework 4.7+）
- Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）
- 基本的 C# 語法熟悉度
- Visual Studio 或 VS Code 等開發環境

不需要額外的函式庫；整個範例只需一個 NuGet 參考即可執行。

## 如何建立群組並加入圖形

第一個合乎邏輯的步驟是建立一個 **群組**，用來容納多個圖形。群組化可在之後移動或旋轉時，保持圖形一起移動。

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

// 1️⃣ Create an empty document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// 2️⃣ Build a GroupShape (200 × 200 points) and set its bounds
GroupShape groupShape = new GroupShape(document, 200, 200);
groupShape.Bounds = new RectangleF(50, 50, 200, 200);

// 3️⃣ Add a rectangle shape
groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
{
    Width = 80,
    Height = 80,
    Left = 0,
    Top = 0
});

// 4️⃣ Add an ellipse shape next to the rectangle
groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
{
    Width = 80,
    Height = 80,
    Left = 100,
    Top = 0
});
```

**為什麼這很重要：**  
`GroupShape` 如同容器。當您之後移動群組時，矩形與橢圓會一起移動，保留相對位置。這是管理屬於同一邏輯區塊的多個圖形的推薦做法。

## 如何在文件內插入標籤

群組準備好之後，您可以在群組之後 **插入標籤**（StructuredDocumentTag，也稱為 SDT）。此標籤可容納純文字、富文字，甚至可重複的內容。

```csharp
// 5️⃣ Insert the group at the current builder position
builder.InsertNode(groupShape);

// 6️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and write content
builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
builder.Writeln("Content inside the SDT");
```

**為什麼要使用 StructuredDocumentTag：**  
SDT 提供 Word 能辨識的語意標記，可用於內容控制、資料繫結或表單填寫情境。透過 `InsertStructuredDocumentTag`，您可以以 **如何插入標籤** 的方式插入，且在 Microsoft Word 後續編輯時仍能保持。

## 如何保存 docx 並驗證結果

最後一步是將文件寫入磁碟。以下程式碼示範正確的 **將文件另存為 docx** 方法，以及輸出檔案的存放位置。

```csharp
// 7️⃣ Save the document to the file system
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "GroupAndSDT.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

當您在 Word 中開啟 *GroupAndSDT.docx* 時，應該會看到一個已群組的矩形‑橢圓圖形，緊接著是一個標題為 **MyTag**、內容為「Content inside the SDT」的純文字內容控制。

### 預期輸出

- 一個 200 × 200 點的群組，位於頁面 (50, 50) 位置。
- 群組內部：左側為藍色矩形，右側為橢圓（預設顏色）。
- 群組正下方：一個標示為 **MyTag**、文字為「Content inside the SDT」的內容控制。

## 完整、可執行的範例

以下是完整程式碼，您可以直接複製貼上到主控台應用程式中。程式碼包含所有必要的 `using` 指示、錯誤處理，以及說明每一步的註解。

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeWordsGroupAndTag
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document and a DocumentBuilder to work with it
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Build a GroupShape (200x200) and define its bounds
            GroupShape groupShape = new GroupShape(document, 200, 200);
            groupShape.Bounds = new RectangleF(50, 50, 200, 200);

            // Add a rectangle to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
            {
                Width = 80,
                Height = 80,
                Left = 0,
                Top = 0
            });

            // Add an ellipse to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
            {
                Width = 80,
                Height = 80,
                Left = 100,
                Top = 0
            });

            // Insert the group into the document at the current builder position
            builder.InsertNode(groupShape);

            // Insert a plain‑text StructuredDocumentTag (SDT) and write some content inside it
            builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
            builder.Writeln("Content inside the SDT");

            // Save the resulting document
            string outputPath = Path.Combine(
                Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
                "GroupAndSDT.docx");

            document.Save(outputPath);
            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

執行程式後，前往桌面，雙擊 *GroupAndSDT.docx*，即可驗證群組與標籤是否如說明所示。

## 常見問題與邊緣案例

| 問題 | 答案 |
|----------|--------|
| **我可以在群組中加入超過兩個圖形嗎？** | 可以。在插入群組之前，對每個額外的圖形呼叫 `groupShape.AppendChild(new Shape(...))`。 |
| **如果需要富文字標籤而非純文字該怎麼做？** | 在 `InsertStructuredDocumentTag` 中使用 `StructuredDocumentTagType.RichText`。 |
| **如何變更矩形或橢圓的顏色？** | 設定各自 `Shape` 例項的 `FillColor` 屬性，例如 `shape.FillColor = Color.LightBlue;`。 |
| **能否旋轉整個群組？** | 在插入節點前設定 `groupShape.Rotation = 45;`（單位為度）。 |
| **需要手動呼叫 `Dispose()` 釋放物件嗎？** | Aspose.Words 會自行管理大多數資源；在短暫執行的主控台應用程式中，釋放 `Document` 為可選。 |

## 保存 DOCX 檔案的最佳實踐

- **始終使用絕對路徑**（或明確的相對路徑）呼叫 `document.Save`，以避免因工作目錄不明而產生「找不到檔案」的錯誤。
- **若需透過 HTTP 傳送或存入資料庫，建議使用接受 Stream 的 `Save` 重載**。
- **若必須相容舊版 Word（例如 Word 2003），請設定 `CompatibilityOptions`**。對於大多數現代情境，預設設定已足夠。

## 後續步驟

既然您已掌握 **如何插入標籤**、**如何加入圖形**、**如何建立群組**，以及 **如何保存 docx**，接下來可以探索更進階的情境：

- 結合多個群組以建立複雜圖表。
- 在 Word 範本中使用 `StructuredDocumentTag` 進行資料繫結。
- 將相同文件匯出為 PDF（`document.Save("output.pdf")`），同時保留群組圖形。
- 透過程式碼設定 SDT 內容以自動化表單填寫（`builder.MoveToDocumentEnd(); builder.Write("New value");`）。

嘗試不同的 `ShapeType`（例如 `ShapeType.Polygon`、`ShapeType.Line`），觀察它們在 `GroupShape` 內的行為。相同的模式亦適用於表格、圖片或任何您想一起保留的節點。

---

**總結：** 本教學示範了 **如何在群組圖形內插入標籤**、**如何加入圖形**、**如何建立群組**，以及使用 Aspose.Words for .NET 正確 **將文件另存為 docx** 的方法。您現在已具備以程式方式建立豐富、互動式 DOCX 檔案的堅實基礎。

## 接下來該學什麼？

以下教學與本指南的技術緊密相關，能進一步深化您的 API 應用與實作方式，每篇皆提供完整可執行的程式碼範例與逐步說明。

- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [How to Recover DOCX – Complete Guide Using Aspose.Words](/words/english/net/programming-with-loadoptions/how-to-recover-docx-complete-guide-using-aspose-words/)
- [How to Check Grammar in DOCX with Aspose.Words – use gpt-4 turbo](/words/english/net/ai-powered-document-processing/how-to-check-grammar-in-docx-with-aspose-words-use-gpt-4-tur/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}