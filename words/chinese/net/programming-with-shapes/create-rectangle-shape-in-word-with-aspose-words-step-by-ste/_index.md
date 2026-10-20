---
category: general
date: 2026-02-18
description: 使用 Aspose.Words 创建矩形形状，并学习如何添加阴影、设置形状大小以及在几分钟内保存 Word 文档。
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: zh
og_description: 在 Word 文件中创建矩形形状，学习如何添加阴影、设置形状大小，并使用 Aspose.Words 在 C# 中保存文档。
og_title: 在 Word 中创建矩形形状 – 完整的 Aspose.Words 教程
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 Aspose.Words 在 Word 中创建矩形形状 – 步骤指南
url: /zh/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 Aspose.Words 创建矩形形状 – 步骤指南

是否曾经需要在 Word 文件中 **创建矩形形状**，但不知从何入手？你并非唯一遇到此问题的开发者——大家常问：“如何为形状添加阴影并保持文档可编辑？”本教程将为你解答，并演示 **如何添加阴影**、**设置形状大小**以及 **保存 Word 文档** 的完整流程。

我们将一步步演示从初始化新文档（是的，这也是 **how to create document** 的第一步）到将最终的 *.docx* 持久化到磁盘。无需外部引用，只需一个自包含的示例，你可以直接复制粘贴到 Visual Studio 并立即运行。

---

## 前置条件

- .NET 6+（或 .NET Framework 4.7+）。Aspose.Words 可在任何近期的 .NET 运行时上运行。
- 有效的 Aspose.Words 许可证（或免费评估密钥）——否则会看到水印。
- Visual Studio、Rider 或任意你喜欢的 C# 编辑器。
- 基础的 C# 知识——不需要高级技巧，只要能运行控制台应用即可。

> **专业提示：** 如果你使用 Mac，相同的代码可在 .NET 6 与 VS Code 下运行——只需确保引用 `Aspose.Words` NuGet 包。

## 步骤 1：初始化文档 – **how to create document** 的基础

在绘制任何内容之前，我们需要一个空白画布。Aspose.Words 将其称为 `Document`。  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **为什么这很重要：** `Document` 对象代表整个 *.docx* 文件。你添加的所有形状、段落和节都会成为该对象的子级。使用全新的文档可以确保没有隐藏样式干扰你的矩形。

## 步骤 2：定义矩形并 **设置形状大小**

矩形只是一个 `Shape`，其 `ShapeType` 为 `Rectangle`。我们将为其指定明确的尺寸，使其呈现出预期的外观。  

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **数字含义：** Aspose.Words 使用点（1 pt = 1/72 英寸）。根据你的布局调整这些数值；对于常规的 A4 页面，200 pt 是一个舒适的宽度。

## 步骤 3：**如何添加阴影** – 让形状更突出

阴影提供了形状“悬浮”于页面上的视觉提示。`Shadow` 属性允许你调整颜色、距离、透明度和模糊程度。  

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **为什么使用透明度？** 完全不透明的阴影可能显得生硬。将其设为 0.4 可使效果更为柔和、专业。

## 步骤 4：定位矩形 – 与周围文本的内联流

如果希望形状在段落中表现得像一个字符，需将其 `WrapType` 设置为 `Inline`。这能保持布局的可预测性，尤其在文档后期编辑时。  

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **特殊情况：** 若需要矩形漂浮在文本上方（例如水印），可将 `WrapType` 改为 `Square` 或 `BehindText`。

## 步骤 5：将形状插入文档主体

现在我们将矩形实际放入第一段落。如果文档尚未有内容，`FirstParagraph` 会自动创建。  

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **提示：** 你也可以先创建一个新段落，然后再追加形状——在需要周围文本时非常有用。

## 步骤 6：**保存 Word 文档** – 最后一步

所有内容就绪后，保存文件只需一行代码。选择任意路径；示例中使用了占位符，请替换为你自己的目录。  

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **结果：** 在 Microsoft Word 中打开生成的 *.docx*。你会看到一个带黑色阴影的矩形，宽 200 pt、高 100 pt，内联于第一段落。

## 预期输出

打开 **ShadowShape.docx** 时，文档显示：

- 一个包含矩形形状的单段落。
- 矩形拥有轻微的黑色阴影，偏移 5 pt。
- 形状尺寸与步骤 2 中设置的尺寸相匹配。
- 除非手动添加，否则不会出现额外文本。

如果形状未出现，请再次确认已引用正确的 Aspose.Words 版本，并且许可证（或试用版）已激活。

## 常见问题与变体

| Question | Answer |
|----------|--------|
| *我可以将阴影颜色改为除黑色之外的其他颜色吗？* | 当然可以——设置 `rectangleShape.Shadow.Color = Color.Blue;` 或任意 `System.Drawing.Color`。 |
| *如果需要更大的矩形怎么办？* | 调整 `Width` 和 `Height` 值。记住它们的单位是点；72 pt = 1 in。 |
| *可以将形状放在绝对位置吗？* | 可以——使用 `WrapType = WrapType.Absolute` 并设置 `Top`/`Left` 属性。 |
| *这在 .NET Core 上能工作吗？* | 能。Aspose.Words 跨平台，只需为 .NET Standard 安装相应的 NuGet 包。 |
| *我能在矩形内部添加文字吗？* | 不能直接实现；需要插入 `TextBox` 形状来代替普通矩形。 |

## 完整可运行示例（复制粘贴即用）

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

运行程序，导航至 `C:\Temp\ShadowShape.docx`，即可看到如描述所示带阴影的矩形。

## 结论

你现在已经掌握了使用 Aspose.Words 在 Word 文件中 **创建矩形形状**、**设置形状大小**、**添加阴影**，以及最终 **保存 Word 文档** 的完整步骤。整个过程——从 **how to create document** 到持久化结果——只需几行 C# 代码，并且可以扩展以实现更复杂的布局。

准备好迎接下一个挑战了吗？尝试将矩形换成圆角形状，实验不同的阴影颜色，或将形状嵌入表格单元格中。每一次微调都在巩固我们在本指南中覆盖的核心概念。

如果你觉得本指南对你有帮助，请分享、留下你的变体评论，或浏览我们关于 Word 自动化的其他教程，例如插入图像或使用 Aspose.Words 生成表格。祝编码愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}