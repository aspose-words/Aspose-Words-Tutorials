---
title: 使用 Aspose.Words for .NET 在 Word 文档的特定段落中插入 Comment。
weight: 210
limit:
description: 逐步指南：使用 Aspose.Words for .NET 向 Word 文档中选定的段落添加作者批注并保存为 DOCX。
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 逐步指南：使用 Aspose.Words for .NET 向 Word 文档中选定的段落添加作者批注并保存为 DOCX。
  headline: 使用 Aspose.Words for .NET 在 Word 文档的特定段落中插入 Comment。
  type: TechArticle
- description: 逐步指南：使用 Aspose.Words for .NET 向 Word 文档中选定的段落添加作者批注并保存为 DOCX。
  name: 使用 Aspose.Words for .NET 在 Word 文档的特定段落中插入 Comment。
  steps:
  - name: 实例化一个新的 Document 和 DocumentBuilder，以开始构建 Word 文件。
    text: 实例化一个新的 Document 和 DocumentBuilder，以开始构建 Word 文件。
  - name: 使用 DocumentBuilder.Writeln 向文档添加三个独立的文本段落。
    text: 使用 DocumentBuilder.Writeln 向文档添加三个独立的文本段落。
  - name: 安全地获取第二个段落，如果文档少于两个段落，则回退到第一个段落。
    text: 安全地获取第二个段落，如果文档少于两个段落，则回退到第一个段落。
  - name: 创建带有作者信息的 Comment，设置其文本，并将其附加到选定的段落。
    text: 创建带有作者信息的 Comment，设置其文本，并将其附加到选定的段落。
  - name: 将修改后的文档保存为当前文件夹下名为 'sample.docx' 的 DOCX 文件。
    text: 将修改后的文档保存为当前文件夹下名为 'sample.docx' 的 DOCX 文件。
  type: HowTo
- questions:
  - answer: 当 `paraList.Count` 小于 2 时，`if` 块会回退到第一个段落 (`paraList[0]`)，因此批注将附加到该唯一段落，而不是缺失的第二个段落。
    question: 如果文档只有一个段落，代码会怎么做？
  - answer: 它们作为第二和第三个参数传递给 `Comment` 构造函数——`new Comment(wordDoc, "Jordan", "JH",
      DateTime.Now)`——其中 "Jordan" 为作者姓名，"JH" 为缩写。
    question: 在此示例中，批注的作者姓名和缩写是如何设置的？
  - answer: 在此代码片段中，批注通过 `AppendChild` 链接到整个 `Paragraph`，但若要对文本范围进行批注，需要在目标 `Run`
      节点周围创建 `CommentRangeStart` 和 `CommentRangeEnd`，然后在它们之间添加 `Comment` 节点。
    question: 我可以将批注附加到特定文本片段，而不是整个段落吗？
  - answer: '`AppendChild` 将 `Comment` 节点添加到段落的子集合中，Aspose.Words 会在文档保存时自动生成所需的批注开始/结束标记。'
    question: 我需要手动插入批注标记吗，还是 `AppendChild` 会自动处理？
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: 在 Word 段落中插入批注
og_description: 向特定段落添加作者批注，并使用 Aspose.Words 将文件导出为 DOCX。
og_image_alt: 指南：展示如何使用 Aspose.Words for .NET 向 Word 文档的段落添加批注
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文档的特定段落中插入 Comment。
使用 Aspose.Words for .NET，您可以以编程方式向 Word 文件添加批注。本教程演示了创建新文档、插入三个段落、定位第二个段落，并附加包含作者和日期信息的批注。最后，文档以保留批注的方式保存为 DOCX 文件。

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: 如果文档只有一个段落，代码会怎么做？**  
A: 当 `paraList.Count` 小于 2 时，`if` 块会回退到第一个段落 (`paraList[0]`)，因此批注将附加到该唯一段落，而不是缺失的第二个段落。

**Q: 在此示例中，批注的作者姓名和缩写是如何设置的？**  
A: 它们作为第二和第三个参数传递给 `Comment` 构造函数——`new Comment(wordDoc, "Jordan", "JH", DateTime.Now)`——其中 "Jordan" 为作者姓名，"JH" 为缩写。

**Q: 我可以将批注附加到特定文本片段，而不是整个段落吗？**  
A: 在此代码片段中，批注通过 `AppendChild` 链接到整个 `Paragraph`，但若要对文本范围进行批注，需要在目标 `Run` 节点周围创建 `CommentRangeStart` 和 `CommentRangeEnd`，然后在它们之间添加 `Comment` 节点。

**Q: 我需要手动插入批注标记吗，还是 `AppendChild` 会自动处理？**  
A: `AppendChild` 将 `Comment` 节点添加到段落的子集合中，Aspose.Words 会在文档保存时自动生成所需的批注开始/结束标记。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}