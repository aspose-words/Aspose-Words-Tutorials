---
title: 使用 Aspose.Words for .NET 在 Word 文档中插入水平线形状
weight: 110
limit:
description: 使用 Aspose.Words for .NET 将水平线形状插入 Word 文档的分步指南。
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文档中插入水平线形状
了解如何使用 Aspose.Words for .NET 将水平线形状插入 Word 文档。本教程将指导您创建新文档、添加一行文本、使用 DocumentBuilder 放置水平线形状并保存文件。水平线为您的内容提供了简单的视觉分隔。

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

**Q: 我可以更改使用 DocumentBuilder.InsertHorizontalRule() 插入的水平线的外观（颜色、粗细）吗？**
A: InsertHorizontalRule 会创建一个带有默认格式的内置水平线形状；若要修改其外观，必须获取插入的 Shape 对象（builder.CurrentParagraph.LastChild），并调整其 LineFormat 属性。

**Q: 如果在已经以换行结束的段落后调用 InsertHorizontalRule() 会怎样？**
A: 该方法会将水平线作为单独的段落插入，因此前面的换行只会在水平线前生成一个空段落；水平线仍会单独占一行显示。

**Q: 是否可以使用 DocumentBuilder 在同一文档中插入多个水平线？**
A: 可以，每次调用 builder.InsertHorizontalRule() 都会在当前光标位置添加一个新的水平线形状，从而在文档中插入多个水平线。

**Q: InsertHorizontalRule() 在将文档保存为除 DOCX 之外的格式（如 PDF）时是否有效？**
A: 水平线在文档模型中以 Shape 形式存储，因此保存为 PDF、XPS 或其他支持的格式时，水平线会在输出中正确渲染。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}