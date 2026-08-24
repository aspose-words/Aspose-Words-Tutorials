---
category: general
date: 2026-08-23
description: 學習如何在 C# 中使用 Aspose.Words 將形狀分組。指南亦說明如何插入矩形形狀以及在複雜文件中加入形狀文字。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: zh-hant
lastmod: 2026-08-23
og_description: 如何在 C# 中使用 Aspose.Words 對圖形進行分組。跟隨本完整教學，學習插入矩形圖形、在 Word 中加入圖形，並高效地對多個圖形進行分組。
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: 如何在 C# 中對形狀進行分組 – 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: 如何在 C# 中使用 Aspose.Words 將形狀分組
url: /zh-hant/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用 Aspose.Words 群組形狀

如果您需要在 Word 文件中以程式方式 **how to group shapes**，本教學將示範使用 Aspose.Words for .NET 的完整步驟。無論您是建立報表產生器、範本引擎，或是圖表工具，您都會學會如何啟動群組、插入矩形形狀，以及在不離開程式碼的情況下加入 word‑level 內容的形狀。

您還會看到如何 **group multiple shapes** 一起使用，這在您想要將多個物件作為單一實體移動、旋轉或設定樣式時相當重要。以下範例適用於最新的 Aspose.Words 24.x 版本，且僅需 .NET 6 或更新版本。

## 前置條件

- .NET 6 SDK（或任何 Aspose.Words 支援的 .NET 版本）
- Visual Studio 2022 或 VS Code
- Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）
- 具備 C# 與 Aspose.Words 物件模型的基本知識

> **Pro tip:** 使用 Aspose 提供的免費評估授權，以避免測試時的浮水印限制。

## 使用 Aspose.Words 群組形狀

以下是一個完整且可執行的程式，示範 **how to start group**、加入矩形，並完成群組。程式碼遵循您提供的片段相同的邏輯流程，但加入了說明、錯誤處理與註解，以提升可讀性。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### 為何每個步驟都重要

| Step | Purpose | How it relates to the keywords |
|------|---------|--------------------------------|
| **Create a new blank document** | 提供一個乾淨的畫布供形狀操作使用。 | 為之後的 **add shapes word** 做好準備。 |
| **Initialize DocumentBuilder** | Builder 是插入物件的主要 API。 | 在您能執行 **how to start group** 之前必須先初始化。 |
| **StartGroupShape** | 開始一個邏輯容器；之後的所有形狀皆成為此群組的成員。 | 直接回應 **how to start group** 的需求。 |
| **InsertShape** (rectangle, ellipse, text) | 將單一形狀放入群組中。矩形的呼叫符合 **insert rectangle shape**；文字形狀符合 **add shapes word**。 | 示範 **group multiple shapes**。 |
| **EndGroupShape** | 完成群組，使您能將其作為單一單位移動或設定樣式。 | 完成 **how to group shapes** 的工作流程。 |

## 插入矩形形狀 – 深入探討

`InsertShape` 方法接受 `ShapeType` 列舉、寬度與高度。若要 **insert rectangle shape** 並套用自訂樣式，您可以擴充此範例：

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Why style it?** 設定樣式可確保矩形在群組稍後重新定位時仍然突出。它同時示範了形狀屬性可以在群組關閉 *之前* 設定。

## 新增 Word‑level 形狀（add shapes word）

如果您需要將文字直接嵌入形狀中——通常稱為「WordArt」或「文字方塊」——請使用 `ShapeType.TextPlainText`。插入後，您可以使用 `DocumentBuilder.Writeln` 或存取形狀的 `TextBox` 屬性來寫入文字：

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

此做法符合 **add shapes word** 關鍵字，並展示文字如何隨群組一起移動。

## 群組多個形狀 – 實務情境

當您 **group multiple shapes** 時，您可以將它們視為單一物件來進行定位、旋轉或縮放。例如，群組關閉後，您可以移動整個群組：

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

或旋轉群組：

```csharp
group.Rotation = 45; // degrees
```

這些操作之所以可行，是因為這些形狀共享相同的父群組。

## 處理邊緣案例

1. **Nested groups** – Aspose.Words 允許群組內再嵌套群組。若要建立巢狀群組，請在內部群組的 `EndGroupShape` 之前再次呼叫 `StartGroupShape`。
2. **Empty groups** – 若您啟動群組卻未插入任何形狀，`EndGroupShape` 仍會建立一個空的容器。這不會造成問題，但可能會稍微增加檔案大小。
3. **Compatibility** – 產生的 DOCX 可在 Word 2010 及之後的版本開啟。較舊版本可能會忽略群組的中繼資料，因此請務必以目標 Word 版本進行測試。

## 完整來源檔案供參考

將以下內容儲存為 .NET 主控台專案中的 `Program.cs`。程式碼可直接編譯執行，無需修改。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### 預期輸出

開啟 Microsoft Word 中的 `GroupedShapes.docx` 後會看到：

- 一個淡珊瑚色的矩形、一個橢圓形與一個文字方塊——全部在視覺上被綁定在一起。
- 選取群組的任何部分，同時會選取整個群組（會出現單一的外框）。
- 移動或旋轉群組時，三個形狀會一起移動。

## 常見問題

**Q: 我可以群組文件中已存在的形狀嗎？**  
A: 可以。取得現有的 `Shape` 物件，呼叫 `builder.StartGroupShape()`，使用 `builder.InsertShape(existingShape)` 重新插入，最後呼叫 `EndGroupShape()`。

**Q: 群組會影響底層的 XML 嗎？**  
A: Aspose.Words 會加入一個 `<w:grpSp>` 元素，內含每個形狀的 `<w:sp>` 節點。此結構完全符合 Office Open XML 規範。

**Q: 如果之後需要解除群組該怎麼辦？**  
A: 雖未提供直接的「ungroup」API，但您可以遍歷群組的子形狀 (`group.GroupShape.Children`) 並將它們複製到文件主體中。

## 往後步驟

既然您已了解 **how to group shapes**，建議您進一步探索以下相關主題：

- **Apply complex formatting to grouped shapes** – 了解如何設定漸層填色、陰影效果與線條樣式。
- **Export grouped shapes as images** – 使用 `Shape.GetShapeRenderer().Save(...)` 將群組轉為點陣圖。
- **Create dynamic diagrams** – 結合資料驅動的定位與群組功能，自動產生流程圖。

上述每項皆以本教學的基礎為出發點，協助您打造更豐富、互動性更高的 Word 文件。

---

*祝程式開發順利！若您覺得本指南有幫助，請與同事分享或為包含範例專案的儲存庫加星。*

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎延伸。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [在 Word 文件中使用 Aspose.Words for .NET 插入形狀](/words/english/net/working-with-shapes/insert-shape/)
- [使用 Aspose.Words for .NET 在 Word 文件中建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words 在 Word 中建立矩形形狀 – 步驟指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}