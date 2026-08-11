---
category: general
date: 2026-08-10
description: 使用 Aspose.Words 编程创建 Word 文档，学习如何对 Word 中的多个形状进行分组，向 Word 添加矩形，以及在 C#
  中创建组合形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: zh
lastmod: 2026-08-10
og_description: 使用 Aspose.Words 以编程方式创建 Word 文档。本指南展示了如何对 Word 中的多个形状进行分组、添加矩形以及嵌入纯文本内容控件，全部使用
  C#。
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: 以编程方式创建 Word 文档 – 在 C# 中对形状进行分组
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: 在 C# 中以编程方式创建 Word 文档并对形状进行分组
url: /zh/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 编程创建 Word 文档并对形状进行分组

如果您需要 **以编程方式创建 Word 文档**，本教程将向您展示如何使用 Aspose.Words 构建 DOCX 文件并 **将多个形状在 Word 中分组**。我们还会介绍 **向 Word 中添加矩形** 以及 **如何创建包含矩形和椭圆的分组形状**，并加入一个用于用户输入的纯文本 StructuredDocumentTag（内容控件）。

完成后，您将得到一个可直接使用的 Word 文件，其中包含一个已分组的矩形‑椭圆形状以及一个用户可以键入姓名的内容控件。代码运行后无需在 Word 中进行任何手动编辑。

## 您需要的环境

- .NET 6.0 或更高版本（示例针对 .NET 6，但任何近期的 .NET 版本均可）
- Aspose.Words for .NET 授权（免费试用版可用于测试）
- Visual Studio 2022 或您喜欢的任意 C# IDE
- 对 C# 语法的基本了解

## 以编程方式创建 Word 文档 – 整体工作流

该过程分为三个逻辑阶段：

1. **初始化** `Document` 和 `DocumentBuilder` – 这是生成任何 Word 文件的基础。
2. **构建分组形状**，其中包含矩形和椭圆 – 演示 **在 Word 中分组多个形状** 以及 **如何创建分组形状**。
3. **插入 StructuredDocumentTag (SDT)** – 一个纯文本内容控件，允许最终用户填写数据，展示 **向 Word 中添加矩形** 作为整体文档布局的一部分。

下面是完整可运行的代码，随后是逐步解析。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### 步骤 1 – 初始化文档和构建器
`Document` 对象代表整个 DOCX 文件，而 `DocumentBuilder` 提供了便捷的 API 用于添加内容。初始化它们是 **以编程方式创建 Word 文档** 时的首要需求。

> **小贴士：** 如果计划在多个操作中复用同一个文档，请保留单一的 `DocumentBuilder` 实例，以避免不必要的对象创建。

### 步骤 2 – 创建分组形状容器
使用 `ShapeType.Group` 的 `Shape` 充当画布，可容纳其他形状。设置 `Width` 和 `Height` 定义分组的边界框。这是 Aspose.Words 中 **如何创建分组形状** 的核心。

> **边缘情况：** 如果分组的宽度小于其子形状的总宽度，子形状将被裁剪。请确保分组足够大，以容纳所有子形状。

### 步骤 3 – 向 Word 中添加矩形
使用 `ShapeType.Rectangle` 创建矩形。其 `Left` 和 `Top` 属性相对于分组原点定位。此步骤演示 **向 Word 中添加矩形**，并展示如何精确控制位置。

> **常见错误：** 忘记设置 `Left`/`Top` 会导致矩形出现在分组的默认原点 (0,0)，可能与其他子形状重叠。

### 步骤 4 – 向分组中添加椭圆（圆形）
椭圆的添加方式与矩形相同，只是使用 `ShapeType.Ellipse`。`Left = 210` 将其移动到矩形右侧，在同一分组内形成视觉上区分的形状对。

> **为何使用分组？** 分组后，您可以一次性移动、旋转或缩放这两个形状，保持它们的相对布局。

### 步骤 5 – 将完成的分组形状插入文档
`builder.InsertNode(groupShape)` 将整个分组放置在当前光标位置。因为分组已经包含子形状，无需再为矩形或椭圆单独调用插入方法。

### 步骤 6 – 创建纯文本 StructuredDocumentTag (SDT)
StructuredDocumentTag 是一种内容控件，文档在 Word 中打开时，最终用户可以填写。设置 `Title = "CustomerName"` 为控件提供有意义的标识，便于后续数据提取。

> **为何使用纯文本 SDT？** 它限制输入为纯文本，防止意外的格式化导致下游处理出错。

### 步骤 7 – 保存文档
`doc.Save("GroupAndSDT.docx")` 将文件写入磁盘。生成的 DOCX 包含分组形状和 SDT。使用 Microsoft Word 打开文件时，会看到一个矩形旁边是一个圆形，两者可作为单个对象选中，下面还有一个占位文字 “Enter name here …”。

#### 预期输出
- 在执行文件夹中生成名为 **GroupAndSDT.docx** 的文件。
- 在 Word 中：一个分组形状（矩形 + 椭圆），可整体移动。
- 紧随分组下方的是一个灰色阴影的内容控件，提示用户输入姓名。

## 其他变体与最佳实践

### 使用不同的形状类型
您可以将 `ShapeType.Rectangle` 或 `ShapeType.Ellipse` 替换为任意其他 `ShapeType`（例如 `ShapeType.Polygon`、`ShapeType.Line`）。分组逻辑保持不变。

### 设置填充颜色和边框
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
添加填充和描边可以提升视觉区分度，尤其在文档需要与非技术人员共享时。

### 旋转整个分组
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
一次性旋转分组比逐个旋转子形状更高效。

### 导出为 PDF
如果需要 PDF 版本，只需调用：
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
所有分组形状和 SDT（呈现为文本字段）都会出现在 PDF 中。

## 常见陷阱及规避方法

| 症状 | 原因 | 解决方案 |
|------|------|----------|
|      |      |          |
|      |      |          |
|      |      |          |

## 接下来您应该学习什么？

以下教程涵盖与本指南紧密相关的主题，帮助您在实际项目中进一步掌握 API 功能并探索替代实现方式。每篇资源均提供完整可运行的代码示例和逐步解释。

- [使用 Aspose.Words for .NET 在 Word 文档中创建分组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 C# 在 Word 中创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [使用带阴影矩形形状创建空白 Word 文档 – 步骤指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}