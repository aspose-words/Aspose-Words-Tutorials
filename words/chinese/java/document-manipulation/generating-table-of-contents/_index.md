---
"description": "学习如何使用 Aspose.Words for Java 生成和自定义目录 (TOC)。轻松创建井然有序、专业的文档。"
"linktitle": "生成目录"
"second_title": "Aspose.Words Java文档处理API"
"title": "在 Aspose.Words for Java 中生成目录"
"url": "/zh/java/document-manipulation/generating-table-of-contents/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中生成目录


## Aspose.Words for Java 中目录生成简介

在本教程中，我们将引导您使用 Aspose.Words for Java 生成目录 (TOC)。目录是创建井然有序文档的关键功能。我们将介绍如何自定义目录的外观和布局。

## 先决条件

在开始之前，请确保您已在 Java 项目中安装并设置了 Aspose.Words for Java。

## 步骤 1：创建新文档

首先，让我们创建一个新的文档。

```java
Document doc = new Document();
```

## 第 2 步：自定义目录样式

要自定义目录的外观，您可以修改与其关联的样式。在本例中，我们将第一级目录条目设置为粗体。

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## 步骤 3：向文档添加内容

您可以将内容添加到文档中。这些内容将用于生成目录。

## 步骤 4：生成目录

要生成目录，请在文档中的所需位置插入目录字段。此字段将根据文档中的标题和样式自动填充内容。

```java
// 在文档的所需位置插入目录字段。
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## 步骤5：保存文档

最后，将文档与目录一起保存。

```java
doc.save("your_output_path_here");
```

## 自定义目录中的制表位

您还可以自定义目录中的制表位，以控制页码的布局。更改制表位的方法如下：

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // 获取本段落使用的第一个制表符，用于对齐页码。
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // 删除旧标签。
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // 在修改的位置插入一个新标签（例如，向左 50 个单位）。
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

现在，您的文档中已经有了自定义的目录，其中的制表位已调整以便页码对齐。


## 结论

在本教程中，我们探索了如何使用 Aspose.Words for Java（一个功能强大的 Word 文档处理库）生成目录 (TOC)。结构良好的目录对于组织和浏览冗长的文档至关重要，而 Aspose.Words 提供了轻松创建和自定义目录的工具。

## 常见问题解答

### 如何更改目录条目的格式？

您可以使用以下方式修改与目录级别相关的样式 `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`，其中 X 是 TOC 水平。

### 如何为我的目录添加更多级别？

要在目录中包含更多级别，您可以修改目录字段并指定所需的级别数。

### 我可以更改特定目录条目的制表位位置吗？

是的，如上面的代码示例所示，您可以通过遍历段落并相应地修改制表位来更改特定目录条目的制表位位置。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}