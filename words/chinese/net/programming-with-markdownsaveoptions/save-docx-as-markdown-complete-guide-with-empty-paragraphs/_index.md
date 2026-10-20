---
category: general
date: 2026-03-24
description: 学习如何将 docx 保存为 markdown，并在保留换行的情况下将 Word 转换为 markdown。一步一步的代码和技巧。
draft: false
keywords:
- save docx as markdown
- convert word to markdown
- export word to markdown
- preserve line breaks markdown
language: zh
og_description: 轻松将 docx 保存为 markdown。本指南展示了如何仅用几行 C# 代码将 Word 转换为 markdown 并保留换行。
og_title: 将 docx 保存为 markdown – 完整的逐步指南
tags:
- Aspose.Words
- C#
- Document Conversion
title: 将 docx 保存为 markdown – 包含空段落的完整指南
url: /zh/net/programming-with-markdownsaveoptions/save-docx-as-markdown-complete-guide-with-empty-paragraphs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 docx 保存为 markdown – 完整编程演练

有没有想过如何 **将 docx 保存为 markdown**，同时保留那些让文本呼吸的空行？你并不是唯一的遇到这个问题的人。很多开发者在转换时会把空段落压缩掉，导致原本排版良好的文档变成一整块文字。

好消息是，只需几行 C# 代码并使用正确的选项，你就可以 **将 Word 转换为 markdown**，并且完整保留每个空段落。在本教程中，我们将逐步演示具体操作，解释每个设置的意义，并展示如果你更倾向于使用换行符而不是空行时，如何对输出进行微调。

## 你需要准备的东西

在开始之前，请确保你拥有：

- **Aspose.Words for .NET**（任意近期版本；我们使用的 API 在 23.9 及以后均稳定）。  
- 一个 .NET 开发环境（Visual Studio、Rider，或 `dotnet` CLI）。  
- 一个包含若干空段落的源 Word 文件（`input.docx`），这些空段落是你想保留的。  

就这些——不需要额外的 NuGet 包，也没有复杂的构建步骤。如果你已经熟悉 C#，会感觉非常自然。

## 第一步：加载源文档  

首先我们创建一个指向 Word 文件的 `Document` 对象。可以把它想象成在内存中打开了该文件。

```csharp
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **为什么这一步很重要：**  
> 加载文档后，你才能访问其内部结构（段落、run、表格等）。没有这个对象，Aspose.Words 就无法知道要导出什么内容。

## 第二步：配置 Markdown 保存选项  

接下来是关键——告诉库如何处理空段落。`MarkdownSaveOptions` 类提供了 `EmptyParagraphExportMode` 属性来控制此行为。

```csharp
// Step 2: Configure Markdown save options to preserve empty paragraphs
var markdownOptions = new MarkdownSaveOptions
{
    // Preserve empty paragraphs as blank lines in the markdown output.
    EmptyParagraphExportMode = EmptyParagraphExportMode.Preserve
    // Alternatively, use .ConvertToLineBreak if you prefer a line‑break (\\) instead.
};
```

> **为何会在两种模式之间做选择：**  
> - `Preserve` 会将空段落保留为一个空行（`\n\n`），大多数 markdown 渲染器会将其解释为段落换行。  
> - `ConvertToLineBreak` 会把空段落转换为 Markdown 硬换行（`  \n`），适用于需要更紧凑视觉效果的场景。

## 第三步：将文档保存为 Markdown  

最后，将文档写入 `.md` 文件，并传入我们刚才配置好的选项。

```csharp
// Step 3: Save the document as Markdown using the configured options
doc.Save("YOUR_DIRECTORY/PreserveEmpty.md", markdownOptions);
```

> **结果：** 文件 `PreserveEmpty.md` 现在包含的 markdown 与原始 Word 布局一致，空行也全部保留下来。

### 预期输出

如果 `input.docx` 如下（简化示例）：

```
Title

[empty paragraph]

First paragraph.

[empty paragraph]

Second paragraph.
```

生成的 `PreserveEmpty.md` 将会是：

```markdown
# Title

First paragraph.

Second paragraph.
```

注意标题与第一段之间、两段之间各有两个空行——这正是被保留的空段落。

## 可选方案：导出 Word 为带换行符的 markdown  

有些团队更喜欢使用单个换行符而不是完整的空段落。只需将枚举值改成如下：

```csharp
var markdownOptions = new MarkdownSaveOptions
{
    EmptyParagraphExportMode = EmptyParagraphExportMode.ConvertToLineBreak
};
```

输出现在会包含 Markdown 硬换行（`  \n`），而不是完整的空行：

```markdown
# Title  
First paragraph.  
Second paragraph.
```

## 专业技巧与常见坑点  

- **技巧：** 如果你一次性处理大量文件，复用同一个 `MarkdownSaveOptions` 实例。这样可以减少分配开销。  
- **注意：** Word 表格中的空行。默认情况下，Aspose.Words 会把它们当作空段落处理，可能导致 markdown 中出现额外的空行。使用 `markdownOptions.TableExportMode = TableExportMode.Markdown` 可以让表格保持整洁。  
- **边缘情况：** 当文档同时包含 `\r\n` 与 `\n` 换行符时，Aspose.Words 会自动标准化，但仍建议在目标渲染器（GitHub、VS Code 预览等）上验证输出。  
- **版本说明：** `EmptyParagraphExportMode` 属性在 Aspose.Words 22.6 中首次引入。如果你使用的版本更旧，请升级或改用手动后处理（例如正则将 `\n\n` 替换为 `  \n`）。

## 可视化概览  

下面是一张简易的转换流程图。alt 文本已包含主要关键词以利 SEO。

![转换流程：Word → Aspose.Words → Markdown（保留空段落）](conversion-diagram.png "将 docx 保存为 markdown 流程图")

## 完整、可直接运行的示例  

将以下代码复制粘贴到新建的控制台项目（`dotnet new console`）中并运行。它会在可执行文件所在目录生成 `PreserveEmpty.md`。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the .docx file
        Document doc = new Document("input.docx");

        // Set up markdown options to keep empty paragraphs
        var markdownOptions = new MarkdownSaveOptions
        {
            EmptyParagraphExportMode = EmptyParagraphExportMode.Preserve,
            // Optional: keep tables as markdown tables
            TableExportMode = TableExportMode.Markdown
        };

        // Save as .md
        doc.Save("PreserveEmpty.md", markdownOptions);

        Console.WriteLine("Conversion complete! Check PreserveEmpty.md");
    }
}
```

运行 `dotnet run`，你会看到确认信息。使用任意 markdown 查看器打开 `PreserveEmpty.md`，即可验证间距是否与原始 Word 文件保持一致。

## 常见问答  

**问：这对 .doc 文件也适用吗？**  
答：完全适用。`Document` 构造函数支持 `.doc`、`.docx`、`.rtf` 等多种格式，只需指向相应路径即可。

**问：如果只想导出文档的某一部分怎么办？**  
答：使用 `doc.GetChildNodes(NodeType.Paragraph, true)` 获取所需范围，克隆到新的 `Document`，再使用相同的选项保存。

**问：输出是否兼容 GitHub Flavored Markdown？**  
答：兼容。Aspose.Words 生成的是标准 markdown 语法，GitHub 能正确渲染，包括表格和代码块。

## 后续步骤  

既然已经掌握了 **将 docx 保存为 markdown** 并 **保留 markdown 换行** 的技巧，你可以进一步探索：

- 使用自定义 CSS 导出 **word to markdown**，实现样式化标题。  
- 使用 `Directory.GetFiles` 批量转换文件夹中的 Word 文档。  
- 将此转换集成到 ASP.NET Core API 中，实现即时文档渲染。  

这些扩展都基于相同的核心概念，你已经具备了进一步深化的基础。

---

**祝编码愉快！** 如果在使用过程中遇到问题或有其他选项的想法，欢迎在下方留言。你的反馈将帮助社区保持转换流程的顺畅与可靠。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}