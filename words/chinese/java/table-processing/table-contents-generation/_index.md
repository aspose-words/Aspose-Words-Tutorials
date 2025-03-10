---
title: 目录生成
linktitle: 目录生成
second_title: Aspose.Words Java 文档处理 API
description: 了解如何使用 Aspose.Words for Java 创建动态目录。通过分步指导和源代码示例掌握目录生成。
weight: 14
url: /zh/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 目录生成

## 介绍

是否曾经为在 Word 文档中创建动态且专业的目录 (TOC) 而苦恼？别再找了！使用 Aspose.Words for Java，您可以自动化整个过程，节省时间并确保准确性。无论您是构建综合报告还是学术论文，本教程都将引导您使用 Java 以编程方式生成目录。准备好了吗？让我们开始吧！

## 先决条件

在开始编码之前，请确保您具有以下条件：

1.  Java 开发工具包 (JDK)：安装在您的系统上。您可以从以下位置下载[Oracle 网站](https://www.oracle.com/java/technologies/javase-downloads.html).
2. Aspose.Words for Java 库：从下载最新版本[发布页面](https://releases.aspose.com/words/java/).
3. 集成开发环境 (IDE)：例如 IntelliJ IDEA、Eclipse 或 NetBeans。
4.  Aspose 临时许可证：为避免评估限制，请获取[临时执照](https://purchase.aspose.com/temporary-license/).

## 导入包

为了有效地使用 Aspose.Words for Java，请确保导入所需的类。以下是导入的内容：

```java
import com.aspose.words.*;
```

按照以下步骤在 Word 文档中生成动态目录。

## 步骤 1：初始化 Document 和 DocumentBuilder

第一步是创建一个新文档并使用`DocumentBuilder`类来操作它。


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`：代表Word文档。
- `DocumentBuilder`：允许轻松操作文档的辅助类。

## 第 2 步：插入目录

现在，让我们在文档的开头插入目录。


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`：插入目录字段。参数指定：
  - `\o "1-3"`：包括 1 至 3 级标题。
  - `\h`：使条目成为超链接。
  - `\z`：抑制网页文档的页码。
  - `\u`：保留超链接的样式。
- `insertBreak`：在目录后添加分页符。

## 步骤 3：添加标题以填充目录

要填充目录，您需要添加具有标题样式的段落。


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` ：将段落样式设置为特定标题级别（例如，`HEADING_1`, `HEADING_2`）。
- `writeln`：使用指定的样式向文档添加文本。

## 步骤 4：添加嵌套标题

为了展示目录级别，请包含嵌套标题。


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- 添加更深级别的标题以显示目录中的层次结构。

## 步骤 5：更新目录字段

必须更新 TOC 字段才能显示最新的标题。


```java
doc.updateFields();
```

- `updateFields`：刷新文档中的所有字段，确保目录反映添加的标题。

## 步骤 6：保存文档

最后，将文档保存为您想要的格式。


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save` ：将文档导出至`.docx`文件。您可以指定其他格式，例如`.pdf`或者`.txt`如果需要的话。

## 结论

恭喜！您已成功使用 Aspose.Words for Java 在 Word 文档中创建动态目录。只需几行代码，您就自动完成了原本需要数小时才能完成的任务。那么，下一步是什么？尝试使用不同的标题样式和格式，以根据特定需求定制您的目录。

## 常见问题解答

### 我可以进一步自定义 TOC 格式吗？
当然可以！您可以调整目录参数，例如添加页码、对齐文本或使用自定义标题样式。

### Aspose.Words for Java 是否必须有许可证？
是的，需要许可证才能使用完整功能。你可以先从[临时执照](https://purchase.aspose.com/temporary-license/).

### 我可以为现有文档生成目录吗？
是！将文档装入`Document`对象并按照相同的步骤插入和更新目录。

### 这对 PDF 导出有用吗？
是的，如果您将文档保存为`.pdf`格式。

### 在哪里可以找到更多文档？
查看[Aspose.Words for Java 文档](https://reference.aspose.com/words/java/)了解更多示例和详细信息。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
