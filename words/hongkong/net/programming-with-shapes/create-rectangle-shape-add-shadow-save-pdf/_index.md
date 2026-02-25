---
category: general
date: 2026-02-24
description: 使用 Aspose.Words 在 C# 中建立矩形形狀，為形狀添加陰影，並將文件另存為 PDF。只需數分鐘，即可學會如何添加陰影以及如何儲存
  PDF。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: zh-hant
og_description: 使用 C# 及 Aspose.Words 建立矩形形狀，然後為形狀加入陰影，並將文件儲存為 PDF – 完整的逐步教學指南。
og_title: 建立矩形形狀，加入陰影並儲存 PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: 建立矩形形狀，加入陰影並儲存 PDF
url: /zh-hant/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

.

Also need to keep the shortcodes at top and bottom.

Now let's produce translation.

We need to ensure Traditional Chinese (Hong Kong) style: use traditional characters, maybe use "您" etc.

Let's translate.

Start with the shortcodes unchanged.

Then heading "# Create rectangle shape, add shadow & save PDF" translate to "# 建立矩形形狀、加入陰影並儲存為 PDF"

Proceed.

Paragraphs.

Let's translate step by step.

Will keep markdown formatting.

Let's write.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立矩形形狀、加入陰影並儲存為 PDF

是否曾需要在 Word 文件中 **建立矩形形狀**，同時想要加入好看的投影，最後輸出為 PDF？您並非唯一遇到此需求的人。在許多報表或發票產生專案中，視覺上的精緻度——例如細緻的陰影——往往決定了「只是另一個檔案」與「專業等級文件」之間的差距。

在本教學中，我們將逐步示範：使用 **Aspose.Words for .NET** 來建立矩形形狀、為形狀加入陰影，最後 **將文件儲存為 PDF**。完成後，您將得到一個可直接執行的 C# 主控台應用程式，產生帶有陰影的矩形 PDF，並了解如何微調陰影或變更匯出選項。

## 您需要的環境

- .NET 6 SDK（或任何較新的 .NET 版本）——相同的 API 亦可在 .NET Framework 4.x 上執行。  
- Aspose.Words for .NET NuGet 套件 (`Aspose.Words`)——使用 `dotnet add package Aspose.Words` 安裝。  
- 程式碼編輯器——Visual Studio、VS Code 或 Rider 都可以。  

此範例不需要額外的授權步驟；免費的評估模式已足以看到 PDF 輸出結果。

## 步驟 1：建立專案並匯入命名空間

首先，建立一個主控台專案，並引入我們稍後會用到的類別。

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*為什麼這很重要*：`Document` 與 `DocumentBuilder` 提供畫布，`Shape` 與 `ShadowFormat` 則負責繪製與樣式設定。提前匯入可以讓後續程式碼更整潔。

## 步驟 2：**建立矩形形狀** 並設定尺寸

接著，我們建立一個空白文件，並插入矩形。`InsertShape` 方法會回傳 `Shape` 物件，讓我們立即進行樣式設定。

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*說明*：尺寸以點 (pt) 為單位 (1 pt = 1/72 in)。依需求調整數值以符合版面配置。我們同時為形狀填上淡藍色，讓陰影更顯眼。

## 步驟 3：**為形狀加入陰影** ─ 微調效果

陰影不只是「開」或「關」。您可以控制顏色、模糊程度、距離、方向，甚至透明度。以下是一組在大多數報表中表現良好的設定範例。

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*您可能想調整的屬性*：  
- **BlurRadius** ─ 增大會產生夢幻效果，減少則邊緣更銳利。  
- **Direction** ─ 0° 指向右方，90° 向下，180° 向左，依頁面布局自行旋轉。  
- **Transparency** ─ 設為 `0` 為實心陰影，`0.5` 為半透明，依需求調整。

### 加入陰影的其他做法

若需要 **多層陰影**（例如外層較暗、內層較淡），可以再建立第二個形狀、偏移位置，並套用不同的 `ShadowFormat`。或是想要快速的「無模糊」外觀，只要把 `BlurRadius = 0` 即可。

## 步驟 4：**將文件儲存為 PDF** ─ 最終匯出

矩形與陰影設定完成後，最後一步是將檔案寫出為 PDF。Aspose.Words 會在內部處理轉換，只需呼叫 `Save` 並指定格式。

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*小技巧*：若需要控制 PDF 相容性（PDF/A、PDF/X）或嵌入字型，可使用以下重載：

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

以上即為 **如何儲存 PDF** 的精要說明。

## 完整、可執行的範例

以下程式碼可直接貼到 `Program.cs` 中編譯執行（只要確保輸出資料夾已存在）。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### 預期結果

開啟產生的 `ShadowRectangle.pdf`，您會看到單一頁面上有一個淡藍色矩形，右下角 45° 偏移的柔和灰色陰影，且邊緣乾淨。此 PDF 可在任何現代閱讀器（Adobe Acrobat、Edge、Chrome）中檢視。

![建立矩形形狀並加入陰影的 PDF](/images/shadow-rectangle.png "建立矩形形狀並加入陰影的 PDF")

*（圖片 alt 文字已包含主要關鍵字以利 SEO。）*

## 常見問題與邊緣案例處理

**如果陰影在 PDF 中消失了該怎麼辦？**  
請確認使用的是最新版本的 Aspose.Words（≥23.3）。較舊的版本曾有在 PDF 轉換時忽略某些陰影屬性的錯誤。

**可以把陰影顏色改成符合品牌色嗎？**  
當然可以，只要把 `System.Drawing.Color.Gray` 換成任何您想要的 `Color`，例如 `Color.FromArgb(128, 0, 0, 255)` 代表半透明藍色。

**如何為其他形狀（橢圓、星形等）加入陰影？**  
`ShadowFormat` 同樣適用於任何 `Shape` 物件。建立形狀後，取得其 `ShadowFormat` 並設定屬性即可。

**DPI 或縮放會不會有問題？**  
PDF 會依照形狀的點大小渲染。若需更高解析度的輸出（列印用），可調整形狀尺寸或設定 `PdfSaveOptions.ImageResolution`。

**可以匯出成其他格式，例如 PNG 嗎？**  
可以，只要呼叫 `document.Save("output.png", SaveFormat.Png)`。陰影會以相同方式呈現。

## 專業提示與最佳實踐

- **重複使用 builder**：若要加入多個形狀，保留同一個 `DocumentBuilder` 實例；比起每次建立新實例更省資源。  
- **批次儲存**：在迴圈中產生大量 PDF 時，重複使用 `PdfSaveOptions` 物件以避免重複配置。  
- **測試**：每次儲存後務必開啟 PDF 確認陰影如預期顯示。不同 PDF 閱讀器的渲染可能略有差異，Adobe Acrobat 為最可靠的參考。  
- **效能**：對於大型文件，若不需要自動分頁，可將 `builder.PageSetup.DifferentFirstPageHeaderFooter = false` 以關閉 `DocumentBuilder.InsertShape` 的自動分頁功能。

## 結論

我們已完整說明如何使用 Aspose.Words for .NET **建立矩形形狀**、**為形狀加入陰影**，以及 **將文件儲存為 PDF**。程式碼簡潔、概念清晰，您現在已具備穩固的基礎，可進一步嘗試其他形狀、陰影樣式與匯出選項。  

接下來的步驟？試著把矩形換成圓角‑

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}