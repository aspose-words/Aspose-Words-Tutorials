---
category: general
date: 2026-03-01
description: 使用 Aspose.Words 快速在 PDF 中添加矩形。了解如何插入形狀到 PDF、向 PDF 添加圖形，以及以程式方式建立帶自訂陰影的
  PDF 文件。
draft: false
keywords:
- add rectangle to pdf
- insert shape pdf
- add graphics to pdf
- create pdf document programmatically
- create pdf with shape
language: zh-hant
og_description: 使用 Aspose.Words 為 PDF 新增矩形。本教學示範如何在 PDF 中插入形狀、加入圖形，以及以 C# 程式碼建立 PDF
  文件。
og_title: 使用 Aspose.Words 向 PDF 添加矩形 – 完整指南
tags:
- pdf
- aspnet
- csharp
- graphics
title: 使用 Aspose.Words 為 PDF 添加矩形 – 逐步指南
url: /zh-hant/python/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words 中向 PDF 添加矩形 – 完整指南

是否曾經需要 **add rectangle to PDF**（向 PDF 添加矩形），卻不確定該使用哪個 API 呼叫？你並不是唯一有此困惑的人——開發者常常會問：「如何在 PDF 中插入形狀，同時保持檔案輕量？」好消息是 Aspose.Words 讓這變得非常簡單。在本教學中，我們將完整說明從程式化建立 PDF 文件到為矩形套用陰影樣式的整個流程。

我們還會額外提供幾個小技巧：你將學會如何 **add graphics to PDF**（向 PDF 添加圖形），看到 **insert shape PDF**（插入形狀 PDF）的具體步驟，並以一個可直接執行的範例結束，該範例 **creates PDF with shape**（建立帶形狀的 PDF）。不需要外部參考，僅提供一個可自行複製貼上的完整解決方案。

## 前置條件

- .NET 6.0 或更新版本（Aspose.Words 支援 .NET Standard 2.0+）
- 有效的 Aspose.Words for .NET 授權或臨時評估金鑰
- Visual Studio 2022（或任何你喜歡的 IDE）
- 基本的 C# 知識——不需要高深技巧，只要能執行主控台應用程式

就這樣。如果你已具備上述條件，就可以開始了。

## 步驟 1：以程式方式建立 PDF 文件

當你想要 **add rectangle to PDF** 時，第一件事就是建立一個空白文件。把 `Document` 類別想像成一張白紙；之後加入的所有內容都會存在於其中。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – initialise a new empty document
        Document doc = new Document();

        // The rest of the steps follow...
```

為什麼要從空白文件開始？因為這樣可以確保你對每個元素都有完整的控制權——不會在之後與隱藏的頁眉或頁腳糾纏。

## 步驟 2：初始化 DocumentBuilder 以插入 shape PDF

`DocumentBuilder` 就像你的繪圖筆刷。它知道如何放置文字、影像，以及對我們而言最關鍵的形狀。若沒有它，你必須自行操作底層的節點樹——對大多數開發者而言是噩夢。

```csharp
        // Step 2 – create a builder that will let us add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

請注意，我們尚未手動新增任何頁面。Builder 會在你第一次插入內容時自動建立頁面，讓程式碼保持簡潔。

## 步驟 3：插入矩形形狀 – “add rectangle to PDF” 的核心

現在進入有趣的部分：插入矩形。`InsertShape` 方法支援數十種 `ShapeType` 值；我們將選擇 `ShapeType.Rectangle`，並設定大小為 200 × 100 點。

```csharp
        // Step 3 – insert a rectangle (200 × 100 points) into the document
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

此時 PDF 已經包含一個簡單的矩形。如果此時開啟檔案，你會看到一個位於第一頁左上角的方框。這就是 **adding graphics to PDF** 的基礎。

## 步驟 4：為矩形設定樣式 – 加入自訂陰影

沒有樣式的矩形很無聊。讓我們為它加上一個細緻的投影，使其在 PDF 渲染時更突出。`ShadowFormat` 物件負責控制從模糊半徑到不透明度的所有設定。

```csharp
        // Step 4 – configure a custom shadow for the shape
        ShadowFormat shadow = rectangle.ShadowFormat;
        shadow.Visible = true;
        shadow.BlurRadius = 8.0;          // pixels
        shadow.Distance = 5.0;           // points from the shape
        shadow.Direction = 45.0;         // degrees clockwise
        shadow.Opacity = 0.6;            // 0‑1 range
        shadow.Color = Color.Black;
```

為什麼要加陰影？除了提升美觀外，陰影還能協助區分重疊的圖形——在較複雜的報告中 **add graphics to PDF** 時可能會需要。

## 步驟 5：儲存檔案 – 完成 “create PDF with shape” 工作流程

最後一行會將所有內容寫入磁碟。Aspose.Words 會自動選擇正確的 PDF 版本並嵌入必要的資源。

```csharp
        // Step 5 – save the document as a PDF file
        doc.Save(@"C:\Temp\ShapeWithShadow.pdf");
    }
}
```

開啟 `ShapeWithShadow.pdf`，你會看到一個帶有精緻陰影的矩形自豪地呈現在頁面上。這就是完整的 **create pdf document programmatically** 流程，全部不到 30 行程式碼即可完成。

## 完整範例 – 從頭到尾建立帶形狀的 PDF

以下是完整的程式碼，你可以直接複製貼上到新的 Console App 專案中。它包含所有 `using` 陳述式、`Main` 方法，以及供未來參考的簡短註解標頭。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectanglePdfDemo
{
    /// <summary>
    /// Demonstrates how to add a rectangle to PDF, configure a shadow,
    /// and save the result using Aspose.Words for .NET.
    /// </summary>
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty PDF document
            Document doc = new Document();

            // 2️⃣ Initialise a DocumentBuilder – the tool that lets us add content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a rectangle shape (200 × 100 points) – this is the core of "add rectangle to pdf"
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

            // 4️⃣ Apply a custom shadow – makes the graphic stand out
            ShadowFormat shadow = rect.ShadowFormat;
            shadow.Visible = true;
            shadow.BlurRadius = 8.0;   // pixels
            shadow.Distance = 5.0;    // points
            shadow.Direction = 45.0;  // degrees
            shadow.Opacity = 0.6;     // semi‑transparent
            shadow.Color = Color.Black;

            // 5️⃣ Save the document – the final step in creating a PDF with shape
            string outputPath = @"C:\Temp\ShapeWithShadow.pdf";
            doc.Save(outputPath);

            Console.WriteLine($"PDF saved successfully to {outputPath}");
        }
    }
}
```

**預期結果：** 一個單頁的 PDF，裡面有一個 200 × 100 點的矩形位於左上角附近，並帶有柔和的 45 度陰影。使用任何 PDF 檢視器開啟檔案即可驗證。

## 常見問題與邊緣情況

### 這能套用於其他形狀類型嗎？

當然可以。將 `ShapeType.Rectangle` 替換為 `ShapeType.Ellipse`、`ShapeType.Triangle`，或 Aspose.Words 支援的 150 多種選項之一。`ShadowFormat` 的屬性同樣適用。

### 如果我需要將矩形放在特定頁面上該怎麼做？

在插入形狀之後，你可以透過在呼叫 `InsertShape` 前調整 builder 的 `CurrentPage` 屬性，將其移至其他頁面。例如：

```csharp
builder.MoveToPage(3);
Shape rectOnPage3 = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

### 我可以變更矩形的填色嗎？

可以的。使用 `FillColor` 屬性：

```csharp
rect.FillColor = Color.LightBlue;
```

### 這會對檔案大小產生什麼影響？

加入簡單的形狀與陰影只會增加幾 KB。如果你開始堆疊大量圖形，建議壓縮影像或使用向量形狀，以保持 PDF 輕量。

### 正式環境需要授權嗎？

Aspose.Words 在評估模式下仍可運作，但輸出的 PDF 會帶有浮水印。購買授權即可解除限制並移除浮水印。

## 小技巧與竅門（進階）

- **批次插入：** 若需要插入數十個矩形，可遍歷座標集合並重複使用同一個 `DocumentBuilder`——效能保持線性。
- **圖層設定：** 若希望矩形隨文字流動，將 `rect.WrapType = WrapType.Inline`；若希望文字環繞矩形，則使用 `WrapType.Square`。
- **PDF/A 相容性：** 若需要符合保存標準的 PDF，於儲存前呼叫 `doc.CompatibilityOptions.OptimizeForPdfA = true;`。

## 視覺摘要

![向 PDF 添加矩形範例](https://example.com/rectangle-shadow.png "向 PDF 添加矩形範例")

此圖說明最終的 PDF 版面：一個帶有細緻陰影的簡潔矩形，正是我們程式碼產生的結果。

## 結論

現在你已了解如何使用 Aspose.Words **how to add rectangle to PDF**，以及如何 **insert shape PDF**，並且能以自訂樣式 **add graphics to PDF**——同時 **creating PDF document programmatically**，最後提供一個可於明天重複使用的 **create PDF with shape** 範例。

接下來，嘗試將矩形換成商標，或結合多個形狀來建立簡易圖表。你也可以探索文字環繞、旋轉，甚至在形狀內嵌入超連結。API 功能相當豐富，讓你能將靜態 PDF 轉變為互動且圖形豐富的報告，而無需離開 C#。

盡情試驗吧，若遇到問題，歡迎在下方留言。祝開發愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}