---
category: general
date: 2026-09-05
description: 學習如何使用 C# 的 Aspose.Words 建立空白 Word 文件，並加入可隱藏的矩形形狀。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: zh-hant
lastmod: 2026-09-05
og_description: 使用 Aspose.Words 建立空白 Word 文件並插入隱藏矩形形狀 – C# 開發者逐步指南.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: 建立帶隱藏矩形形狀的空白 Word 文件
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: 建立一個空白的 Word 文件並加入矩形形狀
url: /zh-hant/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立空白 Word 文件並加入矩形形狀

如果您需要建立 **空白 Word 文件**，且其中還包含一個不想在版面上顯示的形狀，本指南將會示範如何使用 Aspose.Words for .NET 完成此操作。您將看到一個完整且可執行的範例，該範例會建立新文件、加入矩形形狀、隱藏該形狀，並儲存檔案——不需要額外工具。

本教學涵蓋從專案設定到常見問題排除的全部內容。完成後，您將能產生一個對讀者看起來是空白的 Word 檔案，但仍攜帶隱藏的中繼資料，這對於浮水印、客製 XML 儲存或版面錨點等情境非常有用。

## 先決條件

在開始之前，請確保您已具備以下條件：

* .NET 6.0 SDK 或更新版本（程式碼亦相容於 .NET Framework 4.7+）
* Visual Studio 2022（或任何支援 C# 的 IDE）
* 有效的 **Aspose.Words** NuGet 授權（免費試用版可用於測試）
* 基本的 C# 使用經驗以及文件節點的概念

您可以使用下列 CLI 指令安裝此函式庫：

```bash
dotnet add package Aspose.Words
```

> **專業提示:** 保持您的 Aspose.Words 版本為最新；本教學中使用的 API 在版本 23.10 之後已穩定。

## 如何使用 Aspose.Words 建立空白 Word 文件

第一步是實例化一個 `Document` 物件。全新的 `Document` 代表一個空的 **空白 Word 文件**——沒有段落、沒有章節，只有檔案容器本身。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **為什麼重要:** 從乾淨的文件開始，可確保之後加入的隱藏形狀不會與既有內容或樣式產生衝突。

## 在文件中加入矩形形狀

接下來我們建立一個矩形形狀。在 Aspose.Words 中，形狀是一個節點，可放置於文件樹的任何位置，且可設定大小、填色、線條樣式與可見性。

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

上述程式碼會建立一個可見的矩形。此時您可以使用 `builder.InsertNode(rectangle)` 將其插入文件。然而，因為我們希望形狀保持隱藏，會在插入前調整其 `Hidden` 屬性。

## 如何在 Word 文件中隱藏形狀

Word 為形狀節點提供 `Hidden` 屬性。將其設為 `true` 後，形狀不會出現在頁面版面中，但仍保留於文件的 XML 中。這正是 **如何隱藏形狀** 的核心需求。

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **說明:** 設定 `Hidden = true` 會在形狀的 XML 中加入 `<w:hide>` 屬性。Word 會在渲染時忽略該形狀，但仍可透過程式或 Word 的 XML 檢視器存取。

## 將隱藏形狀插入空白文件

現在將隱藏的矩形放入文件樹中。因為文件仍是空的，該形狀會成為主故事的第一個節點。

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

若在 Microsoft Word 中開啟產生的檔案，您會看到看似空白的頁面。形狀確實存在，只是不可見。

## 儲存文件

最後，將文件寫入磁碟。您可以選擇任何支援的格式（`.docx`、`.pdf`、`.odt` 等）。本教學使用現代的 DOCX 格式。

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### 預期結果

在 Word 中開啟 `HiddenRectangle.docx`：

* 文件顯示為空白（沒有可見的形狀或文字）。
* 若使用 **Open XML SDK** 或 **Word XML Viewer** 等工具檢查檔案，會看到包含 `hidden` 屬性的 `<w:pict>` 元素，內含矩形。

![帶有隱藏矩形形狀的空白 Word 文件](image.png){: .align-center alt="帶有隱藏矩形形狀的空白 Word 文件"}

## 完整、可執行的範例

以下是可直接貼到主控台應用程式的完整程式碼，包含所有必要的 `using` 指示、錯誤處理與註解。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

執行程式 (`dotnet run`) 並驗證輸出檔案。主控台會顯示儲存位置的確認訊息。

## 常見問題與邊緣情況

### 我可以一次隱藏多個形狀嗎？

可以。為每個形狀設定 `Hidden = true`，然後依序插入。隱藏旗標是針對每個節點生效的，因此在同一文件中混合隱藏與可見形狀是受支援的。

### 如果我只想在列印檢視中隱藏形狀該怎麼辦？

Word 透過 `DisplayWhen` 屬性區分 **顯示** 與 **列印** 可見性。Aspose.Words 並未直接提供此旗標的 API，但您可以修改底層 XML：

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

僅在需要列印專屬可見性時使用此方法。

### 隱藏形狀會影響檔案大小嗎？

隱藏形狀會加入與可見形狀相同的 XML 負載，因此檔案大小的增加是相同的。然而，因為形狀

## 接下來您可以學習什麼？

以下教學與本指南示範的技術密切相關，並可作為進一步探索 API 功能與替代實作方式的資源。每篇文章皆提供完整可執行的程式碼範例與逐步說明，協助您在自己的專案中掌握更多技巧。

- [建立帶陰影矩形形狀的空白 Word 文件 – 步驟說明指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [使用 C# 在 Word 中建立矩形形狀 – 步驟說明指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words 形狀陰影教學 – 在 C# 中為 Word 形狀加入陰影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}