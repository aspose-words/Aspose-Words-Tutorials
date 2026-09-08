---
category: general
date: 2026-09-08
description: 使用 C# 在 Word 文件中建立矩形形狀。學習設定形狀大小、將多個形狀群組，以及以程式方式建立空白 Word 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: zh-hant
lastmod: 2026-09-08
og_description: 使用 C# 在 Word 文件中建立矩形形狀。本指南說明如何設定形狀大小、將多個形狀分組，以及以程式方式建立空白 Word 文件。
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: 使用 C# 在 Word 中建立矩形形狀並將形狀分組
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 C# 在 Word 中建立矩形形狀並群組形狀
url: /zh-hant/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 在 Word 中建立矩形形狀並群組形狀

如果您需要 **在 Word 檔案中建立矩形形狀**，本教學提供完整、可直接執行的解決方案。您將學會設定形狀大小、群組多個形狀，以及從頭建立空白 Word 文件——全部使用 Aspose.Words for .NET 函式庫。

以程式方式操作 Word 文件常常需要處理許多細節。閱讀完本指南後，您將擁有一個方法，能產生包含矩形與橢圓群組在內的 `.docx` 檔案，供後續編輯或列印使用。

## 前置條件

開始之前，請確保您已具備：

* .NET 6.0 或更新版本（此程式碼亦相容 .NET Framework 4.6 以上）
* **Aspose.Words for .NET** 的授權副本（可使用免費評估金鑰）
* 如 Visual Studio 2022 或 Visual Studio Code 等 IDE
* 基本的 C# 語法概念

除 `Aspose.Words` 之外，無需其他 NuGet 套件。

## 步驟 1：建立空白 Word 文件

第一步是建立一個空的文件，以容納形狀。這滿足 *建立空白 Word 文件* 的需求。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

建立空白文件可提供乾淨的畫布。`Document` 物件代表整個 `.docx` 檔案，而 `FirstSection.Body.FirstParagraph` 則是新節點的預設插入點。

## 步驟 2：建立矩形形狀

現在可以加入矩形。這就是執行 **建立矩形形狀** 的地方。

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

直接設定尺寸即回應 **設定形狀大小** 的關鍵字。所有尺寸值皆以點 (pt) 為單位，讓您精確控制形狀在最終文件中的呈現。

## 步驟 3：建立額外形狀（橢圓）

常見的使用情境是結合多個形狀。此處我們加入一個橢圓，稍後會與同一容器共享。

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

此時兩個形狀仍是獨立的。下一步將示範如何 **群組多個形狀**。

## 步驟 4：在 Word 中群組形狀

群組形狀可讓您一次移動、調整大小或格式化它們。這同時滿足 **在 Word 中群組形狀** 與 **群組多個形狀** 的需求。

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

`GroupShape.Bounds` 屬性決定子形狀的座標系統。將矩形與橢圓放入同一個 `GroupShape` 後，您只需一次呼叫即可一起移動或旋轉它們。

## 步驟 5：儲存文件

最後，將文件寫入磁碟。檔案將包含剛才建立的群組形狀。

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

執行程式後，於 Microsoft Word 開啟 `GroupedShapes.docx`。您應該會看到矩形與橢圓已被群組；選取其中一個形狀時，另一個也會同時被選取，證明群組成功。

## 完整原始碼

將以下完整程式貼入新的 console‑app 專案並執行。無需額外程式碼。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### 預期輸出

執行程式會產生 `GroupedShapes.docx`。在 Word 中開啟該檔案會看到：

* 一個 **矩形**（100 pt × 50 pt），藍色邊框、淡灰色填色。
* 一個 **橢圓**（80 pt × 80 pt），深綠色邊框、淡黃色填色。
* 兩個形狀位於同一個群組內，移動其中一個會同時移動另一個。

## 常見問題與邊緣情況

| 問題 | 答案 |
|----------|--------|
| **我可以在群組中加入超過兩個形狀嗎？** | 可以。建立額外的 `Shape` 物件，然後對每個呼叫 `group.AppendChild(yourShape)`。 |
| **如果需要旋轉群組該怎麼做？** | 設定 `group.RotationAngle = 45;`（單位為度）。所有子形狀會一起旋轉。 |
| **文件已儲存後還能再群組形狀嗎？** | 必須在儲存前修改文件結構；否則需要重新載入檔案、定位形狀並重新建立群組。 |
| **需要手動釋放任何物件嗎？** | Aspose.Words 會自行管理資源，但若手動開啟 `FileStream`，應自行釋放。 |
| **程式碼能否支援 .doc（二進位）格式？** | 能，將 `doc.Save("output.doc")` 即可。群組行為相同。 |

## 結論

現在您已掌握如何在 Word 檔案中使用 C# **建立矩形形狀**、**設定形狀大小**，以及 **群組多個形狀**。此方法讓您能以程式方式建立複雜圖表、浮水印或基於範本的報表，免除手動編輯。

### 後續步驟

* 進一步探索 **在 Word 中群組形狀**，加入文字方塊或圖片至同一群組。
* 使用 `SetShapeSize` 模式，根據頁面佈局動態計算尺寸。
* 結合此技巧與合併列印欄位，批量產生個人化文件。

歡迎嘗試不同的形狀類型、顏色與群組變換。祝開發順利！

## 接下來您可以學習什麼？

以下教學涵蓋與本指南緊密相關的主題，進一步深化您對 API 功能的掌握，並提供可直接套用於專案的完整範例與步驟說明。

- [使用 Aspose.Words for .NET 在 Word 文件中建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)
- [使用陰影矩形形狀建立空白 Word 文件 – 步驟說明](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [使用陰影矩形建立 Word 文件 – 步驟說明](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}