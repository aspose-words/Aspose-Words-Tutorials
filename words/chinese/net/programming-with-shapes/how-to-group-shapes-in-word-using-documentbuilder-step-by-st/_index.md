---
category: general
date: 2026-09-08
description: 学习如何使用 DocumentBuilder 在 Word 中对形状进行分组，创建空白 Word 文档，并仅用几行 C# 代码插入矩形形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: zh
lastmod: 2026-09-08
og_description: 使用 DocumentBuilder 在 Word 中对形状进行分组。本教程展示了如何创建空白 Word 文档、插入矩形形状以及将形状合并为
  GroupShape。
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: 使用 DocumentBuilder 在 Word 中对形状进行分组 – 完整 C# 示例
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 DocumentBuilder 在 Word 中对形状进行分组 – 步骤指南
url: /zh/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 DocumentBuilder 在 Word 中对形状进行分组 – 步骤指南

如果您需要以编程方式 **在 Word 中对形状进行分组**，本教程展示了一个完整的 C# 解决方案。您将看到如何 **创建一个空白 Word 文档**，使用 **DocumentBuilder**，以及 **插入矩形形状**，随后将其与椭圆进行分组。结果是一个单一的 `GroupShape`，您可以将其作为一个对象进行移动、调整大小或设置样式。

本指南涵盖了使用 Aspose.Words for .NET 库生成带有分组图形的 Word 文档所需的全部内容。阅读完本文后，您将拥有一个可运行的项目，生成的 `GroupedShapes.docx` 包含一个矩形和一个椭圆组合成的单个形状。

## 先决条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.7.2+）
- Aspose.Words for .NET NuGet 包（`Aspose.Words`）– 版本 23.12 或更新
- Visual Studio 2022、Visual Studio Code 等 C# IDE
- 对 C# 语法和面向对象编程有基本了解

> **专业提示：** 从命令行安装 NuGet 包以保持项目整洁：  
> `dotnet add package Aspose.Words --version 23.12.0`

## 第 1 步：创建空白 Word 文档

首先实例化一个 `Document` 对象，它代表一个空的 Word 文件，并创建一个 `DocumentBuilder` 用于添加内容。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**为什么重要：** `Document` 提供文件容器，而 `DocumentBuilder` 则提供流式 API 用于插入文本、图像和形状。如果没有 `DocumentBuilder`，您必须手动操作文档的节点树，容易出错。

## 第 2 步：插入矩形形状

矩形是绘制图表的常用构件。使用 `InsertShape` 并传入 `ShapeType.Rectangle`，同时以点为单位指定宽度和高度（1 pt ≈ 1/72 in）。

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**为什么重要：** 设置 `Left` 和 `Top` 可以精确定位矩形在页面上的位置，这在后续将其与其他形状分组时至关重要。`InsertShape` 方法会自动将形状添加到当前段落。

## 第 3 步：插入椭圆形状

接下来，添加一个将位于矩形旁边的椭圆。

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**为什么重要：** 使用不同的 `ShapeType` 演示了相同的 `DocumentBuilder` API 能创建多样化的图形。将椭圆定位使其与矩形重叠，可清晰展示分组效果。

## 第 4 步：将两个形状分组

`GroupShape` 类似于一个容器。将矩形和椭圆作为子对象追加后，它们就表现为单一对象。

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**为什么重要：** `Bounds` 属性告诉 Word 该组在页面上的位置。通过追加子形状，您保留了它们各自的格式，同时能够对整个组执行统一的变换（移动、旋转、缩放）。

## 第 5 步：保存文档

最后，将文档写入磁盘。您可以将路径更改为任意文件夹。

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

打开 Microsoft Word 中的 `GroupedShapes.docx`，您会看到矩形和椭圆已被分组。选中该组时，两种形状都会被高亮，您可以像操作单个对象一样拖动或调整大小。

### 预期输出

- 一个名为 **GroupedShapes.docx** 的 Word 文件
- 第 1 页包含一个 **矩形**（100 pt × 50 pt），位置为 (50, 50)
- 一个 **椭圆**（80 pt × 80 pt），位置为 (200, 70)
- 两个形状均属于一个 **GroupShape**，其边界框为 300 pt × 200 pt

## 常见变体和边缘情况

| 场景 | 调整 |
|----------|------------|
| **不同的页面尺寸** | Set `document.Sections[0].PageSetup.PageWidth` and `PageHeight` before inserting shapes. |
| **超过两个形状** | Create additional `Shape` objects and call `groupShape.AppendChild(newShape)` for each. |
| **应用填充颜色** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **旋转整个组** | `groupShape.Rotation = 45;` (degrees) |
| **导出为 PDF** | After saving the DOCX, call `document.Save("GroupedShapes.pdf");` |

## 完整源代码（可直接运行）

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

将代码复制到新的控制台项目中，恢复 Aspose.Words NuGet 包后运行。控制台会确认文件位置，打开文件即可看到分组的图形。

## 结论

现在您已经掌握了使用 Aspose.Words `DocumentBuilder` **在 Word 中对形状进行分组** 的方法。教程演示了创建 **空白 Word 文档**、**插入矩形形状**、添加椭圆并将它们组合成 `GroupShape` 的完整过程。基于此，您可以直接从 C# 构建更丰富的图表、流程图或自定义图形。

### 接下来可以做什么？

- 探索 **如何使用 DocumentBuilder** 创建表格、页眉和页脚。
- 将 **插入矩形形状 Word** 技术与文本框结合，用于带注释的图示。
- 使用 **创建空白 Word 文档** 作为模板，实现自动化报告生成。

随意尝试颜色、渐变和更多形状。祝编码愉快！

## 您接下来应该学习什么？

以下教程涵盖了与本指南技术密切相关的主题，可帮助您进一步掌握 API 功能并在项目中探索替代实现方式。每篇资源均提供完整可运行的代码示例和逐步解释。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}