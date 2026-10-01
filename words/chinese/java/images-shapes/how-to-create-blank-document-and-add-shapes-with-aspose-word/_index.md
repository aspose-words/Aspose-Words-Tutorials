---
category: general
date: 2026-09-30
description: 使用 Aspose.Words 在 C# 中创建空白文档并插入矩形、椭圆以及对多个形状进行分组。了解如何插入形状以及如何创建分组。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: zh
lastmod: 2026-09-30
og_description: 在 C# 中创建空白文档，学习如何使用 Aspose.Words 插入形状并对多个形状进行分组。请按照分步教程操作。
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: 在 C# 中创建空白文档并对形状进行分组 – Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: 如何使用 Aspose.Words 在 C# 中创建空白文档并添加形状
url: /zh/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words 在 C# 中创建空白文档并添加形状

如果您需要 **创建空白文档** 并用图形填充它，本指南将准确展示操作步骤。您将看到如何 **插入矩形形状**、添加其他绘图对象，然后 **将多个形状分组** 使其表现为一个整体。

在生成合同、证书或自定义报告时，处理形状是常见需求。在本教程中，您将学习完整的工作流程，从初始化文档到保存最终文件，使用 Aspose.Words API for .NET。

## 前提条件

* .NET 6.0（或更高）SDK 已安装  
* 有效的 Aspose.Words for .NET 许可证（免费试用版可用于本示例）  
* 如 Visual Studio 2022 或 Visual Studio Code 等 IDE  

除 `Aspose.Words` 外，无需其他 NuGet 包。

## 如何创建空白文档并使用形状

第一步是实例化一个 `Document` 对象。该对象代表内存中的 Word 文件，并提供对 `DocumentBuilder` 的访问，后者是插入内容的主要工具。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**为什么这很重要：** 空白文档为您提供了干净的画布。`DocumentBuilder` 维护当前插入点，因此您添加的每个形状都会自动放置在相应的页面上。

## 插入矩形形状及其他形状

接下来，我们添加一个矩形和一个椭圆。这两个调用都使用相同的 `InsertShape` 方法，这是在 Aspose.Words 中 **如何插入形状** 的推荐方式。

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*`InsertShape` 方法会自动将形状定位在当前光标位置。* 如果需要精确定位，您可以在插入后调整 `Shape.Left` 和 `Shape.Top`。

## 将多个形状分组为单个对象

现在我们将矩形和椭圆组合成一个逻辑实体。分组在您希望一起移动或调整多个形状大小时非常有用。

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**工作原理：** `InsertGroupShape` 创建一个容器，其行为类似于其他 `Shape`。通过调用 `AppendChild`，您将现有形状移动到该容器中，容器会自动更新它们的相对坐标。

### 实用技巧

如果以后需要为超过两个形状以编程方式 **如何创建分组**，只需对每个额外的 `Shape` 实例重复 `AppendChild`。该组可以包含任意数量的绘图对象，包括图片、文本框，甚至其他组。

## 完整示例 – 如何插入形状并保存文档

下面是完整的可运行程序，演示了迄今为止讨论的每一步。运行代码会生成一个 `ShapesDemo.docx` 文件，其中包含矩形、椭圆和一个分组形状。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**预期输出：** 在 Microsoft Word 中打开 `ShapesDemo.docx`，会看到单页上有一个蓝色矩形、一个绿色椭圆，以及表示该组的灰色边框。移动该组会一起移动两个形状，确认 **分组多个形状** 操作成功。

## 常见问题及边缘情况处理

| 问题 | 答案 |
|----------|--------|
| *如果我需要形状位于特定页面怎么办？* | 在插入形状之前调用 `builder.MoveToDocumentEnd();`，或使用 `builder.MoveToSection(sectionIndex);` 定位到特定章节。 |
| *我可以在分组形状内部添加文本吗？* | 可以。创建类型为 `ShapeType.TextBox` 的 `Shape`，配置其文本，然后将其 `AppendChild` 到 `GroupShape` 中。 |
| *形状尺寸使用点还是像素？* | Aspose.Words 使用 **点**（1 pt = 1/72 英寸）。这可确保在打印机和显示器之间保持一致的尺寸。 |
| *如何更改组的旋转？* | 将 `groupShape.RotationAngle = 45;`（度）设置即可。所有子形状围绕组的原点旋转。 |

## 结论

现在您已经了解如何使用 Aspose.Words for .NET **创建空白文档**、**插入矩形形状**、**如何插入形状**（如椭圆），以及 **将多个形状分组** 为单个对象。完整的代码示例展示了推荐的做法，上述技巧帮助您将解决方案适配到更复杂的场景，例如添加文本框或旋转组。

准备好进一步探索了吗？尝试向组中添加图片形状，实验不同的填充颜色，或生成每页都包含各自分组图表的多页报告。相同的原理适用于所有情况，您可以将此模式扩展到任何文档自动化项目。

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能，并在自己的项目中探索替代实现方法。

- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words for .NET 在 Word 文档中插入形状](/words/english/net/working-with-shapes/insert-shape/)
- [使用 Aspose.Words 创建空白 Word 文档 – 步骤指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}