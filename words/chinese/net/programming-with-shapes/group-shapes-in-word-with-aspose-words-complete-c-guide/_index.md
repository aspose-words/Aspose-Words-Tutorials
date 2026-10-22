---
category: general
date: 2026-07-19
description: 使用 Aspose.Words 在 Word 中对形状进行分组。了解如何添加矩形形状、定义椭圆形状以及将形状插入 Word 文档。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: zh
lastmod: 2026-07-19
og_description: 使用 Aspose.Words 在 Word 中对形状进行分组。掌握添加矩形形状、定义椭圆形状以及将形状插入 Word 文档的方法。
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Word 中的组合形状 – 步骤式 C# 教程
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 在 Word 中使用 Aspose.Words 对形状进行分组 – 完整 C# 指南
url: /zh/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中对形状进行分组 – 完整 C# 指南

有没有想过如何在 **Word 中对形状进行分组** 而不必手动操作界面？你并不孤单。无论是程序化生成合同、传单还是图表，能够 **添加矩形形状**、**定义椭圆形状**，随后 **在 Word 中对形状进行分组**，都能为你节省大量手工工作时间。

在本教程中，我们将使用 **Aspose.Words for .NET** 通过一个真实案例进行演示。完成后，你将掌握如何 **将形状插入 Word**、将它们组合，并生成可以交付给客户或团队成员的精美文档。

---

## 你需要准备的内容

在开始之前，请确保具备以下条件：

- **Aspose.Words for .NET**（最新版本，例如 24.9）。可通过 NuGet 使用 `Install-Package Aspose.Words` 获取。
- .NET 开发环境（Visual Studio 2022 或配有 C# 扩展的 VS Code 均可）。
- 对 C# 语法有基本了解——只需常规的 `using` 语句和对象创建即可。

就这些。无需额外库、无需 COM 互操作，纯托管代码即可。

---

## 使用 Aspose.Words 在 Word 中对形状进行分组的步骤

下面是与您已有代码相对应的逐步说明。每一步都会解释 **为什么** 要这么做，而不仅仅是 **做了什么**，帮助你将此模式应用到任意形状上。

### 步骤 1：设置文档和 Builder

我们先创建一个空的 `Document` 和一个 `DocumentBuilder`。Builder 就是我们的“笔”，可以在任意位置插入内容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **为什么？** `Document` 对象代表整个 .docx 文件，而 `DocumentBuilder` 提供了便捷的 API，用于在不直接操作底层节点树的情况下插入节点（如形状）。

### 步骤 2：添加矩形形状（add rectangle shape）

现在我们 **添加矩形形状** 到文档中。设置其大小、位置以及填充颜色，使其突出显示。

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **提示：** 你可以将 `FillColor` 改为任意 `System.Drawing.Color`。在报告中需要颜色编码的章节时，这非常有用。

### 步骤 3：定义椭圆形状（define ellipse shape）

接下来，我们 **定义椭圆形状**。注意不同的 `ShapeType` 以及偏移量（`Left = 120`），使椭圆位于矩形旁边。

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **为什么重要：** 通过显式定位形状，你可以控制它们在分组前的显示方式。如果依赖自动布局，分组后可能会出现偏移。

### 步骤 4：（可选）单独插入形状进行预览

如果想在分组前查看每个形状，可以 **将形状插入 Word** 单独展示。此步骤可选，但对调试很有帮助。

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **专业技巧：** 确认形状显示正常后，将这两行代码注释掉；否则在分组后会出现重复的视觉元素。

### 步骤 5：如何分组形状 – 创建 GroupShape

下面是本教程的核心：**如何分组形状**。我们创建一个 `GroupShape`，将矩形和椭圆附加进去，并决定该组在文本中的环绕行为。

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **解释：** `GroupShape` 本质上是一个小型画布，用来容纳其他形状。将 `WrapType` 设置为 `Inline`，整个组在添加或删除文本时会作为单一单元移动。

### 步骤 6：将分组后的形状插入文档（insert shape into word）

现在我们 **将形状插入 Word**——这一次插入的是分组容器，而不是单个形状。

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **底层发生了什么？** `InsertNode` 调用将 `GroupShape` 添加到文档的节点集合中。因为该组已经包含矩形和椭圆，它们会一起作为一个对象出现。

### 步骤 7：保存文档

最后，将文件写入磁盘。你可以根据项目结构修改路径。

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **结果：** 在 Microsoft Word 中打开 `GroupShape.docx`，你会看到一个淡蓝色矩形和一个珊瑚色椭圆被锁定在一起。拖动其中一个会连带另一个移动——这正是 “在 Word 中对形状进行分组” 所承诺的效果。

---

## 可视化确认

下面是分组形状在 Word 文件中的示意图。  

![使用 Aspose.Words 创建的 Word 文档中分组形状的截图](grouped_shapes_placeholder.png "在 Word 中对形状进行分组")

*图片的 alt 文本包含了主要关键词，以提升可访问性和 SEO 效果。*

---

## 常见问题与边缘情况

### 如果需要超过两个形状怎么办？

只需在插入组之前继续调用 `groupShape.AppendChild(yourNewShape);`。API 对子形状数量没有限制。

### 能否旋转或调整整个组的大小？

完全可以。`GroupShape` 继承自 `Shape`，因此可以在组本身上设置 `RotationAngle`、`Width`、`Height` 等属性，所有子形状会随之变化。

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### 如何更改组的背景颜色？

使用 `groupShape.FillColor`。这会填充不可见的边界框，适用于高亮显示。

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### 这在旧的 Word 格式（.doc）下能用吗？

`Aspose.Words` 也可以保存为 `.doc`——只需在 `Save` 时更改文件扩展名。不过，某些高级形状功能（如分组）只能在 OOXML `.docx` 格式中得到完整支持。

---

## 完整可运行示例

将下面的代码块复制粘贴到新的控制台应用程序中，即可看到完整流程的实际效果。内容完整，无缺失，是 **完整可运行的示例**。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**预期输出：** 打开 `GroupShape.docx`，你会看到一个由淡蓝色矩形和淡珊瑚色椭圆组成的单一分组对象，完美并排对齐。

---

## 小结

我们已经覆盖了使用 Aspose.Words **在 Word 中对形状进行分组** 所需的全部步骤：

1. 创建文档和 Builder。  
2. **添加矩形形状** 并 **定义椭圆形状**，并设定明确的尺寸。  
3. （可选）**将形状插入 Word** 进行快速预览。  
4. 使用 `GroupShape` 实现 **如何分组形状**——追加每个子形状、设置环绕方式并插入。  
5. 保存文件并验证结果。

## 接下来你可以学习什么？

以下教程与本指南紧密相关，帮助你进一步掌握 API 功能并在项目中探索其他实现方式。每篇资源都包含完整的可运行代码示例和逐步解释。

- [使用 Aspose.Words for .NET 在 Word 文档中插入形状](/words/english/net/working-with-shapes/insert-shape/)
- [使用 Aspose.Words 在 Word 中创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words 形状阴影教程 – 在 C# 中为 Word 形状添加阴影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}