---
category: general
date: 2026-02-26
description: 使用 Aspose.Words 在 Word 中创建矩形形状，并学习如何向 Word 添加形状、为形状应用阴影以及在几分钟内设置形状透明度。
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: zh
og_description: 使用 Aspose.Words 在 Word 中创建矩形形状。学习如何向 Word 添加形状、为形状应用阴影以及快速设置形状透明度。
og_title: 在 Word 中创建矩形形状 – 完整 Aspose.Words 指南
tags:
- Aspose.Words
- C#
- Word Automation
title: 在 Word 中创建矩形形状 – 完整 Aspose.Words 指南
url: /zh/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

have a table with columns: Property, What It Controls, Typical Values. Translate header row content? Probably yes, translate "Property", "What It Controls", "Typical Values" to Chinese, but keep property names unchanged. The table rows have property names and values; keep property names unchanged, but translate description and typical values? Typical values are numbers; keep as is. So translate "Softness of the shadow edges" etc.

Also translate bullet points, etc.

Let's produce final content.

Be careful with markdown formatting.

Let's start.

We need to keep the shortcodes at top exactly as they are.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中创建矩形形状 – 完整 Aspose.Words 指南

是否曾需要在 Word 文档中 **创建矩形形状**，却不知从何入手？你并不孤单——许多开发者在自动化报表或发票时都会遇到这个难题。在本教程中，我们将通过一个完整、可直接运行的示例，展示如何 **向 Word 添加形状**、应用细腻的阴影，并控制形状的透明度，全部使用 Aspose.Words for .NET。

阅读完本指南后，你将得到一个包含干净矩形及精致阴影的 `.docx` 文件——非常适合品牌标识、提示框，或仅仅让文档看起来更专业。无需外部工具，只需几行 C# 代码。

## 所需环境

- **Aspose.Words for .NET**（截至 2026 年初的最新版本）。可通过 NuGet 获取（`Install-Package Aspose.Words`）。
- .NET 开发环境（Visual Studio、Rider，或带 C# 扩展的 VS Code）。
- 对 C# 语法有基本了解——只需常规的 `using` 语句和对象创建。

如果你已经具备上述条件，太好了——让我们开始吧。

## 创建矩形形状 – 核心步骤

下面是完整源码。复制粘贴到新的控制台项目中，按 **F5** 运行，即可在指定文件夹中看到 `ShadowDemo.docx`。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### 为什么这样写

- **`Document`** 是入口点，代表整个 Word 文件。
- **`Shape`** 与 `ShapeType.Rectangle` 告诉 Aspose 我们需要一个矩形绘图对象。
- 设置 **`Width`** 和 **`Height`** 为形状指定确定的尺寸；否则默认是一个极小的占位符。
- **`Shadow`** 对象让我们可以微调每一个视觉属性：模糊、距离、方向、颜色、透明度和扩散。这正是 *apply shadow to shape* 的核心。
- 最后，**`AppendChild`** 将形状插入文档的第一个段落，这是在不涉及表格或页眉的情况下 *add shape to Word* 最简便的方式。

打开 `ShadowDemo.docx`，你会看到一个灰色矩形舒适地位于文档中，阴影向右下倾斜 45°。阴影不是实心块；模糊半径软化了边缘，透明度让它看起来更像自然的投影，而非生硬的覆盖。

![创建矩形形状示例](image.png "使用 Aspose.Words 在 Word 中创建带阴影的矩形形状")

*(上图展示了代码片段的最终效果。)*

## 向 Word 文档添加形状 – 放置选项

示例使用 **第一个段落**，因为这是最快看到效果的方式。在实际项目中，你可能需要：

- 将形状插入特定的 **section** 或 **header/footer**。
- 将其放入 **表格单元格** 中，以便与表格数据对齐。
- 使用 **文本环绕** 选项（例如 `WrapType.Square`）让周围文字环绕矩形。

下面是一个快速变体，将形状放入带自定义样式的新段落中：

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*小技巧：* 始终在配置完属性后再添加形状；否则可能需要调用 `UpdateLayout` 来刷新视觉效果。

## 为形状应用阴影 – 精细调节外观

阴影可以显著改变文档的美感。`Shadow` 类公开了多个属性：

| 属性            | 控制内容                                           | 常用取值 |
|----------------|----------------------------------------------------|----------|
| `BlurRadius`   | 阴影边缘的柔软程度                                 | 2.0 – 10.0 |
| `Distance`     | 阴影相对于形状的偏移距离                           | 1.0 – 8.0 |
| `Direction`    | 角度（度），0 = 左，90 = 上                         | 0 – 360 |
| `Color`        | 阴影颜色（任意 `System.Drawing.Color`）            | Gray、Black、Custom |
| `Transparency` | 不透明度（0 = 完全不透明，1 = 完全透明）           | 0.0 – 0.5 |
| `Spread`       | 在应用模糊之前阴影的扩展程度                       | 0.0 – 1.0 |

如果你想要 **细腻、专业的外观**，将 `BlurRadius` 保持在 4‑6 左右，`Transparency` 设为约 0.2，正如上面的代码所示。若想要 **戏剧化效果**，可将 `Distance` 提升至 6，`Direction` 设置为 135°，并将 `Transparency` 降至 0.05。

## 设置形状透明度和阴影扩散

透明度不仅适用于阴影，你还可以让矩形本身半透明：

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

将半透明填充与柔和阴影结合，常能营造出现代 UI 感——非常适合在报告中嵌入仪表盘或设计稿。

### 需要注意的边缘情况

1. **旧版 Word（2007 前）** 不支持部分阴影属性。如果目标是 `.doc` 文件，建议简化阴影（例如将 `BlurRadius` 设为 0）。
2. **高 DPI 显示器** 可能会略有不同地渲染阴影。若视觉一致性至关重要，请在目标环境中进行测试。
3. **形状重叠**——Aspose 按添加顺序渲染阴影。请从后向前插入形状，以避免不期望的遮挡。

## 保存并验证结果

`Document.Save` 方法会根据文件扩展名自动检测输出格式。对于 **`.docx`** 文件，你会得到 Open XML 格式，现代 Word 处理器均能识别。若需要 **PDF** 版本且保持相同视觉效果，只需更改扩展名：

```csharp
document.Save("ShadowDemo.pdf");
```

打开生成的 `ShadowDemo.docx`（或 `ShadowDemo.pdf`），应能看到一个带阴影的干净 **矩形**，从而确认你已经成功 *create rectangle shape* 并 *apply shadow to shape* 使用 Aspose.Words。

## 常见问题

**问：我可以使用其他形状，比如椭圆吗？**  
答：完全可以。将 `ShapeType.Rectangle` 替换为 `ShapeType.Ellipse`（或其他 `ShapeType` 枚举）。阴影属性保持不变。

**问：如果需要让矩形可点击怎么办？**  
答：可以为形状分配超链接：

```csharp
rectangleShape.Href = "https://example.com";
```

**问：这在 .NET 6+ 上能工作吗？**  
答：可以。Aspose.Words 23.11 及以后版本完整支持 .NET 6、.NET 7 和 .NET 8。只需引用相应的 NuGet 包。

**问：如何将阴影颜色改为符合品牌色？**  
答：使用任意 `System.Drawing.Color` 即可：

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## 小结

我们已经覆盖了在 Word 文档中 **create rectangle shape**、**add shape to Word**、**apply shadow to shape** 以及 **set shape transparency** 所需的全部内容。完整、可运行的代码位于本文顶部，说明帮助你自信地调整尺寸、颜色和阴影参数，以适配任何项目。

准备好下一步了吗？可以尝试以下实验：

- 将多个形状层叠，以实现徽章效果。
- 根据文档内容动态计算尺寸（例如根据表格列宽计算宽度）。
- 将文档导出为 PDF 或 HTML，同时保留阴影效果。

如果遇到任何问题，欢迎留言讨论，或分享你自己的 “带阴影的矩形” 变体。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}