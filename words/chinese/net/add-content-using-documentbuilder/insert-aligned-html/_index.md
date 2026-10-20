---
title: 使用 Aspose.Words for .NET 将对齐的 HTML 插入 Word 文档
weight: 210
limit:
description: 了解如何使用 Aspose.Words for .NET 将具有特定对齐方式的 HTML 插入 Word 文档。
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 将对齐的 HTML 插入 Word 文档
本教程演示如何使用 Aspose.Words for .NET 的 DocumentBuilder 将 HTML 标记嵌入 Word 文档并控制其对齐方式。您将看到如何插入 HTML、设置段落对齐（左、居中或右），以及随后保存生成的文档。该示例非常适合需要在程序化生成 Word 文件时保留网页样式格式的开发者。

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

**Q: InsertHtml 能否用于将 HTML 添加到已有的 Word 文档，而不是新建文档？**  
A: 可以。先从已有文件创建 Document，将 DocumentBuilder 的光标定位到希望插入 HTML 的位置（例如使用 builder.MoveToDocumentEnd()），然后调用 builder.InsertHtml 并传入您的标记。

**Q: InsertHtml 对对齐支持哪些 HTML 属性？**  
A: InsertHtml 会遵循块级元素（如 &lt;p&gt;、&lt;div&gt; 和标题标签）上的 "align" 属性，并在生成的 Word 文档中应用相应的段落对齐方式。

**Q: 如果 HTML 字符串包含不受支持的标签或 CSS，会发生什么？**  
A: 不受支持的标签会被忽略，其内部文本会以纯文本形式插入；Aspose.Words 未识别的内联 CSS 样式也会被忽略，因此仅渲染受支持的 HTML 子集。

**Q: 在保存文档之前是否需要关闭 DocumentBuilder？**  
A: 无需显式关闭；在插入 HTML 后，您可以直接调用 doc.Save 并指定文件名和格式，builder 的资源会自动释放。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}