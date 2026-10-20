---
category: general
date: 2026-08-14
description: 使用 Aspose.Words 在 Java 中对 Word 进行形状分组。了解如何创建矩形形状、设置形状尺寸，以及在空白 Word 文档中对多个形状进行分组。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: zh
lastmod: 2026-08-14
og_description: 使用 Aspose.Words for Java 在 Word 中对形状进行分组。创建空白 Word 文档，生成矩形形状，设置形状尺寸，并在几分钟内将多个形状分组。
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Word 中的形状分组 – 开发者 Java 示例
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Word 中的形状分组 – 完整编程指南
url: /zh/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中对形状进行分组 – 完整编程指南

如果您需要 **在 Word 中对形状进行分组**，本教程将使用 Java 和 Aspose.Words 带您完整演示整个过程。您将学习如何 **创建空白 Word 文档**、**创建矩形形状**、**设置形状尺寸**，以及最终 **将多个形状分组** 使其表现为单个对象。

在 Word 文件中操作形状常常感觉像在没有画笔的画布上绘画。阅读完本指南后，您将拥有一段可复用的代码片段，能够直接嵌入任何 Java 项目，无论是生成报告、发票还是自定义模板。

## 您需要的环境

- Java 8 或更高版本
- Aspose.Words for Java（最新版本，例如 24.9）
- IntelliJ IDEA 或 Eclipse 等 IDE
- 基本的面向对象编程知识

以上所有前置条件均可免费安装，下面的代码只需一个 Maven 依赖即可编译：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## 第一步：创建空白 Word 文档并初始化构建器

首先必须 **创建一个空白的 Word 文档**。这为后续插入形状提供了干净的画布。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 代表整个 *.docx* 文件，而 `DocumentBuilder` 是用于插入段落、表格和形状的辅助类。初始化这两个对象是任何 Word 自动化任务的基础。

## 第二步：插入分组形状容器

**分组形状** 类似于一个文件夹，可以容纳其他形状。我们首先创建一个固定大小为 400 pt × 200 pt 的容器。

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

`insertGroupShape` 方法返回一个 `GroupShape` 对象。所有后续希望作为单一单元处理的形状都必须追加到该对象中。

## 第三步：创建矩形形状并设置形状尺寸

现在 **创建矩形形状** 对象，配置其大小，并将其定位在分组内部。此步骤还演示了如何 **精确设置形状尺寸**。

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

两个矩形共享相同的尺寸，但它们的 `left` 属性不同，因此会并排显示。您可以修改 `setTop` 和 `setLeft` 来安排任意布局。

## 第四步：保存包含已分组矩形的文档

形状放入分组后，只需保存 `Document` 即可。生成的文件将显示两个矩形，选中其中一个时会一起移动。

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

运行程序后会在工作目录生成 `GroupShape.docx`。在 Microsoft Word 中打开，选中任意一个矩形，您会发现整个组会作为一个整体移动——这正是 **在 Word 中对形状进行分组** 的预期效果。

![Group shapes in Word example](group-shapes.png){alt="Word 中的组合形状示例"}

*图示：在 Word 文档中两个矩形形状已被分组在一起。*

## 小技巧：复用同一分组形状

如果以后需要添加更多形状（例如圆形、文本框），只需保留对 `groupShape` 的引用并继续调用 `appendChild`。这样可以避免重新创建容器，并确保所有成员保持同步。

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## 边缘情况与常见问题

- **如果形状重叠怎么办？** 允许重叠；Word 会按照添加的顺序进行渲染。如需显式的层叠顺序，可使用 `setZOrder`。
- **可以跨页对形状进行分组吗？** 不能。`GroupShape` 受限于单页，因为其坐标系是相对于页面的。
- **分组后的形状会继承格式吗？** 每个子形状保留各自的格式（填充颜色、线条样式）。若要统一样式，可遍历 `groupShape.getChildNodes()` 并以编程方式设置属性。

## 完整源码供参考

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

运行程序后会生成一个 DOCX 文件，其中两个矩形已被 **分组**。选中任意矩形都会一起移动，证明您已成功 **对多个形状进行分组**。

## 结论

现在您已经掌握了使用 Java **在 Word 中对形状进行分组** 的完整流程，包括 **创建空白 Word 文档**、**创建矩形形状**、**设置形状尺寸**，以及最终 **将多个形状分组** 为单个可移动对象。此模式可扩展至任意数量的形状，并可与文本、图像或图表结合，构建丰富的程序化文档。

### 接下来可以做什么？

- 探索 **对不同类型的形状进行分组**（椭圆、箭头、文本框等）。
- 通过调用 `shape.getFillColor()` 和 `shape.getLine().setColor()` 为形状应用填充颜色或边框。
- 将分组形状插入表格单元格，以实现结构化报告。
- 将此方法与邮件合并结合，生成包含品牌图形的个性化合同。

欢迎尝试、调整尺寸或嵌入更多内容。当您熟练掌握分组后，Word 自动化脚本将变得更加灵活且易于维护。祝编码愉快！


## 接下来应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您在项目中进一步掌握 API 功能并探索替代实现方式，每篇资源均提供完整可运行的代码示例和逐步解释。

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}