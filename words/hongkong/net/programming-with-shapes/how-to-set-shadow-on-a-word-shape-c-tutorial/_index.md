---
category: general
date: 2026-03-30
description: 學習如何使用 C# 為 Word 形狀設定陰影。本指南亦示範如何加入形狀陰影、調整形狀透明度，以及加入矩形陰影。
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: zh-hant
og_description: 如何在 C# 中為 Word 形狀設定陰影？請跟隨此一步一步的指南，為形狀添加陰影、調整形狀透明度，並新增矩形陰影。
og_title: 如何在 Word 形狀上設定陰影 – C# 教學
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: 如何在 Word 形狀上設定陰影 – C# 教學
url: /zh-hant/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 形狀上設定陰影 – C# 教學

有沒有想過 **如何在 Word 文件中的形狀上設定陰影**，而不必在介面上手動操作？你並不是唯一有此需求的人。在許多報告或行銷簡報中，細緻的投影會讓矩形更突出，而以程式方式完成則能節省大量時間。

本指南將逐步說明一個完整、可直接執行的範例，不僅示範 **如何設定陰影**，還涵蓋 **新增形狀陰影**、**調整形狀透明度**，甚至 **新增矩形陰影**，適用於經典的說明框。完成後，你將得到一個外觀精緻的 Word 檔 (`output.docx`)，並了解每個屬性的意義。

## 前置條件

- .NET 6+（或 .NET Framework 4.7.2）搭配 C# 編譯器  
- Aspose.Words for .NET NuGet 套件 (`Install-Package Aspose.Words`)  
- 具備 C# 與 Word 物件模型的基本概念  

不需要其他額外函式庫——所有功能皆內建於 Aspose.Words。

---

## 如何在 C# 中為 Word 形狀設定陰影

以下為完整的原始程式碼。將其儲存為 `Program.cs`，然後在 IDE 或使用 `dotnet run` 執行。程式會載入既有的 `.docx`，找到第一個形狀（預設為矩形），開啟陰影，微調幾個視覺參數，最後儲存結果。

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **你會看到** – 矩形現在帶有一個 30% 透明的黑色投影，向右下各偏移 5 點，且具有柔和的模糊效果。請在 Word 中開啟 `output.docx` 以驗證。

## 調整形狀透明度 – 為何重要

透明度不只是美觀的調整項目；它會影響可讀性。0.0 代表陰影完全不透明，1.0 則會完全隱藏陰影。在上面的程式碼片段中，我們使用 `0.3` 以取得在淺色與深色背景皆適用的細緻效果。歡迎自行嘗試：

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

請記得，**調整形狀透明度** 也可以套用在形狀的填色上，若你需要半透明的矩形本身。

## 為不同物件新增形狀陰影

我們的程式碼是針對 `Shape` 物件，但相同的 `ShadowFormat` 屬性同樣適用於 **Image**、**Chart**，甚至 **TextBox** 物件。以下提供一個可直接複製貼上的快速範本：

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

因此，無論是為商標或裝飾圖示 **新增形狀陰影**，做法皆相同。

## 如何為任意形狀新增陰影 – 邊緣情況

1. **沒有邊界框的形狀** – 某些 Word 形狀（例如自由手繪的塗鴉）不支援陰影。嘗試設定 `ShadowFormat.Visible` 會悄悄失敗。若需保險起見，可檢查 `shape.IsShadowSupported`。  
2. **較舊的 Word 版本** – 陰影屬性對應 Word 2007 以上的功能。若必須相容 Word 2003，開啟檔案時會忽略陰影設定。  
3. **多重陰影** – Aspose.Words 目前每個形狀僅支援單一陰影。若需要雙層效果，可複製形狀、偏移位置，並套用不同的陰影設定。

## 新增矩形陰影 – 真實案例

假設你正在產生季報，且每個章節標題都是彩色矩形。加入 **新增矩形陰影** 會讓頁面呈現「卡片」般的外觀。步驟與基礎範例相同，只要確認目標形狀確實為矩形 (`shape.ShapeType == ShapeType.Rectangle`)。若需要從頭建立矩形，請參考下方程式碼片段：

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

執行加入此段程式的完整範例，即可得到已套用 **新增矩形陰影** 效果的全新矩形。

---

![Word shape with shadow](placeholder-image.png){alt="如何在 Word 中為形狀設定陰影"}

*圖示：套用陰影設定後的矩形。*

## 快速回顧（要點速查表）

- **載入** 文件：`new Document(path)`。  
- **定位** 形狀：`doc.GetChild(NodeType.Shape, index, true)`。  
- **啟用** 陰影：`shape.ShadowFormat.Visible = true;`。  
- **設定顏色**，使用任意 `System.Drawing.Color`。  
- **調整透明度**（`0.0–1.0`）以控制不透明度。  
- **OffsetX / OffsetY** 以點為單位水平/垂直移動陰影。  
- **BlurRadius** 使邊緣變柔和——數值越高陰影越模糊。  
- **儲存** 檔案並在 Word 中開啟以檢視結果。

## 接下來可以嘗試什麼？

- **動態顏色** – 從佈景主題或使用者輸入取得陰影顏色。  
- **條件式陰影** – 僅在形狀寬度超過特定門檻時套用陰影。  
- **批次處理** – 迭代文件中所有形狀，並自動 **新增形狀陰影**。

如果你已跟著操作，你現在已掌握 **如何設定陰影**、**調整形狀透明度**，以及 **新增矩形陰影**，讓文件更具專業感。盡情實驗、嘗試不同做法，然後修正——程式碼是最好的老師。

---

*祝開發愉快！如果本教學對你有幫助，歡迎留言或分享你的陰影技巧。彼此交流越多，我們的 Word 文件就會變得越漂亮。*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}