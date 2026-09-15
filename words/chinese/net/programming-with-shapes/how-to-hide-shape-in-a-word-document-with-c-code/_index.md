---
category: general
date: 2026-09-14
description: 学习如何使用 C# 在 Word 中隐藏形状——包括创建 Word 文档的代码、插入矩形形状以及以编程方式在 Word 中隐藏形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: zh
lastmod: 2026-09-14
og_description: 如何使用 C# 在 Word 中隐藏形状——一步步指南，还展示如何创建 Word 文档代码并插入矩形形状。
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: 如何使用 C# 代码在 Word 文档中隐藏形状
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 C# 代码在 Word 文档中隐藏形状
url: /zh/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 代码在 Word 文档中隐藏形状

如果您需要在 Word 文件中**隐藏形状**，本教程提供完整的解决方案。您将看到如何创建 Word 文档、插入矩形形状、添加椭圆形，并隐藏该椭圆，使打开文件时仅显示矩形。

本指南涵盖您所需的一切——无需外部引用，仅有代码和说明。完成后，您即可在任何通过程序生成的 Word 文档中嵌入隐藏的图形。

## 前置条件

- .NET 6.0 或更高（代码同样适用于 .NET Framework 4.7+）
- Aspose.Words for .NET（免费试用版或授权版）  
  通过 NuGet 安装：`dotnet add package Aspose.Words`
- 基本熟悉 C# 和 Visual Studio，或您喜欢的任何 IDE

## 步骤 1：设置项目并导入命名空间

启动一个新的控制台应用程序并添加所需的 `using` 语句。这些导入让您能够访问 `Document`、`DocumentBuilder` 和绘图类，以便操作形状。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Why this matters** – 导入正确的命名空间可防止编译错误，并使用于形状创建和可见性控制的 API 可用。

## 步骤 2：创建新的 Word 文档和构建器

`Document` 表示文件本身，而 `DocumentBuilder` 提供流式 API 用于添加内容。这是首次应用**隐藏形状**逻辑的地方：在任何形状存在之前，您需要先有文档上下文。

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Explanation** – `Document` 对象初始为空。`DocumentBuilder` 位于第一段的开头，准备插入形状或文本。

## 步骤 3：插入可见的矩形形状

矩形将是文档打开时仍然可见的形状。您可以直接通过形状对象控制其大小、位置和格式。

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Why this step** – 添加矩形演示了 **insert rectangle shape word** 的需求。设置 `FillColor` 和 `LineColor` 可让形状在最终文档中易于辨认。

## 步骤 4：插入椭圆形并隐藏它

现在添加您打算隐藏的形状。`Hidden` 属性告诉 Word 不在 UI 中渲染该形状，虽然它仍然是文档结构的一部分。

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Explanation** – 将 `Hidden = true` 设置为 **hide shape in word** 的核心。Word 在普通查看和打印时会遵守此标记，但如果需要，仍可通过代码访问该形状。

## 步骤 5：保存文档

最后，将文档写入磁盘。选择一个您有写入权限的文件夹，并为文件起一个能体现本教程目的的清晰名称。

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Result** – 在 Microsoft Word 中打开 `ShapeVisibility.docx` 时，只会看到浅蓝色的矩形。隐藏的椭圆不会出现，证明您已成功掌握在 Word 文件中**隐藏形状**的方法。

## 完整可运行示例

将所有代码片段组合在一起，即可得到一个完整的可运行程序：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 预期输出

- **Visual**：打开 `ShapeVisibility.docx` 时，您会看到位于左侧边距附近的浅蓝色矩形。没有椭圆可见。
- **Programmatic**：隐藏的椭圆仍然保留在文档的 XML（`<w:drawing>` 元素）中，并带有 `w:hidden` 属性，可通过将文件当作 zip 打开并检查 `document.xml` 来验证。

## 常见问题与边缘情况

| Question | Answer |
|----------|--------|
| *Can I hide multiple shapes?* | Yes. Set `Hidden = true` on each shape you want to conceal. |
| *Will hidden shapes print?* | By default Word does not print hidden objects. If you need them printed, clear the `Hidden` flag before printing. |
| *Is the hidden property supported in older Word versions?* | The `Hidden` attribute is part of the Office Open XML standard and works in Word 2007 and later. |
| *What if I need to toggle visibility at runtime?* | Retrieve the shape via `document.GetChildNodes(NodeType.Shape, true)` and flip the `Hidden` property based on your logic. |

## 专业技巧

- **Performance**: If you generate many documents, reuse a single `DocumentBuilder` instance instead of creating a new one for each file.
- **Version control**: Store the generated `.docx` files in a version‑controlled folder; hidden shapes can act as metadata markers for downstream processing.
- **Testing**: Automate a quick visual test by converting the DOCX to PDF with Aspose.Words (`document.Save("out.pdf")`). The PDF will also hide the ellipse, confirming that the hidden flag propagates through format conversions.

## 结论

您现在已经了解如何使用 C# 在 Word 文档中**隐藏形状**。本教程演示了创建文档、**insert rectangle shape word**、添加椭圆以及应用 `Hidden` 标记以实现 **hide shape in word** 的行为。借助完整的可运行代码，您可以将隐藏图形集成到任何自动化报告或模板工作流中。

### 下一步

- 探索其他形状属性，如旋转、阴影和文本环绕。  
- 将隐藏形状与自定义文档属性结合，以嵌入机器可读数据。  
- 研究 **create word document code** 模式，用于表格、图表和内容控件，扩展您的自动化工具箱。

欢迎尝试不同的形状类型和可见性设置——您的下一个 Word 自动化项目只需几行代码即可实现！

## 接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您在已有技巧的基础上进一步提升。每个资源都提供完整的可运行代码示例和逐步解释，助您掌握更多 API 功能并在项目中探索替代实现方案。

- [使用 C# 在 Word 中创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [创建带阴影矩形形状的空白 Word 文档 – 步骤指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words 形状阴影教程 – 在 C# 中为 Word 形状添加阴影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}