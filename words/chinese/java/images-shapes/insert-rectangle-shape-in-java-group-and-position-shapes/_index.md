---
category: general
date: 2026-07-26
description: 使用 Aspose.Words 在 Java 中插入矩形形状。了解如何设置形状大小、定位形状以及如何在 DOCX 文件中对形状进行分组。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: zh
lastmod: 2026-07-26
og_description: 在 Java 中插入矩形形状，以创建丰富的 DOCX 图形。按照本分步指南，轻松设置形状大小、定位形状并对形状进行分组。
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: 在 Java 中插入矩形形状 – 掌握分组与定位
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: 在 Java 中插入矩形形状 – 组合和定位形状
url: /zh/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中插入矩形形状 – 组合与定位形状

是否曾在编写 Java 代码时需要 **insert rectangle shape** 到 Word 文档中？你并不是唯一遇到这种情况的人——开发报告、发票或自定义模板的开发者经常会碰到这个难题。好消息是，只需几行 Aspose.Words for Java，就可以 **insert rectangle shape**、**set shape size**、**position shape**，甚至 **how to group shapes**，让它们作为一个整体移动。

在本指南中，我们将从创建空白文档到保存包含两个整齐分组矩形的 `.docx`，完整演示整个过程。结束时，你将了解 **how to add rectangle** 对象，控制它们的尺寸，精确定位，并将它们打包成可复用的组。除了 Aspose.Words 外无需其他库，代码兼容 Java 8 及以上。

## 前置条件

- 已安装 Java 8 或更高版本（我使用 JDK 17，但任何支持 Maven 的版本都可）
- Aspose.Words for Java 23.9 或更高 – 将依赖添加到 `pom.xml` 或下载 JAR
- 对 Java 语法有基本了解（只要会写 `main` 方法即可）
- 任选的 IDE 或文本编辑器（IntelliJ IDEA、Eclipse、VS Code…）

> **专业提示：** 如果使用 Maven，依赖配置如下：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

既然基础已搭建好，让我们深入代码。

## 插入矩形形状并设置其大小

首先要做的是创建一个全新的 `Document` 和 `DocumentBuilder`。Builder 就像你的“笔”，用于在页面上绘制形状。下面我们 **insert rectangle shape** 并立即 **set shape size** 为 100 × 80 点。

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

请注意，`setWidth`/`setHeight` 调用是以点为单位 **set shape size**（1 pt ≈ 1/72 英寸）。如果喜欢单一方法，也可以使用 `setSize`，但显式调用能让意图一目了然。

## 在页面上定位形状

在得到第一个矩形后，我们需要 **position shape** 第二个，使其不与第一个重叠。定位方式相同：设置相对于组原点的 `Left` 和 `Top` 属性。

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

如果你想知道为何使用 `setLeft` 而不是 `setX`，那是因为 Aspose.Words 采用经典的 Windows GDI 坐标系——`Left` 为水平偏移，`Top` 为垂直偏移。修改这些值即可在不使用表格或段落的情况下微调布局。

## 如何对形状进行分组

你可能会问：“为什么要使用分组？”当你希望形状一起移动、整体旋转或共享相同样式时，分组就很有意义。在上面的代码片段中，我们已经通过 `builder.insertGroupShape` 创建了一个 `GroupShape`。该对象本质上是一个容器——可以把它想象成一个文件夹，用来保存其他形状。

> **重要原因：** 如果以后决定添加标题或旋转整个图形，只需修改组本身，而不必逐个矩形进行修改。

## 如何将矩形添加到组中

将 **how to add rectangle** 添加到组中，只需调用 `group.appendChild(rectangle)`。在内部，Aspose.Words 会更新组的内部集合，并自动重新计算边界框，使组仍然符合其声明的宽高。

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

你可以尝试其他 `ShapeType`——如 `ShapeType.ELLIPSE`、`ShapeType.TRIANGLE` 等，`appendChild` 的使用方式相同。

## 保存文档

最后，我们将文档持久化到磁盘。路径可以是绝对或相对的，只需确保文件夹已存在。

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

当你在 Microsoft Word 中打开 `GroupShape.docx` 时，会看到两个并排的矩形，都被锁定在一个浅灰色框内。选中灰色框会一次性高亮两个矩形——这证明 **how to group shapes** 确实有效。

![Word 文档中的分组矩形](placeholder-image.png){: .center-image alt="插入矩形形状示例，展示在 Java 生成的 DOCX 文件中分组的两个矩形"}

*图片 alt 文本（SEO）：* **插入矩形形状示例，展示在 Java 生成的 DOCX 文件中分组的两个矩形**。

## 预期输出

- 位于 `output` 文件夹中的 `GroupShape.docx` 文件。
- 文档内部：一个 400 × 200 pt 的组，包含两个矩形（100 × 80 pt 和 120 × 60 pt），分别位于 (20, 30) 和 (150, 50)。
- 该组具有细黑色边框和浅灰色填充，使分组视觉上明显。

打开文件并尝试拖动灰色框——两个矩形应一起移动。如果没有，请再次确认已对每个形状调用 `group.appendChild`。

## 常见陷阱与边缘情况

| 问题 | 产生原因 | 解决方案 |
|-------|----------------|-----|
| **矩形出现在页面之外** | `Left`/`Top` 值超出组的尺寸 | 增大组的大小（`insertGroupShape(width, height)`）或减小偏移量 |
| **保存后组消失** | 组的 `Width`/`Height` 被设为 0 | 在调用 `insertGroupShape` 时提供非零的尺寸 |
| **形状颜色不正确** | 默认填充为透明，Word 可能将其渲染为白色 | 明确设置 `setFillColor` 或使用 `ShapeStyle` |
| **异常 `ArgumentOutOfRangeException`** | 使用了负坐标 | 保持 `Left` 和 `Top` 为非负值 |

## 回顾与后续步骤

我们已经完整覆盖了在 Java 中 **insert rectangle shape** 的整个生命周期：创建文档、**set shape size**、**position shape**、**how to group shapes**，以及 **how to add rectangle** 到该组。完整的可运行示例位于上面的代码块中，你可以直接粘贴到 Maven 项目中查看效果。

接下来怎么办？可以尝试以下实验：

- 在每个矩形内部添加文本，通过

## 接下来应该学习什么？

以下教程涵盖与本指南紧密相关的主题，基于本教程中演示的技术。每个资源都包含完整的可运行代码示例和逐步说明，帮助你掌握更多 API 功能，并在自己的项目中探索替代实现方式。

- [创建 Word 文档 Java – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [在 Word 文档中使用 Aspose.Words for .NET 创建组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [创建带阴影矩形形状的空白 Word 文档 – 步骤指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}