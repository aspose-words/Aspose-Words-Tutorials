---
title: 创建映射到自定义 XML 部分的表重复部分
linktitle: 创建映射到自定义 XML 部分的表重复部分
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 创建一个表格，其中重复部分映射到 Word 文档中的 CustomXmlPart。
weight: 10
url: /zh/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建映射到自定义 XML 部分的表重复部分

## 介绍

在本教程中，我们将介绍如何使用 Aspose.Words for .NET 创建带有重复部分的表格，该表格将映射到自定义 XML 部分。这对于基于结构化数据动态生成文档特别有用。

## 先决条件

在开始之前，请确保您已准备好以下内容：
1. 已安装 Aspose.Words for .NET 库。您可以从[Aspose 网站](https://releases.aspose.com/words/net/).
2. 对 C# 和 XML 有基本的了解。

## 导入命名空间

确保在你的项目中包含必要的命名空间：

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## 步骤 1：初始化 Document 和 DocumentBuilder

首先，创建一个新文档并初始化一个`DocumentBuilder`：

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步骤 2：添加自定义 XML 部分

向文档添加自定义 XML 部分。此 XML 包含我们要映射到表的数据：

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## 步骤 3：创建表结构

接下来，使用`DocumentBuilder`创建表头：

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## 步骤 4：创建重复部分

创建一个`StructuredDocumentTag`（SDT）作为重复部分并将其映射到 XML 数据：

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## 步骤 5：创建重复部分项

为重复节项创建 SDT，并将其添加到重复节：

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## 步骤 6：将 XML 数据映射到表格单元格

为标题和作者创建 SDT，将它们映射到 XML 数据，并将它们附加到行：

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## 步骤 7：保存文档

最后将文档保存到指定目录：

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## 结论

通过执行这些步骤，您已成功使用 Aspose.Words for .NET 创建了一个表格，其中重复部分映射到自定义 XML 部分。这允许基于结构化数据生成动态内容，使文档创建更加灵活和强大。

## 常见问题解答

### 什么是 StructuredDocumentTag (SDT)？
SDT（也称为内容控制）是文档中用于包含结构化数据的有界区域。

### 我可以在自定义 XML 部分使用其他数据类型吗？
是的，您可以使用任何数据类型构建自定义 XML 部分并进行相应的映射。

### 如何向重复部分添加更多行？
重复部分会自动复制映射的 XML 路径中每个项目的行结构。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
