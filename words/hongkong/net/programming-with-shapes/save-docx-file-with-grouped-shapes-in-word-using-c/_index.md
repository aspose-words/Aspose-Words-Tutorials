---
category: general
date: 2026-08-04
description: 在 Word 中以程式方式儲存 docx 檔案，同時加入矩形形狀與群組形狀。學習如何設定形狀尺寸以及以程式方式建立文字方塊。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: zh-hant
lastmod: 2026-08-04
og_description: 使用 C# 透過新增矩形形狀、在 Word 中將形狀分組、設定形狀尺寸，以及程式化建立文字方塊，來儲存 docx 檔案。
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: 在 Word 中將帶有已分組圖形的 docx 檔案儲存 – C# 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 C# 在 Word 中儲存含有組合圖形的 docx 檔案
url: /zh-hant/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 C# 保存含有群組圖形的 docx 檔案

如果您需要 **save docx file** 且其中包含多個一起排列的圖形，本指南將示範如何使用 C# 完成。您將學習如何 **add rectangle shape**、在 Word 文件中群組多個圖形、**set shape dimensions**，以及 **create textbox programmatically**。此解決方案相容於最新的 Aspose.Words for .NET，並可在 .NET 6 或更高版本上執行。

本教學會逐步說明每個步驟，從專案設定到最後的 `doc.Save` 呼叫。完成後，您將擁有可重複使用的程式碼片段，可貼入任何 Console 或 ASP.NET 專案中。無需外部腳本或手動編輯 DOCX 檔案。

## 前置條件

* .NET 6 SDK（或更新版本）已安裝。
* 有效的 **Aspose.Words for .NET** 授權（免費試用版可用於測試）。
* Visual Studio 2022、VS Code，或任何能建置 .NET 專案的 IDE。

程式碼僅使用 Aspose.Words 命名空間，無需額外的 NuGet 套件。

## 在 Word 中保存含有群組圖形的 docx 檔案

解決方案的核心是建立一個包含矩形與文字方塊的 `GroupShape`，然後將該群組插入文件並呼叫 `doc.Save`。以下各節將此流程分解為易於處理的步驟。

### 1. 建立新文件與 Builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this step matters* – 全新的 `Document` 物件代表一個空的 *.docx* 檔案。`DocumentBuilder` 提供高階方法，例如 `InsertNode`，我們將使用它來放置群組圖形。

### 2. 將矩形圖形加入群組

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Why this step matters* – **add rectangle shape** 操作示範如何以精確的尺寸與位置定義視覺元素。矩形位於 `group` 內部，之後移動群組時會自動一起移動矩形。

### 3. 在 Word 文件中群組圖形

`GroupShape` 類別會聚合多個繪圖物件。當您希望將多個物件視為單一單位（例如一起移動、旋轉或複製）時，群組功能非常有用。

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Why we group* – 群組可降低版面配置的複雜度。您不必在頁面上分別定位每個圖形，只需一次調整群組的 `Left`、`Top`、`Width` 與 `Height` 即可。

### 4. 設定圖形尺寸以獲得精確版面

群組本身與其子圖形皆需明確設定尺寸；否則 Word 會套用預設大小，可能與您的設計不符。

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Why we set dimensions* – 精確的測量可確保矩形與文字方塊不會意外重疊，且最終的 **save docx file** 符合預期的版面配置。

### 5. 在群組內以程式方式建立文字方塊

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Why this step matters* – **create textbox programmatically** 片段示範如何在圖形內嵌入豐富文字。透過 `Paragraph` 與 `Run`，您可在之後完整控制格式設定。

### 6. 插入群組圖形並 **save docx file**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Why this final step matters* – `InsertNode` 呼叫會將群組圖形精確放置在 Builder 游標所在的位置。`doc.Save` 方法執行 **save docx file** 操作，將完整功能的 Word 文件寫入磁碟。

> **Result:** 開啟 Microsoft Word 中的 *GroupShape.docx* 後，左側會顯示一個矩形，右側會顯示一個文字方塊，兩者均被鎖定在同一個群組內。您可以將整個群組作為單位移動、調整大小，或套用其他格式設定。

## 完整、可執行範例

將以下程式碼複製到新的 Console 專案（`dotnet new console`）中，然後執行 `dotnet run`。程式會在專案的輸出資料夾中產生 `GroupShape.docx`。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### 預期輸出

* 輸出目錄中會出現名為 **GroupShape.docx** 的檔案。
* 開啟該檔案時，左側顯示矩形圖形，右側顯示包含「Grouped text」的文字方塊，兩者均被鎖定在一起。
* 選取任一圖形會移動整個群組，證實 **group shapes word** 功能如預期運作。

## 常見變體與邊緣案例

| 情況 | 建議 |
|-----------|----------------|
| 需要超過兩個圖形 | 在呼叫 `builder.InsertNode` 之前，將額外的 `Shape` 物件附加到 `group`。 |
| 希望群組顯示在特定頁面 | 使用 `builder.MoveToDocumentEnd()` 或 `builder.MoveToPage(pageNumber)` 移動 Builder 的游標。 |
| 需要不同的單位（例如公分） | 使用 `ConvertUtil.InchToPoint(1.0)` 將英吋轉換為點（Word 所使用的單位）。 |
| 希望文字方塊換行 | 在建立文字方塊後，設定 `textBox.TextBoxWrap = TextBoxWrapType.Square`。 |
| 使用較舊的 .NET Framework 版本 | 相同的 API 可在 .NET Framework 4.7 以上使用，但請確保參考正確的 Aspose.Words 版本。 |

**Pro tip:** 在加入所有子圖形之後，務必設定群組的 `Width` 與 `Height` *after*。這可確保群組完整包覆其內容，避免文件在 Word 中開啟時被裁切。

## 結論

現在您已了解如何使用 Aspose.Words for .NET **save docx file** 同時 **add rectangle shape**、**group shapes word**、**set shape dimensions**，以及 **create textbox programmatically**。完整範例展示了一個簡潔且可重複使用的模式，您可以將其套用於更複雜的版面配置，例如圖表、圖片，

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [在 Word 中使用 C# 建立矩形圖形 – 步驟說明指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [在 Word 文件中使用 Aspose.Words for .NET 建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words 圖形陰影教學 – 在 C# 中為 Word 圖形新增陰影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}