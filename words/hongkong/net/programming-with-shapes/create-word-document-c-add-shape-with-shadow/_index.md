---
category: general
date: 2026-03-27
description: 使用 C# 建立 Word 文件，學習如何新增形狀、為形狀套用陰影，以及設定陰影距離。Aspose.Words 步驟教學指南。
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: zh-hant
og_description: 使用 C# 建立 Word 文件，加入矩形形狀與自訂陰影。請參考本完整教學，設定陰影距離與樣式。
og_title: 使用 C# 建立 Word 文件 – 加入帶陰影的圖形
tags:
- Aspose.Words
- C#
- Document Automation
title: 使用 C# 建立 Word 文件 – 為圖形添加陰影
url: /zh-hant/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立 Word 文件 C# – 新增帶陰影的圖形

有沒有需要 **create word document c#** 且包含一個精美樣式的矩形？也許你正在製作報告範本，想要加入細緻的投影陰影讓版面更突出。在本教學中，我們將一步步說明如何新增圖形、對圖形套用陰影，甚至使用 Aspose.Words 調整陰影距離。

我們會從空白文件開始，插入一個矩形，套用預設陰影，最後儲存檔案。完成後，你將得到一個可直接在 Word 開啟並立即看到效果的 .docx 檔案。無需外部工具，純粹使用 C# 程式碼。

## 前置條件

- 已安裝 .NET 6（或任何較新的 .NET Framework）。
- Visual Studio 2022 或搭配 C# 擴充功能的 VS Code。
- Aspose.Words for .NET NuGet 套件（`Aspose.Words` 版本 23.12 或更新）。  
  你可以透過套件管理員主控台加入：

  ```powershell
  Install-Package Aspose.Words
  ```

就這樣 — 不需要額外的 DLL 或 COM interop。

## 第一步：初始化新文件與 Builder – *create word document c#* 基礎

首先，我們需要一個代表 Word 檔案的 `Document` 物件，以及用來編輯它的 `DocumentBuilder`。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **為什麼這一步很重要：** `Document` 類別是所有 Word 部件（頁面、樣式、圖片）的容器。Builder 是高階 API，抽象化低階節點操作，讓你能輕鬆 **create word document c#** 而不必直接處理 XML。

## 第二步：插入矩形圖形 – *how to create rectangle*  

現在我們要在頁面上放置一個矩形。尺寸以點 (pt) 為單位（1 pt ≈ 1/72 英吋）。

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **小技巧：** 若需要其他形狀，只要將 `ShapeType.Rectangle` 換成 `ShapeType.Ellipse`、`ShapeType.Triangle` 等等。相同程式碼同樣適用於任何類型的 **how to add shape**。

## 第三步：套用預設陰影並微調 – *apply shadow to shape*  

Aspose.Words 內建多種預設陰影格式。我們將使用 `Preset1`，然後自訂距離、模糊、透明度與顏色。

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **為什麼要自訂陰影？** `Distance` 屬性控制陰影與矩形之間的距離——可視為 3D 渲染中的「提升」效果。調整 `BlurRadius` 會使邊緣變得柔和，而 `Transparency` 則能營造細緻、專業的外觀。此步驟滿足 **set shadow distance** 的需求，並示範如何以彈性方式 **apply shadow to shape**。

## 第四步：儲存文件 – *create word document c#* 完成

最後，將文件寫入磁碟。請將路徑調整為你有寫入權限的資料夾。

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

在 Microsoft Word 中開啟產生的檔案，你會看到一個淡藍色的矩形，帶有向右下偏移 5 pt 的柔和灰色陰影。這就是你成功 **create word document c#** 並加入樣式圖形的視覺證明。

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="create word document c# 範例，顯示帶陰影的矩形"}

## 可選變化與邊緣情況

| Scenario | What to Change | Why it Matters |
|----------|----------------|----------------|
| **不同的陰影樣式** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | 提供更具戲劇性的外觀，且不需額外程式碼。 |
| **無預設 – 自訂陰影** | Omit `Format` and set `OffsetX`, `OffsetY` manually. | 完整掌控方向與深度。 |
| **多個圖形** | Call `builder.InsertShape` again before saving. | 適用於包含圖示、標誌等的複雜範本。 |
| **與舊版 Aspose 相容性** | Use `ShadowEffect` class (available in v20.x). | 確保程式碼在舊版專案中仍能執行。 |
| **儲存為 PDF** | `document.Save("ShadowShape.pdf");` | PDF 輸出中會呈現相同的陰影效果。 |

> **常見問題：** *如果陰影在 Word 中未顯示，該怎麼辦？*  
> 請確認你使用的是較新版的 Aspose.Words（≥ 22.9）。舊版對陰影的支援有限。亦請確認文件是在較新版的 Word（2016 以上）開啟。

## 完整範例程式

以下是完整、可直接複製貼上的程式。它包含所有 `using` 指令、註解與錯誤處理，確保執行順暢。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

執行程式後，前往 `C:\Temp\ShadowShape.docx`，即可看到我們設定的矩形與精確陰影。

## 重點回顧與後續步驟

- 你現在已了解如何 **create word document c#**、插入矩形，並以自訂 **set shadow distance** 方式 **apply shadow to shape**。  
- 此範例使用 Aspose.Words，抽象化 OpenXML 的複雜性，並保證在不同 Word 版本間呈現一致。  
- 想更進一步嗎？試著結合多個圖形、在矩形內加入文字，或將同一文件匯出為 PDF，觀察陰影的轉換效果。

### 相關主題你可能會感興趣

- **How to add shape** 用於頁首/頁尾的品牌標示。  
- 使用 **Aspose.Words** 程式化插入圖表與表格。  
- 自訂圖片的 **shadow effects**（而非向量圖形）。  
- 自動化大量文件產生，如發票或證書。

盡情試驗、破壞程式碼再重新建構——這是內化概念的最快方式。若遇到問題，請在下方留言或查閱官方 Aspose.Words 文件，以獲得更深入的 API 資訊。

祝程式開發愉快，讓你的 Word 檔案更顯精緻！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}