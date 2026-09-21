---
category: general
date: 2026-09-21
description: 使用 Aspose.Words 创建一个空白 Word 文档，设置形状大小、位置和颜色，并在一次操作中保存为 docx 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: zh
lastmod: 2026-09-21
og_description: 使用 Aspose.Words 在几分钟内创建空白 Word 文档，设置形状大小、位置和颜色，并保存为 docx 文件。
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: 创建空白 Word 文档并添加彩色形状 – Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: 使用 Aspose.Words 创建空白 Word 文档并添加彩色形状
url: /zh/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words 创建空白 Word 文档并添加彩色形状

如果您需要以编程方式**创建一个空白的 Word 文档**，本指南将向您展示如何使用 Aspose.Words。您将学习如何**设置形状大小**、**设置形状位置**、**设置形状颜色**，以及最终**保存 docx 文件**，全部在 IDE 中完成。

在 C# 中处理 Word 文件通常需要应付低层的 OpenXML 调用，但 Aspose.Words 抽象了这些复杂性。完成本教程后，您将拥有一个完整的 `.docx`，其中包含由两个彩色矩形组成的组合形状——非常适合用于报告、证书或自定义模板。

## 前提条件

- .NET 6.0 或更高（代码同样适用于 .NET Framework 4.7+）
- Aspose.Words for .NET 23.9 或更高（通过 NuGet 安装：`Install-Package Aspose.Words`）
- 对 C# 和 Visual Studio（或任何 C# 编辑器）有基本了解

不需要已有的 Word 文件；本教程从**创建空白 Word 文档**开始。

## 使用 Aspose.Words 创建空白 Word 文档

第一步是实例化一个 `Document` 对象。该对象在内存中表示一个空的 Word 文件。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` 初始为空，这正是您在**创建空白 Word 文档**时所需要的。随后 `builder` 将用于在当前光标位置插入形状组。

## 设置形状大小并创建 GroupShape

`GroupShape` 类似于一个容器，可以容纳多个单独的形状。首先，定义容器的整体尺寸。

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

这里我们为组本身**设置形状大小**（300 × 200）。相同的属性名（`Width`、`Height`）也用于每个子形状，使您能够对每个元素进行细粒度控制。

## 添加第一个矩形并设置形状颜色

现在向组中添加一个矩形并为其设置背景颜色。

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

`FillColor` 属性**设置形状颜色**。使用 `System.Drawing.Color` 可以选择任何预定义或自定义的 ARGB 值。

## 添加第二个矩形，设置其大小、位置和颜色

第二个矩形演示了如何相对于组**设置形状位置**以及如何更改其颜色。

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

由于组的宽度为 300 点，两个 120 点的矩形可以舒适地留出 30 点的间隙。如果需要不同的布局，可调整 `Left` 和 `Top`。

## 将 GroupShape 插入文档

组配置完成后，将其放置在当前光标位置。

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` 将形状直接写入文档主体，保留您之前定义的精确**设置形状位置**。

## 保存 docx 文件

最后一步是将文档持久化到磁盘。这演示了**保存 docx 文件**的操作。

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

运行程序后，在 Microsoft Word 中打开 `GroupShape.docx`。您应该会看到一个空白页，页面上有一个包含两个并排彩色矩形的组合形状。

### 预期输出

- 一个单页的 `.docx` 文件。
- 页面包含一个距离左、上边距各 100 pt 的组形状。
- 在组内部，左侧是一个浅蓝色矩形，右侧是一个浅珊瑚色矩形，尺寸均为 120 × 80 pt。

## 完整、可运行的示例

下面是完整的程序代码，您可以复制粘贴到控制台应用程序中。无需额外的文件。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

运行此程序会创建前文描述的完整文档，满足四个目标：**创建空白 Word 文档**、**设置形状大小**、**设置形状位置**、**设置形状颜色**，以及**保存 docx 文件**。

## 常见变体和边缘情况

| 场景 | 需要更改的内容 | 为什么重要 |
|----------|----------------|----------------|
| **不同的形状类型** | 将 `ShapeType.Rectangle` 替换为 `ShapeType.Ellipse`、`ShapeType.Triangle` 等。 | 允许您在无需外部图像的情况下构建更复杂的图形。 |
| **动态尺寸** | 根据用户输入或配置文件计算 `Width` 和 `Height`。 | 使该方案可在多个文档模板之间复用。 |
| **保存为 PDF** | 调用 `document.Save("output.pdf", SaveFormat.Pdf);` | 如果接收者需要不可编辑的格式，PDF 是安全的选择。 |
| **在形状内添加文本** | 创建 `TextBox` 形状并设置 `TextBox.Text`。 | 用于创建带标签的徽章或标注。 |
| **在同一页上放置多个组** | 使用不同的 `Left`/`Top` 值重复步骤 2‑5。 | 使您能够构建仪表板或多区段布局。 |

### 专业提示

当需要精确对齐形状时，在插入组之前使用 `ShapeBase.WrapType = WrapType.Inline` 属性。这会强制组表现得像段落，从而防止文本意外环绕。

## 结论

现在您已经了解如何使用 Aspose.Words **创建空白 Word 文档**、**设置形状大小**、**设置形状位置**、**设置形状颜色**，以及 **保存 docx 文件**。完整示例展示了一种简洁、可复用的模式，可将组合图形添加到任何 Word 自动化项目中。

从这里您可以进一步探索：

- 向同一 `GroupShape` 添加更多形状或图像（**设置形状大小**、**设置形状颜色** 的变体）。
- 使用 `ShapeBase.Rotation` 旋转矩形以实现装饰效果。
- 将同一文档导出为 PDF 或 HTML，以扩大分发范围（**保存 docx 文件** 的替代方案）。

欢迎尝试不同的颜色、尺寸和布局逻辑，以满足您特定的报表或模板需求。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题，帮助您在此基础上进一步学习。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方式。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}