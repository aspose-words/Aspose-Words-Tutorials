---
title: 使用 Aspose.Words for .NET 在 Word 文档中插入 TC 字段
weight: 110
limit:
description: 了解如何使用 Aspose.Words for .NET 向 Word 文档插入带自定义文本的 TC 字段。
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文档中插入 TC 字段
本教程展示了如何使用 Aspose.Words for .NET 将 TC（目录）字段插入新建的 Word 文档。通过使用 DocumentBuilder，您可以添加带自定义条目文本的 TC 字段，这对于构建目录的可搜索索引非常有用。示例还演示了将文档保存到磁盘。

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


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

**Q: TC 字段代码中的 "\f t" 开关是什么意思？**
A: "\f t" 开关指示 Word 将该条目视为表格条目，从而使其出现在使用 \f 开关生成的目录中。

**Q: 如何更改 TC 字段中显示的文本？**
A: 将 InsertField 调用中的 "Entry Text" 替换为任意字符串，例如：builder.InsertField("TC \"Chapter 1\" \f t");

**Q: 我可以在同一文档中插入多个 TC 字段吗？**
A: 可以；只需在保存文档前，在所需位置使用不同的条目文本调用 builder.InsertField 即可。

**Q: 此代码是否适用于除 .docx 之外的其他格式，例如 .pdf？**
A: 示例中将文档保存为 .docx，但 Aspose.Words 可以通过在 doc.Save 中更改文件扩展名并确保支持相应的输出格式，将文档保存为其他格式（例如 .pdf）。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}