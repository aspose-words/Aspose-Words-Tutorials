---
category: general
date: 2026-03-22
description: 在 C# 中使用 Aspose.Words 创建矩形形状并为其添加阴影。了解如何添加阴影、如何创建矩形以及如何设置阴影属性。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: zh
og_description: 在 C# 中使用 Aspose.Words 创建矩形形状并为其添加阴影。一步一步的指南，涵盖如何添加阴影、如何创建矩形以及如何设置阴影。
og_title: 在 C# 中创建带阴影的矩形形状 – 完整指南
tags:
- Aspose.Words
- C#
- Document Automation
title: 使用 Aspose.Words 在 C# 中创建带阴影的矩形形状
url: /zh/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words 在 C# 中创建带阴影的矩形形状

是否曾需要在 Word 文档中 **创建矩形形状**，但不确定如何为其添加细腻的投影？你并不孤单——许多开发者在首次接触文档自动化时都会遇到这个难题。在本指南中，我们将逐步演示如何使用 Aspose.Words **为形状添加阴影**，并在过程中回答 “**如何添加阴影**”、 “**如何创建矩形**” 和 “**如何设置阴影**” 等问题。

我们将从一个空白的 `Document` 开始，绘制矩形，开启阴影效果，调整模糊度、距离、角度和颜色，最后保存文件。完成后，你将得到一个可直接使用的 `.docx`，其中显示一个灰色矩形漂浮在页面上方。没有神秘，只是可以直接复制粘贴到任何 .NET 项目中的简洁代码。

## 前置条件

在开始之前，请确保你拥有：

* **Aspose.Words for .NET**（截至 2026 年 3 月的最新版本）。可通过 NuGet 使用 `Install-Package Aspose.Words` 获取。
* .NET 开发环境——Visual Studio、Rider，或带有 C# 扩展的 VS Code 都可以。
* 基础的 C# 知识——不需要高级技巧，只要会创建控制台或 WinForms 应用即可。

就这些。无需额外库，也没有隐藏步骤。准备好了吗？让我们开始吧。

## 第一步：初始化一个新的空文档

要 **创建矩形形状**，首先需要一个容器——`Document` 对象，代表 Word 文件本身。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

`Document` 类是 Aspose.Words 所有功能的入口。把它想象成一块空白画布；没有它，你就无法添加任何形状、表格或文本。

## 第二步：创建将承载阴影的矩形

现在我们通过实例化 `Shape`（类型为 `Rectangle`）来 **如何创建矩形**。同时以点为单位设置其大小（1 点 ≈ 1/72 英寸）。

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

为什么选择 200 × 100 点？这对于演示来说尺寸恰当——足够大以清晰看到阴影，但又不会占满整页。你可以根据实际布局自由调整这些数值。

## 第三步：启用阴影效果并配置外观

本教程的核心：**如何添加阴影** 与 **如何设置阴影** 属性。Aspose.Words 在每个形状上都提供了 `Shadow` 对象，允许你打开效果并微调视觉参数。

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** 用于软化边缘——数值越高，阴影越扩散。
* **Distance** 控制阴影相对于矩形的偏移距离。
* **Angle** 决定光源方向；45° 会产生自然的对角线阴影。
* **Color** 让你选择任意 `System.Drawing.Color`。灰色是安全默认，你也可以使用 `Color.Black` 来加重，或 `Color.LightGray` 来保持柔和。

小技巧：如果将 `Enabled = false`，其他所有阴影设置都会被忽略，所以务必检查该标志。

## 第四步：将形状插入文档主体

矩形和阴影配置完成后，需要把它放入文档。最简单的方式是将其追加到第一节的第一个段落。

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

如果文档中已经有文本，你可以定位到特定的 `Paragraph`，甚至是 `Table` 单元格，然后插入形状。`AppendChild` 方法非常通用——它适用于任何 `Node` 类型。

## 第五步：保存文档并验证结果

最后，将文件写入磁盘。将路径改为你想要的位置；目标文件夹必须已存在，否则会抛出异常。

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

在 Microsoft Word（或 LibreOffice）中打开生成的 `ShadowedRectangle.docx`，你应该会看到一个带有清晰对角线阴影的灰色矩形，阴影向右下方偏移。如果阴影显得太淡，增大 `BlurRadius` 或 `Distance` 并重新运行代码——实验是乐趣的一部分。

![创建带阴影的矩形形状示例](rectangle-shadow.png){alt="创建带阴影的矩形形状示例"}

### 预期输出

* 一个单页 Word 文档。
* 一个位于页面左上角、尺寸为 200 × 100 点的灰色矩形。
* 一个以 45° 角度、偏移 8 像素、模糊 5 像素的细腻灰色阴影。

## 深入了解：如何为形状添加阴影

你可能会想，*“我可以为阴影添加动画或根据用户输入动态变化吗？”* 虽然 Aspose.Words 本身不支持动画，但你可以在保存前以编程方式调整阴影属性，从而生成多个外观不同的文档版本。例如，对一组颜色进行循环：

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

这段小代码演示了 **如何动态设置阴影**——非常适合生成主题化报告。

## 创建矩形的替代形状

如果需要圆角矩形，只需切换 `ShapeType`：

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

或者，要得到正方形，只需让 `Width` 等于 `Height`。相同的阴影属性同样适用，因此无论选择哪种形状，你已经掌握了 **如何添加阴影** 的方法。

## 常见问题与排查

| 症状 | 可能原因 | 解决办法 |
|------|----------|----------|
| 阴影未显示 | `Shadow.Enabled` 仍为 `false` | 设置 `rectangleShape.Shadow.Enabled = true;` |
| 阴影过于锐利 | `BlurRadius` 为 0 | 将 `BlurRadius` 提高至至少 3 |
| 保存时抛出 `FileNotFoundException` | 目标文件夹不存在 | 先创建文件夹或使用有效路径 |
| 形状不可见 | Width/Height 为 0 | 确保两个尺寸均大于 0 |

关注这些细节可以避免经典的 “我的形状为什么不显示？” 的困惑。

## 小结 – 我们完成了什么

* 使用 Aspose.Words 在新建 Word 文档中 **创建矩形形状**。  
* 通过切换 `Shadow.Enabled` 标志并调节模糊、距离、角度和颜色，**为形状添加阴影**。  
* 演示了 **如何添加阴影**、**如何创建矩形**、以及 **如何设置阴影** 的完整、可复用代码片段。  
* 提供了一个完整的、可直接运行的示例，能够粘贴到任何 C# 项目中。

## 接下来可以做什么？

掌握基础后，你可以进一步探索：

* **如何为图片添加阴影**——相同的 `Shadow` API 适用于 `ShapeType.Image`。  
* **组合多个形状**——直接在 Word 中创建流程图或信息图。  
* **导出为 PDF**——在添加阴影后调用 `document.Save("output.pdf")`，生成可打印的 PDF 版本。

随意尝试不同的颜色、角度，甚至渐变填充。该 API 足够灵活，让你无需手动打开 Word 就能打造专业文档。

---

祝编码愉快！如果遇到任何问题，欢迎在下方留言或访问 Aspose.Words 论坛——社区会快速提供帮助。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}