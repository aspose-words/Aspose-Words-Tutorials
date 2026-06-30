---
category: general
date: 2026-06-30
description: 在 C# 中将文档保存为 PDF，同时将 docx 转换为 PDF 并处理内联形状。请按照此分步指南正确导出 Word 为 PDF。
draft: false
keywords:
- save document as pdf
- convert docx to pdf
- convert word to pdf
- save word as pdf
- how to export inline
language: zh
og_description: 使用 Aspose.Words 在 C# 中将文档保存为 PDF。了解如何将 docx 转换为 PDF 并将浮动形状导出为内联元素。
og_title: 在 C# 中将文档保存为 PDF – 导出内联形状
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Save document as PDF in C# while converting docx to PDF and handling
    inline shapes. Follow this step‑by‑step guide to export Word to PDF correctly.
  headline: Save Document as PDF in C# – Export Inline Shapes
  type: TechArticle
- description: Save document as PDF in C# while converting docx to PDF and handling
    inline shapes. Follow this step‑by‑step guide to export Word to PDF correctly.
  name: Save Document as PDF in C# – Export Inline Shapes
  steps:
  - name: '**.NET 6+** (or .NET Framework 4.6+).'
    text: '**.NET 6+** (or .NET Framework 4.6+).'
  - name: The **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`).
    text: The **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`).
  - name: A sample `input.docx` that contains at least one floating picture or text
      box.
    text: A sample `input.docx` that contains at least one floating picture or text
      box.
  type: HowTo
tags:
- C#
- PDF
- Aspose.Words
title: 在 C# 中将文档保存为 PDF – 导出内联形状
url: /zh/net/programming-with-pdfsaveoptions/save-document-as-pdf-in-c-export-inline-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中将文档保存为 PDF – 导出内联形状

是否曾想过如何直接在 C# 中 **save document as PDF** 而不丢失浮动图像的布局？你并不是唯一遇到这种情况的人。许多开发者在 Word 文件包含浮动在文本上方的图片或文本框时会遇到麻烦——当你仅仅调用 `doc.Save("output.pdf")` 时，这些元素常常会消失或移动。  

在本教程中，我们将逐步演示如何 **convert docx to pdf**，同时将这些浮动对象保留为内联元素，从而有效回答 *how to export inline* shapes。完成后，你将拥有一个可直接运行的代码片段，能够 **save word as pdf** 如你所期望的那样。

## 你将学到

- 使用 Aspose.Words（或任何兼容的库）加载 `.docx` 文件。  
- 配置 `PdfSaveOptions` 使浮动形状转换为内联。  
- 执行保存操作以 **convert word to pdf**。  
- 处理常见的陷阱，如缺失字体或大图像。  

无需外部工具，也不需要手动操作 Word‑automation COM 对象——只需干净、纯粹的 C# 代码。

## 前提条件

在深入之前，请确保你具备以下条件：

1. **.NET 6+**（或 .NET Framework 4.6+）。  
2. **Aspose.Words for .NET** NuGet 包 (`Install-Package Aspose.Words`)。  
3. 一个包含至少一个浮动图片或文本框的示例 `input.docx`。  

如果你使用的是其他 PDF 库，概念保持不变——寻找类似 `ExportFloatingShapesAsInlineTag` 的属性。

## 步骤 1：加载源文档 – Save Document as PDF 基础  

首先要把 Word 文件加载到内存中。这就是 **save document as pdf** 过程真正开始的地方。

```csharp
using Aspose.Words;

// Step 1: Load the source DOCX file
string inputPath = @"C:\MyDocs\input.docx";
Document doc = new Document(inputPath);
```

*为什么这很重要*：加载文档会验证文件是否存在并解析其所有部分（样式、图像、页眉）。如果加载失败，后续的 PDF 转换将永远不会执行，因此在此捕获错误可以为你节省大量调试时间。

## 步骤 2：配置 PDF 保存选项 – 如何导出内联形状  

现在我们告诉库如何处理浮动形状。关键标志是 `ExportFloatingShapesAsInlineTag`。将其设为 `true` 会强制所有浮动图片或文本框以 **inline** 方式渲染，就像普通段落中的文本一样。

```csharp
// Step 2: Prepare PDF save options
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    // true → inline (text‑flow); false → keep as block‑level floating objects
    ExportFloatingShapesAsInlineTag = true,

    // Optional: improve compatibility with older PDF viewers
    Compliance = PdfCompliance.PdfA1b
};
```

*为什么这很重要*：默认情况下，Aspose.Words 会保持浮动形状的原始位置，这可能导致它们在生成的 PDF 中被裁剪或丢失。启用内联导出可确保形状成为文本流的一部分，保持在所有 PDF 阅读器中的视觉一致性。

## 步骤 3：将文档保存为 PDF – Convert Word to PDF  

在文档已加载且选项已设置后，最后一步是一行代码，实际执行 **save document as pdf**。

```csharp
// Step 3: Save the document as a PDF file
string outputPath = @"C:\MyDocs\FloatingShapes.pdf";
doc.Save(outputPath, pdfOptions);
```

就这样！`doc.Save` 调用会生成一个与原始 Word 布局相匹配的 PDF，浮动图像现在整齐地嵌入文本中。

## 完整工作示例  

将所有内容整合在一起，下面是一个可自行复制、编译并运行的完整控制台应用程序示例：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToPdfInlineExport
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\MyDocs\input.docx";
            string outputPath = @"C:\MyDocs\FloatingShapes.pdf";

            // Load the DOCX file
            Document doc = new Document(inputPath);

            // Configure PDF options to export floating shapes as inline
            PdfSaveOptions pdfOptions = new PdfSaveOptions
            {
                ExportFloatingShapesAsInlineTag = true,
                Compliance = PdfCompliance.PdfA1b // optional, ensures PDF/A‑1b compliance
            };

            // Save as PDF
            doc.Save(outputPath, pdfOptions);

            Console.WriteLine($"Document successfully saved as PDF: {outputPath}");
        }
    }
}
```

**预期输出**（在控制台中）：

```
Document successfully saved as PDF: C:\MyDocs\FloatingShapes.pdf
```

在任意查看器中打开 `FloatingShapes.pdf`；你会看到之前浮动的图片现在已紧密嵌入段落中，正如预期。

## 为什么将浮动形状导出为内联？

浮动形状在 Word 中很有用，因为它们允许你将图像放置在页面的任意位置。然而，PDF 是一种 *面向页面* 的格式——没有 Word 那样的“浮动”概念。当转换引擎将它们保留为块级对象时，可能会出现：

- 与其他内容重叠。  
- 在页面边距处被裁剪。  
- 在旧版 PDF 阅读器中完全消失。  

通过将它们转换为 **inline** 元素，你可以确保 PDF 尊重阅读顺序，并且屏幕阅读器能够正确解释文档——这对可访问性合规性至关重要。

## 转换 Docx 为 PDF 时的常见陷阱

| 问题 | 症状 | 解决方案 |
|-------|---------|-----|
| 缺失字体 | 文本显示为 “□” 或默认使用 Arial | 通过 `PdfSaveOptions.FontEmbeddingMode = FontEmbeddingMode.Always` 嵌入字体。 |
| 大图像导致内存激增 | 大型 DOCX 导致内存不足异常 | 在转换前缩小图像或设置 `PdfSaveOptions.ImageCompression = PdfImageCompression.Jpeg;` |
| 未应用内联导出 | PDF 中浮动形状仍保持浮动 | 确认使用最新的 Aspose.Words 版本；旧版本属性名称有所变化。 |
| 路径错误 | `FileNotFoundException` | 使用 `Path.Combine` 并确保目录存在（`Directory.CreateDirectory`）。 |

## 高级：仅将特定形状导出为内联

有时你希望进行 *选择性* 的内联转换——仅对某些图片进行，而不是全部。你可以在保存之前遍历文档节点来实现：

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.WrapType == WrapType.Inline)
        continue; // already inline

    // Example condition: only convert pictures larger than 300px
    if (shape.HasImage && shape.Width > 300)
        shape.WrapType = WrapType.Inline;
}
```

在调整了 `WrapType` 后，运行相同的 `doc.Save` 调用。这让你能够对 **how to export inline** 行为进行细粒度控制。

## 专业技巧与最佳实践  

- **专业提示**：如果组织需要 PDF/A 归档，请设置 `pdfOptions.Compliance = PdfCompliance.PdfA1b`。  
- **注意**：隐藏的节（`SectionBreakContinuous`）可能会隐藏浮动形状；在保存前运行 `doc.UpdatePageLayout()`。  
- **性能提示**：如果批量转换多个文件，复用同一个 `PdfSaveOptions` 实例，可减少分配开销。  
- **测试**：始终在至少两个查看器（Adobe Reader、Edge）中打开生成的 PDF，以验证布局一致性。

## 可视化概览  

![保存文档为 PDF 的流程图，展示加载 → 配置 → 保存 步骤](https://example.com/flowchart.png "保存文档为 PDF 的流程图")

*Alt text:* **保存文档为 PDF 的流程图** – 说明了加载 DOCX、配置内联导出以及保存为 PDF 的三步流程。

## 结论  

现在你拥有了一套稳固、可用于生产环境的 **save document as PDF** 方法，能够在 C# 中正确处理浮动对象。通过配置 `ExportFloatingShapesAsInlineTag`，你可以确保每个图片、图表或文本框都成为文本流的一部分，消除常见的、导致 **convert word to pdf** 失败的故障。  

试一试：将包含多个浮动图像的复杂报告进行转换，然后使用选择性内联逻辑来保留某些应保持浮动的形状。下次需要 **convert docx to pdf** 时，你将确切知道如何保留每个视觉元素。  

如果遇到任何问题或发现巧妙的技巧，欢迎留言。祝编码愉快！

## 接下来你应该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助你掌握更多 API 功能并在项目中探索替代实现方法。

- [使用 Aspose.Words 将 docx 保存为 pdf – 完整 C# 指南](/words/english/net/basic-conversions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)
- [使用 Aspose.Words 将 Word 保存为 PDF – 完整 C# 指南](/words/english/net/basic-conversions/save-word-as-pdf-with-aspose-words-complete-c-guide/)
- [使用 Aspose.Words 在 C# 中将 word 转换为 pdf – 指南](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}