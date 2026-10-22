---
category: general
date: 2026-08-07
description: 使用 Aspose.Words 在 Java 中创建带有分组形状的空白 Word 文档。了解如何对形状进行分组、设置形状大小以及向 Word
  添加形状。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: zh
lastmod: 2026-08-07
og_description: 在 Java 中创建带有分组形状的空白 Word 文档。按照本指南设置形状大小、向 Word 添加形状，并掌握如何对形状进行分组。
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: 使用分组形状创建空白 Word 文档 – Java 教程
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: 在 Java 中创建带有分组形状的空白 Word 文档
url: /zh/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Java 创建带有组合形状的空白 Word 文档

如果您需要 **create blank Word document**，且其中包含多个形状作为一个整体排列，本教程将一步步演示完整可运行的示例，展示 **how to group shape** 对象、调整它们的尺寸以及使用 Aspose.Words for Java **add shapes to Word** 的方法。

本指南涵盖从项目设置到保存最终 .docx 文件的每一步，您可以直接将代码复制到自己的应用程序中。无需外部引用，解决方案适用于 Aspose.Words 23.9 或更高版本。

## 前置条件

在开始之前，请确保您拥有：

* Java 17（或任何受支持的 JDK）
* 用于依赖管理的 Maven 或 Gradle
* Aspose.Words for Java 许可证（或临时评估密钥）
* 放置在已知目录下的示例图片文件（例如 `sample.jpg`）

如果缺少上述任意项，请先进行安装；后续教程默认环境已就绪。

## 第 1 步：将 Aspose.Words 添加到项目中

在 `pom.xml`（Maven）或 `build.gradle`（Gradle）中添加 Aspose.Words 依赖。该库提供后续使用的 `Document`、`DocumentBuilder`、`GroupShape` 和 `Shape` 类。

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**为什么重要：** 没有此库，Word 处理相关的 API 将不可用，您也无法 **create blank Word document**。

## 第 2 步：创建空白 Word 文档

第一步实际操作是实例化一个 `Document` 对象，它在内存中表示一个 **blank Word document**。

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* 会使用默认设置（A4 页面、默认页边距）创建一个 **blank Word document**。配套的 `DocumentBuilder` 允许您在当前光标位置插入内容。

## 第 3 步：插入组形状（how to group shape）

*组形状* 充当其他形状的容器。在本步骤中，您将学习 **how to group shape** 对象，使它们能够一起移动。

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

`insertGroupShape` 方法将在构建器的光标位置放置容器。组形状在您希望将多个绘图视为单一实体时至关重要——这正是 **group shapes word** 功能的核心。

## 第 4 步：创建矩形并设置尺寸

现在向组中添加一个矩形。这演示了 **set shape size**，用于实现精确布局。

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*为何要设置尺寸？* 显式调用 `setWidth` 和 `setHeight` 可确保矩形始终按预期显示，而不受文档默认形状样式的影响。

## 第 5 步：插入图片并加入组中

插入图片展示了另一个常见的 **add shapes to word** 用例。图片将成为同一组的一部分，随矩形一起移动。

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

如果图片文件缺失，Aspose.Words 会抛出异常。实用技巧是事先验证路径：

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## 第 6 步：保存包含组合形状的文档

最后，将 **blank Word document**（已包含组合形状）持久化到磁盘。

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

在 Microsoft Word 中打开 `GroupShapeDemo.docx` 时，您会看到一个包含矩形和图片的单一组合对象。选中组内任意部分都会移动整个容器，证明形状已成功 **grouped**。

### 预期输出

* 在指定目录下生成名为 `GroupShapeDemo.docx` 的文件。
* 打开文件后可见一个 300 × 200 点的容器，内部包含：
  * 位于 (20, 20) 的 100 × 50 点矩形。
  * 位于 (150, 30) 的图片，位于同一容器内。

## 边缘情况与变体

| 情况 | 处理方式 |
|-----------|-----------------|
| **不同的页面尺寸** | 在插入组之前调用 `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` |
| **多个组** | 对新的 `GroupShape` 实例重复步骤 3‑5；每个组可独立定位。 |
| **旋转形状** | 使用 `shape.setRotationAngle(45.0);` 在将矩形或图片加入组之前进行旋转。 |
| **非图片形状** | 创建 `Shape` 类型为 `ShapeType.ELLIPSE`、`ShapeType.LINE` 等的对象，并像矩形一样追加到组中。 |
| **大图片** | 使用 `picture.setWidth(80.0); picture.setHeight(60.0);` 缩放图片，以保持组在原始边界内。 |

这些变体帮助您将核心模式适配到各种文档生成场景。

## 实践技巧

* **专业提示：** 将组的 `RelativeHorizontalPosition` 和 `RelativeVerticalPosition` 设置为 `RelativeHorizontalPosition.PAGE` 与 `RelativeVerticalPosition.PAGE`，可使组锚定在页面上而非光标位置。
* **注意事项：** 添加超出组尺寸的形状时，Word 会对其进行裁剪。请使用 `group.setWidth()` 与 `group.setHeight()` 相应调整组大小。
* **性能说明：** 若在循环中生成大量文档，复用单个 `DocumentBuilder` 实例并调用 `doc.clone()` 可降低对象创建开销。

## 结论

现在，您已经掌握了使用 Aspose.Words for Java **create blank Word document** 并在其中包含组合形状的完整流程。教程涵盖了库的设置、文档创建、插入组、**set shape size**、**add shapes to word**，以及最终保存。

接下来，您可以探索更高级的功能，如对图表进行分组、为单个形状应用样式，或将文档导出为 PDF。所有这些主题都基于本指南中演示的相同原理。

---


## 接下来您可以学习什么？

以下教程与本指南紧密相关，进一步扩展了本教程中展示的技术。每篇资源均提供完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中尝试不同实现方式。

- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [Java 创建 Word 文档 – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [使用 Aspose.Words for .NET 在 Word 文档中插入形状](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}