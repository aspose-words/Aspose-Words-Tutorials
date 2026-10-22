---
category: general
date: 2026-09-11
description: 学习如何使用 C# 在 Word 中隐藏形状。本指南还展示了如何插入矩形形状以及使用 Aspose.Words 将形状插入 Word 文档。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: zh
lastmod: 2026-09-11
og_description: 如何使用 C# 和 Aspose.Words 在 Word 中隐藏形状。请按照分步教程插入矩形形状并管理 Word 文档中的形状。
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: 如何在 Word 中隐藏形状 – 完整的 C# 指南
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 C# 和 Aspose.Words 隐藏 Word 中的形状
url: /zh/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 C# 和 Aspose.Words 隐藏形状

如果您需要在 Word 中隐藏形状但仍保留该形状在文档结构中的存在，本教程将为您展示完整步骤。使用 Aspose.Words for .NET，您可以插入一个矩形形状、将其隐藏，并在后续处理时仍保留其位置。

Word 自动化常常需要对形状进行细粒度控制——无论是生成模板、准备报告，还是构建文档编辑服务。阅读完本指南后，您将能够：

* 在 Word 文档中插入矩形形状（`insert rectangle shape`）。
* 在不删除形状的情况下隐藏任意形状（`how to hide shape in word`）。
* 保存结果并验证隐藏的形状不会出现在渲染视图中（`insert shape into word document`）。

本示例适用于 Aspose.Words 24.10 或更高版本，目标为 .NET 6.0+，但概念同样适用于更早的版本。

## 前置条件

* **Aspose.Words for .NET** ≥ 24.10。您可以从 Aspose 官网获取免费临时许可证。
* **.NET SDK** 6.0 或更高版本已安装在您的机器上。
* 开发环境，例如 Visual Studio 2022、VS Code 或 Rider。
* 对 C# 和 Word Open XML 概念有基本了解（可选，但有帮助）。

## 使用 Aspose.Words 在 Word 中隐藏形状

下面是一段完整、可运行的程序，演示了整个工作流——从创建文档、插入矩形形状到最终隐藏它。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### 各步骤说明

1. **创建新文档** – `Document` 表示内存中的 Word 文件。`DocumentBuilder` 提供流式 API 用于插入内容。  
2. **插入矩形形状** – `InsertShape` 创建类型为 `Rectangle` 的绘图对象。尺寸以点为单位（1 pt ≈ 1/72 in），满足 `insert rectangle shape` 的需求。  
3. **隐藏形状** – 将 `Shape.Hidden = true` 设置为 true，会在 Word 标记中生成 `<w:hidden/>`。形状仍然是文档树的一部分，后续可以取消隐藏或通过代码引用。这正是 `how to hide shape in word` 的核心。  
4. **保存文件** – 文档写入 `output.docx`。在 Microsoft Word 中打开时，矩形不可见，但仍存在于 XML 中，可使用 ZIP 查看器或 Open XML SDK 检查。

### 预期结果

在 Microsoft Word 中打开 `output.docx`：

* 文档看起来是空的——没有可见的形状。  
* 若检查底层 XML（`word/document.xml`），会发现包含 `<w:pict>` 元素以及 `<w:hidden/>` 属性，证明形状已存在但被隐藏。

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

通过将 `Hidden = false` 并重新保存文档，即可再次显示隐藏的形状。

## 在 Word 文档中插入矩形形状

虽然主要目标是隐藏形状，但许多场景首先需要插入形状。`InsertShape` 方法支持多种 `ShapeType`，包括 `Rectangle`、`Ellipse`、`Line` 以及自定义图片。

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**为什么使用矩形？**  
矩形提供了一个干净、轴对齐的容器，可容纳文本、图片或其他嵌套形状。它常被用作表格、图表等动态内容的占位符。先插入矩形可以在后续隐藏时仍保持布局一致性。

## 向 Word 文档插入形状的最佳实践

在 `insert shape into word document` 时，请考虑以下要点：

* **设置明确的尺寸** – 避免依赖自动大小；使用点指定宽度和高度，以确保跨平台布局一致。  
* **定义定位** – 默认情况下形状锚定在当前段落。使用 `builder.MoveTo` 或 `builder.StartBookmark` 可精确放置。  
* **提前应用样式** – 填充颜色、线条样式和文本环绕会影响最终外观。即使是隐藏的形状，也应设置合适的样式，因为标记保持不变。  
* **版本兼容性** – `Hidden` 属性仅在 Aspose.Words 24.10 及以上可用。若目标为旧版本，可使用 `Node` API 手动添加 `<w:hidden/>` 属性。

### 手动添加 hidden 属性（回退方案）

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## 完整的端到端示例

将所有内容组合在一起，下面的程序会：

1. 插入一个矩形形状。  
2. 隐藏该形状。  
3. 插入一个可见的椭圆以作对比。  
4. 保存文档。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

运行程序后会生成 `demo_output.docx`。打开后，您只会看到珊瑚色的椭圆；绿色矩形仍然存在于 XML 中，但在视图中被隐藏。

## 常见问题与边缘情况

**Q: 隐藏形状会影响分页吗？**  
A: 不会。隐藏的形状会被布局引擎忽略，不会占用空间。这对于不应影响分页的占位内容非常有用。

**Q: 能否隐藏位于页眉或页脚中的形状？**  
A: 可以。`Hidden` 属性同样适用于文档树中任何位置的形状，包括页眉、页脚，甚至表格内部。

**Q: 如果需要一次隐藏多个形状怎么办？**  
A: 遍历 `Document.GetChildNodes(NodeType.Shape, true)` 集合，对每个目标形状设置 `Hidden = true`。

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**Q: 转换为 PDF 时 hidden 属性会被保留吗？**  
A: 转换为 PDF 时，默认会省略隐藏的形状，行为与 Word 的渲染一致。如果需要在 PDF 中保留它们，必须在转换前取消隐藏。

## 提示与陷阱

* **专业技巧：** 在隐藏之前将 `shape.WrapType = WrapType.None`，这样后续取消隐藏时不会扰乱周围文本。  
* **注意旧版 Aspose.Words：** 在 24.10 之前，`Hidden` 属性会抛出 `NotSupportedException`。此时请使用手动 XML 方法。  
* **测试建议：** 始终在 Word 中打开生成的 `.docx`，并使用“显示 XML 标记”（开发者选项卡）确认 `<w:hidden/>` 属性已存在。

## 结论

现在，您已经掌握了使用 C# 和 Aspose.Words 在 Word 中隐藏形状的方法，并了解了如何插入矩形形状以及在文档中插入形状并完全控制其可见性。通过利用 `Hidden` 属性，您可以在文档模型中保留形状以供后续处理，同时向最终用户呈现干净的视图。

接下来，您可以进一步探索以下主题，例如 **运行时更新形状属性**、**将隐藏形状转换为图像**，或 **使用 Open XML SDK 直接操作隐藏元素**。这些扩展将帮助您更深入地使用 API。

## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您在实际项目中进一步应用这些技巧。每个资源都提供完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并探索替代实现方式。

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}