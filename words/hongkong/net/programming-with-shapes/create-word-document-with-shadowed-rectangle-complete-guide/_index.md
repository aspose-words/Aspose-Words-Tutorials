---
category: general
date: 2026-04-21
description: 建立帶有樣式化矩形與陰影的 Word 文件。學習如何在 C# 中加入陰影、插入矩形形狀、設定陰影顏色等。
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: zh-hant
og_description: 在 C# 中建立 Word 文件並加入帶陰影的矩形形狀。依照本指南輕鬆設定陰影顏色、模糊程度與偏移量。
og_title: 建立帶陰影矩形的 Word 文件 – 步驟說明
tags:
- Aspose.Words
- C#
- Document Automation
title: 建立帶陰影矩形的 Word 文件 – 完整指南
url: /zh-hant/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用陰影矩形建立 Word 文件 – 完整指南

有沒有需要 **建立 Word 文件**，但希望它看起來比單純的文字頁面更精緻？也許你在製作報告範本或傳單，只要一個帶有細緻陰影的矩形就能達成目的。本教學將一步步說明——如何插入矩形形狀、開啟陰影，並自訂顏色、模糊程度與偏移量，全部使用 C# 與 Aspose.Words。

我們也會說明 **如何加入陰影**，讓它在 Word 2016、2019 或最新的 Office 365 版本皆能正確顯示。完成後，你將得到一個可直接儲存的 *.docx* 檔案，裡面展示了漂亮的陰影矩形，並了解每個屬性的設定原因。

## 前置條件

- .NET 6（或任何較新的 .NET Framework 版本）  
- Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）  
- 基本的 C# 語法概念  
- 如 Visual Studio 等 IDE（任何編輯器皆可）

不需要額外的函式庫；其餘功能皆內建於 Aspose.Words。

## 第一步 – 初始化文件與 Builder（建立 Word 文件）

要 **建立 Word 文件**，首先使用 `Document` 類別。`DocumentBuilder` 就像你的畫筆，讓你可以加入文字、圖形與其他元素。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*為什麼這很重要：* `Document` 物件代表整個 .docx 檔案。沒有它，就無法附加矩形或其陰影。

## 第二步 – 插入矩形形狀（Insert Rectangle Shape）

現在正式 **插入矩形形狀**。`InsertShape` 方法接受 `ShapeType` 列舉，並以點數指定寬度與高度。

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*小技巧：* 1 點 ≈ 1/72 英吋，所以 200 點大約是 2.78 英吋寬。依需求自行調整數值。

## 第三步 – 開啟陰影（How to Add Shadow）

預設情況下陰影是關閉的。將 `Visible` 屬性設為 `true` 即可開啟。

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*發生了什麼事？* 當 `Visible` 為 true 時，Word 會根據接下來設定的屬性渲染投影。

## 第四步 – 自訂陰影外觀（Set Shadow Color, Blur, Offsets）

接下來 **設定陰影顏色**、模糊半徑以及 X/Y 偏移量。盡情試玩——不同的數值會產生柔和光暈、深層投影，甚至「漂浮」的效果。

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*為什麼要這樣設定？* 模糊 5 點會產生柔和的羽化邊緣，偏移 4 點則把陰影向右下方移動，模擬光源來自左上角。將 `Color` 改為 `Color.Black` 可得到更強的對比，或使用 `Color.FromArgb(128, 0, 0, 0)` 取得半透明的黑色。

### 邊緣情況與變化

- **無模糊：** 設定 `Blur = 0` 可得到銳利、硬邊的陰影。  
- **負向偏移：** 使用 `OffsetX = -4` 可把陰影往左推。  
- **不同形狀：** 相同的陰影屬性同樣適用於圓形、三角形或自由繪製的形狀——只要在第 2 步更改 `ShapeType` 即可。  
- **相容性：** Aspose.Words 會將陰影資料寫入 Office Open XML 格式，支援 Word 2010‑2021 以及 Office 365。

## 第五步 – 儲存文件（建立 Word 文件）

最後，將檔案寫入磁碟。你可以選擇任何支援的格式（`.docx`、`.pdf`、`.odt`…），本教學以傳統的 Word 格式為例。

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

當你在 Microsoft Word 中開啟 **ShadowRectangle.docx** 時，會看到一個帶有細緻、模糊陰影的灰色矩形，陰影向右下方偏移——正是我們程式碼所設定的效果。

### 預期輸出

- 單頁 *.docx* 檔案。  
- 200 點 × 100 點的矩形，位於呼叫 `InsertShape` 時游標所在的中心位置。  
- 灰色陰影向右下方偏移 4 點，模糊度為 5 點。

如果形狀看起來偏離中心，可在插入前使用 `builder.MoveTo` 移動游標，或在插入後調整形狀的 `Left` 與 `Top` 屬性。

## 常見問題與除錯

**Q: 陰影在 Word 中沒有顯示。**  
A: 確認 `ShadowFormat.Visible` 為 `true`。同時檢查使用的 Aspose.Words 版本（陰影功能於 20.3 版加入）。

**Q: 可以為陰影套用漸層嗎？**  
A: `ShadowFormat` 本身不支援漸層。Word UI 可以設定漸層陰影，但 Open XML（Aspose.Words 所遵循的規格）僅提供純色陰影。若需漸層，必須手動編輯底層 XML，屬較進階的情境。

**Q: 若想要只有陰影、沒有填色的透明矩形該怎麼做？**  
A: 插入後設定 `rectangle.FillColor = Color.Transparent;`。陰影仍會顯示，因為它與填色互不相干。

## 生產環境程式碼小技巧

- **重複使用 Builder：** 若要加入多個形狀，請保留同一個 `DocumentBuilder` 實例——為每個形狀重新建立會產生不必要的開銷。  
- **批次儲存：** 完成所有修改後一次儲存；頻繁的 I/O 會拖慢大型文件的產生速度。  
- **錯誤處理：** 把整段程式碼包在 `try / catch` 中，並記錄 `Aspose.Words` 例外；若文件範本損毀，例外訊息通常會提供有用的行號資訊。

## 後續主題（相關議題）

- **如何為圖片或文字方塊加入陰影**（相同的 `ShadowFormat` 用法）。  
- **在表格儲存格內插入矩形形狀**，用於自訂儲存格樣式。  
- **使用 Word 原生 XML 建立矩形**（適合偏好直接操作 Open XML 的開發者）。  
- **根據使用者輸入或主題顏色動態設定陰影顏色**。

盡情嘗試不同的顏色、模糊半徑與偏移量——例如企業報告的柔和藍光，或宣傳單的深黑陰影。可能性無窮，而程式碼變動卻相當簡單。

---

### 快速回顧

- 我們 **建立了 Word 文件** 從零開始。  
- 我們 **插入了矩形形狀** 並開啟了陰影。  
- 我們 **設定陰影顏色、模糊與偏移**，打造專業外觀。  
- 我們儲存檔案，隨時可供分發。

現在你已掌握在任何 Word 自動化專案中加入視覺亮點的基礎。還有其他想法嗎？歡迎留言討論，讓我們持續交流。祝開發愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}