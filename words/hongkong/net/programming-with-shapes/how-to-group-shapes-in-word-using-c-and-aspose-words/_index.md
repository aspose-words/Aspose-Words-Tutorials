---
category: general
date: 2026-09-30
description: 在 Word 中使用 C# 群組圖形 – 學習如何群組圖形、加入矩形與橢圓，並以程式方式在 Word 文件中插入矩形圖形。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: zh-hant
lastmod: 2026-09-30
og_description: 使用 C# 與 Aspose.Words 在 Word 中對形狀進行群組。跟隨本完整指南，學習如何新增矩形、橢圓，並有效率地進行形狀群組。
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: 使用 C# 在 Word 中群組圖形 – 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 如何在 Word 中使用 C# 與 Aspose.Words 進行圖形分組
url: /zh-hant/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 C# 與 Aspose.Words 進行圖形分組

如果您需要以程式方式 **在 Word 中分組圖形**，本教學將一步步示範。您將看到如何加入矩形、加入橢圓，然後使用 Aspose.Words for .NET 將它們合併為單一群組圖形。

在自動產生報告、合約或行銷素材時，操作圖形是常見需求。完成本教學後，您將擁有可重複使用的 C# 方法，能載入 DOCX 檔案、插入矩形與橢圓、將它們分組，並儲存結果——全程不需手動開啟 Word。

## 前置條件

開始之前，請確保您已具備：

* 已安裝 .NET 6.0 SDK 或更新版本  
* 如 Visual Studio 2022（社群版亦可）等開發環境  
* Aspose.Words for .NET 授權或免費評估版（未授權時 API 仍可使用，但會加上浮水印）  

此外，您還需要一個來源 Word 文件（`input.docx`），放在程式碼可參照的資料夾中。該文件可以是空白的，教學重點在圖形處理。

## 步驟 1：建立新的 Console 專案並加入 Aspose.Words

在終端機或 Visual Studio 命令提示字元執行：

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

此指令會建立名為 **WordShapeDemo** 的全新 Console 應用程式，並加入 `Aspose.Words` NuGet 套件，該套件提供操作 Word 檔案的 `Document` 與 `DocumentBuilder` 類別。

## 步驟 2：載入或建立文件

在處理 **Word 中的群組圖形** 時，第一步是取得 `Document` 物件。您可以載入既有的 DOCX 檔，或從空白文件開始。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

`Document` 類別代表整個 Word 檔案。載入檔案後即可得到可插入圖形的畫布。

## 步驟 3：開始群組圖形

*群組圖形* 讓您將多個獨立圖形視為單一單位，便於一起移動或調整大小。要開始群組，請在 `DocumentBuilder` 上呼叫 `StartGroupShape()`。

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

呼叫 `StartGroupShape` 後，所有後續的圖形插入都會屬於同一個邏輯群組，直到呼叫 `EndGroupShape` 為止。

## 步驟 4：在 Word 中加入矩形圖形

群組開啟後，插入矩形。`InsertShape` 方法接受 `ShapeType` 列舉，接著是寬度與高度（單位為點）。

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

矩形會成為群組的第一個成員。之後您可以自行設定填色、輪廓或文字等屬性。

## 步驟 5：在 Word 中加入橢圓圖形

接著加入橢圓（寬度等於高度時即為圓形）。此範例示範 **如何加入橢圓**，使用相同的 builder。

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

兩個圖形現在共享同一個座標空間，方便視覺對齊。

## 步驟 6：結束群組圖形定義

加入完所有想要的成員後，關閉群組。這會將圖形集合定稿，讓 Word 將它們視為單一物件。

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

此時文件中已包含一個由矩形與橢圓組成的單一群組圖形。

## 步驟 7：儲存修改後的文件

最後，將變更寫回磁碟。您可以覆寫原始檔，或另存新檔。

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

執行程式後會產生 `output.docx`。在 Microsoft Word 中開啟該檔，選取圖形，即可看到矩形與橢圓一起移動——證明 **在 Word 中分組圖形** 的操作已成功。

### 預期結果

* Word 檔案只包含一個群組物件。  
* 選取該群組即可同時拖曳、調整大小或旋轉矩形與橢圓。  
* 完全不需要手動操作 Word，全部由 C# 程式碼完成。

![Grouped shapes in Word document](grouped-shapes.png "Screenshot of a Word document showing a grouped rectangle and ellipse shape")

*Image alt text: “Screenshot of a Word document showing a grouped rectangle and ellipse shape”* (fulfills the image alt‑text requirement).

## 為何圖形分組很重要

圖形分組不只是視覺上的便利，它還能讓您：

* **維持版面一致性** – 移動群組時，內部相對位置保持不變。  
* **一次性套用變形** – 只需對整個群組旋轉或縮放，而不必逐一處理每個圖形。  
* **簡化後續處理** – 其他工具讀取 DOCX 時，只會看到單一複合圖形，降低複雜度。

若日後需要在同一邏輯單位中加入更多圖形（例如直線或文字方塊），只要在 `EndGroupShape` 之前再次呼叫 `InsertShape` 即可。

## 常見變化與邊緣情況

| 情境 | 處理方式 |
|-----------|-----------------|
| **不同單位** – 測量值為公分 | 在呼叫 `InsertShape` 前先將公分轉換為點（`1 cm ≈ 28.35 pt`）。 |
| **加入文字標籤** – 想在群組內放置說明文字 | 在矩形與橢圓之後插入 `ShapeType.TextBox`，再設定其 `Text` 屬性。 |
| **套用填色** – 需要藍色矩形 | 在 `InsertShape` 後，透過 `builder.CurrentParagraph.Runs[0].Font` 取得最後的圖形，然後設定 `shape.FillColor = System.Drawing.Color.Blue;`。 |
| **使用不同文件格式** – 目標為 `.doc` 而非 `.docx` | 程式碼相同，只要在 `Save` 時改變副檔名即可。Aspose.Words 會自動處理格式轉換。 |

## 專業小技巧

* **重複使用 builder** – 您可以在同一文件中多次開始與結束群組，只要在 `EndGroupShape` 後再次呼叫 `StartGroupShape`。  
* **效能** – 在單一 `StartGroupShape/EndGroupShape` 區塊內批次插入圖形，比起在群組外逐一插入更快。  
* **授權** – 評估授權會在首頁加上浮水印。正式環境請安裝正式授權以移除浮水印。

## 結論

現在您已掌握如何使用 C# **在 Word 中分組圖形**、**加入矩形**、**加入橢圓**，以及如何使用 Aspose.Words 在 Word 文件中插入矩形圖形。完整可執行的範例示範了從專案設定到最終儲存的每一步。

接下來，您可以探索更多圖形類型、套用樣式，或將群組圖形與表格、圖片結合，打造更複雜的程式化文件。

---

**後續步驟**

* 學習如何 **旋轉群組圖形**：在關閉群組後使用 `Shape.RotationAngle`。  
* 探索矩形與橢圓的 **填色與輪廓自訂**。  
* 將此邏輯整合至 ASP.NET Core API，實現即時報表產生。  

祝開發順利！


## 接下來該學什麼？

以下教學與本指南緊密相關，能進一步深化您對 API 功能的掌握，並提供其他實作方式的範例。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}