---
category: general
date: 2026-08-07
description: 使用 C# 及 Aspose.Words 插入矩形形狀，並學習如何隱藏形狀、設定填充顏色，以及高效地將矩形形狀加入 Word 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: zh-hant
lastmod: 2026-08-07
og_description: 在 Word 文件中使用 C# 插入矩形形狀。了解如何隱藏形狀、設定填充顏色，以及使用 Aspose.Words 添加矩形形狀。
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: 在 C# 中插入矩形形狀 – 完整的 Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: 在 C# 中使用 Aspose.Words 插入矩形形狀 – 逐步指南
url: /zh-hant/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中使用 Aspose.Words 插入矩形形狀 – 步驟指引

如果您需要在 C# 中於 Word 文件插入 **矩形形狀**，本指南會精確說明操作步驟。您將會看到如何設定填充顏色、隱藏形狀使其不在最終版面中顯示，以及儲存檔案——全部只需幾行程式碼。

以下各節將涵蓋您需要了解的全部內容：先決條件、完整程式碼清單、每一步的說明，以及常見變化的技巧，例如重新顯示形狀或使用不同顏色。完成後，您即可以程式方式 **新增矩形形狀** 至任何 .docx 檔案。

## 先決條件

* **Aspose.Words for .NET**（版本 23.10 或更新）。您可以透過 NuGet 安裝：

  ```bash
  dotnet add package Aspose.Words
  ```

* 已在您的機器上安裝 .NET 6.0 SDK 或更新版本。
* 具備 C# 與 Visual Studio（或您偏好的任何 IDE）的基本概念。

不需要額外的函式庫——與形狀相關的 API 已包含於核心 Aspose.Words 套件中。

## 使用 Aspose.Words 插入矩形形狀

此解決方案的核心是一個簡短且獨立的程式，會建立空白文件、插入矩形、設定顏色、隱藏形狀，最後儲存檔案。以下為完整來源程式碼，內含說明每一行背後 *原因* 的註解。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### 各步驟說明

| 步驟 | 原因 |
|------|--------|
| **Create a new document** | 提供一個乾淨的畫布；您也可以透過傳入 `new Document(path)` 的檔案路徑來載入現有的 .docx。 |
| **Initialize DocumentBuilder** | `DocumentBuilder` 是高階輔助工具，讓您在不處理低階節點樹的情況下插入文字、表格與形狀。 |
| **Insert rectangle shape** | `InsertShape` 方法會回傳一個 `Shape` 物件，您可進一步自訂（大小、位置、邊框等）。 |
| **Set fill color** | `FillColor` 屬性控制內部顏色；您可以使用任何 `Color` 值（例如 `Color.Red`、`Color.FromArgb(255, 0, 255, 0)` 等）。 |
| **Hide the shape** | `Hidden = true` 告訴 Word 在版面配置時忽略此形狀，同時仍保留於文件的 XML 中。這是儲存不可見物件的標準方式。 |
| **Save the document** | 將變更寫入 .docx 檔案。儲存的檔案將包含隱藏的矩形形狀。 |

## 如何設定形狀的填充顏色

變更填充顏色只需將 `System.Drawing.Color` 指派給 `FillColor` 屬性。若需自訂色階，可使用 `Color.FromArgb`：

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*為何重要*：填充顏色會儲存在形狀的 XML（`<w:fill>` 屬性）中。即使形狀被隱藏，顏色仍然存在，這對後續處理（例如依顏色代碼擷取中繼資料）很有用。

## 如何在最終文件中隱藏形狀

`Hidden` 旗標是 `Shape` 類別的布林屬性。將其設為 `true` 可確保 Word 版面配置引擎忽略此形狀。

```csharp
rectangleShape.Hidden = true;
```

**常見陷阱**

* **Hidden vs. Visible** – 若日後需要顯示形狀，只需將 `Hidden = false`。
* **Compatibility** – 舊版 Word（2007 前）可能以不同方式處理隱藏的繪圖物件。Aspose.Words 透過在相應的 OOXML 元素中儲存此旗標，以維持相容性。

## 如何以程式方式插入形狀

雖然範例使用矩形，但相同的 `InsertShape` 方法亦適用於許多其他形狀（橢圓、三角形、線條等）。第一個參數為 `ShapeType` 列舉值：

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**提示**：若需將形狀放置於頁面的特定位置，可在呼叫 `InsertShape` 前使用 `builder.MoveTo` 設定插入點。

## 將矩形形狀加入現有文件

通常您會在模板上進行增強，而非從頭開始。將第 1 步替換為：

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

其餘步驟保持相同，矩形將會依 builder 游標所在位置加入（預設通常在文件末端）。

## 處理邊緣情況與變化

### 1. 重新顯示形狀

若工作流程的後續階段需要顯示隱藏的矩形，您可以切換此旗標：

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. 加入邊框（筆畫）

即使形狀被隱藏，當您決定顯示時仍可保留可見的邊框。設定 `LineColor` 與 `LineWidth` 屬性：

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. 絕對定位矩形

若需精確的版面控制，可將形狀的 `WrapType` 切換為 `WrapType.Inline`（預設）或 `WrapType.TopBottom`，並調整 `Left`/`Top` 屬性：

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. 使用不同的測量單位

Aspose.Words 以點為單位（1 pt = 1/72 英吋）。若您偏好公分，請先進行換算：

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## 完整可執行範例

以下為您可以直接複製、貼上並執行的 *完整* 程式。它包含所有必要的 `using` 指令，並使用絕對路徑，您需依環境自行調整。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**預期結果**：檔案 `HiddenRectangleShape.docx` 於 Microsoft Word 開啟時 *不會顯示任何形狀*，但隱藏的矩形仍存在於文件的 XML 中。您可將 .docx 以 zip 壓縮檔方式開啟，檢查 `word/document.xml` 中是否有 `<w:shape>` 元素，且其 `w:fill="yellow"` 與 `w:hidden="true"` 屬性。

## 結論

您現在已了解如何使用 C# 與 Aspose.Words **插入矩形形狀** 至 Word 文件、如何 **設定填充顏色**，以及如何 **隱藏形狀** 使其在最終版面中保持不可見。同樣的模式亦適用於其他形狀類型、自訂顏色與現有模板。可嘗試加入邊框、絕對定位及不同測量單位，以符合您的精確需求。

### 後續步驟

* 探索 **如何在表格或頁首/頁尾內插入形狀** 以作為浮水印。
* 結合 **新增矩形形狀** 與內容控制項，建立動態佔位元。
* 檢視 Aspose.Words 的 **形狀操作** API，了解旋轉、漸層填充與 SVG 匯入等進階功能。

歡迎將程式碼套用至您的專案，並在留言中告訴我們您接下來解決了哪項與形狀相關的挑戰！

## 接下來該學什麼？

以下教學涵蓋與本指南技術密切相關的主題，並以完整可執行的程式碼範例與步驟說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [在 Word 中使用 C# 建立矩形形狀 – 步驟指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words 形狀陰影教學 – 在 C# 為 Word 形狀加入陰影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [使用 Aspose.Words for .NET 在 Word 文件中建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}