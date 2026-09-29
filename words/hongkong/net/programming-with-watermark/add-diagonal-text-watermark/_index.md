---
title: 使用 Aspose.Words for .NET 在 Word 文件中建立自訂字型的對角文字浮水印
weight: 210
limit:
description: 使用 Aspose.Words for .NET 為 Word .docx 加入自訂字型的對角文字浮水印的逐步程式碼。
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: 使用 Aspose.Words for .NET 為 Word .docx 加入自訂字型的對角文字浮水印的逐步程式碼。
  headline: 使用 Aspose.Words for .NET 在 Word 文件中建立自訂字型的對角文字浮水印
  type: TechArticle
- description: 使用 Aspose.Words for .NET 為 Word .docx 加入自訂字型的對角文字浮水印的逐步程式碼。
  name: 使用 Aspose.Words for .NET 在 Word 文件中建立自訂字型的對角文字浮水印
  steps:
  - name: 建立一個名為 `document` 的全新空白 Word 文件實例。
    text: 建立一個名為 `document` 的全新空白 Word 文件實例。
  - name: 將 `watermarkSettings` 設定為 Arial 48 點灰色字型、對角線版面配置，且以不透明方式呈現。
    text: 將 `watermarkSettings` 設定為 Arial 48 點灰色字型、對角線版面配置，且以不透明方式呈現。
  - name: 使用先前定義的設定，將文字浮水印「Private」套用至 `document`。
    text: 使用先前定義的設定，將文字浮水印「Private」套用至 `document`。
  - name: 定義要儲存浮水印文件的檔案路徑。
    text: 定義要儲存浮水印文件的檔案路徑。
  - name: 將已修改的 `document` 以 .docx 檔案儲存至指定路徑。
    text: 將已修改的 `document` 以 .docx 檔案儲存至指定路徑。
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` 決定浮水印是否以部分透明度呈現；設定為 `false` 時浮水印會完全不透明，設定為 `true`
      時則套用預設的半透明效果。'
    question: '`TextWatermarkOptions` 中的 **IsSemitrasparent** 旗標控制什麼？'
  - answer: 可以——在呼叫 `document.Watermark.SetText` 之前，將 `Layout` 屬性設為 `WatermarkLayout.Horizontal`（或其他列舉值）。
    question: 我可以將浮水印方向改為水平而非對角線嗎？
  - answer: Word 會退回使用預設字型作為浮水印，因此文字仍會顯示，但外觀可能與預期樣式不同。
    question: 如果指定的 `FontFamily`（例如「Arial」）未在目標機器上安裝，會發生什麼情況？
  - answer: 使用 `Document document = new Document("Existing.docx");` 載入既有檔案，然後如範例設定
      `TextWatermarkOptions` 並呼叫 `document.Watermark.SetText`。
    question: 是否可以在既有的 `.docx` 檔案上加入浮水印，而不是建立新檔案？
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: 加入自訂字型的對角文字浮水印
og_description: 學會在數分鐘內將自訂字型的斜向文字浮水印嵌入 Word 檔案。
og_image_alt: 指南說明如何使用 Aspose.Words for .NET 為 Word 文件加入自訂字型的對角文字浮水印
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文件中建立自訂字型的對角文字浮水印
本教學一步步帶領您建立全新 Word 文件、以您選擇的字型設定配置對角文字浮水印、透過 Document.Watermark.SetText API 套用，並將結果儲存為 .docx 檔案。完成後，您將擁有一份具專業浮水印的文件，可展示您的品牌或所有權。逐步程式碼已備妥，可直接複製到任何 .NET 專案中。

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: `TextWatermarkOptions` 中的 **IsSemitrasparent** 旗標控制什麼？**  
A: `IsSemitrasparent` 決定浮水印是否以部分透明度呈現；設定為 `false` 時浮水印會完全不透明，設定為 `true` 時則套用預設的半透明效果。

**Q: 我可以將浮水印方向改為水平而非對角線嗎？**  
A: 可以——在呼叫 `document.Watermark.SetText` 之前，將 `Layout` 屬性設為 `WatermarkLayout.Horizontal`（或其他列舉值）。

**Q: 如果指定的 `FontFamily`（例如「Arial」）未在目標機器上安裝，會發生什麼情況？**  
A: Word 會退回使用預設字型作為浮水印，因此文字仍會顯示，但外觀可能與預期樣式不同。

**Q: 是否可以在既有的 `.docx` 檔案上加入浮水印，而不是建立新檔案？**  
A: 使用 `Document document = new Document("Existing.docx");` 載入既有檔案，然後如範例設定 `TextWatermarkOptions` 並呼叫 `document.Watermark.SetText`。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}