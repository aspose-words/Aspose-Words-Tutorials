---
category: general
date: 2026-02-13
description: 在将 DOCX 转换为 Markdown 时保留换行。了解如何将 Word 保存为 Markdown，导出空段落，并保持格式完整。
draft: false
keywords:
- preserve line breaks
- convert docx to markdown
- save word as markdown
- how to export empty
- how to preserve breaks
language: zh
og_description: "在将 DOCX 转换为 markdown 时保留换行。  \n本指南展示了如何将 Word 保存为 markdown 并正确导出空段落。"
og_title: 保留换行符：将 DOCX 转换为 Markdown
tags:
- Aspose.Words
- C#
- Markdown
title: 保留换行：将 DOCX 转换为 Markdown
url: /zh/net/programming-with-markdownsaveoptions/preserve-line-breaks-convert-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 保持换行：将 DOCX 转换为 Markdown

有没有在将 DOCX 文件转换为 Markdown 时需要 **保留换行**？这是一种常见的困扰——您精美的 Word 文档会变成一大段文字，原本有意留出的空行也会消失。好消息是，只需几个简单的设置，就可以保留每一个换行，甚至是空段落。

在本教程中，我们将完整演示 **将 Word 保存为 Markdown** 的整个过程，涵盖从加载源文档到配置正确的导出模式的所有步骤。结束时，您将了解 *如何导出空段落*、*如何在复杂布局中保留换行*，并拥有一个完整、可直接复制粘贴的代码示例。没有缺失的部分，也没有“请查看文档”的死胡同。

## 您将学到

- 为什么保留换行对可读性和下游工具很重要。  
- 如何使用 Aspose.Words for .NET **将 DOCX 转换为 markdown**。  
- 哪些 `MarkdownSaveOptions` 设置控制空段落的处理。  
- 处理表格、列表和代码块等边缘情况的实战技巧。  
- 一个完整、可直接运行的示例，您可以立即放入任何 C# 项目中。

### 前置条件

- 已安装 .NET 6+（或 .NET Framework 4.7.2+）。  
- 拥有 **Aspose.Words for .NET** 的许可证（免费试用版可用于本演示）。  
- 对 C# 和 Markdown 概念有基本了解。  

如果您已满足上述条件，让我们开始吧。

![保留换行示意图](preserve-line-breaks.png "图示空段落在 Markdown 中如何变为换行")

## 保持换行 – 为什么重要

当 Word 文档中包含有意的空行——可以视为章节之间的视觉分隔符——这些空行在转换过程中常常会被去除。Markdown 的设计将单个换行视为同一段落的继续，因此必须显式表示空行。如果不 **保留换行**，输出的文本会显得拥挤，下游解析器（如静态站点生成器）可能会意外合并章节。

保留这些换行不仅仅是美观问题；它还能帮助依赖段落边界进行脚注定位、定制样式，甚至 SEO 友好标题提取的工具。简而言之，忠实的转换尊重作者的意图。

## 使用 Aspose.Words 将 DOCX 转换为 Markdown

Aspose.Words 为您提供对转换过程的细粒度控制。关键类是 `MarkdownSaveOptions`，它允许您决定空段落的导出方式。下面我们将把 `EmptyParagraphExportMode` 设置为 `EmptyLine`，该模式会将 Word 中的空段落转换为 Markdown 的空行。

### 步骤实现

### 1️⃣ 加载源文档

首先，将库指向您的 `.docx` 文件。`Document` 构造函数会完成所有繁重的工作——解析样式、图像和布局信息。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Adjust the path to match your environment
string inputPath  = @"C:\Docs\MyReport.docx";
Document doc = new Document(inputPath);
```

> **为什么重要：** 及早加载文档可以让您访问其内部结构，从而根据发现的情况（例如检测文件是否真的包含空段落）调整选项。

### 2️⃣ 配置 Markdown 保存选项

这里我们来回答 **“如何导出空段落”** 的问题。`EmptyParagraphExportMode` 枚举提供三种选择：

| 模式 | Markdown 中的结果 |
|------|--------------------|
| `EmptyLine` | 插入一个空行（`\n\n`）。 |
| `PreserveLineBreaks` | 将每个换行转为硬换行（`  \n`）。 |
| `None` | 完全省略空段落。 |

对于大多数只需要视觉间隔的场景，`EmptyLine` 就能满足需求。

```csharp
MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
{
    // Export empty paragraphs as a single empty line.
    // This is the most intuitive way to keep visual spacing.
    EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine,

    // Optional: keep original line breaks inside paragraphs.
    // Uncomment if you need finer control.
    // PreserveLineBreaks = true
};
```

> **专业提示：** 如果您还需要保留手动换行（Word 中的 Shift + Enter），请将 `PreserveLineBreaks = true`。这样，空段落和软换行都能在往返转换中保留下来。

### 3️⃣ 将文档保存为 Markdown

现在我们写入输出文件。您可以选择任意文件夹，只需确保扩展名为 `.md` 即可。

```csharp
string outputPath = @"C:\Docs\MyReport.md";
doc.Save(outputPath, mdOpts);
Console.WriteLine($"✅ Conversion complete! Markdown saved to {outputPath}");
```

这就是完整的流程。运行程序，打开 `.md` 文件，您会看到空行正好出现在原始 Word 文件中的位置。

### 完整工作示例

将所有内容整合在一起，以下是一个可立即编译的独立控制台应用程序示例：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source DOCX
        string inputPath = @"C:\Docs\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Set up Markdown options to preserve empty paragraphs
        MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
        {
            EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine,
            // PreserveLineBreaks = true   // Uncomment if you need soft line breaks
        };

        // 3️⃣ Save as Markdown
        string outputPath = @"C:\Docs\WithEmptyParas.md";
        doc.Save(outputPath, mdOpts);

        Console.WriteLine($"✅ Document converted! Check: {outputPath}");
    }
}
```

**预期输出：** 在任意编辑器中打开 `WithEmptyParas.md`。您会发现 `input.docx` 中的每一条空行都在 Markdown 文件中以空行的形式出现，保留了您设计的视觉分隔。

## 将 Word 保存为 Markdown – 高级场景

### 处理表格和列表

Word 中的表格会自动转换为 Markdown 表格，但空行可能会有些棘手。如果表格行仅包含一个空单元格，Aspose.Words 会将其视为空段落。`EmptyParagraphExportMode` 仍然生效，因此您会在表格 **外部** 获得一条空行，而不是表格内部。若要在表格 *内部* 保持视觉间隔，请在单元格中插入不间断空格（`&nbsp;`）。

```csharp
// Example: Adding a placeholder to an empty cell
Table table = doc.GetChild(NodeType.Table, 0, true) as Table;
Cell emptyCell = table.Rows[2].Cells[1];
emptyCell.AppendChild(new Paragraph(doc));
emptyCell.FirstParagraph.AppendChild(new Run(doc, "\u00A0")); // non‑breaking space
```

### 代码块和预格式化文本

如果您的 DOCX 包含预格式化的代码，Aspose.Words 会使用三重反引号将其包裹。代码块内部的空行会自动保留，且不受 `EmptyParagraphExportMode` 的影响。不过，如果发现空行缺失，请再次确认原始 Word 段落样式设置为 “No Spacing”。这样，库会将每一行视为独立的段落。

### 何时改用 `PreserveLineBreaks`

有时您需要硬换行（`  `），而不是完整的空段落。例如，诗歌或地址块通常依赖单行换行。切换此选项：

```csharp
mdOpts.PreserveLineBreaks = true;   // Turns soft breaks into Markdown hard breaks
mdOpts.EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.None; // optional
```

现在，Word 中的每个 `Shift+Enter` 会在 Markdown 中变为 `  \n`，而真正的空段落则会消失（除非您同时保留 `EmptyLine`）。

## 正确导出空段落的方法

简短回答：设置 `EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine`。更详细的答案涉及理解 *为什么* 这样有效。

- **EmptyParagraphExportMode** 告诉序列化器 *如何* 处理不包含任何运行（文本）的段落。  
- **EmptyLine** 插入双换行符，Markdown 将其解释为段落分隔符。  
- 其他模式要么折叠段落（`None`），要么将换行视为硬换行（`PreserveLineBreaks`）。

如果忘记设置此选项，默认行为是 `None`，所有空行都会消失——这正是我们要解决的问题。

## 在复杂文档中保留换行

复杂文档通常混合标题、图像和脚注。以下是确保不丢失任何换行的检查清单：

| 检查项 | 重要原因 |
|----------------|----------------|
| **验证空段落** | 使用 `doc.GetChildNodes(NodeType.Paragraph, true)` 在转换前统计空段落数量。 |
| **为诗歌启用 `PreserveLineBreaks`** | 确保单行换行得以保留。 |
| **检查图片说明** | 说明是独立的段落，需要相同的导出模式。 |
| **执行转换后对比** | 将原始文本（通过 `doc.GetText()` 提取）与 Markdown 输出进行比较。 |
| **使用 Markdown 查看器进行测试** | 某些渲染器对多个空行的处理不同；请验证视觉效果。 |

### 示例验证代码

```csharp
// Count empty paragraphs before saving
int emptyCount = 0;
NodeCollection paragraphs = doc.GetChildNodes(NodeType.Paragraph, true);
foreach (Paragraph p in paragraphs)
{
    if (p.GetText().Trim().Length == 0)
        emptyCount++;
}
Console.WriteLine($"Document contains {emptyCount} empty paragraph(s).");
```

在保存步骤之前运行此代码，可让您确信转换会处理您期望的确切换行数量。

## 常见陷阱与专业技巧

- **陷阱：**

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}