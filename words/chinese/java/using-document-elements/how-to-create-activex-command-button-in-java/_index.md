---
category: general
date: 2026-10-07
description: 在 Java 中创建 ActiveX 命令按钮，并以编程方式将命令按钮添加到 Word 文档。了解如何设置按钮的左上位置。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: zh
lastmod: 2026-10-07
og_description: 在 Java 中创建 ActiveX 命令按钮，将交互式控件嵌入 Word 文档。学习如何以编程方式添加命令按钮、设置其位置并自定义外观。
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: 在 Java 中创建 ActiveX 命令按钮 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: 如何在 Java 中创建 ActiveX 命令按钮
url: /zh/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中创建 ActiveX 命令按钮

如果您需要在 Word 文档中使用 Java **创建 ActiveX 命令按钮**，本指南将手把手教您实现。您将看到一个完整、可运行的示例，**以编程方式添加命令按钮**，使用 `setLeft` 和 `setTop` 定位，并将结果保存为 `.docx` 文件。

在文档中嵌入交互式按钮，可用于构建表单、自动化工作流或直接在 Word 文件中收集用户输入。以下步骤涵盖从项目设置到最终验证的全部内容，您可以直接将代码复制到自己的项目中而不遗漏任何细节。

## 前置条件

在开始之前，请确保您已具备以下条件：

- 已安装 JDK 17 或更高版本  
- Maven 3.8+（或您偏好的构建工具）  
- Aspose.Words for Java 23.9 或更高版本 —— 提供 `DocumentBuilder` 与 OLE 控件支持的库  
- 对 Java 语法和面向对象概念有基本了解  

如果您使用 Maven，请在 `pom.xml` 中添加依赖：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **小贴士：** 使用最新的 Aspose.Words 版本，以获得错误修复和新 OLE 功能。

## 第一步：创建空文档并实例化 DocumentBuilder

**创建 ActiveX 命令按钮**的第一步是实例化一个空的 `Document` 和一个 `DocumentBuilder`。Builder 提供流式 API，用于插入内容，包括 OLE 控件。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 表示内存中的 Word 文件，而 `DocumentBuilder` 则充当光标，帮助您将元素精确放置在所需位置。

## 第二步：插入 OLE 命令按钮控件

ActiveX 控件作为 OLE 对象插入。Aspose.Words 为此提供了 `Forms2OleControl` 类。

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

调用 `insertForms2OleControl()` 时，Aspose 会自动创建一个占位形状，用于承载 ActiveX 按钮。

## 第三步：配置按钮属性

现在您可以 **以编程方式添加命令按钮**的详细信息，如 ProgID、标题和大小。最常用的命令按钮 ProgID 为 `"Forms.CommandButton.1"`。

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### 如何设置按钮的左上坐标

定位按钮时，次要关键词 **how to set button left top**（如何设置按钮左上坐标）变得重要。`setLeft` 和 `setTop` 方法接受以点为单位的数值（1 点 = 1/72 英寸）。

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

根据布局调整这些数值。例如，要将按钮与表格单元格对齐，可计算单元格的坐标并将其传递给 `setLeft`/`setTop`。

## 第四步：保存文档

最后，将文档写入磁盘。文件中将包含可交互的 ActiveX 按钮，打开 Microsoft Word 时即可使用。

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

运行 `main` 方法后会生成 `CommandButton.docx`。在 Word 中打开该文件，若出现提示请启用内容，您将看到一个标记为 **Click Me** 的可点击按钮，位于您指定的坐标位置。

![创建 ActiveX 命令按钮的 Java 示例](/images/activex-button-screenshot.png){.center width=600 alt="创建 ActiveX 命令按钮的 Java 示例截图，显示按钮位于 Word 文档内部"}

## 常见变体与边缘情况

### 添加多个按钮

如果需要多个按钮，请对每个控件重复 **步骤 2** 和 **步骤 3**。记得调整 `setLeft` 和 `setTop`，避免按钮重叠。

### 更改按钮行为

ActiveX 按钮可以在点击时运行 VBA 宏。要关联宏，请使用 `setOnAction` 属性并设置宏名称：

```java
commandButton.setOnAction("MyMacro");
```

确保目标文档中包含相应的 VBA 模块，否则 Word 会报错。

### 兼容性说明

- 该按钮仅在支持 ActiveX 的桌面版 Word（如 Windows 版 Word）中工作。它在 Mac 版 Word 或在线编辑器中会显示为静态图像。  
- 若面向混合环境，建议使用 **内容控件**（`RichTextContentControl`）来替代 ActiveX 控件。

## 完整源码供参考

以下是完整的、可独立运行的示例，您可以直接复制到新的 Maven 项目中并立即执行。

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**预期输出：** 执行后，您将在项目工作目录中看到 `CommandButton.docx`。在 Microsoft Word 中打开该文件，即可看到位于指定位置、标题为 “Click Me” 的按钮。

## 结论

现在，您已经掌握了如何在 Java 中 **创建 ActiveX 命令按钮**、**以编程方式向 Word 文档添加命令按钮**，并使用 **how to set button left top** 方法精确控制其布局。这一技术为您打开了构建丰富交互式 Word 表单的大门，表单可触发宏、启动外部应用或直接在文档内收集用户输入。

### 后续步骤

- 探索其他 ActiveX 控件，如 `Forms.TextBox.1` 或 `Forms.CheckBox.1`。  
- 将多个控件与 VBA 模块结合，实现完整的表单功能。  
- 若需跨平台兼容性，可将 ActiveX 替换为内容控件。  

欢迎尝试不同的尺寸、标题和定位，以匹配您的 UI 设计。如遇问题，请再次确认所使用的 Aspose.Words 版本支持 OLE 控件，并检查 Word 的安全设置是否允许执行 ActiveX。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题，帮助您进一步掌握 API 功能并探索在项目中的替代实现方式，每篇资源均提供完整可运行的代码示例和逐步说明。

- [在 Word 文档中嵌入 OLE 对象和 ActiveX 控件](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [使用 Aspose.Words for Java 的 DocumentBuilder 创建表单字段并添加内容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [使用 Java 在 Word 中创建矩形形状 – 完整指南](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}