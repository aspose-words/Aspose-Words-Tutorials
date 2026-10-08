---
category: general
date: 2026-03-01
description: 使用 Aspose.Words 创建 Word 文档，并学习如何添加矩形形状、如何添加阴影、如何设置透明度以及如何创建形状——全部使用 C#。
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: zh
og_description: 使用 C# 的 Aspose.Words 创建 Word 文档。学习如何添加矩形形状、应用外部阴影以及在几个步骤内设置透明度。
og_title: 创建带矩形形状和阴影的Word文档 – 指南
tags:
- Aspose.Words
- C#
- Document Generation
title: 创建带矩形形状和阴影的 Word 文档 – 步骤指南
url: /zh/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用矩形形状和阴影创建 Word 文档 – 步骤指南

是否曾需要 **create word document**（创建 Word 文档），其中包含自定义样式的矩形？也许您正在构建报告模板，并希望使用细腻的投影阴影来提升布局效果。您并非唯一有此需求的开发者——大家经常问：“如何以编程方式添加矩形形状和阴影？”好消息是，使用 Aspose.Words 您只需几行代码即可实现。

在本教程中，我们将完整演示整个过程：从创建空白 Word 文件、添加矩形形状，到配置带透明度的外部阴影。完成后，您将拥有一个可直接使用的 `Shadow.docx`，打开 Word 即可立即看到效果。无需外部工具，也不需要繁琐的 XML——仅使用简洁的 C# 代码和清晰的说明。

## 您将学到的内容

- **How to create shape** 使用 Aspose.Words 在 Word 文档中创建 shape 对象。
- **How to add rectangle shape** 将矩形形状添加到段落中而不影响现有内容。
- **How to add shadow**（外部阴影）并控制其颜色、偏移、模糊程度和透明度。
- **How to set transparency** 为阴影设置透明度，使其看起来更专业。
- 在实际项目中可能需要的技巧、常见陷阱和变体。

### 前置条件

- .NET 6.0 或更高版本（该 API 也兼容 .NET Framework 4.6+）。
- 通过 NuGet 安装 Aspose.Words for .NET（`Install-Package Aspose.Words`）。
- 对 C# 语法有基本了解——无需高级技巧，只需常规的 `using` 语句和对象创建。

> **Pro tip:** 如果您使用 Visual Studio，请启用“可空引用类型”，以便及早捕获潜在的空引用错误。

## 步骤 1 – 创建空白 Word 文档

要 **create word document**，我们从 `Document` 类开始。可以将其视为空白画布，随后可以添加章节、段落、表格或形状。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

为什么需要一个全新的 `Document` 实例？因为每个形状、段落或样式都存在于文档对象模型（DOM）中。从空白文档开始可以确保您添加的矩形不会与现有内容冲突。

## 步骤 2 – 定义矩形形状

现在我们 **how to create shape** 一个矩形。`Shape` 构造函数接受所属文档和形状类型。我们还以点为单位设置宽度和高度（1 pt ≈ 1/72 英寸）。

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

您可能会想，“能否使用厘米而不是点？”API 只接受点，但可以进行转换：`points = centimeters * 28.35`。在将形状对齐到页面边距时，这个小转换非常实用。

## 步骤 3 – 添加外部阴影并设置透明度

这里就是魔法发生的地方：**how to add shadow** 以及 **how to set transparency** 于该阴影。`ShadowFormat` 属性让您拥有完整的控制权。

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**为什么使用这些设置？**  
- **Transparency** 让底层页面纹理透出，防止阴影显得过于沉重。  
- **OffsetX/Y** 产生形状悬浮于页面的错觉。  
- **BlurRadius** 软化边缘——若没有此设置，阴影将呈现硬直的矩形，显得不自然。  

如果需要更戏剧化的效果，可将 `OffsetX/Y` 调整为 10，并将 `BlurRadius` 增加到 8。相反，若想要细腻的提示，则保持它们分别为 2 和 2。

## 步骤 4 – 将形状插入文档

现在我们 **add rectangle shape** 到文档的第一个段落。如果文档没有内容，`FirstParagraph` 会自动为您创建。

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

如果想将形状放在特定的表格单元格或后面的段落中怎么办？只需定位该节点（`doc.GetChild(NodeType.Paragraph, index, true)`），然后对其调用 `AppendChild`。如果需要多个副本，可以克隆同一个 shape 对象。

## 步骤 5 – 保存文档

最后，我们 **create word document** 到磁盘。使用适合您环境的路径；示例中使用了占位符。

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

当您在 Microsoft Word 中打开 `Shadow.docx` 时，会看到一个浅灰色矩形，带有向右下偏移的柔和外部阴影。阴影的 30 % 透明度确保它不会主导页面。

---

![创建带阴影矩形形状的 Word 文档](image.png "创建带阴影矩形形状的 Word 文档")

*图片替代文字：创建带阴影矩形形状的 Word 文档*

## 完整、可直接运行的代码

下面是完整的程序，您可以复制粘贴到控制台应用中。没有缺失的部分，也没有“请参阅文档获取更多信息”。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### 预期结果

- 在目标文件夹中出现名为 **Shadow.docx** 的文件。
- 在 Word 中打开它时，会显示一个尺寸为 200 × 100 pt、带深灰色外部阴影的矩形。
- 阴影水平和垂直偏移 5 pt，具有模糊效果，且透明度为 30 %。

## 常见问题与边缘情况

| Question | Answer |
|----------|--------|
| **我可以更改阴影颜色以匹配我的品牌吗？** | 当然——只需将 `System.Drawing.Color.DarkGray` 替换为您喜欢的任意 `Color`，例如用于蓝色强调的 `Color.FromArgb(255, 0, 120, 215)`。 |
| **如果需要内部阴影而不是外部阴影怎么办？** | 将 `ShadowFormat.Style = ShadowStyle.InnerShadow`。其余属性保持相同。 |
| **旧版 Word 是否支持透明度？** | 是的。Aspose.Words 会写入 Word 2007 及以上版本能够理解的相应 XML。旧版本可能会忽略透明度值，但仍会显示阴影。 |
| **我可以添加多个具有不同阴影的形状吗？** | 可以——只需创建新的 `Shape` 实例，分别配置每个阴影，然后将它们追加到目标节点。 |
| **数百个形状的性能如何？** | 创建大量形状会增加内存使用。复用单个 `Document` 实例并在循环中添加形状；如果出现压力，可释放临时对象。 |

## 实际项目的技巧

- **批量生成：** 为大量用户生成报告时，实例化单个 `Document` 模板并在每次迭代时克隆它。在追加形状之前替换占位符。
- **动态尺寸：** 使用页面尺寸（`document.FirstSection.PageSetup.PageWidth`）来计算相对于页面的形状大小，确保在不同纸张尺寸下布局一致。
- **测试：** 在更改阴影参数后，始终在 Word 中打开生成的 `.docx`。视觉反馈比猜测数值更快捷。

## 后续步骤

既然您已经了解 **how to add rectangle shape**、**how to add shadow** 和 **how to set transparency**，可以进一步探索：

- 向形状添加 **gradient fills**（渐变填充）（`Shape.FillFormat`）。
- 在形状内部嵌入 **pictures**（图片）以实现水印效果。
- 使用 **tables**（表格）在网格中对齐多个带阴影的形状。
- 将同一文档导出为 PDF（`document.Save("output.pdf")`），同时保留阴影。

这些都基于相同的核心概念，您会对扩展代码感到得心应手。

---

### 回顾

我们首先使用 Aspose.Words **create word document**，随后 **how to create shape** 一个矩形，应用 **how to add shadow**，微调 **how to set transparency**，并保存结果。整个过程形成了一个紧凑且可复用的模式，您可以将其适配到任何自动化场景中。

随意尝试——更改颜色、调整偏移，或堆叠多个形状。当遇到问题时，回顾上述章节；它们旨在提供快速参考。祝编码愉快，愿您的文档始终保持精致！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}