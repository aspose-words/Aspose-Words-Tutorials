---
category: general
date: 2026-10-23
description: 建立一個空白的 Word 文件，加入矩形形狀，並使用 Aspose.Words 在 Word 中隱藏該形狀。針對 .NET 開發人員的逐步程式碼。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: zh-hant
lastmod: 2026-10-23
og_description: 建立一個空白的 Word 文件，加入一個矩形形狀，並使用 Aspose.Words 在 Word 中隱藏該形狀。請參考完整的 C#
  範例。
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: 建立空白 Word 文件並加入隱藏的矩形形狀
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: 建立空白的 Word 文件並加入矩形形狀
url: /zh-hant/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立空白 Word 文件並加入矩形圖形

如果您需要 **建立空白 Word 文件**，本教學將示範如何使用 Aspose.Words for .NET 完成此操作。您還會學習 **如何插入圖形**——特別是矩形——以及 **隱藏圖形** 使其不影響版面配置。

本教學會逐行說明程式碼，解釋每一步的重要性，並討論常見的陷阱，例如在不同的 Word 檢視模式下隱藏圖形的可見性。完成後，您將得到一個完整的 `.docx` 檔案，內含一個隱藏的矩形圖形，之後可以程式化地顯示或操作它。

## 前置條件

- .NET 6.0 或更新版本（此程式碼亦相容 .NET Framework 4.6+）
- Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）
- 開發環境，例如 Visual Studio 2022 或具 C# 擴充功能的 VS Code
- 具備基本的 C# 語法與 Word 文件概念

不需要額外安裝 Office，因為 Aspose.Words 完全在記憶體中運作。

## 建立空白 Word 文件

第一步是實例化一個空的 `Document` 物件。此物件代表一個尚未包含任何節、段落或內容的 Word 檔案。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**為什麼這很重要：**  
空白的 `Document` 為您提供乾淨的畫布。如果從現有範本開始，隱藏的圖形可能會繼承不想要的樣式。從頭開始可確保之後加入的矩形圖形是唯一受您控制的內容。

## 在文件中加入矩形圖形

接下來，我們需要使用 `DocumentBuilder` 來將內容放入文件。`DocumentBuilder` 的 `InsertShape` 方法是 **插入圖形** 物件的標準做法，例如矩形、圓形或自訂圖形。

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**為什麼這很重要：**  
`InsertShape` 會回傳一個 `Shape` 物件，您可以進一步設定（顏色、線條樣式等）。尺寸以點為單位（1 點 = 1/72 吋），與 Word 內部的測量系統相同。

### 可選：設定矩形樣式（可選）

如果您希望在之後取消隱藏時看到可見的邊框，可以設定線條粗細與顏色：

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

這些程式碼屬於可選項目，因為圖形在下一步會被隱藏。

## 在 Word 中隱藏圖形

Word 允許將圖形隱藏於版面配置中，同時仍保留於文件的物件模型。將 `Hidden` 屬性設為 `true` 後，圖形在一般檢視中會變為不可見，但仍可透過 API 進行選取。

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**為什麼這很重要：**  
隱藏的圖形可用於儲存中繼資料、稍後處理的佔位符，或僅在特定情況下才顯示的條件內容（例如產生最終報告時）。圖形仍保留在檔案中，您可以稍後使用 `rectangleShape.Hidden = false;` 程式化地取消隱藏。

## 儲存文件

最後，將文件寫入 **磁碟**。副檔名決定 Word 的檔案格式；`.docx` 為現代的 Open XML 格式。

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**結果：**  
在 Microsoft Word 中開啟 `HiddenShape.docx` 時會看到一個空白頁面。矩形本身不可見，但若前往 **首頁 → 選取 → 選取窗格**，即可看到圖形列在清單中，並可切換其可見性。

## 完整範例程式

以下提供完整程式碼，您可以直接複製、貼上並執行。程式碼已包含所有必要的 `using` 陳述式與註解。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**預期輸出：**  

- 主控台會印出儲存路徑。  
- `HiddenShape.docx` 於 Word 中以空白頁面顯示。  
- 矩形圖形已存在但被隱藏；您可透過 *選取窗格* 或以 **程式化** 方式將 `Hidden = false` 後重新開啟檔案來驗證。

## 常見問題與邊緣情況

| 問題 | 答案 |
|----------|--------|
| **我可以隱藏其他類型的圖形嗎？** | 可以。任何 `Shape`（例如 `ShapeType.Ellipse`、`ShapeType.Picture`）皆支援 `Hidden` 屬性。 |
| **隱藏的圖形會增加檔案大小嗎？** | 增加幅度極小（幾 KB），因為圖形資料以 XML 形式儲存在 `.docx` 套件中。 |
| **如果我只想在列印檢視中顯示圖形該怎麼做？** | 使用 `Shape.IsPrint` 屬性取代 `Hidden`。將 `IsPrint = false` 可讓圖形在列印輸出時隱藏，但仍在螢幕上可見。 |
| **如何在之後取消隱藏圖形？** | 載入文件，依 `Shape.Name` 等方式定位圖形，然後設定 `shape.Hidden = false;` 後儲存。 |
| **這在 .doc（二進位）格式下也有效嗎？** | 有效，Aspose.Words 可使用 `document.Save("file.doc");` 儲存為 `.doc`，隱藏旗標會被保留。 |

## 專業小技巧

- **為圖形命名**：`rectangleShape.Name = "PlaceholderRectangle";` 可讓您之後透過 `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")` 更容易找到它。  
- **批次處理**：若需在多個文件中加入隱藏圖形，請將程式碼封裝成方法，並重複使用同一個 `DocumentBuilder` 實例。  
- **效能考量**：建立圖形本身成本不高，但頻繁儲存大型文件可能受 I/O 限制。建議使用 `MemoryStream` 進行中間處理。

## 結論

現在您已掌握 **建立空白 Word 文件**、**加入矩形圖形**，以及使用 Aspose.Words for .NET **隱藏圖形** 的技巧。此方法讓您能嵌入隱形佔位符，日後再顯示或操作，適用於動態報表產生、條件內容與文件範本化等情境。

接下來您可以探索以下方向：

- 使用 `ShapeType.Picture` 將矩形換成圖片或圖表。  
- 在頁首/頁尾區段使用 **如何插入圖形** 來建立浮水印式佔位符。  
- 結合隱藏圖形與 **加入矩形圖形** 為基礎的資料驗證（例如將 JSON 存於圖形的 `AlternativeText` 屬性）。

祝您開發順利，歡迎自行嘗試其他圖形類型與可見性設定，以符合您的文件自動化需求！

## 接下來該學什麼？

以下教學與本篇內容密切相關，能進一步延伸本指南所示的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索替代實作方式。

- [Create Word Document – How to Add Rectangle Shape and Shadow](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}