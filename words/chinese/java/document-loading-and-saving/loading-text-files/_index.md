---
title: 使用 Aspose.Words for Java 加载文本文件
linktitle: 使用以下方式加载文本文件
second_title: Aspose.Words Java 文档处理 API
description: 解锁 Aspose.Words for Java 的强大功能。学习加载文本文档、管理列表、处理空格和控制文本方向。
weight: 13
url: /zh/java/document-loading-and-saving/loading-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 加载文本文件


## 使用 Aspose.Words for Java 加载文本文件的简介

在本指南中，我们将探索如何使用 Aspose.Words for Java 加载文本文件并将其作为 Word 文档进行操作。我们将介绍检测列表、处理空格和控制文本方向等各个方面。

## 步骤 1：检测列表

要加载文本文档并检测列表，您可以按照以下步骤操作：

```java
//创建一个字符串形式的纯文本文档，其中某些部分可以解释为列表。
//加载后，Aspose.Words 将始终检测到前三个列表，
//并且在加载后将为它们创建 List 对象。
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
//第四个列表，列表编号和列表项内容之间有空格，
//仅当 LoadOptions 对象中的“DetectNumberingWithWhitespaces”设置为 true 时，才会被检测为列表，
//以避免以数字开头的段落被误检测为列表。
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
//使用 LoadOptions 作为参数加载文档并验证结果。
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

此代码演示如何加载具有各种列表格式的文本文档，并使用`DetectNumberingWithWhitespaces`选项来正确检测列表。

## 第 2 步：处理空间选项

要在加载文本文档时控制前导和尾随空格，可以使用以下代码：

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

在此示例中，我们加载文本文档并使用以下方法修剪前导和尾随空格`TxtLeadingSpacesOptions.TRIM`和`TxtTrailingSpacesOptions.TRIM`.

## 步骤 3：控制文本方向

要在加载文本文档时指定文本方向，可以使用以下代码：

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

此代码将文档方向设置为自动检测（`DocumentDirection.AUTO`并加载包含希伯来语文本的文本文档。您可以根据需要调整文档方向。

## 使用 Aspose.Words for Java 加载文本文件的完整源代码

```java
public void detectNumberingWithWhitespaces() throws Exception {
	//创建一个字符串形式的纯文本文档，其中某些部分可以解释为列表。
	//加载后，Aspose.Words 将始终检测到前三个列表，
	//并且在加载后将为它们创建 List 对象。
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	//第四个列表，列表编号和列表项内容之间有空格，
	//仅当 LoadOptions 对象中的“DetectNumberingWithWhitespaces”设置为 true 时，才会被检测为列表，
	//以避免以数字开头的段落被误检测为列表。
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	//使用 LoadOptions 作为参数加载文档并验证结果。
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## 结论

在本指南中，我们探讨了如何使用 Aspose.Words for Java 加载文本文件、检测列表、处理空格以及控制文本方向。这些技术可让您在 Java 应用程序中有效地操作文本文档。

## 常见问题解答

### 什么是 Aspose.Words for Java？

Aspose.Words for Java 是一个功能强大的文档处理库，允许开发人员在 Java 应用程序中以编程方式创建、操作和转换 Word 文档。它提供了处理文本、表格、图像和其他文档元素的广泛功能。

### 如何开始使用 Aspose.Words for Java？

要开始使用 Aspose.Words for Java，请按照以下步骤操作：
1. 下载并安装 Aspose.Words for Java 库。
2. 请参阅以下文档：[Aspose.Words for Java API 参考](https://reference.aspose.com/words/java/)了解详细信息和示例。
3. 探索示例代码和教程以了解如何有效地使用该库。

### 如何使用 Aspose.Words for Java 加载文本文档？

要使用 Aspose.Words for Java 加载文本文档，您可以使用`TxtLoadOptions`类和`Document`类。请确保根据需要指定适当的选项来处理空格和文本方向。请参阅本文中的分步指南以获取详细示例。

### 我可以将已加载的文本文档转换为其他格式吗？

是的，Aspose.Words for Java 允许您将加载的文本文档转换为各种格式，包括 DOCX、PDF 等。您可以使用`Document`类来执行转换。查看文档以获取具体的转换示例。

### 如何处理已加载文本文档中的空格？

您可以使用以下方式控制加载的文本文档中前导空格和尾随空格的处理方式`TxtLoadOptions` 选项包括`TxtLeadingSpacesOptions`和`TxtTrailingSpacesOptions`允许您根据需要修剪或保留空格。请参阅本指南中的“处理空格选项”部分以获取示例。

### Aspose.Words for Java 中的文本方向有什么意义？

对于包含混合脚本或语言（如希伯来语或阿拉伯语）的文档，文本方向至关重要。Aspose.Words for Java 提供了指定文本方向的选项，确保正确呈现和格式化这些语言的文本。本指南中的“控制文本方向”部分演示了如何设置文本方向。

### 在哪里可以找到有关 Aspose.Words for Java 的更多资源和支持？

如需更多资源、文档和支持，请访问[Aspose.Words for Java 文档](https://reference.aspose.com/words/java/)。您还可以参加 Aspose.Words 社区论坛或联系 Aspose 支持以获取有关特定问题或疑问的帮助。

### Aspose.Words for Java 适合商业项目吗？

是的，Aspose.Words for Java 适用于个人和商业项目。它提供许可选项以适应各种使用场景。请务必查看 Aspose 网站上的许可条款和定价，以选择适合您项目的许可证。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
