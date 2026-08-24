---
category: general
date: 2026-08-23
description: 使用 Aspose.Words for Java 创建空白 Word 文档，学习如何对形状进行分组、为矩形形状着色，并在几分钟内将文档保存为
  docx。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: zh
lastmod: 2026-08-23
og_description: 使用 Aspose.Words for Java 创建空白 Word 文档，然后了解如何对形状进行分组、为矩形形状着色，并高效地将文档保存为
  docx。
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: 在 Java 中创建空白 Word 文档并对形状进行分组——一步步指南
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: 在 Java 中创建空白 Word 文档并对形状进行分组
url: /zh/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中创建空白 Word 文档并对形状进行分组

如果您需要以编程方式 **create blank Word document**，Aspose.Words for Java 让这变得简单。本教程将准确演示如何 **create blank Word document**、插入 **group shapes in Word**、应用 **color rectangle shape**，以及最终 **save document as docx**。完成后，您将拥有一个可在任何 Java 项目中直接使用的可复用代码片段。

您将学习：

* Aspose.Words 所需的 Maven/Gradle 依赖。
* 如何实例化空白文档以及 `DocumentBuilder`。
* 在 `GroupShape` 中 **how to group shapes** 的确切步骤。
* 如何为矩形形状设置填充颜色。
* 关于 **save document as docx** 的最佳实践以及输出文件的位置。

不假设您有 Aspose.Words 的任何先前经验，但您应熟悉基本的 Java 开发，并已安装 JDK 8 或更高版本。

---

## 前置条件

| 要求 | 版本 / 细节 |
|-------------|-------------------|
| Java Development Kit | 8 or higher |
| Build tool | Maven 3+ or Gradle 6+ |
| Aspose.Words for Java | 23.12 or later (the latest version at the time of writing) |
| IDE (optional) | IntelliJ IDEA, Eclipse, VS Code, or any Java‑compatible editor |

---

## 步骤 1：将 Aspose.Words 添加到您的项目中

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **专业提示：** 如果您使用公司代理，请按照官方文档的说明配置 Maven/Gradle 从 Aspose 仓库拉取包。

---

## 步骤 2：使用构建器 **Create blank Word document** 

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 构造函数在内存中创建一个空的 `.docx` 容器。`DocumentBuilder` 为您提供流式 API，以添加内容，包括形状。

---

## 步骤 3：插入 **group shapes in Word** 容器

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

`GroupShape` 的工作方式类似于一个小画布。添加到其中的所有形状会一起移动，这正是 **how to group shapes** 用于布局一致性的方式。

---

## 步骤 4：添加第一个 **color rectangle shape**（红色）

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

`ShapeType.RECTANGLE` 常量创建一个简单的矩形。通过调用 `getFill().setForeColor(...)`，您可以控制 **color rectangle shape**。您可以将 `java.awt.Color.RED` 替换为任意 `java.awt.Color` 常量或自定义 RGB 值。

---

## 步骤 5：添加第二个 **color rectangle shape**（绿色）并定位

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

设置 `setLeft`（或 `setTop`）会使形状相对于 **group shapes in Word** 容器的左上角移动。这演示了使用精确定位的 **how to group shapes**。

---

## 步骤 6：**Save document as docx** 并验证结果

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`save` 方法会自动写入 `.docx` 文件，因为文件扩展名是 `.docx`。如果需要其他格式（例如 PDF），请传入相应的 `SaveFormat` 枚举。

> **提示：** 确保目标目录（本例中的 `output/`）存在，或使用 `new File("output").mkdirs();` 在代码中创建它。

---

## 完整源代码，快速复制粘贴

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**预期输出：** 在 Microsoft Word 中打开 `GroupShapeDemo.docx`，会看到单页包含两个彩色矩形（左侧红色，右侧绿色），当您选择该组时，它们会一起移动。

---

## 常见问题与边缘情况处理

| 问题 | 答案 |
|----------|--------|
| 我可以向同一组添加超过两个形状吗？ | 可以。对每个额外的形状调用 `groupShape.appendChild(yourShape)`。组会自动调整大小以适应最远的边界，或者您可以手动调整其宽度/高度。 |
| 如果我需要不同的形状类型（例如椭圆）怎么办？ | 将 `ShapeType.RECTANGLE` 替换为 `ShapeType.ELLIPSE`。填充颜色的逻辑相同。 |
| 我需要释放 `Document` 对象吗？ | Aspose.Words 在内部管理本机资源。当 JVM 退出时，资源会被释放。对于长时间运行的应用程序，如果使用 **Aspose.Words for Java (Native)** 版本，请调用 `doc.dispose();`。 |
| 如何更改 Z 顺序，使一个矩形位于顶部？ | 使用 `groupShape.insertAfter(shape, referenceShape);` 或 `groupShape.insertBefore(shape, referenceShape);` 在组内重新排序子项。 |
| 我可以跨不同章节对形状进行分组吗？ | 不能。`GroupShape` 必须位于单个段落或形状容器内。若要跨章节分组，需要在每个章节创建单独的组。 |

---

## 结论

现在，您已经了解如何使用 Aspose.Words for Java **create blank Word document**、**group shapes in Word**、应用 **color rectangle shape** 样式，并 **save document as docx**。此模式可扩展到更复杂的布局——只需添加更多形状、调整偏移量，必要时在组内设置文本、图像或超链接。

**接下来的步骤** 您可以探索：

* 使用 **group shapes in Word** 构建流程图或 UI 原型。
* 尝试将 **save document as docx** 与 PDF 转换相结合（`doc.save("out.pdf")`）。
* 对 **color rectangle shape** 应用渐变或图案，以获得更丰富的视觉设计。
* 将分组形状与表格或图表结合，用于高级报表文档。

欢迎根据项目品牌修改尺寸、颜色或形状类型。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能，并在自己的项目中探索替代实现方式。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}