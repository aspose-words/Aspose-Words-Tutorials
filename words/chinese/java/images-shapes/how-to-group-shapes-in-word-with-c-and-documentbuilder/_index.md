---
category: general
date: 2026-10-04
description: 学习如何使用 C# 在 Word 中对形状进行分组。本指南展示了如何插入矩形形状、将多个形状分组以及以编程方式创建空白 Word 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: zh
lastmod: 2026-10-04
og_description: 使用 C# 在 Word 中对形状进行分组。请按照本分步指南插入矩形形状、对多个形状进行分组，并使用 DocumentBuilder
  创建空白 Word 文件。
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: 使用 C# 在 Word 中对形状进行分组 – 完整的 DocumentBuilder 教程
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: 如何使用 C# 和 DocumentBuilder 在 Word 中对形状进行分组
url: /zh/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 C# 和 DocumentBuilder 对形状进行分组

如果您需要在 C# 应用程序中**对 Word 中的形状进行分组**，本教程将完整演示操作步骤。您将看到如何*插入矩形形状*、将多个绘图合并为一个组，最终**创建一个包含分组对象的空白 Word 文件**。

在程序化生成报表、发票或自定义模板时，处理形状是常见需求。阅读完本指南后，您将拥有一段可复用的代码片段，能够直接嵌入任何引用 Aspose.Words 的 .NET 项目中。

## 您将学到的内容

- 从头创建一个空白 Word 文档。  
- 使用 `DocumentBuilder` 插入矩形形状和椭圆。  
- **将多个形状分组**为 `GroupShape`。  
- 使用 **append child to group** 构建层级结构。  
- 将文件保存到磁盘并验证结果。

不需要事先了解 Aspose.Words，但您应具备 C# 和 .NET 开发的基础知识。

## 前置条件

| 要求 | 原因 |
|------|------|
| .NET 6.0 或更高版本 | 为 C# 代码提供运行时环境。 |
| Aspose.Words for .NET（最新版本） | 提供 `Document`、`DocumentBuilder` 和形状类。 |
| Visual Studio 2022（或 VS Code）等 IDE | 便于编译和运行示例。 |
| 对本机文件夹的写入权限 | `doc.save` 调用需要此权限。 |

通过 NuGet 安装 Aspose.Words：

```bash
dotnet add package Aspose.Words
```

---

## 在 Word 中分组形状 – 步骤指南

下面是完整的可运行程序。每个部分均有详细说明，帮助您理解 **为什么** 这样写代码，而不仅仅是 **做了什么**。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 每一步的重要性

1. **创建空白 Word 文件** – 从干净的文档开始，可确保没有隐藏的格式影响形状定位。  
2. **初始化 DocumentBuilder** – `DocumentBuilder` 抽象了底层节点操作，让您专注于布局。  
3. **插入单个形状** – 必须先创建独立对象（`insert rectangle shape` 和椭圆），才能进行分组。通过设置 `Left` 和 `Top` 使它们并排显示。  
4. **分组多个形状** – 通过创建 `GroupShape` 并使用 **append child to group**，将两个独立绘图合并为一个逻辑单元。移动或缩放该组会同时影响两个子形状。  
5. **保存文档** – 最终文件 `GroupedShapes.docx` 可在 Microsoft Word 中打开，验证矩形和椭圆已成功分组（选中任意一个，两者一起移动）。

### 预期输出

在 Microsoft Word 中打开 `GroupedShapes.docx`：

- 您会看到一个矩形和一个椭圆并排放置。  
- 选中任意形状时，两者都会被高亮，证明它们属于同一组。  
- 该组可以像单个对象一样拖动、缩放或设置格式。

![Word 文档中分组的矩形和椭圆示意图](https://example.com/grouped-shapes.png){: .center-image alt="Word 文档中分组的矩形和椭圆示意图"}

*该截图展示了最终的分组形状。*

---

## 插入矩形形状 – 自定义大小和样式

如果需要特定填充颜色或边框的矩形，可在插入后修改 `Shape` 对象：

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

这些属性属于 `Shape` 类，适用于任何形状类型，而不仅限于矩形。在 **append child to group** 之前调整样式，可确保组继承您设置的视觉属性。

---

## 分组多个形状 – 处理两种以上对象

示例仅分组了矩形和椭圆，但您可以添加任意数量的形状：

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**小技巧：** 构建复杂组后，可锁定其布局以防止意外更改：

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – 顺序很重要

调用 `AppendChild` 的顺序决定 Z‑order（哪个形状位于上方）。在示例中，矩形先加入，随后是椭圆，因此若两者相交，椭圆会覆盖矩形。重新排序只需调用 `RemoveChild` 再重新添加：

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## 创建空白 Word 文件 – 可复用的帮助方法

如果您的应用经常需要全新的文档，可将创建逻辑封装为方法：

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

随后在主程序中将 `new Document()` 替换为 `CreateBlankWordFile()`。这演示了 **create blank word file** 概念的可复用实现方式。

---

## 常见陷阱及规避方法

| 问题 | 产生原因 | 解决方案 |
|------|----------|----------|
| 形状显示在页面之外 | 默认的 `Left`/`Top` 为 0，导致形状位于页边距处。 | 插入后显式设置 `Left` 和 `Top`。 |
| 组失去格式 | 将子形状加入组后再修改其属性会破坏组的布局。 | 在调用 `AppendChild` **之前** 应用所有视觉属性。 |
| 保存的文件为空 | 未使用 `DocumentBuilder` 添加节点，或在不同的 `Document` 实例上调用 `doc.Save`。 | 确认保存的是您构建的同一个 `Document`。 |
| Word 中出现兼容性警告 | 使用了 Word 不支持的新版形状特性 | 采用兼容的属性或检查目标 Word 版本。 |

## 接下来应该学习什么？

以下教程与本指南紧密相关，帮助您进一步掌握 API 功能并探索在项目中的其他实现方式。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}