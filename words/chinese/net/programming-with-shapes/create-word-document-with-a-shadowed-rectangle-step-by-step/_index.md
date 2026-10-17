---
category: general
date: 2026-01-13
description: 使用 Aspose.Words 创建 Word 文档，并学习如何插入矩形形状、如何添加阴影以及在 C# 中为形状添加阴影。附带完整示例。
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: zh
og_description: 使用 Aspose.Words 创建 Word 文档，了解如何插入矩形形状以及如何添加阴影。请参阅完整的 C# 示例。
og_title: 创建带阴影矩形的 Word 文档 – 完整教程
tags:
- Aspose.Words
- C#
- Document Automation
title: 创建带阴影矩形的Word文档 – 步骤指南
url: /zh/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建带阴影矩形的 Word 文档 – 步骤指南

是否曾需要 **创建 word 文档**，其中包含一个精美的阴影矩形，却不知从何入手？你并不孤单——许多开发者在首次使用 Aspose.Words 时都会遇到同样的难题。

在本教程中，我们将逐步演示如何 **创建 word 文档**，**插入矩形形状**，以及 **如何添加阴影** 使形状更加突出。完成后，你将拥有一段可直接在任何 .NET 项目中使用的 C# 示例代码。

## 你将学到

- 插入形状（矩形）到 Word 文件的完整代码。
- 调整属性以 **添加形状阴影** 并控制其外观的方法。
- 如何保存结果并验证阴影是否可见。
- 一些实用技巧和边缘情况的注意事项，帮助你避免后期的头疼。

无需查阅外部文档——所有内容均在此处。

## 前提条件

在开始之前，请确保你已经具备以下条件：

1. 已安装 **.NET 6.0**（或任意较新的 .NET 版本）。  
2. 拥有 Aspose.Words for .NET 的 **许可证**，或使用免费评估模式进行测试。  
3. 开发环境——Visual Studio 2022 表现良好，任何能够编译 C# 的编辑器均可。

就这些。除 `Aspose.Words` 之外无需额外的 NuGet 包。

## 第一步 – 创建项目并引用 Aspose.Words

首先，新建一个控制台应用并添加 Aspose.Words 包：

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **专业提示：** 如果使用免费试用版，请记得调用 `License.SetLicense` 并提供许可证文件；否则库会添加水印。

## 第二步 – 初始化 Document Builder

现在我们开始实际的 **创建 word 文档** 过程。`Document` 类提供空白画布，`DocumentBuilder` 让我们在其上绘制。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

为什么需要 Builder？它抽象了底层的 OpenXML 细节，让你专注于 *想要的效果* 而不是 *文件结构的实现方式*。这正是 **如何插入形状** 的核心。

## 第三步 – 插入矩形形状

下面我们真正 **插入矩形形状**。矩形尺寸为 150 × 100 点（约 2 英寸 × 1.3 英寸）。

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

`InsertShape` 方法返回一个 `Shape` 对象，后续可以进一步自定义。此时矩形仅是一个纯白实心框——尚未添加阴影。

## 第四步 – 如何添加阴影（Add Shape Shadow）

一旦知道要修改哪些属性，添加阴影其实非常简单。`ShadowFormat` 对象控制可见性、颜色、模糊、偏移和大小。

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

上述代码用通俗的方式回答了 **如何添加阴影**：打开可见性、选择颜色、调整透明度、偏移、模糊和大小。你可以自行实验这些数值，以获得浓重的投影或轻柔的阴影。

### 常见变体

- **不同颜色：** 使用 `Color.Black` 获得经典投影，或 `Color.BlueViolet` 实现时尚效果。  
- **零模糊：** 将 `BlurRadius = 0` 可得到锐利、清晰的边缘。  
- **更大偏移：** 增大 `OffsetX`/`OffsetY` 可让阴影离形状更远。

## 第五步 – 保存文档并验证

最后，将文档写入磁盘。生成的文件是标准的 `.docx`，任何现代 Word 处理器均可打开。

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

在 Microsoft Word 中打开生成的 *ShadowRectangle.docx*。你应能看到一个带有柔和灰色阴影、向右下偏移的矩形——正是代码所指定的效果。

> **预期输出：** 一个单页 Word 文件，包含 150 × 100 点的矩形，阴影为 30 % 透明的灰色，偏移 5 pt，模糊 4 pt，大小为形状的 75 %。

## 完整可运行示例

将所有内容整合在一起，以下是完整的、可直接运行的程序：

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

运行程序（`dotnet run`），即可得到一个带有精美阴影矩形的全新 Word 文件——非常适合报告、证书或任何需要视觉提示的场景。

## 常见问题 (FAQs)

**问：我可以插入其他形状（椭圆、星形）并使用相同的阴影代码吗？**  
答：完全可以。`InsertShape` 方法接受任意 `ShapeType` 枚举值。获取 `Shape` 实例后，`ShadowFormat` 属性的使用方式完全相同，因此 **如何添加阴影** 与形状类型无关。

**问：如果需要在形状的两侧都显示阴影怎么办？**  
答：Aspose.Words 只支持每个形状单一的投影。若想模拟双侧阴影，可复制形状两次，分别设置不同的偏移，并将其中一个的 `ShadowFormat.Visible` 设为 `false`，保留另一个的阴影可见。

**问：这在 .NET Framework 4.8 上能工作吗？**  
答：可以。API 与版本无关，只需引用对应目标框架的 Aspose.Words DLL 即可。

## 技巧与陷阱

- **务必将 `Visible = true`**——否则阴影属性会被忽略。  
- **透明度取值范围为 0.0（不透明）到 1.0（完全透明）。** 常见错误是写成 `30` 而不是 `0.3`。  
- **将文件保存到只读文件夹会抛出异常。** 请确保输出目录具有写入权限。

## 后续步骤

既然已经掌握了 **如何插入形状**、**添加形状阴影**，以及使用 Aspose.Words **创建 word 文档**，你可以进一步探索：

- 在矩形内部使用 `builder.InsertParagraph()` 插入 **文本**。  
- 应用 **渐变填充** 或 **图案边框**，实现更丰富的视觉效果。  
- 自动生成多页文档，每页包含不同的阴影形状，以构建动态报告。

尽情实验——改变阴影的颜色、模糊度或大小，都能显著提升文档的观感。

---

*准备好投入生产了吗？获取代码，微调参数，瞬间让你的 Word 文件焕发专业光彩。*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}