---
category: general
date: 2026-08-14
description: 如何使用 Aspose.Words 快速添加 SDT。学习在 .docx 文件中创建 Word 占位符并插入纯文本控件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: zh
lastmod: 2026-08-14
og_description: 如何在 C# 中使用 Aspose.Words 添加 SDT。请按照本教程创建 Word 占位符并插入纯文本控件，以实现动态文档。
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: 如何在 C# 中添加 SDT – 步骤式 Word 占位符指南
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: 如何在 C# 中添加 SDT – Word 占位符完整指南
url: /zh/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中添加 SDT – Word 占位符完整指南

如果您需要在 Word 文件中 **how to add sdt**，本教程将展示使用 Aspose.Words for .NET 的具体步骤。完成本指南后，您将能够 **create word placeholder** 标签，让最终用户直接在文档中输入，并且您将了解如何可靠地 **insert plain text control**。

使用结构化文档标签（SDT）可以消除手动表单字段的需求，并为您提供一种干净、可编程的方式来构建动态合同、报告或信函。下面的示例涵盖了从项目设置到保存最终 .docx 文件的全部内容，您可以将代码复制粘贴到自己的解决方案中，而不会遗漏任何依赖。

## 前提条件

- .NET 6.0 或更高（代码同样适用于 .NET Framework 4.6+）
- Visual Studio 2022 或您喜欢的任何 C# IDE
- Aspose.Words for .NET 许可证（免费临时许可证可用于测试）
- 对 C# 语法和 SDT 概念有基本了解

> **专业提示：** 如果您计划分发生成的文档，请嵌入许可证文件以避免评估水印。

## 第一步：设置项目并导入 Aspose.Words

创建一个新的控制台应用程序并添加 Aspose.Words NuGet 包：

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

这些 `using` 指令让您能够访问 `Document`、`DocumentBuilder` 和 `StructuredDocumentTag` 类，这些类是进行 **insert plain text control** 操作所必需的。

## 第二步：初始化文档和构建器

第一个代码块创建一个空的 Word 文档以及一个 `DocumentBuilder`，它允许您向其中写入内容。

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` 的工作方式类似于光标；每一次后续调用都会在当前位址添加内容。初始化文档是每个 **how to add sdt** 场景的基础，因为 SDT 必须属于一个活动的 `Document` 实例。

## 第三步：插入纯文本结构化文档标签（SDT）

现在我们 **insert plain text control**，它充当占位符，用户可以在其中输入姓名、日期或任何自定义值。

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` 告诉 Aspose.Words 创建一个简单的文本字段。
- `SdtAppearanceTags.Default` 为标签提供标准的 Word 可视样式（在 Word 中打开文档时显示为带阴影的框）。

## 第四步：使用标题和占位符文本配置 SDT

一个命名合理的 SDT 能让文档对最终用户自解释。在这里我们 **create word placeholder** 元数据并设置出现在字段内部的提示。

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` 是内部标识符，您可以在以后以编程方式提取或更新值时使用。
- `PlaceholderName` 是在 Word 中显示的灰色提示，告诉用户应输入什么内容。

## 第五步：添加周围内容

文档很少只包含单个 SDT。通常需要在占位符前后添加常规段落。使用构建器的 `WriteLine` 方法来添加静态文本。

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

对 `InsertNode` 的调用会将先前创建的 SDT 放置在您需要的位置，保持周围文本的流畅。

## 第六步：将文档保存为 .docx 文件

最后，将文档持久化到磁盘。路径可以是绝对路径，也可以是相对于项目文件夹的路径。

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

在 Microsoft Word 中打开 `SDT.docx` 时，会显示一个灰色占位符，内容为 **Enter name here**。用户可以点击该字段，输入值，文档在再次保存时会保留该值。

## 完整、可运行的示例

将所有部分组合在一起，即可得到一个自包含的程序，您可以立即运行：

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**预期输出** 当您运行程序时：

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

打开生成的 `SDT.docx` 会显示：

```
Dear [Enter name here],
After the SDT
```

方括号中的文本是 **insert plain text control** 占位符，用户可以替换它。

## 常见变体和边缘情况

| 情况 | 代码适配方式 |
|-----------|-----------------------|
| **Multiple placeholders** | 重复调用 `InsertStructuredDocumentTag`，并为每个标签提供唯一的 `Title`。 |
| **Rich‑text SDT** | 使用 `StructuredDocumentTagType.RichText` 替代 `PlainText`。 |
| **Lock the placeholder** | 设置 `plainTextTag.LockContentControl = true;` 以防止用户删除该字段。 |
| **Pre‑populate with a value** | 在保存之前，将 `plainTextTag.Text = "John Doe";` 赋值。 |
| **Conditional appearance** | 使用 `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` 创建复选框控件。 |

这些变体让您能够 **create word placeholder** 结构，以匹配几乎所有表单式场景。

## 故障排除技巧

- **Placeholder not visible** – 确保您在 Microsoft Word（或兼容的查看器）中打开文件。一些轻量级编辑器会隐藏 SDT。
- **License warning** – 如果看到评估水印，请确认您的许可证文件已正确加载（`License license = new License(); license.SetLicense("Aspose.Words.lic");`）。
- **Incorrect cursor position** – 插入 SDT 后，构建器的光标仍然位于标签 *之后*。如果需要在标签 *内部* 添加文本，请在写入前使用 `builder.MoveTo(plainTextTag);`。

## 结论

您现在已经了解如何使用 Aspose.Words for .NET **how to add sdt** 到 Word 文档，如何 **create word placeholder** 标签，以及如何 **insert plain text control** 让用户直接在 Word 中编辑。完整示例演示了初始化、标签插入、配置、周围内容以及保存——全部在一个可运行的程序中完成。

接下来，探索相关主题，例如 **insert rich text control**、**populate SDTs from a database** 或 **convert the final document to PDF**。所有这些都基于本指南中涵盖的相同基础，您可以自信地扩展自动化流水线。

祝编码愉快，欢迎尝试不同的 SDT 类型，以满足您的文档自动化需求！

## 接下来您应该学习什么？

以下教程涵盖与本指南紧密相关的主题，基于本指南展示的技术。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在自己的项目中探索替代实现方法。

- [如何使用 Aspose.Words for Java 中的 DocumentBuilder 创建表单字段并添加内容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [如何使用 Aspose.Words for Java 在只读文档中创建可编辑范围](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [使用 Aspose.Words for Java 添加 Word 书签 – 插入、更新、删除](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}