---
category: general
date: 2026-10-26
description: 在 C# 中建立一個空白的 Word 文件，學習如何插入群組形狀，然後向群組中加入矩形形狀。本指南逐步說明如何將多個形狀群組。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: zh-hant
lastmod: 2026-10-26
og_description: 在 C# 中建立空白 Word 文件，了解如何插入群組，然後加入矩形形狀。完整程式碼範例教你掌握多個形狀的群組。
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: 建立空白 Word 文件並將多個形狀群組 – C# 教學
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 如何建立空白 Word 文件並將多個形狀群組
url: /zh-hant/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何建立空白 Word 文件並群組多個圖形

如果您需要以程式方式 **create blank Word document**，本教學會完整示範。您將看到如何插入群組圖形，然後 **add rectangle** 到該群組，涵蓋從空白文件到群組圖形的完整工作流程。

處理 Word 檔案通常需要將多個圖形一起排列——想像一個由多個圖形組成的圖表。完成本指南後，您將能夠 **group multiple shapes**、插入 **rectangle shape**，並了解 **how to insert group** 與 **how to add rectangle** 的乾淨且可重複使用的做法。

## 您需要的條件

* .NET 6.0 或更新版本（此程式碼亦適用於 .NET Framework 4.6+）
* **Aspose.Words for .NET** NuGet 套件 (`Install-Package Aspose.Words`)
* 具備 C# 基礎知識以及 Visual Studio IDE（任何 IDE 都可）

> **Pro tip:** Aspose.Words 完全離線執行；安裝套件後不需要網路連線。

## 步驟 1：建立空白 Word 文件

第一個操作是實例化一個空的 `Document` 物件。此物件代表您稍後將加入圖形的 **blank Word document**。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters:* 沒有任何節或段落的 `Document` 仍然是有效的 .docx 檔案。從乾淨的起點開始，可確保不會有隱藏的格式干擾您之後加入的圖形。

## 步驟 2：插入群組圖形（how to insert group）

一個 **group shape** 如同容器，可容納其他繪圖物件。在 Aspose.Words 中，您可以使用 `InsertGroupShape` 來建立它。

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*Why use a group?* 群組可讓您將多個圖形作為單一單位移動、旋轉或調整大小。這對於需要保持對齊的圖表而言是必須的。

## 步驟 3：插入矩形圖形（insert rectangle shape）

現在在文件中加入一個矩形。`InsertShape` 方法會回傳一個 `Shape` 物件，您稍後可以將其附加到群組中。

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*Why a rectangle?* 矩形是流程圖、使用者介面模型圖與佔位圖形最常見的組件。其尺寸以點 (points) 表示 (1 pt ≈ 1/72 inch)。

## 步驟 4：將矩形加入群組（how to add rectangle）

使用 `InsertShape` 建立的圖形直接位於文件主體。若要將其納入群組，請對 `GroupShape` 呼叫 `AppendChild`。

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*What happens under the hood?* `AppendChild` 會將矩形節點從文件的主要故事移至群組的內部集合，同時保留相對於群組原點的大小與位置。

## 步驟 5：儲存文件

最後，將檔案寫入磁碟。您可以在 Microsoft Word 中開啟產生的 `.docx`，查看已群組的矩形。

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **Edge case:** 若您打算將更多圖形（例如圓形、線條）加入同一群組，請在儲存前對每個新圖形重複 **Step 3** 與 **Step 4**。群組會自動調整其邊界框以容納所有子圖形。

## 如何群組多個圖形 – 延伸範例

以下是一段快速程式碼，將第二個圖形（橢圓）加入同一群組，示範在單一文件中 **group multiple shapes**。

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

當您開啟 `GroupedShapeExample.docx` 時，若在 Word 中選取群組，矩形與橢圓會一起移動。

## 常見問題與疑難排解

| Question | Answer |
|----------|--------|
| **我需要 Aspose.Words 的授權嗎？** | 免費評估版可在未授權的情況下使用，但會加上浮水印。正式環境請套用授權以移除浮水印並解鎖完整效能。 |
| **我可以精確定位圖形嗎？** | 可以。插入圖形後，您可以設定 `Shape.Left`、`Shape.Top`、`Shape.Width` 與 `Shape.Height` 屬性。 |
| **如果矩形在儲存後消失該怎麼辦？** | 請確保在插入矩形後 *呼叫* `group.AppendChild(rectangle)`。必須先將圖形加入文件主體，然後再移入群組。 |
| **可以跨不同節群組圖形嗎？** | 不能。群組內的所有圖形必須屬於同一個 story（節）。如有需要，請在每個節建立獨立的群組。 |

## 重點回顧

您現在已了解如何使用 Aspose.Words for .NET **create blank Word document**、**insert group**、**add rectangle**，以及 **group multiple shapes**。上述完整可執行的範例可直接複製到 console 應用程式中，即可立即執行。

## 往後步驟

* 嘗試不同的 **insert rectangle shape** 大小與顏色 (`rectangle.FillColor = Color.LightBlue;`).  
* 探索其他圖形類型（`ShapeType.Polygon`、`ShapeType.Line`）以豐富您的圖表。  
* 了解如何將最終的 `.docx` 轉換為 PDF (`doc.Save("output.pdf");`) 以供發佈。  
* 深入了解 **how to add rectangle** 到已包含文字的現有文件——使用 `DocumentBuilder.MoveTo` 來定位群組所在位置。

歡迎依您的報表或圖表產生需求自行調整程式碼。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [如何在 C# 中建立空白 Word 文件並群組圖形](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [如何在 Word 中群組圖形並將圖形加入 Word 文件](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [如何使用 Aspose.Words 在 Word 中建立矩形圖形並群組圖形](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}