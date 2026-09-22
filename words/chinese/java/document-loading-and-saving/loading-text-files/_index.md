---
date: 2025-12-27
description: 了解如何设置方向、加载 txt 文件、去除空格，并使用 Aspose.Words for Java 将 txt 转换为 docx。
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 设置方向并加载文本文件
url: /zh/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words for Java 中设置方向并加载文本文件

## Aspose.Words for Java 加载文本文件简介

在本指南中，您将了解 **如何在加载纯文本文档时设置方向**，并看到使用 Aspose.Words for Java **加载 txt、修剪空格以及将 txt 转换为 docx** 的实用方法。无论您是构建文档转换服务，还是需要对列表检测进行细粒度控制，本教程都将通过清晰的解释和可直接运行的代码，逐步带您完成每一步。

## 快速答疑
- **如何为已加载的 TXT 文件设置文本方向？** 使用 `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` 或指定 `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`。
- **Aspose.Words 能检测纯文本中的编号列表吗？** 能——在 `TxtLoadOptions` 中启用 `DetectNumberingWithWhitespaces`。
- **如何修剪前导和尾随空格？** 设置 `TxtLeadingSpacesOptions.TRIM` 和 `TxtTrailingSpacesOptions.TRIM`。
- **能否一行代码将 TXT 文件转换为 DOCX？** 使用 `TxtLoadOptions` 加载 TXT，然后调用 `Document.save("output.docx")`。
- **需要哪个 Java 版本？** Java 8+ 已足以运行 Aspose.Words 24.x。

## “设置方向” 在 Aspose.Words 中是什么？
当文本文件包含从右到左的脚本（例如希伯来语或阿拉伯语）时，库必须了解阅读顺序。`DocumentDirection` 枚举允许您 **手动设置方向**，或让 Aspose 自动检测，从而确保正确的布局和双向格式化。

## 为什么使用 Aspose.Words 加载 TXT 文件？
- **精准的列表检测**——处理编号、项目符号以及空格分隔的列表。
- **细粒度的空格处理**——修剪或保留前导/尾随空格。
- **自动文本方向检测**——适用于多语言文档。
- **一步完成转换**——将 `.txt` 加载后直接保存为 `.docx`、`.pdf` 或任何受支持的格式。

## 前置条件
- Java 8 或更高版本。
- Aspose.Words for Java 库（在 Maven/Gradle 中添加依赖或将 JAR 放入项目）。
- 基本的 Java I/O 流知识。

## 步骤指南

### 步骤 1：检测列表（如何加载 txt）
要加载文本文档并自动检测列表，创建 `TxtLoadOptions` 实例并启用列表检测。下面的代码展示了多种列表样式并启用了空格感知的编号。

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
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
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **小技巧：** 如果只需要基本的列表检测，可以省略空格选项——Aspose 仍会识别标准的 `1.` 和 `1)` 模式。

### 步骤 2：空格处理选项（如何修剪空格）
前导和尾随空格常导致格式异常。使用 `TxtLeadingSpacesOptions` 和 `TxtTrailingSpacesOptions` 来控制此行为。

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

> **为何重要：** 修剪空格可防止生成的 DOCX 中出现不必要的缩进，使文档在无需手动后处理的情况下保持整洁。

### 步骤 3：控制文本方向（如何设置方向）
针对从右到左的语言，在加载前设置文档方向。下面的示例加载一个希伯来语文本文件，并打印 bidi 标志以确认方向。

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

> **常见陷阱：** 忘记设置 `DocumentDirection` 会导致阿拉伯语/希伯来语字符顺序错误，出现乱码。

### 完整源码：使用 Aspose.Words for Java 加载文本文件
以下是完整、可直接运行的源码，融合了列表检测、空格处理和方向控制。您可以复制粘贴到单个类中，并分别运行三个测试方法。

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
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
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
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

## 常见问题及解决方案
| 问题 | 原因 | 解决方案 |
|------|------|----------|
| 列表未被检测 | `DetectNumberingWithWhitespaces` 为 `false`，导致空格分隔的列表未被识别 | 启用 `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| 加载后出现额外缩进 | 前导空格被保留 | 设置 `TxtLeadingSpacesOptions.TRIM` |
| 希伯来文显示颠倒 | 文档方向未设置或设置为 `LEFT_TO_RIGHT` | 使用 `DocumentDirection.AUTO` 或 `RIGHT_TO_LEFT` |
| 输出 DOCX 为空 | 在第二次加载前未重置输入流 | 为每次加载重新创建 `ByteArrayInputStream` |

## 常见问答

### Q: 什么是 Aspose.Words for Java？
A: Aspose.Words for Java 是一款强大的文档处理库，允许开发者在 Java 应用程序中以编程方式创建、操作和转换 Word 文档。它支持从简单的文本加载到复杂的格式化和转换等广泛功能。

### Q: 如何快速入门 Aspose.Words for Java？
A: 1. 下载并安装 Aspose.Words for Java 库。2. 参考 [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) 获取详细信息和示例。3. 浏览示例代码和教程，学习如何高效使用该库。

### Q: 如何使用 Aspose.Words for Java 加载文本文档？
A: 使用 `TxtLoadOptions` 类配合 `Document` 构造函数。根据步骤章节中的示例，指定列表检测、空格处理或文本方向等选项。

### Q: 能否将加载的文本文档转换为其他格式？
A: 可以。将 TXT 文件加载到 `Document` 对象后，调用 `doc.save("output.pdf")`、`doc.save("output.docx")` 或其他受支持的格式即可。

### Q: 如何处理加载文本文档中的空格？
A: 使用 `TxtLeadingSpacesOptions` 和 `TxtTrailingSpacesOptions` 控制前导和尾随空格。将其设为 `TRIM` 可去除多余空白，设为 `PRESERVE` 则保留原始间距。

### Q: 文本方向在 Aspose.Words for Java 中有什么意义？
A: 文本方向确保从右到左脚本（希伯来语、阿拉伯语等）能够正确渲染。通过设置 `DocumentDirection`，您可以保证双向文本在生成的文档中正确显示。

### Q: 哪里可以找到更多 Aspose.Words for Java 的资源和支持？
A: 访问 [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) 获取 API 参考、代码示例和详细指南。您也可以加入 Aspose 社区论坛或联系 Aspose 支持获取具体问题的帮助。

### Q: Aspose.Words for Java 适用于商业项目吗？
A: 适用。它提供个人和商业两种授权选项。请在 Aspose 官网查看授权条款，选择适合您项目的方案。

## 结论
现在，您已经拥有完整的工具箱，能够 **加载 txt 文件**、**检测列表**、**修剪空格** 并 **设置方向**，从而使用 Aspose.Words for Java 将纯文本转换为丰富的 Word 文档。将这些模式应用于自动化文档工作流，提升多语言支持，并确保每次输出都干净、专业。

---

**最后更新：** 2025-12-27  
**测试环境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}