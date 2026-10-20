---
category: general
date: 2026-09-18
description: 使用 Aspose.Words 建立空白 Word 文件並隱藏橢圓形狀。學習如何在 Word 中隱藏形狀、如何插入橢圓，以及如何快速建立隱藏形狀。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: zh-hant
lastmod: 2026-09-18
og_description: 在 Word 中建立空白 Word 文件並隱藏橢圓形狀。本指南將逐步說明如何在 Word 中插入橢圓形、隱藏形狀，以及使用 Aspose.Words
  建立隱藏形狀。
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: 建立一個包含隱藏橢圓形狀的空白 Word 文件
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 建立一個帶有隱藏橢圓形的空白 Word 文檔
url: /zh-hant/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立一個帶有隱藏橢圓形狀的空白 Word 文件

如果您需要 **建立一個空白的 Word 文件**，且其中包含一個您不想在版面上顯示的圖形，本指南將完整說明如何操作。透過使用 Aspose.Words for .NET，您可以以程式方式插入橢圓，然後隱藏該圖形，使文件在視覺上保持空白，同時仍保留圖形資料。

在本教學中，您將學會：

* 如何 **建立空白 Word 文件** 物件，
* 如何使用 `DocumentBuilder` **插入橢圓**，
* 如何 **在 Word 中隱藏圖形** 使其不影響頁面，
* 如何 **建立隱藏圖形** 物件以供之後處理。

這些步驟適用於 .NET 6 以上版本以及最新的 Aspose.Words 版本（撰寫時為 23.9）。不需要額外安裝 Office。

## 前置條件

* Visual Studio 2022（或任何 C# IDE）
* .NET 6 SDK 或更新版本
* Aspose.Words for .NET NuGet 套件  
  ```bash
  dotnet add package Aspose.Words
  ```
* 具備 C# 與 Word 文件概念的基本知識

## 步驟 1：建立空白 Word 文件

您首先需要做的是實例化一個 `Document` 物件。此物件代表一個空的 `.docx` 檔案，是所有後續操作的基礎。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

建立 **空白 Word 文件** 為您提供一個乾淨的畫布——沒有段落、沒有章節，僅有底層的封裝結構。當您只需要一個隱藏圖形而不需要其他內容時，這是理想的起點。

## 步驟 2：初始化 DocumentBuilder

`DocumentBuilder` 提供了方便的 API 以向 `Document` 中加入內容。它的運作方式類似於在文件中移動的游標。

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

建構器會自動建立預設的第一個章節與段落，讓您可以直接插入圖形，而無需手動新增章節。

## 步驟 3：插入橢圓形狀

現在我們使用 `InsertShape` 方法 **插入橢圓**。此方法接受 `ShapeType` 列舉、寬度以及高度（以點為單位）。

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

為什麼選擇橢圓？橢圓是一種向量圖形，可在不影響周圍文字流的情況下隱藏。寬度 100 pt 與高度 50 pt 只是示範值，您可以依後續處理需求自行調整。

## 步驟 4：隱藏圖形，使其不出現在版面上

若要 **在 Word 中隱藏圖形**，請將 `Shape` 物件的 `Hidden` 屬性設為 `true`。當文件在 Microsoft Word 中開啟時，該圖形將不可見，且不會佔用版面空間。

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

`Hidden` 標誌會儲存在圖形的 XML 中（`<w:hidden/>`）。Word 在渲染時會遵守此屬性，這就是為什麼文件看起來完全空白，儘管圖形仍然存在的原因。

### 小技巧

如果之後需要再次顯示圖形，只需將 `ellipse.Hidden = false;` 設為 `false`，然後儲存文件即可。

## 步驟 5：儲存帶有隱藏圖形的文件

最後，將文件寫入磁碟。此檔案將是一個普通的 `.docx`，任何 Word 處理程式皆可開啟。

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

儲存的檔案 `HiddenEllipse.docx` 是一個 **建立空白 Word 文件**，其中包含隱藏的橢圓。於 Microsoft Word 中開啟時會顯示空白頁面，但圖形仍存在於 Open XML 結構中。

## 完整範例程式

以下是完整、獨立的程式範例，您可以直接複製、貼上並執行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**預期輸出**

* 會在 `C:\Temp` 產生名為 `HiddenEllipse.docx` 的檔案。
* 在 Microsoft Word 中開啟該檔案會顯示完全空白的頁面。
* 若使用 Open XML SDK 或 zip 檢視工具檢查文件，您會在文件部件中找到帶有 `<w:hidden/>` 的 `<w:shape>` 元素。

## 常見問題與邊緣情況

### 如果圖形仍然顯示該怎麼辦？

* 確認您使用的是 Aspose.Words 23.9 或更新版本——舊版曾有 `Hidden` 在某些圖形類型上被忽略的錯誤。
* 確認未套用任何額外的格式設定（例如 `WrapType`），該設定會迫使圖形佔用版面空間。

### 我可以隱藏其他圖形類型嗎？

可以。相同的 `Hidden` 屬性同樣適用於 `ShapeType.Rectangle`、`ShapeType.Picture` 等。只需將 `ShapeType.Ellipse` 替換為您想要的類型即可。

### 之後如何列出隱藏的圖形？

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

此程式碼片段會遍歷所有圖形，並列印出隱藏的圖形，對於需要在之後處理或取消隱藏的 **建立隱藏圖形** 工作流程非常有用。

## 結論

現在您已了解如何 **建立空白 Word 文件**、**插入橢圓**，以及 **在 Word 中隱藏圖形**，以產生對讀者不可見的 **建立隱藏圖形**。此技巧可用於在文件中儲存中繼資料、書籤或自訂 XML，而不會改變其視覺外觀。

### 後續步驟

* 探索如何根據文件內容條件式 **隱藏圖形**。
* 了解在產生最終文件版本時 **取消隱藏圖形** 的方法。
* 結合隱藏圖形與 **自訂文件屬性**，以嵌入機器可讀的資料。

歡迎嘗試不同的圖形類型、尺寸與隱藏狀態邏輯，以符合您的自動化情境。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [建立帶陰影矩形形狀的空白 Word 文件 – 步驟說明指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [在 Word 中使用 Aspose.Words 建立矩形形狀 – 步驟說明指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [使用 Aspose.Words for .NET 在 Word 文件中建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}