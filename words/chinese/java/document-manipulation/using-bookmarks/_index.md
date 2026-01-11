---
date: 2026-01-11
description: 学习如何显示/隐藏书签以及使用 Aspose.Words for Java 创建书签，以实现高效的文档导航和操作。
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: 使用 Aspose.Words for Java 显示/隐藏书签
url: /zh/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 显示/隐藏书签

## 在 Aspose.Words for Java 中使用书签的介绍

书签是 Aspose.Words for Java 中的强大功能，可让您 **create bookmark java**，导航到特定内容，甚至在需要生成不同文档版本时 **show hide bookmarks**。在本分步指南中，我们将演示创建、访问、更新、复制以及切换书签可见性，让您全面控制文档操作。

## 快速答案
- **What is the primary purpose of bookmarks?** 标记并随后检索文档的特定部分。  
- **Can I hide bookmark markers in the final output?** 是的——使用 show/hide API 来切换其可见性。  
- **How do I create a bookmark inside a table cell?** 在光标位于单元格内部时，使用 `DocumentBuilder` 开始和结束书签。  
- **Is it possible to copy bookmarked text to another document?** 当然——使用 `NodeImporter` 保留格式。  
- **What version of Aspose.Words is required?** 任何近期版本；代码在最新的 2026 构建中均可运行。

## 什么是“show hide bookmarks”？

**show hide bookmarks** 功能允许您以编程方式在保存的文档中显示或隐藏书签分隔符。当您希望为最终用户生成干净的输出，同时仍保留内部处理所需的书签数据时，这非常有用。

## 为什么在 Java 文档自动化中使用书签？

- **Efficient navigation** – 直接跳转到章节，无需扫描整个文件。  
- **Dynamic content generation** – 插入、替换或删除与书签关联的文本。  
- **Conditional visibility** – 根据用户偏好或输出格式显示或隐藏书签标记。  
- **Reusability** – 在文档之间复制带书签的片段，同时保留样式。

## 前提条件
- Java Development Kit (JDK) 8 或更高版本。  
- 已在项目中添加 Aspose.Words for Java 库（Maven/Gradle 或 JAR）。  
- 对 `Document` 和 `DocumentBuilder` 类有基本了解。

## 分步指南

### 步骤 1：创建书签 (create bookmark java)

要添加书签，先开始书签，写入内容，然后结束它。下面的示例创建了一个名为 **My Bookmark** 的简单书签。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### 步骤 2：访问书签 (access bookmarks java)

书签可以通过零基索引或名称检索。下面的代码演示了两种方法。

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### 步骤 3：更新书签数据 (update bookmark text)

您可以重命名书签或替换其文本内容。当底层文档发生变化时，这非常方便。

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### 步骤 4：处理带书签的文本 (copy bookmarked text)

使用 `NodeImporter` 将带书签的片段复制到另一个文档并保持原始格式非常简单。

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### 步骤 5：显示和隐藏书签 (show hide bookmarks)

以下代码片段演示了如何在保存的文件中隐藏书签标记。传入 `false` 以隐藏，`true` 以显示。

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### 步骤 6：解开行书签 (bookmark table cell)

当书签跨越表格行时，可能会纠缠。下面的实用方法可解开它们，并允许您通过书签删除特定行。

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## 常见问题及解决方案

| Issue | Solution |
|-------|----------|
| **Bookmark not found** | 确保书签名称完全匹配（区分大小写），并且文档在创建后已保存。 |
| **Copied text loses formatting** | 使用 `ImportFormatMode.KEEP_SOURCE_FORMATTING` 与 `NodeImporter`，如步骤 4 所示。 |
| **Show/hide does not affect output** | 确保在保存文档之前调用 `showHideBookmarkedContent` **before**。 |
| **Bookmark inside a table cell is ignored** | 在构建器光标位于目标单元格内部时调用开始/结束方法。 |

## 常见问题

**Q: 如何在表格单元格中创建书签？**  
A: 使用 `DocumentBuilder` 将光标移动到目标单元格，然后在单元格内容前后调用 `startBookmark` 和 `endBookmark`。

**Q: 我可以将书签复制到另一个文档吗？**  
A: 可以——使用 `NodeImporter` 类（见步骤 4）导入带书签的节点，同时保留其原始格式。

**Q: 如何通过书签删除一行？**  
A: 首先定位包含该书签的行，然后对该行节点调用 `remove`（如步骤 6 所示）。

**Q: 书签有哪些常见用例？**  
A: 生成目录、提取特定章节用于报告、以及基于用户选择自动组装文档。

**Q: 在哪里可以找到关于 Aspose.Words for Java 的更多信息？**  
A: 有关详细文档和下载，请访问 [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/)。

---

**最后更新：** 2026-01-11  
**测试环境：** Aspose.Words for Java 24.11 (2026)  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}