---
category: general
date: 2026-03-01
description: 使用 Aspose.Words 建立 Word 文件，並學習如何加入矩形形狀、如何加入陰影、如何設定透明度，以及如何建立形狀——全部以 C#
  完成。
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: zh-hant
og_description: 使用 Aspose.Words 於 C# 建立 Word 文件。學習如何新增矩形形狀、套用外部陰影以及設定透明度，只需幾個步驟。
og_title: 製作帶有矩形形狀與陰影的 Word 文件 – 教學
tags:
- Aspose.Words
- C#
- Document Generation
title: 建立帶有矩形形狀與陰影的 Word 文件 – 逐步指南
url: /zh-hant/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用矩形形狀與陰影建立 Word 文件 – 步驟說明指南

是否曾需要 **create word document** 並在其中加入自訂樣式的矩形？也許你正在製作報告範本，想要加上一點細緻的投影讓版面更有層次感。你並不是唯一有此需求的人——開發者常問：「如何以程式方式加入矩形形狀與陰影？」好消息是，使用 Aspose.Words 只需幾行程式碼即可完成。

在本教學中，我們將一步步說明整個流程：從建立空白 Word 檔案、加入矩形形狀、設定外部陰影與透明度。完成後，你將得到一個可直接在 Word 中開啟、即時看到效果的 `Shadow.docx`。不需要外部工具，也不必手動編輯 XML——只要乾淨的 C# 程式碼與清晰的說明。

## 你將學會

- **如何在 Word 文件中建立 shape 物件**，使用 Aspose.Words。
- **如何將 rectangle shape 加入段落**，且不會影響既有內容。
- **如何加入陰影**（外部陰影）並控制其顏色、偏移、模糊與透明度。
- **如何設定陰影的透明度**，讓外觀更專業。
- 實務專案中可能遇到的技巧、陷阱與變化。

### 前置條件

- .NET 6.0 或更新版本（API 亦支援 .NET Framework 4.6+）。
- 透過 NuGet 安裝 Aspose.Words for .NET（`Install-Package Aspose.Words`）。
- 具備基本的 C# 語法概念——只要會使用 `using` 陳述式與建立物件即可。

> **Pro tip:** 若使用 Visual Studio，請啟用「nullable reference types」以提前捕捉可能的 null 參考錯誤。

## 第一步 – 建立空白 Word 文件

要 **create word document**，我們先使用 `Document` 類別。它就像一張空白畫布，之後可以加入章節、段落、表格或形狀。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

為什麼需要一個全新的 `Document` 實例？因為每個形狀、段落或樣式都存在於文件物件模型（DOM）之中。從乾淨的文件開始，可確保你加入的矩形不會與既有內容衝突。

## 第二步 – 定義矩形形狀

現在我們 **how to create shape** 一個矩形。`Shape` 建構子需要傳入所屬文件與形狀類型。我們同時設定寬度與高度（單位為點，1 pt ≈ 1/72 in）。

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

你可能會問：「可以改用公分而不是點嗎？」API 只接受點數，但可以自行換算：`points = centimeters * 28.35`。在對齊形狀至頁邊距時，這個小換算非常實用。

## 第三步 – 加入外部陰影並設定透明度

接下來就是關鍵：**how to add shadow** 以及 **how to set transparency**。`ShadowFormat` 屬性讓你全面掌控。

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**為什麼要這樣設定？**  
- **Transparency** 讓底層頁面紋理得以透出，避免陰影顯得過於沉重。  
- **OffsetX/Y** 創造形狀被「抬起」的錯覺。  
- **BlurRadius** 使陰影邊緣柔和——若不設定，陰影會變成硬直的矩形，顯得不自然。

若想要更戲劇化的效果，可將 `OffsetX/Y` 提升至 10，並將 `BlurRadius` 增至 8。相反地，若只想要微妙的提示，保持 2 與 2 即可。

## 第四步 – 將形狀插入文件

我們現在 **add rectangle shape** 到文件的第一個段落。若文件尚無內容，`FirstParagraph` 會自動為你建立。

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

如果想把形狀放在特定的表格儲存格或較後的段落，只需定位該節點（`doc.GetChild(NodeType.Paragraph, index, true)`），然後對其呼叫 `AppendChild`。需要多個相同形狀時，可使用 `Clone` 複製物件。

## 第五步 – 儲存文件

最後，我們 **create word document** 到磁碟。使用符合你環境的路徑；範例中使用佔位符。

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

當你在 Microsoft Word 中開啟 `Shadow.docx`，會看到一個淡灰色矩形，右下角帶有柔和的外部陰影。陰影的 30 % 透明度確保它不會搶走頁面的焦點。

---

![建立帶陰影的矩形形狀的 word 文件](image.png "建立帶陰影的矩形形狀的 word 文件")

*Image alt text: create word document with a shadowed rectangle shape*

## 完整、可直接執行的程式碼

以下是完整程式，你可以直接複製貼上到 Console 應用程式中。沒有遺漏，也不需要「請參考文件」之類的說明。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### 預期結果

- 在目標資料夾中產生名為 **Shadow.docx** 的檔案。
- 用 Word 開啟時會看到一個 200 × 100 pt 的矩形，帶有深灰色外部陰影。
- 陰影水平與垂直各偏移 5 pt，且已模糊、透明度為 30 %。

## 常見問題與邊緣案例

| Question | Answer |
|----------|--------|
| **Can I change the shadow color to match my brand?** | Absolutely—just replace `System.Drawing.Color.DarkGray` with any `Color` you prefer, e.g., `Color.FromArgb(255, 0, 120, 215)` for a blue accent. |
| **What if I need an inner shadow instead of outer?** | Set `ShadowFormat.Style = ShadowStyle.InnerShadow`. The rest of the properties behave the same. |
| **Is transparency supported in older Word versions?** | Yes. Aspose.Words writes the appropriate XML that Word 2007+ understands. Older versions may ignore the transparency value but will still show the shadow. |
| **Can I add multiple shapes with different shadows?** | Sure—just create new `Shape` instances, configure each shadow independently, and append them to the desired nodes. |
| **What about performance for hundreds of shapes?** | Creating many shapes can increase memory usage. Reuse a single `Document` instance and add shapes in a loop; dispose of temporary objects if you run into pressure. |

## 真實專案的實用技巧

- **批次產生：** 為多位使用者產生報表時，先建立單一 `Document` 範本，然後在每次迭代時複製它。插入形狀前先取代佔位字串。
- **動態尺寸：** 使用頁面尺寸 (`document.FirstSection.PageSetup.PageWidth`) 計算相對於頁面的形狀大小，確保在不同紙張尺寸下版面一致。
- **測試：** 每次調整陰影參數後，都在 Word 中開啟產生的 `.docx` 以目視確認。視覺回饋比猜測數值快得多。

## 後續步驟

既然你已掌握 **how to add rectangle shape**、**how to add shadow** 與 **how to set transparency**，可以進一步探索：

- 為形狀加入 **gradient fills**（`Shape.FillFormat`）。
- 在形狀內嵌入 **pictures**，製作浮水印效果。
- 使用 **tables** 讓多個帶陰影的形狀以格線方式排列。
- 將同一文件匯出為 PDF（`document.Save("output.pdf")`），同時保留陰影效果。

上述每項功能皆建基於相同的核心概念，讓你在擴充程式碼時更加得心應手。

---

### 重點回顧

我們先 **create word document**，接著 **how to create shape** 一個矩形，然後 **how to add shadow**，再 **how to set transparency**，最後儲存結果。整個流程簡潔且可重複使用，適用於任何自動化情境。

歡迎自行實驗——變更顏色、調整偏移，或堆疊多個形狀。若遇到問題，回顧上述章節即可快速找到答案。祝開發順利，讓你的文件永遠保持精緻！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}