---
category: general
date: 2026-10-23
description: 创建一个空白的 Word 文档，添加一个矩形形状，并使用 Aspose.Words 在 Word 中隐藏该形状。面向 .NET 开发者的逐步代码示例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: zh
lastmod: 2026-10-23
og_description: 创建一个空白的 Word 文档，添加一个矩形形状，并使用 Aspose.Words 在 Word 中隐藏该形状。请参阅完整的 C#
  示例。
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: 创建一个空白的 Word 文档并添加隐藏的矩形形状
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: 创建空白 Word 文档并添加矩形形状
url: /zh/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建一个空白 Word 文档并添加矩形形状

如果您需要**创建一个空白 Word 文档**，本指南将向您展示如何使用 Aspose.Words for .NET 实现。您还将学习**如何插入形状**——具体来说是矩形——以及**隐藏形状文字**，使其不影响布局。

本教程会逐行讲解代码，说明每一步的重要性，并覆盖常见的陷阱，例如在不同的 Word 视图模式下隐藏形状的可见性。完成后，您将拥有一个完整的 `.docx` 文件，其中包含一个隐藏的矩形形状，您可以随后以编程方式显示或操作它。

## 前置条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.6+）
- Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）
- 开发环境，例如 Visual Studio 2022 或带有 C# 扩展的 VS Code
- 对 C# 语法和 Word 文档概念的基本了解

无需额外的 Office 安装，因为 Aspose.Words 完全在内存中工作。

## 创建一个空白 Word 文档

第一步是实例化一个空的 `Document` 对象。该对象代表一个尚未包含任何节、段落或内容的 Word 文件。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**为什么这很重要：**  
空的 `Document` 为您提供了一个干净的画布。如果从现有模板开始，隐藏的形状可能会继承不需要的样式。从头开始可以确保您稍后添加的矩形形状是唯一受您控制的内容。

## 向文档添加矩形形状

接下来，我们需要一个 `DocumentBuilder` 来向文档中放置内容。构建器的 `InsertShape` 方法是**插入形状**对象的标准方式，例如矩形、圆形或自定义绘图。

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**为什么这很重要：**  
`InsertShape` 返回一个 `Shape` 对象，您可以进一步配置（颜色、线型等）。尺寸使用点（1 point = 1/72 英寸）表示，这与 Word 的内部度量系统相匹配。

### 可选：为矩形设置样式（可选）

如果希望矩形在稍后取消隐藏时拥有可见的边框，可以设置其线宽和颜色：

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

这些代码是可选的，因为形状将在下一步被隐藏。

## 在 Word 中隐藏形状

Word 允许将形状从布局中隐藏，同时仍然是文档对象模型的一部分。将 `Hidden` 属性设为 `true` 可使形状在普通视图中不可见，但仍可通过 API 进行选择。

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**为什么这很重要：**  
隐藏的形状可用于存储元数据、后续处理的占位符，或仅在特定情况下（例如生成最终报告时）才显示的条件内容。形状仍然保留在文件中，您可以稍后通过 `rectangleShape.Hidden = false;` 以编程方式取消隐藏。

## 保存文档

最后，将文档写入磁盘。文件扩展名决定了 Word 的格式；`.docx` 是现代的 Open XML 格式。

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**结果：**  
在 Microsoft Word 中打开 `HiddenShape.docx` 会看到一个空白页面。矩形不可见，但如果进入 **Home → Select → Selection Pane**，您会看到该形状列出，并可以切换其可见性。

## 完整工作示例

下面是完整的程序代码，您可以复制、粘贴并运行。它包含所有必要的 `using` 语句和注释。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**预期输出：**  

- 控制台打印保存路径。  
- `HiddenShape.docx` 在 Word 中以空白页打开。  
- 矩形形状存在但被隐藏；您可以通过 *Selection Pane* 验证，或通过编程将 `Hidden = false` 并重新打开文件来查看。

## 常见问题与边缘情况

| Question | Answer |
|----------|--------|
| **Can I hide other shape types?** | Yes. Any `Shape` (e.g., `ShapeType.Ellipse`, `ShapeType.Picture`) supports the `Hidden` property. |
| **Will the hidden shape increase file size?** | The increase is negligible (a few kilobytes) because the shape data is stored as XML in the `.docx` package. |
| **What if I need the shape to appear only in print view?** | Use the `Shape.IsPrint` property instead of `Hidden`. Setting `IsPrint = false` hides the shape from printed output but keeps it visible on screen. |
| **How to unhide the shape later?** | Load the document, locate the shape (e.g., by `Shape.Name`), then set `shape.Hidden = false;` and save. |
| **Does this work with .doc (binary) format?** | Yes, Aspose.Words can save to `.doc` using `document.Save("file.doc");`. The hidden flag is preserved. |

## 专业技巧

- **为形状命名**：`rectangleShape.Name = "PlaceholderRectangle";` 可让您以后通过 `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")` 更容易找到它。  
- **批量处理**：如果需要向大量文档添加隐藏形状，可将代码封装在方法中并复用 `DocumentBuilder` 实例。  
- **性能**：创建形状开销很小，但频繁保存大型文档可能受 I/O 限制。考虑使用 `MemoryStream` 进行中间处理。

## 结论

您现在已经掌握了如何使用 Aspose.Words for .NET **创建一个空白 Word 文档**、**添加矩形形状**以及**隐藏形状文字**。此技术让您能够嵌入不可见的占位符，随后可以显示或操作它们，适用于动态报表生成、条件内容以及文档模板化等场景。

接下来您可以进一步探索：

- 使用 `ShapeType.Picture` 将矩形替换为图片或图表。  
- 在页眉/页脚中使用**how to insert shape**实现水印式占位符。  
- 将隐藏形状与基于**add rectangle shape**的数据验证相结合（例如在形状的 `AlternativeText` 属性中存储 JSON）。

祝编码愉快，欢迎尝试其他形状类型和可见性选项，以满足您的文档自动化需求！

## 接下来应该学习什么？

以下教程涵盖与本指南技术密切相关的主题，每个资源都提供完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [Create Word Document – How to Add Rectangle Shape and Shadow](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}