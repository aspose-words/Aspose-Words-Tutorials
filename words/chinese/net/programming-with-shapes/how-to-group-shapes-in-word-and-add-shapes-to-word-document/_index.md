---
category: general
date: 2026-08-07
description: 如何使用 Aspose.Words 在 Word 中对形状进行分组，并使用 C# 向 Word 文档添加形状。请遵循本分步指南，以获得简洁、可复用的代码。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: zh
lastmod: 2026-08-07
og_description: 如何使用 Aspose.Words for .NET 在 Word 中对形状进行分组。本教程展示了如何向 Word 文档添加形状、对其进行分组，并使用清晰的
  C# 代码保存文件。
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: 如何在 Word 中对形状进行分组 – 快速 C# 指南
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: 如何在 Word 中对形状进行分组并向 Word 文档添加形状
url: /zh/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中对形状进行分组并向 Word 文档添加形状

如果您需要 **how to group shapes in Word**，本指南将通过 Aspose.Words for .NET 带您完成整个过程。您还将学习如何使用几行 C# 代码 **add shapes to Word document**，以便在任何报表或模板场景中直接使用生成的结果。

本教程涵盖您需要的全部内容：必需的 NuGet 包、完整的源文件以及每一步为何重要的解释。完成后，您即可生成一个包含矩形和椭圆组合为单一组形状的 DOCX 文件。

## 前置条件

开始之前，请确保您已具备：

* 已安装 .NET 6.0 SDK 或更高版本  
* Visual Studio 2022（或任何支持 .NET 的 IDE）  
* Aspose.Words for .NET NuGet 包（`Aspose.Words`）——免费试用可用于测试，正式许可证可去除评估水印  

这些即是 **add shapes to Word document** 唯一的外部依赖。

## 如何在 Word 中对形状进行分组

解决方案的核心是创建单独的形状、将它们放置在页面上，然后将它们包装进 `GroupShape`。以下步骤与代码的逻辑顺序保持一致。

### 步骤 1：创建文档和构建器

`Document` 对象代表整个 DOCX 文件。`DocumentBuilder` 提供了一个便捷的 API 用于编辑文档。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*为何重要*：`Document` 是所有 Word 元素的容器。`DocumentBuilder` 负责跟踪当前光标位置，这在后续插入组合形状时必不可少。

### 步骤 2：添加矩形形状

通过指定 `ShapeType.Rectangle` 创建矩形。宽度、高度和位置均以点为单位（1 pt ≈ 1/72 in）。

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*为何重要*：设置 `StrokeColor` 可使形状在打开文档时可见。如果需要实心内部，还可以使用 `FillColor` 填充形状。

### 步骤 3：添加椭圆形状

椭圆使用 `ShapeType.Ellipse`。它的大小和位置独立于矩形，从而可以控制组合的最终布局。

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*为何重要*：将椭圆的 `Left` 设置为 120，可避免与矩形重叠，使组合在视觉上更为分明。

### 步骤 4：将两个形状分组

`GroupShape` 充当容器，将其子对象视为单一对象。这是实现 **how to group shapes in Word** 的关键操作。

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*为何重要*：分组后，您可以一起移动、缩放或旋转这两个形状。对 `groupShape` 的任何变换都会传播到其子形状。

### 步骤 5：将组合形状插入文档

`DocumentBuilder.InsertNode` 将 `GroupShape` 放置在当前光标位置。由于构建器未移动，组合会出现在第一页的起始位置。

```csharp
builder.InsertNode(groupShape);
```

*为何重要*：直接插入节点可避免额外的段落或表格单元格。组合形状因此成为文档流的一部分。

### 步骤 6：保存文档

最后，将 DOCX 文件写入磁盘。请使用应用程序有写入权限的完整路径。

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*为何重要*：`doc.Save` 完成所有更改的最终写入。生成的文件可在 Microsoft Word、LibreOffice 或任何支持 DOCX 的查看器中打开。

## 完整源文件

将下面的代码复制到新建的控制台项目（`dotnet new console`）中并运行。程序会生成名为 `GroupShape.docx` 的文件，里面包含一个已分组的矩形和椭圆。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### 预期结果

打开 `GroupShape.docx`。您会看到一个单一的可视对象，左侧是蓝色矩形，右侧是绿色椭圆。 在 Word 中选中该对象时，两种形状会同时被高亮——这证明 **how to group shapes in Word** 已成功实现。

## 常见问题与边缘情况

* **可以添加超过两个形状吗？**  
  可以。在插入组合之前，对每个额外的 `Shape` 调用 `groupShape.AppendChild`。

* **如果需要旋转组合该怎么办？**  
  在构建完组合后设置 `groupShape.RotationAngle = 45;`（角度为度）。

* **需要调用 `doc.UpdatePageLayout()` 吗？**  
  本场景下不需要。保存文档时布局会自动更新。

* **许可证对代码有什么影响？**  
  使用有效的 Aspose.Words 许可证（`License license = new License(); license.SetLicense("Aspose.Words.lic");`）后，生成的文档将不包含评估水印。

## 结论

现在，您已经掌握了使用 Aspose.Words for .NET **how to group shapes in Word** 和 **add shapes to Word document** 的方法。教程涵盖了创建文档、定义单个形状、对它们进行分组、插入组合以及保存文件的完整流程。

接下来，您可以尝试：

* 向组合中添加文本框或图片  
* 更改填充颜色、线条样式或阴影效果  
* 在表格或页眉中对形状进行分组  

这些扩展可帮助您以编程方式构建复杂的 Word 模板，同时保持代码的简洁和可维护性。祝编码愉快！


## 接下来您应该学习什么？

以下教程涉及与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式，每篇资源均提供完整可运行的代码示例和逐步解释。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}