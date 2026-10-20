---
category: general
date: 2026-03-25
description: 在 C# 中创建 PDF 文档，并学习如何添加矩形形状、设置填充颜色、调整形状大小以及设置形状透明度，只需几个步骤。
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: zh
og_description: 在 C# 中创建 PDF 文档，了解如何添加矩形、设置填充颜色、大小和透明度，以获得精美的 PDF 输出。
og_title: 使用矩形形状创建 PDF 文档 – C# 教程
tags:
- C#
- PDF
- Aspose.Words
title: 使用矩形形状创建 PDF 文档 – 完整 C# 指南
url: /zh/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用矩形形状创建 PDF 文档 – 完整 C# 指南

是否曾需要**创建 PDF 文档**并包含自定义样式的形状，但不知从何入手？你并不孤单。无论是构建报告生成器还是营销传单，能够以编程方式绘制矩形、设置填充颜色、调整尺寸，甚至调节透明度，都能让你的 PDF 看起来更专业。

在本教程中，我们将逐步演示一个完整、可直接运行的 C# 示例，**创建 PDF 文档**、**添加矩形形状**、**设置填充颜色**、**定义形状尺寸**，以及**设置形状透明度**以实现细腻的外部阴影。完成后，你将得到一个名为 `shadow.pdf` 的 PDF 文件，打开即可看到效果。

> **技巧提示：** 同样的方法适用于其他形状类型（椭圆、直线等）——只需将 `ShapeType.RECTANGLE` 替换为所需的形状即可。

---

## 你需要的准备

| 先决条件 | 原因 |
|--------------|----------------|
| **.NET 6+**（或 .NET Framework 4.6+） | Aspose.Words 库面向现代运行时。 |
| **Aspose.Words for .NET** NuGet 包 | 提供 `Document`、`Shape`、`ShadowEffect` 等相关类。 |
| **C# IDE**（Visual Studio、Rider、VS Code） | 让调试和运行示例变得轻松无痛。 |
| **基本的 C# 知识** | 你无需深入学习即可理解语法。 |

你可以通过命令行安装该库：

```bash
dotnet add package Aspose.Words
```

就这么简单——无需额外的 DLL，也没有本地依赖。安装好包后，下面的代码即可编译运行。

---

## 步骤实现

下面我们将过程拆分为五个逻辑步骤。每个步骤都有明确的标题（便于 AI 模型索引），并附有可直接复制粘贴的简短代码块。

### ## 1. 创建 PDF 文档并准备画布

我们首先实例化一个 `Document`。可以把它看作最终会生成 PDF 文件的空白画布。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **为什么？** `Document` 包含所有章节、段落和形状。使用全新的对象可确保没有来自之前运行的隐藏残留。

### ## 2. 添加矩形形状 – 设置填充颜色和形状尺寸

现在我们创建一个矩形，给它一个亮黄色填充，并定义其尺寸。这同时实现了 **add rectangle shape**、**set fill color** 和 **set shape size**。

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **注意：** 宽度/高度的单位是点（1 point = 1/72 英寸）。根据你的布局调整这些数值。

### ## 3. 应用外部阴影并设置形状透明度

阴影可以增加层次感，控制其不透明度正是 **set shape transparency** 的核心。下面我们配置一个 30 % 透明度的灰色外部阴影。

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **为什么要设置透明度？** 30 % 透明的阴影看起来更柔和，避免矩形在页面上显得“平坦”。

### ## 4. 将形状插入文档正文

现在我们将矩形放入文档第一节的第一个段落中。此步骤将所有内容关联起来。

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **特殊情况：** 如果需要在新页面上放置形状，请在追加形状之前在代码前面加入 `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;`。

### ## 5. 将文档保存为 PDF 文件

最后，我们将内存中的结构持久化为实际的 PDF 文件。文件会写入你指定的文件夹。

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

运行程序后，会生成名为 `shadow.pdf` 的文件。打开后可看到一个黄色矩形，带有向右下偏移 4 点的柔和灰色阴影——正是代码所描述的效果。

> **预期输出：** 单页 PDF，矩形位于页面左上角附近，填充黄色，尺寸为 200 × 100 点，并投射出半透明的外部阴影。

## 完整可运行示例（复制粘贴即可）

下面是完整的源文件，可直接放入新的控制台项目中使用。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **提示：** 将 `YOUR_DIRECTORY` 替换为绝对路径（如 `C:\\Temp`）或相对路径（如 `./output`）。如果文件夹不存在，程序会自动创建。

## 常见问题 (FAQ)

**Q: 我可以更改矩形在页面上的位置吗？**  
A: 当然可以。在将其追加到段落之前，设置 `rectangle.Left` 和 `rectangle.Top`（单位均为点）。

**Q: 如果我需要透明填充而不是透明阴影怎么办？**  
A: 使用 `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` ——第一个参数是 alpha 通道（0‑255），其中 128 大约对应 50 % 透明度。

**Q: 这在 .NET Core 上可用吗？**  
A: 可以。Aspose.Words 支持 .NET Standard 2.0+，因此可以在 .NET 6、.NET 7 或 .NET Framework 4.6+ 上运行相同代码。

**Q: 如何添加多个形状？**  
A: 只需对每个形状重复步骤 2‑4，必要时将它们插入不同的段落或章节。

## 结论

我们刚刚**从零创建了 PDF 文档**，**添加了矩形形状**，**设置了填充颜色**，**定义了尺寸**，并**调整了形状透明度**，实现了精致的阴影效果。示例代码是独立的，运行时间不到一分钟，展示了构建更复杂 PDF 布局所需的核心概念。

准备好接受下一个挑战了吗？尝试将矩形换成圆角形状、在形状内部嵌入图像，或自动生成目录。相同的 API 让你可以层叠文本、图像和矢量——无限可能。

如果你觉得本指南有帮助，请在 GitHub 上给它加星，分享给同事，或留下评论分享你的实现方式。祝编码愉快！

![使用矩形形状创建 PDF 文档示例](/images/rectangle-shadow.png "显示创建的 PDF，包含黄色矩形和灰色外部阴影的截图")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}