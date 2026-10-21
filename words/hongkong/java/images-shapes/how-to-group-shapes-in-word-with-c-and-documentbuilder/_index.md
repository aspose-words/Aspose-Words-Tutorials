---
category: general
date: 2026-10-04
description: 學習如何使用 C# 在 Word 中對形狀進行群組。此指南展示如何插入矩形形狀、將多個形狀群組，以及以程式方式建立空白的 Word 檔案。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: zh-hant
lastmod: 2026-10-04
og_description: 使用 C# 在 Word 中對形狀進行分組。按照本分步指南插入矩形形狀、將多個形狀分組，並使用 DocumentBuilder 建立空白
  Word 檔案。
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: 使用 C# 在 Word 中將圖形分組 – 完整 DocumentBuilder 教學
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: 如何使用 C# 與 DocumentBuilder 在 Word 中將圖形分組
url: /zh-hant/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 C# 和 DocumentBuilder 群組圖形

如果您需要在 C# 應用程式中 **在 Word 中群組圖形**，本教學將逐步說明如何操作。您將看到如何 *插入矩形圖形*、將多個繪圖合併為單一群組，最後 **建立包含群組物件的空白 Word 檔案**。

在程式化產生報告、發票或自訂範本時，操作圖形是一項常見需求。閱讀完本指南後，您將擁有可重複使用的程式碼片段，能直接放入任何參考 Aspose.Words 的 .NET 專案中。

## 您將學會

- 從頭開始 **建立空白 Word 文件**。  
- 使用 `DocumentBuilder` **插入矩形圖形與橢圓形**。  
- **將多個圖形群組** 成 `GroupShape`。  
- 使用 **append child to group** 來建構層級結構。  
- 將檔案儲存至磁碟並驗證結果。

不需要先前使用 Aspose.Words 的經驗，但您應具備 C# 與 .NET 開發的基本概念。

## 前置條件

| 需求 | 原因 |
|-------------|--------|
| .NET 6.0 or later | 提供 C# 程式碼的執行環境。 |
| Aspose.Words for .NET (latest version) | 提供 `Document`、`DocumentBuilder` 以及圖形類別。 |
| An IDE such as Visual Studio 2022 (or VS Code) | 讓您輕鬆編譯與執行範例。 |
| Write permission to a folder on your machine | 執行 `doc.save` 時所需的寫入權限。 |

透過 NuGet 安裝 Aspose.Words：

```bash
dotnet add package Aspose.Words
```

---

## 在 Word 中群組圖形 – 步驟說明指南

以下是完整且可執行的程式碼。每個區段都會詳細說明，讓您了解程式碼 **為何** 這樣寫，而不只是 **它做了什麼**。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 為何每個步驟都很重要

1. **建立空白 Word 檔案** – 從全新文件開始，可確保沒有隱藏的格式影響圖形定位。  
2. **初始化 DocumentBuilder** – `DocumentBuilder` 抽象化低階節點操作，讓您專注於版面配置。  
3. **插入個別圖形** – 您必須先有獨立的物件（`insert rectangle shape` 與橢圓形）才能進行群組。調整 `Left` 與 `Top` 可確保它們並排顯示。  
4. **群組多個圖形** – 透過建立 `GroupShape` 並使用 **append child to group**，可將兩個獨立的圖形合併為單一邏輯單元。移動或調整群組大小時，兩個子圖形會同步變化。  
5. **儲存文件** – 最終檔案 `GroupedShapes.docx` 可於 Microsoft Word 開啟，以驗證矩形與橢圓確實已群組（選取其中一個，兩者會一起移動）。

### 預期輸出

在 Microsoft Word 中開啟 `GroupedShapes.docx`：

- 您會看到矩形與橢圓並排放置。  
- 選取任一圖形時，兩者皆會被高亮，證明它們屬於同一群組。  
- 該群組可被拖曳、調整大小，或作為單一物件進行格式設定。

![Diagram of grouped rectangle and ellipse inside a Word document](https://example.com/grouped-shapes.png){: .center-image alt="Word 文件中群組的矩形與橢圓示意圖"}

*此螢幕截圖說明最終的群組圖形。*

---

## 插入矩形圖形 – 自訂大小與樣式

如果您需要具有特定填色或邊框的矩形，可在插入後修改 `Shape` 物件：

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

這些屬性屬於 `Shape` 類別，適用於任何圖形類型，而不僅限於矩形。在 **append child to group** 之前調整樣式，可確保群組繼承您設定的視覺屬性。

---

## 群組多個圖形 – 處理兩個以上的物件

本範例將矩形與橢圓群組，但您可以加入任意數量的圖形：

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**小技巧：** 建立複雜群組後，您可以鎖定其版面配置，以防止意外變更：

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – 順序很重要

呼叫 `AppendChild` 的順序決定 Z 軸順序（哪個圖形位於上方）。在範例中，先加入矩形，接著加入橢圓，若兩者相交，橢圓會覆蓋矩形。重新排序只需呼叫 `RemoveChild` 後再重新加入即可：

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## 建立空白 Word 檔案 – 可重複使用的輔助方法

如果您的應用程式經常需要全新文件，可將建立邏輯封裝起來：

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

之後您可以將主程式中的 `new Document()` 行改為 `CreateBlankWordFile()`。這示範了 **create blank word file** 概念的可重複使用方式。

---

## 常見陷阱與避免方法

| 問題 | 發生原因 | 解決方法 |
|-------|----------------|-----|
| 圖形出現在頁面之外 | 預設的 `Left`/`Top` 為 0，會將圖形放置在邊距位置。 | 插入後明確設定 `Left` 與 `Top`。 |
| 群組失去格式 | 在圖形加入群組後再變更子圖形，可能破壞群組的版面配置。 | 在呼叫 `AppendChild` 前 **先** 套用所有視覺屬性。 |
| 儲存的檔案為空 | `DocumentBuilder` 從未用於加入節點，或 `doc.Save` 被呼叫於不同的 `Document` 實例。 | 確認您儲存的是同一個已建構的 `Document`。 |
| Word 中的相容性警告 | 使用較新且未受支援的圖形功能 |  |

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與步驟說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [使用 Aspose.Words for .NET 在 Word 文件中建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words for .NET 在 Word 文件中插入圖形](/words/english/net/working-with-shapes/insert-shape/)
- [使用 C# 在 Word 中建立矩形圖形 – 步驟說明指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}