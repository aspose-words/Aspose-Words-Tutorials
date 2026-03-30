---
category: general
date: 2026-03-30
description: 学习如何使用 C# 为 Word 形状设置阴影。本指南还展示了如何添加形状阴影、调整形状透明度以及添加矩形阴影。
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: zh
og_description: 如何在 C# 中为 Word 形状设置阴影？请按照本分步指南添加形状阴影、调整形状透明度以及添加矩形阴影。
og_title: 如何在 Word 形状上设置阴影 – C# 教程
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: 如何在 Word 形状上设置阴影 – C# 教程
url: /zh/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 形状上设置阴影 – C# 教程

是否曾想过 **如何在 Word 文档中的形状上设置阴影** 而不必手动操作 UI？你并不是唯一有此需求的人。在许多报告或营销演示文稿中，细微的投影可以让矩形更突出，而以编程方式实现则能节省数小时的工作量。

在本指南中，我们将逐步演示一个完整、可直接运行的示例，除了展示 **如何设置阴影**，还涵盖 **添加形状阴影**、**调整形状透明度**，甚至 **为矩形添加阴影**（适用于经典的标注框）。完成后，你将得到一个外观精致的 Word 文件（`output.docx`），并且了解每个属性的作用。

## 前置条件

- .NET 6+（或 .NET Framework 4.7.2）并配有 C# 编译器  
- Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）  
- 对 C# 和 Word 对象模型有基本了解  

无需其他库——所有功能均由 Aspose.Words 提供。

---

## 如何在 C# 中为 Word 形状设置阴影

下面是完整的源文件。将其保存为 `Program.cs`，然后在 IDE 或使用 `dotnet run` 运行。代码会加载已有的 `.docx`，找到第一个形状（默认是矩形），打开其阴影功能，微调若干视觉参数，并保存结果。

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **你将看到的效果** – 矩形现在拥有一个 30 % 透明度的黑色投影，向右下各偏移 5 pt，并带有柔和的模糊。打开 `output.docx` 进行验证。

## 调整形状透明度 – 为什么重要

透明度不仅是美观的调节钮，它还影响可读性。`0.0` 表示阴影完全不透明，`1.0` 则完全隐藏。在上面的代码片段中我们使用 `0.3`，实现了在浅色和深色背景下都适用的细腻效果。欢迎自行尝试：

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

请记住，**调整形状透明度** 也可以用于形状的填充颜色，以实现半透明的矩形本身。

## 为不同对象添加形状阴影

我们使用的代码针对 `Shape` 对象，但相同的 `ShadowFormat` 属性同样适用于 **Image**、**Chart** 甚至 **TextBox** 对象。下面是一段可以直接复制粘贴的通用模式：

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

因此，无论是 **为徽标添加形状阴影** 还是为装饰图标添加阴影，方法都是一致的。

## 如何为任意形状添加阴影 – 边缘情况

1. **没有边界框的形状** – 某些 Word 形状（如自由手绘线条）不支持阴影。尝试设置 `ShadowFormat.Visible` 时会悄然失效。若需安全检查，请使用 `shape.IsShadowSupported`。  
2. **旧版 Word** – 阴影属性对应 Word 2007 及以上的功能。如果必须兼容 Word 2003，打开文件时阴影会被忽略。  
3. **多个阴影** – Aspose.Words 目前每个形状仅支持单一阴影。如需双层效果，可复制形状、偏移位置并分别设置不同的阴影参数。

## 为矩形添加阴影 – 实际案例

设想你正在生成一份季度报告，每个章节标题都是一个彩色矩形。为其 **添加矩形阴影** 能让页面呈现出“卡片式”外观。步骤与基础示例相同，只需确保目标形状确实是矩形（`shape.ShapeType == ShapeType.Rectangle`）。如果需要从头创建矩形，请参考下面的代码片段：

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

运行包含此代码的完整程序后，你将得到一个已经具备 **添加矩形阴影** 效果的新矩形。

---

![Word shape with shadow](placeholder-image.png){alt="在 Word 中为形状设置阴影"}

*图示：应用阴影设置后的矩形。*

## 快速回顾（要点速查表）

- **加载** 文档：`new Document(path)`。  
- **定位** 形状：`doc.GetChild(NodeType.Shape, index, true)`。  
- **启用** 阴影：`shape.ShadowFormat.Visible = true;`。  
- **设置颜色**：使用任意 `System.Drawing.Color`。  
- **调整透明度**（`0.0–1.0`）以控制不透明度。  
- **OffsetX / OffsetY** 以点为单位水平/垂直移动阴影。  
- **BlurRadius** 用于软化边缘——数值越大阴影越模糊。  
- **保存** 文件并在 Word 中打开查看效果。

## 接下来可以尝试什么？

- **动态颜色** – 从主题或用户输入中获取阴影颜色。  
- **条件阴影** – 仅当形状宽度超过阈值时才应用阴影。  
- **批量处理** – 遍历文档中所有形状，自动 **添加形状阴影**。  

如果你已经跟随完成上述步骤，现在你已经掌握了 **如何设置阴影**、**如何调整形状透明度**，以及 **如何为矩形添加阴影**，从而让文档更具专业感。尽情实验、敢于出错再修复——编码是最好的老师。

---

*祝编码愉快！如果本教程对你有帮助，欢迎留言或分享你的阴影技巧。大家相互学习，Word 文档会变得更美观。*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}