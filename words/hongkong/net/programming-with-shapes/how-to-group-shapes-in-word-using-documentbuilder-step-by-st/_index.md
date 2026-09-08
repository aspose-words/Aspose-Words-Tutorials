---
category: general
date: 2026-09-08
description: 學習如何使用 DocumentBuilder 在 Word 中對形狀進行分組、建立空白 Word 文件，並僅用幾行 C# 程式碼插入矩形形狀。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: zh-hant
lastmod: 2026-09-08
og_description: 使用 DocumentBuilder 在 Word 中對形狀進行分組。此教學示範如何建立空白 Word 文件、插入矩形形狀，並將形狀合併為
  GroupShape。
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: 在 Word 中使用 DocumentBuilder 分組圖形 – 完整 C# 範例
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 DocumentBuilder 在 Word 中分組圖形 – 步驟指南
url: /zh-hant/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 DocumentBuilder 在 Word 中對形狀進行分組 – 步驟說明指南

如果您需要以程式方式 **在 Word 中對形狀進行分組**，本教學提供完整的 C# 解決方案。您將會看到如何 **建立空白 Word 文件**、使用 **DocumentBuilder**，以及 **插入矩形形狀**，然後再與橢圓形進行分組。最終會得到一個可作為單一物件移動、調整大小或設定樣式的 `GroupShape`。

本指南涵蓋使用 Aspose.Words for .NET 函式庫產生含有分組圖形的 Word 文件所需的全部知識。閱讀完本文後，您將擁有一個可執行的專案，產生的 `GroupedShapes.docx` 內含一個矩形與橢圓形組合成的單一形狀。

## 前置條件

- .NET 6.0 或更新版本（程式碼亦相容於 .NET Framework 4.7.2 以上）
- Aspose.Words for .NET NuGet 套件（`Aspose.Words`）– 版本 23.12 或更新
- C# 開發環境，例如 Visual Studio 2022 或 Visual Studio Code
- 具備 C# 語法與物件導向程式設計的基本概念

> **小技巧：** 從命令列安裝 NuGet 套件，以保持專案整潔：  
> `dotnet add package Aspose.Words --version 23.12.0`

## 步驟 1：建立空白 Word 文件

第一步是實例化 `Document` 物件，它代表一個空的 Word 檔案，並建立 `DocumentBuilder` 以便加入內容。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**為什麼這很重要：** `Document` 提供檔案容器，而 `DocumentBuilder` 則提供流暢的 API 來插入文字、圖片與形狀。若沒有 `DocumentBuilder`，您必須手動操作文件的節點樹，容易出錯。

## 步驟 2：插入矩形形狀

矩形是圖表常見的組件。使用 `InsertShape` 搭配 `ShapeType.Rectangle`，並以點 (pt) 為單位指定寬度與高度 (1 pt ≈ 1/72 in)。

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**為什麼這很重要：** 設定 `Left` 與 `Top` 可將矩形精確定位於頁面上，這對之後與其他形狀分組至關重要。`InsertShape` 方法會自動將形狀加入目前段落。

## 步驟 3：插入橢圓形狀

接著，加入一個會位於矩形旁邊的橢圓形。

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**為什麼這很重要：** 使用不同的 `ShapeType` 可展示相同的 `DocumentBuilder` API 能產生多樣的圖形。將橢圓形定位於與矩形重疊，可明顯呈現分組效果。

## 步驟 4：將兩個形狀分組

`GroupShape` 如同容器。將矩形與橢圓形以子形狀方式加入，即可讓它們作為單一物件運作。

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**為什麼這很重要：** `Bounds` 屬性告訴 Word 分組在頁面上的位置。透過加入子形狀，您保留各自的格式，同時可對整個群組執行統一的變換（移動、旋轉、調整大小）。

## 步驟 5：儲存文件

最後，將文件寫入磁碟。您可以自行更改儲存路徑至任意資料夾。

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

當您在 Microsoft Word 中開啟 `GroupedShapes.docx` 時，會看到已分組的矩形與橢圓形。選取該群組會同時突顯兩個形狀，讓您能以單一單位拖曳或調整大小。

### 預期輸出

- 一個名為 **GroupedShapes.docx** 的 Word 檔案
- 第一頁包含一個 **矩形**（100 pt × 50 pt），位置為 (50, 50)
- 一個 **橢圓形**（80 pt × 80 pt），位置為 (200, 70)
- 兩個形狀皆屬於一個 **GroupShape**，其外框尺寸為 300 pt × 200 pt

## 常見變形與例外情況

| 情境 | 調整 |
|----------|------------|
| **不同的頁面尺寸** | 在插入形狀之前設定 `document.Sections[0].PageSetup.PageWidth` 與 `PageHeight`。 |
| **超過兩個形狀** | 建立額外的 `Shape` 物件，並對每個呼叫 `groupShape.AppendChild(newShape)`。 |
| **套用填充顏色** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **旋轉群組** | `groupShape.Rotation = 45;`（度） |
| **匯出為 PDF** | 儲存 DOCX 後，呼叫 `document.Save("GroupedShapes.pdf");` |

## 完整原始碼（可直接執行）

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

將程式碼複製到新的 Console 專案中，還原 Aspose.Words NuGet 套件，然後執行。主控台會顯示檔案路徑，開啟檔案即可看到分組圖形。

## 結論

現在您已了解如何使用 Aspose.Words 的 `DocumentBuilder` **在 Word 中對形狀進行分組**。本教學示範了建立 **空白 Word 文件**、**插入矩形形狀**、加入橢圓形，並將它們組合成 `GroupShape` 的步驟。憑藉此基礎，您可以直接從 C# 建立更豐富的圖表、流程圖或自訂圖形。

### 接下來可以做什麼？

- 探索 **如何使用 DocumentBuilder** 來建立表格、頁首與頁尾。
- 將 **insert rectangle shape Word** 技巧與文字方塊結合，用於註解圖表。
- 使用 **create blank word doc** 作為自動化報告產生的範本。

歡迎自行嘗試不同的顏色、漸層與其他形狀。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並在此基礎上進一步說明。每篇資源皆提供完整可執行的程式碼範例與步驟說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [使用 Aspose.Words for .NET 在 Word 文件中建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words for .NET 在 Word 文件中插入形狀](/words/english/net/working-with-shapes/insert-shape/)
- [使用 C# 在 Word 中建立矩形形狀 – 步驟說明指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}