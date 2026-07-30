---
date: 2026-01-01
description: 学习如何使用 Aspose.Words for Java 的 DocumentBuilder 创建表单字段并添加文本、表格、图像、超链接等。面向开发者的逐步指南。
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 中的 DocumentBuilder 创建表单字段并添加内容
url: /zh/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 的 DocumentBuilder 添加内容

## 使用 Aspose.Words for Java 的 DocumentBuilder 添加内容简介

在本分步指南中，您将 **create form fields** 并将各种内容——文本、表格、水平线、HTML、超链接、图片等——添加到使用 Aspose.Words for Java 的 Word 文档中。无论您是在构建报告、合同模板还是交互式表单，`DocumentBuilder` 类都能让您对每个元素进行细粒度控制。让我们开始吧！

## 快速答案
- **How do I create form fields?** 使用 `DocumentBuilder` 的 `insertTextInput`、`insertCheckBox` 或 `insertComboBox`。
- **What method adds plain text?** 调用 `builder.write("Your text")` 或 `builder.writeln("Your text")`。
- **Can I insert a horizontal rule?** 可以——`builder.insertHorizontalRule()` 会添加一条分隔线。
- **How to embed HTML?** 使用 `builder.insertHtml("<p>HTML content</p>")`。
- **How to add an inline image?** `builder.insertImage("path/to/image.png")` 将图片放置在文本流中。

## 什么是 DocumentBuilder，为什么使用它来创建表单字段？

`DocumentBuilder` 是 Aspose.Words 的流式 API，用于以编程方式构建和编辑 Word 文档。它抽象了底层的 OpenXML 结构，让您专注于 *what* 您想要添加的内容——例如 **form fields**——而不是 *how* XML 的具体形式。这使其非常适合生成动态表单、合同或任何需要用户交互的文档。

## 前提条件

在开始之前，请确保您的项目中已安装 Aspose.Words for Java 库。您可以从 [here](https://releases.aspose.com/words/java/) 下载。

## 添加文本（如何添加文本）

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## 添加表格

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## 添加水平线（添加水平线）

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## 添加表单字段（创建表单字段）

### 文本输入表单字段

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### 复选框表单字段

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### 下拉框表单字段

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## 添加 HTML（插入 HTML）

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## 添加超链接（如何添加超链接）

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## 添加目录

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## 添加图片

### 内联图片（插入内联图片）

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### 浮动图片

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## 添加段落

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## 移动光标（第 10 步）

您可以使用 `moveToParagraph`、`moveToCell` 等方法来控制文档中光标的位置。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

这些是使用 Aspose.Words for Java 的 `DocumentBuilder` 可以执行的一些常见操作。请查阅库的文档以获取更高级的功能和自定义选项。祝您文档创建愉快！

## 结论

在本综合指南中，我们展示了如何 **create form fields** 并使用 Aspose.Words for Java 的 `DocumentBuilder` 添加各种类型的内容——文本、表格、水平线、HTML、超链接、目录、图片、格式化段落以及光标导航。现在，您已经拥有了以编程方式生成动态、交互式 Word 文档的坚实基础。

## 常见问题

### Q: 什么是 Aspose.Words for Java？

A: Aspose.Words for Java 是一个 Java 库，允许开发者以编程方式创建、修改和操作 Microsoft Word 文档。它提供了广泛的文档生成、格式化和内容插入功能。

### Q: 如何向文档添加目录？

A: 要添加目录，使用 `DocumentBuilder` 插入 TOC 字段，然后在添加内容后调用 `doc.updateFields()`。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Q: 如何使用 Aspose.Words for Java 向文档插入图片？

A: 您可以使用 `DocumentBuilder` 插入图片，包括内联和浮动图片。

#### 内联图片：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### 浮动图片：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: 添加内容时可以格式化文本和段落吗？

A: 可以，您可以使用 `DocumentBuilder` 对文本和段落进行格式化。在写入内容之前设置字体属性、段落对齐、缩进等。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Q: 如何将光标移动到文档中的特定位置？

A: 使用 `moveToParagraph`、`moveToCell` 等方法在插入新内容之前定位光标。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

这些答案涵盖了使用 Aspose.Words for Java 的 `DocumentBuilder` 时最常见的场景。欲了解更深入的细节，请参考 [library's documentation](https://reference.aspose.com/words/java/) 或加入 Aspose.Words 社区获取支持。

---

**Last Updated:** 2026-01-01  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}