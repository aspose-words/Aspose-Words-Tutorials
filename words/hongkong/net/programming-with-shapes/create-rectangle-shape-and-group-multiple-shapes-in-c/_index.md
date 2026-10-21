---
category: general
date: 2026-09-18
description: 使用 C# 在 Word 文件中建立矩形形狀。了解如何新增多個形狀、將形狀加入群組，以及使用 Aspose.Words 插入群組形狀。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: zh-hant
lastmod: 2026-09-18
og_description: 使用 C# 在 Word 檔案中建立矩形形狀。本指南示範如何新增多個形狀、將形狀加入群組，以及使用 Aspose.Words 插入群組形狀。
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: 在 C# 中建立矩形形狀並將形狀群組
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: 在 C# 中建立矩形形狀並將多個形狀分組
url: /zh-hant/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中建立矩形形狀並將多個形狀分組

如果您需要在 Word 文件中 **建立矩形形狀**，本教學提供完整解決方案。您將會看到如何 **新增多個形狀**、**將形狀加入群組**，以及使用 Aspose.Words API for .NET **插入群組形狀**。

在程式化產生報告、合約或行銷素材時，操作形狀是常見需求。完成本指南後，您將擁有一個可執行的 C# 主控台應用程式，能產生包含矩形、橢圓以及包含兩者的群組形狀的 `.docx` 檔案。

唯一的前置條件是近期的 .NET SDK（6.0 或更新）以及授權的 Aspose.Words for .NET 版本。無需其他工具。

## 前置條件

- .NET 6.0 SDK 或更新版本  
- Aspose.Words for .NET（NuGet 套件 `Aspose.Words`）  
- 基本熟悉 C# 語法  

您可以使用以下指令安裝套件：

```bash
dotnet add package Aspose.Words
```

## 步驟 1：使用 Aspose.Words 建立矩形形狀

第一步是建立一個類型為 `Rectangle` 的 `Shape` 物件。此物件代表文件中將顯示的視覺矩形。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**為什麼這很重要：** `ShapeType.Rectangle` 告訴 Aspose.Words 繪製幾何矩形。設定 `Width` 與 `Height` 定義其以點為單位的大小（1 點 = 1/72 英吋）。加入填充色與邊框色使形狀可見，無需額外樣式。

## 步驟 2：將多個形狀新增至文件

在矩形之後，您可以建立任意數量的其他形狀。在此範例中，我們加入一個橢圓，以示範 **新增多個形狀** 的運作方式。

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**為什麼這很重要：** 每次呼叫 `new Shape` 都會建立一個獨立的繪圖物件。依序插入它們即可累積形狀集合，之後可將其分組或個別定位。

## 步驟 3：將形狀加入群組

將形狀分組可簡化版面配置，因為群組會作為單一節點運作。本步驟示範如何使用 `GroupShape` **將形狀加入群組**。

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**為什麼這很重要：** `GroupShape` 如同容器。當您移動、旋轉或調整群組大小時，所有子形狀會自動跟隨。邊界框（200 × 200 點）定義了子形狀的座標空間。

## 步驟 4：將群組形狀插入文件

現在群組已包含矩形與橢圓，您需要在所需位置 **插入群組形狀**。建構器已放置空的群組，但若需要也可以將其插入其他位置。

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**為什麼這很重要：** 調整 `Left` 與 `Top` 可將整個群組在頁面內移動。儲存文件會將形狀層級寫入 `.docx` 檔案，該檔案可於 Microsoft Word、LibreOffice 或任何相容檢視器開啟。

## 完整可執行範例

以下為結合所有步驟的完整程式碼。將程式碼複製到新的主控台專案中並執行，即可產生 `GroupShapeExample.docx`。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**預期輸出：**  
開啟 `GroupShapeExample.docx` 後會看到一個包含淡藍色矩形與淡珊瑚色橢圓的單一群組，兩者皆位於 200 × 200 點的容器內。該群組在 Word 中可作為單一物件選取，證實 **將形狀加入群組** 成功。

## 常見變化與邊緣情況

| Situation | Recommended adjustment |
|-----------|------------------------|
| 不同的形狀類型（例如 `ShapeType.Line`） | 使用所需的 `ShapeType` 建立形狀，並相應設定其幾何形狀。 |
| 需要旋轉形狀 | 在將形狀加入群組前，使用 `shape.Rotation = 45;`（度）設定旋轉角度。 |
| 大型文件且包含多個群組 | 重複使用單一的 `DocumentBuilder` 實例；避免為每個群組建立新建構器，以減少記憶體開銷。 |
| 儲存為 PDF 而非 DOCX | 在插入群組後呼叫 `doc.Save("output.pdf", SaveFormat.Pdf);`。 |

**專業提示：** 需要精確定位時，務必為群組設定明確的 `Left` 與 `Top` 值。若省略，群組會繼承建構器目前的游標位置，可能導致版面配置出現意外結果。

## 結論

現在您已了解如何在 Word 文件中使用 C# **建立矩形形狀**、**新增多個形狀**、**將形狀加入群組**，以及 **插入群組形狀**。完整範例示範了從建立文件到儲存最終檔案的完整工作流程。  

接下來，您可以探索相關主題，如 **相對於文字定位形狀**、**套用文字環繞** 與 **將群組形狀匯出為 PDF**。這些延伸功能讓您能以 Aspose.Words 建立複雜且程式化的文件版面配置。

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，建立在所示技術之上。每個資源皆提供完整可運作的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [使用 C# 在 Word 中建立矩形形狀 – 步驟指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [在 Word 文件中使用 Aspose.Words for .NET 建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)
- [使用陰影矩形形狀建立空白 Word 文件 – 步驟指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}