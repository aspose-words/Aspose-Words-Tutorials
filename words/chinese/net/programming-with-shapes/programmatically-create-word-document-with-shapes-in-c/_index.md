---
category: general
date: 2026-11-22
description: 在 C# 中以编程方式创建 Word 文档，插入矩形形状、插入多个形状，并使用 Aspose.Words 将形状写入 Word。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: zh
lastmod: 2026-11-22
og_description: 使用 C# 通过编程方式创建 Word 文档，插入矩形形状、插入多个形状，并使用 Aspose.Words 将形状写入 Word。
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: 使用 C# 编程创建带有形状的 Word 文档
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: 在 C# 中以编程方式创建带形状的 Word 文档
url: /zh/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 编程方式创建带形状的 Word 文档

如果您需要 **以编程方式创建包含自定义图形的 Word 文档**，本指南将展示如何使用 Aspose.Words for .NET 实现。您将学习插入矩形形状、添加其他形状、将它们分组，最后将形状写入 Word——全部只需几行 C# 代码。

使用图形创建 Word 文件不再需要手动编辑或宏脚本。完成本教程后，您将拥有一个可复用的方法，生成包含矩形和椭圆组合在一起的 `.docx` 文件，便于后续处理或报告。

## 您需要的环境

- .NET 6.0 或更高（代码同样适用于 .NET Framework 4.6+）
- Aspose.Words for .NET（NuGet 包 `Aspose.Words`）
- 如 Visual Studio 2022 等 IDE（任何能够编译 C# 的编辑器均可）

> **Pro tip:** 在开始编码前，使用 CLI 命令 `dotnet add package Aspose.Words` 安装该包。

## 编程方式创建 Word 文档 – 概览

整体流程分为三个逻辑阶段：

1. **初始化** 一个新的 `Document` 和 `DocumentBuilder`。  
2. **插入多个形状**（矩形和椭圆），并将它们放入 `GroupShape` 中。  
3. **将形状写入 Word**，通过将 `Document` 保存为 `.docx` 文件。

每个阶段在下面都有对应的步骤，您可以直接复制粘贴代码到项目中。

![以编程方式创建带分组形状的 Word 文档](grouped-shapes.png){: .align-center alt="以编程方式创建带分组形状的 Word 文档"}

## 步骤 1：初始化文档和构建器

`Document` 类代表整个 Word 文件，而 `DocumentBuilder` 提供流式 API 用于添加内容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*为什么重要：* 首先创建 `Document` 能为您提供一个干净的画布。`DocumentBuilder` 会跟踪当前的插入点，这在后续将形状附加到段落层次结构时至关重要。

## 步骤 2：插入分组形状容器

`GroupShape` 允许您将多个单独的形状视为一个整体。当您希望一起移动或缩放它们时，这非常有用。

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*说明：* `InsertGroupShape` 会插入一个空容器并自动将其设为当前形状。随后所有的形状插入都会添加到该容器中，直到您关闭分组。

## 插入矩形形状

现在我们添加第一个图形——矩形。这满足 **插入矩形形状** 的需求。

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

矩形继承了分组的格式上下文，因此会出现在 `GroupShape` 内。您以后也可以设置线条颜色、填充或文字等属性。

## 插入多个形状

为了演示 **插入多个形状** 的能力，我们在矩形后面添加一个椭圆。您可以在关闭分组之前继续添加任意数量的形状（例如三角形、星形）。

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

此时分组中包含两个不同的形状：一个矩形和一个椭圆。因为它们共享同一个父级，您可以将它们作为一个整体移动。

## 步骤 3：将分组形状附加到段落层次结构

Word 文档将内容存储在段落树中。要让分组在最终文件中可见，必须将其附加到当前段落。

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*为什么需要此步骤：* 如果不将分组追加到段落，形状仅存在于内存中，保存文档时会被省略。

## 步骤 4：保存文档 – 将形状写入 Word

最后，我们将内存中的 `Document` 持久化到磁盘。这实现了 **将形状写入 Word** 的目标。

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

当您在 Microsoft Word 中打开 `GroupShape.docx` 时，会看到一个矩形（100 pt × 50 pt）和一个椭圆（80 pt × 40 pt）已被分组，正如代码所插入的那样。

### 预期输出

- 项目输出文件夹中生成名为 **GroupShape.docx** 的文件。
- 在 Word 文件中：单个段落包含一个分组的矩形（100 pt × 50 pt）和一个椭圆（80 pt × 40 pt）。选中任意一个形状都会选中整个组。

## 处理常见边缘情况

| 情况 | 建议 |
|-----------|----------------|
| **不同 DPI 或页面尺寸** | 在插入形状前显式设置 `builder.PageSetup.PaperSize`，以避免意外的缩放。 |
| **需要精确定位形状** | 使用 `builder.MoveTo` 移动插入点，然后设置 `groupShape.Left` 和 `groupShape.Top` 属性（单位为点）。 |


## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。

- [Create Word Document – Insert Rectangle Shape & Shadow in C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Create word document programmatically and group shapes in C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programmatically create a Word document with a group shape](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}