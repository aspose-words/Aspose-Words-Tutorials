---
category: general
date: 2026-08-04
description: 使用 C# 在 Word 文件中插入矩形形狀。了解如何在 Word 中對形狀進行分組、將文件另存為 docx，並使用 DocumentBuilder
  進行進階版面配置。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: zh-hant
lastmod: 2026-08-04
og_description: 在 Word 檔案中使用 C# 插入矩形形狀，然後將形狀群組以實現進階版面配置。本教學亦說明如何將文件另存為 docx 以及高效使用
  DocumentBuilder。
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: 在 Word 中插入矩形形狀 – C# 步驟教學
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 C# 在 Word 中插入矩形形狀 – 完整指南
url: /zh-hant/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 C# 插入矩形形狀 – 完整指南

如果你需要在 Word 文件中使用 C# **插入矩形形狀**，本教學會一步步示範。你亦會學習 **如何在 Word 中群組形狀**、**將文件儲存為 docx**，以及 **如何使用 Builder** 以撰寫乾淨且易於維護的程式碼。

在程式中產生報告、證書或自訂版面時，常會需要操作形狀。完成本指南後，你將擁有一個完整可執行的範例，能建立矩形、加入橢圓、將它們群組，並將結果儲存為 DOCX 檔案。

## 前置條件

在開始之前，請確保你已具備：

* 已安裝 .NET 6.0 或更新版本  
* Visual Studio 2022（或任何支援 C# 的 IDE）  
* **Aspose.Words for .NET** 函式庫（可透過 NuGet 取得）  

你可以使用以下指令加入函式庫：

```bash
dotnet add package Aspose.Words
```

## 使用 DocumentBuilder 插入矩形形狀

第一步是建立新的 `Document` 與 `DocumentBuilder`。Builder 提供流暢的 API 以插入內容，包括形狀。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` 實例是你用來 **插入矩形形狀** 以及其他元素的核心物件。它會追蹤文件內目前的游標位置，確保所有插入都發生在正確的位置。

## 如何插入矩形形狀

Builder 準備好後，呼叫 `InsertShape`。你需要指定 `ShapeType`、寬度與高度（單位為點，1 pt ≈ 1/72 in）。

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*為什麼這很重要*：設定 `FillColor` 與 `StrokeColor` 會讓矩形在視覺上更明顯，方便之後與其他形狀一起群組。

## 如何在 Word 中群組形狀

群組形狀可讓你將多個物件視為單一實體來移動、旋轉或格式化。插入矩形後，加入另一個形狀（本例中的橢圓），再建立 `GroupShape`。

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

`InsertGroupShape` 呼叫會建立一個可容納任意數量子形狀的佔位元。將矩形與橢圓加入其中，即可實際 **在 Word 中群組形狀**。此群組會像單一形狀一樣運作——你可以重新定位、套用邊框或調整大小，而不會影響每個子形狀的內部版面配置。

### 專業提示

群組完成後，你可以變更群組相對於頁面的定位：

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## 將文件儲存為 docx

形狀排好後，需要將檔案寫入磁碟。`Document.Save` 方法會自動依檔案副檔名判斷格式。若要 **將文件儲存為 docx**，只要傳入以 `.docx` 結尾的路徑即可。

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

執行程式會產生 `output.docx`。在 Microsoft Word 中開啟檔案，你會看到一個淡藍色矩形與淡珊瑚色橢圓已被群組。點選該群組即可將其作為單一物件移動。

## 如何有效使用 DocumentBuilder

`DocumentBuilder` 不只是插入形狀的工具；它同時處理文字、表格、頁首與頁尾。當你將形狀建立與文字結合時，若需在其他位置插入內容，請記得重設游標：

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

明確維持 Builder 的狀態可避免意外覆寫，讓程式碼更易於維護。

## 邊緣情況與變化

| 情況 | 建議做法 |
|-----------|----------------------|
| **超過兩個形狀** | 依序插入每個形狀，然後在儲存前對每個形狀呼叫 `AppendChild`。 |
| **巢狀群組** | 建立一個群組，加入形狀後，再將該群組插入另一個 `GroupShape`。 |
| **不同的測量單位** | 若尺寸以像素為單位，使用 `builder.ConvertPixelsToPoints`。 |
| **相容舊版 Word** | 變更副檔名為 `.doc` 以儲存；大多數形狀功能仍可使用。 |

## 完整可執行範例

以下是完整程式碼，你可以直接複製貼上至新的 Console 專案中。無需額外片段。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**預期結果**：開啟 `output.docx` 後會看到一個淡藍色矩形與淡珊瑚色橢圓已被群組，且左邊距 150 pt、上邊距 100 pt。說明文字會出現在群組下方。

## 結論

現在你已了解如何使用 C# **插入矩形形狀** 到 Word 檔案、**在 Word 中群組形狀**，以及使用 Aspose.Words 的 `DocumentBuilder` **將文件儲存為 docx**。掌握這些步驟後，你即可透過程式碼建立複雜版面——如證書、報告或自訂表單。

接下來，可探索相關主題，例如 **加入文字方塊**、**操作表格**，或 **匯出為 PDF**。這些皆以你剛剛練習的 `DocumentBuilder` 基礎為出發點。

準備好自動化你的 Word 文件了嗎？試著為範例加入更多形狀、套用漸層，或以迴圈處理資料一次產生完整報告。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助你掌握更多 API 功能，並在專案中探索其他實作方式。

- [使用 Aspose.Words for .NET 在 Word 文件中建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words for .NET 在 Word 文件中插入形狀](/words/english/net/working-with-shapes/insert-shape/)
- [使用 Aspose.Words 在 Word 中建立矩形形狀 – 步驟指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}