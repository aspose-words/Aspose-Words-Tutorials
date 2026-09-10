---
title: 使用 Aspose.Words for .NET 将对齐的 HTML 插入 Word 文档
weight: 210
limit:
description: 学习使用 Aspose.Words for .NET 将原始 HTML 以左、居中或右对齐方式插入 Word 文档。
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 将对齐的 HTML 插入 Word 文档
本交互式教程展示了如何使用 Aspose.Words for .NET 将原始 HTML 嵌入到 Word 文档中并控制其对齐方式（左对齐、居中或右对齐）。通过利用 Document 和 DocumentBuilder，您可以在几行代码内插入 HTML 字符串并应用所需的段落对齐。该示例非常适合在需要保留 HTML 格式并将内容精确放置在文档中的场景。

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

**Q: 如果传递给 DocumentBuilder.InsertHtml 的 HTML 字符串包含 Aspose.Words 不支持的标签，例如 <script> 或 <iframe>，会发生什么？**
A: 不支持的标签会被忽略；Aspose.Words 只解析它能够渲染的 HTML 子集，因此 <script>、<iframe> 等类似元素会被剥离，而其余内容会被插入。

**Q: 使用 InsertHtml 时，内联 CSS 样式（例如 <span style\="color:red;\">）会被保留吗？**
A: 是的，InsertHtml 会尊重许多内联 CSS 属性，如 color、font‑size 和 background，并将其转换为相应的 Word 格式。

**Q: InsertHtml 会为块级元素（如 <div> 或 <h1>）自动创建新段落吗？**
A: 块级元素会映射为 Word 段落，因此每个 <div>、<p>、<h1> 等都会在文档中成为单独的段落。

**Q: 如何在现有文档的特定位置插入 HTML，而不是在开头插入？**
A: 在调用 InsertHtml 之前，将 DocumentBuilder 的光标移动到目标节点（例如 builder.MoveToDocumentEnd() 或 builder.MoveToParagraph(index)），HTML 将插入到当前光标位置。

**Q: 如果文档已经包含文本，调用 InsertHtml 会覆盖已有内容吗？**
A: 不会，InsertHtml 会在 builder 当前所在位置插入解析后的 HTML，除非您事先显式移动光标到这些节点或删除它们，否则不会删除已有节点。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}