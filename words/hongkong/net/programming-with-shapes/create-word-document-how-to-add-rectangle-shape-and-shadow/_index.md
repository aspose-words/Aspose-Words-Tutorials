---
category: general
date: 2026-03-19
description: 使用 C# 與 Aspose.Words 建立 Word 文件，學習如何加入形狀、加入矩形形狀、套用陰影，並在數分鐘內將文件儲存為 docx。
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: zh-hant
og_description: 使用 Aspose.Words 建立 Word 文件，加入矩形形狀，套用外部陰影，並將文件儲存為 docx。逐步指南。
og_title: 建立 Word 文件 – 加入矩形形狀及陰影
tags:
- Aspose.Words
- C#
- Document Automation
title: 建立 Word 文件 – 如何加入矩形圖形及陰影
url: /zh-hant/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立 Word 文件 – 如何加入矩形形狀及陰影

是否曾經需要以程式方式 **建立 Word 文件**，卻不知道從何開始？您並不孤單。許多開發者在首次嘗試產生包含自訂圖形的 .docx 檔案時，都會卡在同一個問題上。在本教學中，我們將完整說明整個流程——如何加入形狀，特別是 **加入矩形形狀**，為其添加時尚的 **為形狀加入陰影**，最後 **將文件儲存為 docx**。  

完成本指南後，您將擁有一段可直接使用的 C# 程式碼片段，能夠直接嵌入任何 .NET 專案。沒有模糊的參考，只有完整且可執行的範例。  

## 前置條件

- .NET 6.0 或更新版本（此程式碼亦可於 .NET Framework 使用）。  
- 已安裝 Aspose.Words for .NET（NuGet 套件 `Aspose.Words`）。  
- 具備基本的 C# 語法概念—不需要任何進階知識。  

如果缺少此函式庫，請執行：

```bash
dotnet add package Aspose.Words
```

就這樣—不需要額外的 SDK、也不需要 COM interop，只要一個 NuGet 參考即可。

---

## 步驟 1：建立 Word 文件（主要目標）

我們首先需要的是一個乾淨的畫布。可以把 `Document` 類別想像成 Microsoft Word 中的全新頁面；它會容納章節、段落以及之後要加入的所有內容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

為什麼要從空白的 `Document` 開始？因為這樣可以保證不會有來自範本的隱藏格式滲入。依我的經驗，從頭開始可以避免在之後插入形狀時出現神祕的版面變動。

---

## 步驟 2：插入矩形形狀 – 加入視覺元素

既然已有文件，讓我們在第一段落 **加入矩形形狀**。`Shape` 物件相當多功能；您可以選擇 `ShapeType.Rectangle`、`Ellipse`，甚至自訂繪圖。以下是最簡化的程式碼：

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**底層發生了什麼？**  
- `ShapeType.Rectangle` 告訴 Aspose 我們想要一個簡單的方框。  
- `WrapType.Inline` 確保矩形會隨文字流動，這通常是文字處理情境下的預期行為。  
- 透過附加到 `FirstParagraph`，我們免除手動插入新段落的需求；若文件真的空白，Aspose 會自動為我們建立段落。  

> **專業提示：** 若需要形狀位於文字*後方*，將 `WrapType` 改為 `WrapType.Transparent`。這個小變更即可帶來巨大的視覺差異。

---

## 步驟 3：套用外部陰影 – 增強外觀

平面的矩形…就是平的。為形狀 **加入陰影** 能在不使用額外圖片的情況下增加立體感。Aspose 的 `ShadowFormat` 讓這只需要一行程式碼即可完成。

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

為什麼要使用這些特定數值？  
- `5.0` 的 **Blur** 產生細緻的羽化邊緣，在大多數螢幕上看起來相當專業。  
- `3.0` 的 **Distance** 與 `45` 的 **Angle** 模擬左上方的自然光源，這是常見的設計慣例。  
- **Color.Gray** 在亮色與暗色佈景主題下皆適用；若需要更強的對比，可改為 `Color.Black`。  

如果您需要*內部*陰影（例如凹陷的按鈕），只要將 `ShadowType.OuterShadow` 改為 `ShadowType.InnerShadow`。其他屬性仍然適用。

---

## 步驟 4：將文件儲存為 DOCX – 保存您的工作

所有的操作都很有趣，但最終您仍需要將檔案寫入磁碟。**將文件儲存為 docx** 的步驟相當直接：

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

需要留意的幾點：  
- `SaveFormat.Docx` 列舉確保使用現代的 Office Open XML 格式，與 Word 2007 以上版本相容。  
- 若需直接將檔案串流至 Web 回應，只要將檔案路徑改為 `MemoryStream`，再寫入 HTTP 回應即可。  

執行程式碼後，於 Microsoft Word 開啟 `ShadowedRectangle.docx`。您應該會看到一個帶有柔和陰影的灰色矩形，與第一段落內聯顯示——正是我們預期的結果。

---

## 如何加入形狀 – 替代方法

上述範例使用 *內聯* 方式，但有時您會希望形狀浮於文字之上。這時 **如何加入形狀** 並搭配不同的環繞方式就派上用場。

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

此處我們將 `WrapType` 改為 `Square`，並將形狀置中於頁面。此模式適用於封面或裝飾性橫幅。請記得：浮動形狀會略微增加檔案大小，因為 Word 會儲存額外的定位資料。

---

## 預期輸出與驗證

當您開啟產生的檔案時，應該會看到：

- 一個包含灰色矩形的單一段落。  
- 矩形尺寸約為 2.8 × 1.4 英吋。  
- 一個微妙的外部陰影，偏移至右下角。  

如果形狀出現在段落*外部*，請再次確認 `WrapType`。若陰影過於刺眼，請降低 `Blur` 數值或將 `Color` 改為較淡的色調。

---

## 常見陷阱與避免方法

| 問題 | 發生原因 | 解決方法 |
|-------|----------------|-----|
| 儲存後形狀消失 | `WrapType` 設為 `Inline`，但段落已被移除 | 確保段落存在；使用 `doc.FirstSection.Body.FirstParagraph` 以保證段落存在。 |
| 陰影呈像素化 | 使用過低的 `Blur` 數值 | 將 `Blur` 提升至至少 `3.0` 以獲得平滑邊緣。 |
| 檔案大小急劇增加 | 在形狀旁加入大量高解析度圖片 | 若已加入圖片，於儲存前使用 `doc.RemoveUnusedResources()`。 |
| 深色模式下顏色不顯示 | 形狀本身使用深色 `Color` | 選擇對比色（例如 `Color.White`）以提升可見度。 |

---

## 完整範例程式碼

以下是完整、可直接複製貼上的程式碼，涵蓋我們所討論的所有內容。您可以將其作為主控台應用程式執行。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**每個區塊的說明** 以註解形式內嵌，兼顧 SEO 讀者與喜歡自包含答案的 AI 助手。

---

## 結論

我們剛剛從頭 **建立 Word 文件**，學會 **如何加入形狀**，特別是 **加入矩形形狀**，為其 **加入陰影**，最後 **將文件儲存為 docx**。步驟簡單，程式碼精簡，結果也相當精緻。  

如果您想更進一步，可以嘗試將矩形換成自訂圖片、實驗不同的陰影顏色，或產生包含多個形狀區段的完整報告。Aspose.Words API 足夠彈性，能處理從發票到行銷手冊的各種需求。  

對其他形狀類型有疑問，或需要將此功能整合至 ASP.NET Core 服務中？歡迎在下方留言，祝編程愉快！ 

![建立 Word 文件，帶有矩形形狀與陰影](placeholder-image.png "建立 Word 文件，帶有矩形形狀與陰影

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}