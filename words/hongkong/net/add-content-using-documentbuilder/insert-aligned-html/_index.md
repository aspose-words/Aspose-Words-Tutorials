---
title: 使用 Aspose.Words for .NET 在 Word 文件中插入對齊的 HTML
weight: 210
limit:
description: 了解如何使用 Aspose.Words for .NET 在 Word 文件中插入具有特定對齊方式的 HTML。
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文件中插入對齊的 HTML
本教學示範如何使用 Aspose.Words for .NET 的 DocumentBuilder 將 HTML 標記嵌入 Word 文件並控制其對齊方式。您將看到如何插入 HTML、設定段落對齊（左、置中或右），以及儲存最終文件。此範例特別適合需要在程式產生 Word 檔時保留網頁樣式格式的開發人員。

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

**Q: InsertHtml 能否用於將 HTML 加入已存在的 Word 文件，而不是新文件？**
A: 可以。先以現有檔案建立 Document，將 DocumentBuilder 游標移至欲插入 HTML 的位置（例如使用 builder.MoveToDocumentEnd()），然後呼叫 builder.InsertHtml 並傳入您的標記。

**Q: InsertHtml 在對齊方面會遵循哪些 HTML 屬性？**
A: InsertHtml 會遵守區塊級元素（如 <p>、<div> 以及標題標籤）上的 "align" 屬性，並在產生的 Word 文件中套用相應的段落對齊。

**Q: 如果 HTML 字串包含不支援的標籤或 CSS，會發生什麼情況？**
A: 不支援的標籤會被忽略，其內部文字會以純文字形式插入；Aspose.Words 無法辨識的行內 CSS 樣式亦會被忽略，僅會呈現支援的 HTML 子集。

**Q: 在儲存文件之前需要關閉 DocumentBuilder 嗎？**
A: 不需要額外關閉；插入 HTML 後即可直接呼叫 doc.Save 並指定檔名與格式，builder 的資源會自動釋放。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}