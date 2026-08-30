---
category: general
date: 2026-07-23
description: 在 C# 中创建空白 Word 文档并添加矩形形状。学习如何使用 Aspose.Words 在 Word 中插入形状并对形状进行分组。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: zh
lastmod: 2026-07-23
og_description: 在 C# 中创建空白 Word 文档，学习如何插入形状、添加矩形形状以及使用 Aspose.Words 对 Word 形状进行分组。
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: 使用分组矩形创建空白 Word 文档 – C# 教程
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 创建带有分组矩形的空白 Word 文档 – C# 指南
url: /zh/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 创建带分组矩形的空 Word 文档 – 指南

是否曾需要 **创建空的 Word 文档**，并且已经包含一组形状，却不确定如何将它们整齐地分组？你并不是唯一遇到这种情况的人。在许多报表或模板生成场景中，你希望拥有一个干净的画布，上面有几个矩形充当占位符，并且希望它们能够作为一个整体一起移动。

在本教程中，我们将逐步演示如何 **创建空的 Word 文档**、**添加矩形形状**，以及随后使用 Aspose.Words 库 **对 Word 中的形状进行分组**。完成后，你将得到一个可直接使用的 `.docx` 文件，其中两个矩形已经成为同一个组的一部分，后续的定位或大小调整将同时作用于它们。

我们还会回答论坛和 Stack Overflow 上常见的 “**如何插入形状**” 与 “**如何分组形状**” 问题。无需外部文档——所有内容都在这里。

---

## 前置条件

- .NET 6 或更高版本（代码同样可以在 .NET Core 上编译）  
- Aspose.Words for .NET（NuGet 包 `Aspose.Words`）  
- 对 C# 语法有基本了解（如果你已经写过 “Hello World”，就足够了）  

如果尚未安装 Aspose.Words，请运行：

```bash
dotnet add package Aspose.Words
```

就这么简单——无需额外的 DLL、无需 COM 互操作，只需一个干净的 NuGet 引用。

---

## 第一步：创建空的 Word 文档并初始化 Builder

首先我们实例化一个空的 `Document` 对象。把它想象成一张全新的纸张。随后我们附加一个 `DocumentBuilder`，这是 Aspose 提供的用于插入内容的便利工具。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **为什么这很重要：** 没有 `DocumentBuilder`，你必须手动操作底层的节点树，容易出错。Builder 将 `.docx` 文件的 XML 细节抽象掉，使用起来更安全。

---

## 第二步：如何插入形状 – 先添加一个组容器

Aspose 允许你插入一个 *组形状*，随后可以在其中放入其他形状。这是实现 **group shapes word** 的基础。  

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **小技巧：** 组本身是不可见的，直到你向其中添加子形状为止。因此在下一步之前，你在生成的文档中看不到任何痕迹。

---

## 第三步：添加矩形形状 – 实际可见的对象

现在我们将 **添加矩形形状** 两次，每次使用不同的尺寸。`InsertShape` 方法接受 `ShapeType` 和以点为单位的尺寸（1 pt ≈ 1/72 英寸）。

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **为什么使用矩形？** 矩形是最简单的几何形状，适合作为占位符、类似按钮的 UI 模拟，或是简单的图形元素。

---

## 第四步：如何分组形状 – 将矩形附加到组中

创建完矩形后，我们通过将它们作为子节点追加到之前插入的组形状来 **如何分组形状**。

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **内部机制是什么？** 组形状成为文档 XML 树中的父节点。移动组就会一起移动两个矩形，保持它们之间的相对位置不变。

---

## 第五步：保存文档 – 现在你拥有一个带分组形状的 Word 文件

最后，将文档持久化到磁盘。请将路径更改为你机器上实际存在的目录。

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

这就是完整的程序。运行后打开 `GroupShape.docx`，你会看到两个矩形并排放置。如果选中其中一个，整个组都会被高亮——这正是 **group shapes word** 所应实现的效果。

---

## 完整源码一览

为方便起见，这里提供可直接复制粘贴的完整示例：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**预期结果：** 打开 `GroupShape.docx`，会看到一个空白页面，上面有两个已分组的矩形。选中任意一个矩形时，另一个会自动被选中，证明分组成功。

---

## 常见问题与边缘情况处理

### 如果需要超过两个形状怎么办？

只需继续调用 `builder.InsertShape(...)` 并对每个新形状执行 `group.AppendChild(...)` 即可。组可以容纳任意数量的子形状。

### 能为矩形设置填充颜色或边框吗？

当然可以。创建矩形后，你可以修改其 `FillColor`、`OutlineColor` 和 `LineWidth`：

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### 创建完组后，如何整体移动它？

使用组的 `Left` 和 `Top` 属性，单位同样是点：

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### 如何对组进行缩放？

设置 `group.Width` 与 `group.Height`，或使用 `group.ScaleX` / `group.ScaleY`。子矩形会相对于组保持比例。

### 这能在旧的 .doc 文件中使用吗？

Aspose.Words 对文件格式进行了抽象，同一段代码既适用于 `.doc` 也适用于 `.docx`。唯一的限制是某些新形状特性在保存为旧的二进制格式时可能会被降级。

---

## 生产环境代码的最佳实践

- **释放资源** – 如果处理大文件，请将 `Document` 包装在 `using` 块中，以便及时释放内存。  
- **错误处理** – 若计划嵌入自定义字体，请捕获 `Aspose.Words.Fonts.FontSettingsException`。  
- **性能优化** – 插入大量形状时，可临时关闭布局更新：`doc.LayoutOptions = new LayoutOptions { UpdateFields = false };`，完成后再重新启用。

---

## 结论

现在，你已经掌握了使用 Aspose.Words 在 C# 中 **创建空的 Word 文档**、**添加矩形形状**，以及 **对 Word 中的形状进行分组** 的完整流程。示例涵盖了关键的 “**如何插入形状**” 与 “**如何分组形状**” 步骤，解释了每行代码的作用，并涉及了自定义、边缘情况以及最佳实践。

接下来，你可以进一步探索 **如何插入图片**、**在分组形状内部添加文本**，或 **将文档导出为 PDF**——这些操作同样遵循 `DocumentBuilder` 与形状操作的模式。多多实验，Aspose API 足以应对几乎所有你能想象的 Word 自动化场景。

祝编码愉快，如有问题欢迎留言交流！

## 接下来该学习什么？

以下教程与本指南的技术紧密相连，帮助你进一步深化对相关 API 的掌握，并提供可直接运行的代码示例与逐步讲解。

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}