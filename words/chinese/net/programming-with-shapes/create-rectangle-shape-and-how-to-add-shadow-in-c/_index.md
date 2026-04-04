---
category: general
date: 2026-04-04
description: 使用 Aspose.Words 在 C# 中创建矩形形状，并学习如何添加阴影、对阴影应用模糊以及使阴影透明——一步步指南。
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: zh
og_description: 使用 Aspose.Words 在 C# 中创建矩形形状。学习如何添加阴影、对阴影应用模糊以及使阴影透明的简明教程。
og_title: 在 C# 中创建矩形形状并添加阴影
tags:
- Aspose.Words
- C#
- Document Automation
title: 在 C# 中创建矩形形状以及如何添加阴影
url: /zh/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建矩形形状并在 C# 中添加阴影

是否曾经需要在 Word 文档中 **创建矩形形状**，但不确定如何为其添加细腻的投影？你并不孤单。在许多报表或品牌化场景中，一个带有柔和半透明阴影的简单矩形可以让布局显得更精致，而不需要付出太多努力。

在本教程中，我们将演示 **如何使用 Aspose.Words 创建文档**，随后展示 **如何添加阴影**、**对阴影应用模糊**，甚至 **使阴影透明**。完成后，你将拥有一段可直接运行的 C# 代码片段，能够生成带有精美阴影矩形的 *.docx* 文件——只需几分钟。

## 所需环境

- .NET 6 或更高版本（该 API 也兼容 .NET Framework 4.6+）
- Aspose.Words for .NET（免费试用版即可运行本示例）
- 任意代码编辑器 – Visual Studio、VS Code、Rider，随你喜欢
- 基础 C# 知识 – 不需要高级技巧，只要能运行控制台应用即可

如果你已经准备好上述条件，我们即可直接进入实现步骤。

## 第 1 步 – 创建文档并初始化画布

首先，需要一个空的 `Document` 对象。可以把它想象成一张空白纸，随后 Aspose.Words 会将其转换为 Word 文件。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

为什么要实例化 `Document` 而不是加载模板？从零开始可以确保没有隐藏的样式或节干扰我们的矩形，同时也能保持文件体积极小——在循环生成大量文档时这是个好习惯。

## 第 2 步 – 创建矩形形状（核心关键字）

现在我们真正 **创建矩形形状**。`Shape` 类非常灵活；你只需指定类型（Rectangle）、尺寸以及与周围文本的环绕方式。

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

请注意使用对象初始化器语法——简洁且能降低后期忘记设置属性的风险。矩形将放置在第一段落中，后续步骤会将其加入文档。

## 第 3 步 – 添加阴影并自定义外观

添加阴影并非只需一行代码，你需要调节多个属性。这正是次要关键字 **apply blur to shadow** 和 **make shadow transparent** 发挥作用的地方。

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

关于数值的简要说明：`BlurRadius` 为 5 时产生柔和的羽化效果；若想更柔软可调至 10，若想边缘更锐利则调至 2。`Transparency` 的取值范围是 0（不透明）到 1（完全透明），可根据品牌对比度需求自行调整。

### 专业提示

如果需要彩色阴影（例如企业蓝），只需将 `Color.DarkGray` 替换为 `Color.FromArgb(80, 0, 120, 215)`。第一个参数是 alpha 通道——保持较低数值即可获得低调效果。

## 第 4 步 – 将形状插入文档

矩形及其阴影准备好后，我们将其放入文档的第一段落。此步骤确保形状出现在文件的最顶部。

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

为何选择第一段落？这是一个安全的默认位置，即使文档完全为空也能正常工作。如果你希望将形状插入特定位置（例如标题之后），只需定位相应节点并在其处插入形状即可。

## 第 5 步 – 保存文件并验证结果

最后，将文档持久化到磁盘。你可以自行决定保存路径，只需确保目标文件夹已存在。

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

打开 *ShadowRectangle.docx*（Microsoft Word）后，你应能看到一个 200 × 100 点的矩形，带有深灰色、略微模糊、透明度为 30 % 的阴影，阴影向右下偏移三个点。效果虽细微，却为原本平面的布局增添了层次感。

![在 Aspose.Words 中创建带阴影的矩形形状](https://example.com/placeholder-image.png "在 Aspose.Words 中创建带阴影的矩形形状")

*图片替代文字:* **在 Aspose.Words 中创建带阴影的矩形形状** – 图中展示了最终文档中带阴影的矩形。

## 常见变体与边缘情况

### 动态更改阴影颜色

如果你的应用支持主题，可从配置文件中读取阴影颜色：

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### 将形状设为非内联

有时希望矩形漂浮在文本之上。将 `WrapType` 改为 `WrapType.Square`，并将 `RelativeHorizontalPosition` 设置为 `RelativeHorizontalPosition.Margin`，即可获得更灵活的控制。

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### 处理多页文档

若需在每一页都放置矩形，可遍历 `doc.Sections`，并将克隆的形状追加到每个节的第一段落。记得使用 `rect.Clone(true)` 同时复制阴影设置。

## 小结 – 我们完成了什么

- 使用 Aspose.Words **创建矩形形状**
- **如何添加阴影**（颜色、偏移、模糊、透明度）
- 演示了 **apply blur to shadow** 与 **make shadow transparent**
- 保存了一个可直接打开的 Word 文件

仅凭几行代码即可实现这些视觉效果，证明了复杂的视觉微调并不一定需要重量级的图形库。

## 接下来可以做什么？

- 尝试其他 `ShapeType`（Ellipse、Cloud 等），观察阴影的表现差异。
- 将矩形与文本框组合，构建带标签的标注框。
- 深入了解 **如何创建文档** 模板，预置形状占位符，然后通过代码填充。

随意调整模糊半径、颜色或透明度，直到阴影与设计语言完美契合。API 容错度高，重新运行控制台应用即可即时看到效果。

祝编码愉快，愿你的文档始终拥有额外的层次感！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}