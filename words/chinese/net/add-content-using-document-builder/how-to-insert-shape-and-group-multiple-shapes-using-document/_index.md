---
category: general
date: 2026-11-15
description: 学习如何使用 Aspose.Words DocumentBuilder 在 Word 文档中插入形状并对多个形状进行分组。包括插入矩形形状和插入多个形状的示例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: zh
lastmod: 2026-11-15
og_description: 如何使用 Aspose.Words 在 Word 文件中插入形状。本指南涵盖对多个形状进行分组、插入矩形形状以及高效添加多个形状。
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: 如何使用 DocumentBuilder 插入形状并对多个形状进行分组
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: 如何使用 C# 中的 DocumentBuilder 插入形状并对多个形状进行分组
url: /zh/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 DocumentBuilder 在 C# 中插入形状并对多个形状进行分组

如果您需要了解如何使用 Aspose.Words **插入形状** 到 Word 文档，本指南将为您展示具体步骤。您还将学习如何 **对多个形状进行分组** 使其表现为单一对象，以及如何 **插入矩形形状** 与其他图形一起使用。

文档自动化通常需要添加多种图形——图表、徽标、标注——并保持它们有序。完成本教程后，您将能够 **插入多个形状**、将它们放入一个组中，并保存整洁、可复用的布局。

## 前置条件

在开始之前，请确保您已具备：

* 已安装 .NET 6.0 或更高版本  
* Visual Studio 2022（或任何 C# IDE）  
* Aspose.Words for .NET 许可证或免费评估密钥  
* 对 C# 和 Aspose.Words `DocumentBuilder` 类有基本了解  

您 **不** 需要任何其他第三方库；所有必需的内容都已包含在 Aspose.Words 中。

## 步骤 1：通过 NuGet 安装 Aspose.Words

在 Visual Studio 中打开项目，并在 “Package Manager Console” 中运行以下命令：

```powershell
Install-Package Aspose.Words
```

该包包含本教程中使用的 `DocumentBuilder`、`Shape` 和 `GroupShape` 类。

## 步骤 2：创建 DocumentBuilder 实例 – **插入形状** 的基础

第一行可执行代码是创建一个 `DocumentBuilder`。该对象让您直接访问文档树，能够将形状精确放置在所需位置。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*为什么这很重要*：`DocumentBuilder` 维护一个光标（即“插入点”）。随后所有的 `Insert...` 调用都会使用该光标，这也是我们随后将光标移动到 `GroupShape` 中以保持所有形状在一起的原因。

## 步骤 3：**插入矩形形状** – 您将添加的第一个图形

矩形是表格、图像或标注的常见占位符。使用 `InsertShape` 并传入 `ShapeType.Rectangle`，同时以点为单位指定宽度和高度（1 pt ≈ 1/72 in）。

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

矩形会出现在当前光标位置。若有需要，您可以随后自定义其填充、线条样式或文本。

## 步骤 4：插入另一个形状 – 用于视觉变化的椭圆

添加多个形状演示了 **插入多个形状**。椭圆将在文档流中位于矩形之后。

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

此时文档中包含两个独立的形状。即使您移动光标或添加文本，这些形状仍会保持在插入时的位置。

## 步骤 5：**对多个形状进行分组** 使其作为单一单元

当需要一起移动、旋转或格式化多个图形时，分组是必不可少的。下面的代码创建一个 `GroupShape`，将 builder 的光标移动到该组内部，然后再次插入相同的形状——这一次它们成为组的子节点。

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### 为什么使用分组？

* **单点变换** – 只需一次调用即可旋转或调整整个组的大小。  
* **逻辑组织** – Word 文档树会反映分组结构，使后续编辑更简便。  
* **布局一致** – 移动组时，子形状之间的相对位置保持不变。

### 添加更多形状 – 在分组内扩展 **插入多个形状**

只要光标仍位于 `GroupShape` 内，您就可以继续调用 `InsertShape`。例如，添加一个三角形：

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

每一次调用都会遵循组上下文，因而三角形会自动成为同一分组集合的一部分。

## 步骤 6：保存文档并验证结果

所有形状放置完毕后，将文档持久化为 `.docx` 文件。使用 Microsoft Word（或任何兼容的查看器）打开该文件，应能看到两个独立的形状，随后是一个包含相同矩形、椭圆和三角形的分组块。

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### 预期输出

* **前两个形状** – 矩形和椭圆分别独立放置在页面上。  
* **分组块** – 矩形、椭圆和三角形在 Word 中点击任意一个时会一起移动。

您可以通过选中组内的任意形状来测试分组效果；Word 会高亮整个集合，证明 **对多个形状进行分组** 操作已成功。

## 常见陷阱与专业提示

| 问题 | 为什么会发生 | 解决方案 |
|------|--------------|----------|
| 形状出现在预期页面之外 | 在插入前未将 builder 的光标移动到 `GroupShape` 中 | 在任何属于该组的 `InsertShape` 调用 **之前** 始终调用 `builder.MoveTo(group)` |
| 保存后组消失 | 插入组时未将其添加到文档的节点集合中 | 创建 `GroupShape` 后立即使用 `builder.InsertNode(group)` |
| 由于文档 DPI 导致尺寸异常 | Aspose.Words 使用点作为单位，若按像素思考会产生尺寸不匹配 | 将像素转换为点 (`points = pixels * 72 / 96`) 或直接使用点 |
| 形状意外重叠 | 未设置显式定位，Word 会顺序放置 | 插入后设置 `Shape.Left` 和 `Shape.Top` 以控制精确位置 |

**专业提示**：分组后，您可以获取组的 `Shapes` 集合 (`group.Shapes`) 来遍历、重命名或批量应用格式。

## 步骤 7：扩展示例 – 接下来做什么？

现在您已经掌握了 **插入形状**、**插入矩形形状** 与 **对多个形状进行分组**，可以进一步探索：

* **动画分组形状** – 为组设置旋转或翻转属性。  
* **应用样式** – 使用 `Shape.FillColor`、`Shape.LineFormat` 或 `Shape.TextBox` 添加标签。  
* **导出为 PDF** – 调用 `doc.Save("output.pdf")` 时，同样的分组布局会正确渲染。  

所有这些扩展都复用相同的 `DocumentBuilder` 工作流，使代码保持简洁、易于维护。

## 结论

本教程演示了如何使用 Aspose.Words **插入形状** 到 Word 文档，如何 **插入矩形形状**，以及如何 **对多个形状进行分组** 使其表现为单一对象。通过遵循逐步代码，您可以可靠地 **插入多个形状**、将它们组织成组，并以编程方式生成专业级文档。

欢迎尝试不同的形状类型、颜色和组变换。当您准备好后，可将此模式集成到更大的报表或模板解决方案中，实现复杂文档布局的自动化。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。

- [使用 Aspose.Words for .NET 在 Word 文档中插入形状](/words/english/net/working-with-shapes/insert-shape/)
- [如何在 Word 文档中使用 Aspose.Words 创建并在组形状内插入椭圆和矩形形状](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [如何使用 Aspose.Words 在 Word 文档中对形状进行分组](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}