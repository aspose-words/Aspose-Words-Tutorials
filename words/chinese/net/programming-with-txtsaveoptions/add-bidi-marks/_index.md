---
title: 在 Word 文档中添加双向标记
linktitle: 在 Word 文档中添加双向标记
second_title: Aspose.Words 文档处理 API
description: 通过本指南了解如何使用 Aspose.Words for .NET 在 Word 文档中添加双向 (Bidi) 标记。确保多语言内容的文本方向正确。
weight: 10
url: /zh/net/programming-with-txtsaveoptions/add-bidi-marks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文档中添加双向标记

## 介绍

在文档处理领域，双向 (Bidi) 文本通常有点难以管理。在处理具有不同文本方向的语言（例如阿拉伯语或希伯来语）时尤其如此。幸运的是，Aspose.Words for .NET 可以轻松处理此类情况。在本教程中，我们将介绍如何使用 Aspose.Words for .NET 向 Word 文档添加 Bidi 标记。

## 先决条件

在深入研究代码之前，请确保您具有以下内容：

1. Aspose.Words for .NET：您需要安装 Aspose.Words for .NET。您可以从[Aspose 下载页面](https://releases.aspose.com/words/net/).
2. .NET Framework 或 .NET Core：确保您已设置兼容的 .NET 环境来运行示例。
3. C#基础知识：熟悉C#编程语言和.NET中的基本操作。

## 导入命名空间

首先，您需要导入必要的命名空间。以下是如何将它们包含在项目中：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

让我们将 Word 文档中添加 Bidi 标记的过程分解为清晰的步骤。每个步骤都会引导您完成代码及其用途。

## 步骤 1：设置文档

首先创建一个新的实例`Document`类和一个`DocumentBuilder`向文档添加内容。

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENTS DIRECTORY";

//创建文档并添加内容
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

在此步骤中，您将初始化一个新的 Word 文档并设置`DocumentBuilder`以方便插入内容。

## 步骤 2：向文档添加内容

接下来，在文档中添加一些文本。在这里，我们将添加不同语言的文本来说明双向文本的处理。

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

在这里，我们首先添加一个标准英语短语。然后，我们为后续的文本启用双向文本格式，该文本用希伯来语和阿拉伯语书写。这演示了如何合并双向文本。

## 步骤 3：配置双向标记的保存选项

为了确保双向标记正确保存在文档中，您需要配置`TxtSaveOptions`并启用`AddBidiMarks`选项。

```csharp
//添加 Bidi 标记
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

在此步骤中，我们创建一个实例`TxtSaveOptions`并设置`AddBidiMarks`财产`true`这可确保将文档保存为文本文件时包含双向标记。

## 结论

在处理包含具有不同文本方向的语言的多语言内容时，向 Word 文档添加 Bidi 标记可能是至关重要的一步。使用 Aspose.Words for .NET，此过程简单而高效。通过遵循上述步骤，您可以确保您的文档正确表示 Bidi 文本，从而提高可读性和准确性。

## 常见问题解答

### 什么是 Bidi 商标？为什么 Bidi 商标如此重要？
双向标记是用于控制文档中文本方向的特殊字符。它们对于正确显示从右向左阅读的语言（如阿拉伯语和希伯来语）至关重要。

### 我可以使用 Aspose.Words for .NET 处理其他类型的文本方向问题吗？
是的，Aspose.Words for .NET 为各种文本方向和格式需求提供全面支持，包括从右到左和从左到右的语言。

### 是否可以将双向格式仅应用于文档的特定部分？
是的，您可以根据需要将双向格式应用于文档的特定段落或部分。

### 我可以使用哪些格式保存带有双向标记的文档？
在提供的示例中，文档被保存为文本文件。但是，Aspose.Words 还支持以各种格式保存文档，同时保留 Bidi 标记。

### 在哪里可以找到有关 Aspose.Words for .NET 的更多信息？
您可以通过以下方式了解有关 Aspose.Words for .NET 的更多信息[Aspose 文档](https://reference.aspose.com/words/net/)并访问[支持论坛](https://forum.aspose.com/c/words/8)以获得更多帮助。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
