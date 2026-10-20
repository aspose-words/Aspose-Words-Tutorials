---
category: general
date: 2026-08-14
description: 如何使用 C# 在 Word 文档中对形状进行分组。学习创建 Word 文档、插入矩形形状、在 Word 中对形状进行分组，并将文档保存为
  docx。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: zh
lastmod: 2026-08-14
og_description: 如何使用 C# 在 Word 文档中对形状进行分组。请按照本完整教程创建 Word 文件、插入矩形形状、在 Word 中对形状进行分组，并将结果保存为
  docx。
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: 如何使用 C# 在 Word 文档中对形状进行分组 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: 如何使用 C# 在 Word 文档中对形状进行分组
url: /zh/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文档中使用 C# 对形状进行分组

如果您需要在 Word 文档中**对形状进行分组**，本指南将展示使用 C# 和 Aspose.Words 库的具体步骤。您将看到如何创建 Word 文档、插入矩形形状、在 Word 中对形状进行分组，最后**将文档保存为 docx**——全部在一个可运行的程序中完成。

创建和操作形状是以编程方式生成报告、合同或营销手册时的常见需求。阅读完本教程后，您将拥有一段可复用的代码片段，能够直接嵌入任何 .NET 项目中。

## 前置条件

在开始之前，请确保您已经：

- 安装 .NET 6.0 或更高版本  
- 安装 Visual Studio 2022（或任何支持 .NET 的 IDE）  
- 拥有 Aspose.Words for .NET 授权（或免费试用版）  
- 对 C# 语法有基本了解  

除 `Aspose.Words` 之外，无需额外的 NuGet 包。

## 如何在 Word 文档中对形状进行分组

解决方案的核心是一个五步流程。每一步都有详细说明，完整源码位于文章末尾。

### 步骤 1：创建一个新的空白文档

当您想要**以编程方式创建 Word 文档**时，首先实例化一个 `Document` 对象。该对象在内存中表示整个 .docx 文件。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**为什么重要：**`DocumentBuilder` 是一个高级助手，能够让您在不手动处理底层节点树的情况下插入文本、表格和形状。

### 步骤 2：插入矩形形状

为了演示**插入矩形形状**，我们使用 `InsertShape` 方法。矩形将作为组的第一个成员。

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**为什么重要：**形状相对于插入点定位。设置填充颜色可以帮助您在打开生成的文档时看到该形状。

### 步骤 3：插入椭圆形状

接下来，我们**插入椭圆形状**（API 中称为 `Ellipse`）。这将成为组的第二个成员。

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**为什么重要：**在矩形之后立即插入椭圆，两个形状会位于同一段落中，这为后续分组简化了操作。

### 步骤 4：将矩形和椭圆分组

现在我们回答核心问题——**如何在 Word 文档中对形状进行分组**。Aspose.Words 提供 `AppendGroupShape` 用于创建组容器，然后在该容器上调用 `Group()`。

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**为什么重要：**一旦分组，对 `groupedShape` 进行的任何变换（移动、缩放、旋转）都会自动作用于矩形和椭圆。这对于保持生成文档的布局一致性至关重要。

### 步骤 5：将文档保存为 DOCX 文件

最后一步是**将文档保存为 docx**。您可以自行选择保存路径，示例中使用占位符 `"YOUR_DIRECTORY"`，请替换为实际文件夹。

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**为什么重要：**以 DOCX 格式保存会保留分组元数据，打开 Microsoft Word 时您会看到矩形和椭圆作为单一对象出现。

## 完整、可运行的示例

下面是结合所有五个步骤的完整程序。将其复制到新的控制台项目中，恢复 Aspose.Words NuGet 包后运行即可。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### 预期输出

在 Microsoft Word 中打开 `groupedShapes.docx`，您会看到一个淡蓝色矩形和一个淡珊瑚色椭圆已锁定在一起。单击任意一个形状都会选中两者，您可以将它们作为单个单元移动或缩放。

## 常见问题与边缘情况

| 问题 | 答案 |
|----------|--------|
| **我可以对超过两个形状进行分组吗？** | 可以。将任意数量的 `Shape` 对象传递给 `AppendGroupShape`。该方法接受数组，您可以动态构建集合。 |
| **如果需要将组锚定到表格单元格怎么办？** | 将形状插入到单元格的段落中，然后在该段落上调用 `AppendGroupShape`。组会继承单元格的锚定方式。 |
| **分组会影响底层 XML 吗？** | Aspose.Words 会写入一个 `<w:grpSp>` 元素，其中包含子形状。Word 会将其识别为组，并保留相对位置。 |
| **我以后如何取消分组？** | 调用 `groupedShape.Ungroup()`；该方法返回各个子形状，您可以单独操作它们。 |
| **对大量形状进行分组会有性能影响吗？** | 分组本身开销不大，但渲染非常大的组（数百个形状）可能会增大文件体积。如有需要，可考虑将图像展平以降低大小。 |

## 专业技巧

- **在分组前设置明确的坐标**（`Left`、`Top`），以实现精确对齐。  
- **使用 `Shape.WrapType = WrapType.Inline`**，当您希望组表现得像段落元素而非浮动对象时。  
- **为组应用线条样式**（`groupedShape.LineFormat`），为整个集合添加边框。  
- **复用组**：调用 `Group()` 后，您可以克隆 `groupedShape` 并将克隆插入文档的其他位置。

## 后续步骤

了解了**如何在 Word 文档中对形状进行分组**后，您可以进一步探索以下相关主题：

- **插入矩形形状**，并在形状内部放置自定义文本或图像。  
- **通过嵌套组**（对组进行分组）创建复杂图表。  
- **导出文档为 PDF**，同时保留形状分组（`doc.Save("output.pdf", SaveFormat.Pdf)`）。  

这些内容都基于本教程中介绍的基础，帮助您进一步扩展 Word 自动化工具箱。

## 结论

本教程演示了使用 C# **在 Word 文档中对形状进行分组**的完整过程。您学习了**创建 Word 文档**、**插入矩形形状**、**在 Word 中对形状进行分组**，以及**将文档保存为 docx**。借助完整的可运行示例和实用技巧，您可以将形状分组功能集成到任何文档生成工作流中。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术密切相关的主题，每篇资源都提供完整的代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方式。

- [在 Word 文档中使用 Aspose.Words for .NET 创建组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words for .NET 在 Word 文档中插入形状](/words/english/net/working-with-shapes/insert-shape/)
- [使用 C# 在 Word 中创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}