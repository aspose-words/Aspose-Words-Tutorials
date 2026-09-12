---
category: general
date: 2026-09-11
description: 學習如何使用 Aspose.Words 建立 Word 文件、加入矩形形狀，並設定形狀尺寸。一步一步的 C# 指南，助您精確調整形狀大小。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: zh-hant
lastmod: 2026-09-11
og_description: 使用 C# 及 Aspose.Words 建立 Word 文件。本指南示範如何以程式方式加入矩形形狀、設定形狀大小及管理形狀尺寸。
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: 使用形狀建立 Word 文件 – Aspose.Words C# 教程
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: 如何在 C# 中使用 Aspose.Words 建立含有形狀的 Word 文件
url: /zh-hant/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words 在 C# 中建立含圖形的 word document

如果您需要 **create word document**（建立 Word 文件）且其中包含自訂圖形，您可以完全以程式碼完成。本教學將帶您一步步建立 Word 檔案、加入矩形圖形，並控制圖形的每個尺寸。完成後，您將擁有一段可重複使用的程式碼片段，能直接放入任何 .NET 專案中。

您將學會如何在群組容器中 **add rectangle shape**、**set shape size** 以及 **set shape dimensions**。本範例使用 Aspose.Words 13.9，但概念同樣適用於之後的版本。無需事先了解 Aspose 繪圖 API——只要具備基本的 C# 知識即可。

## Prerequisites

- .NET 6.0 或更新版本已安裝  
- Aspose.Words for .NET NuGet 套件 (`Install-Package Aspose.Words`)  
- 如 Visual Studio 2022 等 IDE（任何支援 C# 的編輯器皆可）  

具備上述工具後，您即可立即執行程式碼，無需額外設定。

## Step 1: Initialize the document and builder – create word document basics

第一步是實例化 `Document` 物件與 `DocumentBuilder`。`Document` 代表檔案本身，而 `DocumentBuilder` 提供流暢的 API 以插入內容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**為什麼這很重要：**  
預先建立文件可為您提供乾淨的畫布。建構器的游標會位於第一段落，之後我們將在此 **create shapes in word**。

## Step 2: Build a GroupShape to hold multiple graphics

步驟 2：建立 GroupShape 以容納多個圖形

`GroupShape` 如同容器；您可以將整個群組視為單一單位進行移動、旋轉或調整大小。此處我們以點 (pt) 定義容器的寬度與高度 (1 pt ≈ 1/72 in)。

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**為什麼這很重要：**  
將圖形群組化可簡化版面配置管理。若日後需要加入更多圖形（例如圓形或文字方塊），它們會繼承群組的定位與縮放。

## Step 3: Create a rectangle shape and configure its dimensions

步驟 3：建立矩形圖形並設定其尺寸

現在我們加入實際的矩形。`Shape` 建構子需要文件參考與圖形類型。建立後，我們會明確 **set shape size** 與 **set shape dimensions**。

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**為什麼這很重要：**  
指定寬度、高度、左側與上側，可讓您對圖形進行像素級的精確控制。當文件必須符合設計規範或印刷表單時，這點尤為重要。

## Step 4: Assemble the group by appending the rectangle

步驟 4：透過加入矩形組合群組

將矩形加入 `GroupShape` 後，它會成為子節點。您可以在將群組插入文件之前，加入任意數量的子節點。

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**提示：** 若您打算加入第二個圖形，請以相同方式建立，然後呼叫 `group.AppendChild(secondShape)`。所有子圖形皆共享群組的座標系統。

## Step 5: Insert the grouped shape into the document and save

步驟 5：將群組圖形插入文件並儲存

群組完成後，我們將其放入目前段落。建構器的 `CurrentParagraph` 屬性可直接存取底層節點樹。

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**為什麼這很重要：**  
將群組加入段落可確保圖形與文字流同列顯示。儲存文件即完成 **create word document** 操作。

## Common variations and edge cases

| 情境 | 調整方式 |
|----------|------------|
| **不同的頁面方向** | 在建立群組之前設定 `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;`。 |
| **多個矩形** | 建立額外的 `Shape` 物件，並對每個呼叫 `group.AppendChild(newRect)`。 |
| **根據內容動態調整大小** | 根據影像尺寸或文字度量計算寬度/高度，然後指派給 `rectangle.Width` / `rectangle.Height`。 |
| **匯出為 PDF** | 在 `doc.Save` 之後，呼叫 `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`。 |
| **相容舊版 Word** | 使用 `SaveFormat.Doc` 而非 `Docx` 儲存，以相容 Word 97‑2003。 |

這些變化說明了相同的核心邏輯如何套用於許多實務需求。

## Full, runnable example

完整、可執行的範例

以下是完整的程式碼，您可以複製、貼上並執行。它包含所有 `using` 指令、`Main` 入口點，以及說明每一行的註解。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**預期輸出：**  
開啟 *GroupShape.docx* 後，第一頁會顯示一個灰色邊框的矩形，距離左/上邊距 50 pt，且矩形本身在群組內部偏移 10 pt。尺寸與程式碼中設定的值相符。

## Conclusion

結論

您現在已了解如何使用 Aspose.Words **create word document**、**add rectangle shape**，以及精確 **set shape size** 與 **set shape dimensions**。群組圖形的做法讓您的版面保持彈性，且可隨時擴充，例如加入其他圖形或文字方塊。

接下來，您可以探索相關主題，例如 **create shapes in word**（圓形、箭頭或自訂 SVG 路徑），以及學習如何 **set shape fill color** 或 **apply rotation**。嘗試不同的測量單位，觀察 Word 如何呈現點與公分的差異，並將程式碼整合至更大型的文件產生流程中。

祝程式開發順利，隨時依需求調整此模式，以應對任何自動化報告或表單填寫的情境！

## What Should You Learn Next?

接下來您可以學習什麼？

以下教學涵蓋與本指南密切相關的主題，並在此基礎上延伸技術。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索替代的實作方式。

- [使用 C# 在 Word 中建立矩形圖形 – 步驟指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [建立帶陰影矩形圖形的空白 Word 文件 – 步驟指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words 圖形陰影教學 – 在 C# 中為 Word 圖形加入陰影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}