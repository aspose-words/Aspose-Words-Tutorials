---
category: general
date: 2025-12-25
description: 如何在 C# 中添加阴影并提供简易代码示例。了解如何设置阴影距离、自定义颜色，以及为图形创建深度。
draft: false
keywords:
- how to add shadow
- how to set shadow distance
language: zh
og_description: 逐步讲解如何在 C# 中添加阴影。按照指南设置阴影距离、颜色和模糊，以获得专业外观的形状。
og_title: 如何在 C# 中添加阴影 – 完整编程指南
tags:
- C#
- graphics
- Aspose.Words
- shadows
title: 如何在 C# 中添加阴影 – 完整编程指南
url: /zh/python/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中添加阴影 – 完整编程指南

在 C# 中添加阴影是当你希望图形从页面中凸显出来时的常见需求。在本教程中，我们将逐步演示如何为形状设置阴影，包括如何设置阴影距离、调整模糊程度以及选择合适的颜色。

如果你曾盯着一个平面的矩形并想“这需要一点深度”，那么你来对地方了。我们将从空白文档开始，加入一个形状，最后呈现出看起来像是由设计师精心放置的阴影。没有冗余，只提供可直接复制‑粘贴的实用示例。

## 你将学到

- 创建新文档并以编程方式插入形状。  
- 为形状的阴影应用柔和的模糊。  
- **如何设置阴影距离** 使阴影自然偏移。  
- 选择在任何背景下都适用的阴影颜色。  
- 将结果保存为 PDF（或任意你需要的格式）。  

### 前置条件

- .NET 6.0 或更高（代码同样适用于 .NET Core 和 .NET Framework）。  
- Aspose.Words for .NET（免费试用版或正式授权版）。  
- 对 C# 语法有基本了解。  

就这些——无需额外库，也不需要魔法。让我们开始吧。

![带有柔和黑色阴影的形状示例 – 如何添加阴影](https://example.com/placeholder-shadow.png "如何添加阴影示例")

## 第 1 步：设置项目并导入命名空间

首先，创建一个新的控制台应用（或任意 C# 项目），并添加 Aspose.Words NuGet 包：

```bash
dotnet new console -n ShadowDemo
cd ShadowDemo
dotnet add package Aspose.Words
```

现在打开 `Program.cs`，将所需的命名空间引入作用域：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;
```

> **小贴士：** 如果使用 Visual Studio，IDE 会在你键入 `Document` 时自动建议 `using` 语句。

## 第 2 步：创建新文档并添加形状

准备好库后，我们可以实例化一个 `Document` 对象，并在首页放置一个简单的矩形。

```csharp
// Step 2: Initialize the document
Document doc = new Document();

// Add a blank page (Aspose.Words creates one automatically)
Section section = doc.FirstSection;

// Insert a rectangle shape – this will be the object we give a shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    // Size the shape (width, height) in points (1 point = 1/72 inch)
    Width = 200,
    Height = 100,
    
    // Position the shape 100 points from the left and 150 from the top
    Left = 100,
    Top = 150,
    
    // Fill the shape with a light gray so the shadow stands out
    FillColor = System.Drawing.Color.LightGray
};

// Add the shape to the document's first page
section.Body.FirstParagraph.AppendChild(rectangle);
```

为什么是矩形？它是一个中性的画布，能够让阴影效果在不受干扰的情况下得到评估。你也可以将 `ShapeType.Rectangle` 替换为 `Ellipse` 或 `Star`——阴影逻辑保持不变。

## 第 3 步：如何添加阴影 – 应用模糊、距离和颜色

下面进入本教程的核心：**如何为矩形添加阴影**。Aspose.Words 在每个形状上都提供了 `Shadow` 对象，允许你调节模糊、距离和颜色。

```csharp
// Step 3: Access the shape's shadow settings
Shadow shadow = rectangle.Shadow;

// 3a) Apply a soft blur – larger values make the shadow fuzzier
shadow.Blur = 5.0;          // 5 points blur gives a subtle, professional look

// 3b) Set the shadow's offset distance – this determines how far the shadow is displaced
shadow.Distance = 3.0;      // 3 points offset is enough to suggest depth without looking detached

// 3c) Choose a shadow color – black works on most backgrounds, but you can experiment
shadow.Color = Color.Black; // Solid black; you could use Color.FromArgb(128, 0, 0, 0) for semi‑transparent

// OPTIONAL: Rotate the shadow to match a light source direction (45 degrees works well)
shadow.Angle = 45.0;
```

请注意注释 `// 3b) Set the shadow's offset distance`。该行直接回答了 **如何设置阴影距离**。通过调整 `shadow.Distance`，你可以控制形状与阴影之间的视觉间隙，从而模拟特定角度的光源。

### 为什么使用这些数值？

- **Blur = 5.0** – 适度的模糊可以避免硬朗的轮廓，同时仍保持可见。  
- **Distance = 3.0** – 让阴影足够靠近，看起来像是由形状本身投射的。  
- **Color = Black** – 在明暗两种背景下都能保证对比度。  

随意修改这些数值；API 接受任意 `double` 类型的值。

## 第 4 步：保存文档并验证结果

阴影配置完成后，只需将文件写入磁盘。Aspose.Words 支持多种输出格式，PDF 是常用的共享格式。

```csharp
// Step 4: Save the document as a PDF (you could also use .docx, .png, etc.)
string outputPath = "ShadowedShape.pdf";
doc.Save(outputPath, SaveFormat.Pdf);

Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
```

打开 `ShadowedShape.pdf`，你应该会看到一个带有柔和黑色阴影、略微向右下偏移的灰色矩形。如果阴影显得太淡，可增大 `shadow.Blur` 或 `shadow.Distance` 后重新运行。

## 常见问题与边缘情况

### 如果需要透明阴影怎么办？

使用带有小于 255 的 alpha 通道的 ARGB 颜色：

```csharp
shadow.Color = Color.FromArgb(80, 0, 0, 0); // 80/255 opacity = ~31% transparent
```

### 能否将相同的阴影应用到多个形状？

完全可以。创建一个帮助方法：

```csharp
static void ApplyStandardShadow(Shape shape)
{
    shape.Shadow.Blur = 5.0;
    shape.Shadow.Distance = 3.0;
    shape.Shadow.Color = Color.Black;
}
```

对每个新增的形状调用 `ApplyStandardShadow(rectangle);`。

### 这在旧版 .NET Framework 上能工作吗？

可以。Aspose.Words 22.9+ 支持 .NET Framework 4.5 及以上版本。只需相应地调整项目文件即可。

## 完整工作示例

下面是可以直接复制到 `Program.cs` 的完整程序。只要安装了 NuGet 包，即可编译运行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;

namespace ShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Initialize the document
            Document doc = new Document();
            Section section = doc.FirstSection;

            // Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 100,
                Top = 150,
                FillColor = System.Drawing.Color.LightGray
            };
            section.Body.FirstParagraph.AppendChild(rectangle);

            // Apply shadow – this is the core of "how to add shadow"
            Shadow shadow = rectangle.Shadow;
            shadow.Blur = 5.0;                // Soft blur
            shadow.Distance = 3.0;            // How to set shadow distance
            shadow.Color = Color.Black;       // Classic black shadow
            shadow.Angle = 45.0;              // Light source direction

            // Save as PDF
            string outputPath = "ShadowedShape.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
        }
    }
}
```

运行程序：

```bash
dotnet run
```

你将在项目文件夹中找到 `ShadowedShape.pdf`。使用任意 PDF 阅读器打开，确认阴影效果如描述所示。

## 结论

我们已经从头到尾完整演示了 **如何在 C# 中为形状添加阴影**，并展示了 **如何设置阴影距离**、模糊和颜色。只需几行代码，就能为图形赋予专业的三维感——无需外部设计工具。

掌握基础后，尝试以下变体：

- 将阴影颜色改为淡蓝色，营造更凉爽的氛围。  
- 增大模糊程度，获得梦幻、柔和的效果。  
- 将相同技巧应用于图表、图片或文本框。  

每一次变化都在巩固相同的核心概念，让你能够在任何场景下自如定制阴影。

还有其他问题吗？欢迎留言，祝编码愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}