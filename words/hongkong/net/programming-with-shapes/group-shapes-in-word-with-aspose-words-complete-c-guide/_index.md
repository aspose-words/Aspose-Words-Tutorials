---
category: general
date: 2026-07-19
description: 使用 Aspose.Words 在 Word 中對形狀進行分組。了解如何新增矩形形狀、定義橢圓形狀，並將形狀插入 Word 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: zh-hant
lastmod: 2026-07-19
og_description: 使用 Aspose.Words 在 Word 中對形狀進行分組。主控件添加矩形形狀、定義橢圓形狀，並將形狀插入 Word 檔案。
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: 在 Word 中群組圖形 – 一步一步的 C# 教學
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 使用 Aspose.Words 在 Word 中群組形狀 – 完整 C# 指南
url: /zh-hant/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中群組形狀 – 完整 C# 指南

有沒有想過如何在不操作介面的情況下 **group shapes in Word**？你並不孤單。無論是程式化產生合約、傳單或圖表，能夠 **add rectangle shape**、**define ellipse shape**，然後 **group shapes in Word** 都能為你節省數小時的手動工作。

在本教學中，我們將使用 **Aspose.Words for .NET** 走過一個真實案例。完成後，你將清楚知道如何 **insert shape into Word**、將它們結合，並產出可交付給客戶或團隊成員的精緻文件。

---

## 您需要的條件

- **Aspose.Words for .NET**（最新版本，例如 24.9）。您可以透過 NuGet 使用 `Install-Package Aspose.Words` 取得。
- .NET 開發環境（Visual Studio 2022 或安裝 C# 擴充功能的 VS Code 均可）。
- 基本熟悉 C# 語法——不需高階技巧，只要會使用一般的 `using` 陳述式與物件建立即可。

就這樣。無需額外函式庫、無 COM interop，純粹使用受管理的程式碼。

---

## 使用 Aspose.Words 在 Word 中群組形狀

以下是與您現有程式碼相符的逐步說明。每一步都解釋 **why** 我們這麼做，而不只是 **what** 這行程式碼的功能，讓您能將此模式套用到任何形狀。

### 步驟 1：設定文件與 Builder

我們先建立一個空的 `Document` 與 `DocumentBuilder`。Builder 就像我們的「筆」，讓我們能在需要的地方插入內容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why?** `Document` 物件代表整個 .docx 檔案，而 `DocumentBuilder` 提供方便的 API 來插入節點（例如形狀），無需處理底層的節點樹。

### 步驟 2：新增矩形形狀（add rectangle shape）

現在我們 **add rectangle shape** 到文件中。我們設定其大小、位置與填色，使其突出顯示。

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **Tip:** 您可以將 `FillColor` 更改為任何您喜好的 `System.Drawing.Color`。當您需要在報告中使用顏色編碼的區段時，這很有用。

### 步驟 3：定義橢圓形狀（define ellipse shape）

接著，我們 **define ellipse shape**。請注意不同的 `ShapeType` 以及偏移量（`Left = 120`），使橢圓位於矩形旁邊。

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Why this matters:** 透過明確定位形狀，您可以在群組之前控制它們的顯示方式。如果依賴自動版面配置，群組可能會出現偏離中心的情況。

### 步驟 4：（可選）插入單獨形狀以預覽

如果您想在群組前先看到每個形狀，可以分別 **insert shape into Word**。此步驟為可選，但對除錯很有幫助。

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Pro tip:** 當您確定形狀顯示正確後，請將這兩行註解掉；否則群組後會出現重複的視覺效果。

### 步驟 5：如何群組形狀 – 建立 GroupShape

以下是本教學的核心：**how to group shapes**。我們建立 `GroupShape`，將矩形與橢圓附加上去，並決定群組與周圍文字的互動方式。

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Explanation:** `GroupShape` 本質上是一個容納其他形狀的迷你畫布。將 `WrapType` 設為 `Inline` 後，當您新增或刪除文字時，整個群組會作為單一單位移動。

### 步驟 6：將群組形狀插入文件（insert shape into word）

現在我們 **insert shape into Word**——但這次插入的是群組容器，而非單獨的形狀。

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **What happens under the hood?** `InsertNode` 呼叫會將 `GroupShape` 加入文件的節點集合。因為群組已包含矩形與橢圓，它們會以單一物件的形式一起顯示。

### 步驟 7：儲存文件

最後，將檔案寫入磁碟。您可以依專案結構調整路徑。

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Result:** 在 Microsoft Word 中開啟 `GroupShape.docx`，您會看到一個淡藍色的矩形與一個珊瑚色的橢圓被鎖定在一起。拖曳其中一個會同時移動另一個——正是 “group shapes in word” 所承諾的效果。

---

## 視覺確認

以下是群組形狀在 Word 檔案內的示意圖。  

![使用 Aspose.Words 建立的 Word 文件中群組形狀的螢幕截圖](grouped_shapes_placeholder.png "在 Word 中群組形狀")

*此圖片的 alt 文字包含主要關鍵字，以提升可及性與 SEO。*

---

## 常見問題與邊緣情況

### 如果需要超過兩個形狀該怎麼辦？

只要在插入群組之前持續呼叫 `groupShape.AppendChild(yourNewShape);` 即可。API 對子形狀的數量沒有任何限制。

### 我可以旋轉或調整整個群組的大小嗎？

當然可以。`GroupShape` 繼承自 `Shape`，因此您可以在群組本身設定 `RotationAngle`、`Width` 或 `Height` 等屬性，所有子形狀都會跟隨變更。

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### 如何變更群組的背景顏色？

使用 `groupShape.FillColor`。這會填滿看不見的邊界框，對於突顯區域相當有用。

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### 這能在較舊的 Word 格式（.doc）中使用嗎？

`Aspose.Words` 也能儲存為 `.doc`——只要在 `Save` 時更換副檔名即可。然而，某些進階的形狀功能（例如群組）僅在 OOXML `.docx` 格式中得到完整支援。

---

## 完整可執行範例

將以下程式碼複製貼上至新的 console 應用程式，即可看到完整流程。內容完整無遺，這是一個 **complete, runnable example**（完整可執行範例）。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**預期輸出：** 當您開啟 `GroupShape.docx` 時，會看到一個由淡藍色矩形與淡珊瑚色橢圓組成的單一群組物件，兩者完美並排對齊。

---

## 重點回顧

我們剛剛已說明使用 Aspose.Words **group shapes in Word** 所需的全部內容：

1. 建立文件與 Builder。  
2. 使用明確尺寸 **Add rectangle shape** 與 **define ellipse shape**。  
3. （可選）**insert shape into Word** 以快速預覽。  
4. 使用 `GroupShape` 來 **how to group shapes**——將每個子形狀加入、設定換行方式，然後插入。  
5. 儲存檔案並驗證結果。

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，建立在此處示範的技巧之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [在 Word 文件中插入形狀（使用 Aspose.Words for .NET）](/words/english/net/working-with-shapes/insert-shape/)
- [使用 Aspose.Words 在 Word 中建立矩形形狀 – 步驟指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words 形狀陰影教學 – 在 C# 中為 Word 形狀加入陰影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}