---
category: general
date: 2026-10-26
description: 学习如何使用 Aspose.Words for Java 编程创建 Word 文档、添加形状以及在 Word 中隐藏对象——一步步指南。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: zh
lastmod: 2026-10-26
og_description: 使用 Aspose.Words for Java 编程创建 Word 文档，学习如何在 Word 中添加形状并隐藏对象。完整可运行的示例。
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: 使用 Java 编程创建 Word 文档 – 添加并隐藏形状
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: 在 Java 中以编程方式创建 Word 文档并添加形状
url: /zh/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中以编程方式创建 Word 文档并添加形状

如果您需要**以编程方式创建 Word 文档**，本教程将准确展示如何操作，添加形状，然后在 Word 中隐藏该对象。无论您是在构建报告生成器还是自动化合同系统，您都能在几分钟内获得完整的、可直接运行的解决方案。

您将学习如何：

* 使用 Aspose.Words for Java 初始化 Word 文档。  
* 使用**how to add shape**技术插入椭圆（或任何其他形状）。  
* 隐藏该形状，使其在打开文件时永不出现，解答**how to hide shape**问题。  

除了 Aspose.Words 库外，无需任何外部工具，代码可在 Java 17 及更高版本上运行。

## 先决条件

在开始之前，请确保您拥有：

* 已安装 Java Development Kit (JDK) 17 或更高版本。  
* 用于管理依赖的 Maven 或 Gradle（示例使用 Maven）。  
* 有效的 Aspose.Words for Java 许可证（免费评估版可用于测试）。  

如果您是 Aspose.Words 的新手，请参考官方的 Getting Started 指南，但您无需阅读它即可跟随本教程。

## Maven 依赖

将以下依赖添加到您的 `pom.xml`：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **专业提示：**保持版本号为最新；较新版本包含形状处理的错误修复。

## 步骤 1：以编程方式创建 Word 文档 – 初始化文档

当您**以编程方式创建 Word 文档**时，首先要实例化一个 `Document` 对象。该对象在内存中表示整个 .docx 文件。

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*此步骤的重要性*：`Document` 类是所有 Word 处理操作的入口。没有它，您无法添加页面、段落或形状。

## 步骤 2：如何添加形状 – 插入椭圆

现在我们来讨论教程中的**how to add shape**部分。Aspose.Words 支持多种形状类型（Ellipse、Rectangle、TextBox 等）。下面我们插入一个宽高为 50 点的椭圆。

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

`insertShape` 方法返回一个 `Shape` 对象，您可以进一步自定义——颜色、线条样式、旋转等。坐标以点为单位（1/72 英寸）。

*为什么要添加形状*：形状可用于水印、装饰元素或占位符，您随后可以隐藏或替换它们。

## 步骤 3：如何隐藏形状 – 使对象在 Word 中不可见

为了解答**how to hide shape**问题，只需将形状的 `Hidden` 属性设为 `true`。这会告诉 Word 将该形状视为隐藏对象，从而在文档视图或打印时都不渲染。

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

如果您需要为特定用户或条件**在 Word 中隐藏对象**，可以在运行时根据业务逻辑切换此属性。

> **注意：**隐藏的形状仍然是文档 XML 结构的一部分。稍后可以通过设置 `setHidden(false)` 将其显示。

## 步骤 4：保存文档

在添加并隐藏形状后，将文档写入磁盘。

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

当您在 Microsoft Word 中打开 `HiddenShapeDemo.docx` 时，会看到一个空白页，因为椭圆已被隐藏。除此之外，文档的行为与普通 Word 文件相同。

## 完整工作示例

将所有部分组合在一起，下面是完整的可运行程序：

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**预期输出**

```
Document created successfully.
```

打开 `HiddenShapeDemo.docx` 会显示一个空白页；隐藏的椭圆未渲染，确认**hide object in Word**操作成功。

## 边缘情况和变体

| 情况 | 更改内容 | 原因 |
|-----------|----------------|-----|
| 隐藏矩形而不是椭圆 | 在 `insertShape` 中使用 `ShapeType.RECTANGLE` | 不同的视觉占位符 |
| 一次隐藏多个形状 | 遍历 `doc.getChildNodes(NodeType.SHAPE, true)` 并调用 `setHidden(true)` | 适用于批量处理 |
| 仅在打印视图中显示形状 | 设置 `shape.setVisible(false)` 并 `shape.setPrint(true)` | Word 区分屏幕可见性和打印可见性 |
| 使用不同的测量单位 | 调用 `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` | 符合您的布局要求 |

## 常见陷阱

* **忘记调用 `setHidden(true)`** – 形状将正常显示。  
* **在隐藏形状之前保存文档** – 顺序很重要；先隐藏再保存。  
* **使用过时的 Aspose.Words 版本** – 较旧的版本可能没有 `setHidden` API。  

始终在目标版本的 Microsoft Word 中测试生成的文件，以确保隐藏状态如预期工作。

## 结论

在本指南中，您学习了如何使用 Aspose.Words for Java **以编程方式创建 Word 文档**、**添加形状**以及**在 Word 中隐藏对象**。完整示例演示了从初始化文档到保存形状永不出现的文件的全部步骤。

从这里您可以：

* 尝试其他形状类型（`ShapeType.LINE`、`ShapeType.TEXT_BOX`）。  
* 将隐藏形状与书签结合，创建动态模板。  
* 探索 `setVisible` 和 `setPrint` 属性，以更细粒度地控制对象可见性。

祝编码愉快，尽情享受 Word 文档的自动化！

## 接下来您应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [如何使用 Aspose.Words for Java 创建空白 Word 文档](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [如何使用 Java 在 Word 文档中隐藏形状](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [创建 Word 文档 Java – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}