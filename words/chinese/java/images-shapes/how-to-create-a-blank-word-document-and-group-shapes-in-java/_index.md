---
category: general
date: 2026-09-24
description: 学习如何在 Java 中使用 Aspose.Words 创建空白 Word 文档，并对矩形、线条等形状进行分组。包含逐步代码示例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: zh
lastmod: 2026-09-24
og_description: 在 Java 中创建空白 Word 文档，学习如何对形状进行分组、添加矩形形状以及使用 Aspose.Words 设置形状大小。
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: 在 Java 中创建空白 Word 文档并对形状进行分组 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: 如何在 Java 中创建空白 Word 文档并对形状进行分组
url: /zh/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中创建空白 Word 文档并对形状进行分组

如果您需要**创建一个空白的 Word 文档**并随后组织多个绘图对象，本指南将逐步演示具体做法。使用 Aspose.Words for Java，您可以插入分组形状、添加矩形形状、绘制直线，并控制每个形状的大小和位置——全部在一个可运行的程序中完成。

您将逐步完成从初始化文档到保存最终 `.docx` 的全部过程。结束时，您将掌握**如何对形状进行分组**、**添加矩形形状**以及**设置形状大小**，使您的 Word 文件呈现出预期的效果。

## 前提条件

- Java 17 或更高（代码可在任何近期 JDK 上编译）
- Aspose.Words for Java 库（从 [Aspose 网站](https://products.aspose.com/words/java) 下载）
- 可将 Aspose.Words JAR 添加到类路径的 IDE 或构建工具（Maven/Gradle）
- 基本的 Java 语法知识

> **技巧提示：** 使用 Maven 进行依赖管理；在 `pom.xml` 中添加 `com.aspose:aspose-words:23.12`（或最新版本）。

## 第一步：创建空白 Word 文档

首要任务是**创建一个空白的 Word 文档**。这为您提供了一个干净的画布，后续可以在其上插入形状。

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*为什么这很重要：* `Document` 对象代表整个 `.docx` 文件。以空白文档开始可确保没有隐藏的格式影响您后续添加的形状。

## 第二步：插入分组形状 – 多对象的容器

**分组形状**充当容器，使您能够一起移动、调整大小或旋转多个形状。这是 Word 中**如何对形状进行分组**的核心。

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*说明：* `insertGroupShape` 方法创建一个 `GroupShape` 对象并将其放置在当前光标位置。随后您 `appendChild` 到该组的所有形状都将被视为一个整体。

## 第三步：添加矩形形状并设置其大小

现在我们向组中**添加矩形形状**并**精确设置形状大小**。

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*为什么需要设置形状大小：* 宽度和高度决定矩形在页面上的显示方式。`setLeft` 和 `setTop` 方法相对于组的原点定位矩形，为您提供像素级的布局控制。

## 第四步：添加直线形状并配置其尺寸

直线是另一种常见的绘图对象。我们将对直线使用类似**添加矩形形状**的逻辑，展示相同的尺寸原则同样适用。

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*关键点：* 即使直线没有高度，仍需使用 `setWidth` 来定义其长度。定位（`setLeft`、`setTop`）遵循与其他形状相同的坐标系。

## 第五步：保存包含分组形状的文档

最后，通过保存文档来持久化更改。这将生成一个 `.docx` 文件，您可以在 Microsoft Word 中打开以验证结果。

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**预期输出：** 打开 `GroupShapeDemo.docx` 时，会看到一个包含分组矩形和直线的空白页。选择任意形状都会选中整个组，从而可以一起移动它们。

## 常见问题与边缘情况处理

| Question | Answer |
|----------|--------|
| *我可以向组中添加超过两个形状吗？* | 可以。对每个额外的形状调用 `group.appendChild(yourShape)`。 |
| *如果我需要使用不同的单位（例如厘米）来设置大小怎么办？* | Aspose.Words 使用点（1 点 = 1/72 英寸）。可使用 `Points = centimeters * 28.3465` 进行转换。 |
| *在其他机器上打开文档时，组的布局会保持吗？* | 当然。所有大小和位置数据都存储在 `.docx` 文件中，使布局可移植。 |
| *我以后如何取消分组？* | 获取 `GroupShape` 对象，然后遍历 `group.getChildNodes(NodeType.SHAPE, true)`，将每个子对象移出组。 |
| *如果需要旋转整个组怎么办？* | 在保存之前使用 `group.setRotationAngle(double angleInDegrees)`。 |

## 完整、可运行的示例

下面是完整的程序，您可以复制粘贴到 IDE 中使用。它包含所有必要的导入和注释。

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

运行程序，在 Microsoft Word 中打开 `GroupShapeDemo.docx`，您将看到如描述的分组形状。

## 结论

现在，您已经了解如何使用 Aspose.Words for Java **创建空白 Word 文档**、**在 Word 中对形状进行分组**、**添加矩形形状**以及**设置形状大小**。将形状放入 `GroupShape` 中，可完全控制整体的定位、缩放和旋转——非常适合用于图表、流程图或嵌入自动化报告的自定义图形。

**下一步：**  
- 探索使用更复杂的对象（如图片或文本框）**对形状进行分组**。  
- 尝试使用 `setRotationAngle` 旋转整个组。  
- 将此技术与邮件合并结合，生成包含品牌图形的个性化文档。

欢迎将代码适配到您自己的项目中，并在评论区分享您的成果！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都提供完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [在 Word 中使用 Java 创建矩形形状 – 完整指南](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [使用 Java 创建 Word 文档 – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [使用 Aspose.Words for .NET 在 Word 文档中创建分组形状](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}