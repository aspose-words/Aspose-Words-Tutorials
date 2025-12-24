---
date: 2025-12-24
description: 学习如何使用 Aspose.Words for Java 将 Word 文档创建为纯文本文件。本指南展示了如何将 Word 转换为 txt、使用制表符缩进以及将
  Word 保存为 txt。
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 创建纯文本文件
url: /zh/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 创建纯文本文件

## 在 Aspose.Words for Java 中将文档保存为文本文件的简介

在本教程中，您将学习如何使用 Aspose.Words for Java 库从 Word 文档 **创建纯文本文件**。无论您需要 **将 word 转换为 txt**、自动化报告生成，还是仅仅提取原始文本以进行进一步处理，本指南将带您完成整个工作流——从文档创建到微调保存选项，例如 **使用制表符缩进** 或添加双向标记。让我们开始吧！

## 快速答复
- **创建文档的主要类是什么？** `Document` 来自 Aspose.Words。  
- **哪个选项为从右到左语言添加双向标记？** `TxtSaveOptions.setAddBidiMarks(true)`。  
- **如何使用制表符缩进列表项？** 将 `ListIndentation.Character` 设置为 `'\t'`。  
- **开发时需要许可证吗？** 免费试用可用于测试；生产环境需要许可证。  
- **我可以使用自定义名称和路径保存文件吗？** 可以——将完整路径传递给 `doc.save()`。

## 先决条件

在开始之前，请确保您已具备以下先决条件：

- 已在系统上安装 Java Development Kit (JDK)。  
- 已在项目中集成 Aspose.Words for Java 库。您可以从 [here](https://releases.aspose.com/words/java/) 下载。  
- 具备基本的 Java 编程知识。

## 步骤 1：创建文档

要 **将 word 保存为 txt**，我们首先需要一个 `Document` 实例。下面是一个简单的 Java 代码片段，用于创建文档并写入几行多语言文本：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

在此代码中，我们创建了一个新文档，添加了英文、希伯来文和阿拉伯文文本，并为希伯来段落启用了从右到左的格式。

## 步骤 2：定义文本保存选项

接下来，我们配置文档将如何保存为纯文本文件。Aspose.Words 提供了 `TxtSaveOptions` 类，可让您控制从双向标记到列表缩进的所有内容。

### 示例 1：添加双向标记（如何保存具有正确 RTL 支持的 txt）

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

将 `AddBidiMarks` 设置为 `true` 可确保右到左字符在生成的 **纯文本文件** 中正确显示。

### 示例 2：使用制表符字符进行列表缩进（使用制表符缩进）

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

这里我们指示 Aspose.Words 在每个列表级别前添加一个制表符字符 (`'\t'`)，使文本输出更易阅读。

## 步骤 3：将文档保存为文本

现在保存选项已准备好，您可以将文档持久化为 **纯文本文件**：

```java
doc.save("output.txt", saveOptions);
```

将 `"output.txt"` 替换为您希望存储文件的完整路径。

## 完整的 Aspose.Words for Java 文本文件保存示例源代码

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## 常见问题及解决方案

| 问题 | 解决方案 |
|-------|----------|
| **Bidi characters appear as garbled text** | 确保已启用 `setAddBidiMarks(true)`，并使用 UTF‑8 编码打开输出文件。 |
| **List indentation looks wrong** | 验证 `ListIndentation.Count` 和 `Character` 已设置为所需的值（制表符 `'\t'` 或空格 `' '`）。 |
| **File not created** | 检查目录路径是否存在以及应用程序是否具有写入权限。 |

## 常见问题

### 如何向文本输出添加双向标记？

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### 我可以自定义列表缩进字符吗？

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words for Java 是否适合处理多语言文本？

是的，Aspose.Words for Java 支持广泛的语言和字符编码，非常适合提取并将多语言内容保存为纯文本。

### 我如何获取更多 Aspose.Words for Java 的文档和资源？

您可以在 Aspose.Words for Java 文档页面找到完整的文档和资源： [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/)。

### 我可以从哪里下载 Aspose.Words for Java？

您可以从官方网站下载库： [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)。

### 如果我需要在批处理过程中 **将 word 转换为 txt**，该怎么办？

将上述代码放入循环中，加载每个 `.docx` 文件，应用相同的 `TxtSaveOptions`，并将其保存为 `.txt`。确保在每次迭代后释放 `Document` 对象以管理资源。

### API 是否支持直接保存到流而不是文件？

是的，您可以将 `OutputStream` 传递给 `doc.save(outputStream, saveOptions)`，用于内存处理或与 Web 服务集成时。

---

**最后更新：** 2025-12-24  
**测试环境：** Aspose.Words for Java 24.12（最新）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}