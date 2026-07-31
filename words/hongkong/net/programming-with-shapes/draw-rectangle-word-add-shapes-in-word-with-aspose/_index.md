---
category: general
date: 2026-07-29
description: 使用 Aspose.Words 在 Word 中繪製矩形。了解如何新增矩形形狀、線條形狀，以及在單一文件中管理多個形狀的 Word。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: zh-hant
lastmod: 2026-07-29
og_description: 使用 Aspose.Words 在 Word 中繪製矩形。跟隨本逐步指南，輕鬆加入矩形形狀、線條形狀，並在 Word 中輕鬆處理多個形狀。
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: 在 Word 中繪製矩形 – 精通在 Word 中添加形狀
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: 在 Word 中繪製矩形 – 使用 Aspose 在 Word 中添加形狀
url: /zh-hant/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – 在 Word 中新增圖形的完整指南

有沒有想過如何在 **draw rectangle word** 文件中不必每次都開啟 UI 就能畫矩形？你並不孤單。許多開發者需要即時產生 Word 檔案，而最簡單的方式就是讓程式庫幫你完成繁重的工作。在本教學中，我們將示範如何使用 Aspose.Words for .NET **新增圖形**——特別是矩形與直線——並且全程聚焦於 *draw rectangle word* 這個關鍵字，讓你不會走偏。

把它想像成一個隱藏在程式碼裡的迷你美術工作室。完成後，你將能 **新增矩形圖形**、**新增直線圖形**，甚至把它們組合成 **multiple shapes word** 群組。無需 UI、無需手動操作，純粹乾淨、可重複的 C# 程式碼。

## 你將學會什麼

- 使用 Aspose.Words 建立新的 Word 文件。  
- 建立可容納多個物件的 **GroupShape**。  
- 在該群組內 **add rectangle shape** 與 **add line shape**。  
- 將群組插入文件主體。  
- 儲存檔案並即時看到結果。  

只要你對基本的 C# 有一定了解，且手上有 Aspose.Words 的授權，即可開始。除核心函式庫外，無需額外的 NuGet 套件。

> **專業提示：** Aspose.Words 支援 .NET 6、.NET 7 與 .NET Framework 4.6 以上版本。請依專案需求選擇相符的執行環境。

![draw rectangle word example](https://example.com/placeholder-image.png "draw rectangle word – 在 Word 檔案中以群組方式呈現的圖形")

## draw rectangle word – 設定文件

在 **draw rectangle word** 之前，我們需要一張乾淨的畫布。`Document` 類別就是畫布；`DocumentBuilder` 則是我們的畫筆。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

上面的兩行程式碼會在記憶體中建立一個全新的 `.docx`，尚未寫入磁碟，讓你可以隨意實驗而不會產生雜亂的檔案。

## 如何新增圖形 – 建立 GroupShape 容器

當你希望 **multiple shapes word** 如同單一單位一起移動、一起旋轉時，只需要把它們包在 `GroupShape` 裡。把群組想像成一個資料夾，裡面放著其他圖形。

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

為什麼要使用群組？因為之後你可能會 **add rectangle shape** 與 **add line shape**，然後一次性一起移動。若不使用群組，就必須分別調整每個圖形的位置。

## add rectangle shape – 在群組內插入矩形

容器已建立，接下來 **add rectangle shape**。矩形是一個 `Shape`，其 `ShapeType` 為 `Rectangle`。

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

請注意，`Left` 與 `Top` 的數值是相對於群組的原點，而非整頁。這樣可以更精確地對齊圖形。矩形會出現在群組左上角附近。

## add line shape – 在同一群組內加入直線

直線也是 `Shape`，只不過其 `ShapeType` 為 `Line`。我們會把它放在矩形下方。

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

因為直線的高度為 0，`Top` 屬性決定了它在垂直方向上的位置；`Width` 則控制直線的水平長度。

## multiple shapes word – 把群組插入文件主體

現在我們已擁有一個包含 **add rectangle shape** 與 **add line shape** 的群組。最後一步是把整個群組放入文件中。

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` 會把群組插入到 `DocumentBuilder` 目前所在的位置。如果你想把它放在特定段落，先使用 `builder.MoveToParagraph(index)` 移動建構器。

## 儲存結果 – 看到 draw rectangle word 的輸出

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

在 Microsoft Word 中開啟產生的檔案，你會看到一個包含矩形與直線的單一群組。你可以點選整個群組、拖曳或調整大小——所有圖形會同步移動。這就是 **multiple shapes word** 的威力。

### 預期輸出

- 一個名為 `GroupShape.docx` 的 `.docx` 檔案。  
- 單頁文件，左上角有一個尺寸為 120 × 80 pt 的群組矩形。  
- 矩形正下方有一條長度 150 pt 的水平直線。  
- 兩個圖形可作為單一物件一起選取。

如果雙擊群組，Word 會允許你分別編輯每個圖形，方便微調。

## 常見問題與特殊情況

**如果需要超過兩個圖形怎麼辦？**  
只要對每個額外的物件呼叫 `group.AppendChild(yourShape)` 即可。群組可容納任意數量的圖形，適合製作複雜圖表。

**可以變更矩形的填色嗎？**  
當然可以。建立矩形後，設定 `rectangle.FillColor = System.Drawing.Color.LightBlue;` 即可。所有支援填色的圖形皆可這樣操作。

**直線需要把 `Height = 0` 嗎？**  
是的，對於水平直線，高度應設為 0。若是垂直直線，則把 `Width = 0`，並給予正值的 `Height`。

**這樣能支援 .doc（Word 97‑2003）檔案嗎？**  
Aspose.Words 能儲存為舊版 `.doc` 格式，但某些較新的圖形功能可能受限。建議使用 `.docx` 以確保完整相容性。

**如何旋轉整個群組？**  
在插入之前設定 `group.Rotation = 45;`（單位為度）即可。旋轉會同時套用到所有子圖形。

## 重點回顧 – 程式化在 Word 中新增圖形

- **draw rectangle word** 從建立 `Document` 與 `DocumentBuilder` 開始。  
- 建立 **GroupShape** 以容納 **multiple shapes word**。  
- **add rectangle shape** 與 **add line shape** 依序加入群組。  
- 使用 `builder.InsertNode` 把群組插入文件主體。  
- 儲存檔案並開啟檢查視覺結果。

以上即為完整流程，全部以簡潔易讀的程式碼示範呈現。

## 往後的步驟與相關主題

既然已掌握 **如何新增圖形**，可以進一步探索：

- 使用圓角矩形 (`ShapeType.Rectangle` + `CornerRadius`) 的 **add rectangle shape**。  
- 以不同虛線樣式 (`line.LineFormat.DashStyle`) 來美化直線。  
- 在圖形旁嵌入圖片，製作更豐富的報表。  
- 利用 **multiple shapes word** 建構流程圖或簡易 UML 圖。  

上述每個主題都建立在本教學的基礎上，遵循相同的「建立 → 設定 → 群組」模式。

---

祝編程愉快！若在實作過程中遇到問題或有有趣的應用案例，歡迎在下方留言。你的回饋將幫助大家一起精通 **draw rectangle word** 以及更廣泛的圖形操作。

## 接下來該學什麼？

以下教學與本篇內容緊密相關，能進一步深化你所學的技巧。每篇皆提供完整可執行的程式碼範例與逐步說明，協助你掌握更多 API 功能，或在自己的專案中嘗試不同的實作方式。

- [使用 C# 在 Word 中建立矩形圖形 – 步驟教學](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [使用 Aspose.Words 在 Word 中建立矩形圖形 – 步驟教學](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [使用 Aspose.Words for .NET 在 Word 文件中插入圖形](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}