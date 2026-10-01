---
category: general
date: 2026-03-04
description: Learn how to create rectangle shape, add shadow to shape and apply shadow
  effect in a Word document, then save Word document automatically.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: zh-hant
og_description: Create rectangle shape, add shadow to shape and apply shadow effect
  in a Word document using C#. Follow this guide to save Word document effortlessly.
og_title: 在 Word 中建立矩形形狀 – 完整 C# 教學
tags:
- C#
- Aspose.Words
- Document Automation
title: 使用 C# 在 Word 中建立矩形形狀 – 步驟指南
url: /zh-hant/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 C# 建立矩形形狀 – 完整程式教學

有沒有曾經需要在 Word 檔案中 **create rectangle shape**，卻不知道從哪裡開始？你並不孤單——許多開發者在第一次接觸程式化文件產生時都會卡在這裡。好消息是，只要幾行 C# 程式碼，就能插入矩形、**add shadow to shape**，以及 **apply shadow effect**，而不必自行開啟 Word。本指南將一步步說明完整流程，從全新 **create blank document** 到將最終的 **save word document** 儲存至磁碟。

我們會涵蓋所有必備項目：所需的 NuGet 套件、精確的 API、每個屬性的意義，以及避免常見陷阱的幾個小技巧。完成後，你將擁有一個可直接在任何 .NET 專案中執行的完整範例。

## 前置條件

- .NET 6.0 或更新版本（此程式碼同樣支援 .NET Framework 4.7+）
- Visual Studio 2022 或任何你慣用的 IDE
- 透過 NuGet 安裝 **Aspose.Words for .NET** (`Install-Package Aspose.Words`)
- 基本的 C# 語法概念

不需要額外的 Word interop 函式庫——Aspose.Words 會在記憶體中處理所有工作。

## 步驟 1 – 建立空白文件

首先，我們 **create blank document**。把它想成之後 **create rectangle shape** 的空白畫布。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **為什麼這很重要：** 從乾淨的 `Document` 物件開始，可確保沒有隱藏的樣式或節段會在之後影響形狀的定位。

## 步驟 2 – 在文件中插入矩形形狀

現在正式 **create rectangle shape**。我們會設定尺寸、位置，並告訴 Word 不要讓文字環繞它。

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **小技巧：** 若需要將矩形放入表格儲存格內，將 `WrapType` 改為 `WrapType.Inline`。對於大多數報表而言，`None` 會讓形狀浮在文字之上。

## 步驟 3 – 為形狀加入陰影並設定外觀

這裡就是魔法發生的地方：我們 **add shadow to shape** 並 **apply shadow effect**。陰影能讓矩形在頁面上更突出，尤其是列印時。

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **為什麼要這樣設定？**  
> - **BlurRadius** 控制邊緣的模糊程度；約 `5` 的數值可呈現細緻、專業的外觀。  
> - **Transparency** 讓底下的文字仍保持可讀。  
> - **OffsetX/Y** 將陰影向外移動，營造深度感。  
> - 使用 **blue** 色調僅為示範——任何 `System.Drawing.Color` 都可使用。

## 步驟 4 – 將設定好的形狀加入文件主體

在矩形完成樣式設定後，我們 **add rectangle shape** 到文件的第一個節段。此步驟實際將形狀寫入檔案。

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **邊緣情況：** 若文件已包含多個節段，可能需要指定特定節段（例如 `doc.Sections[2]`）。上述程式碼適用於單節段文件，這在快速報表中相當常見。

## 步驟 5 – 儲存 Word 文件

最後，我們 **save word document** 到磁碟。檔案將包含帶陰影的矩形，隨時可在 Microsoft Word 中開啟。

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **小提醒：** 若需明確指定格式，可使用 `doc.Save(outputPath, SaveFormat.Docx)`。`Save` 方法會自動偵測副檔名，但在程式動態產生路徑時，明確指定可避免混淆。

## 完整可執行範例

以下是可直接貼到 Console 應用程式的完整程式碼，已包含所有 `using` 陳述式與 `Main` 方法，直接執行即可。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### 預期結果

當你在 Microsoft Word 中開啟 *shadowed_rectangle.docx* 時，會看到一個藍色邊框的矩形漂浮在第一頁上方，並帶有向右下方偏移 8 pt 的柔和藍色陰影。因為我們將 `WrapType` 設為 `None`，所以不會有額外文字環繞。

## 常見問題與變化

| 問題 | 解答 |
|----------|--------|
| **可以把形狀改成橢圓嗎？** | 可以——將 `ShapeType.Rectangle` 改為 `ShapeType.Ellipse`。所有陰影屬性保持不變。 |
| **如果需要多個形狀該怎麼辦？** | 只要對每個新的 `Shape` 例項重複步驟 2‑4，並調整 `OffsetX/Y` 或 `Left/Top` 以避免重疊。 |
| **有沒有辦法讓陰影顏色與形狀填色相同？** | 當然可以。先設定 `rectangle.FillColor`，再將 `rectangle.ShadowFormat.Color = rectangle.FillColor;`。 |
| **如何把形狀插入表格儲存格？** | 在取得目標 `Cell` 物件後，使用 `cell.FirstParagraph.AppendChild(rectangle);`。 |
| **這在 .NET Core 上能跑嗎？** | 能——Aspose.Words 是跨平台的。只要引用對應 .NET Core/5/6 的 NuGet 版本即可。 |

## 常見陷阱與進階技巧

- **陷阱：** 忘記設定 `ShadowFormat.Visible = true`。陰影屬性會被靜默忽略。  
  **解決方法：** 在調整其他陰影參數前，務必先啟用可見性。

- **陷阱：** 使用過大的 `BlurRadius`（例如 20）會讓陰影看起來模糊且不專業。  
  **解決方法：** 大多數商業文件建議使用 `3` 到 `8` 之間的數值。

- **進階技巧：** 若希望形狀之後仍能被使用者選取（例如讓最終使用者編輯），請避免使用 `WrapType.Inline`。浮動形狀（`WrapType.None`）較易於程式碼中移動。

- **進階技巧：** 在迴圈中大量產生文件時，可重複使用單一 `Document` 實例，並以 `doc.Clone(true)` 為每次迭代建立副本，以提升效能。

## 相關主題推薦

- **在矩形形狀內加入文字** – 了解如何使用 `Shape.TextPath` 來放置標籤。  
- **建立複雜圖表** – 結合多個形狀、連接線與群組功能。  
- **匯出為 PDF** – 只需一行 `doc.Save("output.pdf")` 即可將同一文件轉為 PDF。  
- **套用不同填充樣式** – 漸層、紋理，甚至在形狀內放入圖片。

## 結論

我們已在 Word 檔案中使用 C# **create rectangle shape**、**add shadow to shape**，並 **apply shadow effect**。透過這五個簡潔步驟，你現在擁有一套可重複使用的文件自動化模式，且知道如何可靠地 **save word document**。隨意調整尺寸、顏色，或將矩形換成其他幾何形狀——Aspose.Words 讓一切變得簡單。

如果本教學對你有幫助，請在 GitHub 上給予星標，或在留言區分享你的變化版本。祝程式開發愉快，願你的文件永遠如同這個帶陰影的矩形般精緻！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}