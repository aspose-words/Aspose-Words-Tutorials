---
title: 使用 Aspose.Words for .NET 將對齊的 HTML 插入 Word 文件
weight: 210
limit:
description: 學習使用 Aspose.Words for .NET 將原始 HTML 以左、置中或右對齊方式插入 Word 文件。
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 將對齊的 HTML 插入 Word 文件
本互動式教學示範如何使用 Aspose.Words for .NET 將原始 HTML 嵌入 Word 文件，同時控制其對齊方式（左、置中或右）。透過 Document 與 DocumentBuilder，你只需幾行程式碼即可插入 HTML 字串並套用所需的段落對齊。當你需要保留 HTML 格式並將內容精確放置於文件中時，此範例非常適用。

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: 如果傳遞給 DocumentBuilder.InsertHtml 的 HTML 字串包含 Aspose.Words 不支援的標籤，例如 <script> 或 <iframe>，會發生什麼情況？**
A: 不支援的標籤會被忽略；Aspose.Words 只解析它能呈現的 HTML 子集，因此 <script>、<iframe> 以及類似元素會被剔除，而其餘內容則會被插入。

**Q: 使用 InsertHtml 時，內聯 CSS 樣式（例如 <span style=\"color:red;\">）會被保留嗎？**
A: 會，InsertHtml 會保留許多內聯 CSS 屬性，如 color、font‑size、background，並將它們轉換為相對應的 Word 格式。

**Q: InsertHtml 會自動為區塊級元素（例如 <div> 或 <h1>）建立新段落嗎？**
A: 區塊級元素會映射為 Word 段落，因此每個 <div>、<p>、<h1> 等都會成為文件中的獨立段落。

**Q: 如何在現有文件的特定位置插入 HTML，而不是在開頭插入？**
A: 在呼叫 InsertHtml 之前，先將 DocumentBuilder 游標移至目標節點（例如 builder.MoveToDocumentEnd() 或 builder.MoveToParagraph(index)），HTML 會插入到當前游標位置。

**Q: 如果文件已經包含文字，呼叫 InsertHtml 會覆寫現有內容嗎？**
A: 不會，InsertHtml 會將解析後的 HTML 插入到 builder 目前的位置，除非你事先明確將游標移入或刪除那些節點，否則不會刪除現有節點。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}