---
category: general
date: 2026-09-27
description: 使用 Aspose.Words 在 C# 中以编程方式创建包含组形状的 Word 文档。请按照本分步指南生成文件并学习实用技巧。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: zh
lastmod: 2026-09-27
og_description: 使用 Aspose.Words 以编程方式创建包含组形状的 Word 文档。本教程将带您逐步了解完整的 C# 代码，解释每一步，并展示最终输出。
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: 使用 C# 编程创建包含组合形状的 Word 文档 – 指南
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 使用编程方式创建包含组合形状的 Word 文档
url: /zh/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 以编程方式创建包含组形状的 Word 文档

如果您需要**以编程方式创建包含分组绘图的 Word 文档**，本指南将向您展示如何使用 Aspose.Words for .NET 完成此操作。无论您是在构建合同生成器、报告生成器，还是表单填充工具，您都将学习完整的 C# 代码、每个 API 调用的意义以及如何处理常见的边缘情况。

在 Word 中创建分组形状可能会感觉棘手，因为 Word 对象模型将组形状视为其他绘图对象的容器。本教程不仅解答了**如何在 Word 文档中创建组形状**的问题，还演示了如何在组内嵌入纯文本 StructuredDocumentTag（SDT），使形状能够容纳可编辑内容。

## 您将完成的工作

- 使用 `Document` 和 `DocumentBuilder` 初始化一个新的空白 Word 文档。
- 在当前光标位置插入一个 `GroupShape`。
- 向组形状中添加一个纯文本 `StructuredDocumentTag`（SDT）。
- 将文件保存为可在 Microsoft Word 中打开的 `.docx`。
- 了解 `GroupShape` 和 `StructuredDocumentTag` 的关键属性，以便将来扩展使用。

### 前置条件

- .NET 6.0 或更高（代码同样适用于 .NET Framework 4.7+）。
- Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）。
- C# IDE，例如 Visual Studio 2022 或带有 C# 扩展的 VS Code。

---

## 以编程方式创建 Word 文档 – 项目设置

1. **创建一个新的控制台项目**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **在 IDE 中打开项目**，并将 `Program.cs` 的内容替换为下一节中展示的代码。

> **小贴士：** 保持项目文件夹整洁；除非您提供绝对路径，否则 Aspose.Words 会将输出文件写入工作目录。

## 步骤 1：初始化文档和构建器

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**为什么这很重要：**  
`Document` 表示整个 Word 文件，而 `DocumentBuilder` 允许您在不手动遍历节点树的情况下定位新元素。提前设置页面尺寸可确保组形状不会超出页面。

## 步骤 2：在当前光标位置插入 GroupShape

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**解释：**  
`GroupShape` 是一种绘图对象，可容纳其他形状、图片或文本框。通过设置 `Width`、`Height`、`Left` 和 `Top`，您可以精确控制其在页面上的位置。`InsertNode` 方法将形状放置在主文档流中，表现为浮动对象。

## 步骤 3：在组内添加纯文本 StructuredDocumentTag（SDT）

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**为什么使用 SDT？**  
StructuredDocumentTag 是 Word 的原生内容控件。它们允许用户在已保存的文档中直接编辑文本，并且以后可以通过编程方式访问以进行数据提取。将 SDT 放置在组形状内部，可实现视觉分组与可编辑内容的结合。

## 步骤 4：保存文档

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**结果：**  
在 Microsoft Word 中打开 `GroupShapeDemo.docx` 时，会看到一个包含文本占位符“Enter text here”的浮动矩形（组形状）。用户可以直接点击形状内部并输入文字。

### 预期输出截图（概念示意）

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

外部框为 `GroupShape`；内部灰色区域为 `StructuredDocumentTag`。

## 如何创建 group shape word – 其他注意事项

### 添加更多子形状

您可以通过追加其他绘图对象（如图片或文本框）来丰富组形状：

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### 控制环绕样式

如果需要组形状位于文本后方或实现紧密环绕，请设置 `WrapType` 属性：

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### 边缘情况：空组形状

`GroupShape` 若没有子对象，将渲染为不可见的占位符。请始终确保至少添加一个子对象（例如 SDT 或图片），否则 Word 在保存时可能会丢弃该组。

### 兼容性说明

Aspose.Words 23.10 及以上版本完全支持 `GroupShape` 和 `StructuredDocumentTag`。如果使用较旧版本，`AppendChild` 方法的行为可能不同，保存后可能需要调用 `UpdatePageLayout`。

## 完整可运行示例

将下面的完整代码片段复制到 `Program.cs` 中并运行项目。该代码将上述所有步骤整合在一个独立的程序中。



## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题，帮助您进一步学习。每个资源都提供完整的可运行代码示例和一步步的解释，帮助您掌握更多 API 功能并在自己的项目中探索替代实现方案。

- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 C# 在 Word 中创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [使用 Aspose.Words 创建空白 Word 文档 – 步骤指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}