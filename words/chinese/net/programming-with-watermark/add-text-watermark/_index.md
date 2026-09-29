---
title: 使用 Aspose.Words for .NET 为 Word 文档添加红色对角线文字水印
weight: 110
limit:
description: 使用 Aspose.Words for .NET 自动为批量生成的每个 Word 文件添加红色对角线文字水印。
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: 使用 Aspose.Words for .NET 自动为批量生成的每个 Word 文件添加红色对角线文字水印。
  headline: 使用 Aspose.Words for .NET 为 Word 文档添加红色对角线文字水印
  type: TechArticle
- description: 使用 Aspose.Words for .NET 自动为批量生成的每个 Word 文件添加红色对角线文字水印。
  name: 使用 Aspose.Words for .NET 为 Word 文档添加红色对角线文字水印
  steps:
  - name: 创建 "GeneratedReports" 文件夹，用于保存输出文件。
    text: 创建 "GeneratedReports" 文件夹，用于保存输出文件。
  - name: 启动一个循环，生成三个独立的文档。
    text: 启动一个循环，生成三个独立的文档。
  - name: 创建一个新的空 Word 文档对象。
    text: 创建一个新的空 Word 文档对象。
  - name: 使用 DocumentBuilder 在文档中写入标题行和描述。
    text: 使用 DocumentBuilder 在文档中写入标题行和描述。
  - name: 定义水印的外观，包括字体、大小、颜色和对角布局。
    text: 定义水印的外观，包括字体、大小、颜色和对角布局。
  - name: 将配置好的红色对角线水印（文本为 "PROTECTED"）应用到文档中。
    text: 将配置好的红色对角线水印（文本为 "PROTECTED"）应用到文档中。
  - name: 将带水印的文档以唯一文件名保存到 "GeneratedReports" 文件夹。
    text: 将带水印的文档以唯一文件名保存到 "GeneratedReports" 文件夹。
  - name: 处理完当前文档后关闭循环。
    text: 处理完当前文档后关闭循环。
  type: HowTo
- questions:
  - answer: IsSemitrasparent 决定水印是否以部分不透明度渲染；设置为 **true** 时，文字会半透明，从而使底层内容更易阅读。
    question: '**IsSemitrasparent** 选项控制什么？将其设置为 **true** 会有什么效果？'
  - answer: 可以——在调用 **document.Watermark.SetText** 之前，将 **TextWatermarkOptions** 的
      **Layout** 属性设为 **WatermarkLayout.Horizontal**。
    question: 我可以将水印方向改为水平而不是对角线吗？
  - answer: 该代码片段创建了一个全新的 **Document** 实例，但你可以打开任何已有文件（例如 `new Document("Existing.docx")`），随后调用
      **document.Watermark.SetText** 来应用相同的水印。
    question: 这段代码是给已有的 Word 文件添加水印，还是仅针对新创建的文档？
  - answer: 使用 **Color.FromArgb(red, green, blue)** 为 **TextWatermarkOptions** 的 **Color**
      属性分配自定义颜色，例如 `Color = Color.FromArgb(128, 0, 128)` 可得到紫色。
    question: 如何使用自定义 RGB 颜色而不是预定义的 **Color.Red** 来设置水印？
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: 为 Word 文档添加红色对角线文字水印
og_description: 了解如何使用 Aspose.Words 在批量处理中自动为每个 Word 文档应用红色对角线水印。
og_image_alt: 指南：展示如何使用 Aspose.Words for .NET 为 Word 文档添加红色对角线文字水印
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 为 Word 文档添加红色对角线文字水印
本教程演示了如何在批量报告生成过程中，自动将红色对角线文字水印嵌入每个创建的 Word 文档。通过使用 Aspose.Words for .NET 的 Document 和 DocumentBuilder 类，水印在文件生成时以编程方式应用，确保每个文档都携带相同的品牌或保密声明，无需人工操作。

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: **IsSemitrasparent** 选项控制什么？将其设置为 **true** 会有什么效果？**  
A: IsSemitrasparent 决定水印是否以部分不透明度渲染；设置为 **true** 时，文字会半透明，从而使底层内容更易阅读。

**Q: 我可以将水印方向改为水平而不是对角线吗？**  
A: 可以——在调用 **document.Watermark.SetText** 之前，将 **TextWatermarkOptions** 的 **Layout** 属性设为 **WatermarkLayout.Horizontal**。

**Q: 这段代码是给已有的 Word 文件添加水印，还是仅针对新创建的文档？**  
A: 该代码片段创建了一个全新的 **Document** 实例，但你可以打开任何已有文件（例如 `new Document("Existing.docx")`），随后调用 **document.Watermark.SetText** 来应用相同的水印。

**Q: 如何使用自定义 RGB 颜色而不是预定义的 **Color.Red** 来设置水印？**  
A: 使用 **Color.FromArgb(red, green, blue)** 为 **TextWatermarkOptions** 的 **Color** 属性分配自定义颜色，例如 `Color = Color.FromArgb(128, 0, 128)` 可得到紫色。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}