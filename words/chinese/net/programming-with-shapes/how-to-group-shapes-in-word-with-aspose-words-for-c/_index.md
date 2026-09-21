---
category: general
date: 2026-09-21
description: 学习如何使用 Aspose.Words for C# 在 Word 中对形状进行分组。本分步指南涵盖了创建、定位和保存分组形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: zh
lastmod: 2026-09-21
og_description: 使用 Aspose.Words for C# 在 Word 中对形状进行分组。遵循本简明教程，程序化地创建、定位并保存分组形状。
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: 使用 Aspose.Words 在 Word 中对形状进行分组 – 完整 C# 指南
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 Aspose.Words for C# 在 Word 中对形状进行分组
url: /zh/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 Aspose.Words for C# 对形状进行分组

如果您需要以编程方式**在 Word 中对形状进行分组**，Aspose.Words 使其变得简单。本教程展示了如何创建两个矩形形状，将它们并排放置，合并为一个 `GroupShape`，并将结果保存为 DOCX 文件。

您将看到完整的可运行示例、每一步为何重要的解释，以及处理常见边缘情况（如形状重叠或动态尺寸）的技巧。阅读完本指南后，您即可在任何 Word 自动化项目中集成形状分组功能。

## 前提条件

在开始之前，请确保您具备以下条件：

* 已安装 .NET 6.0（或更高版本）– Aspose.Words 支持 .NET Standard 2.0+、.NET Core 和 .NET Framework。
* 有效的 Aspose.Words for .NET 许可证（或临时评估密钥）– 库在没有许可证的情况下仍可工作，但会添加水印。
* Visual Studio 2022（或任何 C# IDE）用于编译和运行示例。

除 `Aspose.Words` 外，无需其他 NuGet 包。

## 使用 Aspose.Words 在 Word 中对形状进行分组

解决方案的核心是一个 **`GroupShape`** 对象，它充当各个形状的容器。下面我们将过程拆分为清晰的步骤。

### 步骤 1：创建空白文档和 `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*为什么这一步？*  
`Document` 表示整个 DOCX 文件，而 `DocumentBuilder` 提供流式方法（例如 `InsertShape`），这些方法会自动将新元素放置在当前光标位置。

### 步骤 2：插入第一个矩形形状

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

`InsertShape` 调用会将形状添加到文档并返回一个 `Shape` 对象，您可以进一步配置（颜色、边框等）。尺寸以点为单位（1 pt ≈ 1/72 英寸）。

### 步骤 3：插入第二个矩形并进行偏移

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

设置 `Left` 可以相对于页面边距定位形状。偏移量必须大于第一个形状的宽度（100 pt），以避免重叠；这里使用 120 pt 留出一点间隙。

### 步骤 4：创建足够容纳两个矩形的 `GroupShape`

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` 需要所属的 `Document` 和容器尺寸。容器宽度应超过最右侧形状的右边缘，否则第二个形状会被裁剪。

### 步骤 5：将各个形状追加到组中

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

追加操作会将形状移动到组的内部集合中。调用此方法后，这些形状不再是文档树中的独立对象——它们属于该组。

### 步骤 6：将分组后的形状插回文档

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` 会将整个 `GroupShape` 放置在光标当前所在的位置。如果需要将组放入特定段落，请先将 builder 移动到该段落。

### 步骤 7：保存文档

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

生成的文件包含两个矩形，表现为单个对象——在 Microsoft Word 中您可以一起移动、调整大小或删除它们。

## 完整源代码

将所有步骤组合在一起即可得到一个自包含的程序：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**预期输出：** 在 Microsoft Word 中打开 *GroupedShapes.docx*，会看到两个并排的矩形，被视为单个可选对象。拖动该组会同时移动两个矩形。

## 常见变体和边缘情况

| 情况 | 推荐的调整 |
|-----------|------------------------|
| **多于两个形状** | 创建额外的 `Shape` 对象，按需定位，并将每个对象追加到同一个 `GroupShape` 中。 |
| **动态尺寸** | 根据子形状的最大 `Right` 和 `Bottom` 值计算组的宽度/高度。 |
| **不同形状类型** | `ShapeType.Ellipse`、`ShapeType.Triangle` 等可以以相同方式插入；组容器不关心具体类型。 |
| **旋转形状** | 在追加之前设置 `shape.Rotation = 45;`；旋转会在组内保留。 |
| **保存为 PDF** | 调用 `doc.Save("GroupedShapes.pdf");` —— 组在 PDF 渲染中仍然保留。 |

**技巧：** 分组后，仍可通过 `group.GetChildNodes(NodeType.Shape, true)` 访问并修改单个形状。这在需要更改某个矩形的填充颜色而不破坏整体组时非常有用。

## 如何以编程方式验证分组

如果需要确认形状已正确分组（例如在单元测试中），可以检查文档节点层次结构：

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

输出应为：

```
Number of groups: 1
Children in first group: 2
```

这表明 **在 Word 中的形状分组** 已按预期创建。

## 结论

现在您已经掌握了使用 Aspose.Words for C# **在 Word 中对形状进行分组** 的方法。该过程包括创建单个形状、定位它们、将它们包装进 `GroupShape`，然后将组插回文档。借助上面的完整示例，您可以将此技术扩展到任意数量的形状、不同类型，甚至与文本框和图像组合使用。

接下来，您可以进一步探索 **Aspose.Words 形状分组**、**C# Word 形状操作** 和 **DocumentBuilder 插入形状** 等相关主题，以实现更高级的文档自动化场景。尝试动态尺寸、条件分组以及导出为 PDF，充分发挥 Aspose.Words 的强大功能。

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题，每个资源都提供完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [使用 Aspose.Words for .NET 在 Word 文档中插入形状](/words/english/net/working-with-shapes/insert-shape/)
- [使用 Aspose.Words 创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words 形状阴影教程 – 在 C# 中为 Word 形状添加阴影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}