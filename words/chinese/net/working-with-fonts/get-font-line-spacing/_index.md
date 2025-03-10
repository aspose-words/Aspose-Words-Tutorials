---
title: 获取字体行距
linktitle: 获取字体行距
second_title: Aspose.Words 文档处理 API
description: 通过本分步教程学习如何使用 Aspose.Words for .NET 获取字体行距。非常适合开发人员。
weight: 10
url: /zh/net/working-with-fonts/get-font-line-spacing/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 获取字体行距

## 介绍

Aspose.Words for .NET 是一个功能强大的库，允许您以编程方式创建、操作和转换 Word 文档。您可能需要执行的一项常见任务是检索文档中特定字体的行距。在本教程中，我们将逐步指导您完成该过程，确保您可以使用 Aspose.Words for .NET 轻松获取字体行距。 

## 先决条件

在深入研究代码之前，请确保您已满足以下先决条件：

1.  Aspose.Words for .NET Library：从以下网址下载并安装最新版本[这里](https://releases.aspose.com/words/net/).
2. 开发环境：确保您已安装类似 Visual Studio 的 IDE。
3. C# 基础知识：本教程假设您对 C# 编程有基本的了解。

## 导入命名空间

首先，您需要在 C# 项目中导入必要的命名空间。这些命名空间将允许您访问 Aspose.Words 功能。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

让我们将获取字体行距的过程分解为简单、易于管理的步骤。

## 步骤 1：创建新文档

第一步是使用 Aspose.Words for .NET 创建一个新的 Word 文档实例。

```csharp
Document doc = new Document();
```

## 第 2 步：初始化 DocumentBuilder

接下来，我们需要初始化`DocumentBuilder`对象。该对象将帮助我们构建和操作文档内容。

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步骤 3：设置字体属性

现在，我们设置要插入的文本的字体属性。在本例中，我们将使用“Calibri”字体。

```csharp
builder.Font.Name = "Calibri";
```

## 步骤 4：将文本写入文档

使用`DocumentBuilder`对象，将一些文本写入文档。此文本将使用我们在上一步中设置的字体属性。

```csharp
builder.Writeln("Sample Text");
```

## 步骤 5：检索字体对象

要获取行距，我们需要访问刚刚添加的文本的字体对象。这可以通过浏览文档结构到第一个段落来完成。

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## 步骤 6：获取行距

最后，我们从字体对象中检索行距并将其打印到控制台。

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## 结论

就这样！使用 Aspose.Words for .NET 检索字体行距非常简单，只需将其分解为这些简单的步骤即可。无论您是创建新文档还是使用现有文档，Aspose.Words 都提供了有效管理字体属性所需的所有工具。

## 常见问题解答

### 什么是 Aspose.Words for .NET？
Aspose.Words for .NET 是一个功能强大的库，允许开发人员使用 C# 以编程方式创建、操作和转换 Word 文档。

### 我可以在其他.NET 语言中使用 Aspose.Words for .NET 吗？
是的，您可以将 Aspose.Words for .NET 与任何 .NET 语言一起使用，包括 VB.NET 和 F#。

### 如何下载 Aspose.Words for .NET？
您可以从以下网址下载最新版本的 Aspose.Words for .NET[这里](https://releases.aspose.com/words/net/).

### Aspose.Words for .NET 有免费试用版吗？
是的，你可以从[这里](https://releases.aspose.com/).

### 在哪里可以找到 Aspose.Words for .NET 的文档？
 Aspose.Words for .NET 文档现已发布[这里](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
