---
category: general
date: 2026-02-24
description: 使用 Aspose.Words 在 C# 中创建矩形形状，给形状添加阴影，并将文档保存为 PDF。学习如何添加阴影以及如何在几分钟内保存
  PDF。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: zh
og_description: 使用 Aspose.Words 在 C# 中创建矩形形状，然后为形状添加阴影并将文档保存为 PDF——完整的逐步指南。
og_title: 创建矩形形状，添加阴影并保存为 PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: 创建矩形形状，添加阴影并保存为 PDF
url: /zh/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建矩形形状，添加阴影并保存为 PDF

是否曾经需要在 Word 文档中 **创建矩形形状**，但又想要一个漂亮的投影并导出为 PDF？你并不是唯一有此需求的人。在许多报表或发票生成项目中，视觉上的精致——比如细微的阴影——决定了文件是“仅仅是另一个文件”还是“专业级文档”。  

在本教程中，我们将一步步演示：使用 **Aspose.Words for .NET** 创建矩形形状、为形状添加阴影，最后 **将文档保存为 PDF**。完成后，你将拥有一个可直接运行的 C# 控制台应用程序，生成带阴影矩形的 PDF，并了解如何微调阴影或更改导出选项。

## 您需要的环境

- .NET 6 SDK（或任何近期的 .NET 版本）——API 在 .NET Framework 4.x 上同样适用。  
- Aspose.Words for .NET NuGet 包 (`Aspose.Words`)——使用 `dotnet add package Aspose.Words` 安装。  
- 代码编辑器——Visual Studio、VS Code 或 Rider 都可以。  

此示例无需额外的授权步骤；免费评估模式已足以查看 PDF 输出。

## 步骤 1：设置项目并导入命名空间

首先，让我们创建一个控制台项目并引入所需的类。

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*为什么重要*：`Document` 和 `DocumentBuilder` 为我们提供画布，而 `Shape` 与 `ShadowFormat` 则用于绘制和设置矩形的样式。提前导入它们可以让后续代码更简洁。

## 步骤 2：**创建矩形形状** 并设定所需尺寸

现在我们实际创建一个空白文档并插入矩形。注意 `InsertShape` 方法返回一个 `Shape` 对象，随后即可对其进行样式设置。

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*说明*：尺寸以点为单位（1 pt = 1/72 in）。根据你的布局调整数值。我们还为形状填充了浅蓝色，以便阴影更加突出。

## 步骤 3：**为形状添加阴影** – 微调效果

阴影并非只有“开/关”。你可以控制颜色、模糊程度、距离、方向，甚至透明度。以下是一个在大多数报表中表现良好的实用配置。

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*为什么可能需要更改这些值*：  
- **BlurRadius** – 增大可获得梦幻效果，减小则边缘更清晰。  
- **Direction** – 0° 指向右，90° 向下，180° 向左，依此类推。根据页面布局旋转。  
- **Transparency** – 设置为 `0` 表示实心阴影，`0.5` 表示半透明，依此类推。

### 添加阴影的替代方法

如果需要 **多层阴影**（例如更暗的外层阴影加上更浅的内层阴影），可以创建第二个形状，偏移后设置不同的 `ShadowFormat`。或者想要快速实现“无模糊”效果，只需将 `BlurRadius = 0`。

## 步骤 4：**将文档保存为 PDF** – 最终导出

矩形及其阴影准备就绪后，最后一步是将文件写出为 PDF。Aspose.Words 在内部完成转换，只需调用 `Save` 并指定所需格式。

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*提示*：如果需要控制 PDF 合规性（PDF/A、PDF/X）或嵌入字体，请使用相应的重载：

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

这就是 **如何保存 PDF** 的要点。

## 完整、可运行的示例

下面是完整的程序代码，可直接复制粘贴到 `Program.cs` 中。它可以直接编译运行（只需确保输出文件夹已存在）。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### 预期结果

打开生成的 `ShadowRectangle.pdf`。你会看到单页上有一个浅蓝色矩形，右下角偏移 45° 的柔和灰色阴影，边缘清晰。该 PDF 可在任何现代阅读器（Adobe Acrobat、Edge、Chrome）中查看。

![在 PDF 中创建带阴影的矩形形状](/images/shadow-rectangle.png "在 PDF 中创建带阴影的矩形形状")

*(图片 alt 文本包含主要关键词，有助于 SEO。)*

## 常见问题与边缘情况处理

**如果阴影在 PDF 中消失怎么办？**  
确保使用的是最新版本的 Aspose.Words（≥23.3）。旧版本存在在 PDF 转换时忽略某些阴影属性的 bug。

**可以将阴影颜色改成符合品牌的颜色吗？**  
完全可以——只需将 `System.Drawing.Color.Gray` 替换为任意 `Color`，例如 `Color.FromArgb(128, 0, 0, 255)` 可得到半透明蓝色。

**如何为其他形状（椭圆、星形等）添加阴影？**  
`ShadowFormat` 对任何 `Shape` 对象都适用。创建形状后，获取其 `ShadowFormat` 并设置相应属性即可。

**DPI 或缩放会有问题吗？**  
PDF 渲染会遵循形状的点大小。如果需要更高分辨率的输出（用于打印），请相应地增大形状尺寸或设置 `PdfSaveOptions.ImageResolution`。

**可以导出为其他格式，如 PNG 吗？**  
可以——只需调用 `document.Save("output.png", SaveFormat.Png)`。阴影会以相同方式渲染。

## 专业技巧与最佳实践

- **复用 builder**：如果要添加多个形状，保持使用同一个 `DocumentBuilder` 实例；比创建多个实例更省资源。  
- **批量保存**：在循环中生成大量 PDF 时，复用 `PdfSaveOptions` 对象以避免重复分配。  
- **测试**：保存后务必打开 PDF 验证阴影是否如预期显示。部分 PDF 阅读器对阴影的渲染略有差异，Adobe Acrobat 是最可靠的参考。  
- **性能**：对于大型文档，可通过将 `builder.PageSetup.DifferentFirstPageHeaderFooter = false` 来关闭 `DocumentBuilder.InsertShape` 的自动分页（前提是你不需要它）。

## 结论

我们已经覆盖了使用 Aspose.Words for .NET **创建矩形形状**、**为形状添加阴影**以及**将文档保存为 PDF**的全部要点。代码简洁，概念清晰，现在你拥有了实验其他形状、阴影样式和导出选项的坚实基础。  

下一步？尝试将矩形换成圆角‑

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}