---
category: general
date: 2026-09-21
description: 使用 Java 编程创建 Word 文档。学习如何在 Word 中对形状进行分组、插入矩形形状、设置形状大小以及向 Word 文档添加形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: zh
lastmod: 2026-09-21
og_description: 使用 Java 编程创建 Word 文档：本指南展示了如何在 Word 中对形状进行分组、插入矩形形状、设置形状大小以及将形状添加到
  Word 文档中。
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: 在Java中以编程方式创建Word文档并对形状进行分组
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: 使用 Java 编程创建 Word 文档并对形状进行分组
url: /zh/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Java 编程创建 Word 文档并对形状进行分组

如果您需要**以编程方式创建 Word 文档**，本指南将为您提供完整的解决方案。您将看到如何**在 Word 中对形状进行分组**，插入矩形、设置其大小，并添加其他形状——全部使用 Java 和 Aspose.Words for Java 库。

本教程涵盖了从项目设置到保存最终 .docx 文件的每一步。完成后，您将能够生成一个包含矩形和图像的 Word 文档，这两个对象被包装在同一个组中，便于一起移动或调整大小。无需事先了解 Aspose.Words API，但您应具备基本的 Java 开发环境。

## 前置条件

* Java Development Kit (JDK) 8 或更高版本  
* 用于依赖管理的 Maven 或 Gradle  
* Aspose.Words for Java 23.9（或最新版本）——该库可免费评估使用  
* 一张图像文件（例如 `sample.jpg`），放置在已知目录中  

准备好这些项目可确保代码在无需额外配置的情况下运行。

## 第一步：设置项目并导入 Aspose.Words

创建一个 Maven 项目（或在现有的 `pom.xml` 中添加依赖）：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

如果您更喜欢 Gradle，请在 `build.gradle` 中添加以下内容：

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

依赖解析完成后，在 Java 源文件中导入所需的类：

```java
import com.aspose.words.*;
import java.io.File;
```

## 第二步：以编程方式创建 Word 文档

在任何自动化场景中，第一步都是实例化 `Document` 对象和 `DocumentBuilder`。Builder 简化了文本、图像和形状的插入。

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

此时文档仅存在于内存中。接下来即可开始添加形状。

## 第三步：插入矩形形状 – 如何插入矩形形状

矩形是一个基本的 `Shape`，其 `ShapeType` 为 `RECTANGLE`。您可以使用 `setWidth`、`setHeight` 来控制尺寸，并使用 `setTop`、`setLeft` 来定位。

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**为什么这很重要：** 明确设置大小和位置（`set shape size word`）可确保矩形恰好出现在您期望的位置，而不受文档默认布局的影响。

## 第四步：插入图像 – 向 Word 文档添加形状

`DocumentBuilder` 可以直接从文件路径插入图像。插入后，您可以像处理其他形状一样重新定位该图片。

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

此时矩形和图片已成为文档中相互独立的形状。

## 第五步：对形状进行分组 – 如何在 Word 中对形状进行分组

当您希望将多个形状作为一个整体移动或调整大小时，分组非常有用。Aspose.Words 提供了 `GroupShape` 容器来实现此目的。

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

保存分组后，Word 会将这两个子对象视为一个逻辑对象。以后您可以选中该组并拖动，矩形和图像会一起移动。

## 第六步：保存文档

最后，将文档写入磁盘。路径必须对 Java 进程可写。

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

运行 `main` 方法会生成名为 **GroupShapeExample.docx** 的文件。使用 Microsoft Word 打开，可看到一个矩形和一张图像被锁定在同一个组内。选中该组即可同时移动两个对象，验证分组成功。

## 预期输出

* 一个位于您指定目录的 Word 文件（`GroupShapeExample.docx`）。  
* 在文件中，矩形（浅灰填充）出现在左上角，图像紧随其下。  
* 两个对象属于同一个组，拖动其中一个会一起移动另一个。

## 常见变体和边缘情况

| 情况 | 建议 |
|-----------|----------------|
| **不同的图像格式** | Aspose.Words 支持 PNG、BMP、GIF 和 TIFF。请在 `insertImage` 中使用相应的文件扩展名。 |
| **负尺寸** | API 会抛出 `ArgumentException`。在调用 `setWidth` / `setHeight` 前请始终验证宽度和高度。 |
| **大型文档** | 对大量形状进行分组可能会增加文件大小。若对性能有要求，可考虑将形状合并为单张图片。 |
| **Word 版本兼容性** | GroupShape 适用于 Word 2007（`.docx`）及更高版本。对于旧的 `.doc` 文件，组会被展平。 |
| **动态定位** | 如需自适应放置，可基于页面尺寸进行计算（`doc.getFirstSection().getPageSetup().getPageWidth()`）。 |

**技巧提示：** 创建分组后，您可以更改

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您进一步掌握 API 的其他功能，并在自己的项目中探索替代实现方式。每个资源都提供了完整的可运行代码示例和逐步解释。

- [使用 Java 创建 Word 文档 – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [使用 Java 在 Word 中创建矩形形状 – 完整指南](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}