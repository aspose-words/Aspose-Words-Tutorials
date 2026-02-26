---
category: general
date: 2026-02-26
description: 在 Word 中使用 Aspose.Words 建立矩形形狀，並學習如何將形狀加入 Word、為形狀套用陰影，以及在幾分鐘內設定形狀透明度。
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: zh-hant
og_description: 在 Word 中使用 Aspose.Words 建立矩形形狀。學習如何將形狀加入 Word、為形狀套用陰影，以及快速設定形狀透明度。
og_title: 在 Word 中建立矩形形狀 – 完整 Aspose.Words 指南
tags:
- Aspose.Words
- C#
- Word Automation
title: 在 Word 中建立矩形形狀 – 完整 Aspose.Words 指南
url: /zh-hant/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

any missed items: The image alt and title changed. The table translation done.

Make sure to keep code block placeholders unchanged.

Now craft final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中建立矩形形狀 – 完整 Aspose.Words 指南

是否曾需要在 Word 文件中 **create rectangle shape**（建立矩形形狀），卻不知從何開始？您並不孤單——許多開發人員在自動化報告或發票時都會遇到這個問題。在本教學中，我們將逐步示範一個完整、可直接執行的範例，說明如何 **add shape to Word**（將形狀加入 Word），套用細緻的陰影，並控制形狀的透明度，全部使用 Aspose.Words for .NET。

完成本指南後，您將得到一個包含乾淨矩形與精緻陰影的 `.docx` 檔案——非常適合用於品牌標示、說明框，或僅僅讓您的文件看起來更專業。無需外部工具，只需幾行 C# 程式碼。

## 您需要的條件

- **Aspose.Words for .NET**（截至 2026 年初的最新版本）。您可以從 NuGet 取得（`Install-Package Aspose.Words`）。
- .NET 開發環境（Visual Studio、Rider，或安裝 C# 擴充功能的 VS Code）。
- 具備基本的 C# 語法知識——不需要特別技巧，只要會使用一般的 `using` 陳述式與建立物件即可。

如果您已具備上述條件，太好了——讓我們開始吧。

## 建立矩形形狀 – 核心步驟

以下是完整的原始程式碼。將它複製貼上到新的主控台專案，按 **F5**，您就會在指定的資料夾中看到 `ShadowDemo.docx`。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### 為什麼這樣可行

- **`Document`** 是入口點；它代表整個 Word 檔案。
- **`Shape`** 搭配 `ShapeType.Rectangle` 告訴 Aspose 我們想要一個矩形繪圖物件。
- 設定 **`Width`** 與 **`Height`** 為形狀指定確定的大小；否則會預設為極小的佔位符。
- **`Shadow`** 物件讓我們能微調每個視覺屬性：模糊、距離、方向、顏色、透明度與擴散。這正是 *apply shadow to shape* 的核心。
- 最後，**`AppendChild`** 將形狀插入文件的第一段落，這是 *add shape to Word* 最簡單的方式，無需處理表格或頁首。

當您開啟 `ShadowDemo.docx` 時，會看到一個灰色矩形舒適地位於文件中，其陰影向右下方傾斜 45°。陰影不是實心方塊；模糊半徑使邊緣變得柔和，透明度則讓它看起來像自然的投影，而非生硬的覆蓋。

![建立矩形形狀範例](image.png "在 Word 中使用 Aspose.Words 建立帶陰影的矩形形狀")

（上圖顯示程式碼片段的最終結果。）

## 將形狀加入 Word 文件 – 放置選項

此範例使用 **第一段落**，因為它是最快看到結果的方式。在實務情境中，您可能想要：

- 將形狀插入特定的 **section** 或 **header/footer**。
- 將其放置於 **table cell** 內，以配合表格資料的對齊。
- 使用 **text wrapping** 選項（例如 `WrapType.Square`）將其環繞，讓周圍文字圍繞矩形流動。

以下是一個快速變體，將形狀放入具有自訂樣式的新段落：

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*小技巧：* 總是在設定完屬性 **之後** 再加入形狀；否則可能需要呼叫 `UpdateLayout` 以重新整理視覺外觀。

## 套用陰影於形狀 – 微調外觀

陰影可以顯著改變文件的美感。`Shadow` 類別提供多個屬性：

| 屬性          | 控制項目                                           | 典型值          |
|---------------|----------------------------------------------------|----------------|
| `BlurRadius`  | 陰影邊緣的柔和程度                                 | 2.0 – 10.0      |
| `Distance`    | 陰影相對於形狀的偏移距離                           | 1.0 – 8.0       |
| `Direction`   | 角度（度），0 = 左，90 = 上                         | 0 – 360         |
| `Color`       | 陰影顏色（任何 `System.Drawing.Color`）            | Gray, Black, Custom |
| `Transparency`| 不透明度（0 = 完全不透明，1 = 完全透明）           | 0.0 – 0.5       |
| `Spread`      | 在套用模糊前陰影的擴展程度                         | 0.0 – 1.0       |

如果您想要 **細緻、專業的外觀**，將 `BlurRadius` 保持在約 4‑6，`Transparency` 接近 0.2，就像上面的程式碼。若要 **營造戲劇化效果**，將 `Distance` 提升至 6，將 `Direction` 設為 135°，並將 `Transparency` 降至 0.05。

## 設定形狀透明度與陰影擴散

透明度不僅適用於陰影；您也可以讓矩形本身部分透明：

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

將半透明填色與柔和陰影結合，常能營造現代 UI 感覺——非常適合儀表板或報告中的設計模型。

### 需留意的邊緣情況

1. **舊版 Word（2007 之前）** 不支援某些陰影屬性。如果目標是 `.doc` 檔案，請考慮簡化陰影（例如將 `BlurRadius` 設為 0）。
2. **高 DPI 顯示器** 可能會使陰影的呈現略有不同。如視覺精確度很重要，請在目標環境中測試。
3. **形狀重疊**——Aspose 會依加入的順序渲染陰影。請從後至前插入形狀，以避免不必要的遮蔽。

## 儲存並驗證結果

`Document.Save` 方法會自動根據檔案副檔名偵測輸出格式。對於 **`.docx`** 檔案，會使用 Open XML 格式，這是大多數現代 Word 處理器所支援的。如果您需要相同視覺樣式的 **PDF** 版本，只要更改副檔名即可：

```csharp
document.Save("ShadowDemo.pdf");
```

開啟產生的 `ShadowDemo.docx`（或 `ShadowDemo.pdf`）應會看到乾淨的 **帶陰影的矩形**，證明您已成功使用 Aspose.Words *create rectangle shape* 並 *apply shadow to shape*。

## 常見問題

**Q: 我可以使用其他形狀，例如橢圓形嗎？**  
A: 當然可以。將 `ShapeType.Rectangle` 換成 `ShapeType.Ellipse`（或任何其他 `ShapeType` 列舉）。陰影屬性保持不變。

**Q: 如果我需要讓矩形可點擊呢？**  
A: 您可以為形狀指派超連結：

```csharp
rectangleShape.Href = "https://example.com";
```

**Q: 這在 .NET 6 以上版本可用嗎？**  
A: 可以。Aspose.Words 23.11 及之後的版本完整支援 .NET 6、.NET 7 與 .NET 8。只需引用相應的 NuGet 套件即可。

**Q: 我要如何將陰影顏色改成符合品牌的色彩？**  
A: 使用任意您想要的 `System.Drawing.Color`：

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## 結語

我們已說明在 Word 文件中 **create rectangle shape**、**add shape to Word**、**apply shadow to shape** 以及 **set shape transparency** 所需的全部內容。完整、可執行的程式碼位於本頁上方，說明應能讓您有足夠信心在任何專案中調整大小、顏色與陰影參數。

準備好進一步了嗎？試著進行以下實驗：

- 將多個形狀層疊，以產生徽章效果。
- 根據文件內容動態調整大小（例如，從表格欄位計算寬度）。
- 將文件匯出為 PDF 或 HTML，同時保留陰影。

如果遇到任何問題，歡迎留言，或分享您對「帶陰影的矩形」主題的自訂變化。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}