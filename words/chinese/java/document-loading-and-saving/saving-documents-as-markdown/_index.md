---
title: 在 Aspose.Words for Java 中将文档保存为 Markdown
linktitle: 将文档保存为 Markdown
second_title: Aspose.Words Java 文档处理 API
description: 了解如何使用 Aspose.Words for Java 将 Word 文档转换为 Markdown。本分步指南涵盖表格对齐、图像处理等。
weight: 18
url: /zh/java/document-loading-and-saving/saving-documents-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中将文档保存为 Markdown


## 使用 Aspose.Words for Java 将文档保存为 Markdown 的简介

在本分步指南中，我们将演示如何使用 Aspose.Words for Java 将文档保存为 Markdown。Markdown 是一种轻量级标记语言，通常用于格式化文本文档。使用 Aspose.Words for Java，您可以轻松地将 Word 文档转换为 Markdown 格式。我们将介绍保存 Markdown 文件的不同方面，包括表格内容对齐和处理图像。

## 先决条件

开始之前，请确保您满足以下先决条件：

- 您的系统上安装了 Java 开发工具包 (JDK)。
-  Aspose.Words for Java 库。您可以从以下位置下载[这里](https://releases.aspose.com/words/java/).

## 步骤 1：创建 Word 文档

让我们首先创建一个 Word 文档，稍后将其转换为 Markdown 格式。您可以根据需要自定义此文档。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//插入包含两个单元格的表格
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

//将文档另存为 Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

在此示例中，我们创建一个包含两个单元格的简单表格，并设置这些单元格内段落的对齐方式。然后，我们使用`MarkdownSaveOptions`.

## 步骤 2：自定义表格内容对齐方式

Aspose.Words for Java 允许您在保存为 Markdown 时自定义表格内容的对齐方式。您可以将表格内容左对齐、右对齐、居中对齐，或让其根据每个表格列中的第一段自动确定。

自定义表格内容对齐的方法如下：

```java
//将表格内容对齐方式设置为左对齐
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

//将表格内容对齐方式设置为右对齐
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

//将表格内容对齐方式设置为居中
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

//将表格内容对齐方式设置为自动（由第一段决定）
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

通过改变`TableContentAlignment`属性，您可以控制转换为 Markdown 时表格内的内容如何对齐。

## 步骤 3：处理图像

要在 Markdown 文档中包含图像，您需要指定图像所在的文件夹。Aspose.Words for Java 允许您在`MarkdownSaveOptions`.

以下是如何设置图像文件夹并保存包含图像的文档：

```java
//加载包含图像的文档
Document doc = new Document("document_with_images.docx");

//设置图像文件夹路径
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

//保存包含图像的文档
doc.save("document_with_images.md", saveOptions);
```

确保更换`"document_with_images.docx"`包含图像的 Word 文档的路径和`"images_folder/"`使用存储图像的文件夹的实际路径。

## 在 Aspose.Words for Java 中将文档保存为 Markdown 的完整源代码

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	//使表格内的所有段落对齐。
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	//在这种情况下，对齐将取自相应表格列中的第一个段落。
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## 结论

在本指南中，我们探讨了如何使用 Aspose.Words for Java 将文档保存为 Markdown。我们介绍了如何创建 Word 文档、自定义表格内容对齐方式以及处理 Markdown 文件中的图像。现在，您可以高效地将 Word 文档转换为 Markdown 格式，使其适用于各种发布平台和文档需求。

## 常见问题解答

### 如何安装 Aspose.Words for Java？

可以通过将库包含在 Java 项目中来安装 Aspose.Words for Java。您可以从以下位置下载该库[这里](https://releases.aspose.com/words/java/)并按照文档中提供的安装说明进行操作。

### 我可以将包含表格和图像的复杂 Word 文档转换为 Markdown 吗？

是的，Aspose.Words for Java 支持将包含表格、图像和各种格式元素的复杂 Word 文档转换为 Markdown。您可以根据文档的复杂程度自定义 Markdown 输出。

### 如何处理 Markdown 文件中的图像？

要在 Markdown 文件中包含图像，请使用`setImagesFolder`方法`MarkdownSaveOptions`确保图像文件存储在指定的文件夹中，Aspose.Words for Java 将相应地处理图像引用。

### 是否有适用于 Java 的 Aspose.Words 试用版？

是的，您可以从 Aspose 网站获取 Aspose.Words for Java 的试用版。试用版允许您在购买许可证之前评估该库的功能。

### 在哪里可以找到更多示例和文档？

有关 Aspose.Words for Java 的更多示例、文档和详细信息，请访问[文档](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
