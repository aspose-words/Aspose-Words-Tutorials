---
title: 在 Aspose.Words for Java 中合并和附加文档
linktitle: 合并和附加文档
second_title: Aspose.Words Java 文档处理 API
description: 了解如何使用 Aspose.Words for Java 轻松合并和附加文档。保留格式、管理页眉页脚等。
weight: 30
url: /zh/java/document-manipulation/joining-and-appending-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中合并和附加文档


## Aspose.Words for Java 中合并和附加文档的简介

在本教程中，我们将探索如何使用 Aspose.Words for Java 库合并和附加文档。您将学习如何无缝合并多个文档，同时保留格式和结构。

## 先决条件

在开始之前，请确保您已经在 Java 项目中设置了 Aspose.Words for Java API。

## 文档合并选项

### 简单追加

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### 附加导入格式选项

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### 附加到空白文档

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### 附加页码转换

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); //转换 NUMPAGES 字段
dstDoc.updatePageLayout(); //更新页面布局以获得正确的编号
```

## 处理不同的页面设置

附加具有不同页面设置的文档时：

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
//确保页面设置与目标文档匹配
```

## 合并不同风格的文档

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## 智能风格行为

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## 使用 DocumentBuilder 插入文档

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## 保留源编号

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## 处理文本框

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## 管理页眉和页脚

### 链接页眉和页脚

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### 取消页眉和页脚的链接

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## 结论

Aspose.Words for Java 提供灵活而强大的工具来合并和附加文档，无论您需要维护格式、处理不同的页面设置还是管理页眉和页脚。尝试使用这些技术来满足您特定的文档处理需求。

## 常见问题解答

### 如何才能无缝连接不同风格的文档？

要合并不同风格的文档，请使用`ImportFormatMode.USE_DESTINATION_STYLES`追加时。

### 附加文档时可以保留页码吗？

是的，你可以使用`convertNumPageFieldsToPageRef`方法并更新页面布局。

### 什么是智能风格行为？

智能样式行为有助于在附加文档时保持一致的样式。将其用于`ImportFormatOptions`以获得更好的结果。

### 附加文档时如何处理文本框？

放`importFormatOptions.setIgnoreTextBoxes(false)`在附加过程中包含文本框。

### 如果我想链接/取消链接文档之间的页眉和页脚怎么办？

您可以使用以下方式链接页眉和页脚`linkToPrevious(true)`或取消链接`linkToPrevious(false)`根据需要。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
