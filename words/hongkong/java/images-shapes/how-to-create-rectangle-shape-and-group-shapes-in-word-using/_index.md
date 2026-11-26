---
category: general
date: 2026-11-18
description: 學習如何使用 C# 在 Word 文件中建立矩形形狀。本指南亦涵蓋設定形狀大小、設定形狀位置，以及在 Word 中將形狀分組。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: zh-hant
lastmod: 2026-11-18
og_description: 使用 C# 在 Word 檔案中建立矩形形狀，並學習設定形狀尺寸、設定形狀位置以及在 Word 中將形狀群組。
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: 使用 C# 在 Word 中建立矩形形狀並將形狀分組
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 C# 在 Word 中建立矩形形狀並群組形狀
url: /zh-hant/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 在 Word 中建立矩形形狀並將形狀分組

如果您需要在 Word 文件中 **建立矩形形狀**，本教學會提供完整、可直接執行的解決方案。您將會看到如何設定形狀大小、設定形狀位置，並在 Word 中將形狀分組，使其行為如同單一物件。

在程式化產生報告、發票或圖表時，操作形狀是一項常見需求。完成本指南後，您將能產生一個包含矩形、橢圓以及分組容器的 `.docx` 檔案——全部使用 Aspose.Words for .NET 建立。

## 前置條件

- .NET 6.0 SDK 或更新版本（程式碼亦相容於 .NET Framework 4.7+）
- Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）
- 程式碼編輯器或 IDE（Visual Studio、VS Code、Rider 等）

不需要其他額外的函式庫。

## 如何在 Word 中建立矩形形狀並將形狀分組

核心步驟如下：

1. **建立空白文件** 並建立 `DocumentBuilder`。
2. **插入 `GroupShape`**，用來容納各個形狀。
3. **建立矩形形狀**，設定其尺寸，並加入至群組。
4. **建立橢圓形狀**，設定其大小與位置，並加入至群組。
5. **儲存** 文件。

以下將逐步說明每個步驟，完整的原始碼則緊隨說明之後。

### 步驟 1：初始化文件與建構器

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 代表整個 Word 檔案，而 `DocumentBuilder` 提供流暢的 API 以插入內容。在加入任何形狀之前，必須先初始化它們。

### 步驟 2：插入群組形狀

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

`GroupShape` 如同容器；所有子形狀會一起移動。當您需要整體變換（例如移動、旋轉或刪除）時，這是 **在 Word 中分組形狀** 的推薦方式。

### 步驟 3：建立矩形並設定其大小

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

此處我們透過指派 `Width` 與 `Height` **建立矩形形狀** 並 **設定形狀大小**。在 Aspose.Words 中，尺寸以點 (pt) 為單位（1 pt ≈ 1/72 英吋）。明確設定尺寸可確保矩形精確呈現。

### 步驟 4：建立橢圓、設定尺寸並定位

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

對於橢圓而言，**設定形狀尺寸** 的寬度與高度相同，形成完美的圓形。`Left` 屬性示範了 **設定形狀位置**：橢圓從群組原點向右偏移 120 pt，避免與矩形重疊。

### 步驟 5：儲存文件

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

儲存會將 Word 檔寫入磁碟。您可以在 Microsoft Word 中開啟 `GroupShape.docx`，以驗證矩形與橢圓已正確分組與定位。

## 設定形狀尺寸與大小 – 深入探討

- **點與英吋的換算**：72 pt = 1 in。若偏好使用英吋，可乘以 72（例如 `2.5 * 72` 代表 2.5 in）。
- **自動縮放**：若省略 `Width` 或 `Height`，形狀會使用預設大小。請明確 **設定形狀大小** 以避免版面配置的意外。
- **長寬比**：對於 `Ellipse` 等形狀，保持 `Width` 與 `Height` 相等即可維持圓形外觀。

## 在 Word 中定位形狀

`Left` 與 `Top` 屬性控制形狀在其容器（群組或頁面）內的偏移。正值會將形狀向右/向下移動，負值則向左/向上移動。進行分組時，位置是相對於群組原點，簡化了版面計算。

## 使用 Aspose.Words 在 Word 中分組形狀

當您希望多個形狀作為單一單元時，分組是必要的。`GroupShape` 物件：

- 支援 `AppendChild` 以加入任何 `Shape`（矩形、橢圓、圖像等）。
- 可透過一次呼叫即移動、旋轉或刪除整個群組。
- 保持子形狀相對於群組的位置，使複雜圖表更易管理。

**小技巧：** 加入所有子形狀後，您可以調整群組的 `Width`、`Height`、`Left` 與 `Top`，一次性重新定位整個集合。

## 完整可執行範例

以下是完整程式碼，您可以直接複製、貼上並執行。它包含所有 `using` 指令、`Main` 方法，以及說明每行程式碼的註解。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**預期結果：** 執行程式後，`GroupShape.docx` 會出現在執行目錄中。於 Word 開啟時，可見左側有一個 100 pt × 50 pt 的矩形，右側有一個 80 pt × 80 pt、向右偏移 120 pt 的橢圓，兩者皆屬於同一個分組物件。

![含有分組矩形與橢圓的 Word 文件](grouped_shapes.png){: .center alt="使用 C# 建立的顯示分組矩形與橢圓形狀的 Word 文件截圖" }

*上圖說明最終結果；矩形與橢圓可作為同一個群組被選取。*

## 常見問題與邊緣案例

| 問題 | 答案 |
|----------|--------|
| **我可以加入超過兩個形狀嗎？** | 可以。對每個額外的形狀呼叫 `group.AppendChild(yourShape)`。 |
| **如果需要旋轉群組怎麼辦？** | 在加入所有子形狀後，使用 `group.RotationAngle = 45;`（度數）即可。 |
| **如何變更群組的背景顏色？** | 設定 `group.FillColor = System.Drawing.Color.LightGray;`。 |
| **這能用於 .doc 檔案嗎？** | Aspose.Words 支援 `.doc` 與 `.docx`。相同程式碼皆可使用，只需在 `Save` 時更改檔案副檔名。 |
| **大量形狀分組會有記憶體影響嗎？** | 分組本身只會產生極小的開銷。主要考量是形狀總數，對於大型文件請保持在合理範圍。 |

## 結論

在本教學中，您學會了如何使用 C# 在 Word 檔案中 **建立矩形形狀**，以及如何 **設定形狀大小**、**設定形狀尺寸**、**設定形狀位置**，最後如何使用 Aspose.Words **在 Word 中分組形狀**。完整範例展示了一種簡潔且易於維護的方法，您可以將其擴充至更複雜的圖表、圖形或自訂圖形。

接下來，您可以探索：

- 在形狀內加入文字 (`Shape.TextPath.Text = "Hello"` )。
- 將圖像插入 `GroupShape`。
- 使用 `doc.Save("output.pdf")` 將分組形狀匯出為 PDF。

歡迎嘗試不同的尺寸、位置與其他形狀類型，以符合您的專案需求。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可運作的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [使用 Aspose.Words for .NET 在 Word 文件中建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}