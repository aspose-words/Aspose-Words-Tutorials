---
"description": "了解如何使用 Aspose.Words for .NET 防止 Word 文档中的表格跨页断裂。遵循我们的指南，维护专业且可读的文档。"
"linktitle": "保持桌子齐整"
"second_title": "Aspose.Words文档处理API"
"title": "保持桌子齐整"
"url": "/zh/net/programming-with-tables/keep-table-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 保持桌子齐整

## 介绍

您是否曾因 Word 文档中的表格横跨两页而感到沮丧？这就像您精心布局的信息突然在中途中断了一样！将表格保持在一页上对于可读性和演示效果至关重要。无论是报告、项目提案还是个人文档，表格拆分都会非常不协调。幸运的是，Aspose.Words for .NET 提供了一种巧妙的方法来解决这个问题。在本教程中，我们将逐步讲解如何保持表格的完整性和美观性。让我们开始吧！

## 先决条件

在开始之前，请确保您具备以下条件：

1. Aspose.Words for .NET - 如果您尚未安装，可以从 [这里](https://releases。aspose.com/words/net/).
2. 带有表格的 Word 文档 - 我们将使用包含跨越多页的表格的示例文档。
3. C# 基础知识 - 本教程假设您对 C# 编程有基本的了解。

## 导入命名空间

首先，让我们导入必要的命名空间。这将使我们能够访问 Aspose.Words for .NET 所需的类和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

让我们把这个过程分解成几个简单易懂的步骤。首先加载文档，最后保存更新后的文档，表格保持不变。

## 步骤 1：加载文档

要使用 Word 文档，我们首先需要加载它。我们将使用 `Document` 为此课程。

```csharp
// 文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## 第 2 步：访问表

接下来，我们需要获取要保留的表格。我们假设它是文档中的第一个表格。

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## 步骤 3：设置段落的 KeepWithNext

为了防止表格跨页断裂，我们需要设置 `KeepWithNext` 表格中每个段落的属性，最后一行的最后几个段落除外。

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
    foreach (Paragraph para in cell.Paragraphs)
    {
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
    }
}
```

## 步骤4：保存文档

最后，我们保存更新后的文档。这将应用我们的更改并确保表格保持在同一个页面上。

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## 结论

就这样！只需几行代码，即可防止Word文档中的表格跨页拆分。这个简单而有效的解决方案可确保您的表格保持整洁专业，从而增强文档的可读性。Aspose.Words for .NET 使处理此类格式问题变得轻而易举，让您专注于创建精彩的内容。

## 常见问题解答

### 我可以使用此方法将多个表放在一起吗？  
是的，您可以通过遍历文档中的每个表将相同的逻辑应用于多个表。

### 如果我的表格太大，无法放在一页上怎么办？  
如果表格太大，无法在一页内显示，它仍然会跨越多个页面。这种方法可以确保较小的表格保持完整，不会分裂。

### 有没有办法自动对文档中的所有表格进行此操作？  
是的，您可以循环遍历文档中的所有表格并应用 `KeepWithNext` 每个段落的属性。

### 我需要 Aspose.Words for .NET 的付费许可证吗？  
您可以从以下位置开始免费试用 [这里](https://releases.aspose.com/)，但为了获得全部功能，建议购买付费许可证。

### 我可以将其他格式应用于表格同时保持它们一致吗？  
当然！您可以根据需要设置表格格式，同时确保它们位于同一页上。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}