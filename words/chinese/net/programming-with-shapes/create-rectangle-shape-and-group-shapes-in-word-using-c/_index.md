---
category: general
date: 2026-09-08
description: 使用 C# 在 Word 文档中创建矩形形状。学习设置形状大小、将多个形状分组以及以编程方式创建空白 Word 文档。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: zh
lastmod: 2026-09-08
og_description: 使用 C# 在 Word 文档中创建矩形形状。本指南展示了如何设置形状大小、对多个形状进行分组以及以编程方式创建空白 Word 文档。
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: 使用 C# 在 Word 中创建矩形形状并将形状分组
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 C# 在 Word 中创建矩形形状并将形状分组
url: /zh/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 C# 创建矩形形状并对形状进行分组

如果您需要在 Word 文件中 **create rectangle shape**，本教程提供一个完整、可直接运行的解决方案。您将看到如何 **set shape size**、对多个形状进行 **group multiple shapes**，以及从头创建一个空白 Word 文档——全部使用 Aspose.Words for .NET 库。

以编程方式处理 Word 文档通常感觉像在 juggling 许多细节。通过本指南，您将拥有一个方法，生成包含矩形和椭圆并已分组的 `.docx` 文件，随时可进行进一步编辑或打印。

## 前置条件

在开始之前，请确保您拥有：

* .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.6+）
* 已授权的 **Aspose.Words for .NET** 副本（可使用免费评估密钥）
* 如 Visual Studio 2022 或 Visual Studio Code 等 IDE
* 对 C# 语法的基本了解

无需除 `Aspose.Words` 之外的其他 NuGet 包。

## 步骤 1：创建空白 Word 文档

第一步是创建一个空文档，用于容纳形状。这满足 *create blank word document* 的要求。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

创建空白文档可为您提供干净的画布。`Document` 对象代表整个 `.docx` 文件，其 `FirstSection.Body.FirstParagraph` 是新节点的默认插入点。

## 步骤 2：创建矩形形状

现在可以添加矩形了。这正是 **create rectangle shape** 操作发生的地方。

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

直接设置尺寸即可满足 **set shape size** 关键字。所有尺寸值均以点（pt）为单位，提供对形状在最终文档中外观的精确控制。

## 步骤 3：创建额外的形状（椭圆）

典型的使用场景是组合多个形状。这里我们添加一个稍后将共享同一容器的椭圆。

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

此时两个形状仍然是独立的。下一步将展示如何 **group multiple shapes**。

## 步骤 4：在 Word 中对形状进行分组

对形状进行分组可让您将其作为单一单元移动、调整大小或格式化。这满足 **group shapes in word** 和 **group multiple shapes** 的需求。

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

`GroupShape.Bounds` 属性决定子形状的坐标系。将矩形和椭圆放入同一个 `GroupShape` 后，您可以通过一次调用一起移动或旋转它们。

## 步骤 5：保存文档

最后，将文档写入磁盘。文件将包含您刚创建的分组形状。

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

运行程序后，在 Microsoft Word 中打开 `GroupedShapes.docx`。您应该看到矩形和椭圆已被分组；选中一个形状会同时选中另一个，证明分组成功。

## 完整源代码

将以下完整程序复制到新的 console‑app 项目中并运行。无需额外代码。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### 预期输出

运行程序会生成 `GroupedShapes.docx`。在 Word 中打开该文件会看到：

* 一个 **rectangle**（100 pt × 50 pt），蓝色边框、浅灰色填充。
* 一个 **ellipse**（80 pt × 80 pt），深绿色边框、浅黄色填充。
* 两个形状位于同一组中，移动其中一个会一起移动另一个。

## 常见问题与边缘情况

| Question | Answer |
|----------|--------|
| **Can I add more than two shapes to the group?** | Yes. Create additional `Shape` objects and call `group.AppendChild(yourShape)` for each. |
| **What if I need to rotate the group?** | Set `group.RotationAngle = 45;` (degrees). All child shapes rotate together. |
| **Is it possible to group shapes after the document is saved?** | You must modify the document structure before saving; otherwise you’d need to load the file, locate the shapes, and recreate the group. |
| **Do I need to dispose of any objects?** | Aspose.Words manages its own resources, but you should dispose of `FileStream` objects if you open streams manually. |
| **Will the code work with .doc (binary) format?** | Yes, change `doc.Save("output.doc")`. The grouping behavior is identical. |

## 结论

您现在已经了解如何使用 C# 在 Word 文件中 **create rectangle shape**、**set shape size**，以及 **group multiple shapes**。此方法让您能够以编程方式构建复杂图表、水印或基于模板的报告，而无需手动编辑。

### 接下来的步骤

* 进一步探索 **group shapes in word**，通过向同一组中添加文本框或图像来实现更丰富的布局。  
* 使用 `SetShapeSize` 模式，根据页面布局动态计算尺寸。  
* 将此技术与邮件合并字段结合，批量生成个性化文档。

欢迎尝试不同的形状类型、颜色和组变换。祝编码愉快！

## 接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，每个资源都包含完整的可运行代码示例以及逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}