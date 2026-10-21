---
category: general
date: 2026-09-11
description: 在 Word 中对形状进行分组，并使用 Aspose.Words for Java 添加矩形形状。了解如何设置形状大小、分组对象以及保存文档。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: zh
lastmod: 2026-09-11
og_description: 在 Word 中对形状进行分组，并使用 Aspose.Words for Java 添加矩形形状。本教程展示了如何设置形状大小、分组形状以及导出文档。
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: 在 Word 中对形状进行分组 – 使用 Aspose.Words 添加矩形
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: 在 Word 中对形状进行分组并使用 Aspose.Words 添加矩形
url: /zh/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中对形状进行分组并添加矩形（使用 Aspose.Words）

如果您需要在以编程方式添加矩形时 **在 Word 中对形状进行分组**，本指南提供了完整、可直接运行的解决方案。您将看到如何插入分组形状、添加矩形形状、设置形状大小，最后保存文档，以便立即查看结果。

在处理 Word 文档时，通常需要将多个对象——图片、图表或简单的几何形状——组织成一个逻辑单元。对这些对象进行分组可以更轻松地一起移动、旋转或设置样式。在本教程中，我们还将介绍 **如何添加矩形** 形状以及 **设置形状大小**，以实现完美的布局控制。

## 您将学到的内容

* 使用 Aspose.Words for Java 创建新的 Word 文档。  
* **如何对形状进行分组**，使其表现为单个对象。  
* **向分组中添加矩形形状** 并在同一分组中插入图片。  
* 为矩形和图片 **设置形状大小**。  
* 保存文档并在 Microsoft Word 中打开以验证结果。

### 前置条件

* 已安装 Java 17 或更高版本。  
* 使用 Maven 或 Gradle 管理依赖。  
* 有效的 Aspose.Words for Java 许可证（或免费评估密钥）。  
* 将图片文件（`sample.png`）放置在已知目录中（将 `YOUR_DIRECTORY` 替换为实际路径）。

---

## 使用 Aspose.Words 在 Word 中对形状进行分组的方法

第一步是创建 `Document` 和 `DocumentBuilder`。`DocumentBuilder` 为您提供了便捷的 API 来插入形状、文本和其他元素。

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **为什么重要：**`DocumentBuilder` 直接操作底层的 `Document` 对象，使您能够在不手动处理低层节点集合的情况下插入形状。

### 添加分组形状

分组形状是一个容器，可以容纳其他形状。可以把它想象成用于绘图对象的文件夹。

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

`insertGroupShape()` 方法创建一个 `GroupShape` 节点并返回它，以便您随后追加子形状。

---

## 向分组中添加矩形形状

现在我们将 **向先前创建的分组中添加矩形形状**。矩形将作为图片的背景或边框。

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **提示：** 设置 `FillColor` 和 `StrokeColor` 可以使矩形在最终文档中可见。如果省略这些属性，形状可能会呈现透明。

### 如何添加矩形

上面的代码演示了 **如何添加矩形**：通过创建 `Shape` 实例并使用 `ShapeType.RECTANGLE`，然后将其追加到 `GroupShape`。此模式同样适用于其他形状类型（例如 `ELLIPSE`、`POLYLINE`）。

---

## 为矩形和图片设置形状大小

正确的尺寸确保矩形和图片能够正确对齐。这里我们还 **为随后插入的图片设置形状大小**。

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

现在矩形和图片共享相同的尺寸（100 × 50 点）。因为它们属于同一分组，移动或旋转该分组会同时影响两个形状。

> **为什么要匹配尺寸？** 对齐尺寸可保证图片整齐地位于矩形内部，形成干净的“带框图片”效果。

---

## 保存文档并查看结果

最后，我们将文档写入磁盘。用 Microsoft Word 打开文件即可看到分组形状作为单个可选对象显示。

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

打开 `output.docx` 时，您会看到一个内部包含图片的矩形。单击该形状会同时选中矩形和图片，因为它们已经 **分组**。

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*图片替代文字：* *group shapes in word example* – 一个展示分组矩形和图片的 Word 文档。

---

## 常见问题与边缘情况处理

| Question | Answer |
|----------|--------|
| **如果需要为图片设置不同的尺寸怎么办？** | 在插入后使用 `picture.setWidth()` 和 `picture.setHeight()` 调整。矩形可以保持原尺寸，或也一起调整以匹配。 |
| **可以向同一分组中添加更多形状吗？** | 可以。对任何额外的 `Shape` 对象调用 `group.appendChild(newShape)` 即可。 |
| **如何旋转整个分组？** | 使用 `group.setRotationAngle(double angleInRadians)`。旋转会作用于所有子形状。 |
| **如果图片文件缺失会怎样？** | `insertImage` 会抛出 `FileNotFoundException`。请将调用包装在 try‑catch 块中，并提供占位形状作为后备。 |
| **以后可以取消分组吗？** | 调用 `group.removeAllChildren()` 可分离子形状，然后将它们单独插入文档。 |

---

## 结论

现在您拥有一个完整、可运行的示例，展示了 **如何在 Word 中对形状进行分组**、**添加矩形形状**、**设置形状大小**，并使用 Aspose.Words for Java **保存**文档。通过将矩形和图片分组，您可以将它们作为单个单元移动、调整大小或旋转——这正是许多文档自动化场景所需的功能。

接下来您可以探索：

* 向同一分组中添加文本框（类似 **添加矩形** 风格的文本）。  
* 应用不同的填充图案或渐变（结合 **设置形状大小** 与样式）。  
* 使用相同技术对图表、表格或 SmartArt 进行分组（在其他对象类型上 **对形状进行分组**）。

欢迎尝试其他形状类型、颜色和布局选项。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您在自己的项目中进一步掌握 API 功能并探索替代实现方式。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}