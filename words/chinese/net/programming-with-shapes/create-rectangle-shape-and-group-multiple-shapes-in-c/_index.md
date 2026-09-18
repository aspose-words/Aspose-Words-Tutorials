---
category: general
date: 2026-09-18
description: 使用 C# 在 Word 文档中创建矩形形状。了解如何添加多个形状、将形状添加到组以及使用 Aspose.Words 插入组形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: zh
lastmod: 2026-09-18
og_description: 使用 C# 在 Word 文件中创建矩形形状。本指南展示了如何添加多个形状、将形状添加到组以及使用 Aspose.Words 插入组形状。
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: 在 C# 中创建矩形形状并将形状分组
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: 在 C# 中创建矩形形状并对多个形状进行分组
url: /zh/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中创建矩形形状并对多个形状进行分组

如果您需要在 Word 文档中 **创建矩形形状**，本教程提供完整解决方案。您将看到如何 **添加多个形状**、**将形状添加到组**，以及使用 Aspose.Words for .NET API **插入组形状**。

在以编程方式生成报告、合同或营销材料时，处理形状是常见需求。阅读完本指南后，您将拥有一个可运行的 C# 控制台应用程序，它会生成一个包含矩形、椭圆以及包含这两个形状的组的 `.docx` 文件。

唯一的前置条件是最近的 .NET SDK（6.0 或更高）以及一份已授权的 Aspose.Words for .NET。无需额外工具。

## 前提条件

- .NET 6.0 SDK 或更高版本  
- Aspose.Words for .NET（NuGet 包 `Aspose.Words`）  
- 对 C# 语法的基本了解  

您可以使用以下命令安装该包：

```bash
dotnet add package Aspose.Words
```

## 第一步：使用 Aspose.Words 创建矩形形状

第一步是创建一个 `Shape` 对象，类型为 `Rectangle`。该对象代表文档中将显示的可视矩形。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**为什么重要：** `ShapeType.Rectangle` 告诉 Aspose.Words 渲染几何矩形。设置 `Width` 和 `Height` 定义了其尺寸（单位为点，1 point = 1/72 英寸）。添加填充和描边颜色使形状可见，无需额外样式。

## 第二步：向文档中添加多个形状

在矩形之后，您可以创建任意数量的其他形状。本例中我们添加一个椭圆，以演示 **add multiple shapes** 的工作方式。

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**为什么重要：** 每次调用 `new Shape` 都会创建一个独立的绘图对象。顺序插入它们即可构建一个形状集合，后续可以对这些形状进行分组或单独定位。

## 第三步：将形状添加到组

对形状进行分组可以简化布局管理，因为组表现为单一节点。本步骤展示如何使用 `GroupShape` **add shapes to group**。

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**为什么重要：** `GroupShape` 类似于容器。当您移动、旋转或调整组的大小时，所有子形状会自动跟随。边界框（200 × 200 points）定义了子形状的坐标空间。

## 第四步：将组形状插入文档

现在组已包含矩形和椭圆，您需要在所需位置 **insert group shape**。构建器已经放置了空组，但如果需要，也可以将其插入到其他位置。

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**为什么重要：** 调整 `Left` 和 `Top` 可以在页面内移动整个组。保存文档会将形状层次写入 `.docx` 文件，可在 Microsoft Word、LibreOffice 或任何兼容的查看器中打开。

## 完整可运行示例

下面是整合所有步骤的完整程序。将代码复制到新建的控制台项目中并运行，即可生成 `GroupShapeExample.docx`。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**预期输出：**  
打开 `GroupShapeExample.docx` 后会看到一个包含淡蓝色矩形和淡珊瑚色椭圆的单一组，两者都位于 200 × 200 points 的容器内。该组在 Word 中可以作为一个对象被选中，说明 **add shapes to group** 已成功。

## 常见变体和边缘情况

| 情形 | 推荐调整 |
|-----------|------------------------|
| 不同的形状类型（例如 `ShapeType.Line`） | 使用所需的 `ShapeType` 创建形状，并相应设置其几何属性。 |
| 需要旋转形状 | 在将形状加入组之前使用 `shape.Rotation = 45;`（单位为度）。 |
| 大型文档包含大量组 | 重用同一个 `DocumentBuilder` 实例；避免为每个组创建新 builder，以降低内存开销。 |
| 保存为 PDF 而非 DOCX | 在插入组后调用 `doc.Save("output.pdf", SaveFormat.Pdf);`。 |

**小技巧：** 当需要精确定位时，务必为组设置明确的 `Left` 和 `Top` 值。如果省略，它会继承 builder 当前的光标位置，可能导致布局意外。

## 结论

现在您已经掌握了如何在 Word 文档中使用 C# **create rectangle shape**、**add multiple shapes**、**add shapes to group**，以及 **insert group shape**。完整示例展示了从文档创建到最终保存的完整工作流。

接下来，您可以进一步了解 **相对于文本定位形状**、**应用文本环绕**以及**将分组形状导出为 PDF**等主题。这些扩展让您能够使用 Aspose.Words 构建复杂的程序化文档布局。

## 接下来该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您在项目中进一步运用这些技巧。每个资源均提供完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并探索替代实现方式。

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}