---
category: general
date: 2026-07-20
description: 使用 Aspose.Words 在 Java 中创建空白 Word 文档。学习如何创建组、插入矩形形状以及在形状中嵌入图像。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: zh
lastmod: 2026-07-20
og_description: 使用 Aspose.Words 在 Java 中创建空白 Word 文档。本指南展示了如何创建组、插入矩形形状以及在形状中嵌入图像，以实现动态
  Word 文件。
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: 使用分组形状创建空白 Word 文档 – Java 指南
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: 创建带有分组形状的空白 Word 文档 – Java 指南
url: /zh/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建空白 Word 文档并包含分组形状 – Java 指南

是否曾想过如何 **创建空白 Word 文档** 并且已经包含一个精美的分组形状？也许您正在构建报告模板，或者需要一个用于徽标和说明的占位符。无论哪种情况，这个问题都很常见：您从一个空文件开始，然后必须添加一个组，在内部放置一个矩形，最后嵌入一张图片——全部通过代码实现。

在本教程中，我们将逐步演示一个完整的、可直接运行的 Java 示例，正好实现上述功能。您将学习 **how to create group**、**insert rectangle shape** 和 **add image word document** 在同一组内的用法。完成后，您将拥有一个看起来像精致模板的 Word 文件，随时可以进一步自定义。

> **您将获得：** 一个完整可运行的 Java 类、逐步解释、处理文件路径的技巧以及预期输出的预览。无需外部文档——所有内容都在这里。

---

## 创建空白 Word 文档 – 步骤概览

我们首先需要的是一个真正的空白 Word 文件。Aspose.Words 让这变得非常简单：只需使用默认构造函数实例化 `Document` 类。这会为您提供一个干净的画布，相当于在 Word 中点击 **New → Blank document**。

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **为什么要从空白文档开始？**  
> 空白文档确保没有隐藏的样式或节会干扰您后续添加的形状。它还能保持文件大小最小化，这在批量生成数十个文件时非常方便。

## 如何创建分组并添加形状

**group shape** 本质上是一个容器，可以容纳多个子形状——可以把它想象成绘图对象的文件夹。通过分组，您可以一次性移动、调整大小或旋转整个集合。

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

`insertGroupShape` 方法返回一个 `GroupShape` 对象，我们将其用作矩形和图像的父对象。尺寸以点为单位（1 点 = 1/72 英寸），因此 200 点大约相当于 2.78 × 2.78 英寸的框。

**技巧提示：** 如果需要组透明，请在创建后设置 `group.setFillColor(Color.getWhite());`。

现在组已经存在，我们需要告诉 builder 接下来形状放置的位置。builder 的光标必须定位在组的第一个段落内部。

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

## 在组内插入矩形形状

矩形常用作文本占位符或视觉提示。将其作为组的 **first child** 添加，可确保它位于后续图像的后面。

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

矩形继承组的坐标系，因此其 100 × 50 点的尺寸默认会居中。您可以进一步设置样式——添加边框、更改填充颜色或应用阴影——只需访问返回的 `Shape` 对象即可。

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

## 添加图像到 Word 文档 – 在形状中嵌入图像

现在进入有趣的部分：**embed image in shape**。我们将在同一组中插入 JPEG 图片作为第二个子对象。由于光标仍在组内，图像会自动成为子节点。

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

如果找不到图像文件，Aspose.Words 会抛出 `FileNotFoundException`。为避免此情况，请将 `sample.jpg` 放在项目的工作目录中，或使用绝对路径。

**如果需要不同的图像格式怎么办？**  
Aspose.Words 支持 PNG、BMP、GIF、TIFF，甚至 SVG。只需更改文件扩展名，库会自动处理转换。

## 保存文档并查看结果

最后，我们将内存中的文档持久化到磁盘。生成的 `.docx` 将包含一个页面，其中的分组形状包含矩形和图像。

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

当您在 Microsoft Word 中打开 `output.docx` 时，应该会看到左上角有一个 200 × 200 点的组。组内，顶部有一个浅灰色矩形，紧接其下是您指定的图片，完美对齐。

![Grouped shape example](grouped-shape.png){:alt="空白 Word 文档的截图，包含一个分组形状，其中有矩形和嵌入的图像"}

## 常见变体和边缘情况处理

| 场景 | 需要更改的内容 | 重要原因 |
|----------|----------------|----------------|
| **不同的组大小** | 调整 `insertGroupShape(width, height)` 的参数 | 更大的组可以容纳更复杂的布局。 |
| **多个图像** | 每次移动到组的段落后，重复调用 `builder.insertImage()` | 每次调用都会添加一个新子对象；您也可以使用 `Shape.setLeft()` / `setTop()` 来定位它们。 |
| **动态图像路径** | 使用 `String.format("images/%s.jpg", imageName)` | 使代码在批处理时可复用。 |
| **保存为 PDF** | 将 `doc.save("output.pdf")` 替换 | Aspose.Words 可以即时转换，直接生成 PDF。 |
| **旋转组** | `group.setRotation(45);` | 对装饰性水印或样式化标题很有用。 |

## 预期输出与验证

运行该类后：

1. `output.docx` 出现在项目文件夹中。  
2. 打开文件会显示一个包含分组形状的单页。  
3. 在组内，矩形位于左上角，图像紧随其下。  
4. 在 Word 中选中该组会高亮两个子对象，确认它们真的被分组。

如果上述任何步骤失败，请再次检查图像路径并确保 Aspose.Words JAR 已加入类路径。

## 结论

您现在已经了解 **how to create blank word document** 并通过包含矩形和嵌入图片的分组形状来丰富它。掌握了 **how to create group**、**insert rectangle shape** 和 **add image word document** 后，您可以完全通过代码构建复杂的 Word 模板——无需手动调整。

准备好接受下一个挑战了吗？尝试在同一组内添加文本框，或尝试不同的形状样式以匹配企业品牌。您甚至可以生成一个完整的报告库，每个文档都以此布局开始。

祝编码愉快，欢迎在下方评论中分享您的各种变体！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题，帮助您进一步学习。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [创建 Word 文档 Java – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [如何使用 Aspose.Words for Java 的 DocumentBuilder 创建表单字段并添加内容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [如何使用 Aspose.Words for Java 创建 PDF 文档 | 文档处理 API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}