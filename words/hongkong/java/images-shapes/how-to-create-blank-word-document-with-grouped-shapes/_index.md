---
category: general
date: 2026-09-08
description: 學習如何使用 C# 建立空白 Word 文件、插入矩形形狀以及將多個形狀群組。請跟隨本逐步指南。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: zh-hant
lastmod: 2026-09-08
og_description: 在 C# 中建立空白 Word 文件、插入矩形形狀並將多個形狀群組。本教學將帶您完整了解整個過程。
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: 使用 C# 建立帶有群組圖形的空白 Word 文件
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: 如何建立帶有群組形狀的空白 Word 文件
url: /zh-hant/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何建立包含群組圖形的空白 Word 文件

如果您需要 **建立空白 Word 文件** 並包含自訂圖形，本指南將一步步說明。您將學習如何使用 Aspose.Words for .NET **插入矩形圖形**、**群組多個圖形**，以及 **將圖形加入群組**。

空白文件提供乾淨的畫布，而群組圖形讓您能一次移動、調整大小或旋轉它們。此教學涵蓋所有步驟——從初始化文件到儲存最終檔案——您只要將程式碼複製到自己的專案，即可立即看到結果。

## 您需要的條件

在開始之前，請確保您已具備：

* .NET 6.0 或更新版本（此程式碼亦相容於 .NET Framework 4.6+）
* 有效的 Aspose.Words for .NET 授權（免費評估版可用於測試）
* 開發環境，例如 Visual Studio 2022 或 Visual Studio Code
* 具備 C# 語法的基本認識

除 `Aspose.Words` 之外，無需其他 NuGet 套件。

## 如何建立空白 Word 文件

第一步是實例化一個 `Document` 物件。此物件代表一個可使用 `DocumentBuilder` 編輯的空白 `.docx` 檔案。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 建構子會在記憶體中建立 **空白 Word 文件**。`DocumentBuilder` 提供流暢的 API，讓您插入文字、圖片與繪圖物件。

## 在文件中插入矩形圖形

接著，加入一個矩形圖形。此矩形將成為稍後要建立的群組的第一個子項目。

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

使用 `ShapeType.Rectangle` 呼叫 `InsertShape` **插入矩形圖形**，位置位於目前游標所在處。寬度與高度以點（pt）為單位（1 pt ≈ 1/72 in）。

## 將多個圖形群組在一起

`GroupShape` 如同容器。群組內的所有子圖形會一起移動與變形。先建立群組，然後加入剛才建立的矩形。

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

`InsertGroupShape` 方法會在 builder 的游標位置放置一個空的群組。將矩形附加上去，即可 **群組多個圖形**——矩形成為群組內部節點集合的一部份。

## 將圖形加入群組並儲存檔案

現在加入第二個圖形——橢圓形，以示範多個物件共享同一容器。之後儲存文件。

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

當您將回傳的 `Shape` 附加到 `GroupShape` 時，`InsertShape` 呼叫會 **將圖形加入群組**。儲存 `Document` 會寫入 `.docx` 檔案，您可以在 Microsoft Word、LibreOffice 或任何相容的檢視器中開啟。

### 預期結果

開啟 *GroupShapeDemo.docx* 後，您會看到一個空白頁面，裡面有一個群組物件，包含淡藍色矩形與粉紅色橢圓。選取該群組即可同時移動兩個圖形，證明 **群組多個圖形** 已如預期運作。

## 為什麼使用 GroupShape？

* **原子化變換** – 縮放、旋轉或移動群組時，所有子圖形會同時以相同方式變化。
* **邏輯組織** – 將相關圖形聚集在一起，使文件結構更易於維護。
* **效能** – 渲染單一容器通常比處理多個獨立圖形更快。

若日後需要修改單一子圖形，可透過索引或其 `Name` 屬性從 `group.ChildNodes` 取得。

## 常見變化與邊緣情況

| 情境                                 | 如何調整程式碼                                                            |
|--------------------------------------|--------------------------------------------------------------------------|
| **不同的圖形類型**                | 將 `ShapeType.Rectangle` 或 `ShapeType.Ellipse` 替換為其他任意 `ShapeType` |
| **在圖形內加入文字**               | 在插入圖形後使用 `Shape.TextPath.Text = "Hello"`                        |
| **設定旋轉角度**                   | `group.Rotation = 45;`（度）                                             |
| **儲存為 PDF 而非 DOCX**          | `doc.Save("GroupShapeDemo.pdf");`                                        |
| **為群組套用邊框**                 | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`       |

## 專業提示

* **為圖形命名** – `rectangle.Name = "MyRect";` 可讓您日後更容易找到它們。
* **使用相對定位** – 若希望群組固定於頁面邊界，請將 `group.RelativeHorizontalPosition` 設為 `RelativeHorizontalPosition.Page`。
* **釋放資源** – 在較大型的應用程式中，將 `Document` 包在 `using` 區塊中，以即時釋放非受控記憶體。

## 完整原始碼，快速複製貼上

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

將程式碼複製到新的 Console 專案，還原 `Aspose.Words` NuGet 套件，然後執行。輸出檔案會出現在專案的 `bin/Debug/net6.0`（或等效）資料夾中。

## 後續步驟

現在您已能 **建立空白 Word 文件**、**插入矩形圖形**，以及 **群組多個圖形**，接下來可以探索：

* 在群組內加入 **文字方塊**，製作帶標籤的圖示。
* 使用 `doc.Save("image.png", SaveFormat.Png)` 將群組圖形匯出為影像。
* 將群組與表格結合，製作內容豐富的報告。

嘗試不同的圖形屬性、群組層級與匯出格式，充分發揮 Aspose.Words 繪圖功能的威力。

--- 

*提醒*: 群組圖形是保持 Word 文件整潔、程式碼易於維護的強大方式。祝開發順利！

## 接下來該學什麼？

以下教學涵蓋與本指南技術緊密相關的主題，並在此基礎上延伸。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [在 Word 中使用 C# 建立矩形圖形 – 步驟說明指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [在 Word 文件中插入圖形（使用 Aspose.Words for .NET）](/words/english/net/working-with-shapes/insert-shape/)
- [在 Word 文件中建立群組圖形（使用 Aspose.Words for .NET）](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}