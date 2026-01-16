---
date: 2026-01-16
description: 学习如何将英寸转换为点，使用 Aspose.Words for Java 读取文档元数据、添加自定义属性以及设置页面边距。
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: 将英寸转换为点 – 在 Aspose.Words for Java 中使用文档属性
url: /zh/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 将英寸转换为点 – 在 Aspose.Words for Java 中使用文档属性

在本教程中，您将学习在设置页面边距时 **将英寸转换为点**，以及在 Java 中读取文档元数据、添加自定义属性、以及使用 Aspose.Words for Java 操作内置文档属性的技巧。无论是生成报告、发票还是法律文档，掌握这些技术都能让您对 Word 文件的外观和元数据进行细粒度控制。

## 快速答案
- **如何将英寸转换为点？** 使用 Aspose.Words 提供的 `ConvertUtil.inchToPoint(value)`。
- **可以在 Java 中读取文档元数据吗？** 可以 – 调用 `doc.getBuiltInDocumentProperties()` 或 `doc.getCustomDocumentProperties()`。
- **如何在 Java 中添加自定义属性？** 使用 `doc.getCustomDocumentProperties().add(name, value)`。
- **哪个方法以点为单位设置页面边距？** `PageSetup.setTopMargin`、`setBottomMargin` 等接受点值。
- **是否支持链接到书签？** 支持 – 在自定义属性集合上使用 `addLinkToContent`。

## 文档属性简介

文档属性是任何 Word 文件的重要组成部分。它们存储标题、作者、主题、关键字以及您在后续处理时需要的任何自定义元数据。在 Aspose.Words for Java 中，您可以操作内置和自定义文档属性，还可以通过转换测量单位（例如 **将英寸转换为点**）来控制布局细节，如边距。

## 什么是 “将英寸转换为点”？

在 Word 中，布局测量采用点（1 point = 1/72 英寸）表示。将英寸转换为点可以让您使用熟悉的英制单位定义边距、缩进和间距，而 API 在内部使用点进行计算。

## 为什么在 Java 中管理文档元数据？

嵌入元数据可以更方便地搜索、分类和自动化工作流。例如，您可以为合同添加 “Authorized” 标记，或存储修订号以便审计。以编程方式读取和写入这些信息可确保在大量文档批次中保持一致性。

## 前置条件
- Java 17+（或兼容的 JDK）
- 已在项目中添加 Aspose.Words for Java 库（Maven/Gradle）
- 一个示例 `.docx` 文件（如 `Properties.docx`），放置在可访问的目录中

## 步骤指南

### 枚举内置文档属性
下面的示例代码打开文档并打印所有内置属性，如 Title、Author 和 Keywords。

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **专业提示：** 使用此代码片段可验证之前步骤中元数据是否已正确写入。

### 添加自定义文档属性（add custom properties java）
自定义属性允许您存储任意数据类型——布尔值、字符串、日期、数字等。

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **为何重要：** 添加 **Authorized** 之类的标记可以在不更改文档内容的情况下驱动后续审批工作流。

### 删除自定义属性
如果某个属性不再需要，可以干净利落地将其删除。

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### 配置内容链接（书签链接）
您可以创建书签，然后添加指向该书签的自定义属性，实现动态交叉引用。

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### 在测量单位之间转换（set page margins java）
这里是关键关键词发挥作用的地方。我们先以英寸设置边距，然后使用 `ConvertUtil` **将英寸转换为点**。

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **注意：** `ConvertUtil` 还提供 `pointToInch`、`mmToPoint` 等方法，以实现灵活的布局处理。

### 使用控制字符（read document metadata java）
控制字符帮助您清理文本流。此示例将回车符（`\r`）替换为 Windows 换行序列（`\r\n`）。

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## 常见问题与解决方案
| 问题 | 原因 | 解决方案 |
|------|------|----------|
| 转换后边距显示不正确 | 使用了错误的单位（例如将厘米当作英寸） | 确认对英寸值调用 `ConvertUtil.inchToPoint` |
| 自定义属性未出现 | 属性在保存文档后才添加 | 在添加属性后调用 `doc.save(...)` |
| 书签链接失效 | 书签名称拼写错误 | 确保 `addLinkToContent` 中的书签名称完全匹配 |

## FAQ

### 如何访问内置文档属性？

要在 Aspose.Words for Java 中访问内置文档属性，可对 `Document` 对象调用 `getBuiltInDocumentProperties` 方法。该方法返回一个内置属性集合，您可以遍历其中的属性。

### 能否向文档添加自定义文档属性？

可以，使用 `CustomDocumentProperties` 集合即可向文档添加自定义属性。您可以定义包括字符串、布尔值、日期和数值在内的多种数据类型。

### 如何删除特定的自定义文档属性？

要删除特定的自定义文档属性，可在 `CustomDocumentProperties` 集合上调用 `remove` 方法，并传入要删除的属性名称。

### 链接到文档内容的目的是什么？

在文档内部创建链接可以实现对特定部分的动态引用。这对于制作交互式文档或在章节之间建立交叉引用非常有用。

### 如何在 Aspose.Words for Java 中进行单位转换？

可以使用 `ConvertUtil` 类进行单位转换。它提供了英寸转点、点转厘米等多种方法。

## 常见问答

**Q: 如何在不加载整个文件的情况下读取 Java 文档元数据？**  
A: 使用 `DocumentInfo` 可在不完全加载文档内容的情况下获取核心属性。

**Q: 能否在已有文档上以 Java 编程方式设置页面边距？**  
A: 可以——打开文档后，修改 `PageSetup` 的边距（如有需要先将英寸转换为点），然后保存。

**Q: 是否可以将自定义属性导出为 PDF 元数据？**  
A: 保存为 PDF 时，Aspose.Words 会自动将自定义文档属性映射为 PDF 的自定义元数据。

**Q: 控制字符会影响 PDF 转换吗？**  
A: 转换过程中会保留控制字符，但您可能希望统一换行符以保持一致性。

**Q: 使用 `ConvertUtil` 需要哪个版本的 Aspose.Words？**  
A: `ConvertUtil` 自 Aspose.Words 16.5 起提供，任何较新版本均支持。

## 结论

通过掌握 **将英寸转换为点**、读取 Java 文档元数据以及添加自定义属性的技巧，您可以全面控制 Word 文件的视觉布局和隐藏数据。这些能力使您能够构建自动化文档流水线、确保合规性，并创建丰富格式的报告——全部使用 Aspose.Words for Java。

---

**最后更新：** 2026-01-16  
**测试环境：** Aspose.Words for Java 24.11  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}