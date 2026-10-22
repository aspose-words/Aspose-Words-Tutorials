---
category: general
date: 2026-07-26
description: 如何使用 Aspose.Words 在 Word 文档中插入 ActiveX 按钮——只需几行代码即可设置按钮的标题、位置和大小。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: zh
lastmod: 2026-07-26
og_description: 如何使用 Aspose.Words 在 Word 文档中插入 ActiveX 按钮。请按照本分步教程设置按钮的标题、位置和大小。
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: 如何在 Word 中插入 ActiveX 按钮 – 快速指南
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: 如何在 Word 中插入 ActiveX 按钮 – 设置按钮标题
url: /zh/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中插入 ActiveX 按钮 – 设置按钮标题

有没有想过 **如何在不打开 UI 的情况下向 Word 文件插入 ActiveX** 控件？你并不是唯一有此需求的人。在许多企业应用中，你需要一个可点击的按钮来运行宏，而以编程方式实现可以节省数小时的工作。本文指南将准确展示如何使用 Aspose.Words for Java **插入 ActiveX** CommandButton，并且——是的——如何 **设置按钮标题** 让用户知道该点击什么。

我们将逐步演示整个过程：从设置库、创建新文档、放置按钮、微调大小和位置、添加友好的标题，最后保存文件。完成后，你将得到一个可运行的 `.docx`，在 Word 中打开时会出现一个功能完整的 ActiveX 按钮，随时准备触发你的宏。

---

## 你将学到的内容

- 在 Java 项目中安装并引用 Aspose.Words。  
- 创建新的 `Document` 和 `DocumentBuilder`。  
- 使用一行代码 **插入 ActiveX** CommandButton 控件。  
- **设置按钮标题**，调整其位置并定义尺寸。  
- 保存文档并在 Word 中打开以查看结果。

不需要任何 ActiveX 先前经验；只需具备基本的 Java 知识和一份 Aspose.Words 即可。

---

## 前提条件

- 在机器上已安装 Java 8 或更高版本。  
- 用于依赖管理的 Maven 或 Gradle（我们将展示 Maven 示例）。  
- **Aspose.Words for Java** 的授权或评估版（免费试用版足以完成本演示）。  
- Microsoft Word（任意近期版本）用于测试生成的文件。

---

## 步骤 1：在项目中设置 Aspose.Words

首先——添加 Aspose.Words 依赖。如果使用 Maven，请将以下内容放入 `pom.xml`：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Gradle 用户可以添加：

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

运行 `mvn clean install`（或 `gradle build`）后，库将位于类路径中，您即可开始编码。

---

## 步骤 2：创建新文档和构建器

`Document` 代表整个 Word 文件，而 `DocumentBuilder` 允许您编辑它。可以把构建器想象成在全新画布上绘图的笔。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

为什么要从空白文档开始？这确保您对添加的每个元素拥有完全控制，并且不会在后期遇到隐藏的格式问题。

---

## 步骤 3：插入 ActiveX CommandButton 控件

现在轮到主角登场。Aspose.Words 提供 `insertForms2OleControl` 方法，可放置您指定的任何 ActiveX 控件。这里我们请求一个 **CommandButton**。

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

该方法返回一个 `Forms2OleControl` 对象，允许您以编程方式访问按钮属性。这就是 **如何插入 ActiveX** 只需一行代码——无需与底层 COM API 纠缠。

---

## 步骤 4：定位、尺寸并设置按钮标题

一个漂浮在页面中间的按钮并不实用。您需要将其放置在用户预期的位置，赋予合适的尺寸，且——最重要的是——**设置按钮标题**，让用户知道点击后会发生什么。

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**为什么使用这些数值？** Word 使用点（1 pt ≈ 1/72 英寸）。`100 pt` 大约距左侧 1.4 英寸，`150 pt` 大约距顶部 2.1 英寸——大致位于标准 A4 页的中心。根据您的布局自行调整。

设置标题至关重要；如果没有标题，按钮看起来像一个空白矩形。`setCaption` 方法接受任意字符串，您以后可以根据需要进行本地化。

---

## 步骤 5：保存文档

最后，将文档写入磁盘。您可以选择任意文件夹，只需确保路径已存在。

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

当您在 Word 中打开 `ActiveXButton.docx` 时，会看到一个标有 **“Click Me.”** 的按钮。双击它时，Word 会提示您启用宏（因为 ActiveX 控件被视为宏启用）。随后，您可以将 VBA 例程绑定到按钮的 `Click` 事件。

---

## 边缘情况与可能忽略的技巧

- **宏启用格式**：Word 在普通 `.docx` 文件中会禁用 ActiveX 控件，除非用户启用宏。如果需要按钮开箱即用，请考虑使用 `doc.save(outputPath, SaveFormat.DOCM);` 将文件保存为 `.docm`（宏启用）。
- **兼容性**：Word 旧版本（2007 之前）使用二进制 `.doc` 格式。Aspose.Words 可以保存为该格式，但控件属性可能会略有不同。
- **安全设置**：某些企业环境会锁定 ActiveX。如果按钮未出现，请检查 Word 的“受信任中心 → ActiveX 设置”。
- **多个按钮**：需要多个按钮吗？只需重复调用 `insertForms2OleControl` 并调整每个按钮的 `Left`/`Top` 值。记录返回的对象，以便为每个按钮设置单独的标题。
- **标题样式**：标题继承默认字体。若要更改，需要编辑底层 XML 或在插入后应用 Word 样式——这超出本快速指南的范围，但可通过 Aspose.Words 的 `ParagraphFormat` API 实现。

---

## 完整工作示例

下面是完整的、可直接运行的 Java 类。复制粘贴到 IDE 中，调整输出路径，然后点击 **Run**。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**预期输出**：运行后，控制台会打印保存位置。打开生成的 Word 文件，会看到一个大致位于页面中间、标签为 “Click Me” 的按钮。点击它将触发标准的 ActiveX click 事件（您需要附加 VBA 宏来响应）。

---

## 结论

现在，您已经了解了如何使用 Aspose.Words 以编程方式向 Word 文档插入 ActiveX CommandButton 控件，并且已经看到如何 **设置按钮标题**、定位以及设定控件尺寸。这种方法消除了手动 UI 操作，能够干净地集成到自动化报告生成器中，并为您提供对控件的完整控制 the

## 接下来您应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能，并在自己的项目中探索替代实现方法。

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert an Image into Word Document Header | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}