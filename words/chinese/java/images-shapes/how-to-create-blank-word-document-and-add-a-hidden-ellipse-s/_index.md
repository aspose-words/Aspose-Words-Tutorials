---
category: general
date: 2026-09-21
description: 使用 C# 创建带有隐藏椭圆的空白 Word 文档。学习如何在 Word 中隐藏形状并以编程方式生成隐藏形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: zh
lastmod: 2026-09-21
og_description: 使用 C# 创建带有隐藏椭圆的空白 Word 文档。本指南展示了如何在 Word 中隐藏形状以及以编程方式构建隐藏形状。
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: 在 C# 中创建带隐藏椭圆形状的空白 Word 文档
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: 如何在 C# 中创建空白 Word 文档并添加隐藏的椭圆形
url: /zh/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中创建空白 Word 文档并添加隐藏的椭圆形状

如果您需要 **创建空白 Word 文档** 并包含一个不可见的图形，本指南将精确演示操作步骤。教程结束时，您将拥有一个看似空白但实际上存有隐藏椭圆形状的 .docx 文件。

我们将使用 Aspose.Words for .NET 来构建文档、插入椭圆、隐藏它并保存文件。步骤还涵盖了 **how to create ellipse** 对象、在 Word 中 **hide shape in Word** 的正确方法，以及适用于任何 .NET 项目的 **create hidden shape** 代码。

## 前置条件

在开始之前，请确保您已具备：

* 已安装 .NET 6.0 SDK 或更高版本  
* Visual Studio 2022（或任何 C# 编辑器）  
* Aspose.Words for .NET 许可证或免费评估版  
* 对 C# 语法有基本了解  

除 `Aspose.Words` 外无需其他 NuGet 包。

## 使用 Aspose.Words 创建空白 Word 文档

第一步是生成一个空的 Word 文件。这为我们提供了一个干净的画布，后续可以在其上插入隐藏的图形。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**为什么从空白文档开始** – 从空文件开始可确保没有不需要的内容干扰隐藏形状。同时保持文件大小最小，这在文档后续用作模板时非常有用。

## 如何在空白文档中创建椭圆

接下来我们需要一个 `DocumentBuilder` 来添加内容。该构建器让我们能够精确地将形状放置在所需位置。

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**说明** – `ShapeType.Ellipse` 告诉 Aspose.Words 绘制一个近似圆形的图形。宽度和高度以点为单位（1 pt ≈ 1/72 英寸）。您可以调整这些数值以满足设计需求。

## 在 Word 中隐藏形状，使其不出现在布局中

被隐藏的形状仍然存在于文档的 XML 中，这对于元数据、条件格式或后续的编程修改都很有用。要隐藏它，只需将 `Hidden` 属性设为 `true`。

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**为什么隐藏形状** – 隐藏的形状会被布局引擎忽略，因此页面看起来完全空白。但形状数据仍然保留，可用于存储标记、书签或下游进程可读取的自定义 XML。

## 保存包含隐藏形状的文档

最后我们将文件写入磁盘。保存的 `.docx` 在 Microsoft Word 中打开时没有可见内容，但隐藏的椭圆仍然存在。

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**验证** – 在 Word 中打开生成的文件，然后按 `Alt+F9` 切换域代码，接着 `Ctrl+A` → `Ctrl+Shift+F9` 查看隐藏对象。您会在文档的 XML (`word/document.xml`) 中看到椭圆，但页面上没有任何显示。

---

## 完整、可运行的示例

下面是完整的程序，您可以复制粘贴到新的控制台项目中。它包含所有 `using` 指令和 `Main` 方法，您可以直接运行，无需额外的脚手架。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**预期输出** – 运行程序后，控制台会打印文件路径，生成的 Word 文件不包含可见对象。如果使用压缩工具检查文档（`.docx` 本质上是 zip 压缩包），您会在 `word/document.xml` 中找到描述椭圆的 `<w:pict>` 元素。

---

## 常见变体和边缘情况

| 场景 | 需要更改的内容 | 原因/重要性 |
|----------|----------------|----------------|
| **Different shape** | 将 `ShapeType.Ellipse` 替换为 `ShapeType.Rectangle`、`ShapeType.Line` 等。 | 允许在保持相同工作流的情况下隐藏其他图形。 |
| **Multiple hidden shapes** | 多次调用 `InsertShape` 并对每个形状设置 `Hidden = true`。 | 便于嵌入一组标记或占位符。 |
| **Conditional visibility** | 将 `shape.Visible = false` 与 `shape.Hidden = true` 同时使用，以提高安全性。 | 某些旧版 Word 对 `Visible` 的处理不同；同时设置两者可覆盖所有情况。 |
| **Saving to a stream** | 将 `doc.Save(path)` 替换为 `doc.Save(stream, SaveFormat.Docx)`。 | 可直接通过 HTTP 发送文档或存储到数据库。 |
| **Applying a style** | 插入后，修改 `ellipse.FillColor`、`ellipse.LineWeight` 等属性再隐藏。 | 形状的样式会保留在 XML 中，后续取消隐藏时可用。 |

**专业提示**：始终在目标 Word 版本（例如 Word 2019、Word 365）上测试隐藏形状，因为隐藏对象与复杂页面布局交互时偶尔会出现渲染异常。

---

## 常见问题

**问：隐藏形状会影响文档大小吗？**  
答：形状的 XML 只会增加几百字节，对大多数使用场景而言可以忽略不计。文件大小基本与真正的空白文档相同。

**问：可以在以后通过代码取消隐藏形状吗？**  
答：可以。加载文档，定位形状（`doc.GetChildNodes(NodeType.Shape, true)`），并将 `shape.Hidden = false`。

**问：隐藏形状在打印时会出现吗？**  
答：不会。隐藏对象会被排除在打印布局之外，打印的页面保持空白。

**问：此方法仅兼容 Office Open XML (OOXML) 吗？**  
答：`Hidden` 属性是 OOXML 规范的一部分，任何完整实现 OOXML 的 Word 处理器（Word、LibreOffice、Google Docs）都会遵守该隐藏标记。

---

## 结论

现在您已经了解如何使用 Aspose.Words for .NET **创建空白 Word 文档**、**创建椭圆**、**在 Word 中隐藏形状**以及**创建隐藏形状**。本教程覆盖了完整的生命周期——从初始化空文件到插入、隐藏并保存形状——以及验证步骤和常见变体。

接下来，您可以探索：

* 为元数据添加隐藏文本框（将 `hide shape in word` 技术应用于文本）  
* 使用自定义 XML 部分在隐藏形状旁存储结构化数据  
* 将包含隐藏形状的文档转换为 PDF，同时保留隐藏元素  

尝试不同的形状和可见性设置，了解隐藏内容如何在 Word 文件中充当轻量级数据存储。

祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [使用 C# 在 Word 中创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [使用阴影矩形创建 Word 文档 – 步骤指南](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}