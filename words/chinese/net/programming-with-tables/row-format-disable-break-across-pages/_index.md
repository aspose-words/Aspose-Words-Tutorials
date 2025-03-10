---
title: 行格式禁用跨页拆分
linktitle: 行格式禁用跨页拆分
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 禁用 Word 文档中跨页的换行符，以保持表格的可读性和格式。
weight: 10
url: /zh/net/programming-with-tables/row-format-disable-break-across-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 行格式禁用跨页拆分

## 介绍

在处理 Word 文档中的表格时，您可能希望确保行不会跨页中断，这对于维护文档的可读性和格式至关重要。Aspose.Words for .NET 提供了一种简单的方法来禁用跨页的行中断。

在本教程中，我们将引导您完成使用 Aspose.Words for .NET 在 Word 文档中禁用跨页换行的过程。

## 先决条件

在开始之前，请确保您满足以下先决条件：
- 已安装 Aspose.Words for .NET 库。
- 包含跨越多页的表格的 Word 文档。

## 导入命名空间

首先，在您的项目中导入必要的命名空间：

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## 步骤 1：加载文档

加载包含跨越多页的表格的文档。

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## 第 2 步：访问表

访问文档中的第一个表格。假设您要修改的表格是文档中的第一个表格。

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## 步骤 3：禁用所有行的跨页分页

循环遍历表中的每一行并设置`AllowBreakAcrossPages`财产`false`。这确保行不会跨页。

```csharp
//禁用表格中所有行的跨页分页。
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## 步骤 4：保存文档

将修改后的文档保存到您指定的目录中。

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## 结论

在本教程中，我们演示了如何使用 Aspose.Words for .NET 禁用 Word 文档中跨页的换行符。通过遵循上面概述的步骤，您可以确保表格行保持完整且不会跨页拆分，从而保持文档的可读性和格式。

## 常见问题解答

### 我可以针对特定行（而不是所有行）禁用跨页换行吗？  
是的，您可以通过访问所需行并设置其`AllowBreakAcrossPages`财产`false`.

### 此方法对带有合并单元格的表格有效吗？  
是的，此方法适用于包含合并单元格的表格。属性`AllowBreakAcrossPages`适用于整行，无论单元格是否合并。

### 如果表嵌套在另一个表中，这种方法是否有效？  
是的，您可以用同样的方式访问和修改嵌套表。确保您通过其索引或其他属性正确引用嵌套表。

### 如何检查某一行是否允许跨页分行？  
您可以通过访问`AllowBreakAcrossPages`的财产`RowFormat`并检查其价值。

### 有没有办法将此设置应用于文档中的所有表格？  
是的，您可以循环遍历文档中的所有表格并将此设置应用于每个表格。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
