---
category: general
date: 2026-10-26
description: 在 C# 中创建一个空白的 Word 文档，学习如何插入组合形状，然后向该组合中添加矩形形状。本指南逐步讲解如何对多个形状进行组合。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: zh
lastmod: 2026-10-26
og_description: 在 C# 中创建空白 Word 文档，了解如何插入组，然后添加矩形形状。通过完整的代码示例掌握多个形状的分组。
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: 创建空白 Word 文档并对多个形状进行分组 – C# 教程
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 如何创建空白Word文档并对多个形状进行组合
url: /zh/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何创建空白 Word 文档并对多个形状进行分组

如果您需要以编程方式 **创建空白 Word 文档**，本教程将为您详细演示。您将看到如何插入一个组形状，然后 **添加矩形** 到该组，完整覆盖从空文档到分组绘图的工作流程。

处理 Word 文件通常意味着将多个绘图对象一起排列——比如由多个形状组成的示意图。阅读完本指南后，您将能够 **对多个形状进行分组**，插入 **矩形形状**，并以简洁、可复用的方式了解 **如何插入组** 和 **如何添加矩形**。

## 您需要的条件

* .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.6+）
* **Aspose.Words for .NET** NuGet 包 (`Install-Package Aspose.Words`)
* 对 C# 和 Visual Studio IDE（任何 IDE 都可）有基本了解

> **小贴士：** Aspose.Words 完全离线运行；安装完包后无需互联网连接。

## 步骤 1：创建空白 Word 文档

第一步是实例化一个空的 `Document` 对象。该对象代表您随后将向其添加形状的 **空白 Word 文档**。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*为什么重要：* 即使没有任何节或段落的 `Document` 仍然是有效的 .docx 文件。从干净的起点开始可确保没有隐藏的格式会干扰您之后添加的形状。

## 步骤 2：插入组形状（how to insert group）

**组形状** 类似于一个容器，可容纳其他绘图对象。在 Aspose.Words 中，您可以使用 `InsertGroupShape` 创建它。

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*为什么使用组？* 通过分组，您可以将多个形状作为一个整体移动、旋转或调整大小。这对于需要保持对齐的图表至关重要。

## 步骤 3：插入矩形形状（insert rectangle shape）

现在向文档中添加一个矩形。`InsertShape` 方法返回一个 `Shape` 对象，您随后可以将其附加到组中。

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*为什么是矩形？* 矩形是流程图、UI 原型和占位图形最常用的构建块。尺寸以点为单位表示（1 pt ≈ 1/72 英寸）。

## 步骤 4：将矩形添加到组中（how to add rectangle）

使用 `InsertShape` 创建的形状直接位于文档主体中。要将其加入组中，请对 `GroupShape` 调用 `AppendChild`。

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*内部发生了什么？* `AppendChild` 会将矩形节点从文档的主故事移动到组的内部集合中，同时保留其相对于组原点的大小和位置。

## 步骤 5：保存文档

最后，将文件写入磁盘。您可以在 Microsoft Word 中打开生成的 `.docx`，查看已分组的矩形。

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **特殊情况：** 如果您打算向同一组中添加更多形状（例如圆形、线条），请在保存之前对每个新形状重复 **步骤 3** 和 **步骤 4**。组会自动调整其边界框以容纳所有子形状。

## 如何对多个形状进行分组 – 示例扩展

下面是一个快速代码片段，向同一组中添加第二个形状（椭圆），演示在单个文档中 **对多个形状进行分组**。

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

当您打开 `GroupedShapeExample.docx` 时，您会看到在 Word 中选中该组时，矩形和椭圆会一起移动。

## 常见问题与故障排除

| Question | Answer |
|----------|--------|
| **我需要为 Aspose.Words 购买许可证吗？** | 免费评估版无需许可证即可使用，但会添加水印。用于生产环境时，请申请许可证以去除水印并解锁全部性能。 |
| **我可以精确定位形状吗？** | 可以。插入形状后，您可以设置 `Shape.Left`、`Shape.Top`、`Shape.Width` 和 `Shape.Height` 属性。 |
| **如果保存后矩形消失了怎么办？** | 确保在插入矩形后 *调用* `group.AppendChild(rectangle)`。必须先将形状添加到文档主体，然后再将其移动到组中。 |
| **可以跨不同节对形状进行分组吗？** | 不可以。组内的所有形状必须属于同一故事（节）。如有需要，请在每个节创建单独的组。 |

## 回顾

现在，您已经了解如何使用 Aspose.Words for .NET **创建空白 Word 文档**、**插入组**、**添加矩形**以及 **对多个形状进行分组**。上面的完整可运行示例可以直接复制到控制台应用程序中并立即执行。

## 后续步骤

* 试验 **insert rectangle shape** 的尺寸和颜色（例如 `rectangle.FillColor = Color.LightBlue;`）。  
* 探索其他形状类型（如 `ShapeType.Polygon`、`ShapeType.Line`），以丰富您的图表。  
* 学习如何将最终的 `.docx` 转换为 PDF（`doc.Save("output.pdf");`）以便分发。  
* 深入了解 **how to add rectangle** 到已包含文本的现有文档——使用 `DocumentBuilder.MoveTo` 将组定位到所需位置。

欢迎根据自己的报告或图表生成需求自行改写代码。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题，构建在本指南演示的技巧之上。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [How to create blank Word document and group shapes in C#](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [How to group shapes in Word and add shapes to Word document](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [How to create rectangle shape and group shapes in Word with Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}