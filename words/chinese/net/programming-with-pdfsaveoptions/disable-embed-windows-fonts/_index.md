---
title: 通过禁用嵌入字体来减小 PDF 大小
linktitle: 通过禁用嵌入字体来减小 PDF 大小
second_title: Aspose.Words 文档处理 API
description: 使用 Aspose.Words for .NET 禁用嵌入字体，从而减小 PDF 大小。按照我们的分步指南优化您的文档，以实现高效存储和共享。
weight: 10
url: /zh/net/programming-with-pdfsaveoptions/disable-embed-windows-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 通过禁用嵌入字体来减小 PDF 大小

## 介绍

减小 PDF 文件的大小对于高效存储和快速共享至关重要。一种有效的方法是禁用嵌入字体，尤其是在大多数系统上已经提供标准字体的情况下。在本教程中，我们将探讨如何使用 Aspose.Words for .NET 禁用嵌入字体来减小 PDF 大小。我们将逐步介绍每个步骤，以确保您可以在自己的项目中轻松实现这一点。

## 先决条件

在深入研究代码之前，请确保您已具备以下条件：

-  Aspose.Words for .NET：如果你还没有，请从[下载链接](https://releases.aspose.com/words/net/).
- .NET 开发环境：Visual Studio 是一个流行的选择。
- 示例 Word 文档：准备好要转换为 PDF 的 DOCX 文件。

## 导入命名空间

首先，确保已将必要的命名空间导入到项目中。这样您就可以访问我们任务所需的类和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

让我们将流程分解为简单、易于管理的步骤。每个步骤都会指导您完成任务，确保您了解每个步骤发生的情况。

## 步骤 1：初始化文档

首先，我们需要加载要转换为 PDF 的 Word 文档。这就是您的旅程的开始。

```csharp
//文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

这里，`dataDir`是文档所在目录的占位符。替换`"YOUR DOCUMENT DIRECTORY"`与实际路径。

## 步骤 2：配置 PDF 保存选项

接下来，我们将设置 PDF 保存选项。在这里我们指定不想嵌入标准 Windows 字体。

```csharp
//输出的 PDF 将被保存而不嵌入标准 Windows 字体。
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedNone
};
```

通过设置`FontEmbeddingMode`到`EmbedNone`，我们指示 Aspose.Words 不要在 PDF 中包含这些字体，以减小文件大小。

## 步骤 3：将文档保存为 PDF

最后，我们使用配置的保存选项将文档保存为 PDF。这是您的 DOCX 转换为紧凑 PDF 的关键时刻。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DisableEmbedWindowsFonts.pdf", saveOptions);
```

代替`"YOUR DOCUMENT DIRECTORY"`再次使用您的实际目录路径。输出 PDF 现在将保存在指定的目录中，不包含嵌入的标准字体。

## 结论

通过遵循这些步骤，您可以显著减小 PDF 文件的大小。禁用嵌入字体是一种简单而有效的方法，可以让您的文档更轻便、更易于共享。Aspose.Words for .NET 使此过程变得无缝，确保您可以以最小的努力优化文件。

## 常见问题解答

### 为什么我应该禁用 PDF 中的嵌入字体？
禁用嵌入字体可以显著减少 PDF 的文件大小，使其更高效地存储和更快地共享。

### 如果没有嵌入字体，PDF 还能正确显示吗？
是的，只要字体是标准的并且在查看 PDF 的系统上可用，它就会正确显示。

### 我可以选择性地在 PDF 中嵌入某些字体吗？
是的，Aspose.Words for .NET 允许您自定义嵌入的字体，从而灵活地减少文件大小。

### 我是否需要 Aspose.Words for .NET 来禁用 PDF 中的嵌入字体？
是的，Aspose.Words for .NET 提供了在 PDF 中配置字体嵌入选项所需的功能。

### 如果我遇到问题，如何获得支持？
您可以访问[支持论坛](https://forum.aspose.com/c/words/8)为您遇到的任何问题提供帮助。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
