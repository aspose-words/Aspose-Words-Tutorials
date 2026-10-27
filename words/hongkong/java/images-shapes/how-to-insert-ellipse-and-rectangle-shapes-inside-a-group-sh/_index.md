---
category: general
date: 2026-10-23
description: 學習如何使用 Aspose.Words 在 Word 中插入橢圓形以及添加矩形形狀。包括將游標移至形狀以及如何建立群組形狀。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: zh-hant
lastmod: 2026-10-23
og_description: 如何在 Word 中使用 Aspose.Words 插入橢圓形及新增矩形形狀。請參考逐步指南，將游標移至形狀並建立群組形狀。
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: 如何在 Word 群組圖形中插入橢圓形與矩形形狀
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 如何在 Aspose.Words 中於群組形狀內插入橢圓形與矩形形狀
url: /zh-hant/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中於群組形狀內插入橢圓形與矩形形狀

如果您需要了解 **how to insert ellipse** 在 Word 文件中以程式方式插入的方式，本指南將展示完整流程。您還會看到 **how to add rectangle** 形狀，學習 **move cursor to shape**，以及發現 **how to create group shape** 能夠容納多個繪圖物件的方式。

Word 自動化通常需要精確定位繪圖物件。完成本教學後，您即可產生一個包含群組矩形與橢圓形的 `.docx` 檔案，方便進一步樣式設定或匯出。除了 Aspose.Words for .NET 函式庫與 .NET 開發環境外，無需其他外部工具。

## 前置條件

* 已安裝 .NET 6.0 或更新版本。
* 已於專案中加入 Aspose.Words for .NET（NuGet 套件 `Aspose.Words`）。
* 具備 C# 語法與 Visual Studio（或任何 IDE）的基本知識。

這些需求可確保程式碼在未額外設定的情況下成功編譯。

## 如何在 Word 中建立群組形狀

群組形狀充當容器，讓您能將多個形狀一起移動、旋轉或格式化，視為單一單元。以下程式碼會建立一個特定尺寸（300 × 200 點）的群組，並為後續的繪圖操作做好文件準備。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*此步驟的重要性*：群組形狀定義了本地座標系統。所有在將游標移入群組後加入的形狀，都會相對於群組的原點定位，使版面計算變得直接。

## 如何在 Word 中加入矩形形狀

既然群組已建立，您即可在其中 **insert rectangle shape**。此矩形可作為背景或其他內容的視覺佔位。

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*說明*：`MoveTo(group)` 告訴建構器目前的插入點位於群組形狀。若未移動游標，`InsertShape` 會將矩形加入主文件正文，而非群組內。

## 如何插入橢圓形

矩形已就位後，您現在可以示範 **how to insert ellipse**。橢圓形將置於同一群組的中心，若需要可與矩形重疊。

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*為何必須移動游標*：每次呼叫 `InsertShape` 都會遵循目前的游標位置。再次呼叫 `MoveTo(group)` 可確保橢圓形同樣成為群組的子項，維持預期的層級結構。

## 在插入其他物件前先將游標移至形狀

若稍後需要加入更多形狀，請在每次插入前皆 **move cursor to shape**。此模式可避免意外將物件放置於群組外部。

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*提示*：重複使用 `MoveTo(group)` 成本低且提升程式碼可讀性。因為插入上下文明確，也使未來維護更為簡單。

## 儲存文件

最後，將文件寫入磁碟。範例會將檔案儲存為 `GroupShape.docx`，放在您指定的資料夾中。

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

當您在 Microsoft Word 中開啟儲存的檔案時，會看到一個包含矩形與橢圓形的單一群組，兩者皆正確定位。

### 預期輸出

* 一個名為 `GroupShape.docx` 的 `.docx` 檔案。
* 文件內部有一個尺寸為 300 × 200 點的群組繪圖物件。
* 在群組內：
  * 一個位於群組原點的矩形（100 × 50 點）。
  * 一個與矩形重疊的橢圓形（80 × 80 點）。
  * 任何在移動游標後您加入的其他形狀。

## 常見變化與邊緣情況

| 情況 | 建議做法 |
|-----------|----------------------|
| **Different unit sizes** | Aspose.Words 使用點 (1 pt = 1/72 in)。在呼叫 `InsertShape` 前，先將公分或英吋轉換為點。 |
| **Rotating shapes inside the group** | 插入形狀後，取得其 `ShapeBase` 物件並設定 `ShapeBase.RotationAngle`。 |
| **Adding text inside a shape** | 使用 `ShapeBase.AppendChild(new Paragraph(document))`，然後加入帶有所需文字的 `Run`。 |
| **Saving to PDF instead of DOCX** | 呼叫 `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – PDF 輸出中會保留群組層級結構。 |

這些變化說明，同樣的 **how to insert ellipse** 邏輯可套用於許多實務情境。

## 專業提示

* **Reuse the same `DocumentBuilder` instance** – 它可減少記憶體開銷，並保持文件狀態一致。
* **Validate shape dimensions** – 極大的寬度或高度可能在舊版 Word 中造成渲染問題。
* **Group before styling** – 在所有子項加入後再對群組套用填色或線條樣式，可確保外觀一致。

## 結論

您現在已了解如何在 Word 文件中使用 Aspose.Words 於群組容器內 **how to insert ellipse** 與 **how to add rectangle** 形狀。透過在每次插入前持續 **move cursor to shape**，您可維持清晰的層級結構，避免意外放置。完整範例可編譯、執行，並產生可進一步自訂或匯出的群組形狀。

準備好深入探索了嗎？試著將此技巧與 **how to create group shape** 結合，以製作複雜圖表，或與 **insert rectangle shape word** 搭配文字方塊，產生豐富的報告。祝開發愉快！

## 接下來您應該學習什麼？

以下教學涵蓋與本指南技術密切相關的主題。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [如何在 Word 中使用 Aspose.Words 建立矩形形狀與群組形狀](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [如何建立空白 Word 文件並在 C# 中加入隱藏的橢圓形](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [如何建立群組形狀 docx 並在 C# 中加入互動控制項](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}