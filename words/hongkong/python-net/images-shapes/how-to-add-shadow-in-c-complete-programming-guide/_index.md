---
category: general
date: 2025-12-25
description: 如何在 C# 中加入陰影，附簡單程式範例。了解如何設定陰影距離、客製化顏色，並為您的圖形創造深度。
draft: false
keywords:
- how to add shadow
- how to set shadow distance
language: zh-hant
og_description: 一步一步說明如何在 C# 中加入陰影。依照本指南設定陰影距離、顏色與模糊，打造專業外觀的形狀。
og_title: 如何在 C# 中加入陰影 – 完整程式設計指南
tags:
- C#
- graphics
- Aspose.Words
- shadows
title: 如何在 C# 中加入陰影 – 完整程式設計指南
url: /zh-hant/python/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中加入陰影 – 完整程式設計指南

在 C# 中加入陰影是讓圖形更具立體感的常見需求。本文將逐步說明如何為形狀設定陰影，包括設定陰影距離、調整模糊程度以及選擇合適的顏色。

如果你曾經盯著一個平面的矩形，心想「這個可以加點深度」，那麼你來對地方了。我們會從空白文件開始，加入形狀，最後完成一個看起來像是設計師精心擺放的陰影。沒有多餘的說明，只有可直接複製貼上的實作範例。

## 你將學會

- 以程式方式建立新文件並插入形狀。  
- 為形狀的陰影套用柔和的模糊。  
- **如何設定陰影距離**，讓陰影自然偏移。  
- 選擇在任何背景下都適用的陰影顏色。  
- 將結果儲存為 PDF（或其他任何你需要的格式）。  

### 前置條件

- .NET 6.0 或更新版本（程式碼同樣適用於 .NET Core 與 .NET Framework）。  
- Aspose.Words for .NET（免費試用版或正式授權版）。  
- 基本的 C# 語法概念。  

就這樣——不需要額外的函式庫，也不需要魔法。讓我們開始吧。

![範例：帶有柔和黑色陰影的形狀 – 如何加入陰影](https://example.com/placeholder-shadow.png "加入陰影範例")

## 第 1 步：設定專案並匯入命名空間

首先，建立一個新的 Console 應用程式（或任何 C# 專案），並加入 Aspose.Words NuGet 套件：

```bash
dotnet new console -n ShadowDemo
cd ShadowDemo
dotnet add package Aspose.Words
```

接著開啟 `Program.cs`，將必要的命名空間引用進來：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;
```

> **專業提示：** 若使用 Visual Studio，IDE 會在你輸入 `Document` 時自動建議 `using` 陳述式。

## 第 2 步：建立新文件並加入形狀

套件就緒後，我們可以實例化 `Document` 物件，並在第一頁放置一個簡單的矩形。

```csharp
// Step 2: Initialize the document
Document doc = new Document();

// Add a blank page (Aspose.Words creates one automatically)
Section section = doc.FirstSection;

// Insert a rectangle shape – this will be the object we give a shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    // Size the shape (width, height) in points (1 point = 1/72 inch)
    Width = 200,
    Height = 100,
    
    // Position the shape 100 points from the left and 150 from the top
    Left = 100,
    Top = 150,
    
    // Fill the shape with a light gray so the shadow stands out
    FillColor = System.Drawing.Color.LightGray
};

// Add the shape to the document's first page
section.Body.FirstParagraph.AppendChild(rectangle);
```

為什麼選擇矩形？它是一個中性的畫布，讓陰影效果不受其他因素干擾。你也可以把 `ShapeType.Rectangle` 改成 `Ellipse` 或 `Star`——陰影的邏輯保持不變。

## 第 3 步：如何加入陰影 – 套用模糊、距離與顏色

現在進入本教學的核心：**如何加入陰影** 到矩形。Aspose.Words 為每個形狀提供 `Shadow` 物件，讓你調整模糊、距離與顏色。

```csharp
// Step 3: Access the shape's shadow settings
Shadow shadow = rectangle.Shadow;

// 3a) Apply a soft blur – larger values make the shadow fuzzier
shadow.Blur = 5.0;          // 5 points blur gives a subtle, professional look

// 3b) Set the shadow's offset distance – this determines how far the shadow is displaced
shadow.Distance = 3.0;      // 3 points offset is enough to suggest depth without looking detached

// 3c) Choose a shadow color – black works on most backgrounds, but you can experiment
shadow.Color = Color.Black; // Solid black; you could use Color.FromArgb(128, 0, 0, 0) for semi‑transparent

// OPTIONAL: Rotate the shadow to match a light source direction (45 degrees works well)
shadow.Angle = 45.0;
```

注意註解 `// 3b) Set the shadow's offset distance`。這一行直接回答了 **如何設定陰影距離**。透過調整 `shadow.Distance`，即可控制形狀與陰影之間的視覺間距，模擬特定角度的光源。

### 為什麼使用這些數值？

- **Blur = 5.0** – 輕微的模糊避免硬朗的輪廓，同時仍保持可見。  
- **Distance = 3.0** – 讓陰影貼近形狀，看起來像是由形狀本身投射。  
- **Color = Black** – 在亮暗兩種背景下都能保證對比度。  

隨意調整這些數值；API 接受任意 `double` 型別的值。

## 第 4 步：儲存文件並驗證結果

陰影設定完成後，只要將檔案寫入磁碟即可。Aspose.Words 支援多種輸出格式，PDF 是最常見的分享方式。

```csharp
// Step 4: Save the document as a PDF (you could also use .docx, .png, etc.)
string outputPath = "ShadowedShape.pdf";
doc.Save(outputPath, SaveFormat.Pdf);

Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
```

開啟 `ShadowedShape.pdf`，你應該會看到一個帶有柔和黑色陰影、稍微向右下偏移的灰色矩形。若陰影過淡，可增加 `shadow.Blur` 或 `shadow.Distance` 後重新執行。

## 常見問題與特殊情況

### 如果需要透明的陰影該怎麼做？

使用帶有小於 255 的 Alpha 通道的 ARGB 顏色：

```csharp
shadow.Color = Color.FromArgb(80, 0, 0, 0); // 80/255 opacity = ~31% transparent
```

### 能否將相同的陰影套用到多個形狀？

當然可以。建立一個輔助方法：

```csharp
static void ApplyStandardShadow(Shape shape)
{
    shape.Shadow.Blur = 5.0;
    shape.Shadow.Distance = 3.0;
    shape.Shadow.Color = Color.Black;
}
```

對每個新增的形狀呼叫 `ApplyStandardShadow(rectangle);`。

### 這在較舊的 .NET Framework 版本上可用嗎？

可以。Aspose.Words 22.9 以上版本支援 .NET Framework 4.5 及以上。只要在專案檔中相應調整即可。

## 完整範例程式

以下是可直接貼入 `Program.cs` 的完整程式碼，安裝好 NuGet 套件後即可編譯執行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;

namespace ShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Initialize the document
            Document doc = new Document();
            Section section = doc.FirstSection;

            // Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 100,
                Top = 150,
                FillColor = System.Drawing.Color.LightGray
            };
            section.Body.FirstParagraph.AppendChild(rectangle);

            // Apply shadow – this is the core of "how to add shadow"
            Shadow shadow = rectangle.Shadow;
            shadow.Blur = 5.0;                // Soft blur
            shadow.Distance = 3.0;            // How to set shadow distance
            shadow.Color = Color.Black;       // Classic black shadow
            shadow.Angle = 45.0;              // Light source direction

            // Save as PDF
            string outputPath = "ShadowedShape.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
        }
    }
}
```

執行程式：

```bash
dotnet run
```

執行後會在專案資料夾產生 `ShadowedShape.pdf`，使用任意 PDF 閱讀器開啟，即可確認陰影效果如說明所示。

## 結論

我們從頭到尾說明了 **如何在 C# 中加入陰影**，並示範了 **如何設定陰影距離**、模糊與顏色。只需幾行程式碼，就能為圖形賦予專業的三維感，無需外部設計工具。

掌握基礎後，建議你自行嘗試以下變化：

- 將陰影顏色改為淡藍，營造更冷冽的氛圍。  
- 增加模糊程度，打造夢幻、散射的效果。  
- 將相同技巧套用於圖表、圖片或文字方塊。  

每一次變化都會加深對核心概念的理解，讓你在任何情境下都能自如調整陰影。

有其他問題嗎？歡迎留言，祝開發愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}