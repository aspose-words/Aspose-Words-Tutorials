---
category: general
date: 2026-02-21
description: 在 C# 中為形狀加入陰影，並學習如何自訂陰影、套用陰影效果以及設定陰影不透明度，提供完整可執行的範例。
draft: false
keywords:
- add shadow to shape
- how to customize shadow
- apply shadow effect
- how to add shadow
- set shadow opacity
language: zh-hant
og_description: 使用本指南在 C# 中為形狀添加陰影。學習如何自訂陰影、套用陰影效果，以及僅用幾行程式碼設定陰影不透明度。
og_title: 為形狀加上陰影 – 完整 C# 教學
tags:
- C#
- Aspose.Words
- Graphics
- Shadow Effect
title: 為形狀添加陰影 – C# 開發者逐步指南
url: /zh-hant/net/programming-with-shapes/add-shadow-to-shape-step-by-step-guide-for-c-developers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 為形狀添加陰影 – 完整 C# 教程

是否曾需要在 Word 文件中 **為形狀添加陰影**，卻不知從何下手？你並非唯一遇到此問題的開發者——許多人在美化報告或行銷傳單時都會卡關。好消息是，只要幾個步驟，就能把平面的矩形變成具有立體感、從頁面中跳脫出來的精緻元素。

本指南將示範一個 **完整、可執行的範例**，教你如何自訂陰影、套用陰影效果，甚至為任意形狀設定陰影不透明度。完成後，你將擁有可直接嵌入任何 Aspose.Words 專案的可重用程式碼片段，無需額外參考。

## 前置條件

在開始之前，請確保你已具備：

* **.NET 6.0**（或更新版本）— 此程式碼亦相容 .NET Framework 4.6 以上。
* **Aspose.Words for .NET** NuGet 套件 — 建議使用 23.9 或更新版本。
* 基本的 C# 與物件導向程式設計概念。

若尚未安裝 NuGet 套件，執行：

```bash
dotnet add package Aspose.Words
```

基礎已備妥，現在就動手實作吧。

## 步驟 1 – 載入或建立文件並取得第一個形狀

首先需要一個實際包含形狀的 `Document` 物件。為了示範，我們會建立新文件、插入一個簡單的矩形，然後取得它。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank document
        Document doc = new Document();

        // 2️⃣ Add a new shape (a rectangle) to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle);
        rect.Width = 150;
        rect.Height = 100;
        rect.WrapType = WrapType.Inline;
        rect.StrokeColor = Color.DarkBlue;
        rect.FillColor = Color.LightBlue;
        rect.StrokeWeight = 2.0;

        // Insert the shape into the document body
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Retrieve the shape we just added (demonstrates add shadow to shape)
        Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (firstShape == null)
        {
            Console.WriteLine("No shape found – aborting.");
            return;
        }

        // The remaining steps modify the shadow of firstShape
```

**為什麼這樣做：**  
透過 `GetChild` 取得形狀，可模擬實務上形狀已存在（例如從範本載入）的情況，同時確保後續的陰影程式碼作用於有效物件，避免 NullReference 例外。

> **小技巧：** 若要處理多個形狀，可使用 `GetChild(NodeType.Shape, index, true)` 或遍歷 `doc.GetChildNodes(NodeType.Shape, true)`。

## 步驟 2 – 開啟陰影效果

形狀的陰影預設是關閉的。先將其啟用，才能進行後續的自訂設定。

```csharp
        // 4️⃣ Enable the shadow
        firstShape.Shadow.Enabled = true;
```

**為什麼重要：**  
若未將 `Enabled = true`，之後的屬性變更（顏色、模糊、偏移）都會被忽略。這就像先開燈才能調整燈泡亮度一樣。

## 步驟 3 – 選擇陰影顏色（以及為何黑色是良好起點）

顏色會直接影響深度感。黑色（或極深的灰）是最常見的選擇，因為它在任何背景下都能表現良好。

```csharp
        // 5️⃣ Set the shadow color – black gives a classic look
        firstShape.Shadow.Color = Color.Black;
```

**備選方案：**  
若文件背景較暗，可改用較亮的色調：

```csharp
        // firstShape.Shadow.Color = Color.FromArgb(150, 150, 150); // light gray
```

## 步驟 4 – 設定陰影不透明度

不透明度的取值介於 `0.0`（完全透明）與 `1.0`（完全不透明）之間。對大多數 UI 設計而言，40 % 透明的陰影較為自然。

```csharp
        // 6️⃣ Make the shadow 40 % transparent
        firstShape.Shadow.Transparency = 0.4; // 0 = opaque, 1 = invisible
```

**自訂方式：**  
- **更柔和：** `0.2`（20 % 透明）  
- **非常淡：** `0.7`（70 % 透明）

## 步驟 5 – 定義模糊與邊緣柔和度

模糊值決定陰影邊緣的柔軟程度。`4.0` 的設定對中等大小的形狀相當適合。

```csharp
        // 7️⃣ Soften the edges with a blur radius
        firstShape.Shadow.Blur = 4.0;
```

**特殊情況：**  
若將 `Blur` 設為 `0`，陰影會變成硬邊的剪影，感覺較為刺眼。相反地，超過 `10` 的數值則會讓陰影看起來像發光效果。

## 步驟 6 – 設定陰影相對於形狀的位置

`OffsetX` 與 `OffsetY` 分別控制陰影在水平方向與垂直方向的位移。正值會使陰影向右下方移動。

```csharp
        // 8️⃣ Position the shadow 5 points right and 5 points down
        firstShape.Shadow.OffsetX = 5;
        firstShape.Shadow.OffsetY = 5;
```

**實驗：**  
- **投影陰影：** `OffsetX = 0`, `OffsetY = 10`  
- **提升效果：** `OffsetX = -5`, `OffsetY = -5`

## 步驟 7 – 儲存並驗證結果

最後，將文件寫入磁碟，使用 Microsoft Word（或其他相容檢視器）開啟，觀察陰影效果。

```csharp
        // 9️⃣ Save the document
        string outPath = "ShadowedShape.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}. Open it to see the shadow.");
    }
}
```

開啟 **ShadowedShape.docx** 後，你應該會看到一個淡藍色矩形，旁邊有一個柔和、半透明的黑色陰影，偏移五點。如果陰影未顯示，請再次確認 `firstShape.Shadow.Enabled` 為 `true`，且使用的是最新版的 Aspose.Words。

### 完整原始碼（可直接複製貼上）

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        Document doc = new Document();
        Shape rect = new Shape(doc, ShapeType.Rectangle);
        rect.Width = 150;
        rect.Height = 100;
        rect.WrapType = WrapType.Inline;
        rect.StrokeColor = Color.DarkBlue;
        rect.FillColor = Color.LightBlue;
        rect.StrokeWeight = 2.0;
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (firstShape == null)
        {
            Console.WriteLine("No shape found – aborting.");
            return;
        }

        // Enable shadow
        firstShape.Shadow.Enabled = true;

        // Choose shadow color
        firstShape.Shadow.Color = Color.Black;

        // Set opacity (40 % transparent)
        firstShape.Shadow.Transparency = 0.4;

        // Soften edges
        firstShape.Shadow.Blur = 4.0;

        // Position shadow
        firstShape.Shadow.OffsetX = 5;
        firstShape.Shadow.OffsetY = 5;

        // Save document
        string outPath = "ShadowedShape.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}. Open it to see the shadow.");
    }
}
```

## 常見問題與特殊情況

| 問題 | 解答 |
|----------|--------|
| **如果形狀是圖片而非矩形，該怎麼辦？** | 陰影屬性相同，只需確保形狀的 `ShapeType` 為 `Picture`。 |
| **我可以為陰影加入動畫嗎？** | Aspose.Words 不支援動畫，但可產生多頁文件，分別設定不同偏移，再使用 PowerPoint 進行動畫。 |
| **陰影在 PDF 匯出時會保留嗎？** | 會。將文件另存為 PDF（`doc.Save("out.pdf")`）時，Aspose.Words 會保留陰影效果。 |
| **之後要移除陰影該怎麼做？** | 設定 `firstShape.Shadow.Enabled = false;` 或直接將 `firstShape.Shadow = null`。 |
| **模糊值有上限嗎？** | 實務上，超過 `15` 會讓陰影看起來像光暈，且可能增加檔案大小。 |

## 下一步 – 持續前進

既然已掌握 **如何添加陰影** 以及 **設定陰影不透明度**，可以進一步探索：

* 使用 `Shadow.Distance` 讓偏移更為明顯，進一步自訂陰影。
* 為文字框或 WordArt 套用陰影，提升文件設計層次。
* 結合多重陰影（例如內陰影 + 外陰影）打造分層效果。
* 匯出為 HTML，觀察 CSS `box-shadow` 如何映射相同設定。

若你在開發報表產生器，建議在標題、圖表或說明框上加入陰影，引導讀者視線。多嘗試不同顏色與透明度——或許可以為企業主題加入淡藍色陰影，營造專業氛圍。

---

### 簡要摘要

我們示範了一個 **完整、獨立的範例**，說明如何使用 Aspose.Words 在 C# 中 **為形狀添加陰影**、**自訂陰影**、**套用陰影效果**，以及 **設定陰影不透明度**。程式碼已可直接執行，說明同時涵蓋 *做什麼* 與 *為什麼*，讓你在任何 Word 自動化專案中都有堅實的樣式基礎。

祝開發順利，讓你的文件總是散發出立體的精緻感！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}