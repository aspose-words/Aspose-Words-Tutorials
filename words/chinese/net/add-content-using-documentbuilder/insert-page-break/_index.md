---
title: 使用 Aspose.Words for .NET 在 Word 文档中插入分页符
weight: 110
limit:
description: 学习使用 Aspose.Words for .NET 的 Document 和 DocumentBuilder 向 Word 文件添加分页符。
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文档中插入分页符
在本交互式教程中，您将学习如何使用 Aspose.Words for .NET 以编程方式向 Word 文档添加分页符。通过创建 Document 对象并使用 DocumentBuilder，您可以控制新页面的起始位置，这对于格式化报告、发票或任何多节文档至关重要。按照逐步示例查看代码运行效果并预览生成的文件。

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-page-break" >}}


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

**Q: 我可以使用 InsertBreak 添加换行符或节分隔符，而不是分页符吗？**
A: 是的，InsertBreak 接受任何 BreakType 枚举值，例如 BreakType.LineBreak 或 BreakType.SectionBreakContinuous，以插入相应的分隔符。

**Q: 我需要在写入新页面的文本之前还是之后调用 InsertBreak？**
A: InsertBreak 应在当前页面的内容之后调用；随后调用的 Writeln 将在分页符创建的新页面上开始。

**Q: 如果 dataDir 路径没有以目录分隔符结尾，会发生什么？**
A: 如果 dataDir 缺少结尾的斜杠，文件名将直接拼接（例如 "C:\\DocsAddContentUsingDocumentBuilder.InsertBreak.docx"），可能导致路径无效；请确保路径以 "\\" 结尾或使用 Path.Combine。

**Q: 我可以重复使用同一个 DocumentBuilder 实例在文档中插入多个分页符吗？**
A: 可以，同一个 DocumentBuilder 可以重复使用；每次调用 InsertBreak 都会在构建器当前光标位置插入一个分隔符。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}