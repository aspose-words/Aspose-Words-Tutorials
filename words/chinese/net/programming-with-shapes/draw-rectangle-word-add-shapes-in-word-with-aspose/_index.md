---
category: general
date: 2026-07-29
description: 使用 Aspose.Words 绘制矩形文字。了解如何添加矩形形状、添加线形状，以及在单个文档中管理多个形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: zh
lastmod: 2026-07-29
og_description: 使用 Aspose.Words 在 Word 中绘制矩形。请按照本分步指南添加矩形形状、添加线形状，并轻松处理 Word 中的多个形状。
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: 在 Word 中绘制矩形 – 掌握在 Word 中添加形状
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: 在 Word 中绘制矩形 – 使用 Aspose 添加形状
url: /zh/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – 在 Word 中添加形状的完整指南

是否曾想过如何在不每次打开 UI 的情况下 **draw rectangle word** 文档？你并不孤单。许多开发者需要即时生成 Word 文件，最简单的方法是让库来完成繁重的工作。在本教程中，我们将向您展示如何 **add shapes**——具体来说是矩形和直线——使用 Aspose.Words for .NET，并且我们将重点放在 *draw rectangle word* 这一短语上，确保您不会迷失。

把它想象成一个居于代码内部的迷你艺术工作室。完成后，您将能够 **add rectangle shape**、**add line shape**，甚至将它们组合成 **multiple shapes word** 组。无需 UI，无需手动操作，只需干净、可重复的 C#。

## 您将学习的内容

- 使用 Aspose.Words 设置一个新的 Word 文档。  
- 创建一个可以容纳多个对象的 **GroupShape**。  
- 在该组内 **add rectangle shape** 和 **add line shape**。  
- 将分组的形状插入文档主体。  
- 保存文件并立即查看结果。  

如果您熟悉基本的 C# 并拥有 Aspose.Words 的副本，您已经准备就绪。除核心库外，无需额外的 NuGet 包。

> **专业提示：** Aspose.Words 支持 .NET 6、.NET 7 和 .NET Framework 4.6+。请选择与您的项目匹配的运行时。

![draw rectangle word example](https://example.com/placeholder-image.png "draw rectangle word – grouped shapes in a Word file")

## draw rectangle word – 设置文档

在我们能够 **draw rectangle word** 之前，需要一个干净的画布。`Document` 类就是该画布；`DocumentBuilder` 是我们的画笔。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

上面的两行代码为我们提供了一个全新的、内存中的 `.docx`。尚未写入磁盘，这意味着我们可以在不弄乱文件系统的情况下进行实验。

## 如何添加形状 – 创建 GroupShape 容器

当您希望 **multiple shapes word** 像单个单元一样行为——一起移动、一起旋转——可以将它们包装在 `GroupShape` 中。把组想象成一个容纳其他形状的文件夹。

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

为什么要使用组？因为之后您可能想要 **add rectangle shape** 和 **add line shape**，然后一起移动它们。如果没有组，您必须单独重新定位每个形状。

## add rectangle shape – 在组内插入矩形

现在容器已经存在，让我们 **add rectangle shape**。矩形是 `Shape`，其 `ShapeType` 为 `Rectangle`。

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

请注意，`Left` 和 `Top` 值是相对于组的原点，而不是页面。这使得精确对齐形状变得容易。矩形将出现在组的左上角附近。

## add line shape – 向同一组添加直线

直线只是另一个 `Shape`，但其 `ShapeType` 为 `Line`。我们将在矩形下方放置它。

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

由于直线的高度为零，`Top` 属性决定了直线在垂直方向上的位置。`Width` 控制直线在水平方向的长度。

## multiple shapes word – 将组插入文档主体

我们已经有一个包含 **add rectangle shape** 和 **add line shape** 的组。最后一步是将整个组放入文档中。

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` 将组精确放置在 `DocumentBuilder` 当前所在的位置。如果需要放在特定段落，请先使用 `builder.MoveToParagraph(index)` 移动构建器。

## 保存结果 – 查看 draw rectangle word 输出

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

在 Microsoft Word 中打开生成的文件，您会看到一个包含矩形和直线的单一组。您可以点击该组，拖动它，甚至调整大小——所有形状都会一起移动。这就是 **multiple shapes word** 的强大之处。

### 预期输出

- 一个名为 `GroupShape.docx` 的 `.docx` 文件。  
- 单页上在左上角附近有一个分组的矩形（120 × 80 pt）。  
- 一条水平线（长 150 pt），位于矩形正下方。  
- 两个形状可作为单个对象被选中。

如果双击该组，Word 将允许您单独编辑每个形状——非常适合微调。

## 常见问题与边缘情况

**如果我需要超过两个形状怎么办？**  
只需对每个额外对象调用 `group.AppendChild(yourShape)`。组可以容纳任意数量的形状，非常适合复杂图表。

**我可以更改矩形的填充颜色吗？**  
当然可以。在创建矩形后，设置 `rectangle.FillColor = System.Drawing.Color.LightBlue;`。这适用于任何支持填充的形状。

**我必须为直线设置 `Height = 0` 吗？**  
是的，对于水平直线，高度应为零。对于垂直直线，设置 `Width = 0` 并为 `Height` 赋予正值。

**这能在 .doc 文件（Word 97‑2003）中工作吗？**  
Aspose.Words 可以保存为旧的 `.doc` 格式，但某些现代形状功能可能受限。请使用 `.docx` 以获得完整保真度。

**如何旋转整个组？**  
您可以在插入之前设置 `group.Rotation = 45;`（度数）。旋转会应用于每个子形状。

## 回顾 – 如何在 Word 中以编程方式添加形状

- **draw rectangle word** 从创建 `Document` 和 `DocumentBuilder` 开始。  
- 构建一个 **GroupShape** 来容纳 **multiple shapes word**。  
- **add rectangle shape** 和 **add line shape** 被追加到组中。  
- 使用 `builder.InsertNode` 将组插入主体。  
- 保存文件并打开以验证视觉结果。

这就是完整的工作流，全部封装在一个易于阅读的代码示例中。

## 后续步骤与相关主题

既然您已经了解 **how to add shapes**，可以考虑探索以下内容：

- 使用圆角的 **add rectangle shape**（`ShapeType.Rectangle` + `CornerRadius`）。  
- 使用不同虚线模式为线条设置样式（`line.LineFormat.DashStyle`）。  
- 将图像嵌入形状旁以生成更丰富的报告。  
- 使用 **multiple shapes word** 构建流程图或简单的 UML 图表。  

这些主题都自然地建立在我们这里奠定的基础之上，并且都遵循相同的模式：创建形状、配置它们，并在需要时进行分组。

---

祝编码愉快！如果遇到问题或有酷炫的使用案例想分享，请在下方留言。您的反馈帮助大家掌握 **draw rectangle word** 及其更广阔的艺术。

## 接下来应该学习什么？

以下教程涵盖与本指南紧密相关的主题，构建在本指南演示的技术之上。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在自己的项目中探索替代实现方法。

- [在 Word 中使用 C# 创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [使用 Aspose.Words 在 Word 中创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [使用 Aspose.Words for .NET 在 Word 文档中插入形状](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}