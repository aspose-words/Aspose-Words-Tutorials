---
category: general
date: 2026-08-10
description: 使用 Aspose.Words 程式化建立 Word 文件，學習如何在 Word 中將多個圖形分組、加入矩形，並在 C# 中建立群組圖形。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: zh-hant
lastmod: 2026-08-10
og_description: 使用 Aspose.Words 程式化建立 Word 文件。本指南示範如何在 Word 中將多個形狀分組、加入矩形，以及嵌入純文字內容控制項，全部使用
  C#。
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: 以程式方式建立 Word 文件 – 在 C# 中對形狀分組
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: 以 C# 程式方式建立 Word 文件並將圖形群組
url: /zh-hant/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 以程式方式建立 Word 文件並在 C# 中群組圖形

如果您需要**以程式方式建立 Word 文件**，本教學將示範如何使用 Aspose.Words 建立 DOCX 檔案，並**將多個圖形在 Word 中群組**。我們亦會說明**在 Word 中加入矩形**以及**如何建立群組圖形**，該群組包含矩形與橢圓，外加一個供使用者輸入的純文字 StructuredDocumentTag。

完成後您將得到一個可直接使用的 Word 檔案，內含已群組的矩形‑橢圓圖形以及讓使用者輸入姓名的內容控制項。程式執行完畢後不需要在 Word 中手動編輯。

## 您需要的環境

- .NET 6.0 或更新版本（範例以 .NET 6 為目標，但任何較新的 .NET 版本皆可使用）
- Aspose.Words for .NET 授權（免費試用版可用於測試）
- Visual Studio 2022 或您偏好的任何 C# IDE
- 具備基本的 C# 語法知識

## 以程式方式建立 Word 文件 – 整體工作流程

此流程分為三個邏輯階段：

1. **Initialize** 一個 `Document` 與 `DocumentBuilder` – 這是您產生任何 Word 檔案的基礎。
2. **Build a group shape** 以容納矩形與橢圓 – 示範 **group multiple shapes word** 與 **how to create group shape**。
3. **Insert a StructuredDocumentTag (SDT)** – 一個純文字內容控制項，讓最終使用者填寫資料，並以 **add rectangle to word** 作為整體文件版面的示例。

以下為完整可執行的程式碼，接著是逐步說明。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### 步驟 1 – 初始化文件與建構器
`Document` 物件代表整個 DOCX 檔案，而 `DocumentBuilder` 提供便利的 API 以加入內容。每當您**以程式方式建立 Word 文件**時，初始化它們是第一步需求。

> **專業提示：** 若您打算在多個操作中重複使用同一份文件，請保留單一的 `DocumentBuilder` 實例，以避免不必要的物件建立。

### 步驟 2 – 建立群組圖形容器
`Shape` 搭配 `ShapeType.Group` 可作為容納其他圖形的畫布。設定 `Width` 與 `Height` 會定義群組的邊界框。這就是 Aspose.Words 中 **how to create group shape** 的核心。

> **邊緣情況：** 若群組的寬度小於其子圖形的總寬度，子圖形將被裁切。請確保群組足夠大以容納所有子圖形。

### 步驟 3 – 在 Word 中加入矩形
使用 `ShapeType.Rectangle` 建立矩形。其 `Left` 與 `Top` 屬性相對於群組原點定位。此步驟示範 **add rectangle to word**，並說明如何精確控制位置。

> **常見錯誤：** 忘記設定 `Left`/`Top` 會導致矩形出現在群組的預設原點 (0,0)，可能與其他子圖形重疊。

### 步驟 4 – 在群組中加入橢圓（圓形）
橢圓的加入方式與矩形相同，只是使用 `ShapeType.Ellipse`。`Left = 210` 會將其移至矩形右側，於同一群組內形成視覺上分明的兩個圖形。

> **為何使用群組？** 群組可讓您之後以單一操作同時移動、旋轉或調整兩個圖形的大小，保持它們之間的相對布局。

### 步驟 5 – 將完成的群組圖形插入文件
`builder.InsertNode(groupShape)` 會將整個群組放置於目前游標位置。由於群組已包含其子圖形，您不需要再額外插入矩形或橢圓。

### 步驟 6 – 建立純文字 StructuredDocumentTag (SDT)
StructuredDocumentTag 是一種內容控制項，使用者在 Word 開啟文件時可填寫。設定 `Title = "CustomerName"` 為控制項提供有意義的識別名稱，方便之後的資料擷取。

> **為何使用純文字 SDT？** 它限制輸入為純文字，防止意外的格式化導致後續處理失敗。

### 步驟 7 – 儲存文件
`doc.Save("GroupAndSDT.docx")` 會將檔案寫入磁碟。產生的 DOCX 包含群組圖形與 SDT。於 Microsoft Word 開啟時，會看到矩形與圓形相鄰，兩者可作為單一物件選取，且下方有「Enter name here …」的佔位文字。

#### 預期輸出
- 執行目錄下產生名為 **GroupAndSDT.docx** 的檔案。
- 在 Word 中：一個群組圖形（矩形 + 橢圓），可作為單位移動。
- 緊接群組下方，有一個灰色陰影的內容控制項，提示使用者輸入姓名。

## 其他變化與最佳實踐

### 使用不同的圖形類型
您可以將 `ShapeType.Rectangle` 或 `ShapeType.Ellipse` 替換為其他任何 `ShapeType`（例如 `ShapeType.Polygon`、`ShapeType.Line`）。群組邏輯保持不變。

### 設定填色與邊框
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
加入填色與邊框可提升視覺辨識度，特別是在文件需與非技術利害關係人共享時。

### 旋轉整個群組
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
旋轉整個群組比逐一旋轉子圖形更有效率。

### 匯出為 PDF
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
所有群組圖形與 SDT（以文字欄位呈現）皆會出現在 PDF 中。

## 常見陷阱與避免方法

| 症狀 | 原因 | 解決方案 |
|------|------|----------|

## 接下來您應該學習什麼？

以下教學涵蓋與本指南密切相關的主題，建立在本篇示範的技巧之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [使用 Aspose.Words for .NET 在 Word 文件中建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 C# 在 Word 中建立矩形圖形 – 步驟指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [建立帶陰影矩形圖形的空白 Word 文件 – 步驟指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}