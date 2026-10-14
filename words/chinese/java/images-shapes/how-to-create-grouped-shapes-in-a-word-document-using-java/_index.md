---
category: general
date: 2026-10-13
description: 学习如何使用 Java 在 Word 中创建组合形状。本指南展示了如何插入组合形状、向组合中添加线条，以及在整个文档中对多个形状进行分组。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: zh
lastmod: 2026-10-13
og_description: 使用 Java 在 Word 中创建分组形状。跟随本完整教程，插入分组形状、向分组添加线条，并在 Word 文档中对多个形状进行分组。
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: 使用 Java 在 Word 中创建分组形状 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: 如何使用 Java 在 Word 文档中创建组合形状
url: /zh/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Java 在 Word 文档中创建组合形状

如果你需要在 Microsoft Word 文件中 **创建组合形状**，本教程将手把手教你完成整个过程。你将看到如何 **插入组形状**、在同一个容器中放置矩形和直线，最后保存包含组合图形的文档。

将形状组合在一起可以让你像操作单个对象一样移动、缩放或设置样式——非常适合用于图表、流程图或自定义页面装饰。阅读完本指南后，你将能够 **向组中添加直线**、**在 Word 文档中组合多个形状**，并将相同的技巧复用于任意数量的形状。

## 前置条件

- 开发机器上已安装 Java 17 或更高版本。  
- 拥有 Aspose.Words for Java 许可证（或免费试用版）。  
- 一个可以添加 Aspose.Words 依赖的 Maven 或 Gradle 项目：

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

无需其他库。

## 第一步：插入组形状容器

第一步是 **插入组形状** 到文档中。该容器将容纳后续的所有形状。

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` 会创建一个类型为 `GROUPSHAPE` 的空 `Shape` 对象。可以把它看作一个透明画布，用来容纳其他绘图对象。

## 第二步：向组中添加矩形

矩形通常用作一组形状的可视背景。

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

将 `Left` 和 `Top` 设置为 `0` 可以把矩形放在组的左上角。你可以修改这些值，以在组内偏移矩形的位置。

## 第三步：**向组中添加直线** – 创建直线形状

现在我们 **向组中添加直线**。该直线会出现在矩形下面。

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

`Top` 属性将直线向下移动 60 点，形成一个简单的堆叠布局。如果需要水平偏移，也可以设置 `Left`。

## 第四步：保存包含组合形状的文档

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

当你在 Microsoft Word 中打开 `GroupShapeDemo.docx` 时，会看到一个包含矩形和直线的单一组。选中该组即可一起移动两个形状，证明你已经成功 **在 Word 中组合多个形状**。

## 完整可运行示例

下面是包含所有 import 和错误处理的完整程序。复制到 IDE 中，将 `YOUR_DIRECTORY` 替换为实际文件夹路径后运行。

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### 预期输出

- 在目标文件夹中生成名为 `GroupShapeDemo.docx` 的文件。  
- 在 Word 中打开该文件，会看到一个包含顶部矩形和底部直线的单一组合对象。  
- 拖动该组时，两种形状会一起移动，确认你已 **成功创建组合形状**。

## 提示与常见陷阱

- **专业提示：** 如果需要在组内旋转或设置单个形状的样式，请在将它们追加到组之前调用相应的 setter（如 `setRotation`、`getFill().setForeColor` 等）。组会保留这些视觉属性。  
- **注意事项：** 忘记为直线设置 `Top` 属性会导致它与矩形重叠，使组看起来杂乱。  
- **边缘情况：** 当添加超过两个形状时，请记住每个子形状的坐标是相对于组原点 (0,0) 的。请相应规划布局。  
- **性能说明：** 对大量形状（数百个）进行组合可能会略微增大文件体积，但会简化后续在 Word 中的编辑工作。

## 如何以编程方式 **在 Word 文档中组合多个形状**

上面展示的模式——创建组容器、配置每个子形状、追加——适用于任意数量的形状：圆形、图片、文本框等。只需在调用 `doc.save()` 之前重复 “创建形状 → 设置属性 → 追加” 步骤。

如果需要在组已经包含其他形状后 **向组中添加直线**，可以使用以下代码获取已有的组：

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

这表明你可以在文档生命周期的任何阶段修改组。

## 结论

现在你已经掌握了如何使用 Java 和 Aspose.Words 在 Word 文档中 **创建组合形状**。通过 **插入组形状**、**向组中添加直线**、以及 **在 Word 中组合多个形状**，你可以构建行为如单一对象的复杂绘图——非常适合用于图表、模板和自动化报告生成。

接下来，探索以下相关主题：

- **对组合形状应用样式** – 学习如何一次性为所有子形状设置填充颜色、边框和效果。  
- **将组合形状导出为 PDF** – 查看在将文档转换为 PDF 时组如何保持。  
- **使用 VBA 为形状添加动画** – 将 Java 生成的组与 Word 宏结合，实现交互式文档。

欢迎尝试不同的形状类型、尺寸和位置。组合形状让你能够把多个对象视为一个整体，从而简化代码和用户交互。祝编码愉快！


## 接下来该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助你在项目中进一步掌握 API 功能并探索替代实现方式。每个资源都提供完整的可运行代码示例和逐步解释。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}