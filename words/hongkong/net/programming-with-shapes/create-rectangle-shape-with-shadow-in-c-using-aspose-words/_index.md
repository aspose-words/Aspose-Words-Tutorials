---
category: general
date: 2026-03-22
description: 在 C# 中建立矩形形狀，並使用 Aspose.Words 為形狀添加陰影。了解如何添加陰影、如何建立矩形以及如何設定陰影屬性。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: zh-hant
og_description: 使用 Aspose.Words 在 C# 中建立矩形形狀並為形狀添加陰影。逐步指南，涵蓋如何添加陰影、如何建立矩形以及如何設定陰影。
og_title: 在 C# 中建立帶陰影的矩形形狀 – 完整指南
tags:
- Aspose.Words
- C#
- Document Automation
title: 使用 Aspose.Words 在 C# 中建立帶陰影的矩形形狀
url: /zh-hant/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words 在 C# 中建立帶陰影的矩形形狀

是否曾需要在 Word 文件中 **建立矩形形狀**，卻不確定要如何為它加上細緻的投影？你並不孤單——許多開發者在首次接觸文件自動化時都會碰到這個問題。在本教學中，我們將一步步說明如何使用 Aspose.Words **為形狀加入陰影**，同時回答「**如何加入陰影**」、「**如何建立矩形**」以及「**如何設定陰影**」等問題。

我們會從一個全新的 `Document` 開始，繪製矩形、開啟陰影、調整模糊度、距離、角度與顏色，最後儲存檔案。完成後，你將得到一個可直接使用的 `.docx`，裡面顯示一個灰色矩形漂浮在頁面上方。沒有神祕，只是可以直接複製貼上到任何 .NET 專案的簡單程式碼。

## 前置條件

在開始之前，請確保你已具備：

* **Aspose.Words for .NET**（截至 2026 年 3 月的最新版本）。可透過 NuGet 使用 `Install-Package Aspose.Words` 取得。
* .NET 開發環境——Visual Studio、Rider，或是安裝 C# 擴充功能的 VS Code 都可以。
* 基本的 C# 知識——不需要高階技巧，只要能建立 console 或 WinForms 應用程式即可。

就這樣。沒有額外的函式庫，沒有隱藏步驟。準備好了嗎？讓我們開始吧。

## 步驟 1：初始化一個新的空白文件

要 **建立矩形形狀**，首先需要一個容器——`Document` 物件，代表 Word 檔案本身。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

`Document` 類別是 Aspose.Words 所有功能的入口。把它想像成一張白布，沒有它就無法加入任何形狀、表格或文字。

## 步驟 2：建立將承載陰影的矩形

現在我們要 **如何建立矩形**，只要實例化一個 `Shape`，型別設為 `Rectangle`。同時以點 (1 point ≈ 1/72 吋) 設定大小。

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

為什麼選擇 200 × 100 點？這個尺寸對示範來說剛好——足夠看清陰影，但又不會佔滿整頁。你可以自行調整這些數值以符合版面需求。

## 步驟 3：啟用陰影效果並設定外觀

以下是本教學的核心：**如何加入陰影** 以及 **如何設定陰影** 屬性。Aspose.Words 在每個形狀上提供 `Shadow` 物件，讓你開關效果並微調視覺參數。

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** 使邊緣變得柔和——數值越高，陰影看起來越擴散。
* **Distance** 將陰影向外推離矩形的距離。
* **Angle** 決定光源方向；45° 會產生自然的對角線陰影。
* **Color** 讓你選擇任意 `System.Drawing.Color`。灰色是安全的預設值，也可以使用 `Color.Black` 來加深，或 `Color.LightGray` 來減淡。

小技巧：若將 `Enabled = false`，其他所有陰影設定都會被忽略，務必確認此旗標已設為 `true`。

## 步驟 4：將形狀插入文件主體

矩形與陰影設定完成後，需要把它放入文件。最簡單的方式是將它附加到第一個章節的第一個段落。

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

如果文件已經有文字，你也可以定位到特定的 `Paragraph`，甚至是 `Table` 的儲存格，再插入形狀。`AppendChild` 方法相當彈性——適用於任何 `Node` 類型。

## 步驟 5：儲存文件並驗證結果

最後，我們把檔案寫入磁碟。請自行修改路徑為你想要的位置；若資料夾不存在，程式會拋出例外。

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

在 Microsoft Word（或 LibreOffice）開啟產生的 `ShadowedRectangle.docx`，你應該會看到一個灰色矩形，右下方帶有清晰的對角線陰影。若陰影過於淡薄，可增加 `BlurRadius` 或 `Distance` 後重新執行程式碼——實驗是學習的一部分。

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="建立帶陰影的矩形範例"}

### 預期輸出

* 單頁 Word 文件。
* 位於頁面左上角、尺寸為 200 × 100 點的灰色矩形。
* 以 45° 角度、偏移 8 像素、模糊 5 像素的細緻灰色陰影。

## 深入探討：如何為形狀加入陰影

你可能會想，「*我可以讓陰影動態變化或根據使用者輸入調整嗎？*」雖然 Aspose.Words 本身不支援動畫，但你可以在儲存前程式化調整陰影屬性，從而產生多個外觀不同的文件版本。例如，遍歷一組顏色：

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

這段小程式碼示範了 **如何動態設定陰影**——非常適合產生主題化報表。

## 建立矩形的其他形狀

如果需要圓角矩形，只要切換 `ShapeType`：

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

或是想要正方形，只要把 `Width` 設為與 `Height` 相同。相同的陰影屬性仍然適用，讓你在 **如何加入陰影** 時不必重新學習。

## 常見問題與除錯

| 症狀 | 可能原因 | 解決方式 |
|------|----------|----------|
| 陰影未顯示 | `Shadow.Enabled` 為 `false` | 設定 `rectangleShape.Shadow.Enabled = true;` |
| 陰影過於銳利 | `BlurRadius` 設為 0 | 將 `BlurRadius` 提高至至少 3 |
| 儲存時拋出 `FileNotFoundException` | 目標資料夾不存在 | 先建立資料夾或使用有效路徑 |
| 形狀不可見 | Width/Height 為 0 | 確認寬高皆大於 0 |

留意這些問題，可避免常見的「為什麼我的形狀不顯示？」情況。

## 重點回顧

* **在新 Word 文件中建立矩形形狀**，使用 Aspose.Words。  
* **為形狀加入陰影**，透過 `Shadow.Enabled` 旗標並調整模糊、距離、角度與顏色。  
* 示範了 **如何加入陰影**、**如何建立矩形**、以及 **如何設定陰影** 的完整、可重複使用程式碼。  
* 提供一個完整、可直接執行的範例，讓你能貼到任何 C# 專案中。

## 下一步？

掌握基礎後，你可以進一步探索：

* **如何為圖片加入陰影**——相同的 `Shadow` API 也適用於 `ShapeType.Image`。
* **組合多個形狀**——直接在 Word 中建立流程圖或資訊圖表。
* **匯出為 PDF**——在加入陰影後呼叫 `document.Save("output.pdf")`，即可得到可列印的 PDF 版本。

盡情嘗試不同的顏色、角度，甚至漸層填色。API 足夠彈性，讓你在不開啟 Word 的情況下，也能打造專業級文件。

---

祝編程愉快！若遇到任何問題，歡迎在下方留言或前往 Aspose.Words 論壇——社群回應快速且熱心。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}