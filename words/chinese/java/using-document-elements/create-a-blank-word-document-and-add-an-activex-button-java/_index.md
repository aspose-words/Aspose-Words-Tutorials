---
category: general
date: 2026-10-16
description: 使用 Java 创建一个空白的 Word 文档，并学习如何使用 Aspose.Words 添加 ActiveX 按钮、设置其标题以及调整其尺寸。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: zh
lastmod: 2026-10-16
og_description: 使用 Java 创建一个空白的 Word 文档，然后添加 ActiveX 按钮，设置其标题，并使用 Aspose.Words 定义其尺寸。
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: 创建空白 Word 文档并嵌入 ActiveX 按钮 – Java 指南
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: 创建一个空白的 Word 文档并添加 ActiveX 按钮（Java）
url: /zh/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建空白 Word 文档并添加 ActiveX 按钮 (Java)

如果您需要以编程方式**创建空白 Word 文档**，本指南将向您展示如何使用 Java 和 Aspose.Words 实现。您还将学习如何**添加 ActiveX 按钮**、**设置按钮标题**以及**设置按钮尺寸**，以便控件呈现出您期望的外观。

本教程涵盖：

* 使用 Aspose.Words for Java 初始化一个空的 Word 文件。  
* 插入 ActiveX `CommandButton` 控件。  
* 配置按钮的标题和大小。  
* 保存最终的 `.docx` 文件。

您应具备基本的 Java 知识，并使用最新版本的 Aspose.Words for Java 库（代码在 23.9 及以后版本均可运行）。无需额外的依赖项。

![使用 ActiveX 按钮创建空白 Word 文档](/images/activex-button-example.png){: .align-center alt="使用 ActiveX 按钮创建空白 Word 文档"}

## 使用 Aspose.Words 创建空白 Word 文档

第一步是实例化一个空的 `Document` 对象。该对象在内存中表示整个 Word 文件，并提供 `DocumentBuilder` 类用于编辑。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**为什么这很重要：**  
创建空白文档为您提供了干净的画布，避免任何隐藏的样式或节影响后续的布局计算。

## 向文档中添加 ActiveX 按钮

Aspose.Words 允许通过 `Forms2OleControl` 类嵌入传统的 ActiveX 控件。以下代码在当前光标位置插入一个 `CommandButton` 控件。

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**提示：** `setOleClassName` 的值 `"Forms.CommandButton.1"` 是标准 Microsoft Forms 按钮的 ProgID。使用其他 ProgID（例如 `"Forms.CheckBox.1"`）将插入不同类型的控件。

## 设置按钮标题

标题是显示在按钮表面的文字。您可以在保存文档之前随时更改它。

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**为什么需要这样做：** 当控件的用途明确时，用户才能理解它。设置有意义的标题可提升可用性，尤其是在 Windows 上的 Word 中打开文档时。

## 设置按钮尺寸

位置和大小使用点（1 point = 1/72 英寸）指定。根据您的布局调整这些值。

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**常见变体：**

| 场景 | 调整 |
|----------|------------|
| 触摸屏的大按钮 | 按比例增加 `setWidth` 和 `setHeight` |
| 页面居中按钮 | 计算 `left = (pageWidth - width) / 2` |
| 列中多个按钮 | 对每个新按钮递增 `setTop` |

## 保存包含 ActiveX 按钮的文档

最后，将文档写入磁盘。`.docx` 格式会在 Windows 版 Microsoft Word 中保留 ActiveX 控件。

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**预期结果：** 在 Windows 上的 Word 中打开 `ActiveXCommandButton.docx` 时，会看到一个空白页面，左边距 100 pt、上边距 200 pt 处有一个标注为 **Click Me** 的可点击按钮。

## 完整可运行示例

将下面的整个类复制到您的 IDE 中，向项目类路径添加 Aspose.Words for Java JAR，然后运行它。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

运行程序后会在工作目录生成 `ActiveXCommandButton.docx`。使用 Microsoft Word（Windows）打开，以验证按钮是否完全按照配置显示。

## 为什么推荐这种方法

* **简洁性：** 仅使用核心 Aspose.Words API；无需 COM 互操作或额外库。  
* **可移植性：** 代码可在任何支持 Java 的平台上运行，尽管 ActiveX 控件本身仅在 Windows 版 Word 上有效。  
* **可维护性：** 所有属性（标题、尺寸、位置）均通过清晰的自解释方法设置，使未来的调整变得简单。

## 常见问题及避免方法

| 常见问题 | 解决方案 |
|---------|------------|
| 按钮在 macOS 或 Linux 的 Word 中不显示 | ActiveX 控件仅限 Windows。请使用其他控件（例如内容控件）以实现跨平台文档。 |
| 标题被截断 | 确保按钮宽度足以容纳文本；增加 `setWidth` 或使用更短的标题。 |
| 按钮与其他内容重叠 | 调整 `setTop` 和 `setLeft` 值，或在控件前插入新段落以为其留出空间。 |

## 下一步

现在您已经能够**创建空白 Word 文档**、**添加 ActiveX 按钮**、**设置按钮标题**以及**设置按钮尺寸**，可以进一步探索：

* 通过 VBA 宏添加事件处理代码（需要嵌入宏模块）。  
* 在表格布局中插入多个控件，以创建类似表单的文档。  
* 使用 Aspose.Words 的 **FormField** API 实现跨平台表单解决方案。

尝试不同的尺寸、位置和标题，以适配您的特定文档设计。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在自己的项目中探索替代实现方案。

- [创建 Word 文档 Java – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [如何使用 Aspose.Words for Java 的 DocumentBuilder 创建表单字段并添加内容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [使用 Aspose.Words for Java 为文档添加水印](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}