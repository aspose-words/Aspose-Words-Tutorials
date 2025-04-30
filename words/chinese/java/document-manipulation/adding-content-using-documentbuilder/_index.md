---
"description": "使用 Aspose.Words for Java 精通文档创建。逐步指导您添加文本、表格、图像等内容。轻松创建精美的 Word 文档。"
"linktitle": "使用 DocumentBuilder 添加内容"
"second_title": "Aspose.Words Java文档处理API"
"title": "使用 Aspose.Words for Java 中的 DocumentBuilder 添加内容"
"url": "/zh/java/document-manipulation/adding-content-using-documentbuilder/"
"weight": 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 中的 DocumentBuilder 添加内容


## 使用 Aspose.Words for Java 中的 DocumentBuilder 添加内容简介

在本分步指南中，我们将探索如何使用 Aspose.Words for Java 的 DocumentBuilder 向 Word 文档添加各种类型的内容。我们将介绍如何插入文本、表格、水平线、表单字段、HTML、超链接、目录、内联和浮动图像、段落等等。让我们开始吧！

## 先决条件

在开始之前，请确保您的项目中已安装 Aspose.Words for Java 库。您可以从以下链接下载： [这里](https://releases。aspose.com/words/java/).

## 添加文本

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入简单文本段落
builder.write("This is a simple text paragraph.");

// 保存文档
doc.save("path/to/your/document.docx");
```

## 添加表格

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 开始一个表
Table table = builder.startTable();

// 插入单元格和内容
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// 结束表
builder.endTable();

// 保存文档
doc.save("path/to/your/document.docx");
```

## 添加水平线

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入水平线
builder.insertHorizontalRule();

// 保存文档
doc.save("path/to/your/document.docx");
```

## 添加表单字段

### 文本输入表单字段

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入文本输入表单字段
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// 保存文档
doc.save("path/to/your/document.docx");
```

### 复选框表单字段

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入复选框表单域
builder.insertCheckBox("CheckBox", true, true, 0);

// 保存文档
doc.save("path/to/your/document.docx");
```

### 组合框表单字段

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 定义组合框的项目
String[] items = { "Option 1", "Option 2", "Option 3" };

// 插入组合框表单域
builder.insertComboBox("DropDown", items, 0);

// 保存文档
doc.save("path/to/your/document.docx");
```

## 添加 HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入 HTML 内容
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// 保存文档
doc.save("path/to/your/document.docx");
```

## 添加超链接

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入超链接
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", 假);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// 保存文档
doc.save("path/to/your/document.docx");
```

## 添加目录

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入目录
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// 添加文档内容
// ...

// 更新目录
doc.updateFields();

// 保存文档
doc.save("path/to/your/document.docx");
```

## 添加图像

### 内联图像

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入内嵌图像
builder.insertImage("path/to/your/image.png");

// 保存文档
doc.save("path/to/your/document.docx");
```

### 浮动图像

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入浮动图像
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// 保存文档
doc.save("path/to/your/document.docx");
```

## 添加段落

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 设置段落格式
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

// 插入段落
builder.writeln("This is a formatted paragraph.");

// 保存文档
doc.save("path/to/your/document.docx");
```

## 步骤 10：移动光标

您可以使用各种方法控制文档中的光标位置，例如 `moveToParagraph`， `moveToCell`等等。以下是示例：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 将光标移动到特定段落
builder.moveToParagraph(2, 0);

// 在新的光标位置添加内容
builder.writeln("This is the 3rd paragraph.");
```

这些是您可以使用 Aspose.Words for Java 的 DocumentBuilder 执行的一些常见操作。浏览该库的文档，了解更多高级功能和自定义选项。祝您文档创建愉快！


## 结论

在本指南中，我们探索了 Aspose.Words for Java 的 DocumentBuilder 向 Word 文档添加各种内容的功能。我们涵盖了文本、表格、水平线、表单字段、HTML、超链接、目录、图像、段落和光标移动等操作。

## 常见问题解答

### 问：什么是 Aspose.Words for Java？

答：Aspose.Words for Java 是一个 Java 库，允许开发人员以编程方式创建、修改和操作 Microsoft Word 文档。它提供了丰富的文档生成、格式化和内容插入功能。

### 问：如何在我的文档中添加目录？

答：要添加目录，请使用 `DocumentBuilder` 在文档中插入目录字段。添加内容后，请务必更新文档中的字段以填充目录。以下是示例：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入目录字段
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// 添加文档内容
// ...

// 更新目录
doc.updateFields();
```

### 问：如何使用 Aspose.Words for Java 将图像插入文档？

答：您可以使用 `DocumentBuilder`。以下是两者的示例：

#### 内嵌图片：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入内嵌图像
builder.insertImage("path/to/your/image.png");
```

#### 浮动图像：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入浮动图像
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### 问：添加内容时可以设置文本和段落的格式吗？

答：是的，您可以使用 `DocumentBuilder`。您可以设置字体属性、段落对齐方式、缩进等。以下是示例：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 设置字体和段落格式
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

// 插入格式化的段落
builder.writeln("This is a formatted paragraph.");
```

### 问：如何将光标移动到文档中的特定位置？

答：您可以使用以下方法控制光标位置 `moveToParagraph`， `moveToCell`等等。以下是示例：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 将光标移动到特定段落
builder.moveToParagraph(2, 0);

// 在新的光标位置添加内容
builder.writeln("This is the 3rd paragraph.");
```

以下是一些常见问题及解答，旨在帮助您快速入门 Aspose.Words for Java 的 DocumentBuilder。如果您还有其他问题或需要进一步帮助，请参阅 [图书馆的文献](https://reference.aspose.com/words/java/) 或向 Aspose.Words 社区和支持资源寻求帮助。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}