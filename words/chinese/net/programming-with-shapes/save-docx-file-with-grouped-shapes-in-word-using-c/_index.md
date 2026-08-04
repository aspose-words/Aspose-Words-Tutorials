---
category: general
date: 2026-08-04
description: 在 Word 中以编程方式保存 docx 文件，同时添加矩形形状和组合形状。学习如何设置形状尺寸并以编程方式创建文本框。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: zh
lastmod: 2026-08-04
og_description: 使用 C# 保存 docx 文件，通过添加矩形形状、在 Word 中对形状进行分组、设置形状尺寸以及以编程方式创建文本框。
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: 在 Word 中保存包含组合形状的 docx 文件 – C# 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 C# 在 Word 中保存包含分组形状的 docx 文件
url: /zh/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 C# 保存带有分组形状的 docx 文件

如果您需要 **save docx file** 包含多个一起排列的形状，本指南将向您展示如何使用 C# 实现。您将学习如何 **add rectangle shape**、在 Word 文档中分组多个形状、**set shape dimensions**，以及 **create textbox programmatically**。该解决方案适用于最新的 Aspose.Words for .NET，并在 .NET 6 或更高版本上运行。

本教程逐步演示了从项目设置到最终 `doc.Save` 调用的每一步。完成后，您将拥有一个可复用的代码片段，可粘贴到任何控制台或 ASP.NET 项目中。无需外部脚本或手动编辑 DOCX 文件。

## 前置条件

* .NET 6 SDK（或更高版本）已安装。  
* 有效的 **Aspose.Words for .NET** 许可证（免费试用可用于测试）。  
* Visual Studio 2022、VS Code，或任何能够构建 .NET 项目的 IDE。

代码仅使用 Aspose.Words 命名空间，因此不需要额外的 NuGet 包。

## 在 Word 中保存带有分组形状的 docx 文件

解决方案的核心是构建一个包含矩形和文本框的 `GroupShape`，然后将该组插入文档并调用 `doc.Save`。以下各节将把过程拆分为易于管理的部分。

### 1. 创建新文档和构建器

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*此步骤重要原因* – 一个全新的 `Document` 对象代表一个空的 *.docx* 文件。`DocumentBuilder` 提供诸如 `InsertNode` 的高级方法，我们将使用它来放置分组形状。

### 2. 向组中添加矩形形状

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*此步骤重要原因* – **add rectangle shape** 操作演示了如何使用精确的大小和位置定义可视元素。矩形位于 `group` 内部，因此后续移动组时矩形会自动随之移动。

### 3. 在 Word 文档中分组形状

`GroupShape` 类聚合多个绘图对象。当您希望将多个对象视为单个单元（例如一起移动、旋转或复制）时，分组非常有用。

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*为何进行分组* – 分组降低了布局复杂度。您只需一次性调整组的 `Left`、`Top`、`Width` 和 `Height`，而无需单独定位每个形状。

### 4. 为精确布局设置形状尺寸

组本身及其子形状都需要明确的尺寸；否则 Word 会使用默认大小，可能与您的设计不符。

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*为何设置尺寸* – 精确的测量可确保矩形和文本框不会意外重叠，并且最终的 **save docx file** 符合预期布局。

### 5. 在组内以编程方式创建文本框

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*此步骤重要原因* – **create textbox programmatically** 部分展示了如何在形状内部嵌入富文本。使用 `Paragraph` 和 `Run` 可让您在后续对格式进行完全控制。

### 6. 插入分组形状并 **save docx file**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*此最终步骤重要原因* – `InsertNode` 调用将分组形状准确放置在构建器光标所在位置。`doc.Save` 方法执行 **save docx file** 操作，将完整的 Word 文档写入磁盘。

> **结果：** 在 Microsoft Word 中打开 *GroupShape.docx* 时，会显示左侧的矩形和右侧的文本框，它们被锁定在同一个组内。您可以将整个组作为一个单元移动、调整大小或应用其他格式设置。

## 完整、可运行的示例

将下面的代码复制到新的控制台项目（`dotnet new console`）中并运行 `dotnet run`。程序将在项目的输出文件夹中创建 `GroupShape.docx`。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### 预期输出

* 输出目录中出现一个名为 **GroupShape.docx** 的文件。  
* 打开文件后，左侧显示矩形形状，右侧显示包含 “Grouped text” 的文本框，两者被锁定在一起。  
* 选择任意形状都会移动整个组，确认 **group shapes word** 功能如预期工作。

## 常见变体和边缘情况

| Situation | Recommendation |
|-----------|----------------|
| Need more than two shapes | 在调用 `builder.InsertNode` 之前，向 `group` 添加额外的 `Shape` 对象。 |
| Want the group to appear on a specific page | 使用 `builder.MoveToDocumentEnd()` 或 `builder.MoveToPage(pageNumber)` 移动构建器光标。 |
| Require different units (e.g., centimeters) | 使用 `ConvertUtil.InchToPoint(1.0)` 将英寸转换为点（Word 所需的单位）。 |
| Want the textbox to wrap text | 创建文本框后，设置 `textBox.TextBoxWrap = TextBoxWrapType.Square`。 |
| Working with older .NET Framework versions | 相同的 API 在 .NET Framework 4.7+ 上可用，但请确保引用正确的 Aspose.Words 版本。 |

**技巧提示：** 始终在添加所有子形状 *之后* 设置组的 `Width` 和 `Height`。这可确保组完整包围其内容，防止文档在 Word 中打开时被裁剪。

## 结论

现在您已经了解如何使用 Aspose.Words for .NET **save docx file**，同时 **add rectangle shape**、**group shapes word**、**set shape dimensions** 和 **create textbox programmatically**。完整示例展示了一种简洁、可重复的模式，您可以将其应用于更复杂的布局，例如图表、图像，

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题，构建在本指南演示的技巧之上。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [使用 C# 在 Word 中创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words 形状阴影教程 – 在 C# 中为 Word 形状添加阴影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}