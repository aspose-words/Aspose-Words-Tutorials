---
category: general
date: 2026-09-08
description: 在使用 Aspose.Words for .NET 加载 Word 文档时，检索尾注分隔符并显示脚注分隔符。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve endnote separator
- load word document
- display footnote separator
- Aspose.Words C#
- footnote and endnote handling
language: zh
lastmod: 2026-09-08
og_description: 使用 Aspose.Words for .NET 加载 Word 文档时，检索尾注分隔符并显示脚注分隔符。
og_image_alt: Console screenshot showing the footnote separator text printed by a
  C# program
og_title: 在 C# 加载 Word 文档时检索尾注分隔符
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Retrieve endnote separator and display footnote separator when you
    load a Word document using Aspose.Words for .NET.
  headline: Retrieve endnote separator while loading a Word document in C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word processing
title: 在 C# 中加载 Word 文档时检索尾注分隔符
url: /zh/net/working-with-footnote-and-endnote/retrieve-endnote-separator-while-loading-a-word-document-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中加载 Word 文档时检索尾注分隔符

如果您需要从 Word 文件中 **检索尾注分隔符**，本指南将准确展示如何操作。您还将学习如何使用 Aspose.Words **加载 Word 文档** 并在控制台中 **显示脚注分隔符** 文本，所有内容都在一个可运行的示例中。

在法律、学术或出版类应用中，处理脚注和尾注是常见需求。本教程涵盖您所需的全部内容——从打开文件到处理分隔符缺失的情况——让您无需猜测即可将解决方案集成到任何 .NET 项目中。

## 本教程涵盖内容

* 如何使用 Aspose.Words API **加载 Word 文档**。  
* 如何 **检索尾注分隔符** 以及分隔符为何重要。  
* 如何在控制台上 **显示脚注分隔符** 以进行调试或日志记录。  
* 当文档不包含脚注或尾注时的边缘情况处理。  
* 一个完整的、可直接复制粘贴的代码示例，可在 .NET 6 或更高版本上运行。

### 前置条件

| 要求 | 原因 |
|-------------|--------|
| .NET 6 SDK or newer | 为 C# 示例提供运行时环境。 |
| Aspose.Words for .NET (NuGet package `Aspose.Words`) | 提供 `Document.Footnotes` 和 `Document.Endnotes` 的库。 |
| A Word file (`Footnotes.docx`) that contains at least one footnote or endnote | 用于演示分隔符。 |
| Any IDE (Visual Studio, Rider, VS Code) | 用于编译和运行程序。 |

> **技巧提示：** 如果没有带脚注的文档，可在 Microsoft Word 中快速创建：插入 → 脚注 → 输入一些文字，然后另存为 `Footnotes.docx`。

## 使用 Aspose.Words 加载 Word 文档

第一步是将 **Word 文档加载** 到内存中。Aspose.Words 读取文件格式并构建可供查询的对象模型。

```csharp
using Aspose.Words;
using System;

class Program
{
    static void Main()
    {
        // Step 1: Load the document containing footnotes and endnotes
        // Adjust the path to point to your local file.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");
```

*为什么这很重要*：加载文档是进行任何后续操作的前提。如果文件路径不正确，`Document` 会抛出 `FileNotFoundException`，因此请在运行前验证路径。

## 检索脚注分隔段落

脚注分隔符是将正文与脚注列表在视觉上分开的段落。检索它可以让您检查或修改其格式。

```csharp
        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.Footnotes.Separator;

        // The separator may be null if the document has no footnotes.
        if (footnoteSeparator != null)
        {
            // Step 3: **display footnote separator** text in the console
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }
```

*为什么这很重要*：**显示脚注分隔符** 有助于您确认访问了正确的段落，尤其是在需要应用自定义样式（例如线条或特定字体）时。

## 检索尾注分隔段落

现在我们 **检索尾注分隔符**。该过程与脚注处理类似，只是使用 `Endnotes` 集合。

```csharp
        // Step 4: Retrieve the endnote separator paragraph
        Paragraph endnoteSeparator = doc.Endnotes.Separator;

        // The separator can also be null if there are no endnotes.
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

*为什么这很重要*：**检索尾注分隔符** 步骤在您需要调整正文与尾注列表之间的视觉分隔时至关重要——这在学术出版中很常见，因为尾注出现在章节末尾。

### 处理缺失的分隔符

当文档未定义分隔符时，`Footnotes.Separator` 和 `Endnotes.Separator` 都会返回 `null`。在调用 `GetText()` 之前务必检查是否为 `null`，以避免 `NullReferenceException`。如果需要默认分隔符，可以创建一个：

```csharp
if (endnoteSeparator == null)
{
    endnoteSeparator = new Paragraph(doc);
    endnoteSeparator.AppendChild(new Run(doc, "—")); // Simple dash as a separator
    doc.Endnotes.InsertSeparator(endnoteSeparator);
}
```

此代码注入一个最小的分隔符，以便后续处理可以依赖其存在。

## 预期的控制台输出

当示例针对包含一个脚注和一个尾注的文档运行时，您应看到类似以下内容：

```
Document loaded successfully.
Footnote separator text: — 
Endnote separator text: — 
```

如果文档缺少脚注或尾注，程序会打印相应的 “未找到” 信息，展示了优雅的错误处理。

## 完整、可运行的示例

下面是完整的程序，您可以复制到新的 C# 控制台项目中。无需额外代码。

```csharp
using Aspose.Words;
using System;

class RetrieveSeparatorsDemo
{
    static void Main()
    {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");

        // Retrieve and display the footnote separator
        Paragraph footnoteSeparator = doc.Footnotes.Separator;
        if (footnoteSeparator != null)
        {
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }

        // Retrieve and display the endnote separator
        Paragraph endnoteSeparator = doc.Endnotes.Separator;
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

将文件保存为 `Program.cs`，添加 Aspose.Words NuGet 包（`dotnet add package Aspose.Words`），然后运行 `dotnet run`。程序将打印分隔符文本，或在缺失时提示您。

## 常见变体和假设情景

| 场景 | 如何调整代码 |
|----------|-----------------------|
| **多个自定义分隔符** | 使用 `doc.Footnotes.Separator` 替换默认分隔符，然后手动使用 `doc.Footnotes.Add(separatorParagraph)` 添加额外的分隔段落。 |
| **更改分隔符样式** | 检索到分隔符后，修改其 `ParagraphFormat`（例如 `footnoteSeparator.ParagraphFormat.Alignment = ParagraphAlignment.Center;`）。 |
| **处理 .doc 文件** | 同样的 API 适用，只需确保文件路径以 `.doc` 结尾。 |
| **处理多个文档** | 将加载和分隔符检索包装在 `foreach` 循环中；仅在使用 `doc = new Document(path)` 重置后才复用同一 `Document` 实例。 |

## 最佳实践检查清单

- ✅ **在访问分隔符文本之前始终检查 `null`**。  
- ✅ **Trim** `GetText()` 的结果以去除隐藏的换行字符。  
- ✅ **在批量处理大量文件时释放大型 `Document` 对象**（使用 `using` 或调用 `doc.Dispose()`）。  
- ✅ **仅在开发阶段记录分隔符文本**；除非必要，否则避免在生产日志中暴露它。  

## 结论

现在，您已经了解如何在 **加载 Word 文档** 时 **检索尾注分隔符**，以及在 .NET 控制台应用中 **显示脚注分隔符**。完整示例演示了加载、查询以及安全处理缺失分隔符的过程，为任何脚注或尾注的操作任务提供了坚实的基础。

接下来，您可以探索：

* **自定义脚注/尾注格式** —— 调整字体、边框或编号样式。  
* **提取脚注/尾注内容** —— 遍历 `doc.Footnotes` 或 `doc.Endnotes` 集合。  
* **保存修改后的文档** —— 使用 `doc.Save("output.docx")` 将更改持久化。

随意尝试不同的 Word 文件、分隔符样式和 Aspose.Words 功能。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步学习。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [如何使用 Aspose.Words LoadOptions 加载 Word 文档](/words/english/net/programming-with-loadoptions/)
- [获取 Word 文档中的段落样式分隔符](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [在 Aspose.Words for .NET 中创建并设置 Word 文档样式](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}