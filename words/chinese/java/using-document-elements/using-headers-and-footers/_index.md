---
title: 在 Aspose.Words for Java 中使用页眉和页脚
linktitle: 使用页眉和页脚
second_title: Aspose.Words Java 文档处理 API
description: 逐步了解如何在 Aspose.Words for Java 中使用页眉和页脚。轻松创建专业文档。
weight: 16
url: /zh/java/using-document-elements/using-headers-and-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用页眉和页脚


在本综合指南中，我们将引导您完成在 Aspose.Words for Java 中使用页眉和页脚的过程。页眉和页脚是文档格式的基本元素，Aspose.Words 提供了强大的工具来根据您的需要创建和自定义它们。

现在，让我们详细了解每个步骤。

## 1. Aspose.Words简介

Aspose.Words 是一个功能强大的 Java API，允许您以编程方式创建、操作和呈现 Word 文档。它提供了广泛的文档格式化功能，包括页眉和页脚。

## 2.设置 Java 环境

在开始使用 Aspose.Words 之前，请确保您已正确设置 Java 开发环境。您可以在 Aspose.Words 文档页面上找到必要的设置说明：[Aspose.Words Java 文档](https://reference.aspose.com/words/java/).

## 3.创建新文档

要使用页眉和页脚，您需要使用 Aspose.Words 创建一个新文档。以下代码演示了如何执行此操作：

```java
//用于创建新文档的 Java 代码
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. 了解页面设置

页面设置对于控制文档的布局至关重要。您可以使用`PageSetup`类。例如：

```java
//设置页面属性
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5.首页页眉/页脚不同

Aspose.Words 允许您为文档的第一页设置不同的页眉和页脚。使用`pageSetup.setDifferentFirstPageHeaderFooter(true);`启用此功能。

## 6. 使用标题

### 6.1. 在标题中添加文本

您可以使用`DocumentBuilder`。下面是一个例子：

```java
//向首页页眉添加文本
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. 在页眉中插入图像

要将图像插入页眉，您可以使用`insertImage`方法。以下是示例：

```java
//在页眉中插入图像
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. 自定义标题样式

您可以通过设置各种属性（例如字体、对齐方式等）来自定义标题样式，如上面的示例所示。

## 7. 使用页脚

### 7.1. 在页脚中添加文本

与页眉类似，您可以使用`DocumentBuilder`。下面是一个例子：

```java
//在主页脚中添加文本
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
//根据需要插入文本和字段
```

### 7.2. 在页脚中插入图像

要将图像插入页脚，请使用`insertImage`方法，就像在标题中一样。

### 7.3. 自定义页脚样式

使用自定义页脚样式`DocumentBuilder`，类似于自定义标题。

## 8. 页码

您可以使用以下字段在页眉和页脚中添加页码`PAGE`和`NUMPAGES`。当您添加或删除页面时，这些字段会自动更新。

## 9. 页脚中的版权信息

要将版权信息添加到文档的页脚，您可以使用一个包含两个单元格的表格，将一个单元格左对齐，另一个单元格右对齐，如代码片段所示。

## 10. 使用多个部分

Aspose.Words 允许您处理文档中的多个部分。您可以为每个部分设置不同的页面设置和页眉/页脚。

## 11. 横向

如果需要，您可以将特定部分的方向更改为横向模式。

## 12. 从前一节复制页眉/页脚

从前面的部分复制页眉和页脚可以节省创建复杂文档的时间。

## 13.保存文档

创建和自定义文档后，请不要忘记使用`doc.save()`方法。

## 完整源代码
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        //指定是否希望第一页的页眉/页脚与其他页面不同。
        //您还可以使用 PageSetup.OddAndEvenPagesHeaderFooter 属性来指定
        //奇数页和偶数页使用不同的页眉/页脚。
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        //将定位图像插入页眉的顶部/左角。
        //距页面上/左边缘的距离设置为 10 点。
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        //我们使用一个包含两个单元格的表格来将文本的一部分放在一行上（带有页码）。
        //左对齐，文本的其他部分（带有版权）右对齐。
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        //它使用 PAGE 和 NUMPAGES 字段自动计算当前页码和页数。
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        //进行分页以创建第二页，在该页面上将显示主要的页眉/页脚。
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        //此部分不需要不同的首页页眉/页脚，我们只需要文档中的一个标题页，
        //并且此页面的页眉/页脚已在上一节中定义。
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        //此部分显示上一节的页眉/页脚
        //默认调用currentSection.HeadersFooters.LinkToPrevious(false)取消此页面宽度
        //对于新的部分来说有所不同，因此我们需要为页脚表设置不同的单元格宽度。
        currentSection.getHeadersFooters().linkToPrevious(false);
        //如果我们想为这一部分使用已经存在的页眉/页脚设置。
        //但经过一些小的修改，复制页眉/页脚可能会有所帮助
        //来自上一节并在我们想要的地方应用必要的修改。
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
copyHeadersFootersFromPreviousSection 方法源代码
```java
    //<摘要>
    //将页眉/页脚从前一节克隆并复制到指定节。
    /// </摘要>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## 结论

在本教程中，我们介绍了在 Aspose.Words for Java 中使用页眉和页脚的基础知识。您已经学习了如何创建、自定义和设置页眉和页脚的样式，以及其他必要的文档格式化技术。

有关更多详细信息和高级功能，请参阅[Aspose.Words Java 文档](https://reference.aspose.com/words/java/).

## 常见问题解答

### 1. 如何在文档页脚中添加页码？
您可以通过插入`PAGE`使用 Aspose.Words 将字段放入页脚。

### 2. Aspose.Words 与 Java 开发环境兼容吗？
是的，Aspose.Words 提供对 Java 开发的支持。请确保您已完成必要的设置。

### 3. 我可以自定义页眉和页脚的字体和样式吗？
当然，您可以自定义字体、对齐方式和其他样式，以使页眉和页脚具有视觉吸引力。

### 4. 奇数页和偶数页可以有不同的页眉吗？
是的，你可以使用`PageSetup.OddAndEvenPagesHeaderFooter`为奇数页和偶数页指定不同的页眉。

### 5. 如何开始使用 Aspose.Words for Java？
首先，请访问[Aspose.Words Java 文档](https://reference.aspose.com/words/java/)获得有关使用 API 的全面指导。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
