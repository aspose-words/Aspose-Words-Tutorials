---
category: general
date: 2026-07-16
description: 如何在 Java 中使用 Aspose.Words 插入组合形状——添加矩形形状，设置形状尺寸，并创建彩色矩形和圆形。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: zh
lastmod: 2026-07-16
og_description: 如何在 Java 中插入组合形状：使用 Aspose.Words 的实用指南，添加矩形形状、设置形状尺寸，并创建彩色矩形和圆形。
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: 在 Java 中插入组形状 – 完整的 Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: 如何在 Java 中插入组合形状 – 完整指南
url: /zh/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中插入组合形状 – 完整指南

是否曾想过 **how to insert group shape** 在使用 Java 的 Word 文档中？你并不是唯一有此疑问的人。无论是构建报告生成器还是动态传单创建器，将形状分组都能让布局整洁，代码易于管理。

在本教程中，我们将逐步演示使用 Aspose.Words 库 **add rectangle shape**、**set shape dimensions**、**create colored rectangle** 和 **create colored circle** 的确切步骤。完成后，你将拥有一个可运行的程序，生成一个包含蓝色矩形和红色圆形并整齐包装在组合中的 .docx 文件。

## 前提条件

- Java 17（或任何近期的 JDK）已安装并配置。
- Maven 或 Gradle 用于管理依赖。
- Aspose.Words for Java 23.9 或更高版本 – 你可以从 Maven Central 获取。
- 对 Java 语法的基本了解 – 不需要任何高级技巧。

如果缺少上述任意项，请从 Oracle 网站获取 JDK，并将 Aspose.Words 依赖添加到你的 `pom.xml`：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

现在基础工作已就绪，让我们动手实践吧。

## 如何插入组合形状 – 概览

核心思路很简单：创建一个 `Document`，打开一个 `DocumentBuilder`，插入一个 **group shape**，然后将各个形状（矩形和圆形）放入该组合中。组合充当容器，后期移动时会一起移动内部所有对象——非常适合复杂布局。

下面是完整的、可直接运行的代码。随意将其复制粘贴到一个名为 `InsertGroupShapeDemo` 的新 Java 类中。

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **技巧提示：** `setLeft` 和 `setTop` 的值是相对于组合的原点，而不是页面。这使得后期重新定位整个组合变得轻而易举。

### 刚才发生了什么？

1. **Document & Builder** – 我们创建一个空的 Word 文件并使用 `DocumentBuilder` 来插入内容。
2. **Group Shape** – `builder.insertGroupShape()` 创建一个容器。可以把它想象成绘图对象的文件夹。
3. **Blue Rectangle** – 我们实例化一个类型为 `RECTANGLE` 的 `Shape`，设置尺寸、位置，并填充蓝色——这就是 **create colored rectangle** 步骤。
4. **Red Circle** – 同样的模式，但使用 `ELLIPSE` 来绘制完美的圆形，然后填充红色——这就是 **create colored circle** 部分。
5. **Saving** – 最后我们将所有内容保存为 `GroupShapeDemo.docx`。

运行程序 (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) 并打开生成的文件。你应该会看到左侧的蓝色矩形和右侧的红色圆形，它们都被锁定在同一个组合框中。

## 添加矩形形状

如果只需要一个不分组的矩形，你可以省略 `insertGroupShape()` 调用，直接将矩形追加到文档主体。但分组能够让你一次性移动、旋转或删除多个形状，提供更大的灵活性。

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

请注意这里我们使用了 **add rectangle shape** 的逻辑。矩形会作为独立对象出现在页面上。不过在大多数实际场景中，你会希望使用组合，因为它保持了相对定位。

## 设置形状尺寸

当看到 `setWidth` 和 `setHeight` 等方法时，请记住它们接受 **points**（1/72 英寸）作为单位。如果你更喜欢使用毫米，需要先进行转换：

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

此代码片段演示了使用单位转换的 **set shape dimensions**——当你的设计规格来自使用公制单位的 UI 原型时非常方便。

## 创建彩色矩形

为形状着色只需调用 `getFill().setForeColor()`。你可以传入任意 `java.awt.Color`。想要渐变？使用 `setForeColor` 设置起始颜色，`setBackColor` 设置结束颜色。

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

这是一种快速实现 **create colored rectangle** 的方式，使用渐变填充而非纯色。

## 创建彩色圆形

圆形只是宽高相等的椭圆。相同的着色逻辑同样适用：

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

如果需要透明填充，请设置 alpha 通道：

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

现在你已经掌握了 **create colored circle** 技巧。

## 保存文档

Aspose.Words 支持输出多种格式：DOCX、PDF、HTML、PNG，随你选择。此示例我们使用 DOCX，因为它能完美保留矢量形状。

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

只需切换 `SaveFormat`，即可生成相同组合艺术作品的 PDF 版本。

## 常见陷阱及规避方法

- **忘记将形状添加到组合中？** 形状会出现在页面上，但不会随组合移动。务必调用 `group.appendChild(yourShape)`。

## 接下来该学习什么？

以下教程涵盖与本指南紧密相关的主题，基于本教程演示的技术。每个资源都包含完整的可运行代码示例和逐步解释，帮助你掌握更多 API 功能，并在项目中探索替代实现方案。

- [创建 Word 文档（Java） – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [如何使用 Aspose.Words for Java 的 DocumentBuilder 创建表单字段并添加内容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [使用 Aspose.Words 在 Word 中创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}