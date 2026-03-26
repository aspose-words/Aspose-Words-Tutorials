---
category: general
date: 2026-03-25
description: 在 C# 中建立 PDF 文件，並學習如何加入矩形形狀、設定填充顏色、調整形狀大小以及設定形狀透明度，只需幾個步驟。
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: zh-hant
og_description: 在 C# 中建立 PDF 文件，了解如何加入矩形、設定填色、尺寸與透明度，以獲得精緻的 PDF 輸出。
og_title: 使用矩形形狀建立 PDF 文件 – C# 教學
tags:
- C#
- PDF
- Aspose.Words
title: 使用矩形形狀建立 PDF 文件 – 完整 C# 指南
url: /zh-hant/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用矩形形狀建立 PDF 文件 – 完整 C# 指南

有沒有需要 **建立 PDF 文件**，但想加入自訂樣式的圖形卻不知從何下手？你並不孤單。無論是建立報表產生器或行銷傳單，能以程式方式繪製矩形、設定填色、調整尺寸，甚至調整透明度，都能讓你的 PDF 看起來更專業。

在本教學中，我們將一步步示範完整、可直接執行的 C# 範例，說明如何 **建立 PDF 文件**、**加入矩形形狀**、**設定填色**、**定義形狀尺寸**，以及 **設定形狀透明度** 以產生細緻的外部陰影。完成後，你會得到一個名為 `shadow.pdf` 的單一 PDF 檔案，打開即可看到結果。

> **專業小技巧：** 同樣的作法也適用於其他形狀（橢圓、線條等）——只要將 `ShapeType.RECTANGLE` 換成你需要的類型即可。

---

## 需要的前置條件

| 先決條件 | 重要原因 |
|--------------|----------------|
| **.NET 6+** (或 .NET Framework 4.6+) | Aspose.Words 函式庫針對現代執行環境。 |
| **Aspose.Words for .NET** NuGet 套件 | 提供 `Document`、`Shape`、`ShadowEffect` 等相關類別。 |
| **C# IDE**（Visual Studio、Rider、VS Code） | 讓除錯與執行範例更輕鬆。 |
| **基本的 C# 知識** | 只要了解語法即可，無需深入探討。 |

你可以透過指令列安裝此函式庫：

```bash
dotnet add package Aspose.Words
```

就這樣——不需要額外的 DLL，也沒有本機相依性。套件安裝完成後，以下程式碼即可編譯執行。

---

## 步驟說明

以下我們將整個流程分成五個邏輯步驟。每個步驟都有清楚的標題（方便 AI 模型索引）以及可直接複製貼上的程式碼區塊。

### ## 1. 建立 PDF 文件並準備畫布

首先，我們會建立一個 `Document` 物件。把它想像成最終會變成 PDF 檔案的空白畫布。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **為什麼這樣做？** `Document` 會保存所有節、段落與圖形。從乾淨的物件開始，可避免前一次執行遺留下的隱藏 artefacts。

### ## 2. 新增矩形形狀 – 設定填色與形狀尺寸

接著，我們建立矩形、設定亮黃色填色，並定義其寬高。此步驟同時涵蓋 **add rectangle shape**、**set fill color** 與 **set shape size**。

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **備註：** 寬度與高度的單位為點 (1 point = 1/72 吋)。依需求自行調整數值即可符合版面配置。

### ## 3. 套用外部陰影並設定形狀透明度

陰影能增加立體感，而調整不透明度則是 **set shape transparency** 的核心。以下程式碼會設定一個 30 % 透明度的灰色外部陰影。

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **為什麼要設定透明度？** 30 % 的半透明陰影看起來較為柔和，避免矩形在頁面上顯得「平板」。

### ## 4. 將圖形插入文件正文

現在把矩形放入文件第一節的第一段落中。這一步將所有前面的設定串連起來。

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **特殊情況：** 若需要將圖形放在新頁面，請在加入圖形前加入 `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;`。

### ## 5. 儲存文件為 PDF 檔案

最後，我們把記憶體中的結構寫入實體 PDF 檔案。檔案會寫入你指定的資料夾。

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

執行程式後，會產生名為 `shadow.pdf` 的檔案。開啟後會看到一個黃色矩形，右下方有 4 點偏移的柔和灰色陰影——正是程式碼所描述的效果。

> **預期輸出：** 單頁 PDF，矩形位於頁面左上角附近，填滿黃色，尺寸為 200 × 100 點，並帶有半透明的外部陰影。

---

## 完整範例（直接複製貼上）

以下是完整的程式檔案內容，直接貼到新的 Console 專案即可執行。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **小技巧：** 把 `YOUR_DIRECTORY` 替換成絕對路徑（例如 `C:\Temp`）或相對路徑（例如 `.\output`）。程式會在資料夾不存在時自動建立。

---

## 常見問題 (FAQ)

**Q: 可以改變矩形在頁面上的位置嗎？**  
A: 當然可以。在把圖形加入段落前，設定 `rectangle.Left` 與 `rectangle.Top`（單位同樣為點）。

**Q: 如果想要填色透明而不是陰影透明，該怎麼做？**  
A: 使用 `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` ——第一個參數是 Alpha 通道 (0‑255)，128 代表約 50 % 透明度。

**Q: 這在 .NET Core 上能跑嗎？**  
A: 能。Aspose.Words 支援 .NET Standard 2.0+，因此可在 .NET 6、.NET 7 或 .NET Framework 4.6+ 上執行相同程式碼。

**Q: 要如何加入多個圖形？**  
A: 只要對每個圖形重複步驟 2‑4，並視需要插入不同的段落或節即可。

---

## 結論

我們已從頭開始 **建立 PDF 文件**、**加入矩形形狀**、**設定填色**、**定義尺寸**，並 **調整形狀透明度** 以產生精緻的陰影效果。此範例程式碼自給自足、執行時間不到一分鐘，展示了製作更複雜 PDF 版面的核心概念。

準備好接受下一個挑戰了嗎？試著把矩形換成圓角形狀、在圖形內嵌入圖片，或自動產生目錄。相同的 API 讓你可以層疊文字、影像與向量——無限可能等你探索。

如果本指南對你有幫助，請在 GitHub 上給予星標，與同事分享，或留下你的變化版本評論。祝開發愉快！

---

![create pdf document with rectangle shape example](/images/rectangle-shadow.png "Screenshot showing the created PDF with a yellow rectangle and gray outer shadow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}