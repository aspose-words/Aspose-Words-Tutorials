---
category: general
date: 2026-09-11
description: 学习如何使用 Aspose.Words 创建 Word 文档、添加矩形形状并设置形状尺寸。一步一步的 C# 指南，帮助实现精确的形状大小。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: zh
lastmod: 2026-09-11
og_description: 使用 Aspose.Words 在 C# 中创建 Word 文档。本指南展示了如何添加矩形形状、设置形状大小以及以编程方式管理形状尺寸。
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: 使用形状创建 Word 文档 – Aspose.Words C# 教程
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: 如何使用 Aspose.Words 在 C# 中创建带有形状的 Word 文档
url: /zh/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words 在 C# 中创建带形状的 Word 文档

如果您需要 **创建 Word 文档** 并在其中包含自定义图形，完全可以通过代码实现。本教程将手把手教您创建 Word 文件、添加矩形形状以及控制形状的每一个尺寸。完成后，您将拥有一段可在任何 .NET 项目中直接使用的可复用代码片段。

您将学习如何 **添加矩形形状**、**设置形状大小**，以及在分组容器内部 **设置形状尺寸**。示例使用 Aspose.Words 13.9，但这些概念同样适用于后续版本。无需事先了解 Aspose 绘图 API——只要具备基本的 C# 知识即可。

## 前置条件

- 已安装 .NET 6.0 或更高版本  
- Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）  
- 如 Visual Studio 2022 等 IDE（任何支持 C# 的编辑器均可）  

准备好这些工具后，您即可立即运行代码，无需额外配置。

## 步骤 1：初始化文档和构建器 – 创建 Word 文档基础

首要操作是实例化 `Document` 对象和 `DocumentBuilder`。`Document` 代表文件本身，而 `DocumentBuilder` 提供用于插入内容的流畅 API。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**为什么这很重要：**  
提前创建文档可以为您提供一块干净的画布。构建器的光标默认位于第一个段落，这正是我们随后 **在 Word 中创建形状** 的位置。

## 步骤 2：构建 GroupShape 以容纳多个图形

`GroupShape` 类似一个容器；您可以将整个组整体移动、旋转或缩放。这里我们以点为单位（1 pt ≈ 1/72 in）定义容器的宽度和高度。

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**为什么这很重要：**  
对形状进行分组可以简化布局管理。如果以后需要添加更多形状（例如圆形或文本框），它们将继承组的定位和缩放属性。

## 步骤 3：创建矩形形状并配置其尺寸

现在我们添加实际的矩形。`Shape` 构造函数需要文档引用和形状类型。创建后，我们显式 **设置形状大小** 并 **设置形状尺寸**。

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**为什么这很重要：**  
指定宽度、高度、左侧和顶部位置可以让您对形状实现像素级的精准控制。当文档必须符合设计规范或打印表单时，这一点尤为关键。

## 步骤 4：通过追加矩形来组装分组

将矩形追加到 `GroupShape` 中，使其成为子节点。您可以在将组插入文档之前，根据需要添加任意数量的子节点。

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**提示：** 如果计划添加第二个形状，使用相同方式创建后调用 `group.AppendChild(secondShape)` 即可。所有子节点共享同一坐标系。

## 步骤 5：将分组形状插入文档并保存

组装完成后，我们将其放入当前段落。构建器的 `CurrentParagraph` 属性可直接访问底层节点树。

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**为什么这很重要：**  
将组追加到段落可确保形状随文本流内联显示。保存文档即完成 **创建 Word 文档** 的操作。

## 常见变体和边缘情况

| 场景 | 调整方式 |
|----------|------------|
| **不同的页面方向** | 在创建组之前设置 `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` |
| **多个矩形** | 创建额外的 `Shape` 对象，并对每个调用 `group.AppendChild(newRect)` |
| **基于内容的动态尺寸** | 根据图像尺寸或文本度量计算宽高，然后赋值给 `rectangle.Width` / `rectangle.Height` |
| **导出为 PDF** | 在 `doc.Save` 之后调用 `doc.Save("GroupShape.pdf", SaveFormat.Pdf);` |
| **兼容旧版 Word** | 使用 `SaveFormat.Doc` 而非 `Docx` 保存，以兼容 Word 97‑2003 |

这些变体展示了相同核心逻辑如何适配各种实际需求。

## 完整可运行示例

下面是完整的程序代码，您可以直接复制、粘贴并运行。示例包含所有 `using` 指令、`Main` 入口以及解释每行代码的注释。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**预期输出：**  
打开 *GroupShape.docx* 后，第一页会显示一个灰色边框的矩形，距左/上边距 50 pt，矩形本身在组内偏移 10 pt。其尺寸与代码中设置的数值完全一致。

## 结论

现在，您已经掌握了如何 **创建 Word 文档**、**添加矩形形状**，以及使用 Aspose.Words 精确 **设置形状大小** 和 **设置形状尺寸** 的方法。分组形状的做法让布局保持灵活，便于后续扩展（如添加更多图形或文本框）。

接下来，您可以进一步探索 **在 Word 中创建形状**（如圆形、箭头或自定义 SVG 路径），以及学习如何 **设置形状填充颜色** 或 **应用旋转**。尝试不同的度量单位，观察 Word 对点与厘米的渲染差异，并将此代码集成到更大的文档生成流水线中。

祝编码愉快，欢迎将此模式应用于任何自动化报表或表单填充场景！

## 接下来您应该学习什么？

以下教程与本指南紧密相关，帮助您进一步深化所学技术。每篇资源均提供完整可运行的代码示例，并配有逐步解释，助您掌握更多 API 功能或在项目中尝试替代实现方案。

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}