---
category: general
date: 2026-11-22
description: 在 C# 中以程式方式建立 Word 文件，插入矩形形狀、插入多個形狀，並使用 Aspose.Words 將形狀寫入 Word。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: zh-hant
lastmod: 2026-11-22
og_description: 使用 C# 程式方式建立 Word 文件，插入矩形形狀、插入多個形狀，並使用 Aspose.Words 將形狀寫入 Word。
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: 以程式方式在 C# 中建立帶圖形的 Word 文件
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: 在 C# 中以程式方式建立含圖形的 Word 文件
url: /zh-hant/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 以程式方式建立 Word 文件（含圖形）— C# 範例

如果您需要 **以程式方式建立 Word 文件**，且文件中包含自訂圖形，本教學將示範如何使用 Aspose.Words for .NET 完成。您將學會插入矩形圖形、加入其他圖形、將它們分組，最後將圖形寫入 Word——全部只需幾行 C# 程式碼。

以圖形建立 Word 檔案不再需要手動編輯或巨集腳本。完成本教學後，您將擁有一個可重複使用的方法，產生包含矩形與橢圓分組的 `.docx` 檔案，供後續處理或報表使用。

## 您需要的環境

- .NET 6.0 或更新版本（此程式碼亦相容 .NET Framework 4.6+）
- Aspose.Words for .NET（NuGet 套件 `Aspose.Words`）
- 如 Visual Studio 2022 等 IDE（任何能編譯 C# 的編輯器皆可）

> **專業小技巧：** 在開始編寫程式碼前，先使用 CLI 指令 `dotnet add package Aspose.Words` 安裝套件。

## 以程式方式建立 Word 文件 – 概觀

整體流程分為三個邏輯階段：

1. **初始化** 新的 `Document` 與 `DocumentBuilder`。  
2. **插入多個圖形**（矩形與橢圓），並將它們放入 `GroupShape`。  
3. **寫入 Word**，將 `Document` 儲存為 `.docx` 檔案。

每個階段皆在下方以獨立步驟說明，您可以直接將程式碼複製貼上至專案中。

![以程式方式建立 Word 文件並分組圖形](grouped-shapes.png){: .align-center alt="以程式方式建立 Word 文件並分組圖形"}

## 步驟 1：初始化文件與建構器

`Document` 類別代表整個 Word 檔案，而 `DocumentBuilder` 提供流暢的 API 以加入內容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*為什麼這很重要：* 先建立 `Document` 能提供乾淨的畫布。`DocumentBuilder` 會追蹤目前的插入點，這在之後將圖形附加至段落層級時相當關鍵。

## 步驟 2：插入群組圖形容器

`GroupShape` 讓您將多個獨立圖形視為單一單元。當您需要一起移動或調整大小時，非常方便。

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*說明：* `InsertGroupShape` 會插入一個空的容器，並自動將其設為目前圖形。之後的所有圖形插入都會加入此容器，直到您關閉群組為止。

### 插入矩形圖形

現在加入第一個圖形——矩形。這滿足 **插入矩形圖形** 的需求。

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

矩形會繼承群組的格式環境，因而出現在 `GroupShape` 內。之後您亦可設定線條顏色、填色或文字等屬性。

### 插入多個圖形

為了示範 **插入多個圖形** 的功能，我們在矩形之後加入一個橢圓。您可以在關閉群組前持續加入任意數量的圖形（例如三角形、星形）。

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

此時群組內已包含兩個不同的圖形：矩形與橢圓。因為它們共用同一個父層，您可以一次性移動整個群組。

## 步驟 3：將群組圖形附加至段落層級

Word 文件以段落樹狀結構儲存內容。為了讓群組在最終檔案中可見，我們必須將它附加到目前的段落。

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*為什麼需要這一步：* 若未將群組附加至段落，圖形只會存在於記憶體中，文件儲存時會被省略。

## 步驟 4：儲存文件 – 將圖形寫入 Word

最後，我們將記憶體中的 `Document` 持久化至磁碟。這即完成 **將圖形寫入 Word** 的目標。

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

當您在 Microsoft Word 中開啟 `GroupShape.docx` 時，會看到一個矩形與一個橢圓已被分組，正如程式碼所插入的那樣。

### 預期輸出

- 於專案輸出資料夾產生名為 **GroupShape.docx** 的檔案。  
- 在 Word 檔案內：單一段落包含一個已分組的矩形（100 pt × 50 pt）與橢圓（80 pt × 40 pt）。選取任一圖形即會同時選取整個群組。

## 常見邊緣案例處理

| 情境 | 建議 |
|-----------|----------------|
| **不同 DPI 或頁面尺寸** | 在插入圖形前，明確設定 `builder.PageSetup.PaperSize`，以避免意外的縮放。 |
| **需要精確定位圖形** | 使用 `builder.MoveTo` 移動插入點，然後設定 `groupShape.Left` 與 `groupShape.Top` 屬性（單位為點）。 |

## 接下來您可以學習什麼？

以下教學與本指南緊密相關，能進一步深化您對 API 的掌握，並探索在實際專案中使用的其他實作方式。每篇資源皆提供完整可執行的程式碼範例與逐步說明。

- [Create Word Document – Insert Rectangle Shape & Shadow in C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Create word document programmatically and group shapes in C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programmatically create a Word document with a group shape](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}