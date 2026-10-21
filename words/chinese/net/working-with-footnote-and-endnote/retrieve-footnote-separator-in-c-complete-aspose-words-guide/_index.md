---
category: general
date: 2026-08-07
description: 使用 Aspose.Words for .NET 检索脚注分隔符。了解如何提取脚注和尾注分隔符、检查节点类型并在 C# 中进行修改。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: zh
lastmod: 2026-08-07
og_description: 使用 Aspose.Words for .NET 检索脚注分隔符。本指南展示了如何提取脚注和尾注分隔符、检查它们的节点类型以及保存更改。
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: 在 C# 中检索脚注分隔符——一步一步的 Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: 在 C# 中检索脚注分隔符 – 完整的 Aspose.Words 指南
url: /zh/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中检索脚注分隔符 – 完整 Aspose.Words 指南

如果您需要从 Word 文档中**检索脚注分隔符**，本教程将向您展示如何使用 Aspose.Words for .NET 完成此操作。无论您是在构建文档处理服务还是清理脚注格式，您都将看到一个完整的可运行示例，提取脚注和尾注分隔符。

在本指南中，您将学习如何加载 `.docx` 文件，调用 `FootnoteSeparator` 和 `EndnoteSeparator` 属性，检查返回的 `Node` 对象，并可选择替换分隔线。无需外部文档——下面已包含所有必要内容。

## 前置条件

* .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.7.2）
* Aspose.Words for .NET NuGet 包（版本 24.9 或更高）
* 包含脚注和/或尾注的 Word 文档（例如 `Footnotes.docx`）

您可以使用以下 CLI 命令添加 Aspose.Words 包：

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## 步骤 1：设置项目并导入命名空间

创建一个新的控制台项目或将代码添加到现有项目中。所需的 `using` 指令列在下方。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

这些命名空间让您能够访问 `Document` 类、`Node` 层次结构以及执行**检索脚注分隔符**操作所需的 `NodeType` 枚举。

## 步骤 2：加载包含脚注和尾注的文档

在任何 Aspose.Words 工作流中，第一步都是加载源文件。将占位路径替换为实际的 `.docx` 文件位置。

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

加载文件会准备内部节点树，这对于**检索脚注分隔符**至关重要，因为分隔符节点位于该树中。

## 步骤 3：检索脚注分隔符节点

现在，您可以通过访问 `Document` 对象的 `FootnoteSeparator` 属性**检索脚注分隔符**。该节点代表将脚注与正文分开的那条线。

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

标准分隔线的 `NodeType` 将是 `Paragraph`。了解节点类型有助于决定是修改分隔符还是完全替换它。

## 步骤 4：检索尾注分隔符节点

同样，您可以使用 `EndnoteSeparator` 属性**检索尾注分隔符**。该节点将尾注与主体内容分开。

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

在大多数文档中，两个分隔符节点共享相同的 `NodeType`（`Paragraph`），但它们可以独立自定义。

## 步骤 5：检查或修改分隔符内容（可选）

如果需要更改分隔符的视觉外观——例如将一串破折号替换为细线——可以直接编辑 `Paragraph` 节点。下面的示例将默认的分隔符文本替换为自定义字符串。

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

修改节点后，您可以保存文档，以在 Word 中看到更改效果。

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## 预期的控制台输出

运行程序并使用原始的 `Footnotes.docx` 时，您应看到类似以下的输出：

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

如果在 Microsoft Word 中打开 `Footnotes_Updated.docx`，脚注和尾注分隔符将显示您插入的自定义文本。

## 常见问题与边缘情况

**如果文档没有脚注怎么办？**  
`FootnoteSeparator` 属性仍会返回一个 `Paragraph` 节点，因为 Word 总会包含一个分隔符占位符。该节点将为空，您可以安全地添加内容或保持不变。

**我可以检索特定章节的分隔符吗？**  
脚注和尾注分隔符是全局文档范围的，而非章节特定的。如果需要章节级别的控制，必须使用 `Section.FootnoteOptions` 和 `Section.EndnoteOptions`，而不是全局分隔符节点。

**这在 .NET Core 上能工作吗？**  
可以。Aspose.Words for .NET 是跨平台的，同样的代码可在 Windows、Linux 和 macOS 上运行，前提是使用 .NET 6+。

**我应该期待什么节点类型？**  
`FootnoteSeparator` 和 `EndnoteSeparator` 都返回 `Paragraph` 节点（`NodeType.Paragraph`）。如果遇到其他类型，可能是文档损坏，建议重新加载或验证源文件。

## 完整源码，快速复制粘贴

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

将代码复制到 `Program.cs` 文件，调整文件路径后运行 `dotnet run`。该程序演示了完整的**检索脚注分隔符**工作流，从加载文档到持久化更改。

## 结论

您现在已经掌握了使用 Aspose.Words for .NET **检索脚注分隔符**和**检索尾注分隔符**的方法，能够检查它们的 `document node type`，并可选择替换其内容。此技术可帮助您自动化脚注格式化、生成自定义分隔线，或在任何 C# 应用程序中验证文档结构。

接下来，您可以探索诸如 **C# 脚注提取**（用于单个脚注文本）之类的相关主题，或学习如何使用 `FootnoteOptions` **修改脚注引用标记**。这两个概念都直接基于本文所覆盖的节点树基础。

祝编码愉快，欢迎尝试不同的分隔符样式，以匹配您项目的品牌形象！

## 接下来您应该学习什么？

以下教程涵盖与本指南中演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能，并在自己的项目中探索替代实现方案。

- [使用脚注和尾注的文字处理](/words/english/net/working-with-footnote-and-endnote/)
- [在 Aspose.Words for .NET 中使用 Document Builder 添加内容](/words/english/net/add-content-using-document-builder/)
- [使用脚注和尾注](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}