---
category: general
date: 2026-10-23
description: 学习如何使用 Aspose.Words 在 Word 中插入椭圆以及添加矩形形状。包括将光标移动到形状以及如何创建组合形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: zh
lastmod: 2026-10-23
og_description: 如何在 Word 中使用 Aspose.Words 插入椭圆并添加矩形形状。请按照逐步指南将光标移动到形状并创建组合形状。
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: 如何在 Word 组合形状中插入椭圆和矩形形状
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 Aspose.Words 在组形状中插入椭圆和矩形形状
url: /zh/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中向组形状内部插入椭圆和矩形形状

如果您需要了解如何以编程方式在 Word 文档中 **插入椭圆**，本指南展示了完整的过程。您还将看到 **如何添加矩形** 形状，学习 **将光标移动到形状**，并发现 **如何创建组形状** 来容纳多个绘图对象。

Word 自动化通常需要对绘图对象进行精确定位。通过本教程的学习，您可以生成一个包含分组矩形和椭圆的 `.docx` 文件，准备进行进一步的样式设置或导出。除 Aspose.Words for .NET 库和 .NET 开发环境外，无需其他外部工具。

## 前提条件

在开始之前，请确保您拥有：

* 已安装 .NET 6.0 或更高版本。
* 已在项目中添加 Aspose.Words for .NET（NuGet 包 `Aspose.Words`）。
* 具备 C# 语法和 Visual Studio（或任意 IDE）的基本知识。

这些要求确保代码能够在无需额外配置的情况下编译。

## 如何在 Word 中创建组形状

组形状充当容器，使您能够将多个形状作为单个单元进行移动、旋转或格式化。以下代码创建了一个特定尺寸（300 × 200 点）的组，并为后续的绘图操作准备文档。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*此步骤的重要性*：组形状定义了局部坐标系。将光标移动到组后添加的所有形状都相对于组的原点定位，使布局计算变得直观。

## 如何在 Word 中添加矩形形状

现在组已存在，您可以在其中 **插入矩形形状**。矩形将作为背景或其他内容的可视占位符。

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*解释*：`MoveTo(group)` 告诉构建器当前的插入点是组形状。如果不移动光标，`InsertShape` 将把矩形添加到文档主体而不是组中。

## 如何插入椭圆

在矩形就位后，您现在可以演示 **如何插入椭圆**。椭圆将居中于同一组内，若需要可与矩形重叠。

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*为何必须移动光标*：每次调用 `InsertShape` 都会遵循当前光标位置。重新调用 `MoveTo(group)` 可确保椭圆也是组的子对象，保持预期的层次结构。

## 在插入其他对象前将光标移动到形状

如果以后需要添加更多形状，请在每次插入前始终 **将光标移动到形状**。此模式可避免意外放置在组外。

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*提示*：重复使用 `MoveTo(group)` 开销低且提升代码可读性。由于插入上下文明确，也使后续维护更简便。

## 保存文档

最后，将文档持久化到磁盘。示例将文件保存为您指定文件夹中的 `GroupShape.docx`。

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

当您在 Microsoft Word 中打开保存的文件时，会看到一个包含矩形和椭圆的单一组，两者均已正确定位。

### 预期输出

* 一个名为 `GroupShape.docx` 的 `.docx` 文件。
* 文档内部包含一个尺寸为 300 × 200 点的分组绘图对象。
* 在组内：
  * 一个位于组原点的矩形（100 × 50 点）。
  * 一个与矩形重叠的椭圆（80 × 80 点）。
  * 任何在移动光标后添加的其他形状。

## 常见变体和边缘情况

| 情况 | 推荐做法 |
|-----------|----------------------|
| **不同的单位尺寸** | Aspose.Words 使用点（1 pt = 1/72 in）。在调用 `InsertShape` 之前，将厘米或英寸转换为点。 |
| **在组内旋转形状** | 插入形状后，获取其 `ShapeBase` 对象并设置 `ShapeBase.RotationAngle`。 |
| **在形状内添加文本** | 使用 `ShapeBase.AppendChild(new Paragraph(document))`，然后添加带有所需文本的 `Run`。 |
| **保存为 PDF 而非 DOCX** | 调用 `document.Save("GroupShape.pdf", SaveFormat.Pdf);` —— 组层次结构在 PDF 输出中得以保留。 |

## 专业技巧

* **复用同一个 `DocumentBuilder` 实例** —— 可减少内存开销并保持文档状态一致。
* **验证形状尺寸** —— 极大的宽度或高度可能在旧版 Word 中导致渲染问题。
* **先分组后样式** —— 在所有子对象添加完毕后再对组应用填充颜色或线条样式，可确保外观统一。

## 结论

您现在已经了解了使用 Aspose.Words 在 Word 文档的分组容器中 **插入椭圆** 和 **添加矩形** 形状的方法。通过在每次插入前始终 **将光标移动到形状**，您可以保持层次结构清晰，避免意外放置。完整示例能够编译、运行，并生成一个可进一步自定义或导出的分组形状。

准备好进一步探索了吗？尝试将此技术与 **如何创建组形状** 结合，以绘制复杂图表，或与 **在 Word 中插入矩形形状** 结合使用文本框，生成丰富的报告。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [如何使用 Aspose.Words 在 Word 中创建矩形形状和组形状](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [如何创建空白 Word 文档并在 C# 中添加隐藏的椭圆形状](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [如何在 C# 中创建组形状 docx 并添加交互式控件](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}