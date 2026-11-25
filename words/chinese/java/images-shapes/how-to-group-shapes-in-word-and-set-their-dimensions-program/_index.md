---
category: general
date: 2026-11-25
description: 如何使用 Java 在 Word 中对形状进行分组，以及如何使用 Aspose.Words 在 DOCX 文件中设置形状尺寸。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: zh
lastmod: 2026-11-25
og_description: 如何使用 Aspose.Words Java API 在 Word 中对形状进行分组并快速设置形状大小。请按照完整的逐步解决方案操作。
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: 在 Word 中如何对形状进行分组并设置尺寸 – Java 指南
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: 如何在 Word 中对形状进行分组并以编程方式设置其尺寸
url: /zh/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中对形状进行分组并以编程方式设置其尺寸

如果您需要**在 Word 中对形状进行分组**并控制其精确大小，本指南为您提供完整可运行的解决方案。使用 Aspose.Words for Java，您可以创建矩形、椭圆，将它们添加到 `GroupShape`，然后**设置形状尺寸**（例如宽度和高度）到同一个 DOCX 文件中。

您将学习如何：

* 从头创建一个新的 Word 文档。  
* 插入一个 `GroupShape`（版本 24.9 中的新 API）。  
* 向组中添加矩形和椭圆。  
* **使用 `setWidth` 和 `setHeight` 精确设置形状大小**。  
* 将文档保存到磁盘。

无需外部工具——只需 Java 17+、Maven 和 Aspose.Words for Java 库。

## 前置条件

* Java Development Kit 17 或更高版本。  
* 用于依赖管理的 Maven（或 Gradle）。  
* Aspose.Words for Java 24.9 或更高版本（`GroupShape` API 在 24.9 中引入）。  
* 对 Java 语法和面向对象概念有基本了解。

如果您还没有将 Aspose.Words 添加到项目中，请包含以下 Maven 依赖：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## 步骤 1：创建新文档和 DocumentBuilder

`Document` 类代表整个 Word 文件，而 `DocumentBuilder` 提供了一种便捷的方式来添加内容。

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*为什么需要这一步？*  
创建一个全新的 `Document` 为您提供了干净的画布。`DocumentBuilder` 是高级助手，允许您插入段落、表格，以及在本例中的形状。

## 步骤 2：插入 GroupShape（版本 24.9 中的新 API）

`GroupShape` 像一个容器；您添加的任何形状都会成为同一视觉组的一部分。

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*为什么使用 `GroupShape`？*  
对形状进行分组可简化一次性移动、旋转或应用格式到多个对象。该 API 在 24.9 中加入，因此旧版本无法编译此行代码。

## 步骤 3：创建矩形，设置尺寸，并将其添加到组中

这里我们演示如何为矩形 **设置形状尺寸**。

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*为什么要显式设置宽度和高度？*  
Word 以点（point）存储形状尺寸。通过调用 `setWidth` 和 `setHeight`，您可以控制精确的视觉占位，这在需要精确布局或导出为 PDF 时至关重要。

## 步骤 4：创建椭圆，设置尺寸，并添加到同一组中

相同的 **设置形状尺寸** 技术适用于任何形状类型。

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*为什么将椭圆添加到同一个 `GroupShape`？*  
两个形状将作为一个整体一起移动。这对于创建必须保持对齐的图标、徽标或复杂图表非常有用。

## 步骤 5：保存包含分组形状的文档

最后，将 DOCX 文件持久化到磁盘。

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

运行此程序会生成一个名为 **GroupShape.docx** 的文件，其中包含已分组的矩形和椭圆。使用 Microsoft Word 打开该文件时，您会看到这两个形状表现为单个对象——可以一起拖动、调整大小或旋转。

### 预期输出

* 一个包含单页的 Word 文档（`GroupShape.docx`）。  
* 一个 `GroupShape`，其中包含一个 100 × 50 pt 的矩形和一个 80 × 80 pt 的椭圆。  
* 选中任意形状都会选中整个组。

## 常见问题与边缘情况

### 如何更改分组形状的位置？

创建 `GroupShape` 后，您可以设置其 `left` 和 `top` 属性：

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

这些坐标同样以点为单位。

### 如果需要添加超过两个形状怎么办？

`GroupShape` 的工作方式类似于其他容器节点。对每个额外的形状调用 `groupShape.appendChild(yourShape)`。该 API 对子节点数量没有限制。

### 能否对单个形状应用样式（填充颜色、线宽）？

可以。每个 `Shape` 对象都公开格式化属性：

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### 代码是否兼容旧版本的 Aspose.Words？

`insertGroupShape` 方法在 24.9 版本中引入。如果您使用的是更早的版本，则需要通过节点树手动创建 `GroupShape`，这会更复杂。建议升级到新版本。

## 专业提示

* **使用点作为单位以保持一致**——Word 的内部单位是点（1/72 英寸）。从像素或厘米转换可能导致意外的尺寸。  
* **先分组后定位**——在添加完所有子形状后再定位 `GroupShape`；否则可能需要重新计算偏移。  
* **复用 DocumentBuilder**——通过在每次 `insertGroupShape` 调用前移动构建器光标（`builder.moveTo`），可以在同一文档中插入多个组。

## 结论

现在，您已经拥有一个完整的、端到端的示例，展示了如何使用 Aspose.Words for Java **在 Word 中对形状进行分组**以及**设置形状尺寸**。本教程涵盖了创建文档、插入 `GroupShape`、添加矩形和椭圆、设置它们的精确尺寸以及保存结果的全过程。

从这里您可以探索：

* 将文本框或图片添加到同一组中。  
* 使用 Word 的 SmartArt 功能（通过 API）为分组形状添加动画。  
* 将分组形状导出为 PDF 或 SVG 以供网页使用。

欢迎尝试不同的形状类型、尺寸和位置——分组为您在 Word 文档中对复杂布局提供了强大的控制能力。

## 接下来您应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在自己的项目中探索替代实现方法。

- [如何在 Java 中创建空白 Word 文档并对形状进行分组](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [如何使用 Java 在 Word 中对形状进行分组 – 完整指南](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}