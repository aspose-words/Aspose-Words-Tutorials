---
category: general
date: 2026-11-18
description: 学习如何使用 C# 在 Word 文档中创建矩形形状。本指南还涵盖设置形状大小、设置形状位置以及在 Word 中对形状进行分组。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: zh
lastmod: 2026-11-18
og_description: 使用 C# 在 Word 文件中创建矩形形状，并学习设置形状尺寸、设置形状位置以及在 Word 中对形状进行分组。
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: 使用 C# 在 Word 中创建矩形形状并对形状进行分组
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 C# 在 Word 中创建矩形形状并对形状进行分组
url: /zh/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 在 Word 中创建矩形形状并对形状进行分组

如果您需要在 Word 文档中 **创建矩形形状**，本教程提供了一个完整、可直接运行的解决方案。您将看到如何设置形状大小、设置形状位置，以及在 Word 中对形状进行分组，使其表现为单个对象。

在程序化生成报告、发票或图表时，处理形状是常见需求。阅读完本指南后，您将能够生成一个包含矩形、椭圆和分组容器的 `.docx` 文件——全部使用 Aspose.Words for .NET 创建。

## 前提条件

- .NET 6.0 SDK 或更高版本（代码同样适用于 .NET Framework 4.7+）
- Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）
- 代码编辑器或 IDE（Visual Studio、VS Code、Rider 等）

无需其他库。

## 在 Word 中创建矩形形状并对形状进行分组

核心步骤如下：

1. **创建一个空白文档** 并创建 `DocumentBuilder`。
2. **插入一个 `GroupShape`**，用于容纳各个形状。
3. **创建矩形形状**，设置其尺寸，并将其添加到组中。
4. **创建椭圆形状**，设置其大小和位置，并将其添加到组中。
5. **保存** 文档。

下面将逐步解释每个步骤，完整的源代码紧随说明之后。

### 步骤 1：初始化文档和构建器

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 表示整个 Word 文件，而 `DocumentBuilder` 提供了一个流式 API 用于插入内容。在添加任何形状之前，必须先初始化它们。

### 步骤 2：插入分组形状

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

`GroupShape` 像容器一样工作；所有子形状一起移动。这是在需要整体变换（例如移动、旋转或删除）时 **在 Word 中对形状进行分组** 的推荐方式。

### 步骤 3：创建矩形并设置其大小

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

这里我们通过赋值 `Width` 和 `Height` 来 **创建矩形形状** 并 **设置形状大小**。在 Aspose.Words 中，尺寸以点为单位（1 pt ≈ 1/72 in）。显式设置尺寸可确保矩形准确呈现。

### 步骤 4：创建椭圆，设置尺寸并定位

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

对椭圆的 **设置形状尺寸** 中，宽度和高度相同，形成完美的圆形。`Left` 属性展示了 **设置形状位置**：椭圆相对于组的原点向右偏移 120 pt，因而不会与矩形重叠。

### 步骤 5：保存文档

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

保存操作会将 Word 文件写入磁盘。您可以在 Microsoft Word 中打开 `GroupShape.docx`，以验证矩形和椭圆已正确分组并定位。

## 设置形状尺寸和大小 – 深入了解

- **点与英寸**：72 pt = 1 in。如果您更喜欢使用英寸，可乘以 72（例如 `2.5 * 72` 表示 2.5 in）。
- **自动缩放**：如果省略 `Width` 或 `Height`，形状将使用默认尺寸。显式 **设置形状大小** 可避免布局意外。
- **宽高比**：对于 `Ellipse` 等形状，保持 `Width` 与 `Height` 相等可保持圆形外观。

## 在 Word 中定位形状

`Left` 和 `Top` 属性控制形状在其容器（组或页面）内的偏移。正值使形状向右/向下移动，负值使其向左/向上移动。进行分组时，位置相对于组的原点，这简化了布局计算。

## 使用 Aspose.Words 在 Word 中对形状进行分组

当您希望多个形状作为单一单元时，分组是必不可少的。`GroupShape` 对象：

- 支持 `AppendChild` 来添加任意 `Shape`（矩形、椭圆、图像等）。
- 允许您通过一次调用移动、旋转或删除整个组。
- 保持子形状相对于组的位置，使复杂图表更易管理。

**专业提示：** 添加完所有子形状后，您可以调整组的 `Width`、`Height`、`Left` 和 `Top`，一次性重新定位整个集合。

## 完整可运行示例

下面是完整的程序示例，您可以复制、粘贴并运行。它包含所有 `using` 指令、`Main` 方法以及解释每行代码的注释。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**预期输出：** 运行程序后，`GroupShape.docx` 会出现在执行文件夹中。用 Word 打开后，可看到左侧有一个矩形（100 pt × 50 pt），右侧有一个椭圆（80 pt × 80 pt），两者均位于同一个分组对象内。

![Word document with grouped rectangle and ellipse](grouped_shapes.png){: .center alt="使用 C# 创建的包含分组矩形和椭圆形状的 Word 文档截图" }

*上图展示了最终效果；矩形和椭圆可作为一个组进行选择。*

## 常见问题与边缘情况

| 问题 | 答案 |
|----------|--------|
| **我可以添加超过两个形状吗？** | 可以。对每个额外的形状调用 `group.AppendChild(yourShape)`。 |
| **如果需要旋转组怎么办？** | 在添加完所有子形状后，使用 `group.RotationAngle = 45;`（度）进行旋转。 |
| **如何更改组的背景颜色？** | 设置 `group.FillColor = System.Drawing.Color.LightGray;`。 |
| **这能用于 .doc 文件吗？** | Aspose.Words 支持 `.doc` 和 `.docx`。相同代码可工作，只需在 `Save` 中更改文件扩展名。 |
| **对大量形状进行分组会有内存影响吗？** | 分组本身只会产生极小的开销。主要关注点是形状的总数量；在大型文档中请保持合理的数量。 |

## 结论

在本教程中，您学习了如何使用 C# 在 Word 文件中 **创建矩形形状**，以及如何 **设置形状大小**、**设置形状尺寸**、**设置形状位置**，最终使用 Aspose.Words **在 Word 中对形状进行分组**。完整示例展示了一种简洁、易于维护的方法，您可以将其扩展到更复杂的图表、图形或自定义图形。

接下来，您可以探索：

- 在形状内部添加文本 (`Shape.TextPath.Text = "Hello"` )。
- 向 `GroupShape` 插入图像。
- 使用 `doc.Save("output.pdf")` 将分组形状导出为 PDF。

欢迎尝试不同的尺寸、位置和其他形状类型，以满足项目需求。祝编码愉快！

## 接下来您可以学习什么？

以下教程涵盖与本指南紧密相关的主题，基于所示技术进行扩展。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方式。

- [使用 Aspose.Words 在 Word 中创建矩形形状并对形状进行分组](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [使用 Aspose.Words for .NET 在 Word 文档中创建分组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 C# 在 Word 中创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}