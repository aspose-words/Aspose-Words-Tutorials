---
category: general
date: 2026-01-03
description: 使用 C# 在 Word 中创建矩形形状并为其添加阴影。学习如何在 Word 中插入形状、为形状添加阴影以及以编程方式生成 Word 文档。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: zh
og_description: 使用 C# 在 Word 中创建矩形形状并为形状添加阴影。请按照本指南在 Word 中插入形状、配置阴影，并以编程方式生成文档。
og_title: 使用 C# 在 Word 中创建矩形形状 – 完整教程
tags:
- C#
- Word Automation
- Aspose.Words
title: 使用 C# 在 Word 中创建矩形形状 – 步骤指南
url: /zh/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 C# 创建矩形形状 – 完整教程

是否曾需要在 Word 文档中 **create rectangle shape**，但不知从何入手？你并不孤单——许多开发者在想要 **add shadow to shape** 以获得精致外观时都会遇到同样的难题。在本教程中，我们将逐步演示如何 **insert shape in Word**，应用细腻的阴影，最终 **c# generate word document** 并生成可供用户使用的文件。

我们将覆盖从项目设置到微调阴影属性的全部内容，并以可直接运行的代码示例收尾。没有冗余，只提供完成任务的实用要点。

## 您将学习的内容

- 如何使用 Aspose.Words（或 Open XML）在 C# 中 **create rectangle shape**
- 实现深度所需的 **add shadow to shape** 的确切属性
- 使用 `DocumentBuilder` 放置形状的位置
- 如何保存文件，使其在 Microsoft Word 中正确打开
- 针对真实场景的技巧、常见陷阱和变体

### 前提条件

- .NET 6.0 或更高（代码在 .NET Core 和 .NET Framework 上均可运行）
- 一个可以操作 Word 文件的 NuGet 包——我们将使用 **Aspose.Words for .NET**，因为其 API 简洁。如果你更喜欢 Open XML SDK，概念相同，只是类不同。
- Visual Studio、VS Code 或任何你喜欢的 C# IDE

> **专业提示：** 如果预算有限，Aspose 提供免费试用，非常适合学习。测试时只需将许可证行替换为注释即可。

## 步骤 1：安装 Word 处理库

首先，将库添加到项目中。在解决方案文件夹中打开终端并运行：

```bash
dotnet add package Aspose.Words
```

如果使用 Open XML SDK，命令应为 `dotnet add package DocumentFormat.OpenXml`。本指南其余部分默认使用 Aspose.Words，但替换 API 调用也很简单。

## 步骤 2：创建新空白文档

库准备就绪后，我们可以通过创建一个干净的 `Document` 对象来 **create rectangle shape**。把它想象成一块全新的画布。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` 为我们提供了一种高级方式来插入内容，无需深入低层节点树。

## 步骤 3：插入矩形形状

手握 builder 后，我们可以 **insert shape in Word**。`InsertShape` 方法接受形状类型以及以点为单位的尺寸（宽度、高度）。

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

此时矩形已出现在文档中，但看起来有些平淡。接下来的步骤将解决这个问题。

## 步骤 4：为形状添加阴影

阴影为形状提供深度感。`Shadow` 对象让我们可以微调模糊、距离、角度、颜色和透明度。下面是一套适用于大多数报告的完整配置。

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**为何使用这些数值？**  
- `5.0` 的 **BlurRadius** 保持边缘平滑且不显模糊。  
- `4.0` 的 **Distance** 将阴影偏移到恰好可见的程度。  
- `45` 的 **Angle** 模拟左上方的自然光照，这是常见的 UI 约定。  
- `0.3` 的 **Transparency** 防止阴影压过形状的填充颜色。

如果需要更强烈的效果，可增大 `BlurRadius` 并降低 `Transparency`。若想要细微、几乎不可见的提升，则相反调节这些数值。

## 步骤 5：保存文档

最后，将文件写入磁盘。`Save` 方法会根据文件扩展名检测格式，因此 `.docx` 会生成现代 Word 格式。

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

在 Microsoft Word 中打开 `ShadowRectangle.docx`，你会看到一个带有柔和阴影的清晰矩形——正是你在询问 “**how to add shape**” 时想要的专业效果。

![Create rectangle shape with shadow in Word](placeholder-image.png "Create rectangle shape with shadow in Word")

*图片替代文字：create rectangle shape with shadow in Word*

## 完整工作示例

将所有步骤整合在一起，下面是完整的可直接运行的程序。复制粘贴到控制台应用并按 **F5** 运行。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### 预期结果

- 生成的 `ShadowRectangle.docx` 包含 **一个矩形形状**，位于光标所在的中心位置。  
- 矩形显示 **柔和、30 % 透明的黑色阴影**，偏移角度为 45°。  
- 未添加其他内容，使文件保持轻量，便于嵌入更大的报告中。

## 常见问题与边缘情况

### 如果需要不同的形状怎么办？

将 `ShapeType.Rectangle` 替换为任意其他 `ShapeType` 枚举值（例如 `Ellipse`、`Triangle`）。阴影 API 的使用方式相同，配置可直接复用。

### 如何更改填充颜色？

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### 能否将形状添加到特定段落？

可以。在调用 `InsertShape` 之前，使用 `builder.MoveToParagraph(index)` 将 `DocumentBuilder` 移动到目标段落。这样可确保形状出现在所需位置。

### 老版本 Word 格式（.doc）怎么办？

只需更改扩展名：

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

阴影功能在 Word 2003 及以后版本均受支持，因此仍可看到效果。

### 使用 Open XML SDK 而非 Aspose？

步骤保持不变：创建 `WordprocessingDocument`，添加 `Drawing` 元素，设置 `<a:shadow>` 属性。XML 更为冗长，但相同的概念（尺寸、模糊、距离、角度）仍然适用。

## 避免陷阱的技巧

- **不要忘记许可证**，如果使用付费的 Aspose 版本，否则会出现水印。  
- **单位是点**，而非像素。典型屏幕像素约为 0.75 pt，请相应调整尺寸。  
- **如果形状的 `WrapType` 设置为 `Inline`，阴影属性会被忽略**。使用 `WrapType = WrapType.Square` 对于能够呈现阴影的浮动形状。  
- **保存到网络共享**可能需要适当的权限；请始终先测试路径。

## 结论

现在你已经掌握了如何使用 C# 在 Word 文档中 **create rectangle shape**，**add shadow to shape**，以及 **c# generate word document** 并生成即开即用、外观精致的文件。核心步骤——安装库、实例化 `Document`、插入形状、配置阴影以及保存——易于记忆且可适配其他形状、颜色或动态数据。

接下来可以尝试叠加多个形状、嵌入图片，或生成包含表格和图表的完整报告。你还可以探索条件格式——根据数据值改变阴影强度，使文档不仅功能完整，还具备视觉吸引力。

欢迎随意实验，如遇奇怪问题，请在下方留言。祝编码愉快，愿你的 Word 文档始终拥有完美的投影阴影！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}