---
title: 使用 Aspose.Words for .NET 在 Word 文档中插入水平线形状
weight: 110
limit:
description: 学习使用 DocumentBuilder 和 Aspose.Words for .NET 向 Word 文档添加水平线形状。
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文档中插入水平线形状
在本教程中，您将学习如何使用 Aspose.Words for .NET 以编程方式在 Word 文档中插入水平线形状。通过使用 Document 和 DocumentBuilder 类，我们创建一个新文档，添加一段文本，然后在所需位置放置水平线形状。水平线可作为视觉分隔符，对章节分割或视觉强调非常有用。

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

**Q: `builder.InsertHorizontalRule()` 在文档中的确切插入位置是哪里？**
A: `InsertHorizontalRule` 会在 `DocumentBuilder` 的当前光标位置插入水平线形状；如果希望它单独占一行，请在插入前调用 `builder.Writeln()`。

**Q: 我可以更改插入的水平线的粗细、颜色或宽度吗？**
A: `InsertHorizontalRule` 添加的是默认样式的水平线，且不提供格式化选项；若要自定义这些属性，需要手动插入 `Shape`（例如 `builder.InsertShape(ShapeType.HorizontalLine)`），然后设置其 `LineFormat` 属性。

**Q: 是否可以在同一文档中添加多个水平线？**
A: 可以——每当需要新水平线时，只需调用 `builder.InsertHorizontalRule()`；每次调用都会在 builder 当前所在位置创建一个独立的形状。

**Q: 保存的 .docx 在 Microsoft Word 中打开时，水平线会显示吗？**
A: 当然会；水平线作为形状保存在 .docx 文件中，Word 会按生成文档中的样子准确显示。

**Q: 如果在调用 `doc.Save(...)` 之前 `dataDir` 文件夹不存在，会发生什么？**
A: `doc.Save` 会抛出 `DirectoryNotFoundException`；请确保目标目录存在，或在保存前通过代码创建它。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}