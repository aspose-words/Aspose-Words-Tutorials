---
category: general
date: 2026-09-05
description: 使用 Aspose.Words 在 Word 文件中建立矩形形狀，然後學習如何在 Word 中插入橢圓形並將形狀群組，以打造更豐富的版面配置。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: zh-hant
lastmod: 2026-09-05
og_description: 使用 Aspose.Words 在 Word 文件中建立矩形形狀，然後了解如何在 Word 中插入橢圓形並將形狀群組，以實現複雜的版面配置。
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: 在 Word 中建立矩形形狀並將形狀分組 – Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 Aspose.Words 在 Word 中建立矩形形狀與群組形狀
url: /zh-hant/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 Aspose.Words 建立矩形形狀並群組形狀

如果您需要在 Word 文件中**建立矩形形狀**，本指南將示範使用 Aspose.Words for .NET 的完整步驟。您還會看到如何插入橢圓形、在 Word 中群組形狀，並將結果儲存為 DOCX 檔案。此解決方案適用於任何 .NET 6 以上的專案，且不需要在伺服器上安裝 Microsoft Office。

本教學涵蓋從專案設定到處理常見版面配置問題的所有步驟，讓您可以直接複製程式碼並立即執行。

## Prerequisites

在開始之前，請確保您已具備：

* 已安裝 .NET 6 SDK 或更新版本  
* 支援 NuGet 的 IDE（Visual Studio、Rider 或 VS Code）  
* Aspose.Words for .NET 授權（或臨時評估金鑰）  
* 基本的 C# 與 Word 文件結構知識  

上述項目可確保程式碼能編譯，且形狀能正確呈現。

## Step 1: Set up the project and add Aspose.Words

建立一個新的 Console 專案，並加入 Aspose.Words 套件：

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

此套件提供本教學中會使用到的 `Document`、`DocumentBuilder`、`Shape` 與 `GroupShape` 類別。

## Step 2: Initialize a blank document and a builder

`Document` 物件代表整個 Word 檔案，而 `DocumentBuilder` 讓您以程式方式插入內容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

先建立文件可確保後續所有形狀操作都有有效的容器。

## Step 3: **Create rectangle shape** and set its dimensions

矩形是最常用的文字或圖片容器。您需要以點 (pt) 為單位定義其大小 (1 pt ≈ 1/72 英吋)。

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

此步驟的重要性在於：`Shape` 類別封裝了幾何、填色與線條屬性。於插入前先設定 `Width` 與 `Height` 可保證形狀以預期尺寸顯示。

## Step 4: **How to insert ellipse word** – add an ellipse shape

橢圓形可用於圖示、標記或裝飾元素。程式碼與建立矩形相同，唯一不同的是 `ShapeType`。

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

`FillColor` 與 `Line.Color` 屬性示範了如何在不使用外部圖片的情況下自訂外觀。

## Step 5: **Group shapes in Word** – combine rectangle and ellipse

群組可讓您一次移動、調整大小或旋轉多個形狀。當需要組合圖形（例如帶標籤的圖示）時，這是必備功能。

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

呼叫 `AppendChild` 後，原始形狀會從文件主流程中移除，成為 `GroupShape` 的子項目。群組會表現為單一形狀，簡化後續的版面調整。

## Step 6: Save the document

最後，將文件寫入磁碟。您可以選擇任何支援的格式（`.docx`、`.pdf`、`.html` 等），本教學保留原生 Word 格式。

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

執行程式後，於 Microsoft Word 開啟 *GroupShape.docx*，即可看到已群組的矩形與橢圓，且位置符合您指定的座標。

## Common variations and edge cases

| 情況 | 需要變更的項目 | 原因 |
|-----------|----------------|--------|
| **不同的尺寸單位** | 使用 `ConvertUtil.InchToPoint(2.5)` 以英吋為單位，或 `ConvertUtil.MillimeterToPoint(30)` 以公釐為單位。 | 在使用非點數測量時，使程式碼更易讀。 |
| **在矩形內加入文字** | 建立 `Paragraph` 節點，設定其 `Text` 屬性，並透過 `AppendChild` 加入至 `rectangleShape`。 | 讓您在形狀內加上標籤，而不需要額外的文字方塊。 |
| **旋轉群組** | 設定 `groupShape.Rotation = 45;`（度）。 | 可用於建立斜向徽章或浮水印。 |
| **另存為 PDF** | 呼叫 `doc.Save("GroupShape.pdf");`。 | Aspose.Words 會自動將向量形狀光柵化為 PDF 輸出。 |
| **多個群組** | 建立額外的 `GroupShape` 實例，並重複 append/insert 步驟。 | 可實現包含多個獨立組合的複雜頁面版面配置。 |

### Pro tip

始終在群組之前**先加入形狀**。若嘗試將已屬於其他群組的形狀再度群組，Aspose.Words 會拋出 `ArgumentException`。在單一方法內建構群組可避免此執行時錯誤。

### Watch out for

* **座標系統** – `Left` 與 `Top` 是以頁面的左、上邊距為基準測量，而非文件邊緣。誤解此概念可能導致形狀被放置在頁面外。  
* **授權** – 若未使用有效授權，儲存的文件會出現「Aspose.Words for .NET Evaluation」浮水印。請在程式碼開頭盡早載入授權 (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) 以避免此情況。

## Full source code (runnable)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

執行此程式會產生 *GroupShape.docx*，其中的群組形狀完全符合說明內容。

## Conclusion

您現在已掌握如何使用 Aspose.Words **建立矩形形狀**、**插入橢圓形**，以及**在 Word 中群組形狀**。完整範例展示了從初始化文件到儲存最終檔案的完整工作流程，讓您能將形狀處理整合至任何自動化報表或文件產生解決方案中。

### What’s next?

* 探索 **aspose.words create shapes**，以建立更複雜的幾何圖形，例如 `Polygon` 或 `Freeform`。  
* 結合群組形狀與 **content controls**，打造動態範本。  
* 將 DOCX 轉換為 PDF 或 HTML，觀察向量形狀在不同格式下的呈現方式。  

歡迎嘗試不同的尺寸、顏色與旋轉角度。當您熟練形狀群組後，即可在 Word 文件內直接建立複雜的圖表、徽章與自訂 UI 元件。

## What Should You Learn Next?

以下教學與本指南所示技術緊密相關，能進一步深化您的應用。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索替代實作方式。

- [在 Word 文件中使用 Aspose.Words for .NET 建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words for .NET 在 Word 文件中插入形狀](/words/english/net/working-with-shapes/insert-shape/)
- [使用 C# 在 Word 中建立矩形形狀 – 步驟說明指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}