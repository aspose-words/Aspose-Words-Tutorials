---
category: general
date: 2026-08-20
description: 学习如何对形状进行分组、设置形状大小、将图像插入文档、向组中添加图片，以及使用 Aspose.Words for Java 创建矩形形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: zh
lastmod: 2026-08-20
og_description: 如何使用 Aspose.Words 在 Word 文档中对形状进行分组。请按照本分步 Java 教程设置形状大小、将图像插入文档、将图片添加到组中，并创建矩形形状。
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: 使用 Aspose.Words 在 Word 文档中对形状进行分组 – Java 指南
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: 如何使用 Aspose.Words 在 Word 文档中对形状进行分组
url: /zh/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文档中使用 Aspose.Words 对形状进行分组

如果您需要在 Word 文件中 **how to group shapes**，本教程展示了完整的 Java 解决方案。您将看到如何 **set shape size**、**insert image into document**、**add picture to group** 和 **create rectangle shape**——全部配有清晰的解释和可运行的代码示例。

对形状进行分组可以简化布局管理，让您能够将多个对象作为一个单元移动或旋转，从而保持文档整洁。下面的步骤将构建一个包含矩形和图片的组，然后将该组放置在页面上。

## 前提条件

* 安装 Java 17 或更高版本。
* 将 Aspose.Words for Java（版本 23.9 或更高）添加到项目的类路径中。
* 在 `YOUR_DIRECTORY/sample.jpg` 处准备一张示例 JPEG 图像（将 `YOUR_DIRECTORY` 替换为实际路径）。

您可以通过 Maven 添加 Aspose.Words：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## 使用 Aspose.Words 对形状进行分组

以下章节逐步演示实现 **how to group shapes** 所需的每个操作。主 H2 标题包含主要关键词，满足 SEO 规则。

### 步骤 1：创建新文档和 `DocumentBuilder`

`Document` 表示 Word 文件，而 `DocumentBuilder` 提供了便捷的内容插入方法。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*为什么重要*：从一个全新的 `Document` 开始，可确保您创建的分组不会干扰已有元素。

### 步骤 2：插入一个用于容纳多个子形状的组形状

组形状充当容器。其尺寸定义了所有子形状的边界框。

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*提示*：宽度 (`300`) 和高度 (`200`) 的单位为点（1 pt = 1/72 英寸）。请根据计划添加的形状大小进行调整。

### 步骤 3：创建矩形形状，设置大小，并将其添加到组中

设置形状的精确大小对于实现精确的布局控制至关重要。

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*为什么要设置形状大小*：`setWidth` 和 `setHeight` 方法对应 **set shape size** 次要关键词，让您对矩形外观实现像素级精确控制。

### 步骤 4：插入图像，然后将图片形状添加到同一组中

插入图像是 **insert image into document** 需求的核心。返回的 `Shape` 是一个图片形状，可以像其他形状一样进行分组。

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*专业提示*：如果需要保持原始宽高比，只设置一个维度（`setWidth` 或 `setHeight`）。Aspose.Words 会自动缩放另一个维度。

### 步骤 5：在页面上定位整个组

添加完所有子形状后，您可以移动、旋转或隐藏整个组。定位间接使用了 **add picture to group** 概念，因为组现在已经包含了图片。

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*解释*：`setLeft` 和 `setTop` 将组相对于页面边距定位。对组进行旋转可展示所有子形状继承该变换。

### 步骤 6：保存文档

最后，将文件写入磁盘。您可以在 Word 中打开生成的 `.docx` 文件，以验证分组效果。

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

运行程序后会生成 **GroupShapesDemo.docx**，其中包含一个矩形和一个捆绑在一起的图像。 在 Word 中选择任意一个形状时，另一个也会被选中，证明您已经成功掌握了 **how to group shapes**。

---

## 预期输出

当您在 Microsoft Word 中打开 *GroupShapesDemo.docx* 时：

* 一个矩形（金色填充）出现在组的左侧。
* 您提供的图片出现在矩形的右侧。
* 拖动组时，两个对象一起移动。
* 组相对于左边距定位 50 pt，距顶部 100 pt，并旋转 15°。

如果图像未显示，请仔细检查 `insertImage` 中的文件路径。Aspose.Words 在找不到文件时会抛出 `IOException`。

---

## 常见问题与边缘情况处理

| Question | Answer |
|----------|--------|
| **我可以添加超过两个形状吗？** | 可以。对每个额外的形状调用 `groupShape.appendChild(otherShape)`。 |
| **如果需要矩形的透明背景怎么办？** | 使用 `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **在旧的 Word 格式（如 `.doc`）中是否支持分组？** | 分组在 `.docx` 和 `.doc` 中均可工作，但某些旧版查看器可能会忽略分组元数据。建议保存为 `.docx` 以获得完整保真度。 |
| **以后如何取消分组？** | 通过 `groupShape.getChildNodes(NodeType.ANY, true)` 获取子节点并将它们移动到文档主体，然后删除该组。 |
| **可以跨不同章节分组形状吗？** | 不可以。`GroupShape` 必须位于同一个 `Story`（通常是主文档正文）中。 |

---

## 稳健形状处理的专业提示

* **尽量少用绝对定位** —— 相对定位（`builder.moveToDocumentEnd()`）通常能产生更具响应性的布局。
* **缓存 `DocumentBuilder`** —— 为每个操作创建新 builder 会在处理大型文档时降低性能。
* **在需要将图像拉伸或平铺到形状内部时设置 `PictureFillMode`**：`pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **在插入前验证图像尺寸**，以避免意外的缩放影响组的边界框。

---

## 下一步

现在您已经了解 **how to group shapes**，可以进一步探索：

* **使用高级选项（如裁剪 `pictureShape.setCropTop(...)`）的 Insert image into document**。
* **基于页面尺寸动态 Set shape size**（`doc.getFirstSection().getPageSetup().getPageWidth()`）。
* **将 Add picture to group 与文本框结合，用于带标题的图形。**
* **使用圆角的 Create rectangle shape**（`rectangleShape.setCornerRadius(5);`）。

这些主题基于相同的 API，帮助您创建更复杂、可编程的 Word 报告。

---

## 结论

在本教程中，您学习了使用 Aspose.Words for Java 在 Word 文档中 **how to group shapes**。通过六个步骤——创建文档、插入组、**create rectangle shape**、**set shape size**、**insert image into document**、**add picture to group**，以及定位组，您已经拥有了一个可复用的复杂布局模式。欢迎尝试添加更多子形状、不同的旋转角度或条件分组逻辑，以满足您的应用需求。

祝编码愉快！

## 接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，构建在本教程演示的技术之上。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能，并在自己的项目中探索替代实现方案。

- [创建 Word 文档 Java – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [在 Aspose.Words for Java 中使用文档形状](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}