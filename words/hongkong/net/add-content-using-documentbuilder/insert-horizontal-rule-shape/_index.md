---
title: 使用 Aspose.Words for .NET 在 Word 文件中插入水平線形狀
weight: 110
limit:
description: 逐步指南：使用 Aspose.Words for .NET 在 Word 文件中插入水平線形狀。
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文件中插入水平線形狀
了解如何使用 Aspose.Words for .NET 在 Word 文件中插入水平線形狀。本教學將帶領您建立新文件、加入一行文字、使用 DocumentBuilder 放置水平線形狀，並儲存檔案。水平線可為您的內容提供簡單的視覺分隔。

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: 我可以變更使用 DocumentBuilder.InsertHorizontalRule() 插入的水平線外觀（顏色、粗細）嗎？**
A: InsertHorizontalRule 會建立具預設格式的內建水平線形狀；若要修改其外觀，必須取得插入的 Shape 物件（builder.CurrentParagraph.LastChild）並調整其 LineFormat 屬性。

**Q: 如果在已以換行結尾的段落之後呼叫 InsertHorizontalRule()，會發生什麼情況？**
A: 此方法會將水平線作為獨立段落插入，因此前面的換行只會在水平線前產生一個空白段落；水平線仍會單獨顯示在一行上。

**Q: 是否可以使用 DocumentBuilder 在同一文件中插入多個水平線？**
A: 可以，對 builder.InsertHorizontalRule() 的每一次呼叫都會在目前游標位置加入新的水平線形狀，讓文件中可出現多個水平線。

**Q: InsertHorizontalRule() 在將文件儲存為除 DOCX 之外的格式（例如 PDF）時是否仍然有效？**
A: 水平線以 Shape 形式儲存在文件模型中，因此在儲存為 PDF、XPS 或其他支援的格式時，水平線會正確呈現在輸出檔案中。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}