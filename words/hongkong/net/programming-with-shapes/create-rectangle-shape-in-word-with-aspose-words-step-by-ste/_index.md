---
category: general
date: 2025-12-29
description: 使用 Aspose.Words C# 在 Word 文件中建立矩形形狀。學習設定形狀透明度、設定陰影顏色，輕鬆儲存 Word 文件。
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: zh-hant
og_description: 使用 Aspose.Words C# 在 Word 文件中建立矩形形狀。本指南說明如何設定形狀透明度、設定陰影顏色，並儲存 Word
  文件。
og_title: 在 Word 中建立矩形形狀 – 完整的 Aspose.Words 教程
tags:
- Aspose.Words
- C#
- Word Automation
title: 使用 Aspose.Words 在 Word 中建立矩形形狀 – 逐步指南
url: /zh-hant/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中建立矩形形狀 – 完整 Aspose.Words 教程

是否曾需要在 Word 文件中 **建立矩形形狀**，卻不知從何開始？你並不孤單；許多開發人員在自動化報告或發票時都會碰到這個問題。在本指南中，我們將逐步說明如何建立矩形形狀、設定形狀透明度、設定陰影顏色，最後使用 Aspose.Words for .NET **儲存 Word 文件**。

我們會從最初的 Document 物件講到磁碟上的最終 `.docx` 檔案，讓您在結束時能夠以程式方式 **建立 Word 文件**，不再需要猜測。無需外部參考，只要一個可直接複製貼上的完整解決方案。

## Prerequisites

- .NET 6.0 或更新版本（程式碼亦相容於 .NET Framework 4.7+）
- Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）
- 具備基本的 C# 語法概念
- 您慣用的 IDE（Visual Studio、Rider、VS Code 等）

> **小技巧:** 若您使用 Aspose.Words 的免費試用版，程式庫會在輸出檔案上加上浮水印。正式環境需要有效的授權。

## Step 1: Initialize the Document and Builder

我們首先建立一個全新的空白 Word 文件，並建立一個可讓我們插入內容的 `DocumentBuilder`。可以把 Builder 想像成在頁面上繪圖的虛擬筆。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **為什麼重要:** 若沒有 `DocumentBuilder`，您必須直接操作低階的節點樹，這容易出錯且難以閱讀。

## Step 2: Create rectangle shape

現在我們實際 **建立矩形形狀**。`InsertShape` 方法接受 `ShapeType` 列舉、寬度與高度（以點為單位）。回傳的 `Shape` 物件讓我們之後可以微調視覺屬性。

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

此時矩形是一個固定在目前段落的實心黑色方塊。您可以移動、調整大小，甚至在需要時旋轉它。

![在 Word 文件中建立帶陰影的矩形形狀](/images/rectangle-shadow.png "顯示帶灰色陰影的矩形形狀的 Word 文件")

*圖片替代文字: 在 Word 文件中建立帶陰影的矩形形狀*

## Step 3: Set shape transparency

透明度是形狀填充的「透視」程度。Aspose.Words 使用 `Transparency` 屬性，範圍從 `0.0`（不透明）到 `1.0`（完全透明）。此處我們 **設定形狀透明度** 為 40 %，讓底層文字仍保持可讀。

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **特殊情況:** 若需要完全看不見的形狀但仍想保留陰影，請將 `Transparency` 設為 `1.0`，並給予形狀非零的輪廓寬度。

## Step 4: Configure the shadow

細緻的投影可以增加層次感。我們將 **設定陰影顏色** 為中灰色，調整其模糊半徑，並在水平與垂直方向上各偏移幾個點。

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **為什麼重要:** 陰影若過於銳利或過暗，會看起來像列印瑕疵。調整 `Blur` 與 `Transparency` 直至自然為止。

## Step 5: Save the Word document

最後我們將 **儲存 Word 文件** 到磁碟。`Save` 方法會自動依副檔名判斷檔案格式；`.docx` 為現代的 OpenXML 格式。

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

如果資料夾不存在，Aspose.Words 會拋出 `ArgumentException`。請確保路徑有效，或事先建立目錄。

## Full Working Example

以下是完整、可直接執行的程式範例，將所有步驟整合在一起。將其複製到新的主控台專案中，然後按 **F5**。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Expected result

在 Microsoft Word 中開啟 `ShadowRectangle.docx`。您應該會看到一個淡灰色的矩形，帶有柔和且略微偏移的陰影，且透明度為 40 %。此形狀位於空白頁上，隨時可加入其他內容。

## Common Questions & Variations

**如果需要不同的形狀該怎麼辦？**  
將 `ShapeType.Rectangle` 替換為其他列舉值（`Ellipse`、`Triangle`、`Star` 等）。其餘程式碼保持不變。

**可以變更輪廓顏色嗎？**  
可以——使用 `rectangleShape.StrokeColor = System.Drawing.Color.Blue;`，並可選擇設定 `rectangleShape.StrokeWeight = 1.5;`。

**如何將形狀放置在頁面的特定位置？**  
設定 `rectangleShape.WrapType = WrapType.None;`，然後調整 `rectangleShape.Left` 與 `rectangleShape.Top` 屬性（單位為點）。

**可以在矩形內加入文字嗎？**  
當然可以。建立形狀後，您可以呼叫 `rectangleShape.AppendChild(new Paragraph(document))`，再加入包含文字的 `Run`。若需更豐富的格式，請記得設定 `rectangleShape.TextBox` 屬性。

## Pro Tips & Pitfalls

- **License early:** 若忘記套用授權，Aspose.Words 會在首頁插入浮水印，測試時可能造成混淆。
- **Performance tip:** 在迴圈中大量產生文件時，重複使用單一 `Document` 實例，並在每次儲存後呼叫 `document.RemoveAllChildren();`，以減少 GC 壓力。
- **Shadow visibility:** 在低解析度螢幕上，細微的陰影可能看不見。除錯時可增大 `Blur` 或 `OffsetX/Y`，完成後再調回適當值。

## Next Steps

現在您已掌握 **建立矩形形狀**、**設定形狀透明度**、**設定陰影顏色**、以及 **儲存 Word 文件**，可以考慮擴充本教學：

- 新增多個形狀並將它們群組。
- 將矩形插入表格儲存格以建立報表版面。
- 結合 `DocumentBuilder.InsertHtml` 於形狀上覆蓋 HTML 樣式內容。
- 探索 `Glow` 或 `Reflection` 等其他視覺效果，打造更豐富的 UI 風格文件。

多加實驗、嘗試不同做法，然後再精煉——程式化文件產生是一個結合視覺設計與程式碼的遊樂場。

---

*快樂編程！如果遇到任何問題，歡迎在下方留言，我們一起排除故障。*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}