---
category: general
date: 2026-09-27
description: 使用 Aspose.Words 於 C# 程式碼自動建立包含群組圖形的 Word 文件。請依照本逐步指南產生檔案，並學習實用技巧。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: zh-hant
lastmod: 2026-09-27
og_description: 使用 Aspose.Words 程式化建立含群組圖形的 Word 文件。本教學將帶領您逐步瀏覽完整的 C# 程式碼，說明每個步驟，並展示最終輸出。
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: 以程式方式建立含群組圖形的 Word 文件 – C# 指南
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 以程式方式建立含群組圖形的 Word 文件
url: /zh-hant/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 以程式方式建立包含群組圖形的 Word 文件

如果您需要**以程式方式建立包含群組圖形的 Word 文件**，本指南將向您展示如何使用 Aspose.Words for .NET 完成此操作。無論您是在構建合約產生器、報告生成器，或是表單填寫工具，您都將學習完整的 C# 程式碼、每個 API 呼叫的意義，以及如何處理常見的邊緣情況。

在 Word 中建立群組圖形可能會感到複雜，因為 Word 物件模型將群組圖形視為其他繪圖物件的容器。本教學不僅回答**如何在 Word 文件中建立群組圖形**，還示範如何在群組內嵌入純文字 StructuredDocumentTag（SDT），使圖形能夠容納可編輯的內容。

## 您將完成的工作

- 使用 `Document` 與 `DocumentBuilder` 初始化一個新的空白 Word 文件。
- 在目前游標位置插入 `GroupShape`。
- 在群組圖形中加入純文字 `StructuredDocumentTag`（SDT）。
- 將檔案儲存為可在 Microsoft Word 開啟的 `.docx`。
- 了解 `GroupShape` 與 `StructuredDocumentTag` 的關鍵屬性，以便未來擴充。

### 前置條件

- .NET 6.0 或更新版本（程式碼亦可在 .NET Framework 4.7+ 上執行）。
- Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）。
- C# 開發環境，例如 Visual Studio 2022 或具 C# 擴充功能的 VS Code。

---

## 以程式方式建立 Word 文件 – 設定專案

1. **建立新的主控台專案**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **在您的 IDE 中開啟專案**，並將 `Program.cs` 的內容替換為下一節所示的程式碼。

> **專業提示：** 保持專案資料夾整潔；除非您提供絕對路徑，否則 Aspose.Words 會將輸出檔案寫入工作目錄。

## 步驟 1：初始化文件與建構器

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**為什麼這很重要：**  
`Document` 代表整個 Word 檔案，而 `DocumentBuilder` 讓您在不手動瀏覽節點樹的情況下定位新元素。提前設定頁面尺寸可確保群組圖形不會超出頁面。

## 步驟 2：在目前游標位置插入 GroupShape

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**說明：**  
`GroupShape` 是一種可容納其他圖形、圖片或文字方塊的繪圖物件。透過設定 `Width`、`Height`、`Left` 與 `Top`，您可以精確控制其在頁面上的位置。`InsertNode` 方法將圖形放入主文件流程中，行為類似浮動物件。

## 步驟 3：在群組內加入純文字 StructuredDocumentTag（SDT）

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**為什麼使用 SDT？**  
StructuredDocumentTag 是 Word 原生的內容控制項。它們允許使用者在已儲存的文件中直接編輯文字，且之後可透過程式存取以進行資料擷取。將 SDT 放入群組圖形中，可結合視覺分組與可編輯內容。

## 步驟 4：儲存文件

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**結果：**  
在 Microsoft Word 中開啟 `GroupShapeDemo.docx`，會看到一個浮動的矩形（群組圖形），內含顯示「Enter text here」的文字佔位符。使用者可點擊圖形內部直接輸入文字。

### 預期輸出螢幕截圖（概念圖）

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

外層方框是 `GroupShape`；內層灰色區域是 `StructuredDocumentTag`。

---

## 如何建立群組圖形 Word – 其他考量

### 新增更多子圖形

您可以透過加入額外的繪圖物件（例如圖片或文字方塊）來豐富群組內容：

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### 控制環繞樣式

如果您需要群組圖形位於文字後方或使用緊密環繞，請設定 `WrapType` 屬性：

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### 邊緣情況：空的群組圖形

`GroupShape` 若沒有子項目，會呈現為不可見的佔位符。請務必確認至少加入一個子項目（例如 SDT 或圖片），否則 Word 可能在儲存時移除該群組。

### 相容性說明

Aspose.Words 23.10 以上完整支援 `GroupShape` 與 `StructuredDocumentTag`。若您使用較舊版本，`AppendChild` 方法的行為可能不同，且儲存後可能需要呼叫 `UpdatePageLayout`。

---

## 完整可執行範例

將以下完整程式碼片段複製到 `Program.cs`，然後執行專案。此程式碼將上述所有步驟整合於單一、獨立的程式中。



## 接下來您應該學習什麼？

以下教學涵蓋與本指南緊密相關的主題，並在此基礎上進一步說明。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在自己的專案中探索替代實作方式。

- [使用 Aspose.Words for .NET 在 Word 文件中建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 C# 在 Word 中建立矩形圖形 – 步驟說明指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [使用 Aspose.Words 建立空白 Word 文件 – 步驟說明指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}