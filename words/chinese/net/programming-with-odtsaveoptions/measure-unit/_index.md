---
title: 测量单位
linktitle: 测量单位
second_title: Aspose.Words 文档处理 API
description: 了解如何配置 Aspose.Words for .NET 中的测量单位功能以在 ODT 转换期间保留文档格式。
weight: 10
url: /zh/net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 测量单位

## 介绍

您是否曾经将 Word 文档转换为不同的格式，但需要为布局指定特定的测量单位？无论您处理的是英寸、厘米还是点，确保文档在转换过程中保持完整性都至关重要。在本教程中，我们将介绍如何在 Aspose.Words for .NET 中配置测量单位功能。此强大功能可确保在转换为 ODT（开放文档文本）格式时，文档的格式完全按照您的需要保留。

## 先决条件

在深入研究代码之前，您需要先完成以下几件事：

1. Aspose.Words for .NET：请确保您已安装最新版本的 Aspose.Words for .NET。如果您还没有，可以从以下位置下载[这里](https://releases.aspose.com/words/net/).
2. 开发环境：像 Visual Studio 这样的 IDE，用于编写和执行 C# 代码。
3. C# 基础知识：了解 C# 的基础知识将帮助您跟随本教程。
4. Word 文档：准备好一个可以用于转换的示例 Word 文档。

## 导入命名空间

在开始编码之前，让我们确保已导入必要的命名空间。在代码文件顶部添加以下使用指令：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 步骤 1：设置文档目录

首先，您需要定义文档目录的路径。这是您的 Word 文档所在的位置，也是转换后的文件的保存位置。

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

代替`"YOUR DOCUMENTS DIRECTORY"`替换为目录的实际路径。这可确保您的代码知道在哪里可以找到您的 Word 文档。

## 第 2 步：加载 Word 文档

接下来，您需要加载要转换的 Word 文档。这是使用`Document`来自 Aspose.Words 的类。

```csharp
//加载 Word 文档
Document doc = new Document(dataDir + "Document.docx");
```

确保您的 Word 文档（名为“Document.docx”）存在于指定目录中。

## 步骤 3：配置计量单位

现在，让我们配置 ODT 转换的测量单位。这就是奇迹发生的地方。我们将设置`OdtSaveOptions`使用英寸作为计量单位。

```csharp
//使用“测量单位”功能配置备份选项
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

在此示例中，我们将测量单位设置为英寸。您还可以选择其他单位，例如`OdtSaveMeasureUnit.Centimeters`或者`OdtSaveMeasureUnit.Points`取决于您的要求。

## 步骤 4：将文档转换为 ODT

最后，我们将使用配置的`OdtSaveOptions`.

```csharp
//将文档转换为 ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

这行代码将转换后的文档保存在指定的目录中，并应用新的计量单位。

## 结论

就这样！按照以下步骤，您可以轻松配置 Aspose.Words for .NET 中的测量单位功能，以确保在转换过程中保留文档的布局。无论您使用的是英寸、厘米还是点，本教程都会向您展示如何轻松控制文档的格式。

## 常见问题解答

### 什么是 Aspose.Words for .NET？
Aspose.Words for .NET 是一个功能强大的库，用于以编程方式处理 Word 文档。它允许开发人员创建、修改、转换和处理 Word 文档，而无需 Microsoft Word。

### 除了英寸以外我可以使用其他测量单位吗？
是的，Aspose.Words for .NET 支持其他测量单位，例如厘米和点。您可以使用`OdtSaveMeasureUnit`枚举。

### Aspose.Words for .NET 有免费试用版吗？
是的，您可以从以下网址下载 Aspose.Words for .NET 的免费试用版[这里](https://releases.aspose.com/).

### 在哪里可以找到 Aspose.Words for .NET 的文档？
您可以在以下位置访问 Aspose.Words for .NET 的综合文档[此链接](https://reference.aspose.com/words/net/).

### 如何获得 Aspose.Words for .NET 的支持？
如需支持，您可以访问 Aspose.Words 论坛[此链接](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
