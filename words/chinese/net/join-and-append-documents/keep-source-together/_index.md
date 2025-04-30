---
"description": "学习如何使用 Aspose.Words for .NET 防止表格跨页断裂，并遵循本分步指南。确保 Word 文档整洁、专业"
"linktitle": "保持桌子齐整"
"second_title": "Aspose.Words文档处理API"
"title": "保持桌子齐整"
"url": "/zh/net/join-and-append-documents/keep-source-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 保持桌子齐整

## 介绍

表格是许多 Word 文档的重要组成部分，但有时您可能会遇到表格跨越两页的情况。这会扰乱文档的流畅性并影响其可读性。如果有一种方法可以将整个表格保持在一页中，那岂不是很好？有了 Aspose.Words for .NET，这个问题就可以轻松解决！在本教程中，我们将介绍如何防止表格跨越页面，确保您的文档看起来整洁专业。

## 先决条件

在开始本教程之前，请确保您已准备好顺利完成本教程所需的一切。

### Aspose.Words for .NET 库

首先，您需要安装 Aspose.Words for .NET。这是一个功能强大的库，允许您以编程方式处理 Word 文档。

- [下载 Aspose.Words for .NET](https://releases.aspose.com/words/net/)

### 开发环境

您应该设置一个开发环境来运行 C# 代码，例如：

- Visual Studio（任何最新版本）
- .NET Framework 2.0 或更高版本

### 带有表格的 Word 文档

你需要一个包含表格的 Word 文档。在本教程中，我们将使用一个名为 `"Table spanning two pages.docx"`。该文件包含一个当前跨越两页的表格。

### 临时许可证（可选）

虽然 Aspose.Words 提供免费试用，但您可能想使用 [临时执照](https://purchase.aspose.com/temporary-license/) 充分发挥图书馆的潜力。

## 导入包

在编写任何代码之前，我们需要导入使用 Aspose.Words for .NET 所需的命名空间。在代码文件顶部添加以下导入：

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

这些命名空间使您可以访问以下类 `Document`， `Table`， `Cell`以及我们将在本教程中使用的其他内容。

## 步骤 1：加载文档

我们首先需要加载包含表格的 Word 文档。为此，我们将使用 `Document` 来自 Aspose.Words 的类。该类允许您以编程方式打开和操作 Word 文件。

```csharp
// 文档目录的路径。
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

在此代码片段中，我们指定了文档的位置。替换 `"YOUR DOCUMENTS DIRECTORY"` 与存储文档的实际目录。

## 第 2 步：访问表

文档加载完成后，下一步是访问我们想要合并的表格。在本例中，我们假设该表格是文档中的第一个表格。

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

这行代码查找文档中的第一个表格。 `GetChild` 方法检索特定类型的节点，在本例中是 `NodeType.Table`。 这 `0` 表示我们想要第一个表，并且 `true` 标志确保我们递归搜索所有子节点。

## 步骤 3：循环遍历表格单元格

现在，我们需要循环遍历表格中的每个单元格。由于表格包含多行，每行又包含多个单元格，因此我们将遍历每个单元格，并确保它不会跨页中断。

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

这里， `GetChildNodes` 检索表格中的所有单元格，然后循环遍历每个单元格。 `EnsureMinimum()` 方法确保每个单元格至少包含一个段落，因为空单元格可能会在以后引起问题。

## 步骤 4：设置 KeepWithNext 属性

为了防止表格跨页断裂，我们需要设置 `KeepWithNext` 表格中每个段落的 属性。此属性可确保当前段落与下一个段落保持一致，从而有效防止它们之间出现分页符。

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

此循环检查每个单元格内的每个段落。条件确保我们不应用 `KeepWithNext` 属性应用于最后一行的最后一个段落。否则，该属性将不起作用，因为没有下一个段落。

## 步骤5：保存文档

最后，应用 `KeepWithNext` 属性，我们需要保存修改后的文档。

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

这行代码会用新名称保存更新后的文档，并保留原始文件。现在您可以打开生成的文件，并看到表格不再拆分成两页！

## 结论

就这样！只需遵循这些简单的步骤，您就可以使用 Aspose.Words for .NET 轻松防止 Word 文档中的表格跨页断裂。无论您处理的是报告、合同还是其他文档，保持表格完整都能确保文档更加精美、专业。

Aspose.Words 的优点在于其灵活性和易用性，让您无需在计算机上安装 Microsoft Word，即可通过编程操作 Word 文档。现在您已经掌握了如何整理表格，接下来探索该库的其他功能，将您的文档处理技能提升到新的水平！

## 常见问题解答

### 为什么使用此代码后我的表格仍然会跨页？

如果你的桌子仍然破损，请确保你已经应用了 `KeepWithNext` 属性是否正确。仔细检查每个单元格中除最后一个段落之外的所有段落是否都设置了此属性。

### 我可以只将特定的行放在一起吗？

是的，你可以选择性地应用 `KeepWithNext` 属性到表格中的特定行或段落来控制哪些部分应该保持在一起。

### 这种方法适用于大表吗？

对于非常大的表格，如果一页空间不足以容纳整个表格，Word 仍可能会将其拆分到多个页面。请考虑调整表格的格式或边距以适应更大的表格。

### 我可以将此方法用于其他文档格式吗？

是的！Aspose.Words for .NET 支持多种格式，例如 DOC、DOCX、PDF 等。所有支持表格的格式均可使用相同的方法。

### Aspose.Words for .NET 是一个免费库吗？

Aspose.Words for .NET 提供免费试用，但要使用所有功能，您需要购买许可证。您可以在 [Aspose购买页面](https://purchase。aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}