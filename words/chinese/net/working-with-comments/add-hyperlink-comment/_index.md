---
title: 使用 Aspose.Words for .NET 添加超链接批注并导出为 PDF 注释
weight: 110
limit:
description: 学习在 Word 文件中添加超链接批注，并使用 Aspose.Words for .NET 将其导出为 PDF 注释。
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 学习在 Word 文件中添加超链接批注，并使用 Aspose.Words for .NET 将其导出为 PDF 注释。
  headline: 使用 Aspose.Words for .NET 添加超链接批注并导出为 PDF 注释
  type: TechArticle
- description: 学习在 Word 文件中添加超链接批注，并使用 Aspose.Words for .NET 将其导出为 PDF 注释。
  name: 使用 Aspose.Words for .NET 添加超链接批注并导出为 PDF 注释
  steps:
  - name: 创建一个新的空 Document 对象，并创建一个 DocumentBuilder 来对其进行操作。
    text: 创建一个新的空 Document 对象，并创建一个 DocumentBuilder 来对其进行操作。
  - name: 写入一行可见文本，以容纳即将添加的批注。
    text: 写入一行可见文本，以容纳即将添加的批注。
  - name: 创建一个作者为 Jane Doe 的 Comment，并将其附加到文档的第一段。
    text: 创建一个作者为 Jane Doe 的 Comment，并将其附加到文档的第一段。
  - name: 在该 Comment 中，添加一个段落，并插入指向 Aspose.Words Library 网站的蓝色下划线超链接。
    text: 在该 Comment 中，添加一个段落，并插入指向 Aspose.Words Library 网站的蓝色下划线超链接。
  - name: 配置文档将 Comment 渲染为 PDF 注释，并刷新布局。
    text: 配置文档将 Comment 渲染为 PDF 注释，并刷新布局。
  - name: 在当前目录下创建一个名为 "Output" 的文件夹，用于存放生成的 PDF。
    text: 在当前目录下创建一个名为 "Output" 的文件夹，用于存放生成的 PDF。
  - name: 使用 PdfSaveOptions 将准备好的文档保存为 PDF 文件。
    text: 使用 PdfSaveOptions 将准备好的文档保存为 PDF 文件。
  - name: 检查 PDF 文件是否存在且包含数据，然后将结果输出到控制台。
    text: 检查 PDF 文件是否存在且包含数据，然后将结果输出到控制台。
  type: HowTo
- questions:
  - answer: '`InsertHyperlink` 的第三个参数指定链接是否应被视为字段；将其设为 `false` 会插入普通超链接，在 PDF 注释中可直接使用，无需字段代码。'
    question: '`InsertHyperlink` 中的第三个参数 (`false`) 控制什么？'
  - answer: 在调用 `Save` 之前，将 `myDocument.LayoutOptions.CommentDisplayMode` 设置为 `CommentDisplayMode.ShowInBalloons`；这样生成的
      PDF 将把批注保留为普通的 Word 批注，而不是注释。
    question: 如何让批注在 Word 文档中以气泡形式显示，而不是作为 PDF 注释？
  - answer: 是的——您向段落追加的每个 `Comment` 都可以包含各自的 `InsertHyperlink` 调用，所有超链接在文档保存为 PDF
      时都会被保留为独立的 PDF 注释。
    question: 如果我添加多个批注，导出的 PDF 中每个超链接都会正常工作吗？
  - answer: 打开生成的 PDF，定位批注注释（通常显示为便签图标），点击以展开批注文本，然后点击蓝色下划线链接；它应在网页浏览器中打开目标 URL。
    question: 如何验证生成的 PDF 中批注内的超链接实际可用？
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: 插入超链接批注并导出为 PDF
og_description: 学习在 Word 批注中嵌入可点击链接并将其转换为 PDF 注释。
og_image_alt: 指南展示如何向 Word 文档添加带可点击超链接的批注，并使用 Aspose.Words for .NET 将其导出为 PDF 注释
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 添加超链接批注并导出为 PDF 注释
在本教程中，您将了解如何创建 Word 文档，插入包含指向外部网站的可点击超链接的批注，配置该批注在 PDF 中显示为注释，导出文档为 PDF，并验证生成的 PDF 文件。一步一步的代码示例让您能够添加富文本、带链接的批注，并在转换为 PDF 时保留它们，从而轻松与读者共享交互式注释。

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: `InsertHyperlink` 中的第三个参数 (`false`) 控制什么？**  
A: `InsertHyperlink` 的第三个参数指定链接是否应被视为字段；将其设为 `false` 会插入普通超链接，在 PDF 注释中可直接使用，无需字段代码。

**Q: 如何让批注在 Word 文档中以气泡形式显示，而不是作为 PDF 注释？**  
A: 在调用 `Save` 之前，将 `myDocument.LayoutOptions.CommentDisplayMode` 设置为 `CommentDisplayMode.ShowInBalloons`；这样生成的 PDF 将把批注保留为普通的 Word 批注，而不是注释。

**Q: 如果我添加多个批注，导出的 PDF 中每个超链接都会正常工作吗？**  
A: 是的——您向段落追加的每个 `Comment` 都可以包含各自的 `InsertHyperlink` 调用，所有超链接在文档保存为 PDF 时都会被保留为独立的 PDF 注释。

**Q: 如何验证生成的 PDF 中批注内的超链接实际可用？**  
A: 打开生成的 PDF，定位批注注释（通常显示为便签图标），点击以展开批注文本，然后点击蓝色下划线链接；它应在网页浏览器中打开目标 URL。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}