---
category: general
date: 2026-02-18
description: 使用 Aspose.Words 建立矩形形狀，學習如何加入陰影、設定形狀大小，並在幾分鐘內儲存 Word 文件。
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: zh-hant
og_description: 在 Word 檔案中建立矩形形狀，學習如何加入陰影、設定形狀大小，並使用 Aspose.Words 於 C# 儲存文件。
og_title: 在 Word 中建立矩形形狀 – 完整的 Aspose.Words 教學
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 Aspose.Words 在 Word 中建立矩形形狀 – 步驟指南
url: /zh-hant/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 Aspose.Words 建立矩形形狀 – 步驟指南

曾經需要 **在 Word 檔案中建立矩形形狀**，卻不知道從哪裡開始嗎？你並不孤單——開發者常問：「如何為形狀加入陰影，同時保持文件可編輯？」在本教學中，我們將解答這個問題，並示範 **如何加入陰影**、**設定形狀尺寸**，以及 **儲存 Word 文件**，一次完成整個流程。

我們會一步步說明，從初始化新文件（是的，這是 **如何建立文件** 的第一步）到將最終的 *.docx* 儲存到磁碟。全程不依賴外部參考，僅提供一個可直接複製貼上到 Visual Studio 並立即執行的完整範例。

---

## 前置條件

- .NET 6+（或 .NET Framework 4.7+）。Aspose.Words 支援任何近期的 .NET 執行環境。
- 有效的 Aspose.Words 授權（或免費評估金鑰）——否則會看到浮水印。
- Visual Studio、Rider，或任何你慣用的 C# 編輯器。
- 基本的 C# 知識——不需要高階技巧，只要能執行主控台應用程式即可。

> **專業小技巧：** 若你使用 Mac，只要在 .NET 6 下搭配 VS Code 執行相同程式碼——記得引用 `Aspose.Words` NuGet 套件即可。

---

## 步驟 1：初始化文件 – **如何建立文件** 的基礎

在繪製任何圖形之前，我們需要一張空白畫布。Aspose.Words 稱之為 `Document`。  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **為什麼重要：** `Document` 物件代表整個 *.docx* 檔案。所有加入的形狀、段落與節都會成為此物件的子項。從乾淨的文件開始，可避免隱藏樣式干擾你的矩形。

---

## 步驟 2：定義矩形並 **設定形狀尺寸**

矩形只是 `Shape` 且 `ShapeType.Rectangle`。我們會為它指定明確的寬高，使其呈現如預期的樣子。

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **數值說明：** Aspose.Words 使用點作為單位（1 pt = 1/72 in）。依需求調整數值；對於一般 A4 頁面，200 pt 是一個舒適的寬度。

---

## 步驟 3：**如何加入陰影** – 讓形狀更突出

陰影提供視覺提示，讓形狀看起來「浮起」於頁面。`Shadow` 屬性可調整顏色、距離、透明度與模糊度。

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **為什麼使用透明度？** 完全不透明的陰影會顯得生硬。將透明度設為 0.4 可讓效果更為細膩、專業。

---

## 步驟 4：定位矩形 – 與周圍文字的行內流動

若希望形狀在段落中如同字元般行為，將 `WrapType` 設為 `Inline`。這樣在文件日後編輯時，版面會更可預測。

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **特殊情況：** 若需要矩形漂浮於文字上方（例如浮水印），可將 `WrapType` 改為 `Square` 或 `BehindText`。

---

## 步驟 5：將形狀插入文件主體

現在把矩形放入第一個段落。若文件尚未有內容，`FirstParagraph` 會自動建立。

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **小技巧：** 也可以先建立新段落，再將形狀附加上去——在需要前後文字環繞時特別有用。

---

## 步驟 6：**儲存 Word 文件** – 最後一步

所有設定完成後，儲存檔案只需一行程式碼。路徑可自行決定；範例使用佔位路徑，請自行替換為實際目錄。

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **結果：** 用 Microsoft Word 開啟產生的 *.docx*，即可看到一個寬 200 pt、高 100 pt、帶有黑色陰影的矩形，且與第一段文字行內對齊。

---

## 預期輸出

開啟 **ShadowShape.docx** 時，文件會顯示：

- 單一段落內含一個矩形形狀。
- 矩形具有 5 pt 偏移的細微黑色陰影。
- 形狀尺寸與步驟 2 中設定的寬高相符。
- 除非手動加入，否則不會出現其他文字。

若形狀未顯示，請再次確認已引用正確的 Aspose.Words 版本，且授權（或試用）已啟用。

---

## 常見問題與變化

| 問題 | 答案 |
|----------|--------|
| *我可以把陰影顏色改成除黑色以外的其他顏色嗎？* | 當然可以——設定 `rectangleShape.Shadow.Color = Color.Blue;` 或任意 `System.Drawing.Color`。 |
| *如果需要更大的矩形該怎麼辦？* | 調整 `Width` 與 `Height` 的數值。記得它們的單位是點；72 pt = 1 in。 |
| *能否將形狀放在絕對位置？* | 可以——使用 `WrapType = WrapType.Absolute`，再設定 `Top`/`Left` 屬性。 |
| *這在 .NET Core 上可用嗎？* | 可以。Aspose.Words 為跨平台套件，只要安裝對應的 .NET Standard NuGet 即可。 |
| *我可以在矩形內加入文字嗎？* | 直接的矩形不支援文字；若需文字，請改用 `TextBox` 形狀取代普通矩形。 |

---

## 完整可執行範例（直接複製貼上）

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

執行程式後，前往 `C:\Temp\ShadowShape.docx`，即可看到如說明所示的帶陰影矩形。

---

## 結論

現在你已掌握如何使用 Aspose.Words 在 Word 檔案中 **建立矩形形狀**、**設定形狀尺寸**、**加入陰影**，以及最後 **儲存 Word 文件**。從 **如何建立文件** 到持久化結果，整個流程只需幾行 C# 程式碼，且可延伸至更複雜的版面配置。

準備好接受下一個挑戰了嗎？試著把矩形換成圓角形狀、變換陰影顏色，或將形狀嵌入表格儲存格中。每一次微調都能鞏固我們在本文中討論的核心概念。

如果本指南對你有幫助，歡迎分享、留言你的變化版本，或探索我們其他關於 Word 自動化的教學，例如插入圖片或使用 Aspose.Words 產生表格。祝程式開發愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}