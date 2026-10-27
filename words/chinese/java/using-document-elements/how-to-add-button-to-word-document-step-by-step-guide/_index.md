---
category: general
date: 2026-07-20
description: 如何使用 Aspose.Words 向 Word 文档添加按钮。学习在几分钟内使用 DocumentBuilder 插入 Forms2OleControl
  按钮。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: zh
lastmod: 2026-07-20
og_description: 如何使用 Aspose.Words 在 Word 文档中添加按钮。请按照本实用指南使用 Java 嵌入 Forms2OleControl
  CommandButton。
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: 如何在 Word 文档中添加按钮 – 完整的 Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: 如何在 Word 文档中添加按钮 – 步骤指南
url: /zh/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何向 Word 文档添加按钮 – 完整的 Aspose.Words 教程

是否曾想过 **如何在不打开 UI 并点击操作的情况下向 Word 文档添加按钮**？你并不是唯一有此需求的人。许多开发者需要以编程方式嵌入交互式控件——比如在模板中放置一个“Submit”按钮，随后由最终用户填写。好消息是？使用 Aspose.Words for Java，你只需几行代码即可实现。

在本教程中，我们将逐步演示如何使用 `DocumentBuilder` 插入类型为 **CommandButton** 的 `Forms2OleControl`。完成后，你将拥有一个可直接使用的 `.docx` 文件，其中显示一个标有 “Click Me” 的可点击按钮。没有神秘之处，只有清晰的代码和每行代码背后的原理。

## 您将学习

- 如何从头创建一个新的 Word 文档。  
- 如何使用 **DocumentBuilder** 放置 **Forms2OleControl**。  
- 为什么要像我们示例中那样设置按钮的标题和尺寸。  
- 如何保存并验证结果。  
- 常见陷阱（例如缺少库、不受支持的控件类型）以及如何避免它们。

**先决条件** – 需要 Java 8+（或更高）以及 Aspose.Words for Java 库（版本 23.12 或更高）。IntelliJ IDEA 或 Eclipse 等 IDE 能让操作更顺畅，但任何文本编辑器都可以使用。

---

## 第 1 步：设置项目并导入依赖

在代码运行之前，Maven（或 Gradle）必须知道从哪里获取 Aspose.Words。将以下代码片段添加到你的 `pom.xml` 中：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

如果你更喜欢 Gradle，等价的写法是：

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **专业提示：** 使用最新发布版本；旧版本可能没有 `Forms2OleControl` API。

依赖解析完成后，你就可以开始编写 Java 代码了。

## 第 2 步：创建新文档并获取 DocumentBuilder

`Document` 类代表整个 `.docx` 包，而 `DocumentBuilder` 则是你在其上绘制内容的画笔。可以把 `DocumentBuilder` 看作知道下一个元素应放置位置的“光标”。

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**为什么这很重要：** 初始化一个全新的 `Document` 为你提供了一块干净的画布。构建器会自动指向第一个段落，这样你就不必手动管理章节或页面。

## 第 3 步：插入类型为 CommandButton 的 Forms2OleControl

现在登场的是明星方法：`insertForms2OleControl`。该方法创建一个 Word 视为表单元素的 OLE（对象链接与嵌入）控件。我们将传入三个参数：

1. `Forms2OleControlType.COMMANDBUTTON` – 告诉 Word 我们需要一个按钮。  
2. `100` – 宽度（单位：点，≈1.39 英寸）。  
3. `30` – 高度（单位：点，≈0.42 英寸）。

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**工作原理：** 在内部，Aspose.Words 会在 `word/document.xml` 部分生成相应的 XML，引用该 OLE 对象。你提供的尺寸会被 Word 的布局引擎遵循，按钮会精准出现在构建器光标所在的位置。

## 第 4 步：为按钮设置标题（文本）

没有标签的按钮会让人困惑——想象一下没有标识的电梯按钮。`setCaption` 方法用于设置可见文本：

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

你可以将标题改为任意内容：“Submit”、 “Approve”，甚至是本地化字符串。标题存储在 OLE 对象的属性中，Word 会原生渲染它。

## 第 5 步：保存文档并验证结果

最后，将文件写入磁盘。请选择一个你拥有写权限的文件夹，否则会抛出 `IOException`。

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

在 Microsoft Word 中打开 `button-demo.docx`。你应该会看到位于文档顶部、标有 **Click Me** 的按钮。点击该按钮会触发默认的 OLE 行为（通常是占位消息，除非你绑定了宏）。

## 常见边缘情况及处理方法

| 情况 | 产生原因 | 解决方案 |
|-----------|----------------|-----|
| **缺少 `Forms2OleControl` 类型** | 较旧的 Aspose.Words 版本未公开此枚举。 | 升级到 23.12+ 或更高版本。 |
| **按钮显示为图片** | Word 的安全设置阻止 OLE 控件。 | 在信任中心启用 “信任对 VBA 项目对象模型的访问”，或使用宏启用的 `.docm`。 |
| **尺寸不正确** | 点与像素的混淆。 | 记住 1 点 = 1/72 英寸。相应调整数值。 |
| **保存时抛出 `FileNotFoundException`** | 路径不存在。 | 确保在 `doc.save` 前创建目录（`output/`），如 `new File("output").mkdirs();`。 |

## 扩展示例：添加多个按钮或其他控件

如果需要多个按钮，只需在再次调用 `insertForms2OleControl` 之前使用 `builder.moveTo` 或 `builder.writeln()` 移动构建器光标。

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

你也可以通过将 `Forms2OleControlType.COMMANDBUTTON` 替换为相应的枚举值（`CHECKBOX`、`COMBOBOX`、`LISTBOX` 等）来插入 **CheckBox**、**ComboBox** 或 **ListBox**。宽度/高度参数保持不变。

## 该示例在更大规模的 Word 自动化工作流中的作用

- **模板生成：** 构建包含 “Approve” 按钮的合同模板，以便后续签署。  
- **报告生成：** 生成每日报告并附带 “Refresh Data” 按钮，触发宏执行。  
- **表单分发：** 发送预填充交互式控件的问卷。

所有这些场景都受益于我们演示的 **Word 自动化** 方法。通过以编程方式嵌入控件，你可以消除手动编辑，降低人为错误。

## 完整源代码（可直接复制粘贴）

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**预期输出：** 在 Microsoft Word 中打开 `output/button-demo.docx`，你会看到两个按钮——“Click Me” 与 “Submit”——垂直堆叠在文件顶部。

## 结论

我们已经一步步回答了 **如何在 Word 文档中添加按钮** 的问题，使用 Aspose.Words for Java。从空白 `Document` 开始，利用 **DocumentBuilder** 插入类型为 **CommandButton** 的 `Forms2OleControl`，设置友好的标题并保存结果。该方法可扩展到多个控件，并能干净地集成到更广泛的 **Word 自动化** 流程中。

准备好迎接下一个挑战了吗？尝试将按钮换成 **CheckBox**，或在 `.docm` 文件中绑定宏，以响应用户点击。模式相同——只需更改枚举并调整标题即可。

如果遇到任何问题，请再次检查库版本和输出文件夹的权限。欢迎在下方留言提问或分享你的使用案例。祝编码愉快！

## 接下来你应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助你在自己的项目中进一步掌握 API 功能并探索替代实现方式，每篇资源均提供完整可运行的代码示例和逐步说明。

- [如何使用 DocumentBuilder 在 Aspose.Words for Java 中创建表单字段并添加内容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [使用 Aspose.Words 在 Word 文档中插入内联图片](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}