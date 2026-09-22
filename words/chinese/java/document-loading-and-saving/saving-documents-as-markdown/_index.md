---
date: 2025-12-22
description: 了解如何通过 Aspose.Words for Java 将 Word 文档转换为 Markdown 来导出 Markdown。本分步指南涵盖表格对齐、图像处理等内容。
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 导出 Markdown
url: /zh/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 导出 Markdown

## Aspose.Words for Java 中导出 Markdown 的简介

在本分步教程中，**您将学习如何使用 Aspose.Words for Java 将 Word 文档导出为 markdown**。Markdown 是一种轻量级标记语言，非常适合文档编写、静态站点生成器以及众多发布平台。阅读完本指南后，您将能够**将 Word 转换为 markdown**、自定义表格对齐方式，并**轻松处理 markdown 中的图片**。

## 快速回答
- **保存为 Markdown 的主要类是什么？** `MarkdownSaveOptions`
- **图片可以自动嵌入吗？** 可以 – 通过 `setImagesFolder` 设置图片文件夹。
- **如何控制表格对齐方式？** 使用 `TableContentAlignment`（LEFT、RIGHT、CENTER、AUTO）。
- **最低要求是什么？** JDK 8+ 和 Aspose.Words for Java 库。
- **是否提供试用版？** 是的，可从 Aspose 官网下载。

## 什么是“如何导出 markdown”？
导出 markdown 是指将富文本 Word 文档（`.docx`）转换为纯文本 `.md` 文件，并在 Markdown 语法中保留标题、表格和图片等内容。

## 为什么使用 Aspose.Words for Java 将带图片的 docx 转换？
Aspose.Words 能够处理复杂布局、嵌入图片和表格结构，且不会丢失细节。它还提供对 Markdown 输出的精细控制，例如表格对齐方式和图片文件夹管理。

## 先决条件

- 已在系统上安装 Java Development Kit（JDK）。
- Aspose.Words for Java 库。您可以从 [here](https://releases.aspose.com/words/java/) 下载。

## 步骤 1：创建一个简单的 Word 文档

首先，我们将构建一个包含表格的微型文档，以便后续演示 **自定义表格对齐**。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

在上述代码片段中我们：

1. 创建一个新的 `Document`。
2. 使用 `DocumentBuilder` 插入一个两列的表格。
3. 在每个单元格内应用 **右对齐** 和 **居中对齐** 的段落。
4. 使用 `MarkdownSaveOptions` 将文件保存为 Markdown。

## 步骤 2：自定义表格内容对齐方式

Aspose.Words 允许您决定表格单元格在最终 Markdown 中的呈现方式。您可以强制左、右、居中对齐，或让库根据每列首个段落自动决定对齐方式。

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

通过切换 `TableContentAlignment` 属性，您可以控制 **自定义表格对齐**，从而影响 Markdown 输出的效果。

## 步骤 3：导出为 Markdown 时处理图片

当文档中包含图片时，您希望这些图片能够在生成的 `.md` 文件中正确显示。请设置 Aspose.Words 导出图片的目标文件夹。

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

将 `"document_with_images.docx"` 替换为您的源文件路径，将 `"images_folder/"` 替换为您希望存放图片的位置。生成的 Markdown 将包含指向该文件夹的图片链接，使您能够 **在 markdown 中无缝处理图片**。

## 完整的将文档保存为 Markdown 的源代码（适用于 Aspose.Words for Java）

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
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
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

## 常见问题及解决方案

| 问题 | 解决方案 |
|-------|----------|
| 图片未出现在 `.md` 文件中 | 确认 `setImagesFolder` 指向可写目录，并且生成的 Markdown 正确引用了该文件夹。 |
| 表格对齐显示异常 | 使用 `TableContentAlignment.AUTO` 让 Aspose.Words 根据每列首个段落自动推断最佳对齐方式。 |
| 输出文件为空 | 在调用 `save` 之前，确保 `Document` 对象实际包含内容。 |

## 常见问答

**Q: 如何安装 Aspose.Words for Java？**  
A: Aspose.Words for Java 可通过将库添加到您的 Java 项目中进行安装。您可以从 [here](https://releases.aspose.com/words/java/) 下载库，并按照文档中的安装说明进行操作。

**Q: 能否将包含表格和图片的复杂 Word 文档转换为 Markdown？**  
A: 可以，Aspose.Words for Java 支持将包含表格、图片以及各种格式元素的复杂 Word 文档转换为 Markdown。您可以根据文档的复杂程度自定义 Markdown 输出。

**Q: 如何在 Markdown 文件中处理图片？**  
A: 在 `MarkdownSaveOptions` 中使用 `setImagesFolder` 方法设置图片文件夹路径。确保图片文件存放在指定文件夹中，Aspose.Words 将生成相应的 Markdown 图片链接。

**Q: 是否提供 Aspose.Words for Java 的试用版？**  
A: 是的，您可以从 Aspose 官网获取 Aspose.Words for Java 的试用版。试用版允许您在购买许可证前评估库的功能。

**Q: 在哪里可以找到更多示例和文档？**  
A: 有关 Aspose.Words for Java 的更多示例、文档和详细信息，请访问 [documentation](https://reference.aspose.com/words/java/)。

---

**最后更新：** 2025-12-22  
**测试环境：** Aspose.Words for Java 24.12（撰写时的最新版本）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}