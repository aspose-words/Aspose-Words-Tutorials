---
title: 使用 Aspose.Words for .NET 在 Word 文件中建立旋轉文字表格
weight: 110
limit:
description: 學習使用 Aspose.Words for .NET 建立具有固定欄寬、旋轉文字、精確列高以及已填入內容的 Word 表格。
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: 學習使用 Aspose.Words for .NET 建立具有固定欄寬、旋轉文字、精確列高以及已填入內容的 Word 表格。
  headline: 使用 Aspose.Words for .NET 在 Word 文件中建立旋轉文字表格
  type: TechArticle
- description: 學習使用 Aspose.Words for .NET 建立具有固定欄寬、旋轉文字、精確列高以及已填入內容的 Word 表格。
  name: 使用 Aspose.Words for .NET 在 Word 文件中建立旋轉文字表格
  steps:
  - name: 建立一個新的 Document 以及用於構建表格的 DocumentBuilder。
    text: 建立一個新的 Document 以及用於構建表格的 DocumentBuilder。
  - name: 開始建立新表格，插入第一個儲存格，並固定欄寬，使其不會自動調整。
    text: 開始建立新表格，插入第一個儲存格，並固定欄寬，使其不會自動調整。
  - name: 在目前儲存格中垂直置中內容，並寫入第一列第一個儲存格的文字。
    text: 在目前儲存格中垂直置中內容，並寫入第一列第一個儲存格的文字。
  - name: 插入第一列的第二個儲存格，並寫入其文字。
    text: 插入第一列的第二個儲存格，並寫入其文字。
  - name: 結束第一列，完成其版面配置。
    text: 結束第一列，完成其版面配置。
  - name: 開始第二列的第一個儲存格，將列高設定為正好 100 點，文字向上旋轉，並寫入儲存格文字。
    text: 開始第二列的第一個儲存格，將列高設定為正好 100 點，文字向上旋轉，並寫入儲存格文字。
  - name: 插入第二列的第二個儲存格，將文字向下旋轉，並寫入儲存格文字。
    text: 插入第二列的第二個儲存格，將文字向下旋轉，並寫入儲存格文字。
  - name: 結束第二列，完成表格的第二行。
    text: 結束第二列，完成表格的第二行。
  - name: 結束表格建構，封存表格結構。
    text: 結束表格建構，封存表格結構。
  - name: 將完成的文件儲存為 .docx 檔案。
    text: 將完成的文件儲存為 .docx 檔案。
  type: HowTo
- questions:
  - answer: 固定欄寬後，於插入下一個儲存格前使用 `builder.CellFormat.Width = <valueInPoints>;` 為每個儲存格指定寬度；表格會保留這些精確的寬度。
    question: 在呼叫 `table.AutoFit(AutoFitBehavior.FixedColumnWidths)` 後，我該如何設定特定的欄寬？
  - answer: '`builder.CellFormat.VerticalAlignment` 為儲存格層級的設定，因此在寫入第二列儲存格內容之前，需要再次為該列的儲存格設定（例如
      `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`）。'
    question: 為什麼垂直對齊只影響第一列，而不影響第二列？
  - answer: 可以——在每次呼叫 `builder.EndRow();` 之前，設定 `builder.RowFormat.Height` 並將 `builder.RowFormat.HeightRule
      = HeightRule.Exactly`，如此即可為下一列指定不同的高度值。
    question: 我可以為每一列設定不同的精確高度嗎？如果可以，要如何做到？
  - answer: 在寫入下一個儲存格前，將 `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      指定回水平，即可重設文字方向。
    question: 在使用 `TextOrientation.Upward` 或 `Downward` 後，如何將文字方向恢復為預設？
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: 使用 Aspose.Words 在 Word 中建立旋轉文字表格
og_description: 一步一步的程式碼示範，建立固定欄寬、文字垂直旋轉且列高精確的表格。
og_image_alt: 螢幕截圖顯示使用 Aspose.Words for .NET 建立的 Word 文件，其中的表格具備固定欄寬、儲存格內旋轉文字以及已定義的列高。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文件中建立旋轉文字表格
本教學說明如何產生 Word 文件並加入一個欄寬固定、列高精確且儲存格文字垂直旋轉的表格。您將學會設定垂直對齊、套用文字方向、為每個儲存格填入內容，最後儲存文件——全部使用 Aspose.Words for .NET。

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: 在呼叫 `table.AutoFit(AutoFitBehavior.FixedColumnWidths)` 後，我該如何設定特定的欄寬？**  
A: 固定欄寬後，於插入下一個儲存格前使用 `builder.CellFormat.Width = <valueInPoints>;` 為每個儲存格指定寬度；表格會保留這些精確的寬度。

**Q: 為什麼垂直對齊只影響第一列，而不影響第二列？**  
A: `builder.CellFormat.VerticalAlignment` 為儲存格層級的設定，因此在寫入第二列儲存格內容之前，需要再次為該列的儲存格設定（例如 `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`）。

**Q: 我可以為每一列設定不同的精確高度嗎？如果可以，要如何做到？**  
A: 可以——在每次呼叫 `builder.EndRow();` 之前，設定 `builder.RowFormat.Height` 並將 `builder.RowFormat.HeightRule = HeightRule.Exactly`，如此即可為下一列指定不同的高度值。

**Q: 在使用 `TextOrientation.Upward` 或 `Downward` 後，如何將文字方向恢復為預設？**  
A: 在寫入下一個儲存格前，將 `builder.CellFormat.Orientation = TextOrientation.Horizontal;` 指定回水平，即可重設文字方向。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}