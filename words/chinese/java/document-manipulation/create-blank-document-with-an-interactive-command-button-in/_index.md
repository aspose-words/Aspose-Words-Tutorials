---
category: general
date: 2026-09-18
description: 在 Java 中创建空白文档并添加 ActiveX 按钮。学习如何插入命令按钮、构建交互式表单以及保存 Word 文档。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: zh
lastmod: 2026-09-18
og_description: 在 Java 中创建空白文档并嵌入 ActiveX 命令按钮。按照本分步指南构建交互式表单并保存 Word 文件。
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: 在 Word 中创建带交互式命令按钮的空白文档
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: 使用 Java 在 Word 中创建带交互式命令按钮的空白文档
url: /zh/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 Java 创建带交互式命令按钮的空白文档

如果您需要 **创建空白文档** 并在其中包含可点击的按钮，本指南将向您展示如何使用 Aspose.Words for Java 完成此操作。您将学习如何构建交互式表单、添加 ActiveX 按钮，最后保存 Word 文件——全部只需几个简洁的步骤。

在文档中嵌入命令按钮可以将静态的 .docx 转变为用户可以直接在 Microsoft Word 中交互的功能表单。本教程还涵盖了 **如何插入命令按钮**、常见坑点的处理以及将该方案扩展到更复杂表单的技巧。

## 前置条件

开始之前，请确保您具备以下条件：

* Java 17 或更高版本（代码在 JDK 17+ 下编译）
* Aspose.Words for Java 23.9 或更新版本 —— 提供 `Document`、`DocumentBuilder` 和 `Forms2OleControl` 等类
* 能够添加 Aspose.Words 依赖的 IDE 或构建工具（Maven/Gradle）
* 基本的 Java 语法和 Word 文档概念

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## 第一步：创建空白文档

第一步是实例化一个新的 `Document` 对象。该对象代表一个准备好接受内容的空 Word 文件。

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

创建空白文档可以为您提供一块干净的画布，这在您想要 **以编程方式创建 word document** 而不依赖任何预先存在的模板时尤为重要。

## 第二步：初始化 DocumentBuilder

`DocumentBuilder` 是用于添加文本、表格和表单控件的主要类。它作用于您刚创建的 `Document`。

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

构建器会维护当前的插入点，因此后续命令会影响文件中的正确位置。

## 第三步：插入 Forms2Ole 命令按钮控件

Aspose.Words 提供 `Forms2OleControl` 类来处理 ActiveX 控件。要 **添加 activex 按钮**，只需向构建器请求 `COMMANDBUTTON` 类型。

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

`insertForms2OleControl` 方法会在构建器当前光标所在位置插入控件。由于该控件是 ActiveX 对象，它仅在 Microsoft Word 桌面版中工作，Word Online 不支持。

## 第四步：配置按钮的外观和位置

您可以使用控件的 setter 方法设置按钮的标题、大小和位置。位置值以点为单位（1 点 = 1/72 英寸）。

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*为什么要配置这些属性？* 设置 `Top` 和 `Left` 可以确保按钮出现在页面的预期位置，而 `Caption` 定义了用户可见的标签。如果不设置宽度/高度，Word 会使用默认尺寸，可能与您的设计不符。

### 小技巧
如果计划添加多个控件，请在每次插入前调用 `builder.moveToDocumentEnd()`，以避免对象重叠。

## 第五步：保存带有嵌入式命令按钮的文档

最后，将文档写入磁盘。文件扩展名必须为 `.docx`（或针对旧版 Word 的 `.doc`），以保留 ActiveX 控件。

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

当您在 Microsoft Word 中打开 `CommandButton.docx` 时，会看到一个标有 **Click Me** 的按钮。点击它会触发默认的 ActiveX 动作（默认情况下什么也不做）。您可以随后附加宏或 VBA 脚本来自定义行为。

## 如何在已有表单中插入命令按钮（可选）

如果您已经有一个包含文本字段的表单，并希望 **创建交互式表单** 并在其中加入按钮，请按以下额外步骤操作：

1. 加载已有文档：`Document doc = new Document("ExistingForm.docx");`
2. 将构建器移动到目标位置：`builder.moveToParagraph(5, 0); // 第 6 段，第一个节点`
3. 按第 3 步所示插入按钮。
4. 根据段落布局调整按钮的 `Top`/`Left`。

此方法可让您在不重新创建整个文件的前提下，为任何预制的 Word 模板添加 ActiveX 按钮。

## 边缘情况与故障排除

| 情况 | 检查要点 | 推荐解决方案 |
|-----------|---------------|-----------------|
| 按钮在 Word 中未显示 | 确认您在桌面版 Word 中打开文件（Word Online 会剥离 ActiveX）。 | 在 Word 2016+ 桌面版中打开文件。 |
| 标题被截断 | 确认按钮宽度足够容纳文字。 | 增大 `setWidth` 直至标题完整显示。 |
| 保存时抛出 `IOException` | 确认输出目录存在且您拥有写入权限。 | 创建目录或以提升权限运行程序。 |
| 多个按钮重叠 | 前一个插入后构建器光标可能未移动。 | 在插入每个新控件前调用 `builder.moveToDocumentEnd()`。 |

## 完整可运行示例

下面是一段完整的、独立的 Java 程序，您可以直接复制、编译并运行。它演示了 **create blank document**、**add activex button** 与 **save word document** 的完整流程。

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**预期输出**

```
Document created: CommandButton.docx
```

打开 `CommandButton.docx` 后，您会看到单页文档，页面左上方距离 100 pt 处有一个标为 **Click Me** 的按钮。

## 结论

现在您已经掌握了如何 **create blank document**、嵌入 **ActiveX button**，并将普通 Word 文件转变为 **interactive form**。通过熟练 **how to insert command button**，您可以进一步扩展此模式，添加复选框、下拉框，甚至自定义 VBA 逻辑。

接下来，您可以探索以下相关主题：

* 使用文本字段创建 **interactive form**（`builder.insertField`）  
* 添加运行 VBA 宏的 **activex button**（`builder.insertOleObject`）  
* 使用 `Document(docTemplatePath)` 从模板 **create word document**  
* 将生成的 .docx 转为 PDF 并保留按钮（注意：PDF 中按钮会渲染为静态图像）。

欢迎尝试不同的按钮尺寸、位置和标题，以匹配您的 UI 设计。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您在项目中进一步运用这些技巧。每篇资源都提供完整的代码示例和逐步解释，助您掌握更多 API 功能并探索替代实现方案。

- [如何使用 Aspose.Words for Java 中的 DocumentBuilder 创建表单字段并添加内容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [在 Word 文档中创建 VBA 项目](/words/english/net/working-with-vba-macros/create-vba-project/)
- [创建新 Word 文档](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}