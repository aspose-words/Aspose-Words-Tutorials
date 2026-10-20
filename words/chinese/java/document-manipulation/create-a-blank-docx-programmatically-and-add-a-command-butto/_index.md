---
category: general
date: 2026-10-20
description: 使用 Java 编程创建空白 DOCX 并嵌入命令按钮。学习完整的创建 Word 文档代码，以保存带按钮的 Word 并设置命令按钮的标题。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: zh
lastmod: 2026-10-20
og_description: 以编程方式创建空白 DOCX 并嵌入命令按钮。按照此分步 Java 指南保存带按钮的 Word 并设置命令按钮的标题。
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: 以编程方式创建空白 DOCX – 添加命令按钮
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: 以编程方式创建空白 DOCX 并添加命令按钮
url: /zh/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 以编程方式创建空白 DOCX 并添加命令按钮

如果您需要**以编程方式创建空白 DOCX**，本教程将向您展示如何直接在文件中嵌入命令按钮。您将获得完整的*create word document code*，该代码可保存带有按钮的 Word 文档，让您**set command button caption**，并兼容最新的 Aspose.Words for Java 库。

在 DOCX 文件中嵌入交互式控件非常有用，尤其是当您希望分发能够触发宏、启动外部程序，或仅仅通过可点击的“Click Me”按钮来引导用户的模板时。下面的步骤涵盖了从初始化空白文档到将最终文件持久化到磁盘的全部过程。

## 前置条件

在开始之前，请确保您具备以下条件：

* 已安装 Java 17 或更高版本。
* 已安装 Maven（或您偏好的构建工具）用于管理依赖。
* Aspose.Words for Java 23.9 或更高版本。将依赖添加到您的 `pom.xml` 中：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* 一个 IDE，例如 IntelliJ IDEA 或 VS Code（任何支持 Java 的编辑器均可）。

## 以编程方式创建空白 DOCX – 步骤详解

以下章节将整个过程拆分为清晰的编号步骤。每一步都会解释**为什么**需要这样做，而不仅仅是**怎么写**。

### 步骤 1：初始化一个新的空白文档

空白文档是您放置命令按钮的画布。Aspose.Words 为此提供了 `Document` 类。

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Why this matters*: 从空的 `Document` 开始，可确保没有隐藏的格式或现有控件干扰您稍后添加的按钮。

### 步骤 2：设置 `DocumentBuilder`

`DocumentBuilder` 是一个帮助器，允许您插入内容（包括 OLE 控件），而无需处理底层节点操作。

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters*: 构建器维护当前光标位置，因此按钮会精确放置在您指定的位置。

### 步骤 3：插入 OLE 命令按钮

Word 将交互式控件视为 OLE（对象链接与嵌入）对象。Aspose.Words 通过 `Forms2OleControl` 暴露了相应的接口。

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Why this matters*: 插入控件会创建一个占位符，您随后可以配置（类型、标题、位置）。

### 步骤 4：配置按钮 – 类型、标题和位置

您必须定义控件的类型（`COMMANDBUTTON`），设置用户可见的标题，并将其放置在页面上。

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Why this matters*:  
* **Type** 告诉 Word 该控件表现为可点击的按钮。  
* **Caption** 是用户看到的文字；修改它即是 **set command button caption** 的方式。  
* **Left** 和 **Top** 控制精确的放置位置，这在您 **add command button word** 文档需要精确布局时尤为关键。

### 步骤 5：保存带有嵌入按钮的文档

最后，将文件写入磁盘。生成的文件可在 Microsoft Word 中打开，按钮将保持完整功能。

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Why this matters*: 此步骤 **saves Word with button**，使控件在不同机器间保持持久。该文件可作为模板分发，或用于自动化报表生成流水线。

## 完整工作示例

将下面的整个类复制到名为 `CommandButtonDemo.java` 的文件中，将 `YOUR_DIRECTORY` 替换为真实路径，然后使用 `mvn compile exec:java` 运行。

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### 预期结果

打开 `CommandButton.docx` 时：

* 文档除了一个标有 **Click Me** 的按钮外，完全为空白。  
* 点击按钮会显示 Word 的默认行为（除非附加宏，否则什么也不做），从而确认 OLE 控件已正确嵌入。

## 常见问题与边缘情况

| Question | Answer |
|----------|--------|
| **Can I change the button size?** | Yes. Use `commandButton.setWidth(double)` and `commandButton.setHeight(double)` to adjust dimensions in points. |
| **What if I need a macro attached to the button?** | The button itself is just an OLE control. You must add a VBA macro to the document manually or via the Aspose.Words `Document` API’s `addMacro` utilities. |
| **Will the button work in LibreOffice?** | LibreOffice supports limited OLE controls. The button appears, but its click behavior may differ. |
| **How to add multiple buttons?** | Repeat Steps 3‑4 with a new `Forms2OleControl` instance. Adjust `setLeft`/`setTop` for each button to avoid overlap. |
| **Is the code compatible with .NET?** | The same logic applies, but you’d use `Aspose.Words` for .NET classes (`Document`, `DocumentBuilder`, `Forms2OleControl`). |

## 来自实践的技巧

* **Pro tip:** Use `builder.moveToDocumentEnd()` before inserting the button if you want it at the very end of the document, regardless of prior content.  
* **Watch out for:** Very small `Left`/`Top` values can place the button outside the printable area, making it invisible in Word’s layout view.  
* **Performance note:** Inserting many OLE controls can increase file size. If you only need a visual cue, consider using a plain `Shape` with a hyperlink instead.

## 结论

您现在已经掌握了如何**以编程方式创建空白 DOCX**并使用 Java 嵌入功能完整的命令按钮。教程覆盖了完整的 *create word document code* 工作流，演示了如何**save Word with button**，展示了正确的**add command button word** 元素使用方式，并解释了如何**set command button caption**。

接下来您可以：

* 添加更多 OLE 控件（复选框、下拉框）以构建更丰富的表单。  
* 附加 VBA 宏，使按钮执行自定义操作。  
* 将此技术与文档邮件合并结合，生成动态、交互式模板。

欢迎尝试不同的按钮样式、位置以及额外控件，以满足您的具体业务需求。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您进一步掌握 API 的其他功能，并在项目中探索替代实现方案。

- [Create blank word document with a command button – step‑by‑step guide](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [How to Insert ActiveX Button in Word – Set Button Caption](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Create Blank Word Document with Java – Full Aspose.Words Guide](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}