---
"description": "了解如何使用 Aspose.Words for .NET 禁用 Word 文档中跨页的换行符，以保持表格的可读性和格式。"
"linktitle": "行格式禁用跨页"
"second_title": "Aspose.Words文档处理API"
"title": "行格式禁用跨页"
"url": "/zh/net/programming-with-tables/row-format-disable-break-across-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 行格式禁用跨页

## 介绍

在 Word 文档中使用表格时，您可能希望确保行不会跨页换行，这对于维护文档的可读性和格式至关重要。Aspose.Words for .NET 提供了一种简单的方法来禁用跨页换行。

在本教程中，我们将引导您完成使用 Aspose.Words for .NET 在 Word 文档中禁用跨页换行的过程。

## 先决条件

在开始之前，请确保您满足以下先决条件：
- 已安装 Aspose.Words for .NET 库。
- 包含跨多页表格的 Word 文档。

## 导入命名空间

首先，在您的项目中导入必要的命名空间：

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## 步骤 1：加载文档

加载包含跨越多页的表格的文档。

```csharp
// 文档目录的路径 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## 第 2 步：访问表

访问文档中的第一个表格。假设您要修改的表格是文档中的第一个表格。

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## 步骤 3：禁用所有行的跨页功能

循环遍历表中的每一行并设置 `AllowBreakAcrossPages` 财产 `false`。这确保行不会跨页断开。

```csharp
// 禁用表格中所有行的跨页断行功能。
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## 步骤4：保存文档

将修改后的文档保存到指定的目录中。

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## 结论

在本教程中，我们演示了如何使用 Aspose.Words for .NET 禁用 Word 文档中的跨页换行。按照上述步骤操作，您可以确保表格行保持完整，不会跨页拆分，从而保持文档的可读性和格式。

## 常见问题解答

### 我可以针对特定行（而不是所有行）禁用跨页换行吗？  
是的，您可以通过访问所需行并设置其 `AllowBreakAcrossPages` 财产 `false`。

### 此方法对具有合并单元格的表格有效吗？  
是的，此方法适用于包含合并单元格的表格。属性 `AllowBreakAcrossPages` 适用于整行，无论单元格是否合并。

### 如果表嵌套在另一个表中，此方法是否有效？  
是的，您可以用相同的方式访问和修改嵌套表。请确保通过索引或其他属性正确引用嵌套表。

### 如何检查某一行是否允许跨页？  
您可以通过访问 `AllowBreakAcrossPages` 的财产 `RowFormat` 并检查其值。

### 有没有办法将此设置应用于文档中的所有表格？  
是的，您可以循环遍历文档中的所有表格并将此设置应用于每个表格。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}