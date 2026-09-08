---
category: general
date: 2026-09-08
description: 学习如何使用 C# 创建空白 Word 文档、插入矩形形状并对多个形状进行分组。请按照本分步指南操作。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: zh
lastmod: 2026-09-08
og_description: 在 C# 中创建空白 Word 文档，插入矩形形状并对多个形状进行分组。本教程将带您完整了解整个过程。
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: 在 C# 中创建带有分组形状的空白 Word 文档
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: 如何创建带有组合形状的空白 Word 文档
url: /zh/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何创建带有分组形状的空白 Word 文档

如果您需要 **创建空白 Word 文档** 并在其中包含自定义图形，本指南将为您详细演示。您将学习如何使用 Aspose.Words for .NET **插入矩形形状**、**分组多个形状**，以及 **向组中添加形状**。

空白文档为您提供了干净的画布，而分组形状可以让您将多个对象作为一个整体移动、缩放或旋转。本教程涵盖了从初始化文档到保存最终文件的每一步，您可以将代码复制到自己的项目中并立即看到效果。

## 您需要的条件

在开始之前，请确保您拥有：

* .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.6+）
* 有效的 Aspose.Words for .NET 许可证（免费评估版可用于测试）
* 如 Visual Studio 2022 或 Visual Studio Code 等 IDE
* 基本的 C# 语法了解

除 `Aspose.Words` 外，无需其他 NuGet 包。

## 如何创建空白 Word 文档

第一步是实例化一个 `Document` 对象。该对象代表一个可以使用 `DocumentBuilder` 编辑的空 `.docx` 文件。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 构造函数在内存中创建一个 **空白 Word 文档**。`DocumentBuilder` 提供了用于插入文本、图像和绘图对象的流畅 API。

## 向文档插入矩形形状

接下来，添加一个矩形形状。该矩形将成为我们稍后创建的组的第一个子对象。

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

使用 `ShapeType.Rectangle` 调用 `InsertShape` 会在当前光标位置 **插入矩形形状**。宽度和高度以点为单位（1 pt ≈ 1/72 in）。

## 将多个形状分组

`GroupShape` 类似于一个容器。组内的所有子形状会一起移动和变换。首先创建组，然后将刚才的矩形添加进去。

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

`InsertGroupShape` 方法在构建器的光标处放置一个空组。通过追加矩形，我们 **分组多个形状**——矩形成为组内部节点集合的一部分。

## 向分组添加形状并保存文件

现在添加第二个形状——椭圆，以演示多个对象共享同一容器的效果。随后保存文档。

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

当您将返回的 `Shape` 追加到 `GroupShape` 时，`InsertShape` 调用 **向组中添加形状**。保存 `Document` 会生成一个 `.docx` 文件，您可以在 Microsoft Word、LibreOffice 或任何兼容的查看器中打开。

### 预期结果

打开 *GroupShapeDemo.docx* 时，您会看到一个空白页面，上面有一个分组对象，包含一个淡蓝色矩形和一个粉红色椭圆。选中该组即可一起移动两个形状，证明 **分组多个形状** 已成功实现。

## 为什么使用 GroupShape？

* **原子化变换** – 缩放、旋转或移动组会统一影响所有子形状。
* **逻辑组织** – 将相关图形放在一起，使文档结构更易维护。
* **性能提升** – 渲染单个容器通常比处理众多独立形状更快。

如果以后需要单独修改某个子形状，可以通过索引或其 `Name` 属性从 `group.ChildNodes` 中检索。

## 常见变体和边缘情况

| 场景                                 | 如何调整代码                                                            |
|--------------------------------------|-------------------------------------------------------------------------|
| **不同的形状类型**                    | 将 `ShapeType.Rectangle` 或 `ShapeType.Ellipse` 替换为其他任意 `ShapeType` |
| **在形状内部添加文本**                | 在插入形状后使用 `Shape.TextPath.Text = "Hello"`                         |
| **设置旋转角度**                      | `group.Rotation = 45;`（度）                                            |
| **保存为 PDF 而非 DOCX**              | `doc.Save("GroupShapeDemo.pdf");`                                        |
| **为组应用边框**                      | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`       |

## 专业技巧

* **为形状命名** – `rectangle.Name = "MyRect";` 可让以后定位更方便。
* **使用相对定位** – 将 `group.RelativeHorizontalPosition` 设置为 `RelativeHorizontalPosition.Page`，可使组锚定在页面边距上。
* **释放资源** – 在大型应用中使用 `using` 块包装 `Document`，及时释放非托管内存。

## 完整源码，快速复制粘贴

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

将代码复制到新的控制台项目中，恢复 `Aspose.Words` NuGet 包并运行。输出文件会出现在项目的 `bin/Debug/net6.0`（或等效）文件夹中。

## 后续步骤

现在您已经能够 **创建空白 Word 文档**、**插入矩形形状** 并 **分组多个形状**，可以进一步探索：

* 在组内添加 **文本框**，创建带标签的图示。
* 使用 `doc.Save("image.png", SaveFormat.Png)` 将分组图形导出为图像。
* 将组与表格结合，生成富格式报告。

尝试不同的形状属性、分组层次结构和导出格式，充分发挥 Aspose.Words 绘图功能的潜力。

--- 

*提醒*: 对形状进行分组是保持 Word 文档整洁和代码可维护的强大方式。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您在自己的项目中进一步掌握 API 功能并探索替代实现方式，每篇资源均提供完整可运行的代码示例和逐步解释。

- [在 Word 中使用 C# 创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [使用 Aspose.Words for .NET 在 Word 文档中插入形状](/words/english/net/working-with-shapes/insert-shape/)
- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}