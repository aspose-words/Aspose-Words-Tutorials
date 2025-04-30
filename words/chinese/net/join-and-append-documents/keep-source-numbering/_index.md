---
"description": "学习如何使用 Aspose.Words for .NET 导入文档并保留其格式。包含代码示例的分步指南。"
"linktitle": "保留源编号"
"second_title": "Aspose.Words文档处理API"
"title": "保留源编号"
"url": "/zh/net/join-and-append-documents/keep-source-numbering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 保留源编号

## 介绍

使用 Aspose.Words for .NET 时，可以使用 `NodeImporter` 课程。本教程将逐步指导您完成整个过程。

## 先决条件

开始之前，请确保您已准备好以下内容：
- 您的机器上安装了 Visual Studio。
- 已安装 Aspose.Words for .NET。如果没有，请从 [这里](https://releases。aspose.com/words/net/).
- 具有 C# 和 .NET 编程的基本知识。

## 导入命名空间

首先，在您的项目中包含必要的命名空间：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## 步骤 1：设置您的项目

首先在 Visual Studio 中创建一个新的 C# 项目，然后通过 NuGet 包管理器安装 Aspose.Words。

## 第 2 步：初始化文档
创建源的实例（`srcDoc`) 和目的地 (`dstDoc`) 文件。

```csharp
// 文档目录的路径 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## 步骤 3：配置导入选项
设置导入选项以维护源格式，包括编号段落。

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## 步骤 4：导入段落
遍历源文档中的段落并将其导入目标文档。

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## 步骤5：保存文档
将合并的文档保存到您想要的位置。

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## 结论

总之，使用 Aspose.Words for .NET 导入文档并保留格式非常简单， `NodeImporter` 类。此方法可确保您的文档无缝地保持其原始外观和结构。

## 常见问题解答

### 我可以导入具有不同格式样式的文档吗？
是的， `NodeImporter` 类支持导入具有多种格式样式的文档。

### 如果我的文档包含复杂的表格和图像怎么办？
Aspose.Words for .NET 在导入操作期间处理表格和图像等复杂结构。

### Aspose.Words 是否与所有版本的 .NET 兼容？
Aspose.Words 支持 .NET Framework 和 .NET Core 版本，实现无缝集成。

### 如何处理文档导入过程中的错误？
使用try-catch块来处理导入过程中可能发生的异常。

### 在哪里可以找到有关 Aspose.Words for .NET 的更详细文档？
访问 [文档](https://reference.aspose.com/words/net/) 以获得全面的指南和 API 参考。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}