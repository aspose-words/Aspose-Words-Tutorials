---
title: 结构化文档标签范围开始 XML 映射
linktitle: 结构化文档标签范围开始 XML 映射
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 将 XML 数据动态绑定到 Word 中的结构化文档标签。按照我们的分步指南进行操作。
weight: 10
url: /zh/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 结构化文档标签范围开始 XML 映射

## 介绍

您是否曾经想过将 XML 数据动态插入 Word 文档？好吧，您很幸运！Aspose.Words for .NET 使这项任务变得轻而易举。在本教程中，我们将深入研究结构化文档标签范围开始 XML 映射。此功能允许您将自定义 XML 部分绑定到内容控件，确保您的文档内容与您的 XML 数据无缝更新。准备将您的文档转变为动态杰作。

## 先决条件

在进入编码部分之前，让我们确保您已准备好所需的一切：

1.  Aspose.Words for .NET Library：确保您拥有最新版本。您可以下载它[这里](https://releases.aspose.com/words/net/).
2. 开发环境：Visual Studio 或任何其他支持 C# 的 IDE。
3. C# 基础知识：必须熟悉 C# 编程。
4. Word 文档：可使用的示例 Word 文档。

## 导入命名空间

首先，让我们导入必要的命名空间。这将确保我们可以访问 Aspose.Words for .NET 中所有必需的类和方法。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## 步骤 1：设置文档目录

每个项目都需要基础，对吧？在这里，我们设置文档目录的路径。

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 第 2 步：加载 Word 文档

接下来，我们加载 Word 文档。这是我们将插入 XML 数据的文档。

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## 步骤 3：添加自定义 XML 部分

我们需要构造一个包含要插入的数据的 XML 部分，并将其添加到文档的 CustomXmlPart 集合中。此自定义 XML 部分将作为我们结构化文档标签的数据源。

### 创建 XML 部件

首先，为 XML 部分生成唯一的 ID 并定义其内容。

```csharp
//构造一个包含数据的 XML 部分并将其添加到文档的 CustomXmlPart 集合中。
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### 验证 XML 部分内容

为了确保 XML 部分正确添加，我们打印其内容。

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## 步骤 4：创建结构化文档标签

结构化文档标签 (SDT) 是一种可以绑定到 XML 部分的内容控件。在这里，我们创建一个 SDT，它将显示我们自定义 XML 部分的内容。

首先，在文档中找到 SDT 范围的开始。

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## 步骤 5：设置 SDT 的 XML 映射

现在，是时候将 XML 部分绑定到 SDT 了。通过设置 XML 映射，我们可以指定 XML 数据的哪一部分应显示在 SDT 中。

 XPath 指向我们想要显示的 XML 部分中的特定元素。这里，我们指向第二个`<text>`元素内的`<root>`元素。

```csharp
//为我们的 StructuredDocumentTag 设置映射
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## 步骤 6：保存文档

最后，保存文档以查看实际更改。Word 文档中的 SDT 现在将显示指定的 XML 内容。

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## 结论

就这样！您已成功使用 Aspose.Words for .NET 将 XML 部分映射到 Word 文档中的结构化文档标签。此强大功能使您能够轻松创建动态和数据驱动的文档。无论您是生成报告、发票还是任何其他文档类型，XML 映射都可以显著简化您的工作流程。

## 常见问题解答

### Word 中的结构化文档标签是什么？
结构化文档标签，也称为内容控件，是 Word 文档中特定类型内容的容器。它们可用于绑定数据、限制编辑或指导用户创建文档。

### 如何动态更新 XML 部分内容？
您可以通过修改`xmlPartContent`字符串，然后再将其添加到文档中。只需使用新数据更新字符串，然后将其添加到`CustomXmlParts`收藏。

### 我可以将多个 XML 部分绑定到同一文档中的不同 SDT 吗？
是的，您可以将多个 XML 部分绑定到同一文档中的不同 SDT。每个 SDT 都可以拥有自己独特的 XML 部分和 XPath 映射。

### 是否可以将复杂的 XML 结构映射到 SDT？
当然！您可以使用详细的 XPath 表达式将复杂的 XML 结构映射到 SDT，这些表达式可以准确指向 XML 部分中的所需元素。

### 如何从文档中删除 XML 部分？
您可以通过调用`Remove`方法`CustomXmlParts`收集，传递`xmlPartId`您想要删除的 XML 部分。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
