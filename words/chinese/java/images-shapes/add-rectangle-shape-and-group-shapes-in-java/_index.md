---
category: general
date: 2026-11-22
description: 使用 Java 在 Word 文档中添加矩形形状，设置形状大小，将多个形状分组，并高效地将形状追加到组中。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: zh
lastmod: 2026-11-22
og_description: 使用 Java 在 Word 文档中添加矩形形状，然后设置形状大小，将多个形状分组，并在单个工作流中将形状追加到组中。
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: 在 Java 中添加矩形形状并对形状进行分组 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: 在 Java 中添加矩形形状并对形状进行分组
url: /zh/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中添加矩形形状并对形状进行分组

如果您需要 **在 Word 文档中添加矩形形状**，本指南将一步步带您完成整个过程。您还将学习如何 **设置形状大小**、**对多个形状进行分组**，以及 **将形状追加到组中**，全部在 IDE 中完成。

在 DOCX 文件中处理矢量图形常常感觉像在使用多个 API。完成本教程后，您将拥有一个完整、独立的程序，能够创建矩形、椭圆以及您可能需要的其他形状，然后将它们分组，使其作为一个整体移动。无需任何外部工具，只需 Aspose.Words for Java。

## 前置条件

开始之前，请确保您具备：

* 已安装 Java 17 或更高版本。
* 已安装 Maven 3.8+（或 Gradle）用于管理依赖。
* 有效的 Aspose.Words for Java 许可证（评估版可用于测试）。
* IntelliJ IDEA、VS Code 等 IDE，当然任何文本编辑器也可以。

这些条件可确保代码在任何现代开发环境中编译并运行。

## 第一步：设置 Maven 项目

创建一个新的 Maven 项目，或在已有的 `pom.xml` 中添加 Aspose.Words 依赖：

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

该依赖会引入文档操作所需的所有类，包括 `Document`、`DocumentBuilder`、`Shape` 和 `GroupShape`。运行 `mvn compile` 时，Maven 会自动下载相应的 JAR 包。

## 第二步：加载文档并创建 DocumentBuilder

`DocumentBuilder` 提供了用于插入内容的流式 API。加载已有的 DOCX，或从空白文档开始：

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

提前创建构建器可以让光标定位在文档开头，随时准备插入形状。

## 向 Word 文档添加矩形形状

### 第三步：插入矩形形状

矩形是我们要放入文档的第一个可视元素。使用 `Shape` 构造函数并传入 `ShapeType.RECTANGLE`，即可得到一个完全可编辑的对象。

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

此时插入矩形并不会影响布局，直到为其定义大小并将其追加到容器中。

### 设置形状大小和尺寸

#### 第四步：定义宽度和高度

设置形状的尺寸决定了它在页面上的显示方式。宽度和高度的单位是点（1 pt = 1/72 in）。

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

您可以根据设计需求调整这些数值。相同的方法适用于任何 `Shape` 实例，因此可以复用于圆形、箭头或自定义绘图。

#### 第五步：将矩形插入文档

现在矩形已有尺寸，将其放置在页面上。`DocumentBuilder` 的 `insertShape` 方法会在当前光标位置添加形状。

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

此时矩形单独显示在页面上。接下来的步骤将展示如何将其与其他形状组合。

## 将多个形状分组

对形状进行分组后，您可以将它们视为一个整体进行移动、旋转或缩放。这在创建复杂图表时尤为有用。

### 第六步：创建组形状容器

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`insertGroupShape` 调用会在文档中添加一个空容器。随后追加到该容器的任何形状都会成为组的一部分。

### 将形状追加到组中

#### 第七步：将矩形添加到组

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

追加操作会将矩形从文档主体移动到组的内部集合中。矩形现在会遵循组的变换属性。

#### 第八步：添加椭圆进行演示

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

椭圆与矩形共享相同的坐标空间，您可以通过调整 `setLeft` 和 `setTop` 属性来对齐它们。

### 第九步：保存文档

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

运行程序后会生成 `output.docx`。在 Microsoft Word 或 LibreOffice 中打开，您将看到矩形和椭圆已被分组。选中任意一个形状时，整个组都会被高亮，说明 **将形状追加到组中** 已成功。

![Add rectangle shape example in Java](image.png){alt="Add rectangle shape example in Java"}

*截图展示了矩形和椭圆位于同一组中，已准备好联合操作。*

## 为什么这种做法重要

* **单一真相来源** – 所有形状属性在创建组之前就已设置，避免布局异常。
* **可复用性** – 相同的 `setWidth`/`setHeight` 方法适用于任何形状，您可以将示例扩展到箭头、星形或自定义 SVG。
* **性能** – 分组可减少 Word 渲染器需要处理的绘图对象数量，从而提升大型文档的打开速度。
* **可维护性** – 将形状创建与分组逻辑放在一起，后续开发者可以在不遍历无关代码的情况下修改尺寸或添加新形状。

## 常见变体和边缘情况

| 场景 | 调整方式 |
|----------|------------|
| **不同单位** | 使用 `PointsToPixels` 转换或设置 `Shape.setWrapType(WrapType.INLINE)` 进行行内放置。 |
| **旋转组** | 调用 `groupShape.setRotation(45);` 将所有子形状旋转 45°。 |
| **向形状添加文本** | 在设置尺寸后使用 `Shape.setText("Label");`。 |
| **动态尺寸** | 通过 `doc.getFirstSection().getPageSetup().getPageWidth()` 获取页面宽度，并按比例计算形状大小。 |

这些变体展示了核心模式——**添加矩形形状**、**设置形状大小**、**分组多个形状**、**将形状追加到组中**——如何适配各种实际需求。

## 结论

现在您已经掌握了如何使用 Java **向 Word 文档添加矩形形状**、**设置形状大小**、**分组多个形状**，以及 **将形状追加到组中** 的完整、可维护的实现方式。完整示例可编译为单个可运行的类，生成的 DOCX 文件展示了预期的输出。

接下来您可以探索：

* 为每个形状添加文本标签或超链接。
* 嵌套组以构建层级图表。
* 将文档导出为 PDF，同时保留形状组。

欢迎尝试不同的尺寸、颜色和额外的形状类型。掌握形状操作后，您即可实现自动化报表生成、动态图表以及丰富的文档体验——全部直接通过 Java 代码完成。

## 接下来应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您进一步深化对 API 的使用并探索替代实现方案：

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Create rectangle shape in a Word document using Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}