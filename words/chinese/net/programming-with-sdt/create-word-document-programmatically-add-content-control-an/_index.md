---
category: general
date: 2026-08-04
description: 使用 C# 编程创建 Word 文档。学习如何向 Word 添加内容控件并设置占位文本，以实现动态模板。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add content control to word
- set placeholder text word
- Aspose.Words content control
- dynamic Word template C#
language: zh
lastmod: 2026-08-04
og_description: 使用 C# 编程创建 Word 文档。本指南展示如何向 Word 添加内容控件并设置占位文本，以实现可重复使用的模板。
og_image_alt: Screenshot of a Word document with a highlighted content control placeholder
og_title: 以编程方式创建 Word 文档 – 添加内容控件和占位符
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to add content
    control to word and set placeholder text word for dynamic templates.
  headline: Create word document programmatically – add content control and placeholder
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word automation
title: 以编程方式创建 Word 文档 – 添加内容控件和占位符
url: /zh/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 以编程方式创建 Word 文档 – 添加内容控件和占位符

如果您需要**以编程方式创建 Word 文档**，本教程为您提供一个完整、可直接运行的解决方案。您将看到如何**向 Word 添加内容控件**，为其设置有意义的标题，以及**设置占位符文本**，以便最终用户稍后填写数据。

本指南逐行讲解代码，说明每一步的意义，并指出常见的陷阱。完成后，您将拥有一个可重复使用的 .docx 文件，可用作发票、合同或任何基于表单的文档模板。

## 前提条件

* 已安装 .NET 6.0（或更高版本）– 代码使用最新的 C# 语言特性。
* Aspose.Words for .NET 许可证（免费试用版可用于开发）。
* Visual Studio 2022 或任何能够构建 .NET 项目的 IDE。
* 对 C# 以及结构化文档标签（Structured Document Tags，SDT）的基本了解。

> **专业提示：**如果在没有许可证的情况下运行示例，Aspose.Words 会在保存的文件上添加一个小水印。请在程序中尽早加载许可证以避免出现水印。

## 步骤 1：设置项目并导入命名空间

创建一个新的控制台项目并添加 Aspose.Words NuGet 包。

```bash
dotnet new console -n WordTemplateDemo
cd WordTemplateDemo
dotnet add package Aspose.Words
```

在 `Program.cs` 中导入所需的命名空间：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

这些命名空间让您能够访问 `Document`、`DocumentBuilder` 和 `StructuredDocumentTag` 类，这些类对于**以编程方式创建 Word 文档**至关重要。

## 步骤 2：初始化空文档和构建器

`Document` 类表示整个 .docx 文件，而 `DocumentBuilder` 允许您在特定的光标位置插入内容。

```csharp
// Step 2: Create an empty Word document
Document document = new Document();

// Step 2b: Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*重要性说明*：从空 `Document` 开始可确保您对插入的每个元素拥有完全控制。`DocumentBuilder` 维护内部光标，使您能够在需要的位置精确插入节点。

## 步骤 3：创建纯文本结构化文档标签（SDT）

结构化文档标签是 Word 中**内容控件**的技术名称。我们将创建一个内联的纯文本标签，使其表现为占位字段。

```csharp
// Step 3: Create a plain‑text Structured Document Tag (content control)
StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
    document,
    StructuredDocumentTagType.PlainText,   // plain‑text content control
    MarkupLevel.Inline);                    // appears inside a paragraph
```

*重要性说明*：使用 `StructuredDocumentTagType.PlainText` 告诉 Word 该控件只能接受纯文本。`MarkupLevel.Inline` 使控件在段落中表现为普通文字，这对于表单字段非常合适。

## 步骤 4：分配标题和占位符文本

**标题**是您应用程序以后可以查询的内部标识符。**占位符**是在用户输入之前显示的灰色提示。

```csharp
// Step 4: Set a title and placeholder text for the content control
plainTextTag.Title = "CustomerName";          // internal name used by code
plainTextTag.PlaceholderName = "Enter name here"; // visible hint in the UI
```

这里我们将**占位符文本**设置为 “Enter name here”。当文档在 Microsoft Word 中打开时，占位符会以浅灰色显示，直到用户输入内容。

## 步骤 5：在当前光标位置插入内容控件

`DocumentBuilder.InsertNode` 将 SDT 精确放置在构建器光标所在的位置。默认情况下，光标位于第一个段落的开头。

```csharp
// Step 5: Insert the content control into the document at the builder's current position
builder.InsertNode(plainTextTag);
```

如果需要将控件放入特定段落，请先移动光标：

```csharp
builder.Writeln("Please provide the customer name:");
builder.InsertNode(plainTextTag);
```

此示例演示了如何在保留周围文本的同时**向 Word 添加内容控件**。

## 步骤 6：保存文档

最后，将文件持久化到磁盘。您可以选择任意文件夹，只需确保应用程序具有写入权限。

```csharp
// Step 6: Save the document with the content control
string outputPath = @"YOUR_DIRECTORY\SDT.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

当您在 Microsoft Word 中打开 `SDT.docx` 时，会看到占位符 “Enter name here” 显示在浅灰色框内。用户可以点击该框并将提示替换为实际的客户名称。

## 完整、可运行的示例

下面是完整的程序，您可以直接复制、粘贴并运行，无需修改（除输出路径外）。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Optional: apply your Aspose.Words license here
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new empty document
        Document document = new Document();

        // 2. Initialize a DocumentBuilder for editing the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3. Write a brief instruction line (optional)
        builder.Writeln("Please enter the customer's name below:");

        // 4. Create a plain‑text Structured Document Tag (content control)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
            document,
            StructuredDocumentTagType.PlainText,
            MarkupLevel.Inline);

        // 5. Set a title and placeholder text for the content control
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // 6. Insert the content control at the current cursor position
        builder.InsertNode(plainTextTag);

        // 7. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**预期输出** – 运行程序后，控制台会打印文件路径，生成的 Word 文件包含一行文本，随后是显示 “Enter name here” 的灰色占位符。

## 常见变体和边缘情况

| 场景 | 如何调整代码 |
|----------|-----------------------|
| **多行占位符** | 使用 `StructuredDocumentTagType.RichText` 替代 `PlainText`，并设置 `plainTextTag.MultipleLines = true;`。 |
| **重复相同控件** | 使用 `plainTextTag.Clone(true)` 克隆标签，并在需要的地方插入克隆对象。 |
| **绑定到数据源** | 用户填写文档后，可使用 `document.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().First(t => t.Title == "CustomerName").GetText();` 获取其值。 |
| **锁定控件** | 将 `plainTextTag.LockContentControl = true;` 设置为 true，以防止用户删除控件。 |
| **更改占位符颜色** | Word 通过 SDK 未公开占位符样式；您需要手动编辑模板或使用 Word 宏。 |

## 最佳实践与故障排除

* **始终设置标题** – 如果没有标题，后续定位控件会非常麻烦。
* **避免空占位符** – 如果控件的 `ShowPlaceholderText` 属性为 false，Word 会隐藏空占位符。请保持其为 true，以获得更好的用户体验。
* **验证输出路径** – 如果 `document.Save` 抛出 `UnauthorizedAccessException`，请确保文件夹存在且进程具有写入权限。
* **尽早加载许可证** – 在实例化任何 Aspose.Words 对象之前放置许可证代码，以防止出现试用水印。

## 结论

现在，您已经了解如何使用 Aspose.Words for .NET **以编程方式创建 Word 文档**、**向 Word 添加内容控件**以及**设置占位符文本**。完整示例展示了从初始化文档到持久化模板的每一步，供最终用户填写。

接下来，您可以探索：

* 为表格添加**重复内容控件**（次要关键词：add content control to word）。
* 使用数据库数据填充占位符（次要关键词：set placeholder text word）。
* 将生成的 .docx 转换为 PDF 或 HTML 以进行后续处理。

欢迎尝试不同的标签类型、样式和数据绑定技术。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南紧密相关的主题，基于所示技术进行深入。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [创建新 Word 文档](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [使用 Aspose.Words 创建带页眉页脚的 Word 文档](/words/english/net/header-footer-formatting/create-header-footer/)
- [使用 Aspose.Words 创建带表格的 Word 文档](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}