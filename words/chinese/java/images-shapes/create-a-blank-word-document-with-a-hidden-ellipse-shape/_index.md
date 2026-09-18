---
category: general
date: 2026-09-18
description: 使用 Aspose.Words 创建一个空白 Word 文档并隐藏椭圆形状。学习如何在 Word 中隐藏形状、如何插入椭圆以及如何快速创建隐藏形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: zh
lastmod: 2026-09-18
og_description: 创建一个空白的 Word 文档并在 Word 中隐藏椭圆形状。本指南将一步步向您展示如何在 Word 中插入椭圆、隐藏形状，以及使用
  Aspose.Words 创建隐藏形状。
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: 创建一个带有隐藏椭圆形状的空白 Word 文档
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 创建一个带有隐藏椭圆形状的空白 Word 文档
url: /zh/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建一个带有隐藏椭圆形状的空白 Word 文档

如果您需要**创建一个空白 Word 文档**，其中包含一个您不希望出现在布局中的形状，本指南将准确展示如何操作。通过使用 Aspose.Words for .NET，您可以以编程方式插入椭圆形，然后隐藏该形状，使文档在视觉上保持空白，同时仍保留形状数据。

在本教程中，您将学习：

* 如何**创建空白 Word 文档**对象，
* 如何使用 `DocumentBuilder` **插入椭圆**，
* 如何在 Word 中 **隐藏形状**，使其不影响页面，
* 如何为后续处理 **创建隐藏形状** 对象。

这些步骤适用于 .NET 6+ 和最新的 Aspose.Words 版本（撰写时为 23.9）。无需额外的 Office 安装。

## 先决条件

* Visual Studio 2022（或任何 C# IDE）
* .NET 6 SDK 或更高版本
* Aspose.Words for .NET NuGet 包  
  ```bash
  dotnet add package Aspose.Words
  ```
* 基本的 C# 和 Word 文档概念知识

## 步骤 1：创建一个空白 Word 文档

您首先需要实例化一个 `Document` 对象。该对象代表一个空的 `.docx` 文件，是所有后续操作的基础。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

创建**空白 Word 文档**为您提供了一个干净的画布——没有段落，没有章节，只有底层的包结构。当您只需要一个隐藏形状且不需要其他内容时，这是理想的起点。

## 步骤 2：初始化 DocumentBuilder

`DocumentBuilder` 提供了一个便捷的 API，用于向 `Document` 添加内容。它的工作方式类似于在文档中移动的光标。

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

构建器会自动创建默认的第一个章节和段落，因此您可以直接插入形状，而无需手动添加章节。

## 步骤 3：插入椭圆形状

现在我们使用 `InsertShape` 方法 **插入椭圆**。该方法接受 `ShapeType` 枚举、宽度和高度（单位为点）。

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

为什么选择椭圆？椭圆是一种矢量形状，可以隐藏而不影响周围文本的流动。宽度 100 pt 和高度 50 pt 只是任意值；您可以根据后续处理需求进行调整。

## 步骤 4：隐藏形状，使其不出现在布局中

要在 Word 中 **隐藏形状**，请将 `Shape` 对象的 `Hidden` 属性设为 `true`。当文档在 Microsoft Word 中打开时，形状将不可见，并且不会占用布局空间。

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

`Hidden` 标志存储在形状的 XML 中（`<w:hidden/>`）。Word 在渲染时会尊重此属性，这就是即使形状存在，文档仍然看起来完全空白的原因。

### 专业提示

如果以后需要再次显示该形状，只需将 `ellipse.Hidden = false;` 并保存文档即可。

## 步骤 5：保存带有隐藏形状的文档

最后，将文档持久化到磁盘。该文件将是普通的 `.docx`，任何 Word 处理器都可以打开。

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

保存的文件 `HiddenEllipse.docx` 是一个包含隐藏椭圆的 **创建空白 Word 文档**。在 Microsoft Word 中打开时会显示空白页，但形状仍然存在于 Open XML 结构中。

## 完整工作示例

下面是完整的、独立的程序示例，您可以复制、粘贴并运行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**预期输出**

* 一个名为 `HiddenEllipse.docx` 的文件出现在 `C:\Temp` 中。
* 在 Microsoft Word 中打开该文件会显示完全空白的页面。
* 如果使用 Open XML SDK 或压缩文件查看器检查文档，您会在文档部件中找到带有 `<w:hidden/>` 的 `<w:shape>` 元素。

## 常见问题与边缘情况

### 如果形状仍然出现怎么办？

* 确保您使用的是 Aspose.Words 23.9 或更高版本——旧版本存在一个错误，导致某些形状类型的 `Hidden` 被忽略。
* 确认未对形状应用任何额外的格式（例如 `WrapType`），该格式会强制形状占用布局空间。

### 我可以隐藏其他形状类型吗？

可以。相同的 `Hidden` 属性同样适用于 `ShapeType.Rectangle`、`ShapeType.Picture` 等。只需将 `ShapeType.Ellipse` 替换为所需的类型即可。

### 如何在以后列出隐藏的形状？

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

此代码片段遍历所有形状并打印出隐藏的形状，对于以后需要处理或取消隐藏它们的 **创建隐藏形状** 工作流非常有用。

## 结论

现在您已经了解如何 **创建空白 Word 文档**、**插入椭圆**，以及 **在 Word 中隐藏形状**，从而生成一个对读者不可见的 **创建隐藏形状**。此技术对于在文档中存储元数据、书签或自定义 XML 而不改变其视觉外观非常实用。

### 下一步

* 探索基于文档内容有条件地 **隐藏形状**。
* 了解在生成文档最终版本时 **取消隐藏形状** 的方法。
* 将隐藏形状与 **自定义文档属性** 结合，以嵌入机器可读的数据。

欢迎尝试不同的形状类型、尺寸和隐藏状态逻辑，以适应您的自动化场景。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能，并在自己的项目中探索替代实现方法。

- [创建带阴影矩形形状的空白 Word 文档 – 步骤指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [在 Word 中使用 Aspose.Words 创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [使用 Aspose.Words for .NET 在 Word 文档中创建组合形状](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}