---
category: general
date: 2026-08-14
description: 使用 Aspose.Words 在 Java 中创建 docx ActiveX 按钮。学习如何以编程方式在 Word 中添加表单按钮并保存文档。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: zh
lastmod: 2026-08-14
og_description: 使用 Aspose.Words 在 Java 中创建 docx ActiveX 按钮。本指南展示如何在 Word 中添加表单按钮、进行配置并保存文件。
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: 在 Java 中创建 docx ActiveX 按钮——一步步教程
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: 在 Java 中创建 docx ActiveX 按钮 – 完整编程指南
url: /zh/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中创建 docx ActiveX 按钮 – 完整编程指南

如果您需要在 Java 中 **create docx ActiveX button**，本指南将带您完成整个过程。您将看到如何在 Word 中添加表单按钮，配置其属性，并生成可直接使用的 .docx 文件。

在自动化传统 Word 表单时，使用 ActiveX 控件是常见需求。在本教程中，您将学习如何使用 Aspose.Words for Java 库 **add form button word** 文档，从而在无需手动编辑的情况下嵌入交互式控件。

## 您需要的条件

* Java 17 或更高版本（代码在早期版本也能编译，但推荐使用 Java 17）。
* Aspose.Words for Java 23.10 或更高版本 – 从 Aspose 网站下载 JAR 或添加 Maven 依赖。
* IDE（IntelliJ IDEA、Eclipse 或 VS Code）或简单的文本编辑器和命令行构建工具。
* 基本的 Java 语法和面向对象编程知识。

## 使用 Aspose.Words 创建 docx ActiveX 按钮

以下步骤展示了创建 **create docx ActiveX button** 对象并将其嵌入 Word 文档的完整顺序。

### 步骤 1：设置项目并导入 Aspose.Words

如果使用 Maven，请在 `pom.xml` 中添加 Aspose.Words 依赖：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

或者，如果您更喜欢 Gradle：

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

依赖解析后，在 Java 源文件中导入所需的类：

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

这些导入让您可以使用 `Document`、`DocumentBuilder` 和用于插入 ActiveX 控件的 `Forms2OleControl` API。

### 步骤 2：创建一个新的空白文档

实例化一个 `Document` 对象，它代表一个准备接收内容的空白 Word 文件。

```java
// Step 2: Create a new blank document
Document document = new Document();
```

首先创建文档可确保后续的 builder 在干净的画布上操作。

### 步骤 3：初始化 DocumentBuilder

`DocumentBuilder` 提供了用于插入文本、图像和控件的流畅接口。将其附加到您刚创建的文档上。

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

builder 会跟踪文档内部的当前光标位置，从而确保下一次插入正好发生在您需要的位置。

### 步骤 4：插入 ActiveX CommandButton 控件

使用 `insertForms2OleControl` 方法嵌入 ActiveX `CommandButton`。此方法返回一个可进一步配置的 `Forms2OleControl` 实例。

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

此时 .docx 文件已包含按钮的占位符，但尚未设置可视的标题或尺寸。

### 步骤 5：配置按钮属性

设置控件的名称、标题和布局属性。这些值决定按钮在 Word 中的显示方式以及以后通过 VBA 或自动化脚本引用的方式。

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **技巧提示：** Word 使用点（point）来测量位置（1 pt ≈ 1/72 英寸）。调整 `setTop` 和 `setLeft` 以使按钮与周围内容对齐。

### 步骤 6：保存文档

最后，将文档写入磁盘。使用 `.docx` 扩展名以保持文件为现代的 Office Open XML 格式。

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

在 Microsoft Word 中打开生成的文件时，您会看到一个位于您指定坐标的 **Submit** 按钮。除非附加 VBA 代码，否则在 Word 中点击该按钮不会触发任何操作，但该控件在基于表单的工作流中是完全可用的。

## 常见问题与边缘情况

| 问题 | 答案 |
|----------|--------|
| **我需要特殊的 Word 版本吗？** | ActiveX 控件在 Windows 上的桌面版 Microsoft Word 中受支持。它们在 Mac 版 Word 或 Word Online 中不可用。 |
| **我可以在 `.doc` 文件中使用吗？** | 可以。将文档保存为 `.doc` 扩展名（`document.save("ActiveXButton.doc")`）。相同的 API 也适用于旧的二进制格式。 |
| **如果按钮没有出现怎么办？** | 确保 **文件 → 选项 → 信任中心 → 信任中心设置 → ActiveX 设置** 允许 ActiveX 控件。同时确认文档未在“受保护视图”中打开。 |
| **我可以添加其他 ActiveX 控件吗？** | 当然。将 `Forms2OleControlType.COMMAND_BUTTON` 替换为 `Forms2OleControlType.CHECK_BOX`、`RADIO_BUTTON` 等。 |
| **是否有尺寸限制？** | 控件尺寸仅受页面布局限制。非常大的尺寸可能导致布局溢出。 |

## 完整、可运行的示例

下面是一个完整的 Java 类，您可以复制、编译并运行。它包含所有导入、main 方法以及为清晰起见的内联注释。

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**预期结果：** 运行程序后，工作目录中会出现 `ActiveXButton.docx`。在 Microsoft Word 中打开它会显示一个位于首页左上角附近的可点击 **Submit** 按钮。

## 结论

现在，您已经了解如何使用 Aspose.Words 在 Java 中 **create docx ActiveX button** 对象，并且已经看到如何以编程方式 **add form button word** 文档。上述步骤——设置项目、创建文档、插入控件、配置属性以及保存——涵盖了从头到尾的完整工作流。

接下来，您可能会探索：

* 添加响应按钮点击的 VBA 宏。
* 嵌入其他 ActiveX 控件，如复选框或列表框。
* 自动生成包含多个交互元素的多页表单。

随意尝试不同的尺寸、位置和标题，以满足您特定的表单设计需求。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [如何使用 Aspose.Words for Java 中的 DocumentBuilder 创建表单字段并添加内容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [如何使用 Aspose.Words for Java 加载 HTML 并保存为 DOCX](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [如何使用 Aspose.Words for Java 创建 PDF 文档 | 文档处理 API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}