---
category: general
date: 2026-08-04
description: 使用 C# 在 Word 文档中插入矩形形状。学习如何在 Word 中对形状进行分组，将文档保存为 docx，并使用 DocumentBuilder
  实现高级布局。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: zh
lastmod: 2026-08-04
og_description: 使用 C# 在 Word 文件中插入矩形形状，然后对形状进行分组以实现高级布局。本教程还涵盖将文档保存为 docx 并高效使用 DocumentBuilder。
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: 在 Word 中插入矩形形状 – C# 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 C# 在 Word 中插入矩形形状 – 完整指南
url: /zh/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 C# 插入矩形形状 – 完整指南

如果您需要在 Word 文档中使用 C# **插入矩形形状**，本教程将精确演示操作步骤。您还将学习 **如何在 Word 中对形状进行分组**、**将文档保存为 docx**，以及 **如何使用 Builder** 编写简洁、易维护的代码。

在以编程方式生成报告、证书或自定义布局时，处理形状是常见需求。阅读完本指南后，您将拥有一个完整可运行的示例，能够创建矩形、添加椭圆、将它们分组，并将结果保存为 DOCX 文件。

## 前置条件

在开始之前，请确保您已具备：

* .NET 6.0 或更高版本已安装  
* Visual Studio 2022（或任何支持 C# 的 IDE）  
* **Aspose.Words for .NET** 库（可通过 NuGet 获取）  

您可以使用以下命令添加该库：

```bash
dotnet add package Aspose.Words
```

## 使用 DocumentBuilder 插入矩形形状

第一步是创建一个新的 `Document` 和一个 `DocumentBuilder`。Builder 为您提供了一个流式 API，用于插入内容，包括形状。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` 实例是您用来 **插入矩形形状** 以及其他元素的核心对象。它会跟踪文档内部的当前光标位置，因此任何插入都会恰好发生在您需要的位置。

## 如何插入矩形形状

准备好 Builder 后，调用 `InsertShape`。您需要指定 `ShapeType`、宽度和高度（单位为点，1 pt ≈ 1/72 in）。

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*为什么这很重要*：设置 `FillColor` 和 `StrokeColor` 可以让矩形在视觉上更为突出，这有助于后续将其与其他形状分组。

## 如何在 Word 中对形状进行分组

对形状进行分组可以让您一次性移动、旋转或格式化多个对象。插入矩形后，添加另一个形状（本例中的椭圆），然后创建一个 `GroupShape`。

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

`InsertGroupShape` 调用会创建一个占位符，可容纳任意数量的子形状。通过将矩形和椭圆追加进去，您实际上 **在 Word 中对形状进行分组**。该组表现得像单个形状——您可以重新定位它、应用边框或调整大小，而不会影响每个子形状的内部布局。

### 小技巧

分组后，您可以相对于页面更改组的位置：

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## 将文档保存为 docx

形状排列好后，需要将文件持久化。`Document.Save` 方法会根据文件扩展名自动确定格式。要 **将文档保存为 docx**，只需传入以 `.docx` 结尾的路径。

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

运行程序后会生成 `output.docx`。在 Microsoft Word 中打开该文件，您会看到一个淡蓝色的矩形和一个淡珊瑚色的椭圆已被分组在一起。您可以点击该组并将其作为单个对象移动。

## 如何高效使用 DocumentBuilder

`DocumentBuilder` 不仅仅是形状插入器；它还处理文本、表格、页眉和页脚。当您将形状创建与文本结合时，若需要在其他位置插入内容，请记得重置光标：

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

显式维护 Builder 的状态可避免意外覆盖，并使代码更易于维护。

## 边缘情况和变体

| 情况 | 推荐做法 |
|-----------|----------------------|
| **More than two shapes** | Insert each shape, then call `AppendChild` for every shape before saving. |
| **Nested groups** | Create a group, add shapes, then insert that group into another `GroupShape`. |
| **Different measurement units** | Use `builder.ConvertPixelsToPoints` if you have dimensions in pixels. |
| **Compatibility with older Word versions** | Save as `.doc` by changing the extension; most shape features still work. |

## 完整可运行示例

下面是完整程序，您可以直接复制粘贴到新的控制台项目中。无需额外代码片段。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**预期结果**：打开 `output.docx` 后会看到一个淡蓝色的矩形和一个淡珊瑚色的椭圆已被分组在一起，左边距 150 pt、顶部 100 pt 处。标题出现在组的下方。

## 结论

您现在已经掌握了如何使用 C# **插入矩形形状** 到 Word 文件、**在 Word 中对形状进行分组**，以及使用 Aspose.Words `DocumentBuilder` **将文档保存为 docx**。通过熟练这些步骤，您可以完全通过代码构建复杂布局——证书、报告或自定义表单。

接下来，您可以探索诸如 **添加文本框**、**使用表格** 或 **导出为 PDF** 等相关主题。所有这些都基于您刚刚实践的 `DocumentBuilder` 基础。

准备好自动化您的 Word 文档了吗？尝试在示例中加入更多形状、应用渐变，或循环数据一次性生成完整报告。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，每个资源都提供完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words for .NET 在 Word 文档中插入形状](/words/english/net/working-with-shapes/insert-shape/)
- [使用 Aspose.Words 在 Word 中创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}