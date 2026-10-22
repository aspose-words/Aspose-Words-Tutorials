---
category: general
date: 2026-09-05
description: 使用 Aspose.Words 在 Word 文档中创建矩形形状，然后学习如何在 Word 中插入椭圆形文字并对形状进行分组，以实现更丰富的布局。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: zh
lastmod: 2026-09-05
og_description: 使用 Aspose.Words 在 Word 文档中创建矩形形状，然后了解如何在 Word 中插入椭圆形并对形状进行分组，以实现复杂布局。
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: 在 Word 中创建矩形形状并对形状进行分组 – Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 Aspose.Words 在 Word 中创建矩形形状并对形状进行分组
url: /zh/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words 在 Word 中创建矩形形状并对形状进行分组

如果您需要在 Word 文档中**创建矩形形状**，本指南将展示使用 Aspose.Words for .NET 的完整步骤。您还将看到如何插入椭圆形、在 Word 中对形状进行分组，并将结果保存为 DOCX 文件。该方案适用于任何 .NET 6+ 项目，且无需在服务器上安装 Microsoft Office。

本教程涵盖从项目设置到常见布局陷阱的处理，您可以直接复制代码并立即运行。

## 前置条件

在开始之前，请确保您具备以下条件：

* 已安装 .NET 6 SDK 或更高版本  
* 支持 NuGet 的 IDE（Visual Studio、Rider 或 VS Code）  
* Aspose.Words for .NET 许可证（或临时评估密钥）  
* 基本的 C# 和 Word 文档结构知识  

这些条件可确保代码能够编译并正确渲染形状。

## 第 1 步：创建项目并添加 Aspose.Words

创建一个新的控制台项目并添加 Aspose.Words 包：

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

该包提供了本教程中使用的 `Document`、`DocumentBuilder`、`Shape` 和 `GroupShape` 类。

## 第 2 步：初始化空白文档和构建器

`Document` 对象代表整个 Word 文件，而 `DocumentBuilder` 允许您以编程方式插入内容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

先创建文档可确保后续所有形状操作都有有效的容器。

## 第 3 步：**创建矩形形状**并设置尺寸

矩形是最常用的文本或图像容器。您需要以点为单位定义其大小（1 pt ≈ 1/72 英寸）。

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

此步骤的重要性在于：`Shape` 类封装了几何、填充和线条属性。先设置 `Width` 和 `Height` 再插入，可保证形状以预期尺寸出现。

## 第 4 步：**如何插入椭圆形** – 添加椭圆形状

椭圆可用于图标、标记或装饰元素。代码与矩形创建相似，唯一变化是 `ShapeType`。

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

`FillColor` 和 `Line.Color` 属性演示了如何在不使用外部图片的情况下自定义外观。

## 第 5 步：**在 Word 中对形状进行分组** – 将矩形和椭圆组合

分组可让您将多个形状作为一个单元移动、缩放或旋转。这在需要复合图形（例如带标签的图标）时尤为重要。

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

调用 `AppendChild` 时，原始形状会从主文档流中移除，成为 `GroupShape` 的子节点。该组表现为单个形状，简化后续的布局调整。

## 第 6 步：保存文档

最后，将文档写入磁盘。您可以选择任意受支持的格式（`.docx`、`.pdf`、`.html` 等），本教程使用原生 Word 格式。

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

运行程序后，用 Microsoft Word 打开 *GroupShape.docx*，即可看到矩形和椭圆已被分组，并位于您指定的坐标位置。

## 常见变体和边缘情况

| 场景 | 需要更改的内容 | 原因 |
|-----------|----------------|--------|
| **不同的尺寸单位** | 使用 `ConvertUtil.InchToPoint(2.5)` 表示英寸，或 `ConvertUtil.MillimeterToPoint(30)` 表示毫米。 | 当使用非点单位时，使代码更易读。 |
| **在矩形内部添加文本** | 创建 `Paragraph` 节点，设置其 `Text` 属性，然后通过 `AppendChild` 添加到 `rectangleShape`。 | 无需单独的文本框即可为形状添加标签。 |
| **旋转组** | 设置 `groupShape.Rotation = 45;`（单位：度）。 | 用于创建对角徽章或水印。 |
| **保存为 PDF** | 调用 `doc.Save("GroupShape.pdf");`。 | Aspose.Words 会自动将矢量形状栅格化为 PDF 输出。 |
| **多个组** | 创建额外的 `GroupShape` 实例并重复追加/插入步骤。 | 实现包含多个独立复合体的复杂页面布局。 |

### 专业提示

始终在 **分组之前** 添加形状。如果尝试对已经属于其他组的形状进行分组，Aspose.Words 会抛出 `ArgumentException`。在单一方法中构建组可避免此运行时错误。

### 注意事项

* **坐标系** – `Left` 和 `Top` 是相对于页面的左、上边距，而非文档边缘。误解此概念会导致形状超出页面。  
* **授权** – 若未使用有效许可证，保存的文档会出现 “Aspose.Words for .NET Evaluation” 水印。请在代码开头尽早加载许可证（`License license = new License(); license.SetLicense("Aspose.Words.lic");`），以避免水印。

## 完整源代码（可运行）

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

运行此程序后，会生成 *GroupShape.docx*，其中的形状已按描述进行分组。

## 结论

现在，您已经掌握了使用 Aspose.Words **创建矩形形状**、**插入椭圆形**以及**在 Word 中对形状进行分组**的完整流程。完整示例展示了从初始化文档到保存最终文件的全部工作流，帮助您将形状处理集成到任何自动化报表或文档生成解决方案中。

### 接下来可以做什么？

* 探索 **aspose.words create shapes**，了解更复杂的几何形状，如 `Polygon` 或 `Freeform`。  
* 将分组形状与 **内容控件** 结合，构建动态模板。  
* 将 DOCX 转换为 PDF 或 HTML，观察矢量形状在不同格式下的渲染效果。  

欢迎尝试不同的尺寸、颜色和旋转角度。掌握形状分组后，您可以在 Word 文档中直接创建复杂的图表、徽章以及自定义 UI 元素。

## 接下来应该学习什么？

以下教程与本指南紧密相关，帮助您进一步深化所学技术。每个资源均包含完整的可运行代码示例和逐步解释，助您掌握更多 API 功能并探索替代实现方式。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}