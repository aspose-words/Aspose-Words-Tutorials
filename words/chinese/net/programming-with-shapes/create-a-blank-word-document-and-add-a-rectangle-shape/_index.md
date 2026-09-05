---
category: general
date: 2026-09-05
description: 学习如何使用 C# 中的 Aspose.Words 创建空白 Word 文档并添加可隐藏的矩形形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: zh
lastmod: 2026-09-05
og_description: 使用 Aspose.Words 创建空白 Word 文档并插入隐藏矩形形状 – C# 开发者的逐步指南。
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: 创建一个带有隐藏矩形形状的空白Word文档
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: 创建空白Word文档并添加矩形形状
url: /zh/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建空白 Word 文档并添加矩形形状

如果您需要 **blank word document** 创建且其中包含一个不希望出现在布局中的形状，本指南将向您展示如何使用 Aspose.Words for .NET 完成此操作。您将看到一个完整、可运行的示例：创建新文档、添加矩形形状、隐藏该形状并保存文件——无需额外工具。

本教程涵盖从项目设置到常见陷阱的排查。完成后，您将能够生成一个对读者看起来空白的 Word 文件，但仍携带隐藏的元数据，这在水印、自定义 XML 存储或布局锚点等场景中非常有用。

## 前置条件

开始之前，请确保您拥有：

* .NET 6.0 SDK 或更高版本（代码同样适用于 .NET Framework 4.7+）
* Visual Studio 2022（或任何支持 C# 的 IDE）
* 有效的 **Aspose.Words** NuGet 许可证（免费试用版可用于测试）
* 对 C# 和文档节点概念的基本了解

您可以使用以下 CLI 命令安装库：

```bash
dotnet add package Aspose.Words
```

> **专业提示：** 请保持 Aspose.Words 版本为最新；本教程使用的 API 在 23.10 版及以后是稳定的。

## 如何使用 Aspose.Words 创建空白 Word 文档

第一步是实例化一个 `Document` 对象。全新的 `Document` 代表一个空的 **blank word document**——没有段落、没有节，仅是文件容器。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **原因说明：** 从空白文档开始可确保后续添加的隐藏形状不会与已有内容或样式产生冲突。

## 向文档添加矩形形状

接下来我们创建一个矩形形状。在 Aspose.Words 中，形状是可以放置在文档树任意位置的节点，并且可以配置大小、填充、线条样式和可见性。

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

上面的代码创建了一个可见的矩形。此时您可以使用 `builder.InsertNode(rectangle)` 将其插入文档。然而，因为我们希望形状保持隐藏，在插入之前需要调整其 `Hidden` 属性。

## 如何在 Word 文档中隐藏形状

Word 为形状节点提供了 `Hidden` 属性。当其设置为 `true` 时，形状不会出现在页面布局中，但仍然是文档 XML 的一部分。这正是 **how to hide shape** 要求的核心。

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **解释：** 将 `Hidden = true` 添加到形状的 XML 中会产生 `<w:hide>` 属性。Word 处理器在渲染时会忽略该形状，但仍可通过编程方式或 Word 的 XML 视图访问它。

## 将隐藏形状插入空白文档

现在我们将隐藏的矩形放入文档树。由于文档仍然为空，形状将成为主故事中的第一个节点。

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

如果在 Microsoft Word 中打开生成的文件，您会看到一个看似空白的页面。形状实际上已经存在，只是不可见。

## 保存文档

最后，将文档写入磁盘。您可以选择任何受支持的格式（`.docx`、`.pdf`、`.odt` 等）。本教程使用现代的 DOCX 格式。

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### 预期结果

在 Word 中打开 `HiddenRectangle.docx`：

* 文档显示为空白（没有可见的形状或文本）。
* 若使用 **Open XML SDK** 或 **Word XML Viewer** 等工具检查文件，您会看到包含 `hidden` 属性的 `<w:pict>` 元素，其中包含矩形。

![blank word document with hidden rectangle shape](image.png){: .align-center alt="blank word document with hidden rectangle shape"}

## 完整、可运行的示例

下面是可以直接复制粘贴到控制台应用程序中的完整程序。它包含所有必要的 `using` 指令、错误处理和注释。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

运行程序（`dotnet run`）并验证输出文件。控制台会确认保存位置。

## 常见问题与边缘情况

### 能一次隐藏多个形状吗？

可以。为每个形状设置 `Hidden = true`，然后依次插入。隐藏标志是针对每个节点的，因此在同一文档中混合隐藏和可见形状是受支持的。

### 如果只想在打印视图中隐藏形状怎么办？

Word 通过 `DisplayWhen` 属性区分 **display**（显示）和 **print**（打印）可见性。Aspose.Words 未直接提供该标志的 API，但您可以修改底层 XML：

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

仅在需要仅在打印时隐藏时使用此方法。

### 隐藏形状会影响文件大小吗？

隐藏形状会添加与可见形状相同的 XML 负载，因此文件大小增加是相同的。不过，由于形状…

## 接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您在项目中进一步掌握 API 功能并探索替代实现方式。

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}