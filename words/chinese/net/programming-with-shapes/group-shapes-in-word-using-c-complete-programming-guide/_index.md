---
category: general
date: 2026-10-13
description: 使用 C# 在 Word 中对形状进行分组——学习如何对形状进行分组并使用 Aspose.Words 将形状添加到组中，只需几个简单步骤。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: zh
lastmod: 2026-10-13
og_description: 使用 C# 和 Aspose.Words 在 Word 中对形状进行分组。按照本指南学习如何对形状进行分组以及在 Word 文档中向组添加形状。
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: 使用 C# 在 Word 中对形状进行分组 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 C# 在 Word 中对形状进行分组 – 完整编程指南
url: /zh/net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 在 Word 中对形状进行分组 – 完整编程指南

如果您需要以编程方式**在 Word 中对形状进行分组**，本指南将精准演示如何操作。阅读前两句话后，您将了解所需代码、每一步背后的原理，以及如何**将形状添加到组**而不会出现意外。

我们将覆盖从加载 `.docx` 文件到保存更新后文档的全部过程。教程假设您具备基本的 C# 知识并已引用 Aspose.Words for .NET 库。无需查阅外部文档——只需复制、粘贴并运行即可。

## 前置条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.7+）
- Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）
- 一个已包含至少两个形状（如图片、AutoShape）的 Word 文档（`input.docx`）

> **专业提示：** 若进行测试，可在 Word UI 中创建一个包含两个矩形的简单 Word 文件，并将其保存为 `input.docx`，放置在您可控的文件夹中。

## 在 Word 中对形状进行分组 – 步骤指南

下面我们将过程拆分为五个逻辑步骤。每一步都包含完整的 C# 代码、该行代码的*原因*说明以及常见陷阱的简要提示。

### 步骤 1：加载 Word 文档

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**原因：** `Document` 是所有 Word 操作的入口。提供完整的文件路径即可将文档加载到内存，从而可以查询和修改其节点树。

**陷阱：** 使用相对路径时，如果工作目录不同可能会导致加载失败。请使用绝对路径或 `Path.Combine` 与 `AppContext.BaseDirectory` 组合路径。

### 步骤 2：获取要分组的形状

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**原因：** `GetChild` 会遍历文档树并返回请求类型的第 *n* 个节点。将 `isDeep` 设置为 `true` 可搜索整个文档，而不仅限于当前节。

**边界情况：** 如果文档中形状少于两个，`firstShape` 或 `secondShape` 将为 `null`，在强制转换时会抛出异常。请进行防护：

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### 步骤 3：创建新的 `GroupShape` 容器

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**原因：** `GroupShape` 充当父节点，可容纳多个 `Shape` 对象。它继承自 `Shape`，因此可以像普通形状一样插入到段落等位置。

### 步骤 4：将各个形状添加到组中

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**原因：** `AppendChild` 会将形状从原始位置移动到新建的组中。调用后，原始形状不再作为独立节点存在，而是成为 `groupShape` 的一部分。

**提示：** 分组会自动调整子形状的相对位置。如果需要特定布局，请在追加子节点之前设置 `GroupShape.Bounds` 属性。

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### 步骤 5：将组形状插入文档主体

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**原因：** `GroupShape` 必须放置在段落（或表格单元格）内部才能渲染。将其追加到第一段落可确保可见且不会破坏现有布局。

### 步骤 6：保存修改后的文档

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**原因：** `Save` 将内存中的更改写回 `.docx` 文件。您也可以通过更改重载方式保存到流或 PDF。

**结果验证：** 在 Microsoft Word 中打开 `output.docx`。您应看到原来的两个形状已合并为一个分组对象。选中该组时会显示标准的 Word 分组手柄。

## 编程方式分组形状的深入解析

- **节点所有权：** 调用 `AppendChild` 时，形状的 `ParentNode` 引用会自动更新。这可以防止出现“孤立”节点，从而避免文档损坏。
- **保持格式：** 分组**不会**丢失任何形状的格式（填充颜色、线条样式等）。所有子形状都会保留其原有属性。
- **嵌套分组：** `GroupShape` 可以包含其他 `GroupShape`，从而实现多层级层次结构。只需把内部组当作普通形状处理即可。

## 向组中添加形状并在以后管理它们

如果在创建初始组后需要添加更多形状，可以复用同一个 `GroupShape` 实例：

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

当需要取消分组时，遍历 `groupShape.GetChildNodes(NodeType.Shape, true)` 并将每个子节点重新插入到所需位置。

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**原因说明：** 某些工作流需要临时分组（例如对齐多个对象），随后再取消分组以进行单独编辑。

## 完整可运行示例

下面是一个自包含的程序，您可以直接编译运行。请将 `YOUR_DIRECTORY` 替换为本机实际的文件夹路径。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**预期输出：** 打开 `output.docx` 时，两个原始形状会显示为单个分组对象。选中该组会出现熟悉的 Word 分组手柄，您可以一起移动、缩放或旋转整套形状。

## 结论

现在，您已经掌握了使用 C# 和 Aspose.Words **在 Word 中对形状进行分组** 的方法，并了解了 **将形状添加到组** 以及随后如何操作或取消分组的完整步骤。此技术非常适合自动化报告布局、创建复合图表，或准备需要精确定位多个对象的 Word 模板。

接下来，您可以进一步探索以下主题，例如 **使用不同锚点类型对形状进行分组**、为分组对象应用 **高级格式化**，或将分组结果导出为 PDF。尝试嵌套分组，以编程方式构建更复杂的图形。

祝编码愉快！


## 接下来您应该学习什么？

以下教程涵盖了与本指南技术密切相关的主题，可帮助您在项目中进一步使用 API 功能并探索替代实现方式，每篇资源均提供完整可运行的代码示例和逐步解释。

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Shadow Effect to Word Shapes – Complete C# Guide](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}