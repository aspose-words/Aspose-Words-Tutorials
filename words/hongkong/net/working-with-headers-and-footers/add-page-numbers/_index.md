---
title: 使用 Aspose.Words for .NET 為 Word 文件的頁腳加入頁碼。
weight: 210
limit:
description: 使用 Aspose.Words for .NET 為 Word 文件的主要頁腳加入自動更新的頁碼。
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: 使用 Aspose.Words for .NET 為 Word 文件的主要頁腳加入自動更新的頁碼。
  headline: 使用 Aspose.Words for .NET 為 Word 文件的頁腳加入頁碼。
  type: TechArticle
- description: 使用 Aspose.Words for .NET 為 Word 文件的主要頁腳加入自動更新的頁碼。
  name: 使用 Aspose.Words for .NET 為 Word 文件的頁腳加入頁碼。
  steps:
  - name: 建立一個新的 Document 物件，並建立與之關聯的 DocumentBuilder。
    text: 建立一個新的 Document 物件，並建立與之關聯的 DocumentBuilder。
  - name: 將 builder 的游標移至第一個節的主要頁腳。
    text: 將 builder 的游標移至第一個節的主要頁腳。
  - name: 將段落對齊方式設定為置中，使頁腳文字居中。
    text: 將段落對齊方式設定為置中，使頁腳文字居中。
  - name: 寫入標籤「Page 」並插入 PAGE 欄位，以顯示目前的頁碼。
    text: 寫入標籤「Page 」並插入 PAGE 欄位，以顯示目前的頁碼。
  - name: 寫入「 of 」並插入 NUMPAGES 欄位，以顯示總頁數。
    text: 寫入「 of 」並插入 NUMPAGES 欄位，以顯示總頁數。
  - name: 將文件儲存為 .docx 檔案。
    text: 將文件儲存為 .docx 檔案。
  type: HowTo
- questions:
  - answer: 不會。`MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` 只會將 builder 移至
      *第一* 個節的主要頁腳，因此欄位僅會插入於該處。
    question: 如果文件有多個節，這段程式碼會在每個節的頁腳加入頁碼嗎？
  - answer: 在寫入欄位之前，將 `builder.ParagraphFormat.Alignment` 設為其他 `ParagraphAlignment`
      值（例如 `ParagraphAlignment.Right`）。
    question: 如何變更頁腳中頁碼段落的對齊方式？
  - answer: '`InsertField` 需要欄位代碼以及可選的欄位結果；傳入 `null` 表示讓 Aspose.Words 交由 Word 在執行時計算結果。'
    question: '`InsertField("PAGE", null)` 中的 `null` 參數代表什麼？'
  - answer: 可以——在插入欄位之前，將 `HeaderFooterType.FooterPrimary` 替換為 `HeaderFooterType.HeaderPrimary`（或其他頁首類型）。
    question: 我可以將相同的「Page X of Y」欄位放在頁首而不是頁腳嗎？
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: 在 Word 頁腳插入自動頁碼。
og_description: 逐步程式碼示範，使用 Aspose.Words for .NET 為 Word 頁腳加入即時頁碼。
og_image_alt: 指南說明如何使用 Aspose.Words for .NET 為 Word 文件的頁腳加入自動頁碼。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 為 Word 文件的頁腳加入頁碼。
本教學說明如何使用 Aspose.Words 的 Document 與 DocumentBuilder，將自動更新的頁碼插入 Word 文件的主要頁腳。透過程式方式加入頁碼，可確保整個檔案的分頁一致，免除手動編輯。範例程式碼已可直接在 .NET 環境中執行。

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: 如果文件有多個節，這段程式碼會在每個節的頁腳加入頁碼嗎？**  
A: 不會。`MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` 只會將 builder 移至 *第一* 個節的主要頁腳，因此欄位僅會插入於該處。

**Q: 如何變更頁腳中頁碼段落的對齊方式？**  
A: 在寫入欄位之前，將 `builder.ParagraphFormat.Alignment` 設為其他 `ParagraphAlignment` 值（例如 `ParagraphAlignment.Right`）。

**Q: `InsertField("PAGE", null)` 中的 `null` 參數代表什麼？**  
A: `InsertField` 需要欄位代碼以及可選的欄位結果；傳入 `null` 表示讓 Aspose.Words 交由 Word 在執行時計算結果。

**Q: 我可以將相同的「Page X of Y」欄位放在頁首而不是頁腳嗎？**  
A: 可以——在插入欄位之前，將 `HeaderFooterType.FooterPrimary` 替換為 `HeaderFooterType.HeaderPrimary`（或其他頁首類型）。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}