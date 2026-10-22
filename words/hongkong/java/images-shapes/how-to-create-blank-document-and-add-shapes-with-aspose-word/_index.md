---
category: general
date: 2026-09-30
description: 使用 Aspose.Words 在 C# 中建立空白文件，插入矩形、橢圓形，並將多個形狀分組。了解如何插入形狀以及如何建立分組。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: zh-hant
lastmod: 2026-09-30
og_description: 在 C# 中建立空白文件，學習如何插入形狀並使用 Aspose.Words 將多個形狀分組。請跟隨一步一步的教學。
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: 在 C# 中建立空白文件並將形狀分組 – Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: 如何在 C# 中使用 Aspose.Words 建立空白文件並加入圖形
url: /zh-hant/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用 Aspose.Words 建立空白文件並加入圖形

如果您需要 **create blank document** 並以圖形填充它，本指南將精確說明操作步驟。您將會看到如何 **insert rectangle shape**、加入其他繪圖物件，然後 **group multiple shapes**，使它們如同單一單位般運作。

在產生合約、證書或自訂報告時，處理圖形是一項常見需求。在本教學中，您將學習完整的工作流程，從初始化文件到儲存最終檔案，使用 Aspose.Words API for .NET。

## 前置條件

* 已安裝 .NET 6.0（或更新版本）SDK  
* 有效的 Aspose.Words for .NET 授權（此範例可使用免費試用版）  
* 開發環境（IDE），例如 Visual Studio 2022 或 Visual Studio Code  

除了 `Aspose.Words` 之外，無需其他 NuGet 套件。

## 如何建立空白文件並操作圖形

第一步是實例化 `Document` 物件。此物件代表記憶體中的 Word 檔案，並讓您存取 `DocumentBuilder`，它是插入內容的主要工具。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** 空白文件提供乾淨的畫布。`DocumentBuilder` 會維持目前的插入點，因此您加入的每個圖形都會自動放置在適當的頁面上。

## 插入矩形圖形與其他圖形

接著，我們加入矩形與橢圓。兩個呼叫皆使用相同的 `InsertShape` 方法，這是 Aspose.Words 中 **how to insert shapes** 的建議做法。

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*`InsertShape` 方法會自動將圖形定位於目前游標位置。* 若需精確放置，可在插入後調整 `Shape.Left` 與 `Shape.Top`。

## 將多個圖形群組為單一物件

現在我們將矩形與橢圓合併為一個邏輯實體。群組在需要同時移動或調整多個圖形大小時非常有用。

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**How this works:** `InsertGroupShape` 會建立一個容器，其行為與其他 `Shape` 相同。透過呼叫 `AppendChild`，您可將現有圖形移入容器，系統會自動更新它們的相對座標。

### 實用技巧

如果日後需要以程式方式 **how to create group** 超過兩個圖形，只需對每個額外的 `Shape` 實例重複 `AppendChild`。群組可包含任意數量的繪圖物件，包括圖片、文字方塊，甚至其他群組。

## 完整範例 – how to insert shapes 並儲存文件

以下是完整且可執行的程式碼，示範前述所有步驟。執行程式後會產生一個 `ShapesDemo.docx` 檔案，內含矩形、橢圓以及已群組的圖形。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected output:** 在 Microsoft Word 中開啟 `ShapesDemo.docx`，會看到單一頁面上有藍色矩形、綠色橢圓，以及代表群組的灰色邊框。移動該群組會同時移動兩個圖形，證實 **group multiple shapes** 操作成功。

## 常見問題與邊緣案例處理

| 問題 | 答案 |
|----------|--------|
| *如果我需要圖形出現在特定頁面上怎麼辦？* | 在插入圖形之前呼叫 `builder.MoveToDocumentEnd();`，或使用 `builder.MoveToSection(sectionIndex);` 以定位至特定節。 |
| *我可以在群組圖形內加入文字嗎？* | 可以。建立類型為 `ShapeType.TextBox` 的 `Shape`，設定其文字，然後將其 `AppendChild` 到 `GroupShape` 中。 |
| *圖形尺寸使用點（points）還是像素（pixels）？* | Aspose.Words 使用 **points**（1 pt = 1/72 inch）。此方式確保在印表機與顯示器間的尺寸一致性。 |
| *如何變更群組的旋轉角度？* | 設定 `groupShape.RotationAngle = 45;`（度）。所有子圖形會繞群組原點旋轉。 |

## 結論

您現在已了解如何使用 Aspose.Words for .NET **create blank document**、**insert rectangle shape**、以及 **how to insert shapes**（如橢圓），並將 **group multiple shapes** 成單一物件。完整程式碼範例示範了建議的做法，上述技巧則協助您將解決方案套用至更複雜的情境，例如加入文字方塊或旋轉群組。

準備好深入探索了嗎？試著將圖片圖形加入群組、實驗不同的填色，或產生每頁都有獨立群組圖表的多頁報告。相同的原則適用於所有情況，讓您能將此模式擴展至任何文件自動化專案。

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [在 Word 文件中使用 Aspose.Words for .NET 建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)
- [在 Word 文件中使用 Aspose.Words for .NET 插入圖形](/words/english/net/working-with-shapes/insert-shape/)
- [使用 Aspose.Words 建立空白 Word 文件 – 步驟指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}