---
title: 使用 Aspose.Words for .NET 为 Word 文档的页脚添加页码
weight: 210
limit:
description: 使用 Aspose.Words for .NET 将自动更新的页码添加到 Word 文档的主页脚。
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: 使用 Aspose.Words for .NET 将自动更新的页码添加到 Word 文档的主页脚。
  headline: 使用 Aspose.Words for .NET 为 Word 文档的页脚添加页码
  type: TechArticle
- description: 使用 Aspose.Words for .NET 将自动更新的页码添加到 Word 文档的主页脚。
  name: 使用 Aspose.Words for .NET 为 Word 文档的页脚添加页码
  steps:
  - name: 创建一个新的 Document 对象以及与其关联的 DocumentBuilder。
    text: 创建一个新的 Document 对象以及与其关联的 DocumentBuilder。
  - name: 将 builder 的光标移动到第一节的主页脚。
    text: 将 builder 的光标移动到第一节的主页脚。
  - name: 将段落对齐方式设为居中，以使页脚文本居中显示。
    text: 将段落对齐方式设为居中，以使页脚文本居中显示。
  - name: 写入标签 "Page " 并插入一个显示当前页码的 PAGE 字段。
    text: 写入标签 "Page " 并插入一个显示当前页码的 PAGE 字段。
  - name: 写入 " of " 并插入一个显示总页数的 NUMPAGES 字段。
    text: 写入 " of " 并插入一个显示总页数的 NUMPAGES 字段。
  - name: 将文档保存为 .docx 文件。
    text: 将文档保存为 .docx 文件。
  type: HowTo
- questions:
  - answer: 不会。`MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` 只将 builder 移动到
      *第一* 节的主页脚，因此字段仅插入该页脚。
    question: 如果文档有多个节，此代码会在每个节的页脚中添加页码吗？
  - answer: 在写入字段之前，将 `builder.ParagraphFormat.Alignment` 设置为其他 `ParagraphAlignment`
      值（例如 `ParagraphAlignment.Right`）。
    question: 如何更改页脚中页码段落的对齐方式？
  - answer: '`InsertField` 接受字段代码和可选的字段结果；传入 `null` 表示让 Aspose.Words 在运行时由 Word 计算结果。'
    question: '`InsertField(\"PAGE\", null)` 中的 `null` 参数表示什么？'
  - answer: 可以——在插入字段之前，将 `HeaderFooterType.FooterPrimary` 替换为 `HeaderFooterType.HeaderPrimary`（或其他页眉类型）。
    question: 我可以将相同的 "Page X of Y" 字段放在页眉而不是页脚吗？
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: 在 Word 页脚中插入自动页码
og_description: 使用 Aspose.Words for .NET 的逐步代码，将实时页码添加到 Word 页脚。
og_image_alt: 指南展示了如何使用 Aspose.Words for .NET 为 Word 文档页脚添加自动页码
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 为 Word 文档的页脚添加页码
本教程展示了如何使用 Aspose.Words Document 和 DocumentBuilder 将自动更新的页码插入 Word 文档的主页脚。通过以编程方式添加页码，可确保整个文件的分页保持一致，而无需手动编辑。示例代码已准备好在 .NET 环境中运行。

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: 如果文档有多个节，此代码会在每个节的页脚中添加页码吗？**  
A: 不会。`MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` 只将 builder 移动到 *第一* 节的主页脚，因此字段仅插入该页脚。

**Q: 如何更改页脚中页码段落的对齐方式？**  
A: 在写入字段之前，将 `builder.ParagraphFormat.Alignment` 设置为其他 `ParagraphAlignment` 值（例如 `ParagraphAlignment.Right`）。

**Q: `InsertField(\"PAGE\", null)` 中的 `null` 参数表示什么？**  
A: `InsertField` 接受字段代码和可选的字段结果；传入 `null` 表示让 Aspose.Words 在运行时由 Word 计算结果。

**Q: 我可以将相同的 "Page X of Y" 字段放在页眉而不是页脚吗？**  
A: 可以——在插入字段之前，将 `HeaderFooterType.FooterPrimary` 替换为 `HeaderFooterType.HeaderPrimary`（或其他页眉类型）。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}