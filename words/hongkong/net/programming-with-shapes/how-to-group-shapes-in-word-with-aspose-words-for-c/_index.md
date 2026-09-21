---
category: general
date: 2026-09-21
description: 學習如何在 Word 中使用 Aspose.Words for C# 進行形狀分組。本分步指南涵蓋形狀的建立、定位及儲存分組形狀。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: zh-hant
lastmod: 2026-09-21
og_description: 使用 Aspose.Words for C# 在 Word 中將形狀群組化。請跟隨本簡明教學，以程式方式建立、定位及儲存群組形狀。
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: 使用 Aspose.Words 在 Word 中分組形狀 – 完整 C# 教程
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 如何在 Word 中使用 Aspose.Words for C# 將圖形分組
url: /zh-hant/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 Aspose.Words for C# 進行圖形分組

如果您需要以程式方式 **在 Word 中分組圖形**，Aspose.Words 讓此操作變得相當簡單。本教學將示範如何建立兩個矩形圖形、將它們並排放置、合併成 `GroupShape`，並將結果儲存為 DOCX 檔案。

您將看到完整且可執行的範例、每一步驟的重要說明，以及處理常見邊緣情況（例如圖形重疊或動態尺寸）的技巧。完成本指南後，您即可在任何 Word 自動化專案中整合圖形分組功能。

## 前置條件

開始之前，請確保您已具備：

* 已安裝 .NET 6.0（或更新版本） – Aspose.Words 支援 .NET Standard 2.0+、.NET Core 與 .NET Framework。
* 有效的 Aspose.Words for .NET 授權（或暫時的評估金鑰） – 未授權時仍可使用，但會加上浮水印。
* Visual Studio 2022（或任何 C# IDE）以編譯與執行範例。

除 `Aspose.Words` 之外，無需額外的 NuGet 套件。

## 使用 Aspose.Words 在 Word 中分組圖形的方法

解決方案的核心是一個 **`GroupShape`** 物件，它充當個別圖形的容器。以下將步驟清晰拆解說明。

### 步驟 1：建立空白文件與 `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*為什麼需要這一步？*  
`Document` 代表整個 DOCX 檔案，而 `DocumentBuilder` 提供流暢的 API（例如 `InsertShape`），可自動將新元素插入目前游標所在位置。

### 步驟 2：插入第一個矩形圖形

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

`InsertShape` 呼叫會將圖形加入文件，並回傳可進一步設定（顏色、邊框等）的 `Shape` 物件。尺寸以點為單位（1 pt ≈ 1/72 in）。

### 步驟 3：插入第二個矩形並設定偏移

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

設定 `Left` 會將圖形相對於頁面邊距定位。偏移量必須大於第一個圖形的寬度（100 pt），以避免重疊；此處使用 120 pt 以留下少許間隙。

### 步驟 4：建立足以容納兩個矩形的 `GroupShape`

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` 需要傳入所屬的 `Document` 以及容器尺寸。容器寬度應超過最右側圖形的右邊緣，否則第二個圖形會被裁切。

### 步驟 5：將個別圖形加入群組

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

加入後，圖形會移至群組的內部集合。此時這些圖形不再是文件樹中的獨立物件，而是屬於群組。

### 步驟 6：將群組圖形重新插入文件

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` 會把整個 `GroupShape` 放置在目前游標所在的位置。若需將群組放入特定段落，先將 builder 移至該段落再執行此步驟。

### 步驟 7：儲存文件

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

產生的檔案包含兩個矩形，且它們會作為單一物件運作——在 Microsoft Word 中您可以一起移動、調整大小或刪除。

## 完整原始碼

將上述所有步驟組合，即可得到一個自包含的程式：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**預期輸出：** 在 Microsoft Word 開啟 *GroupedShapes.docx* 時，會看到兩個並排的矩形，且它們被視為單一可選取的物件。拖曳整個群組即可同時移動兩個矩形。

## 常見變化與邊緣情況

| 情境 | 建議調整 |
|-----------|------------------------|
| **超過兩個圖形** | 建立額外的 `Shape` 物件，依需求定位，然後逐一加入同一個 `GroupShape`。 |
| **動態尺寸** | 依子圖形的最大 `Right` 與 `Bottom` 值計算群組的寬度/高度。 |
| **不同圖形類型** | `ShapeType.Ellipse`、`ShapeType.Triangle` 等皆可同樣插入；群組容器不在乎圖形類型。 |
| **旋轉圖形** | 在加入前設定 `shape.Rotation = 45;`；旋轉會在群組內保留。 |
| **另存為 PDF** | 呼叫 `doc.Save("GroupedShapes.pdf");` – 群組在 PDF 轉換中仍會保留。 |

**小技巧：** 分組後仍可透過 `group.GetChildNodes(NodeType.Shape, true)` 取得個別圖形，進而修改單一矩形的填色而不破壞群組。

## 程式化驗證分組結果

若需在單元測試或其他情境下確認圖形已正確分組，可檢查文件的節點層級：

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

輸出應為：

```
Number of groups: 1
Children in first group: 2
```

此結果證實 **在 Word 中的圖形分組** 已如預期建立。

## 結論

現在您已掌握如何使用 Aspose.Words for C# **在 Word 中分組圖形**。整個流程包括建立個別圖形、定位、以 `GroupShape` 包裝，最後將群組插回文件。透過上述完整範例，您可以將此技巧擴展至任意數量、不同類型的圖形，甚至結合文字方塊與圖片。

接下來，您可以探索以下相關主題，如 **Aspose.Words 圖形分組**、**C# Word 圖形操作** 以及 **DocumentBuilder 插入圖形**，以進一步深化文件自動化的應用。嘗試動態尺寸、條件分組與匯出 PDF，全面發揮 Aspose.Words 的強大功能。

## 接下來您可以學習什麼？

以下教學與本指南內容緊密相關，能幫助您在實作上更上一層樓。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能並探索替代實作方式。

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}