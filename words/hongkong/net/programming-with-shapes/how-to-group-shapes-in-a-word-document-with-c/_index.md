---
category: general
date: 2026-08-14
description: 如何使用 C# 在 Word 文件中對形狀進行群組。學習建立 Word 文件、插入矩形形狀、在 Word 中群組形狀，並將文件儲存為 docx。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: zh-hant
lastmod: 2026-08-14
og_description: 如何使用 C# 在 Word 文件中對圖形進行群組。請跟隨本完整教學，建立 Word 檔案、插入矩形圖形、在 Word 中群組圖形，並將結果儲存為
  docx。
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: 如何使用 C# 在 Word 文件中將形狀分組 – 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: 如何使用 C# 在 Word 文件中將形狀分組
url: /zh-hant/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 C# 群組形狀

如果您需要 **how to group shapes**（在 Word 文件中群組形狀），本指南將示範使用 C# 及 Aspose.Words 函式庫的完整步驟。您將會看到如何建立 Word 文件、插入矩形形狀、在 Word 中群組形狀，最後 **save document as docx**——全部於一個可執行的程式中完成。

在程式化產生報告、合約或行銷手冊時，建立與操作形狀是常見需求。完成本教學後，您將擁有可重複使用的程式碼片段，能直接嵌入任何 .NET 專案中。

## 前置條件

- .NET 6.0 或更新版本已安裝  
- Visual Studio 2022（或任何支援 .NET 的 IDE）  
- Aspose.Words for .NET 授權（或免費試用）  
- 基本的 C# 語法熟悉度  

除了 `Aspose.Words` 之外，無需其他 NuGet 套件。

## 如何在 Word 文件中群組形狀

此解決方案的核心是一個五步驟流程。每一步都會詳細說明，完整的原始程式碼則放在文章最後。

### 步驟 1：建立新的空白文件

當您想要以程式方式 **create Word document** 時，第一件事就是實例化 `Document` 物件。此物件在記憶體中代表整個 .docx 檔案。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** `DocumentBuilder` 是高階輔助工具，可讓您插入文字、表格與形狀，而不必手動處理底層節點樹。

### 步驟 2：插入矩形形狀

為了示範 **insert rectangle shape**，我們使用 `InsertShape` 方法。此矩形將作為群組的第一個成員。

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Why this matters:** 形狀的位置是相對於插入點定位的。設定填色可讓您在開啟產生的文件時看見該形狀。

### 步驟 3：插入橢圓形狀

接著，我們 **insert ellipse shape**（API 稱為 `Ellipse`）。這將成為群組的第二個成員。

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Why this matters:** 立即在矩形之後插入橢圓，兩個形狀會位於同一段落，這樣在之後群組時會更簡單。

### 步驟 4：群組矩形與橢圓

現在我們回答核心問題 **how to group shapes**（在 Word 文件中群組形狀）。Aspose.Words 提供 `AppendGroupShape` 以建立群組容器，之後對該容器呼叫 `Group()`。

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Why this matters:** 一旦群組後，對 `groupedShape` 施加的任何變換（移動、調整大小、旋轉）都會自動影響矩形與橢圓。這對於在產生的文件中維持版面一致性至關重要。

### 步驟 5：將文件儲存為 DOCX 檔案

最後一步是 **save document as docx**。您可以自行選擇路徑；範例使用佔位字串 `"YOUR_DIRECTORY"`，請將其替換為實際資料夾。

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Why this matters:** 以 DOCX 格式儲存會保留群組的中繼資料，當您在 Microsoft Word 中開啟檔案時，矩形與橢圓會顯示為單一物件。

## 完整、可執行範例

以下是結合全部五個步驟的完整程式。將其複製到新的主控台專案中，還原 Aspose.Words NuGet 套件，然後執行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### 預期輸出

當您在 Microsoft Word 中開啟 `groupedShapes.docx` 時，會看到一個淡藍色的矩形與一個淡珊瑚色的橢圓被鎖定在一起。點擊任一形狀即會同時選取兩者，讓您能將它們作為單一單位移動或調整大小。

## 常見問題與邊緣情況

| 問題 | 答案 |
|----------|--------|
| **Can I group more than two shapes?** | 可以。將任意數量的 `Shape` 物件傳遞給 `AppendGroupShape`。此方法接受陣列，您可以動態建立集合。 |
| **What if I need the group to be anchored to a table cell?** | 如果需要將群組錨定於表格儲存格，請將形狀插入該儲存格的段落中，然後在該段落上呼叫 `AppendGroupShape`。群組會繼承儲存格的錨定方式。 |
| **Does grouping affect the underlying XML?** | 群組會影響底層 XML 嗎？Aspose.Words 會寫入一個 `<w:grpSp>` 元素，內含子形狀。Word 會將其識別為群組，並保留相對位置。 |
| **How do I ungroup later?** | 稍後若要解除群組，呼叫 `groupedShape.Ungroup()`；此方法會回傳各個形狀，讓您可以分別操作。 |
| **Is there a performance impact when grouping many shapes?** | 大量形狀群組會有效能影響嗎？群組本身開銷不大，但渲染非常大的群組（數百個形狀）可能會增加檔案大小。若檔案尺寸成為問題，請考慮將影像平面化。 |

## 專業技巧

- **Set explicit positions** (`Left`, `Top`) 若需在群組前進行精確對齊，請設定明確的位置。  
- **Use `Shape.WrapType = WrapType.Inline`** 當您希望群組的行為類似段落元素而非浮動物件時，請使用此設定。  
- **Apply a line style** 給群組 (`groupedShape.LineFormat`) 以為整個集合加上邊框。  
- **Reuse the group**：在呼叫 `Group()` 後，您可以複製 `groupedShape`，並將複本插入文件的其他位置。  

## 下一步

既然您已了解 **how to group shapes**（在 Word 文件中群組形狀），可以進一步探索相關主題，例如：

- **Insert rectangle shape** 在形狀內加入自訂文字或圖片。  
- **Create complex diagrams** 透過巢狀群組（群組內再群組）來建立複雜圖表。  
- **Export the document as PDF** 同時保留形狀群組 (`doc.Save("output.pdf", SaveFormat.Pdf)`)。  

上述每項皆建立在本教學所涵蓋的相同基礎上，讓您能順利擴充 Word 自動化工具箱。

## 結論

本教學示範了使用 C# 在 Word 文件中 **how to group shapes**。您學會了 **create Word document**、**insert rectangle shape**、**group shapes in Word**，以及最後的 **save document as docx**。透過完整且可執行的範例與實用技巧，您即可將形狀群組整合至任何文件產生工作流程。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此技術為基礎。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [在 Word 文件中使用 Aspose.Words for .NET 建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)
- [在 Word 文件中使用 Aspose.Words for .NET 插入形狀](/words/english/net/working-with-shapes/insert-shape/)
- [使用 C# 在 Word 中建立矩形形狀 – 步驟指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}