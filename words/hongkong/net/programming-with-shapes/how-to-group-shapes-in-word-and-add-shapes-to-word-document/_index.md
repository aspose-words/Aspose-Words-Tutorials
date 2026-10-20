---
category: general
date: 2026-08-07
description: 如何使用 Aspose.Words 在 Word 中將圖形分組，並使用 C# 向 Word 文件加入圖形。請遵循此一步步指南，撰寫乾淨且可重複使用的程式碼。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: zh-hant
lastmod: 2026-08-07
og_description: 使用 Aspose.Words for .NET 在 Word 中將形狀分組。此教學示範如何向 Word 文件加入形狀、將其分組，並以清晰的
  C# 程式碼儲存檔案。
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: 在 Word 中如何分組圖形 – 快速 C# 指南
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: 如何在 Word 中將圖形分組並將圖形加入 Word 文件
url: /zh-hant/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中將形狀分組並將形狀加入 Word 文件

如果您需要 **how to group shapes in Word**，本指南將使用 Aspose.Words for .NET 帶您完整步驟。您亦會學習 **add shapes to Word document**，只需幾行 C# 程式碼，即可在任何報表或範本情境中使用。

本教學涵蓋您所需的一切：必備的 NuGet 套件、完整的原始檔案，以及每個步驟重要性的說明。完成後，您即可產生一個包含矩形與橢圓，且已合併為單一群組形狀的 DOCX。

## 前置條件

在開始之前，請確保您已具備：

* .NET 6.0 SDK 或更新版本  
* Visual Studio 2022（或任何支援 .NET 的 IDE）  
* Aspose.Words for .NET NuGet 套件（`Aspose.Words`）— 免費試用版可用於測試，授權則會移除評估浮水印  

以上項目即為 **add shapes to Word document** 的唯一外部相依性。

## 如何在 Word 中將形狀分組

解決方案的核心在於建立個別形狀、將它們放置於頁面上，然後以 `GroupShape` 包裹。以下步驟與程式碼的邏輯順序相同。

### 步驟 1：建立文件與建構器

`Document` 物件代表整個 DOCX 檔案。`DocumentBuilder` 提供便利的 API 以編輯文件。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*為什麼重要*：`Document` 是所有 Word 元素的容器。`DocumentBuilder` 會追蹤目前的游標位置，這在稍後插入群組形狀時必須使用。

### 步驟 2：加入矩形形狀

透過指定 `ShapeType.Rectangle` 來建立矩形。寬度、高度與位置以點為單位設定（1 pt ≈ 1/72 in）。

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*為什麼重要*：設定 `StrokeColor` 可讓形狀在文件開啟時可見。若需要實心內部，也可以使用 `FillColor` 來填色。

### 步驟 3：加入橢圓形狀

橢圓使用 `ShapeType.Ellipse`。其大小與位置獨立於矩形，讓您能控制群組的最終版面配置。

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*為什麼重要*：將橢圓的 `Left = 120`，可避免與矩形重疊，使群組在視覺上更為分明。

### 步驟 4：將兩個形狀分組

`GroupShape` 充當容器，將其子項視為單一物件。這是 **how to group shapes in Word** 的關鍵操作。

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*為什麼重要*：分組後，您可以同時移動、調整大小或旋轉兩個形狀。對 `groupShape` 的任何變換都會傳遞至其子項。

### 步驟 5：將群組形狀插入文件

`DocumentBuilder.InsertNode` 會將 `GroupShape` 放置於目前游標位置。因為我們尚未移動建構器，群組會出現在第一頁的起始處。

```csharp
builder.InsertNode(groupShape);
```

*為什麼重要*：直接插入節點可避免額外的段落或表格儲存格。群組會成為文件流程的一部份。

### 步驟 6：儲存文件

最後，將 DOCX 檔寫入磁碟。請使用您的應用程式有寫入權限的完整路徑。

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*為什麼重要*：`doc.Save` 會完成所有變更。產生的檔案可在 Microsoft Word、LibreOffice 或任何支援 DOCX 的檢視器中開啟。

## 完整原始檔案

將下列程式碼複製到新的主控台專案（`dotnet new console`）中並執行。程式會建立名為 `GroupShape.docx` 的檔案，內含已分組的矩形與橢圓。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### 預期結果

開啟 `GroupShape.docx` 後，您會看到一個單一的視覺物件，左側為藍色矩形、右側為綠色橢圓。於 Word 中選取該物件時，兩個形狀會同時被高亮——證明 **how to group shapes in Word** 已成功。

## 常見問題與邊緣情況

* **可以加入超過兩個形狀嗎？**  
  可以。在插入群組之前，對每個額外的 `Shape` 呼叫 `groupShape.AppendChild`。

* **如果需要旋轉群組該怎麼做？**  
  在建立群組後設定 `groupShape.RotationAngle = 45;`（角度為度數）。

* **需要呼叫 `doc.UpdatePageLayout()` 嗎？**  
  此情境下不需要。儲存文件時版面會自動更新。

* **授權會如何影響程式碼？**  
  若使用有效的 Aspose.Words 授權（`License license = new License(); license.SetLicense("Aspose.Words.lic");`），產生的文件將不會出現評估浮水印。

## 結論

您現在已掌握 **how to group shapes in Word** 與 **add shapes to Word document** 的技巧，並使用 Aspose.Words for .NET 完成文件建立、個別形狀定義、分組、插入以及儲存。接下來您可以嘗試：

* 將文字方塊或圖片加入群組  
* 變更填色、線條樣式或陰影效果  
* 在表格或頁首/頁尾內分組形狀  

這些延伸功能讓您能以程式方式建立複雜的 Word 範本，同時保持程式碼的簡潔與可維護性。祝開發愉快！

## 接下來您可以學習什麼？

以下教學與本指南緊密相關，能進一步深化您所學的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索其他實作方式。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}