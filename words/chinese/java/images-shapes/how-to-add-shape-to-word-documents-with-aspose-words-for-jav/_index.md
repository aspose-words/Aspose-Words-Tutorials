---
category: general
date: 2026-11-22
description: 学习如何使用 Aspose.Words for Java 向 Word 添加形状——以编程方式插入矩形并隐藏它。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: zh
lastmod: 2026-11-22
og_description: 使用 Aspose.Words for Java 向 Word 添加形状。本教程展示如何插入矩形、隐藏形状以及保存文档。
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: 使用 Aspose.Words 在 Word 中添加形状 – Java 指南
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: 如何使用 Aspose.Words for Java 向 Word 文档添加形状
url: /zh/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 向 Word 文档添加形状

如果您需要以编程方式 **向 Word 文档添加形状**，Aspose.Words for Java 使其变得简单。在本指南中，您将学习 **如何插入形状**、控制其可见性，以及 **如何隐藏形状**，以便最终文件呈现出您期望的效果。

您将通过一个完整的可运行示例，加载现有的 `.docx`，插入矩形，隐藏它，并保存结果。无需外部脚本或手动步骤，教程还涵盖了常见的变体，例如从头创建新文档或仅在打印时隐藏形状。

## 前提条件

* 已安装 Java 17（或更高版本）——早期版本也可使用，但最新的 LTS 版提供更佳性能。  
* 用于依赖管理的 Maven 3.8+。  
* 有效的 Aspose.Words for Java 许可证（免费评估版可用于学习）。  
* 您选择的 IDE 或文本编辑器（例如 IntelliJ IDEA、VS Code）。

## 第一步：将 Aspose.Words 添加到您的 Maven 项目

在您的 `pom.xml` 中添加以下依赖项。这将获取最新的稳定版本（截至 2026 年 11 月）。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **专业提示：** 如果您计划随自己的授权逻辑一起分发 JAR，请使用 `<scope>provided</scope>` 子句。

## 向 Word 添加形状 – 初始化文档

第一步功能是获取一个 `Document` 对象。您可以加载已有文件，也可以创建一个新文件。

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*为什么这很重要*：`Document` 类是所有 Word 操作的入口。加载已有文件可以保留样式、页眉和页脚，而新文档则提供一个干净的起点。

## 如何在 Word 文档中插入形状

接下来，创建一个 `DocumentBuilder` 来修改文档内容。该构建器提供插入文本、表格和 **形状** 的方法。

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

`insertShape` 调用返回一个 `Shape` 对象，您可以进一步配置（颜色、边框、文本等）。尺寸以点为单位表示（1 pt = 1/72 英寸）。

*为什么可能会使用矩形*：矩形是最常用的注释、水印或占位符容器。您可以将 `ShapeType.RECTANGLE` 替换为 `ShapeType.ELLIPSE`、`ShapeType.LINE` 等，以满足不同的视觉需求。

## 如何在 Word 中隐藏形状

有时您需要形状存在于布局计算中，但不在最终渲染中显示。Aspose.Words 提供 `setHidden(true)` 方法来实现此目的。

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

隐藏标志的工作方式类似于 Microsoft Word 中的 **Hidden** 格式选项：形状在视觉布局中被省略，但仍参与文档的对象模型。这在以下场景中很有用：

* 存储后续由应用读取的元数据或标记。  
* 创建在发布前被移除的占位符。  
* 为不同输出格式控制可见性（例如，在 HTML 中隐藏但在 PDF 中保留）。

> **注意：** 默认情况下，隐藏的形状仍会导出到 PDF。如果您也需要在 PDF 中省略它们，请设置 `rectangle.getWrapType() = WrapType.NONE` 并相应调整 `Hidden` 属性。

## 第四步：保存修改后的文档

最后，将更改持久化到新文件中。

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

当您在 Microsoft Word 中打开 `output.docx` 时，矩形将不可见，但它仍然是文档树的一部分。您可以通过重新加载文件并检查 `Shape.isHidden()` 来以编程方式验证其存在。

### 预期输出

* 文件 `output.docx` 打开后没有任何可见的形状。  
* 如果使用 Aspose.Words 检查文档（例如 `doc.getChildNodes(NodeType.SHAPE, true).size()`），形状计数将为 **1**，确认形状存在但已隐藏。

## 高级变体和边缘情况

### 1. 在新文档中创建形状

如果从头开始，请将加载行替换为：

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. 精确定位形状

默认情况下，`insertShape` 将形状放置在当前光标位置。若要绝对定位：

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. 按输出格式控制可见性

如果您需要形状在 Word UI 中可见，但在导出为 PDF 时隐藏，请将 `Shape.setWrapType(WrapType.NONE)` 与 `Hidden` 一起使用：

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. 在形状内部添加文本

矩形可以包含文本框：

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

然后，您可以使用相同的 `setHidden(true)` 调用来隐藏该文本框。

## 常见陷阱及避免方法

| 症状 | 原因 | 解决方案 |
|---------|-------|-----|
| 即使调用 `setHidden(true)`，形状仍然出现 | 文档在设置隐藏标志之前已保存。 | 确保在 `doc.save()` 之前调用 `setHidden(true)` **。** |
| 形状尺寸看起来失真 | 在高 DPI 屏幕上点与像素混淆。 | 使用点（72 pt = 1 英寸）以在各平台保持一致的尺寸。 |
| 隐藏的形状仍然打印 | 某些打印机忽略隐藏标志。 | 设置 `Shape.setWrapType(WrapType.NONE)`，并且清除 `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`。 |

## 结论

现在您已经了解如何使用 Aspose.Words for Java **向 Word 文档添加形状**、**插入形状**以及 **隐藏形状**，使其对最终用户不可见但仍是文档结构的一部分。上述完整示例加载文件、插入矩形、隐藏它并保存结果，涵盖了典型用例和多个边缘情况。

接下来，您可以探索相关主题，例如使用自定义填充颜色 **插入形状**、为条件打印 **在 Word 中隐藏形状**，或使用 Aspose.Words 自动化批量文档处理。尝试不同的 `ShapeType` 值、定位选项和可见性标志，以适应您的特定工作流。

祝编码愉快，尽情享受编程式 Word 操作为您的 Java 应用带来的灵活性！

## 接下来您应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方法。

- [使用 Aspose.Words 在 Java 中以编程方式创建 Word 文档，添加并隐藏形状](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [如何在 Word 文档中使用 Java 隐藏形状](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [使用 Aspose.Words 创建空白 .docx Word 文档并添加隐藏的矩形形状](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}