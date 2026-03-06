---
category: general
date: 2026-03-06
description: 在 Word 中创建矩形形状并使用 Aspose.Words 添加形状阴影。了解如何在 Word 中插入矩形以及如何在 C# 中为形状添加阴影。
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: zh
og_description: 使用 Aspose.Words 在 Word 中创建矩形形状并添加形状阴影。一步步指南，教您如何在 Word 中插入矩形以及如何为形状添加阴影。
og_title: 使用 Aspose.Words 在 Word 中创建带阴影的矩形形状
tags:
- Aspose.Words
- C#
- Word Automation
title: 使用 Aspose.Words 在 Word 中创建带阴影的矩形形状
url: /zh/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 Aspose.Words 创建矩形形状并添加阴影

是否曾经需要在 Word 文档中 **create rectangle shape**，却不确定如何让它看起来更精致？你并不孤单——大多数开发者在第一次为自动生成的文档添加视觉效果时都会遇到同样的难题。好消息是：使用 Aspose.Words for .NET，你只需几行 C# 代码就能 **create rectangle shape** 并 **add shape shadow**。

在本教程中，我们将一步步演示 **如何在 Word 中插入矩形**，随后展示 **如何为形状添加阴影** 使其从页面中凸显出来。完成后，你将得到一个可直接保存的 `Shadow.docx`，打开后可以看到带有柔和投影的灰色矩形。无需额外的图片文件，也不需要手动调节——全部由代码实现。

## 你将学到

- 使用 Aspose.Words **create rectangle shape** 所需的完整 C# 语句。  
- 如何通过 `Shadow` 对象启用并配置阴影。  
- 每个属性的作用（例如 `Transparency`、`Blur`、`Angle`）。  
- 常见陷阱（单位、版本兼容性）及快速解决方案。  
- 一个完整的、可直接复制粘贴运行的示例程序。

### 前置条件

- .NET 6+（或 .NET Framework 4.7+）。  
- Aspose.Words for .NET 23.10 或更高版本（NuGet 包名为 `Aspose.Words`）。  
- 对 C# 和 Visual Studio（或你喜欢的任意 IDE）有基本了解。  

如果你已经满足上述条件，下面直接进入实践。

---

## 第 1 步：创建项目并导入命名空间

首先，新建一个控制台应用（或使用已有项目），并添加 Aspose.Words NuGet 包：

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

随后在 `Program.cs` 中引入所需的命名空间：

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **小技巧：** 如果你使用的是 .NET 6+，可以启用全局 `using` 指令，省去在每个文件中重复写这些行。

---

## 第 2 步：在空白 Word 文档中 **create rectangle shape**

我们将从一个全新的 `Document` 对象和一个 `DocumentBuilder` 开始操作。矩形的创建依赖于 `InsertShape` 方法。

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

为什么是 200 × 100 点（points）？在 Word 中，1 点等于 1/72 英寸，所以矩形大约为 2.8 × 1.4 英寸——足够显眼但不会占据太多空间。你可以根据布局需要自行修改这些数值，只需记住它们的单位是 **points**，而非像素。

---

## 第 3 步：**Add shape shadow** – 配置外观

现在已有矩形，接下来为它添加一个细腻的灰色阴影。`Shadow` 对象挂在 `Shape` 上，提供了多个实用属性。

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### 各属性作用说明

| Property | Effect | Typical values |
|----------|--------|----------------|
| **Enabled** | 开启或关闭阴影 | `true` 或 `false` |
| **Color** | 阴影的基础颜色 | 任意 `System.Drawing.Color` |
| **Transparency** | 不透明度（0 = 实色，1 = 完全透明） | 0.0 – 1.0 |
| **Blur** | 边缘柔化程度 | 0 – 10（数值越大越柔和） |
| **Distance** | 形状与阴影之间的间距 | 0 – 20 points |
| **Angle** | 光源方向 | 0 – 360 度 |
| **Size** | 阴影相对于形状的比例 | 0 – 200 % |

> **为什么要调这些设置？**  
> 细调阴影可以让你轻松符合企业品牌规范（例如使用 20 % 透明度的细微阴影），而无需借助外部图像编辑器。

---

## 第 4 步：保存文档并验证结果

最后，将文件写入磁盘。你可以自行决定保存路径，只需将 `YOUR_DIRECTORY` 替换为真实的文件夹路径。

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

在 Microsoft Word 中打开 `Shadow.docx`，你应该能看到一个带有柔和投影、倾斜 45° 的灰色矩形。这个视觉效果让形状看起来像是“悬浮”在页面上——正是精致报表或发票所需要的效果。

---

## 完整工作示例

下面是可以直接复制粘贴到 `Program.cs` 的完整程序。所有代码均完整无缺，直接编译运行即可。

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### 预期输出

- **文件：** `Shadow.docx` 位于项目的执行文件夹。  
- **视觉效果：** 页面中心出现一个默认白色填充的矩形，右下方偏移 4 points 的灰色阴影，略带模糊，呈自然外观。

---

## 常见问题与边缘情况

### 1. 如果需要使用其他单位（例如厘米）怎么办？

Aspose.Words 使用 points 作为单位，但可以通过以下公式将厘米转换为 points：  
`points = centimeters * 28.3465`。

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. 旧版本的 Aspose.Words 能否使用？

`Shadow` API 是在 14.0 版本中引入的。如果你使用的是更早的版本，需要通过 NuGet 升级。创建形状的其余代码多年来一直保持稳定，不会出现破坏性更改。

### 3. 能否为其他形状（例如圆形）添加阴影？

完全可以——任何 `Shape` 对象都拥有 `Shadow` 属性。只需将 `ShapeType.Rectangle` 替换为 `ShapeType.Ellipse`、`ShapeType.Cloud` 等，然后使用相同的阴影设置即可。

### 4. 如果需要彩色阴影（例如品牌蓝）怎么办？

将 `Color.Gray` 替换为任意你想要的 `Color`：

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

记得相应调整 `Transparency`，避免颜色过于突出。

---

## 🎨 可视化摘要

![create rectangle shape with shadow in Word using Aspose.Words](image-placeholder.png "create rectangle shape with shadow in Word using Aspose.Words")

*Alt text: create rectangle shape with shadow in Word using Aspose.Words*

占位图展示了最终文档的效果——仅有矩形及其柔和的灰色阴影。

---

## 结论

现在，你已经掌握了如何在 Word 文件中 **create rectangle shape**、**add shape shadow**，并使用 Aspose.Words for .NET 对每个视觉细节进行微调。我们构建的简短程序覆盖了完整工作流——从

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}