---
category: general
date: 2026-10-20
description: 学习如何创建空白 Word 文档、在 Word 中对形状进行分组、设置形状填充颜色，并使用完整的 C# 示例实现内联环绕类型。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: zh
lastmod: 2026-10-20
og_description: 使用 Aspose.Words 和 C# 创建空白 Word 文档，对 Word 中的形状进行分组，并将形状填充颜色设置为内联环绕类型。完整教程请参阅。
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: 创建空白 Word 文档并在 Word 中对形状进行分组——一步步指南
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 Aspose.Words 创建空白 Word 文档并对 Word 中的形状进行分组
url: /zh/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中创建空白文档并对形状进行分组

如果您需要 **创建一个空白的 Word 文档**，其中包含多个形状作为一个整体单元，本指南将手把手教您实现。您将看到如何 **在 Word 中对形状进行分组**、设置形状的填充颜色，以及应用 **wrap type inline**——全部通过一个简洁、可运行的 C# 程序完成。

本教程逐行讲解代码，说明每一步的意义，并指出常见的陷阱。完成后，您将得到一个 .docx 文件，其中矩形和文本框已分组在一起，随时可用于后续自动化。

## 您将学到

* 使用 Aspose.Words 初始化空的 Word 文件。
* 正确创建 **GroupShape** 并向其添加子形状的方法。
* **设置形状填充颜色** 的技巧以及位置控制。
* 使用 **wrap type inline** 使分组在段落中表现为单个内联对象。
* 如何保存并验证结果。

无需事先了解 Aspose.Words，但您应熟悉基本的 C# 语法，并已安装 Visual Studio（或其他 IDE）。

## 前置条件

| 要求 | 原因 |
|------|------|
| .NET 6.0 或更高版本 | 为 C# 项目提供运行时环境。 |
| Aspose.Words for .NET（最新版本） | 提供示例中使用的 `Document`、`DocumentBuilder` 和形状类。 |
| 可写入的文件夹路径 | `doc.Save` 调用需要有效的目录来写入输出文件。 |
| 基础 C# 知识 | 便于您阅读代码并根据自己的场景进行修改。 |

通过 NuGet 安装 Aspose.Words：

```bash
dotnet add package Aspose.Words
```

---

## 步骤 1：创建空白 Word 文档

首要操作是 **创建一个空白的 Word 文档**。Aspose.Words 的 `Document` 类表示内存中的 Word 文件，`DocumentBuilder` 提供了便捷的 API 用于编辑它。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*为什么重要*：从一个干净的文档开始，确保您添加的分组形状是唯一内容，便于后续验证。

## 步骤 2：定义具有 inline 包装类型的分组形状

**GroupShape** 充当其他形状的容器。将其 `WrapType` 设置为 `Inline` 可确保该分组在段落流中表现为单个内联对象。

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*为什么重要*：使用 **wrap type inline** 可防止分组漂浮到周围文本之外，这在您希望整个分组作为一个整体移动时至关重要。

## 步骤 3：添加矩形并设置形状填充颜色

矩形是常见的视觉元素。`Shape` 构造函数接受一个 `ShapeType`，随后我们指定尺寸和填充颜色。

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*为什么重要*：`FillColor` 属性展示了 **设置形状填充颜色** 的实际用法，为矩形赋予淡蓝色背景，使其在最终文档中更为突出。

## 步骤 4：添加文本框——如何有效地对形状进行分组

文本框为分组内提供可编辑的文字。通过调整 `Top` 属性，使其相对于分组坐标系定位。

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*为什么重要*：此步骤回答了 **如何对形状进行分组**——将每个子形状追加到同一个 `GroupShape` 实例中。`Top` 偏移确保文本框出现在矩形下方，展示了精确的布局控制。

## 步骤 5：将完整的分组形状插入文档

现在分组已包含两个子形状，将其插入到当前 builder 的位置。

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*为什么重要*：将分组作为单一节点插入，可确保 Word 将矩形和文本框视为一个逻辑对象，在编辑时保持相对位置不变。

## 步骤 6：保存文档并验证输出

最后，将文档写入磁盘。将 `YOUR_DIRECTORY` 替换为您机器上的实际路径。

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

打开 Microsoft Word 中的 `GroupShape.docx`，您应看到一个淡蓝色矩形，下方紧贴一个标有 “Grouped text” 的文本框。选中任意形状都会选中整个分组，证明 **在 Word 中对形状进行分组** 已成功实现。

### 预期结果

* 一个包含单段落的 .docx 文件。
* 在段落内部，一个看起来像单一复合对象的内联分组。
* 矩形填充淡蓝色，文本框显示 “Grouped text”。

![生成的 Word 文档截图](grouped_shapes.png){.center width=600 alt="使用 Aspose.Words 创建的空白 Word 文档，包含分组的矩形和文本框的截图"}

## 常见问题与边缘情况处理

### 如果需要分组漂浮而不是内联该怎么办？

将 `WrapType.Inline` 替换为 `WrapType.TopBottom`（或其他 `WrapType` 枚举值）。漂浮的分组可以独立于段落流定位，但会失去自动的内联对齐。

### 能否添加更多形状，如圆形或图片？

可以。使用 `ShapeType.Ellipse` 或 `ShapeType.Image` 创建额外的 `Shape` 对象，配置其属性后调用 `group.AppendChild(newShape)`。如果相应更新 `group.Bounds`，分组会自动扩展以容纳新的边界。

### 如何在添加子形状后更改分组的整体大小？

在所有子形状追加完毕后调整 `group.Bounds`，或通过代码计算子形状边界的并集。这样可确保分组的点击区域与可视内容匹配。

### 如果输出文件夹不存在会怎样？

Aspose.Words 会抛出 `DirectoryNotFoundException`。请先创建目录：

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### 这能在 .NET Framework 而非 .NET Core 上运行吗？

所有使用的 API（`Document`、`DocumentBuilder`、`GroupShape`、`Shape`）在 Aspose.Words 的 .NET Framework 版本中同样可用，代码无需修改即可运行。

## 专业技巧

* **性能技巧** – 在插入大量分组时复用同一个 `DocumentBuilder` 实例；为每个分组创建新 builder 会增加开销。
* **视觉一致性** – 将 `rectangle.StrokeColor` 设置为与 `FillColor` 相同，以获得无缝外观，或将 `rectangle.LineWidth = 0` 以隐藏边框。
* **调试** – 在保存前调用 `doc.UpdatePageLayout()`，如果您修改了大量形状，这会强制 Word 重新计算布局，防止意外裁剪。

## 结论

现在您已经掌握了如何 **创建空白 Word 文档**、**在 Word 中对形状进行分组**、**设置形状填充颜色**，以及使用 Aspose.Words for .NET 应用 **wrap type inline**。完整示例展示了在 Word 中构建行为如单一对象的复合图形的标准做法。

接下来您可以进一步探索：

* 添加图片或图表等额外形状。
* 尝试不同的 `WrapType` 值以实现漂浮分组。
* 在多个文档中批量生成分组图形，实现自动化。

欢迎将您的代码适配到自己的自动化场景，并在评论区分享您的成果！

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [How to Save PDF from Word with Inline Shapes – Complete Guide](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}