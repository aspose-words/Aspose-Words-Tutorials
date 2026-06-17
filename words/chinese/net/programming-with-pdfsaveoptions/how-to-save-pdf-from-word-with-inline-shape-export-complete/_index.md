---
category: general
date: 2026-06-02
description: 如何使用 Aspose.Words 将 DOCX 保存为 PDF，导出形状为内联 span 标签，并仅需几步即可将 Word 转换为 PDF。
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: zh
og_description: 如何使用 Aspose.Words 将 Word 文档保存为 PDF，将浮动形状导出为内联 span 标签，以实现干净的 Word
  转 PDF 转换结果。
og_title: 如何从 Word 保存 PDF – 内联形状导出教程
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: 如何在 Word 中使用内嵌形状导出保存 PDF – 完整指南
url: /zh/net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何从 Word 保存 PDF 并导出内联形状 – 完整指南

有没有想过 **如何保存 PDF**，在将 Word 文件转换为 PDF 时还能把所有浮动形状整齐地嵌入到正文流中？你并不是唯一有此需求的人。在许多企业应用中，我们需要 *将 Word 转换为 PDF*，但又不想出现图片错位或绘图对象漂移的情况。好消息是，Aspose.Words 让这一步变得轻而易举，你甚至可以指示库 **将形状导出为内联 `<span>` 标签**，从而让 PDF 看起来与原始 DOCX 完全一致。

在本教程中，我们将完整演示整个过程——加载 DOCX、调整 `PdfSaveOptions`，最后生成干净的 PDF。结束时，你将掌握 **如何保存 PDF**、**将 docx 保存为 pdf**，以及使用 *内联 span 标签* **导出形状** 的方法。

## 您需要的环境

- **Aspose.Words for .NET**（最新版本，本文撰写时为 24.x）。  
- **.NET 6.0** 或更高版本——代码同样适用于 .NET Framework 4.7.2，但 .NET 6 是最佳选择。  
- 一个包含至少一个浮动形状（图片、文本框或绘图）的简单 Word 文档。  
- 任意你喜欢的 IDE（Visual Studio、Rider、VS Code + C# 扩展）。  

就这些——无需额外的 NuGet 包，也不需要繁琐的 COM 互操作。准备好了吗？让我们开始吧。

## 第一步：创建项目并添加 Aspose.Words

首先，创建一个控制台应用（或将代码集成到现有服务中）。

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **小贴士：** 如果使用 Visual Studio，可以通过 NuGet 包管理器 UI 添加包——只需搜索 *Aspose.Words* 即可。

## 第二步：加载源文档

库引用完成后，我们可以加载 DOCX。这是 **如何保存 PDF** 的第一步——将源文件读取到内存中。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**为什么这一步很重要：** 加载文件会验证路径是否正确，以及 Aspose 能否解析 Word 的结构。如果文件中包含浮动形状，它们会成为 `Document` 对象节点树的一部分。

## 第三步：配置 PDF 保存选项 – 将形状导出为内联标签

下面是 **如何导出形状** 的核心。默认情况下，Aspose.Words 会把浮动形状渲染为 PDF 中的独立对象，这可能导致布局偏移。将 `ExportFloatingShapesAsInlineTag` 设置为 `true`，即可让引擎把每个形状包装在内联 `<span>` 元素中，从而保持文本流的连贯性。

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**为什么要启用此标志？** 想象一下合同中的签名框是浮动的，若在转换为 PDF 时未使用此设置，签名框可能会出现在另一页。内联 `<span>` 标签会将形状锚定在其所在段落中，生成的 PDF 与原始 Word 的视觉效果保持一致。

## 第四步：将文档保存为 PDF

最后，使用我们刚才构建的选项调用 `doc.Save`。这就是实际 **将 docx 保存为 pdf** 的时刻。

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

运行程序（`dotnet run`）并检查 `output.pdf`。你应该会看到浮动形状已内联渲染，正如在 Word 中的显示一样。

## 第五步：验证结果 – 快速检查清单

1. **所有文本均已出现** – 没有缺失的段落。  
2. **浮动形状出现在正确位置** – 现在它们是文本流的一部分。  
3. **PDF 大小合理** – 与使用独立图像流相比，导出为内联标签通常可以减少文件体积。  

如果发现异常，请再次确认源 DOCX 确实使用了 *浮动* 形状（右键 → 布局 → “与文字同行” vs “方形/背后文字”）。在转换前将形状改为 “与文字同行” 也能解决问题，但使用内联标签选项可以在不修改原文件的前提下实现同样效果。

## 边缘情况与常见问题

### 文档中包含 **SmartArt** 或 **图表** 怎么办？

SmartArt 和图表会被视为绘图对象。`ExportFloatingShapesAsInlineTag` 标志仍会把它们包装在 `<span>` 标签中，但复杂的图形可能会失去部分细节。此时可以先将图表导出为图像（`Chart.ToImage()`），再将图像内联插入。

### 能否 **保留超链接** 和 **书签**？

完全可以。这些元素不受 `ExportFloatingShapesAsInlineTag` 设置的影响。Aspose.Words 会自动保留所有超链接和书签信息。

### 如何 **更改 PDF 压缩** 或 **嵌入字体**？

`PdfSaveOptions` 提供了许多额外属性：

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

根据下游需求（例如 PDF/A 合规性）自由调整这些设置即可。

## 完整可运行示例（复制‑粘贴即用）

下面是可以直接粘贴到 `Program.cs` 的完整程序。将 `YOUR_DIRECTORY` 替换为实际的文件夹路径。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**控制台预期输出：**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

打开 `output.pdf`——你会看到原始布局完整保留，所有浮动形状都紧贴文本流。

## 结论

我们已经演示了 **如何从 Word 文档保存 PDF**，并确保浮动形状以内联 `<span>` 标签的形式出现。通过加载 DOCX、配置 `PdfSaveOptions`，以及调用 `doc.Save`，你可以可靠地 **将 docx 保存为 pdf**，并实现 **将 word 转换为 pdf** 而不出现布局异常。

接下来可以尝试将此方法与 **PDF/A** 合规性结合，以满足归档需求，或使用简单的 `foreach` 循环批量处理文件夹中的 DOCX。你也可以探索 **自定义渲染**（例如添加水印），通过 Aspose.Words 的 `DocumentVisitor` API 实现。

对形状处理、字体嵌入或性能调优还有其他疑问吗？在下方留言吧，祝编码愉快！

## 接下来该学习什么？

以下教程与本指南的技术紧密相关，帮助你进一步掌握 API 的其他功能，并在项目中尝试不同的实现方式。

- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf – Convert DOCX to PDF in Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}