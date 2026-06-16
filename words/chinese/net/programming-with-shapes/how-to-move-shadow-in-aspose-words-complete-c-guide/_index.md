---
category: general
date: 2026-05-01
description: 如何使用 C# 在 Aspose.Words 中移动形状的阴影。学习在几分钟内为形状添加阴影、更改模糊度、设置透明度以及旋转阴影。
draft: false
keywords:
- how to move shadow
- add shadow to shape
- how to change blur
- how to set transparency
- how to rotate shadow
language: zh
og_description: 如何使用 C# 在 Aspose.Words 中移动形状的阴影。本教程展示了如何为形状添加阴影、更改模糊程度、设置透明度以及旋转阴影。
og_title: 如何在 Aspose.Words 中移动阴影 – 完整 C# 指南
tags:
- Aspose.Words
- C#
- Document Automation
title: 如何在 Aspose.Words 中移动阴影 – 完整 C# 指南
url: /zh/net/programming-with-shapes/how-to-move-shadow-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中移动阴影 – 完整 C# 指南

是否曾经想过 **如何移动阴影** 在 Word 文档中的形状上，而不需要手动打开 Word？在我的日常工作中，我经常需要以编程方式微调形状的阴影——无论是为了打造精致的报告还是动态模板。好消息是？使用 Aspose.Words 只需几行代码，你还将学习 **向形状添加阴影**、**如何更改模糊程度**、**如何设置透明度**以及**如何旋转阴影**，一次搞定。

在本教程中，我们将通过一个真实场景演示：加载已有的包含形状的 DOCX，调整阴影的位置、柔软度、不透明度和方向，最后保存结果。完成后，你将拥有一段可在任何 .NET 项目中直接使用的代码片段，并且了解每个属性背后的意义。

## 前置条件 – 开始之前你需要准备的东西

- **Aspose.Words for .NET**（版本 23.12 或更高）。可通过 NuGet 使用 `Install-Package Aspose.Words` 获取。
- .NET 6+ 开发环境（Visual Studio、VS Code、Rider——任选其一）。
- 一个输入的 Word 文件（`input.docx`），其中已包含至少一个形状（矩形、圆形或图片均可）。
- 对 C# 语法有基本了解——不需要高级技巧。

如果缺少上述任意项，请先暂停并安装相应库；后续示例默认已引用该包。

## 第一步：加载文档并获取目标形状 – **如何移动阴影** 从这里开始

首先我们加载源文档并定位要修改的形状。Aspose.Words 将每个对象（段落、表格、形状）视为树中的节点，因而可以直接查询。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 📂 Load the source DOCX that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // 🎯 Retrieve the first shape in the document.
        // The GetChild method walks the node tree; the third argument (true) means “search deep”.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // If no shape is found, bail out early.
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // -------------------------------------------------
        // The next sections show **how to move shadow**,
        // **add shadow to shape**, **how to change blur**,
        // **how to set transparency**, and **how to rotate shadow**.
        // -------------------------------------------------
```

> **为什么这很重要：** 只加载一次文档并复用同一个 `Document` 实例可以提升效率。`GetChild` 调用是安全的，因为若索引超出范围会返回 `null`，从而让我们能够优雅地处理缺失的形状。

## 第二步：调整模糊半径 – 掌握 **如何更改模糊程度**

柔和的阴影看起来更专业，而硬边的阴影则显得廉价。`BlurRadius` 属性以点（pt）为单位控制柔软度（1 pt ≈ 1/72 英寸）。我们把它提升到 8 pt。

```csharp
        // Increase the blur radius to soften the shadow edges.
        shape.ShadowFormat.BlurRadius = 8.0; // 8 points ≈ 0.11 inches
```

> **小技巧：** 默认模糊值为 0.5 pt。超过 5 pt 通常能明显感受到，但若设置过大，形状会显得与页面脱离。

## 第三步：设置透明度 – 解答 **如何设置透明度**

透明度决定阴影的透视程度。`0` 表示完全不透明，`1` 表示完全透明。为了获得细腻效果，我们使用 `0.3`（30 % 透明）。

```csharp
        // Make the shadow semi‑transparent so the shape remains visible through it.
        shape.ShadowFormat.Transparency = 0.3; // 30% transparent
```

> **你可能关心的原因：** 如果形状本身颜色较深，完全不透明的阴影会淹没底层文字。调低透明度既能保持可读性，又能增加层次感。

## 第四步：移动阴影 – **如何移动阴影** 的核心

`Distance` 属性定义阴影相对于形状的偏移距离，单位为点。距离越大，阴影越远，视觉冲击力越强。

```csharp
        // Move the shadow farther from the shape for a more pronounced effect.
        shape.ShadowFormat.Distance = 4.0; // 4 points ≈ 0.055 inches
```

> **如果只需要微小偏移怎么办？** 将 `Distance` 设为 `0`，阴影会直接贴在形状后面，适用于压纹效果。

## 第五步：旋转光源 – 解决 **如何旋转阴影**

阴影并非只能垂直向下，它会随光源角度变化。`Angle` 属性（单位为度）围绕形状旋转阴影。这里我们将其倾斜 45°。

```csharp
        // Rotate the light source to change the shadow direction.
        shape.ShadowFormat.Angle = 45; // 45 degrees clockwise from the vertical axis
```

> **快速实验：** 试试 `90` 会得到右侧阴影，`-30` 则产生左倾阴影。视觉变化立刻可见。

## 第六步：保存文档 – 查看 **向形状添加阴影** 的结果

完成阴影调整后，我们将文档写回磁盘。可以覆盖原文件，也可以生成新文件；示例使用新输出文件。

```csharp
        // Save the modified document with the adjusted shadow.
        doc.Save(@"YOUR_DIRECTORY\output.docx");

        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

> **预期输出：** 打开 `output.docx`，形状的阴影将更柔和、略微偏移、半透明且倾斜 45°。若将其与 `input.docx` 并排对比，差异一目了然。

### 完整可运行示例（复制粘贴即用）

下面是一整段程序代码。粘贴到新的控制台项目中，将 `YOUR_DIRECTORY` 替换为实际文件夹路径，然后运行。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Retrieve the first shape in the document (the one we will modify).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 1️⃣ Change blur – soften the edges.
        shape.ShadowFormat.BlurRadius = 8.0;

        // 2️⃣ Set transparency – make it 30% see‑through.
        shape.ShadowFormat.Transparency = 0.3;

        // 3️⃣ Move the shadow – increase distance from the shape.
        shape.ShadowFormat.Distance = 4.0;

        // 4️⃣ Rotate the shadow – change light direction.
        shape.ShadowFormat.Angle = 45;

        // Save the result.
        doc.Save(@"YOUR_DIRECTORY\output.docx");
        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

## 常见问题与边缘情况

### 文档中有多个形状怎么办？

可以遍历所有形状：

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    // Apply the same shadow settings or customize per shape.
}
```

### 能给当前没有阴影的形状添加阴影吗？

当然可以。`ShadowFormat` 对象始终存在，只需将其启用：

```csharp
shape.ShadowFormat.Enabled = true;
```

### 这对图片和 SmartArt 有效吗？

有效。任何继承自 `Shape` 的节点——包括图片、图表和 SmartArt——都暴露 `ShadowFormat`，属性使用方式相同。

### 如何控制阴影颜色？

使用 `Color` 属性：

```csharp
shape.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### 兼容性问题？

Aspose.Words 23.12+ 支持 .NET 6、.NET Core 3.1 和 .NET Framework 4.6.2+。本文展示的 API 在这些版本间保持稳定。

## 结论

我们已经完整演示了 **如何在形状上移动阴影**，并顺带展示了 **向形状添加阴影**、**如何更改模糊程度**、**如何设置透明度**以及**如何旋转阴影**。完整的可运行示例让你在几秒钟内即可微调任意形状的阴影，为文档增添专业感，而无需打开 Word。

准备好下一步了吗？尝试将这些阴影调整与 **条件格式** 结合——例如，仅对标题或超过特定尺寸的图表应用更深的阴影。亦或探索 **渐变填充** 为形状本身增色，打造真正抢眼的设计。

如果遇到任何问题，欢迎在下方留言。祝编码愉快，愿你的阴影总是恰到好处！

![Diagram showing the effect of moving a shadow on a shape – how to move shadow example](https://example.com/images/shadow-demo.png "how to move shadow example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}