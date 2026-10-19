---
category: general
date: 2026-05-26
description: 使用 C# 和 Aspose.Words 创建 Word 文档，插入矩形形状，设置填充颜色，并添加阴影效果——一步一步的指南。
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: zh
og_description: 使用 Aspose.Words 在 C# 中创建 Word 文档。学习如何插入矩形形状、设置填充颜色以及添加阴影效果。
og_title: 创建 Word 文档 – 在 C# 中插入矩形形状和阴影
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 创建 Word 文档 – 在 C# 中插入矩形形状和阴影
url: /zh/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建 Word 文档 – 插入矩形形状和阴影（C#）

有没有想过如何在不打开 Microsoft Word 的情况下**创建 Word 文档**？你并不是唯一有此需求的人。在许多自动化场景中——比如发票、合同或批量报告生成——你需要一种可靠的方式来生成 .docx 文件、在其中放置形状、为其着色，甚至添加阴影，以获得更专业的外观。

在本教程中，我们将一步步演示：使用 Aspose.Words for .NET **创建 Word 文档**、**插入矩形形状**、应用填充颜色，并**添加阴影**。完成后，你将得到一个可直接保存的文件，可供后续工作流使用。

我们还会简要说明**如何插入形状**的灵活方式，以及**如何设置填充**对视觉一致性的重要性。没有冗余，只提供可复制粘贴并直接运行的代码。

## 前置条件

在开始之前，请确保你已经具备：

- .NET 6+（或 .NET Framework 4.7+）已安装。
- 有效的 Aspose.Words for .NET 许可证（或临时评估密钥）。
- Visual Studio、Rider 或任意你喜欢的 C# IDE。
- 对 C# 语法有基本了解——不需要高级技巧。

准备好了吗？那我们开始吧。

## 第一步 – 创建 Word 文档

首先需要一个空白的文档对象。这是所有内容的画布。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` 表示内存中的 .docx 文件，而 `DocumentBuilder` 提供了便捷的 API 来插入文本、表格和形状。**以这种方式创建 Word 文档**是瞬间完成的——无需 UI、无需 COM 互操作，纯 .NET 实现。

## 第二步 – 插入矩形形状

有了文档后，接下来**插入矩形形状**。`InsertShape` 方法接受 `ShapeType` 枚举、宽度和高度（单位为点）。我们将使用宽 150 × 高 80 点的矩形，大约相当于 2 × 1 英寸。

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

在幕后，Aspose 会创建一个 `Shape` 对象，将其添加到当前段落，并返回一个可以进一步设置样式的引用。这就是**如何插入形状**的核心——仅一行代码，却极其强大。

## 第三步 – 如何设置填充

没有填充的形状在白页上是不可见的。我们给它一个淡蓝色的背景。

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

你也可以使用渐变、纹理，甚至图片填充，但纯色最能保持示例的简洁。这演示了**如何设置填充**，让任何创建的形状都具备读者期望的视觉提示。

## 第四步 – 如何添加阴影

阴影可以增加深度，使形状更突出。Aspose.Words 提供了 `ShadowFormat` 对象，你可以在其中切换可见性、选择颜色，并微调模糊程度、距离和角度。

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

为什么使用这些特定的数值？45° 的角度模拟自然的左上光源，适度的模糊保持阴影柔和，较短的距离防止形状看起来与页面脱离。你可以自行实验——例如将角度改为 135°，阴影就会落到左下方。

## 第五步 – 保存文档

所有工作已完成，现在将文件写入磁盘。选择任意路径即可，只要确保文件夹已存在。

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

当你在 Microsoft Word 中打开 `ShadowShape.docx` 时，会看到一个淡蓝色的矩形，带有柔和的灰色阴影——正是我们脚本生成的效果。

## 完整工作示例

将上述所有代码组合在一起，即可得到完整的、可直接复制粘贴的程序：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### 预期结果

- 在目标文件夹中生成名为 **ShadowShape.docx** 的文件。
- 用 Word 打开后，第一页面居中显示一个淡蓝色矩形。
- 矩形投射出 45° 角的灰色阴影，呈现细腻的 3D 效果。

## 常见问题与边缘情况

**如果需要其他形状怎么办？**  
将 `ShapeType.Rectangle` 替换为任意其他枚举值（`Ellipse`、`Star`、`Arrow` 等），其余代码保持不变。

**可以在形状内部添加文字吗？**  
可以——在创建形状后，调用 `shape.AppendChild(new Paragraph(doc))`，然后插入包含文本的 `Run`。如果需要换行，请设置 `shape.TextBox` 的相关属性。

**DPI 或测量单位怎么办？**  
Aspose 使用点作为单位（1 pt = 1/72 英寸）。如果想使用厘米，可乘以 28.35（因为 1 cm ≈ 28.35 pt）。

**是否必须拥有许可证才能运行？**  
评估版会在首页添加水印。正式许可证会去除水印并解锁全部 API。

## 小技巧与注意事项

- **高级技巧：** 在插入形状前调用 `builder.MoveToDocumentEnd()`，可将形状放在文档的最末尾。
- **注意：** 将文件保存到只读文件夹会抛出 `UnauthorizedAccessException`。请确保应用拥有写入权限。
- **性能提示：** 对于批量生成（数百份文档）的场景，建议使用单个 `Document` 实例作为模板，并通过 `doc.Clone(true)` 克隆，以避免重复的初始化开销。

## 结论

现在，你已经掌握了使用 Aspose.Words for .NET **创建 Word 文档**、**插入矩形形状**、**设置填充**以及**添加阴影**的完整流程。上面的代码片段是一个自包含的解决方案，可直接嵌入任何 C# 项目，无论是控制台应用、Web API 还是后台服务。

接下来，你可以进一步探索：

- 添加多个形状并使用不同颜色。
- 使用渐变或图片填充（`shape.FillColor = ...` → `shape.FillPattern`）。
- 将形状与表格组合，实现更复杂的报表布局。

动手试一试，调整参数，让你的自动化 Word 文件只需几行代码就显得更加专业。祝编码愉快！

## 相关教程

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}