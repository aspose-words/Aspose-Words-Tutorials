---
category: general
date: 2026-10-16
description: 学习如何使用 Java 在 Word 中对形状进行分组。本教程展示了如何添加矩形形状、设置形状的大小和尺寸，以及保存文档。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: zh
lastmod: 2026-10-16
og_description: 使用 Java 在 Word 中对形状进行分组。添加矩形形状，设置形状大小和尺寸，并以编程方式创建专业文档。
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: 使用 Java 在 Word 中对形状进行分组 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: 如何使用 Java 在 Word 中对形状进行分组——完整指南
url: /zh/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 Java 对形状进行分组 – 完整指南

如果您需要以编程方式 **group shapes in Word**，本教程为您提供一个可直接运行的解决方案。您将看到如何 **add rectangle shape**、调整其大小、设置 shape dimensions，最后保存一个包含分组矩形和椭圆的 DOCX 文件。

在 Word 中对形状进行分组对于构建复杂图表、创建可重用的图形组件，或仅仅在文档后期编辑时保持相关对象在一起非常有用。代码使用 Aspose.Words for Java 库，该库兼容任何近期的 JDK，且无需安装 Microsoft Word。

## 前提条件

| Requirement | Reason |
|-------------|--------|
| Java 17（或更高） | 该库面向现代 Java 运行时。 |
| Aspose.Words for Java（最新版本） | 提供示例中使用的 `Document`、`DocumentBuilder`、`GroupShape` 和 `Shape` 类。 |
| IDE 或构建工具（Maven/Gradle） | 用于编译和运行示例。 |
| 基本的 Java 语法知识 | 需要理解代码流程。 |

将 Aspose.Words 依赖添加到项目中。对于 Maven：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

或者对于 Gradle：

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## 解决方案概述

本教程遵循清晰的 **problem → solution → explanation**（问题 → 解决方案 → 解释）模式：

1. **创建一个新的 Word 文档** 并获取 `DocumentBuilder`。  
2. **插入一个 `GroupShape` 容器**，用于容纳多个形状。  
3. **添加矩形**，设置其宽度/高度（即 **set shape size** 步骤），并将其附加到组中。  
4. **添加椭圆**，将其定位在同一组内，并同样设置其尺寸。  
5. **保存** 文档到磁盘。

每一步都包含代码背后的 **why**，帮助您了解 API 的作用以及如何将其适配到其他场景。

## 步骤 1：创建文档和 DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `Document` 代表整个 DOCX 文件，而 `DocumentBuilder` 是一个帮助器，允许您在不处理低层节点管理的情况下插入内容。首先创建它们为后续的所有形状操作提供了干净的画布。

## 步骤 2：插入 GroupShape 容器

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`GroupShape` 的作用类似于绘图对象的 **文件夹**。当您移动、旋转或删除该组时，所有子形状会自动随之变化。这就是 **group shapes in word** 的核心。

## 步骤 3：添加矩形形状 – 矩形形状代码

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – `Shape` 构造函数接收 `ShapeType.RECTANGLE`，这告诉 Aspose.Words 渲染矩形轮廓。  
- **set shape size** – `setWidth` 和 `setHeight` 以点为单位定义 **shape dimensions**（1 pt = 1/72 in）。这是控制可视大小的最常用方式。  
- **Why we use `appendChild`** – 它将矩形附加到 `GroupShape`，使其随组一起移动。

## 步骤 4：添加椭圆并将其定位在组内

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

椭圆演示了 **set shape dimensions** 超出简单矩形的用法。通过调用 `setLeft`，我们可以控制在组内的水平偏移，这在排列多个对象时非常有用。

## 步骤 5：保存文档

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

当您在 Microsoft Word 中打开 *GroupShapeDemo.docx* 时，您会看到一个矩形和一个椭圆被锁定在同一个组内。选择任意形状都会选中整个组——这正是您在 **group shapes in word** 时所期待的效果。

## 完整、可运行的示例

将所有部分组合在一起，以下是您可以复制到 IDE 中的完整源文件：

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### 预期输出

- 项目文件夹中出现一个名为 **GroupShapeDemo.docx** 的文件。  
- 在 Word 中打开该文件会显示两个形状（矩形和椭圆），它们已被分组在一起。  
- 拖动任意形状会移动整个组，确认 **group shapes in word** 正常工作。

## 常见变体和边缘情况

| Scenario | What to change | Why |
|----------|----------------|-----|
| **不同的形状类型**（例如，三角形） | 在构造 `Shape` 时使用 `ShapeType.TRIANGLE` 或其他枚举值。 | 允许您构建更复杂的图表。 |
| **设置填充颜色** | 在创建形状后调用 `shape.getFillColor().setColor(Color.BLUE);`。 | 在不影响分组的情况下提升视觉外观。 |
| **旋转组** | `groupShape.setRotationAngle(45);` | 一起旋转所有子形状，对图标很有用。 |
| **在形状内部添加文本** | `shape.appendChild(new Paragraph(document));` 然后添加带文本的 `Run`。 | 使形状充当标签或标注。 |
| **保存到流** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | 对直接返回文档的 Web 服务很有用。 |

### 专业提示

当您需要基于动态数据（例如条形码长度）**set shape dimensions** 时，首先以点为单位计算宽度/高度：

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

## 结论

现在您已经了解如何使用 Java **group shapes in Word**，如何 **add rectangle shape**，以及如何使用简洁、可投入生产的代码 **set shape size** 和 **set shape dimensions**。按照上述步骤，您可以创建可重用的图形组，将其嵌入自动化报告，或构建无需手动打开 Word 的自定义绘图工具。

### 接下来做什么？

- 探索 **add rectangle shape** 的变体，例如圆角（使用 `ShapeType.RECTANGLE` 并调用 `setCornerRadius`）。  
- 将 **group shapes in word** 与表格或图表结合，以创建更丰富的文档。  
- 研究 Aspose.Words API 中的 **text wrapping**（`shape.setWrapType(WrapType.SQUARE)`），以控制周围文本与分组图形的交互方式。

随意尝试，改编 **rectangle shape code**，并分享您的成果

## 接下来应该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [创建 Word 文档（Java） – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [使用 Java 在 Word 中创建矩形形状 – 完整指南](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}