---
title: 在 Aspose.Words for Java 中使用结构化文档标签 (SDT)
linktitle: 使用结构化文档标签 (SDT)
second_title: Aspose.Words Java 文档处理 API
description: 通过本综合指南学习如何在 Aspose.Words for Java 中使用结构化文档标签 (SDT)。创建、修改和绑定 SDT 到自定义 XML 数据。
weight: 19
url: /zh/java/document-manipulation/using-structured-document-tags/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用结构化文档标签 (SDT)


## Aspose.Words for Java 中使用结构化文档标签 (SDT) 的简介

结构化文档标签 (SDT) 是 Aspose.Words for Java 中的一项强大功能，可让您在文档中创建和操作结构化内容。在本综合指南中，我们将引导您了解在 Aspose.Words for Java 中使用 SDT 的各个方面。无论您是初学者还是经验丰富的开发人员，您都会在本文中找到有价值的见解和实际示例。

## 入门

在深入了解详细信息之前，让我们设置环境并创建一个基本的 SDT。在本节中，我们将介绍以下主题：

- 创建新文档
- 添加结构化文档标签
- 保存文档

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//创建 CHECKBOX 类型的结构化文档标签
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

//保存文档
doc.save("WorkingWithSDT.docx");
```

## 检查复选框 SDT 的当前状态

将复选框 SDT 添加到文档后，您可能希望以编程方式检查其当前状态。当您需要验证用户输入或根据复选框状态执行特定操作时，这会很有用。

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    //复选框被选中
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## 修改内容控件

在本节中，我们将探讨如何修改文档中的内容控件。我们将介绍三种类型的内容控件：纯文本、下拉列表和图片。

### 修改纯文本内容控件

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    //清除现有内容
    sdtPlainText.removeAllChildren();

    //添加新文本
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### 修改下拉列表内容控件

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    //从列表中选择第二项
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### 修改图片内容控件

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    //用新图像替换
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## 创建 ComboBox 内容控件

ComboBox 内容控件允许用户从预定义的选项列表中进行选择。让我们在文档中创建一个。

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## 使用富文本内容控件

富文本内容控件非常适合将格式化的文本添加到文档中。让我们创建一个并设置其内容。

```java
Document doc = new Document();
StructuredDocumentTag sdtRichText = new StructuredDocumentTag(doc, SdtType.RICH_TEXT, MarkupLevel.BLOCK);
Paragraph para = new Paragraph(doc);
Run run = new Run(doc);
run.setText("Hello World");
run.getFont().setColor(Color.GREEN);
para.getRuns().add(run);
sdtRichText.getChildNodes().add(para);
doc.getFirstSection().getBody().appendChild(sdtRichText);

doc.save("RichTextDocument.docx");
```

## 设置内容控件样式

您可以将样式应用于内容控件以增强文档的外观。让我们看看如何设置内容控件的样式。

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

//应用自定义样式
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## 将 SDT 绑定到自定义 XML 数据

在某些情况下，您可能需要将 SDT 绑定到自定义 XML 数据以生成动态内容。让我们探索如何实现这一点。

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## 创建具有映射到自定义 XML 数据的重复部分的表

具有重复部分的表格对于呈现结构化数据非常有用。让我们创建这样的表格并将其映射到自定义 XML 数据。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
CustomXmlPart xmlPart = doc.getCustomXmlParts().add("Books", "<books>...</books>");
Table table = builder.startTable();
builder.insertCell();
builder.write("Title");
builder.insertCell();
builder.write("Author");
builder.endRow();
builder.endTable();

StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION, MarkupLevel.ROW);
repeatingSectionSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book", "");
table.appendChild(repeatingSectionSdt);

StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION_ITEM, MarkupLevel.ROW);
repeatingSectionSdt.appendChild(repeatingSectionItemSdt);

Row row = new Row(doc);
repeatingSectionItemSdt.appendChild(row);

StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
titleSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.appendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
authorSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.appendChild(authorSdt);

doc.save("RepeatingTableDocument.docx");
```

## 使用多部分结构化文档标签

结构化文档标签可以跨越文档中的多个部分。在本节中，我们将探讨如何使用多部分 SDT。

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## 结论

Aspose.Words for Java 中的结构化文档标签提供了一种管理和格式化文档内容的多功能方法。无论您需要创建模板、表单还是动态文档，SDT 都能提供您所需的灵活性和控制力。通过遵循本文提供的示例和指南，您可以利用 SDT 的强大功能来增强文档处理任务。

## 常见问题解答

### 结构化文档标签 (SDT) 的用途是什么？

结构化文档标签 (SDT) 用于组织和格式化文档中的内容，从而更容易创建模板、表单和结构化文档。

### 如何检查 Checkbox SDT 的当前状态？

您可以使用以下方式检查 Checkbox SDT 的当前状态`setChecked`方法，如文章中所演示的那样。

### 我可以将样式应用于内容控件吗？

是的，您可以将样式应用于内容控件以自定义它们在文档中的外观。

### 是否可以将 SDT 绑定到自定义 XML 数据？

是的，您可以将 SDT 绑定到自定义 XML 数据，从而实现动态内容生成和数据映射。

### SDT 中的重复部分是什么？

SDT 中的重复部分允许您创建包含动态数据的表，其中可以根据映射的 XML 数据重复行。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
