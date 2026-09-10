---
category: general
date: 2025-12-29
description: 使用 Aspose.Words C# 在 Word 文档中创建矩形形状。学习设置形状透明度、设置阴影颜色，并轻松保存 Word 文档。
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: zh
og_description: 使用 Aspose.Words C# 在 Word 文档中创建矩形形状。本指南展示如何设置形状透明度、设置阴影颜色以及保存 Word
  文档。
og_title: 在 Word 中创建矩形形状 – 完整的 Aspose.Words 教程
tags:
- Aspose.Words
- C#
- Word Automation
title: 使用 Aspose.Words 在 Word 中创建矩形形状 – 步骤指南
url: /zh/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中创建矩形形状 – 完整 Aspose.Words 教程

是否曾经需要在 Word 文档中**创建矩形形状**但不知从何入手？你并不孤单；许多开发者在自动化报告或发票时都会遇到这个难题。在本指南中，我们将逐步演示如何使用 Aspose.Words for .NET **创建矩形形状**、设置形状透明度、设置阴影颜色，最后**保存 Word 文档**。

我们将从最初的 Document 对象一直讲到磁盘上的最终 `.docx` 文件，帮助你在结束时能够以编程方式**创建 Word 文档**而无需猜测。无需外部引用，只需一个可直接复制粘贴到项目中的完整解决方案。

## 前置条件

- .NET 6.0 或更高（代码同样适用于 .NET Framework 4.7+）
- Aspose.Words for .NET NuGet 包 (`Install-Package Aspose.Words`)
- C# 语法的基本了解
- 你选择的 IDE（Visual Studio、Rider、VS Code 等）

> **技巧提示：** 如果你使用的是 Aspose.Words 的免费试用版，库会在输出文件上添加水印。正式环境下需要有效的许可证。

## 步骤 1：初始化 Document 和 Builder

我们首先创建一个全新的空白 Word 文档以及一个 `DocumentBuilder`，它允许我们插入内容。可以把 Builder 看作在页面上绘图的虚拟笔。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **重要性说明：** 如果没有 `DocumentBuilder`，你必须直接操作底层节点树，这既容易出错，又难以阅读。

## 步骤 2：创建矩形形状

现在我们实际**创建矩形形状**。`InsertShape` 方法接受一个 `ShapeType` 枚举、宽度和高度（单位为点）。返回的 `Shape` 对象随后可以用于微调视觉属性。

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

此时矩形是一个锚定在当前段落的实心黑色框。你可以移动、调整大小，甚至在需要时旋转它。

![带阴影的矩形形状](/images/rectangle-shadow.png "Word 文档显示带灰色阴影的矩形形状")

*图片替代文字：在 Word 文档中带阴的矩形形状*

## 步骤 3：设置形状透明度

透明度指的是形状填充的“透视”程度。Aspose.Words 使用 `Transparency` 属性，取值范围为 `0.0`（不透明）到 `1.0`（完全透明）。这里我们将**形状透明度**设置为 40 %，以保证底层文字仍然可读。

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **特殊情况：** 如果需要完全不可见的形状但仍希望显示阴影，可将 `Transparency` 设置为 `1.0` 并为形状指定非零的轮廓宽度。

## 步骤 4：配置阴影

细腻的投影可以增加层次感。我们将**设置阴影颜色**为中等灰色，调整其模糊半径，并在水平和垂直方向上各偏移若干点。

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **重要性说明：** 阴影如果过于锐利或过暗会看起来像打印痕迹。请调节 `Blur` 和 `Transparency` 直至呈现自然效果。

## 步骤 5：保存 Word 文档

最后我们将**保存 Word 文档**到磁盘。`Save` 方法会根据文件扩展名自动确定文件格式；`.docx` 是现代的 OpenXML 格式。

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

如果文件夹不存在，Aspose.Words 会抛出 `ArgumentException`。请确保路径有效或提前创建目录。

## 完整工作示例

下面是完整的、可直接运行的程序示例，整合了所有步骤。将其复制到新的控制台项目中并按 **F5** 运行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 预期结果

在 Microsoft Word 中打开 `ShadowRectangle.docx`。你应该会看到一个浅灰色矩形，带有柔和、略微偏移的阴影，透明度为 40 %。该形状位于空白页上，准备添加其他内容。

## 常见问题与变体

**如果需要不同的形状怎么办？**  
将 `ShapeType.Rectangle` 替换为任意其他枚举值（如 `Ellipse`、`Triangle`、`Star` 等）。其余代码保持不变。

**可以更改轮廓颜色吗？**  
可以——使用 `rectangleShape.StrokeColor = System.Drawing.Color.Blue;`，并可选地设置 `rectangleShape.StrokeWeight = 1.5;`。

**如何将形状放置在页面的特定位置？**  
设置 `rectangleShape.WrapType = WrapType.None;`，然后调整 `rectangleShape.Left` 和 `rectangleShape.Top` 属性（单位为点）。

**是否可以在矩形内部添加文字？**  
完全可以。创建形状后，你可以调用 `rectangleShape.AppendChild(new Paragraph(document))`，随后添加包含文本的 `Run`。如果需要更丰富的格式，请记得设置 `rectangleShape.TextBox` 属性。

## 专业技巧与常见陷阱

- **尽早授权：** 如果忘记应用许可证，Aspose.Words 会在首页插入水印，测试时可能导致困惑。
- **性能提示：** 在循环中生成大量文档时，复用同一个 `Document` 实例，并在每次保存后调用 `document.RemoveAllChildren();`，以避免过度的 GC 压力。
- **阴影可见性：** 在低分辨率屏幕上，细微的阴影可能看不见。调大 `Blur` 或 `OffsetX/Y` 进行调试，然后在生产环境中适当降低。

## 后续步骤

既然你已经掌握了**创建矩形形状**、**设置形状透明度**、**设置阴影颜色**以及**保存 Word 文档**，可以考虑扩展本教程：

- 添加多个形状并对其进行分组。
- 将矩形插入表格单元格以实现报表布局。
- 将形状与 `DocumentBuilder.InsertHtml` 结合，以覆盖 HTML 样式的内容。
- 探索其他视觉效果，如 `Glow` 或 `Reflection`，以实现更丰富的 UI 式文档。

大胆实验、敢于出错，然后不断改进——程序化文档生成是视觉设计与代码相结合的实验场。

---

*祝编码愉快！如果遇到任何问题，欢迎在下方留言，我们一起排查。*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}