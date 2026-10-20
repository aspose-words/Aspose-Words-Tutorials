---
category: general
date: 2026-09-27
description: 在 Java 中创建空白 Word 文档并使用 Aspose.Words 对形状进行分组。学习设置形状大小、设置形状填充颜色以及向组中追加子形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: zh
lastmod: 2026-09-27
og_description: 使用 Aspose.Words 在 Java 中创建空白 Word 文档。本教程展示了如何在 Word 中对形状进行分组、设置形状大小、设置形状填充颜色以及向组中追加子形状。
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: 在 Java 中创建空白 Word 文档并对形状进行分组——逐步指南
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: 如何在 Java 中创建空白 Word 文档并对形状进行分组
url: /zh/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中创建空白 Word 文档并对形状进行分组

如果您需要以编程方式**创建空白 Word 文档**，本指南将向您展示如何使用 Aspose.Words for Java 完成此操作。您还将学习**在 Word 中对形状进行分组**、设置每个形状的大小、应用填充颜色，以及**将子对象追加到组**，使这些对象表现为一个整体。

通过代码操作 Word 文件可以避免手动格式化，并能够自动生成报告、合同或营销手册。完成本教程后，您将拥有一个可运行的 Java 程序，生成包含蓝色矩形和图像且已分组的 `.docx` 文件。

## 前提条件

在开始之前，请确保您具备以下条件：

- 已安装 Java 17（或任何近期的 JDK）。
- 用于管理依赖的 Maven 或 Gradle。
- Aspose.Words for Java 许可证（免费评估版可用于测试）。
- 一个示例图像文件（例如 `sample.jpg`），放置在代码可引用的文件夹中。

> **技巧提示：** 将图像文件放在 `resources` 目录中，并使用 `ClassLoader.getResourceAsStream` 加载，以避免硬编码的绝对路径。

## 步骤 1：创建空白 Word 文档并添加 GroupShape

第一步是实例化一个新的 `Document` 对象，它代表一个空的 Word 文件，然后插入一个 `GroupShape`。该组将作为以后添加的所有形状的容器。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*为什么这很重要：* `GroupShape` 允许您一起移动、旋转或格式化多个形状，这对于图表或水印等复杂布局至关重要。

## 步骤 2：插入矩形并**设置形状大小**

接下来，创建一个矩形，定义其尺寸，并将其添加到组中。这演示了**设置形状大小**的操作。

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*解释：* `setWidth` 和 `setHeight` 控制形状的精确大小，单位为点（1 point = 1/72 英寸）。根据布局需求调整这些数值。

## 步骤 3：为矩形**设置形状填充颜色**

使用 `setFillColor` 将矩形的背景设置为蓝色。您可以使用任何 `java.awt.Color` 常量或自定义 RGB 颜色。

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*为什么它有用：* 填充颜色有助于在视觉上区分对象，尤其是在后期将文档导出为 PDF 或打印时。

## 步骤 4：插入图像并**将子对象追加到组**

现在向同一个 `GroupShape` 添加图像。图像通过 `DocumentBuilder.insertImage` 插入，然后追加到组中，使其与矩形一起移动。

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*边缘情况：* 如果图像路径错误，Aspose.Words 会抛出 `FileNotFoundException`。请使用相对路径或从资源加载图像以避免此问题。

## 步骤 5：**保存包含分组形状的文档**

最后，将文档写入磁盘。生成的文件将包含已分组的矩形和图像。

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### 预期输出

- 在指定目录中出现名为 `GroupShape.docx` 的文件。
- 在 Microsoft Word 中打开该文件时，会看到一个空白页，上面有一个蓝色矩形和所选图像，两者被选中为单个对象（可以一起移动或调整大小）。

![创建带有分组形状的空白 Word 文档](/images/grouped-shapes.png "创建带有分组形状的空白 Word 文档")

*上面的截图演示了新创建的 Word 文档中最终的分组形状。*

## 常见变体和附加提示

| 情形 | 处理方法 |
|-----------|-----------------|
| **多个图像** | 使用 `builder.insertImage` 插入每个图像，并对每个图像调用 `group.appendChild(picture)`。 |
| **不同的形状类型** | 在构造 `Shape` 对象时使用 `ShapeType.OVAL`、`ShapeType.LINE` 等。 |
| **更改组位置** | 添加完所有子对象后，设置 `group.setLeft(x)` 和 `group.setTop(y)` 以移动整个组。 |
| **导出为 PDF** | 分组后调用 `doc.save("output.pdf")`；PDF 将保留分组关系。 |
| **许可证强制** | 使用评估版时会出现水印。安装有效许可证即可去除水印。 |

## 结论

现在您已经掌握了如何**创建空白 Word 文档**、插入**GroupShape**、**设置形状大小**、**设置形状填充颜色**以及**将子对象追加到组**，并使用 Aspose.Words for Java 实现这些操作。此模式可帮助您构建复杂的程序化布局，随后可在 Word 中编辑或导出为其他格式。

接下来，您可以探索如何使用文本框**在 Word 中对形状进行分组**、为形状添加超链接，或自动生成多页报告。原理相同——只需创建更多形状、配置属性并追加到同一组即可。

祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中尝试替代实现方式。每篇资源均提供完整可运行的代码示例和逐步解释。

- [使用 Java 在 Word 中创建矩形形状 – 完整指南](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [使用 Java 创建 Word 文档 – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}