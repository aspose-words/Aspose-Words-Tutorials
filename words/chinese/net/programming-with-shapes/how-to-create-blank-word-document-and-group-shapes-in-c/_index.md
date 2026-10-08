---
category: general
date: 2026-10-07
description: 在 C# 中创建空白 Word 文档，并学习添加矩形形状、插入图片形状以及将多个形状分组，以用于动态报告。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: zh
lastmod: 2026-10-07
og_description: 使用 Aspose.Words 在 C# 中创建空白 Word 文档。学习如何添加矩形形状、插入图片形状，以及将多个形状组合，以制作专业文档。
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: 使用 C# 创建空白 Word 文档并对形状进行分组 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 如何在 C# 中创建空白 Word 文档并对形状进行分组
url: /zh/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中创建空白 Word 文档并对形状进行分组

如果您需要以编程方式 **创建空白 Word 文档**，本指南将为您提供完整步骤。您将看到如何 **添加矩形形状**、**插入图片形状**，以及如何 **将多个形状分组**，以便在后续 **向 Word 添加图片** 时，它们能够作为单个对象一起操作。

从代码操作 Word 文件可能会让人望而生畏，但 Aspose.Words 让整个过程变得简洁明了。完成本教程后，您将拥有一个可复用的 C# 代码片段，能够生成一个包含分组矩形和徽标的干净、空白的 Word 文件。您可以将生成的文档嵌入发票、报告或任何自动化文档工作流中。

## 前置条件

在开始之前，请确保您具备以下条件：

* .NET 6.0 或更高版本（该代码同样适用于 .NET Framework 4.7+）。  
* 有效的 Aspose.Words for .NET 许可证或免费评估密钥。  
* 一个图片文件（例如 `logo.png`），放置在代码可引用的文件夹中。  
* Visual Studio 2022 或任意支持 C# 的 IDE。

除 `Aspose.Words` 之外，无需额外的 NuGet 包。

## 使用 Aspose.Words 创建空白 Word 文档的方法

第一步始终是 **创建空白 Word 文档**。该对象将承载后续的所有形状。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 代表整个 `.docx` 文件。此时文件为空，满足 *创建空白 Word 文档* 的需求。

## 创建容器以分组多个形状

对形状进行分组后，您可以一起移动、旋转或调整大小。Aspose.Words 提供了 `GroupShape` 类来实现此功能。

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

`Bounds` 矩形决定了分组在页面上的位置。将分组放置在第一个段落中，可确保 **创建空白 Word 文档** 后立即包含一个可视容器。

## 在分组中添加矩形形状的方法

常见需求是 **添加矩形形状** 作为背景或边框。下面的代码创建一个矩形并将其加入前面定义的分组。

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

由于矩形位于 `GroupShape` 内部，它会随您后续添加的其他形状一起移动。这正是 **分组多个形状** 功能的核心。

## 在分组中插入图片形状的方法

接下来，您将 **插入图片形状**（徽标），并将其放置在矩形旁边。这演示了 **向 Word 添加图片** 的工作流。

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

`SetImage` 方法读取文件并直接嵌入 Word 文档，确保即使源文件被移动，图片仍然保留。这完成了 **插入图片形状** 步骤，并实现了 **向 Word 添加图片** 的需求。

## 保存文档

最后，将文件持久化到磁盘。保存后的文件包含空白文档、分组矩形以及嵌入的徽标。

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

当您在 Microsoft Word 中打开 `GroupShape.docx` 时，会看到一个包含浅灰色矩形和并排徽标的单一分组。选中分组的任意部分即可移动或调整整个集合，证明这些形状已经成功 **分组多个形状**。

## 完整、可运行的示例

下面是完整的程序代码，您可以复制、粘贴并运行。将 `YOUR_DIRECTORY` 替换为您机器上实际存在的绝对或相对路径。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### 预期输出

* 在 `YOUR_DIRECTORY` 中生成一个名为 `GroupShape.docx` 的文件。  
* 在 Word 中打开该文件时，会看到一个包含左侧灰色矩形和右侧 `logo.png` 的单一视觉分组。  
* 选中该视觉分组的任意部分即可移动或调整整个集合，确认形状已正确 **分组多个形状**。

## 常见问题与边缘情况处理

| 问题 | 答案 |
|---|---|
| **我可以向同一分组中添加超过两个形状吗？** | 可以。对每个额外的 `Shape` 调用 `group.AppendChild(yourShape)` 即可。分组可以容纳任意数量的绘图对象。 |
| **如果图片文件缺失会怎样？** | `SetImage` 会抛出 `FileNotFoundException`。请将调用包装在 try‑catch 块中，并提供回退方案（例如占位形状）。 |
| **是否需要为形状设置 `WrapType`？** | 默认情况下形状为内联。如果需要浮动行为，可在加入分组前设置 `picture.WrapType = WrapType.Inline;` 或其他换行模式。 |
| **文档尺寸如何影响分组的边界？** | `Bounds` 矩形使用点作为单位（1 pt ≈ 1/72 in）。如果将分组放置在不同的页面布局（如 A4 与 Letter）上，请相应调整尺寸。 |
| **我能在另一个文档中复用同一分组吗？** | 可以。使用 `GroupShape cloned = (GroupShape)group.Clone(true);` 克隆分组，然后插入到其他 `Document` 中。 |

## 专业技巧

* **复用 `DocumentBuilder`** 在分组前后添加文本。它会自动遵循当前光标位置。  
* **设置 `Shape.StrokeColor`** 以在矩形周围显示可见边框。  
* **使用高分辨率 PNG** 作为徽标，以避免在放大时出现像素化。

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并探索在项目中的其他实现方式。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}