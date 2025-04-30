---
"description": "了解如何使用 Aspose.Words for .NET 检测纯文本文档中带有空格的编号并确保正确识别您的列表。"
"linktitle": "检测带有空格的数字"
"second_title": "Aspose.Words文档处理API"
"title": "检测带有空格的数字"
"url": "/zh/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 检测带有空格的数字

## 介绍

Aspose.Words 专为 .NET 爱好者打造！今天，我们将深入探讨一项引人入胜的功能，它能让纯文本文档中的列表处理变得轻而易举。您是否遇到过这样的情况：文本文件中某些行本应是列表，但加载到 Word 文档中时却显示不正确？现在，我们有一个巧妙的技巧：检测空格编号。本教程将引导您使用 `DetectNumberingWithWhitespaces` Aspose.Words for .NET 中的选项可确保您的列表被正确识别，即使数字和文本之间存在空格。

## 先决条件

在开始之前，请确保您具备以下条件：

- Aspose.Words for .NET：您可以从 [Aspose 版本](https://releases.aspose.com/words/net/) 页。
- 开发环境：Visual Studio 或任何其他 C# IDE。
- 您的机器上安装了 .NET Framework。
- C# 基础知识：了解基础知识将帮助您理解示例。

## 导入命名空间

在开始编写代码之前，请确保已在项目中导入必要的命名空间。以下是一段快速入门代码：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

我们将这个过程分解成几个简单易懂的步骤。每个步骤都会引导您完成必要的代码，并解释具体操作。

## 步骤 1：定义文档目录

首先，让我们设置文档目录的路径。这是存储输入和输出文件的地方。

```csharp
// 文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步骤2：创建纯文本文档

接下来，我们将创建一个纯文本文档作为字符串。该文档将包含可能被解释为列表的部分。

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## 步骤 3：配置 LoadOptions

为了检测带有空格的数字，我们需要设置 `DetectNumberingWithWhitespaces` 选择 `true` 在一个 `TxtLoadOptions` 目的。

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## 步骤 4：加载文档

现在，让我们使用 `TxtLoadOptions` 作为参数。这确保第四个列表（带有空格）被正确检测。

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## 步骤5：保存文档

最后，将文档保存到指定的目录。这将输出一个包含正确检测列表的 Word 文档。

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## 结论

就这样！只需几行代码，您就掌握了使用 Aspose.Words for .NET 检测纯文本文档中带空格的编号的技巧。此功能在处理各种文本格式并确保列表在 Word 文档中准确显示时非常方便。这样，下次您遇到这些棘手的列表时，您就会知道该怎么做了。

## 常见问题解答

### 什么是 `DetectNumberingWithWhitespaces` 在 Aspose.Words for .NET 中？
`DetectNumberingWithWhitespaces` 是一个选项 `TxtLoadOptions` 即使编号和列表项文本之间存在空格，Aspose.Words 也能够识别列表。

### 我可以将此功能用于其他分隔符（例如项目符号和括号）吗？
是的，Aspose.Words 会自动检测带有常见分隔符（例如项目符号和括号）的列表。 `DetectNumberingWithWhitespaces` 特别有助于处理带有空格的列表。

### 如果我不使用会发生什么 `DetectNumberingWithWhitespaces`？
如果没有此选项，编号和文本之间带有空格的列表可能不会被识别为列表，并且项目可能会显示为普通段落。

### 其他 Aspose 产品中是否有此功能？
此特定功能是为 Aspose.Words for .NET 量身定制的，旨在处理 Word 文档。

### 如何获得 Aspose.Words for .NET 的临时许可证？
您可以从 [Aspose临时许可证](https://purchase.aspose.com/temporary-license/) 页。




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}