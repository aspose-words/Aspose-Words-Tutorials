---
category: general
date: 2026-07-16
description: 使用 Aspose.Words for Java 在 Word 文档中以编程方式设置按钮大小。了解如何插入 ActiveX 按钮、设置按钮位置等。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: zh
lastmod: 2026-07-16
og_description: 使用 Java 在 Word 文档中设置按钮大小。本分步指南展示如何插入 ActiveX 按钮、设置按钮位置以及以编程方式添加按钮。
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: 使用 Java 在 Word 中设置按钮大小 – 完整 Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: 使用 Java 在 Word 中设置按钮大小 – 完整 Aspose.Words 指南
url: /zh/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Java 设置 Word 中按钮大小 – 完整 Aspose.Words 指南

是否曾想过如何在不打开 UI 的情况下在 Word 文件中 **设置按钮大小**？你并非唯一有此需求的人。当你需要即时生成填好表单的文档——比如带有“Submit”按钮的入职资料包——以编程方式完成可以节省数小时的手工工作。

在本教程中，我们将逐步演示 **插入 ActiveX 按钮**、调整其尺寸、正确定位并最终保存文件的完整步骤。完成后，你将能够使用 Aspose.Words for Java **以编程方式添加按钮** 控件到任何 Word 文档中。

## 前置条件 – 开始之前你需要的东西

- **Java Development Kit (JDK) 8+** – 代码可在任何近期的 JDK 上运行。
- **Aspose.Words for Java** 库（从官方网站下载最新的 JAR）。  
- 你选择的 **IDE**——IntelliJ IDEA、Eclipse，甚至是简单的文本编辑器都可以。
- 对 Java 语法有基本了解；不需要深入的 Word 自动化知识。

> *小贴士：* 将 Aspose.Words JAR 放在项目的 classpath 中，否则在尝试导入 `com.aspose.words.*` 时会立即遇到 `ClassNotFoundException`。

## 步骤 1：创建新 Word 文档

我们首先创建一个空白文档并实例化 `DocumentBuilder`。可以把 builder 看作一支笔，能够在文件内部绘制任何内容。

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> *这有什么重要性：* `Document` 对象代表整个 .docx 文件，而 `DocumentBuilder` 是核心工具，允许我们插入段落、表格以及——是的——ActiveX 控件。

## 步骤 2：插入 ActiveX 按钮 – “插入 ActiveX 按钮” 时刻

现在我们实际在文档中 **插入 activex 按钮**。Aspose.Words 提供了便利的方法 `insertForms2OleControl`，该方法返回一个 `Forms2OleControl` 对象。

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *内部发生了什么？* `Forms2OleControlType.COMMAND_BUTTON` 告诉 Word 我们需要一个经典的 CommandButton，即在 UI 的 Developer 选项卡中可以插入的那种按钮。

## 步骤 3：设置按钮大小和位置 – 核心的 “设置按钮大小” 逻辑

这正是主要关键词发挥作用的地方。我们将 **设置按钮大小** 并 **设置按钮位置**，使控件恰好出现在页面上我们想要的位置。

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> *你为何需要关注：* Points 是 Word 的原生度量单位（1 point = 1/72 英寸）。通过调整 `setLeft`、`setTop`、`setWidth` 和 `setHeight`，你可以实现像素级的精确控制——不再出现“在我的屏幕上看起来合适，但在打印机上不对”的情况。

> *常见陷阱：* 忘记设置宽度或高度会导致按钮保持默认尺寸，可能太小而无法点击。务必同时指定两者。

## 步骤 4：保存文档 – “创建 Word 文档按钮” 完成

最后，我们将文件写入磁盘。名称暗示我们正在 .docx 中 **创建一个 Word 文档按钮**。

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

当你在 Microsoft Word 中打开 `CommandButtonDemo.docx` 时，你会看到一个 **Submit** 按钮，距离左边缘 100 pt，距离顶部 150 pt，尺寸为 80 × 30 pt。点击该按钮将在 UI 中触发默认的 ActiveX 行为（如有需要，你以后可以使用 VBA 进行绑定）。

### 预期输出截图

![显示已插入按钮并设置按钮大小的 Word 文档](https://example.com/images/set-button-size.png "使用 Aspose.Words for Java 设置按钮大小的 Word 文件截图")

*Alt 文本:* 使用 Java 在 Word 文档中设置按钮大小

## 步骤 5（可选）：添加更多控件或设置按钮样式

如果你需要 **以编程方式添加按钮** 控件，超出单个 Submit 按钮，只需使用新的名称和标题重复插入块即可。你还可以调整字体、背景颜色，甚至以后绑定 VBA 宏。

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *提示：* 保持所有按钮尺寸一致，以获得专业外观。快速方法是将宽度/高度存放在常量中。

## 常见问题与边缘情况

### “我可以使用厘米而不是点来设置按钮大小吗？”

Word 的 API 只接受点（points），但你可以将厘米转换为点（`points = cm * 28.3465`）。如果更喜欢公制单位，可编写一个小的辅助方法。

### “如果我需要按钮出现在特定页面怎么办？”

插入按钮后，你可以使用 `builder.moveToPage(pageNumber)` 将光标移动到指定页面。随后立即插入控件，并按上述方式设置其位置。

### “这在 .doc（Word 97‑2003）文件中有效吗？”

是的——Aspose.Words 会自动处理旧格式。只需在 `doc.save("Demo.doc")` 中更改文件扩展名即可。

## 完整、可运行的示例

下面是完整的程序代码，你可以直接复制粘贴到 Java 类中并立即运行（前提是 Aspose.Words JAR 已在 classpath 中）。

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

运行程序，打开生成的 `CommandButtonDemo.docx`，你会看到两个尺寸恰当的按钮，已准备好交互。

## 结论 – 你已掌握在 Word 中设置按钮大小

我们刚刚完整演示了使用 Aspose.Words for Java 实现 **设置按钮大小** 和 **设置按钮位置** 的端到端解决方案。按照这些步骤，你可以 **插入 activex 按钮**、**以编程方式添加按钮** 控件，最终 **创建 Word 文档按钮** 元素，使其行为完全符合你的需求。

接下来怎么办？尝试将按钮嵌入表格单元格，或附加一个在提交前验证表单字段的 VBA 宏。同样的模式同样适用于其他 ActiveX 控件，如复选框或下拉框——只需将 `Forms2OleControlType.COMMAND_BUTTON` 替换为相应的枚举值即可。

如果遇到任何问题，请在下方留言。祝编码愉快，尽情享受自动化 Word 文档创建的强大力量！

## 接下来你应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，构建在已演示的技巧之上。每个资源都包含完整的可运行代码示例和逐步解释，帮助你掌握更多 API 功能并在项目中探索替代实现方案。

- [如何在 Aspose.Words for Java 中设置 LoadOptions](/words/english/java/document-loading-and-saving/using-load-options/)
- [如何使用 Aspose.Words for Java 从 Word 文档中删除页脚](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java：Word 文档处理综合指南](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}