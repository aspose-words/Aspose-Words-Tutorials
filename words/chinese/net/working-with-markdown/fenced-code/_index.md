---
title: 围栏代码
linktitle: 围栏代码
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 将隔离代码和信息字符串添加到 Word 文档。包含分步指南。增强您的文档格式化技能。
weight: 10
url: /zh/net/working-with-markdown/fenced-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 围栏代码

## 介绍

嗨，程序员们！今天，我们将深入研究 Aspose.Words for .NET 的世界，掌握向 Word 文档添加隔离代码和带信息字符串的隔离代码的技巧。想象一下您的 Word 文档是一块画布，而您，这位艺术家，将以经验丰富的开发人员的精准度进行绘画。使用 Aspose.Words，您可以用结构化、格式化的代码块以编程方式增强您的文档，使您的技术文档以专业性和清晰度脱颖而出。

## 先决条件

在开始本教程之前，请确保您已准备好所需的一切：

- C# 基础知识：对 C# 的一般了解将帮助您快速掌握概念。
-  Aspose.Words for .NET：您需要安装 Aspose.Words for .NET。如果您还没有，请获取它[这里](https://releases.aspose.com/words/net/).
- 开发环境：Visual Studio 或任何您熟悉的其他 C# IDE。

## 导入命名空间

首先，您需要导入必要的命名空间。这就像在开始项目之前收集所有工具一样。

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

现在，让我们逐步分解这个过程。

## 步骤 1：设置项目

在我们可以在 Word 文档中创建漂亮的格式化代码块之前，我们需要在 Visual Studio 中建立一个新项目。

1. 创建新项目：打开 Visual Studio 并创建一个新的 C# 控制台应用程序。
2. 添加 Aspose.Words 参考：通过 NuGet 包管理器安装 Aspose.Words。您可以在解决方案资源管理器中右键单击您的项目，选择“管理 NuGet 包”，然后搜索 Aspose.Words。

## 步骤 2：初始化 DocumentBuilder

现在您的项目已经设置好了，让我们初始化 DocumentBuilder，它将是我们向 Word 文档添加内容的主要工具。

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## 步骤 3：创建隔离代码的样式

要添加隔离代码，我们首先需要创建样式。可以将其视为设置代码块的主题。

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## 步骤 4：向文档添加隔离代码

样式准备好后，我们现在可以向文档添加隔离的代码块。

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## 步骤 5：使用信息字符串创建围栏代码样式

有时，您可能想要指定编程语言或向代码块添加额外信息。让我们为此创建一个样式。

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## 步骤 6：将带有信息字符串的隔离代码添加到文档

现在，让我们添加一个带有信息字符串的隔离代码块来表明它是 C# 代码。

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## 结论

恭喜！您刚刚使用 Aspose.Words for .NET 将隔离代码块和带信息字符串的隔离代码添加到您的 Word 文档中。这只是冰山一角。使用 Aspose.Words，您可以自动化和增强文档处理，使其达到新的高度。继续探索并快乐地编码！

## 常见问题解答

### 什么是 Aspose.Words for .NET？
Aspose.Words for .NET 是一个功能强大的库，允许开发人员以编程方式创建、操作和转换 Word 文档。

### 我可以将 Aspose.Words 与其他编程语言一起使用吗？
Aspose.Words 主要支持 .NET 语言，但也有适用于 Java、Python 和其他语言的版本。

### Aspose.Words 可以免费使用吗？
 Aspose.Words 是一款商业产品，但您可以下载免费试用版[这里](https://releases.aspose.com/)探索其特征。

### 如何获得 Aspose.Words 的支持？
您可以获得 Aspose 社区和开发人员的支持[这里](https://forum.aspose.com/c/words/8).

### Aspose.Words 还提供哪些其他功能？
Aspose.Words 提供广泛的功能，包括文档转换、基于模板的文档生成、报告等。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
