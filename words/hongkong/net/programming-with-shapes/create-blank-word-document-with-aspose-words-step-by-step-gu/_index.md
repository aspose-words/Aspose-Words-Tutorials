---
category: general
date: 2026-02-23
description: 使用 C# 與 Aspose.Words 建立空白 Word 文件。學習如何加入矩形形狀、為文字添加陰影，並在數分鐘內儲存帶有形狀的 Word。
draft: false
keywords:
- create blank word document
- add rectangle shape
- how to add shape
- add shadow word
- save word with shape
language: zh-hant
og_description: 快速建立空白 Word 文件。本指南示範如何使用 Aspose.Words 添加矩形形狀、加入陰影文字，並將含有形狀的 Word 檔案儲存。
og_title: 建立空白 Word 文件 – 完整 C# 教學
tags:
- Aspose.Words
- C#
- Document Automation
title: 使用 Aspose.Words 建立空白 Word 檔案 – 步驟指南
url: /zh-hant/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/
---

色陰影的矩形形狀 – add shadow word 範例". The title attribute also "add shadow word example" maybe translate but keep phrase. We'll translate to "add shadow word 範例". Let's do.

We must keep shortcodes at top and bottom.

Now produce final content.

Let's translate each paragraph.

We'll keep bullet points.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立空白 Word 文件 – 完整 C# 教學

有沒有想過要 **建立空白 Word 文件** 而不必開啟 Microsoft Word？你並不孤單。在許多自動化專案中，我們需要一個全新的 .docx 檔案，往裡面放一個圖形，為圖形加上漂亮的陰影，然後 **儲存含圖形的 Word** 以供日後使用。

在本指南中，我們將一步步完成這件事——從空白文件開始，**新增矩形圖形**，設定 **add shadow word** 效果，最後將檔案寫入磁碟。完成後，你會得到一段完整、可直接貼到任何 .NET 主控台應用程式的程式碼。沒有神祕、沒有遺漏。

## 你需要的環境

- **Aspose.Words for .NET**（任意近期版本，例如 24.10）。  
- .NET 6 或更新版本（此程式碼同樣支援 .NET Framework 4.7+）。  
- 基本的 C# IDE——Visual Studio、Rider，或是安裝 C# 擴充功能的 VS Code。  

就這些。除了 Aspose.Words 之外不需要其他 NuGet 套件，也不需要安裝 Word。

---

## 步驟 1：建立空白 Word 文件

當你想 **建立空白 Word 文件** 時，第一件事就是實例化 `Document` 類別。把它想成 Aspose.Words 提供給你的乾淨畫布。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1 – initialize an empty document
Document document = new Document();   // this is a brand‑new, blank Word file
```

> **為什麼重要：** `Document` 物件會保存所有的節、段落與圖形。從空的實例開始，保證你能掌控之後加入的每一個元素。

---

## 步驟 2：在文件中加入矩形圖形

現在我們有了乾淨的文件，接著 **加入矩形圖形**。矩形就是一個 `Shape`，其 `ShapeType` 為 `Rectangle`。當然你也可以選其他類型，但矩形最適合示範。

```csharp
// Step 2 – create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width = 200,   // width in points (≈2.78 inches)
    Height = 100   // height in points (≈1.39 inches)
};
```

> **小技巧：** 若你想 **how to add shape** 不是矩形，只要把 `ShapeType.Rectangle` 改成其他列舉值，例如 `ShapeType.Ellipse` 或 `ShapeType.Polygon`，其餘程式碼不變。

---

## 步驟 3：為圖形設定自訂陰影

普通的矩形看起來有點單調，我們會 **add shadow word** 讓它更有層次感。Aspose.Words 提供 `ShadowFormat` 物件，裡面有許多屬性可調整。

```csharp
// Step 3 – enable and style the shadow
rectangleShape.ShadowFormat.Enabled = true;                // turn on the shadow
rectangleShape.ShadowFormat.Color = Color.Gray;           // shadow color
rectangleShape.ShadowFormat.OffsetX = 5;                  // horizontal offset (points)
rectangleShape.ShadowFormat.OffsetY = 5;                  // vertical offset (points)
rectangleShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
rectangleShape.ShadowFormat.BlurRadius = 4;               // soft edge blur
```

> **為什麼重要：** 陰影能提供微妙的深度感，特別是文件在螢幕上檢視時。可依設計需求調整 `OffsetX`、`OffsetY` 與 `BlurRadius`。

---

## 步驟 4：將圖形插入文件

圖形已備妥，接下來要把它放到文件裡。最簡單的方式是放在第一個節的第一段落。若文件尚未有段落，Aspose 會自動建立一個。

```csharp
// Step 4 – put the rectangle into the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **邊緣情況：** 若你想把圖形插入特定位置（例如某個標題之後），可透過 `document.GetChildNodes(NodeType.Paragraph, true)` 取得目標 `Paragraph`，再使用 `InsertAfter` 或 `InsertBefore`。

---

## 步驟 5：將含圖形的 Word 文件儲存

最後，我們 **save word with shape** 到磁碟。`Save` 方法會依檔案副檔名自動判斷格式。

```csharp
// Step 5 – persist the document
string outputPath = @"C:\Temp\shadowedRectangle.docx";
document.Save(outputPath);
```

> **執行結果：** 開啟 `shadowedRectangle.docx`（使用 Word 或任何相容檢視器），你會看到第一頁頂端有一個帶柔和陰影的灰色矩形。

---

## 完整範例程式

以下是可直接貼到主控台應用程式的完整程式碼，包含所有 using 陳述、註解與前述步驟。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeWordShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank word document
            Document document = new Document();

            // 2️⃣ Add a rectangle shape
            Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100
            };

            // 3️⃣ Configure a custom shadow (add shadow word)
            rectangleShape.ShadowFormat.Enabled = true;
            rectangleShape.ShadowFormat.Color = Color.Gray;
            rectangleShape.ShadowFormat.OffsetX = 5;
            rectangleShape.ShadowFormat.OffsetY = 5;
            rectangleShape.ShadowFormat.Transparency = 0.3;
            rectangleShape.ShadowFormat.BlurRadius = 4;

            // 4️⃣ Insert the shape into the first paragraph
            document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

            // 5️⃣ Save the document (save word with shape)
            string outputFile = @"YOUR_DIRECTORY\shadow.docx";
            document.Save(outputFile);

            // Confirmation
            System.Console.WriteLine($"Document saved to {outputFile}");
        }
    }
}
```

執行程式後，前往 `YOUR_DIRECTORY`，開啟產生的 `shadow.docx`。你應該會看到帶有細緻灰色陰影的矩形——正是我們預期的結果。

---

## 常見問題與小技巧

### 如何變更圖形顏色？
```csharp
rectangleShape.FillColor = Color.LightBlue;
```
在加入圖形前設定 `FillColor` 即可。

### 若需要在同一頁放多個圖形該怎麼做？
建立額外的 `Shape` 物件，分別加入同一段落或不同段落。也可以使用 `WrapType` 與 `RelativeHorizontalPosition` 來控制版面配置。

### 匯出成 PDF 時能保留陰影嗎？
當然可以。使用 `document.Save("output.pdf")`——Aspose.Words 會在 PDF 轉換時保留陰影效果。

### 這在 .NET Core 上可行嗎？
可以。Aspose.Words 為跨平台套件，同一段程式碼可在 .NET Core、.NET 5+ 與 .NET Framework 上執行。

### 如何在沒有段落的情況下加入圖形？
可以直接將圖形加入 `Run` 或 `Story`。若需要更精確的定位，設定 `rectangleShape.RelativeHorizontalPosition = RelativeHorizontalPosition.Page`，再調整 `Left` 與 `Top` 屬性。

---

## 視覺結果

![Word 文件中帶有灰色陰影的矩形形狀 – add shadow word 範例](https://example.com/placeholder-image.png "add shadow word 範例")

*圖片替代文字包含次要關鍵字 **add shadow word**，以符合 SEO 需求。*

---

## 結論

我們剛剛示範了如何 **建立空白 Word 文件**、**加入矩形圖形**、套用 **add shadow word** 效果，最後 **save word with shape**，全程使用 Aspose.Words for .NET。流程相當直接：實例化 `Document`、建立 `Shape`、調整 `ShadowFormat`、插入文件，最後呼叫 `Save`。

接下來你可以自行實驗——嘗試不同的圖形類型、變換顏色，或是疊加多個圖形。若需要將此文件與既有內容合併，只要用 `new Document("existing.docx")` 讀入既有檔案，然後照相同步驟操作即可。

有其他問題嗎？歡迎留言，祝開發順利！

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}