---
category: general
date: 2026-08-10
description: 使用 C# 在 Word 中插入矩形形状。了解如何隐藏形状、在 Word 中隐藏形状，以及使用 Aspose.Words 创建隐藏形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: zh
lastmod: 2026-08-10
og_description: 使用 C# 在 Word 中插入矩形形状。本教程解释如何隐藏形状、在 Word 中隐藏形状，以及使用完整代码示例创建隐藏形状。
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: 使用 C# 在 Word 中插入矩形形状 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 C# 在 Word 中插入矩形形状 – 完整指南
url: /zh/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 在 Word 中插入矩形形状 – 完整指南

如果你需要 **在 Word 文档中插入矩形形状**，本指南将为你展示完整步骤。你还将学习 **如何隐藏形状** 使其在最终文件中不出现，这回答了常见的查询 **hide shape in Word**，并演示了如何以编程方式 **create hidden shape**。

本教程涵盖了从设置 Aspose.Words SDK 到验证形状已隐藏的全部内容。阅读完本文后，你将拥有一段可在任何 .NET 项目中直接使用的可复用代码片段。

## Prerequisites

在开始之前，请确保你已具备：

- 已安装 .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.6+）
- 有效的 Aspose.Words for .NET 许可证或临时评估密钥
- Visual Studio 2022（或任何支持 C# 的 IDE）
- 对 C# 语法以及 Word 文件的文档对象模型（DOM）有基本了解

除 `Aspose.Words` 之外，无需额外的 NuGet 包。

## Step 1: Create a new blank document and a DocumentBuilder

第一步是实例化一个 `Document` 对象。`DocumentBuilder` 提供了便捷的 API，用于插入形状、段落和表格等内容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**为什么这很重要：** `Document` 代表整个 .docx 文件，而 `DocumentBuilder` 维护一个光标，跟踪下一个元素将被放置的位置。初始化这两个对象是任何 Word 自动化任务的基础。

## Step 2: Insert rectangle shape

现在插入矩形。`InsertShape` 方法需要指定形状类型以及以点为单位的尺寸（1 点 ≈ 1/72 英寸）。**200 × 100 点** 大小约为 2.78 × 1.39 英寸的矩形。

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**为什么这很重要：** 你得到的 `Shape` 对象可以完全配置——颜色、边框、文本以及可见性都可以在保存文档之前进行修改。

## Step 3: Hide the shape

为了防止矩形被显示或打印，将其 `Hidden` 属性设为 `true`。该属性直接映射到 Word 的 “Hidden” 属性，Word 在视图和打印模式下都会遵循此设置。

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**为什么这很重要：** 将 `Hidden` 设置为 **hide shape in Word** 的标准方式，而不会从文档结构中移除形状。形状仍然可以被代码访问，便于后续的条件格式化或数据驱动的可见性切换。

## Step 4: Save the document

最后，将文档持久化到磁盘。可以选择任意文件夹；示例中使用的是占位路径，请自行替换为真实路径。

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**为什么这很重要：** 保存操作会将隐藏标志写入底层 Open XML。当你在 Microsoft Word 中打开文档时，矩形将不可见，证明你已经成功 **created hidden shape**。

## Step 5: Verify the hidden shape

在 Microsoft Word 中打开生成的 `HiddenShape.docx`：

1. 进入 **文件 → 选项 → 显示**，确保 *“显示隐藏文本”* 未勾选。  
2. 矩形在任何页面上都不应可见。  
3. 为了再次确认，启用 *“显示隐藏文本”*；矩形会以淡淡的虚线轮廓出现，证明形状仍然存在但被隐藏。

如果矩形仍然可见，请检查是否在设置 `Hidden = true` 后保存了文件，并确认打开的是正确的文件。

## Full runnable example

下面是完整的程序代码，你可以直接复制、粘贴并运行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**预期输出：** 控制台会打印文件路径和一条简短提示。打开 Word 时，除非启用隐藏文本，否则矩形是不可见的。

## Common questions and edge cases

### Can I hide only the outline but keep the fill visible?

可以。不要设置 `Hidden = true`，而是将 `rectangle.LineFormat.Visible = false`，这样可以隐藏边框而保留填充颜色。这是 **how to hide shape** 的一种变体，保留了部分视觉效果。

### Does the hidden flag work in older Word versions (2003, 2007)?

隐藏属性是随 Word 2007 引入的 Open XML 规范的一部分。使用旧的二进制 `.doc` 格式保存的文档不会保留该标志。若需兼容旧格式，请将文档保存为 `.docx`，必要时可使用 Aspose.Words 的 `SaveFormat.Doc` 进行后续转换。

### What if I need to hide multiple shapes at once?

遍历 `Document.GetChildNodes(NodeType.Shape, true)` 集合，对符合条件的每个形状（例如特定的 `ShapeType` 或自定义的 `AlternativeText`）设置 `Hidden = true`。

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### Is there a performance impact when hiding shapes?

隐藏标志只会在 XML 中添加一个极小的属性，对渲染速度几乎没有影响。不过，隐藏对象数量非常大时会略微增加文件体积。建议删除不再需要的形状，以保持文档精简。

## Tips and best practices

- **为形状指定有意义的名称**，如 `rectangle.Name = "MyHiddenRectangle"`；这有助于后续在 DOM 中搜索该形状。  
- **设置 `AlternativeText`** 为自定义标签（例如 `"HiddenShape"`），可在不依赖索引的情况下定位形状。  
- **将代码包装在 try‑catch 块中**，以优雅地处理许可证错误或 I/O 异常。  
- **在保存后释放 Document**，如果在循环中处理大量文件，可调用 `document.Dispose();` 释放非托管资源。

## Conclusion

现在，你已经掌握了如何使用 C# **在 Word 文档中插入矩形形状**、如何 **hide shape in Word**，以及如何 **create hidden shape**——即形状仍然是文档结构的一部分，但对最终用户不可见。完整的可运行示例展示了从文档创建到验证的全部工作流。

接下来，你可以探索基于用户输入的 **how to hide shape**，或将隐藏形状与内容控件结合，实现动态文档生成。相同技术同样适用于椭圆、箭头或自定义绘图等其他形状类型。

欢迎尝试不同的尺寸、颜色和可见性设置。如果遇到问题，请回顾上述步骤或查阅 Aspose.Words 文档获取更深入的 API 细节。祝编码愉快！

## What Should You Learn Next?

以下教程涵盖了与本指南技术紧密相关的主题，帮助你在项目中进一步扩展 API 功能并探索替代实现方式，每篇资源均提供完整可运行的代码示例和逐步解释。

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}