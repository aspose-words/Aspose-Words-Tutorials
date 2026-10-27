---
title: 使用 Aspose.Words for .NET 為 Word 文件新增紅色斜向文字浮水印
weight: 110
limit:
description: 使用 Aspose.Words for .NET，自動為批次產生的每個 Word 檔案加上紅色斜向文字浮水印。
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: 使用 Aspose.Words for .NET，自動為批次產生的每個 Word 檔案加上紅色斜向文字浮水印。
  headline: 使用 Aspose.Words for .NET 為 Word 文件新增紅色斜向文字浮水印
  type: TechArticle
- description: 使用 Aspose.Words for .NET，自動為批次產生的每個 Word 檔案加上紅色斜向文字浮水印。
  name: 使用 Aspose.Words for .NET 為 Word 文件新增紅色斜向文字浮水印
  steps:
  - name: 建立 "GeneratedReports" 資料夾，以儲存輸出檔案。
    text: 建立 "GeneratedReports" 資料夾，以儲存輸出檔案。
  - name: 啟動一個迴圈，產生三個獨立的文件。
    text: 啟動一個迴圈，產生三個獨立的文件。
  - name: 建立一個新的空白 Word 文件物件。
    text: 建立一個新的空白 Word 文件物件。
  - name: 使用 DocumentBuilder 在文件中寫入標題行與說明文字。
    text: 使用 DocumentBuilder 在文件中寫入標題行與說明文字。
  - name: 定義浮水印的外觀，包括字型、大小、顏色以及斜向布局。
    text: 定義浮水印的外觀，包括字型、大小、顏色以及斜向布局。
  - name: 將已設定的紅色斜向浮水印（文字為 "PROTECTED"）套用至文件。
    text: 將已設定的紅色斜向浮水印（文字為 "PROTECTED"）套用至文件。
  - name: 將加了浮水印的文件以唯一檔名儲存至 "GeneratedReports" 資料夾。
    text: 將加了浮水印的文件以唯一檔名儲存至 "GeneratedReports" 資料夾。
  - name: 處理完目前的文件後結束迴圈。
    text: 處理完目前的文件後結束迴圈。
  type: HowTo
- questions:
  - answer: IsSemitrasparent 決定浮水印是否以半透明方式呈現；設定為 **true** 時，文字會變成半透明，使底層內容更易閱讀。
    question: '**IsSemitrasparent** 選項控制什麼？將其設為 **true** 會產生什麼效果？'
  - answer: 可以——在呼叫 **document.Watermark.SetText** 之前，於 **TextWatermarkOptions** 中將
      **Layout** 屬性設為 **WatermarkLayout.Horizontal**。
    question: 我可以將浮水印方向改為水平而非斜向嗎？
  - answer: 此程式碼片段會建立一個全新的 **Document** 實例，但您也可以開啟任何既有檔案（例如 `new Document(\"Existing.docx\")`），然後呼叫
      **document.Watermark.SetText** 以套用相同的浮水印。
    question: 此程式碼會在既有的 Word 檔案上加浮水印，還是僅針對新建立的文件？
  - answer: 使用 **Color.FromArgb(red, green, blue)** 為 **TextWatermarkOptions** 的 **Color**
      屬性指派自訂顏色，例如 `Color = Color.FromArgb(128, 0, 128)` 代表紫色。
    question: 如何使用自訂的 RGB 顏色作為浮水印，而非預設的 **Color.Red**？
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: 為 Word 文件新增紅色斜向文字浮水印
og_description: 了解如何使用 Aspose.Words 在批次中自動為每個 Word 文件加上紅色斜向浮水印。
og_image_alt: 指南：說明如何使用 Aspose.Words for .NET 為 Word 文件加入紅色斜向文字浮水印
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 為 Word 文件新增紅色斜向文字浮水印
本教學示範如何在批次報告產生過程中，自動將紅色斜向文字浮水印嵌入每一個產生的 Word 文件。透過 Aspose.Words for .NET 的 Document 與 DocumentBuilder 類別，於檔案產生時以程式方式套用浮水印，確保每份文件皆具相同的品牌或機密標示，免除手動操作。

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: **IsSemitrasparent** 選項控制什麼？將其設為 **true** 會產生什麼效果？**  
A: IsSemitrasparent 決定浮水印是否以半透明方式呈現；設定為 **true** 時，文字會變成半透明，使底層內容更易閱讀。

**Q: 我可以將浮水印方向改為水平而非斜向嗎？**  
A: 可以——在呼叫 **document.Watermark.SetText** 之前，於 **TextWatermarkOptions** 中將 **Layout** 屬性設為 **WatermarkLayout.Horizontal**。

**Q: 此程式碼會在既有的 Word 檔案上加浮水印，還是僅針對新建立的文件？**  
A: 此程式碼片段會建立一個全新的 **Document** 實例，但您也可以開啟任何既有檔案（例如 `new Document(\"Existing.docx\")`），然後呼叫 **document.Watermark.SetText** 以套用相同的浮水印。

**Q: 如何使用自訂的 RGB 顏色作為浮水印，而非預設的 **Color.Red**？**  
A: 使用 **Color.FromArgb(red, green, blue)** 為 **TextWatermarkOptions** 的 **Color** 屬性指派自訂顏色，例如 `Color = Color.FromArgb(128, 0, 128)` 代表紫色。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}