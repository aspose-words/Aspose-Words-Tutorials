---
category: general
date: 2026-10-07
description: 在 C# 中建立空白 Word 文件，學習加入矩形形狀、插入圖片形狀，以及將多個形狀群組，以製作動態報表。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: zh-hant
lastmod: 2026-10-07
og_description: 使用 Aspose.Words 在 C# 中建立空白 Word 文件。學習如何加入矩形形狀、插入圖片形狀，並將多個形狀群組，以製作專業文件。
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: 在 C# 中建立空白 Word 文件並將圖形分組 – 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: How to create blank Word document and group shapes in C#
url: /zh-hant/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中建立空白 Word 文件並群組形狀

如果您需要 **以程式方式建立空白 Word 文件**，本教學將一步步示範。您將會看到如何 **加入矩形形狀**、**插入圖片形狀**，以及 **群組多個形狀**，使它們在之後 **將圖片加入 Word** 時能作為單一物件一起操作。

從程式碼操作 Word 檔案乍看可能令人望而卻步，但 Aspose.Words 讓整個流程變得相當簡單。完成本教學後，您將擁有一段可重複使用的 C# 程式碼，能產生一個乾淨的空白 Word 檔，內含已群組的矩形與商標。您可以將產出的檔案嵌入發票、報表或任何自動化文件工作流程中。

## 前置條件

開始之前，請確保您已具備：

* .NET 6.0 或更新版本（此程式碼亦相容 .NET Framework 4.7 以上）。  
* 有效的 Aspose.Words for .NET 授權或免費評估金鑰。  
* 一個圖片檔（例如 `logo.png`），放置於程式碼可參考的資料夾中。  
* Visual Studio 2022 或任何相容 C# 的 IDE。

除 `Aspose.Words` 之外，無需額外的 NuGet 套件。

## 使用 Aspose.Words 建立空白 Word 文件的方法

第一步永遠是 **建立空白 Word 文件**。此物件將承載之後的所有形狀。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 代表整個 `.docx` 檔案。此時檔案為空，已符合 *建立空白 Word 文件* 的需求。

## 建立容器以群組多個形狀

群組形狀可讓您一次移動、旋轉或調整大小。Aspose.Words 提供 `GroupShape` 類別供此用途。

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

`Bounds` 矩形決定群組在頁面上的顯示位置。將群組放在第一段落中，可確保 **建立空白 Word 文件** 後立即包含一個可視的容器。

## 在群組內加入矩形形狀的方法

常見需求是 **加入矩形形狀** 作為背景或邊框。以下程式碼會建立矩形並加入先前定義的群組。

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

因為矩形位於 `GroupShape` 內，之後加入的其他形狀會與它一起移動。這正是 **群組多個形狀** 功能的核心。

## 在群組內插入圖片形狀的方法

接著，您會 **插入圖片形狀**（商標），並將其放置在矩形旁邊。此步驟示範 **將圖片加入 Word** 的工作流程。

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

`SetImage` 方法會讀取檔案並直接嵌入 Word 文件，確保即使來源檔案移動，圖片仍能保留。此步驟完成 **插入圖片形狀**，同時滿足 **將圖片加入 Word** 的需求。

## 儲存文件

最後，將檔案寫入磁碟。儲存後的文件包含空白文件、已群組的矩形以及嵌入的商標。

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

當您在 Microsoft Word 中開啟 `GroupShape.docx`，會看到一個包含淡灰色矩形與商標並排的單一群組。選取群組中的任意部分即可一次移動或調整整個集合，證明形狀已成功 **群組多個形狀**。

## 完整、可執行的範例

以下是完整程式碼，您可以直接複製、貼上並執行。將 `YOUR_DIRECTORY` 替換為您機器上實際存在的絕對或相對路徑。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### 預期結果

* 產生一個名為 `GroupShape.docx` 的檔案，位於 `YOUR_DIRECTORY`。  
* 在 Word 中開啟該檔案時，會看到一個單一視覺群組，左側為灰色矩形，右側為 `logo.png`。  
* 選取視覺群組的任意部分即可移動或調整整個集合，證實形狀已正確 **群組多個形狀**。

## 常見問題與邊緣案例處理

| 問題 | 解答 |
|---|---|
| **我可以在同一群組中加入超過兩個形狀嗎？** | 可以。對每個額外的 `Shape` 呼叫 `group.AppendChild(yourShape)`。群組可容納任意數量的繪圖物件。 |
| **如果圖片檔案遺失會怎樣？** | `SetImage` 會拋出 `FileNotFoundException`。請將呼叫包在 try‑catch 區塊，並提供備用方案（例如佔位形狀）。 |
| **需要為形狀設定 `WrapType` 嗎？** | 預設情況下形狀為內嵌 (inline)。若需浮動行為，可在加入群組前設定 `picture.WrapType = WrapType.Inline;` 或其他換行模式。 |
| **文件大小會影響群組的邊界嗎？** | `Bounds` 矩形以點 (pt) 為單位 (1 pt ≈ 1/72 in)。若將群組放在不同的頁面版面 (例如 A4 與 Letter) 上，請相應調整尺寸。 |
| **我可以在其他文件中重複使用同一群組嗎？** | 可以。使用 `GroupShape cloned = (GroupShape)group.Clone(true);` 複製群組，然後插入到另一個 `Document` 中。 |

## 專業小技巧

* **重複使用 `DocumentBuilder`** 以在群組前後加入文字。它會自動遵循目前的游標位置。  
* **設定 `Shape.StrokeColor`**，若需要在矩形周圍顯示可見邊框。  
* **使用高解析度 PNG** 作為商標，以避免在放大時出現像素化。

## 接下來該學什麼？

以下教學與本指南緊密相關，能進一步深化您對相關 API 的掌握，並提供其他實作方式的範例。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}