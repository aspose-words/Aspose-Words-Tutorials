---
category: general
date: 2026-09-11
description: 學習如何使用 C# 在 Word 中隱藏圖形。本指南亦示範如何插入矩形圖形以及使用 Aspose.Words 將圖形插入 Word 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: zh-hant
lastmod: 2026-09-11
og_description: 使用 C# 與 Aspose.Words 在 Word 中隱藏圖形。跟隨逐步教學，學習在 Word 文件插入矩形圖形及管理圖形。
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: 如何在 Word 中隱藏圖形 – 完整 C# 教學
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 C# 與 Aspose.Words 隱藏 Word 中的圖形
url: /zh-hant/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 C# 和 Aspose.Words 隱藏圖形

如果您需要在 Word 中隱藏圖形，同時保留圖形在文件結構中的存在，本教程將逐步說明如何操作。使用 Aspose.Words for .NET，您可以插入矩形圖形、將其隱藏，並仍保留其位置以供後續處理。

Word 自動化常常需要對圖形進行細緻的控制——無論是生成範本、編寫報告，或是構建文件編輯服務。完成本指南後，您將能夠：

* 在 Word 文件中插入矩形圖形（`insert rectangle shape`）。
* 隱藏任何圖形而不刪除它（`how to hide shape in word`）。
* 儲存結果並驗證隱藏的圖形不會出現在渲染視圖中（`insert shape into word document`）。

此範例適用於 Aspose.Words 24.10 或更新版本，目標為 .NET 6.0+，但其概念同樣適用於較早的版本。

## 前置條件

* **Aspose.Words for .NET** ≥ 24.10。您可從 Aspose 官方網站取得免費的臨時授權。
* **.NET SDK** 6.0 或更新版本，已安裝於您的機器上。
* 開發環境，例如 Visual Studio 2022、VS Code 或 Rider。
* 具備 C# 與 Word Open XML 概念的基本認識（非必須，但有助於學習）。

## 使用 Aspose.Words 在 Word 中隱藏圖形

以下是一個完整且可執行的程式範例，示範整個工作流程——從建立文件、插入矩形圖形到最終隱藏它。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### 各步驟說明

1. **Create a new document** – `Document` 代表記憶體中的 Word 檔案。`DocumentBuilder` 提供用於插入內容的流暢 API。  
2. **Insert rectangle shape** – `InsertShape` 建立類型為 `Rectangle` 的繪圖物件。尺寸以點 (pt) 為單位表示 (1 pt ≈ 1/72 in)。此步驟滿足 `insert rectangle shape` 的需求。  
3. **Hide the shape** – 設定 `Shape.Hidden = true` 會在 Word 標記中將圖形標記為隱藏 (`<w:hidden/>`)。圖形仍保留在文件樹中，之後可取消隱藏或以程式方式引用。這就是 `how to hide shape in word` 的核心。  
4. **Save the file** – 文件寫入 `output.docx`。在 Microsoft Word 中開啟時，矩形不會顯示，但仍存在於 XML 中，可使用 ZIP 檢視器或 Open XML SDK 進行檢查。

### 預期結果

在 Microsoft Word 中開啟 `output.docx`：

* 文件顯示為空白——沒有可見的圖形。  
* 若檢查底層 XML (`word/document.xml`)，會發現含有 `<w:hidden/>` 屬性的 `<w:pict>` 元素，證明圖形仍在但被隱藏。

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

只要將 `Hidden = false` 設定回來並重新儲存文件，即可再次顯示隱藏的圖形。

## 在 Word 文件中插入矩形圖形

雖然主要目標是隱藏圖形，但許多情境會先插入圖形。`InsertShape` 方法支援多種 `ShapeType` 值，包括 `Rectangle`、`Ellipse`、`Line` 以及自訂影像。

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**為什麼使用矩形？**  
矩形提供乾淨、軸對齊的容器，可容納文字、影像或其他嵌套圖形。它常被用作表格或圖表等動態內容的佔位符。先插入矩形，即使之後將其隱藏，也能保持版面配置的一致性。

## 在 Word 文件中插入圖形 – 最佳實踐

在 `insert shape into word document` 時，請考慮以下要點：

* **設定明確的尺寸** – 避免依賴自動調整大小；以點為單位指定寬度與高度，以確保跨平台版面一致。  
* **定義定位** – 預設情況下圖形會錨定於當前段落。可使用 `builder.MoveTo` 或 `builder.StartBookmark` 精確放置。  
* **提前套用樣式** – 填充顏色、線條樣式與文字環繞會影響最終外觀。即使是隱藏的圖形，也應設定適當樣式，因為標記保持不變。  
* **版本相容性** – `Hidden` 屬性僅在 Aspose.Words 24.10 之後提供。若目標較舊版本，可使用 `Node` API 手動加入 `<w:hidden/>` 屬性。

### 手動加入 hidden 屬性（備援方案）

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## 完整端對端範例

將所有步驟整合如下，這是一個完整的程式範例，會：

1. 插入矩形圖形。  
2. 隱藏該圖形。  
3. 插入一個可見的橢圓作為對比。  
4. 儲存文件。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

執行程式會產生 `demo_output.docx`。開啟後，您只會看到珊瑚色的橢圓；綠色矩形則存在於 XML 中，但在視圖中被隱藏。

## 常見問題與邊緣案例

**Q: 隱藏圖形會影響分頁嗎？**  
A: 不會。隱藏的圖形會被版面引擎忽略，因而不佔用空間。這對不應影響分頁的佔位內容非常有用。

**Q: 能否隱藏位於頁首或頁尾的圖形？**  
A: 可以。相同的 `Hidden` 屬性可用於文件樹中任何位置的圖形，包括頁首、頁尾，甚至表格內部。

**Q: 若需一次隱藏多個圖形該怎麼做？**  
A: 迭代 `Document.GetChildNodes(NodeType.Shape, true)` 集合，對每個目標圖形設定 `Hidden = true`。

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**Q: 轉換為 PDF 時 hidden 屬性會被保留嗎？**  
A: 轉換為 PDF 時，預設會省略隱藏的圖形，與 Word 的渲染行為一致。若需要在 PDF 中保留它們，必須在轉換前取消隱藏。

## 提示與陷阱

* **專業提示：** 若之後計畫取消隱藏而不干擾周圍文字，請在隱藏前將 `shape.WrapType = WrapType.None` 設定好。  
* **留意舊版 Aspose.Words：** 在 24.10 之前，`Hidden` 屬性會拋出 `NotSupportedException`。此時請改用手動 XML 方法。  
* **測試：** 必須在 Word 中開啟產生的 `.docx`，並使用「顯示 XML 標記」（開發人員標籤）確認 `<w:hidden/>` 屬性是否存在。

## 結論

現在您已了解如何使用 C# 與 Aspose.Words 在 Word 中隱藏圖形，以及如何插入矩形圖形與在 Word 文件中插入圖形，並完整掌控其可見性。透過 `Hidden` 屬性，您可以將圖形保留在文件模型中以供後續處理，同時向最終使用者呈現乾淨的視圖。

接下來，您可以探索相關主題，例如 **在執行時更新圖形屬性**、**將隱藏圖形轉換為影像**，或 **直接使用 Open XML SDK 操作隱藏元素**。這些延伸內容將進一步加深

## 接下來該學什麼？

以下教程涵蓋與本指南技術緊密相關的主題。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [在 Word 文件中使用 Aspose.Words for .NET 插入圖形](/words/english/net/working-with-shapes/insert-shape/)
- [使用 C# 建立 Word 矩形圖形 – 步驟說明](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [使用 Aspose.Words for .NET 在 Word 文件中建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}