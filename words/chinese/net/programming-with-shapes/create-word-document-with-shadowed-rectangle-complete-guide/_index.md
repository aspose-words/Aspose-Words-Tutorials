---
category: general
date: 2026-04-21
description: 使用 C# 创建带有样式矩形和阴影的 Word 文档。学习如何添加阴影、插入矩形形状、设置阴影颜色等。
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: zh
og_description: 在 C# 中创建 Word 文档并添加带阴影的矩形形状。按照本指南轻松设置阴影颜色、模糊度和偏移量。
og_title: 创建带阴影矩形的Word文档 – 步骤指南
tags:
- Aspose.Words
- C#
- Document Automation
title: 创建带阴影矩形的 Word 文档 – 完整指南
url: /zh/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建带阴影矩形的 Word 文档 – 完整指南

是否曾需要 **创建 Word 文档**，让它看起来比普通的文字页面更精致？也许你在制作报告模板或宣传单，一条带有细腻阴影的矩形就能达到效果。在本教程中，我们将一步步演示——如何插入矩形形状、开启阴影，并自定义颜色、模糊程度和偏移量——全部使用 C# 和 Aspose.Words。

我们还会讲解 **如何添加阴影**，无论你面向的是 Word 2016、2019，还是最新的 Office 365 版本。完成后，你将得到一个可直接保存的 *.docx* 文件，展示出精美的阴影矩形，并了解每个属性背后的原理。

## 前置条件

- .NET 6（或任意近期的 .NET Framework 版本）  
- Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）  
- 基本的 C# 语法了解  
- Visual Studio 等 IDE（任何编辑器均可）

无需额外库，所有功能都在 Aspose.Words 中。

## 第一步 – 初始化文档和 Builder（创建 Word 文档）

要 **创建 Word 文档**，首先使用 `Document` 类。`DocumentBuilder` 就像你的画笔，能够添加文字、形状以及其他元素。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*为什么重要：* `Document` 对象代表整个 .docx 文件。没有它，就没有地方可以附加矩形或其阴影。

## 第二步 – 插入矩形形状（Insert Rectangle Shape）

现在我们真正 **插入矩形形状**。`InsertShape` 方法接受一个 `ShapeType` 枚举，以及宽度和高度（单位为点）。

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*小技巧：* 1 点 ≈ 1/72 英寸，所以 200 pts 大约是 2.78 英寸宽。根据你的布局自行调整这些数值。

## 第三步 – 启用阴影（How to Add Shadow）

默认情况下阴影是关闭的。将 `Visible` 标志设为 true 即可打开。

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*发生了什么？* 当 `Visible` 为 true 时，Word 会根据后续设置的属性渲染投影阴影。

## 第四步 – 自定义阴影外观（Set Shadow Color, Blur, Offsets）

这里我们 **设置阴影颜色**、模糊半径以及 X/Y 偏移量。可以随意尝试——不同的数值会产生柔和光晕、深度投影或“漂浮”效果。

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*为什么选这些数值？* 模糊 5 pts 可得到柔和的羽化边缘，偏移 4 pts 会让阴影向右下方移动，模拟光源来自左上。将 `Color` 改为 `Color.Black` 可获得更强对比，或使用 `Color.FromArgb(128, 0, 0, 0)` 实现半透明黑色。

### 边缘情况与变体

- **无模糊：** 将 `Blur = 0` 可得到锐利、硬边的阴影。  
- **负向偏移：** 使用 `OffsetX = -4` 可将阴影向左移动。  
- **不同形状：** 相同的阴影属性同样适用于圆形、三角形或自由绘制的形状——只需在第 2 步更改 `ShapeType`。  
- **兼容性：** Aspose.Words 将阴影数据写入 Office Open XML 格式，兼容 Word 2010‑2021 以及 Office 365。

## 第五步 – 保存文档（创建 Word 文档）

最后，将文件持久化到磁盘。你可以选择任意受支持的格式（`.docx`、`.pdf`、`.odt` 等），本指南使用经典的 Word 格式。

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

打开 **ShadowRectangle.docx** 时，你会看到一个带有细腻、模糊阴影的灰色矩形，阴影向右下偏移——正是我们脚本实现的效果。

### 预期输出

- 单页 *.docx* 文件。  
- 一个 200 pt × 100 pt 的矩形，位于调用 `InsertShape` 时光标所在的中心位置。  
- 一个灰色阴影，向右下各偏移 4 pts，模糊度为 5 pt。

如果形状出现偏移，可在插入前使用 `builder.MoveTo` 移动光标，或在插入后调整形状的 `Left` 与 `Top` 属性。

## 常见问题与故障排除

**Q: 阴影在 Word 中没有显示。**  
A: 确认 `ShadowFormat.Visible` 为 `true`。同时检查使用的 Aspose.Words 版本是否较新（阴影功能在 20.3 版加入）。

**Q: 能为阴影应用渐变吗？**  
A: `ShadowFormat` 本身不支持渐变。Word UI 支持渐变阴影，但 Open XML（Aspose.Words 所遵循的）仅暴露纯色阴影。若需渐变，需要手动编辑底层 XML，属于高级场景。

**Q: 如果想要只有阴影而没有填充的透明矩形怎么办？**  
A: 在插入后设置 `rectangle.FillColor = Color.Transparent;`。阴影仍会渲染，因为它独立于填充颜色。

## 生产代码的专业建议

- **复用 Builder：** 若要添加多个形状，保持同一个 `DocumentBuilder` 实例——为每个形状新建会带来不必要的开销。  
- **批量保存：** 所有修改完成后一次性保存；频繁 I/O 会拖慢大批量文档生成。  
- **错误处理：** 将整个代码块包裹在 `try / catch` 中，并记录 `Aspose.Words` 异常；异常信息通常会提供有用的行号，帮助定位模板损坏问题。

## 后续步骤（相关主题）

- **如何为图片或文本框添加阴影**（类似的 `ShadowFormat` 用法）。  
- **在表格单元格内插入矩形形状**，实现自定义单元格样式。  
- **使用 Word 原生 XML 创建矩形**（适合喜欢直接操作 Open XML 的开发者）。  
- **根据用户输入或主题颜色动态设置阴影颜色**。

尝试不同的颜色、模糊半径和偏移量——比如企业报告的柔和蓝光，或宣传单的深黑阴影。可能性无限，代码改动极少。

---

### 快速回顾

- 我们 **创建了一个 Word 文档**。  
- **插入了矩形形状** 并开启了阴影。  
- **设置了阴影颜色、模糊度和偏移**，实现专业外观。  
- 保存文件，准备分发。

现在，你已经拥有为任何 Word 自动化项目添加视觉亮点的坚实基础。还有其他想法吗？欢迎留言讨论。祝编码愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}