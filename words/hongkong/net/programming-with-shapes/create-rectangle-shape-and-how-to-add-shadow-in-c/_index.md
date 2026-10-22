---
category: general
date: 2026-04-04
description: 使用 Aspose.Words 在 C# 中建立矩形形狀，並學習如何加入陰影、對陰影套用模糊以及使陰影透明——一步一步的教學指南。
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: zh-hant
og_description: 使用 Aspose.Words 在 C# 中建立矩形形狀。學習如何添加陰影、對陰影套用模糊以及使陰影透明的簡明教學。
og_title: 在 C# 中建立矩形形狀以及如何加入陰影
tags:
- Aspose.Words
- C#
- Document Automation
title: 在 C# 中建立矩形形狀及加入陰影
url: /zh-hant/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立矩形形狀並在 C# 中加入陰影

是否曾需要在 Word 文件中 **建立矩形形狀**，卻不確定如何為它加上細緻的投影陰影？你並不孤單。在許多報告或品牌設計情境中，一個帶有柔和半透明陰影的簡單矩形即可讓版面看起來更精緻，且不需花費太多工夫。

在本教學中，我們將示範如何使用 Aspose.Words **建立文件**，接著說明 **如何加入陰影**、**對陰影套用模糊**，甚至 **讓陰影透明**。完成後，你將擁有一段可直接執行的 C# 程式碼，能產生帶有精緻陰影矩形的 *.docx* 檔案——只需幾分鐘即可完成。

## 需要的環境

- .NET 6 或更新版本（API 亦支援 .NET Framework 4.6+）
- Aspose.Words for .NET（此範例可使用免費試用版）
- 程式碼編輯器 – Visual Studio、VS Code、Rider，或任何你慣用的工具
- 基本的 C# 知識 – 不需要高階技巧，只要能執行主控台應用程式即可

如果你已具備上述條件，我們即可直接進入解決方案。

## 步驟 1 – 如何建立文件並初始化畫布

首先，你需要一個空的 `Document` 物件。可以把它想像成一張空白紙張，之後會由 Aspose.Words 轉換成 Word 檔案。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

為什麼要直接實例化 `Document` 而不是載入範本？從頭開始可確保沒有隱藏的樣式或段落會干擾我們的矩形，同時也能讓檔案大小保持極小——在迴圈大量產生文件時這是一個好習慣。

## 步驟 2 – 建立矩形形狀（我們主要關鍵字的核心）

現在我們真的 **建立矩形形狀**。`Shape` 類別相當彈性，你只需要指定類型（Rectangle）、尺寸，以及它與周圍文字的環繞方式。

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

請留意使用了物件初始化語法——簡潔且降低日後遺漏屬性設定的機會。矩形會放在第一個段落內，我們會在下一步加入該段落。

## 步驟 3 – 如何加入陰影並自訂外觀

加入陰影不只是一行程式碼，你需要調整多個屬性。這正是次要關鍵字 **對陰影套用模糊** 與 **讓陰影透明** 發揮作用的地方。

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

關於數值的說明：`BlurRadius` 設為 5 可產生柔和的羽化效果；若想要更柔軟可提升至 10，若想要較銳利則降至 2。`Transparency` 的取值介於 0（不透明）到 1（完全透明）之間，請依品牌的對比需求調整。

### 小技巧

如果需要彩色陰影（例如企業藍），只要將 `Color.DarkGray` 改成 `Color.FromArgb(80, 0, 120, 215)` 即可。第一個參數是 alpha 通道——保持較低的值可讓陰影更為細緻。

## 步驟 4 – 將形狀插入文件

當矩形及其陰影已準備好後，我們將它插入文件的第一個段落。此步驟可確保形狀出現在檔案最上方。

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

為什麼使用第一個段落？這是個安全的預設，即使文件完全空白也能正常運作。如果你有特定位置（例如標題之後），只要定位到該節點並在那裡插入形狀即可。

## 步驟 5 – 儲存檔案並驗證結果

最後，我們將文件寫入磁碟。你可以自行選擇任何路徑，只要確保該資料夾已存在即可。

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

當你在 Microsoft Word 中開啟 *ShadowRectangle.docx* 時，應該會看到一個 200 × 100 點的矩形，帶有深灰、略為模糊、透明度 30% 的陰影，且陰影向右下各偏移三點。此效果雖然細膩，卻能為原本平面的版面增添深度。

![在 Aspose.Words 中建立帶陰影的矩形形狀](https://example.com/placeholder-image.png "在 Aspose.Words 中建立帶陰影的矩形形狀")

*圖片替代文字:* **在 Aspose.Words 中建立帶陰影的矩形形狀** – 圖片顯示最終文件中帶有陰影的矩形。

## 常見變化與邊緣情況

### 動態變更陰影顏色

如果你的應用程式支援主題，你可以從設定檔中取得陰影顏色：

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### 讓形狀非行內顯示

有時你希望矩形浮在文字之上。將 `WrapType` 改為 `WrapType.Square`，並將 `RelativeHorizontalPosition` 設為 `RelativeHorizontalPosition.Margin`，即可獲得更高的控制度。

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### 處理多頁情況

如果需要在每一頁都放置矩形，可遍歷 `doc.Sections`，並將複製的形狀附加到每個節的第一個段落。別忘了呼叫 `rect.Clone(true)` 以同時複製陰影設定。

## 重點回顧 – 我們完成了什麼

- **使用 Aspose.Words 建立矩形形狀**
- **如何加入陰影**（包含顏色、偏移、模糊與透明度）
- 示範 **對陰影套用模糊** 與 **讓陰影透明**
- 儲存可立即開啟的 Word 檔案

所有這些僅透過少量程式碼即可完成，證明即使是精緻的視覺調整，也不一定需要大型圖形函式庫。

## 接下來可以做什麼？

- 嘗試其他 `ShapeType`（如 Ellipse、Cloud 等），觀察陰影的表現。
- 將矩形與文字方塊結合，建立帶標籤的說明框。
- 深入了解 **如何建立文件** 模板，事先放置形狀佔位符，之後以程式方式填入內容。

隨意調整模糊半徑、顏色或透明度，直到陰影符合你的設計語言。API 十分寬容，重新執行主控台應用程式即可即時看到變化。

祝程式開發順利，願你的文件永遠多一層深度感！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}