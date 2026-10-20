---
category: general
date: 2026-08-04
description: 使用 Aspose.Words 在 C# 中更改脚注分隔符 – 学习如何编辑脚注分隔符并更改 Word 文档中的尾注分隔符。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: zh
lastmod: 2026-08-04
og_description: 使用 Aspose.Words 在 C# 中更改脚注分隔符。本指南展示如何编辑脚注分隔符、定制尾注分隔符并保存更新后的文档。
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: 在 C# 中更改脚注分隔符 – 完整的 Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: 使用 Aspose.Words 在 C# 中更改脚注分隔符
url: /zh/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中使用 Aspose.Words 更改脚注分隔符

如果您需要 **更改 Word 文档中的脚注分隔符**，本教程将通过 Aspose.Words for .NET 为您演示完整步骤。无论是想用符号替换默认的横线，还是为尾注分隔符应用不同的样式，下面的代码都涵盖了完整的工作流。

您还将学习如何 **编辑脚注分隔符** 以及相关的 **更改尾注分隔符** 操作，从而使同一文档的脚注和尾注保持一致的样式。无需外部工具——只需几行 C# 代码。

## 您将实现的目标

阅读完本指南后，您将能够：

* 加载包含脚注和尾注的已有 *.docx* 文件。  
* 访问脚注、脚注续页以及尾注的分隔符节点。  
* 替换分隔符字符（例如，将默认的横线改为星号）。  
* 保存修改后的文档且不丢失其他内容。  

本教程假设您具备 C# 基础并已安装 **Aspose.Words** NuGet 包（版本 24.9 或更高）。

---

## 前置条件

| 要求 | 原因 |
|------|------|
| .NET 6.0+ 或 .NET Framework 4.7.2+ | Aspose.Words 所需的运行时 |
| Aspose.Words for .NET 库 | 提供 `Document` 和 `FootnoteOptions` API |
| 一个包含至少一个脚注或尾注的 Word 文件（`input.docx`） | 用于演示分隔符的更改 |

您可以使用以下 CLI 命令将 Aspose.Words 添加到项目中：

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## 步骤 1：加载包含脚注的文档

首先将源文件读取到 `Document` 对象中。该对象在内存中表示整个 Word 文件，并提供对所有节点的访问。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**为何重要：** 加载文档是进行任何操作的入口。如果文件未找到，Aspose.Words 会抛出 `FileNotFoundException`，因此请确保路径正确后再继续。

---

## 步骤 2：访问脚注和尾注分隔符节点

`Document.FootnoteOptions` 暴露了三个分隔符节点：

* `Separator` – 出现在第一页脚注集合之后的横线。  
* `ContinuationSeparator` – 脚注跨页时使用的横线。  
* `EndnoteSeparator` – 将正文与尾注列表分开的横线。

您可以将这些节点作为通用 `Node` 对象获取，然后强制转换为 `Run` 以修改文本。

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**为何重要：** 这些节点是唯一存放可视分隔符字符的地方。修改其他节点（例如普通段落）不会影响脚注的格式。

---

## 步骤 3：更改脚注分隔符字符

最常见的需求是将默认的横线替换为符号，例如星号 (`*`)。因为分隔符存储为 `Run`，可以安全地修改其 `Text` 属性。

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**为何重要：** 直接编辑 `Run.Text` 会在最终文档中更新可视表现，而不会影响脚注的其他内容。相同的模式可用于任何字符串，包括 Unicode 符号。

---

## 步骤 4：更改尾注分隔符（可选）

如果您还需要 **更改尾注分隔符**，过程与脚注相同。将 `endnoteSeparator` 的文本替换为您想要的字符即可。

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**为何重要：** 尾注的样式通常与脚注不同。提供单独的分隔符可以让您遵循文档设计指南，保持视觉一致性。

---

## 步骤 5：保存修改后的文档

完成所有修改后，使用 `Document.Save` 将更改持久化。您可以覆盖原文件或写入新位置。

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**为何重要：** `Save` 将内存中的表示写入磁盘，保留所有其他元素（样式、图片、表格）不变。

---

## 完整可运行示例

将所有代码片段组合在一起，下面是一个自包含的控制台应用程序，演示完整工作流：

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**预期结果：** 在 Microsoft Word 中打开 *ModifiedSeparators.docx*。第一页脚注区域底部的分隔线将变为单个星号 (`*`)。如果文档包含尾注，正文与尾注列表之间的分隔线将显示为破折号 (`-`)。所有其他内容（文本、图片、表格）保持不变。

---

## 常见问题与边缘情况处理

| 问题 | 解答 |
|------|------|
| **如果文档没有脚注怎么办？** | `FootnoteOptions.Separator` 仍会返回一个 `Run` 节点，但其文本可能为空。代码在修改前会安全检查节点类型。 |
| **可以使用多字符字符串（例如 "***"）吗？** | 可以。`Run.Text` 属性接受任意字符串，包括 Unicode 字符。 |
| **更改分隔符会影响现有的脚注编号吗？** | 不会。分隔符独立于编号方案。 |
| **是否需要释放 `Document` 对象？** | `Document` 通过 `Node` 隐式实现 `IDisposable`。在短生命周期的控制台应用中可选，但在长期运行的服务中建议使用 `using` 块包装。 |
| **在 .NET Core 与 .NET Framework 上有何区别？** | API 在所有运行时中保持一致；唯一需要注意的是目标框架版本必须受 Aspose.Words 包支持。 |

**小技巧：** 如果需要为不同章节设置不同的分隔符，可以遍历 `doc.GetChildNodes(NodeType.Footnote, true)` 并单独调整每个脚注的 `Separator` 属性。这是更高级的用法，但在复杂文档中非常实用。

---

## 结论

现在，您已经掌握了使用 Aspose.Words for C# **更改脚注分隔符** 和 **更改尾注分隔符** 的方法。指南涵盖了加载文档、访问相关分隔符节点、修改其文本以及保存结果——全部在一个自包含的程序中完成。

接下来，您可以进一步探索 **编辑脚注分隔符样式**、自定义脚注编号，或基于页面布局进行条件格式化等相关主题。相同的模式（获取节点 → 强制转换为 `Run` → 修改 `Text`）同样适用于许多其他 Word 处理场景。

祝编码愉快，欢迎尝试不同的符号，甚至将图片嵌入为分隔符，打造独一无二的文档布局！

## 接下来您可以学习什么？

以下教程与本指南紧密相关，帮助您在已有技术基础上进一步深入。每篇资源都提供完整的可运行代码示例和逐步解释，助您掌握更多 API 功能并探索替代实现方式。

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Insert Document Style Separator in Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}