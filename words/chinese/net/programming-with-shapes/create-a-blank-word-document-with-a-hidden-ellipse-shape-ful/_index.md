---
category: general
date: 2026-07-29
description: 创建一个空白的 Word 文档，并学习如何使用 Aspose.Words 在 C# 中隐藏形状、创建隐藏对象以及创建椭圆形。附带一步一步的代码示例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- how to hide shape
- create hidden object
- create ellipse shape
language: zh
lastmod: 2026-07-29
og_description: 创建一个空白的 Word 文档并立即隐藏形状。学习使用 Aspose.Words 在 C# 中创建隐藏对象并绘制椭圆形状。
og_image_alt: Hidden ellipse shape inserted into a blank Word document
og_title: 创建带隐藏椭圆形的空白 Word 文档 – C# 教程
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  headline: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  type: TechArticle
- description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  name: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  steps:
  - name: What if the target Word version doesn’t support hidden shapes?
    text: The `Hidden` flag is part of the Office Open XML spec and is respected by
      Word 2007+ and LibreOffice. Older formats (e.g., `.doc`) ignore the flag, so
      always save as `.docx` when you need reliable hiding.
  - name: Can I hide other types of objects (pictures, tables)?
    text: Yes. Any node derived from `Shape`—including pictures, text boxes, and even
      SmartArt—exposes the `Hidden` property. Just set it to `true` before insertion.
  - name: Does hiding a shape affect document performance?
    text: Negligibly. The shape is stored as XML markup, and Word skips rendering
      hidden objects during layout. If you embed many hidden objects, the file size
      grows, but rendering stays fast.
  - name: How does this differ from using a bookmark or comment as a marker?
    text: Bookmarks are invisible by design, but they’re meant for navigation, not
      visual placeholders. Comments appear in the margin. A hidden shape gives you
      a visual object (size, position) that you can later reveal or manipulate, which
      is handy for templating scenarios.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: 创建带隐藏椭圆形的空白 Word 文档 – 完整 C# 指南
url: /zh/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 完整指南创建带隐藏椭圆形的空白 Word 文档

是否曾需要创建一个 **空白 Word 文档**，随后在其中隐藏一个形状？也许你在生成模板时，需要让某些标记保持不可见，直到后续步骤。本教程将逐步演示 **如何隐藏形状**、**如何创建隐藏对象**，以及 **如何使用 Aspose.Words for .NET 创建椭圆形**。完成后，你将拥有一段可直接运行的 C# 代码片段，生成包含不可见椭圆的 DOCX 文件。

## 你将学到

- 使用 Aspose.Words 初始化一个全新的空白 Word 文档。  
- 构建椭圆形，设置其尺寸并定位到页面上。  
- 将形状标记为隐藏，使其在屏幕和打印时均不可见。  
- 将结果保存到磁盘，并验证隐藏对象确实不可见。  

除 Aspose.Words 外无需其他外部库，代码适用于 24.10 或更高版本（`Hidden` 属性在该版本中引入）。让我们开始吧。

![隐藏椭圆形在空白 Word 文档中的示意图](https://example.com/hidden-ellipse.png "已插入空白 Word 文档的隐藏椭圆形")

## 创建空白 Word 文档并插入隐藏椭圆形

第一步是创建一个全新的文档。把 `Document` 看作空白画布；`DocumentBuilder` 则是你的画笔。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder to edit it.
Document document = new Document();               // This is your blank word document.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **为什么要从空白文档开始？**  
> 干净的画布确保没有已有内容干扰你即将添加的隐藏形状。这也让示例更容易复制粘贴到任何项目中。

## 如何隐藏形状：设置 Hidden 属性

Aspose.Words 24.10 在 `Shape` 上引入了 `Hidden` 标志。将其设为 `true` 时，Word 会将该形状视为批注——在 UI 和打印时完全不可见。

```csharp
// Step 2: Create an ellipse shape and set its size and position.
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width = 100;   // Width in points
ellipseShape.Height = 80;   // Height in points
ellipseShape.Left = 150;    // Horizontal offset from the left margin
ellipseShape.Top = 150;     // Vertical offset from the top margin

// Step 3: Hide the shape so it does not appear when the document is viewed or printed.
ellipseShape.Hidden = true;   // This is the key to "how to hide shape"
```

> **小技巧：** 如果以后需要以编程方式显示该形状，只需切换 `ellipseShape.Hidden = false;` 并重新保存文档。

## 创建隐藏对象：将形状插入文档

现在椭圆已经准备好并设为隐藏，我们将在构建器当前光标位置插入它。构建器的位置默认在第一个段落的起始位置，这对空白文档来说正好合适。

```csharp
// Step 4: Insert the hidden shape into the document at the current builder position.
builder.InsertNode(ellipseShape);
```

> **如果需要将形状放在特定页面怎么办？**  
> 在调用 `InsertNode` 之前先将构建器移动到目标页面（`builder.MoveToDocumentEnd();` 或 `builder.MoveToPage(pageNumber);`）。

## 保存包含隐藏形状的文档

最后，将文件写入磁盘。输出将是一个标准 DOCX，任何 Word 处理器都能打开——只是椭圆保持不可见。

```csharp
// Step 5: Save the document containing the hidden shape.
document.Save("YOUR_DIRECTORY/HiddenShape.docx");
```

> **预期输出：** 在 Microsoft Word 中打开 `HiddenShape.docx`。你看不到任何图形，但文件大小会比真正的空文档略大，因为隐藏的椭圆已存储在 XML 中。

## 编程方式验证隐藏椭圆（可选）

如果想再次确认形状确实被隐藏，可以加载已保存的文件并检查形状的 `Hidden` 属性：

```csharp
Document loaded = new Document("YOUR_DIRECTORY/HiddenShape.docx");
Shape loadedShape = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
Console.WriteLine($"Is shape hidden? {loadedShape.Hidden}"); // Should print True
```

运行此代码片段会打印 `True`，确认隐藏对象在保存‑加载循环中仍然存在。

## 边缘情况与常见问题

### 如果目标 Word 版本不支持隐藏形状怎么办？

`Hidden` 标志是 Office Open XML 规范的一部分，Word 2007+ 和 LibreOffice 都会尊重它。旧格式（如 `.doc`）会忽略该标志，因此在需要可靠隐藏时请始终保存为 `.docx`。

### 我可以隐藏其他类型的对象吗（图片、表格）？

可以。任何从 `Shape` 派生的节点——包括图片、文本框，甚至 SmartArt——都暴露 `Hidden` 属性。只需在插入前将其设为 `true`。

### 隐藏形状会影响文档性能吗？

影响可以忽略不计。形状以 XML 标记存储，Word 在布局时会跳过渲染隐藏对象。如果嵌入大量隐藏对象，文件体积会增大，但渲染仍保持快速。

### 这与使用书签或批注作为标记有什么区别？

书签本身就是不可见的，但它们用于导航，而不是视觉占位。批注会出现在页边。隐藏形状为你提供一个可视对象（大小、位置），以后可以显示或操作，非常适合模板场景。

## 完整可运行示例

下面是完整的、可直接复制粘贴的程序示例。它包含所有 using 指令、隐藏椭圆的创建以及验证步骤。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HiddenEllipseDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Build the ellipse shape.
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width = 100,
            Height = 80,
            Left = 150,
            Top = 150,
            Hidden = true               // ← how to hide shape
        };

        // 3️⃣ Insert the hidden shape.
        builder.InsertNode(ellipse);

        // 4️⃣ Save the file.
        string outPath = "HiddenEllipse.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");

        // 5️⃣ Optional: Verify that the shape is hidden.
        Document loaded = new Document(outPath);
        Shape loadedEllipse = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
        Console.WriteLine($"Is the ellipse hidden? {loadedEllipse.Hidden}");
    }
}
```

运行程序后会在执行文件夹中生成 `HiddenEllipse.docx`。打开它，你会看到一页完全正常的空白页面，但隐藏的椭圆正悄悄地存在其中。

## 小结

我们已经介绍了如何 **创建空白 Word 文档**、**隐藏形状**、**创建隐藏对象**，以及 **创建椭圆形**，全部只需几行 C# 代码。关键在于 `Shape` 的 `Hidden` 属性，它可以将任何可视元素转化为不影响 Word 兼容性的不可见标记。

## 接下来可以做什么？

- **为隐藏形状设置样式**（填充颜色、线条样式），这样在以后显示时即可呈现预期外观。  
- **将隐藏形状与书签结合**，构建可随时打开或关闭的动态模板。  
- **探索其他形状类型**——矩形、箭头，甚至自定义 SVG 路径——只需将 `ShapeType.Ellipse` 替换为相应类型。  

尽情实验：更改大小、移动位置，或插入多个隐藏椭圆。相同的模式同样适用于任何需要隐藏的 Aspose.Words 形状。

如果遇到问题或有扩展思路，欢迎在下方留言。祝编码愉快！

## 接下来该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助你进一步掌握 API 功能并探索在项目中的其他实现方式。

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}