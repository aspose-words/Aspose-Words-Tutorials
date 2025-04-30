---
"description": "了解如何使用 Aspose.Words for .NET 无缝连接两个 Word 文档。按照我们的分步指南，即可顺利高效地完成文档合并。"
"linktitle": "加入连续"
"second_title": "Aspose.Words文档处理API"
"title": "加入连续"
"url": "/zh/net/join-and-append-documents/join-continuous/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 加入连续

## 介绍

您是否希望将两个 Word 文档无缝合并为一个，且不出现任何中断？Aspose.Words for .NET 提供了一个绝佳的解决方案，那就是使用“连续分节符”功能。本教程将逐步指导您完成整个过程，确保您轻松合并文档。让我们开始吧！

## 先决条件

在我们开始之前，请确保您已准备好所需的一切：

- Aspose.Words for .NET：如果您还没有，请下载并安装 [Aspose.Words for .NET](https://releases。aspose.com/words/net/).
- 开发环境：您可以使用 Visual Studio 或任何其他 .NET 开发环境。
- 示例文档：准备好两个要合并的 Word 文档。

## 导入命名空间

要使用 Aspose.Words for .NET，您需要在项目中导入必要的命名空间。操作方法如下：

```csharp
using Aspose.Words;
```

现在，为了清楚起见，我们将示例分解为多个步骤。

## 步骤 1：设置文档目录

首先，我们需要设置文档的存储目录。这将允许我们的代码找到要合并的文件。

```csharp
// 文档目录的路径 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替 `"YOUR DOCUMENT DIRECTORY"` 使用存储文档的实际路径。

## 步骤 2：加载源文档和目标文档

接下来，我们将源文档和目标文档加载到程序中。这两个文档就是您要合并的文档。

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

确保文件名和路径与您要使用的实际文件相匹配。

## 步骤 3：将节的开始设置为连续

为了使源文档的内容在目标文档之后立即出现，我们需要设置 `SectionStart` 源文档第一节的属性 `Continuous`。

```csharp
// 使文档直接出现在目标文档的内容之后。
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.Continuous;
```

这确保了合并文档时文档之间不会出现中断。

## 步骤 4：附加源文档

现在，我们将源文档附加到目标文档。此步骤确保将源文档的内容添加到目标文档的末尾。

```csharp
// 使用源文档中的原始样式附加源文档。
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

使用 `ImportFormatMode.KeepSourceFormatting` 确保源文档的格式保留在最终合并的文档中。

## 步骤5：保存合并文档

最后，我们将合并后的文档保存到指定的目录。这样就完成了文档合并的过程。

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.JoinContinuous.docx");
```

确保路径和文件名符合您的需要。

## 结论

就这样！只需几行代码，您就成功地使用 Aspose.Words for .NET 将两个 Word 文档合并为一个连续的文档。这个过程不仅简单，而且高效，确保您的文档保留其原始格式。

## 常见问题解答

### 我可以合并两个以上的文档吗？
是的，您可以通过加载其他文档并按顺序附加它们来重复该过程以合并多个文档。

### 原始格式会被保留吗？
是的，使用 `ImportFormatMode.KeepSourceFormatting` 确保保留源文档的格式。

### Aspose.Words for .NET 是否与 .NET Core 兼容？
是的，Aspose.Words for .NET 与 .NET Framework 和 .NET Core 兼容。

### 我可以合并具有不同页面设置的文档吗？
是的，但您可能需要调整页面设置属性以确保无缝合并。

### 如果遇到问题，我可以在哪里获得支持？
您可以从 Aspose 社区论坛获得支持 [这里](https://forum。aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}