---
title: 通过不嵌入核心字体来减小 PDF 文件大小
linktitle: 通过不嵌入核心字体来减小 PDF 文件大小
second_title: Aspose.Words 文档处理 API
description: 了解如何通过使用 Aspose.Words for .NET 不嵌入核心字体来减小 PDF 文件大小。按照我们的分步指南优化您的 PDF。
weight: 10
url: /zh/net/programming-with-pdfsaveoptions/avoid-embedding-core-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 通过不嵌入核心字体来减小 PDF 文件大小

## 介绍

您是否曾经感到困惑，想知道为什么您的 PDF 文件这么大？好吧，您并不孤单。一个常见的罪魁祸首是嵌入 Arial 和 Times New Roman 等核心字体。幸运的是，Aspose.Words for .NET 有一个巧妙的方法来解决这个问题。在本教程中，我将向您展示如何通过避免嵌入这些核心字体来减小 PDF 文件大小。让我们开始吧！

## 先决条件

在我们踏上这段激动人心的旅程之前，让我们确保您已准备好一切所需。以下是一份快速检查清单：

-  Aspose.Words for .NET：确保已安装 Aspose.Words for .NET。如果尚未安装，可以下载[这里](https://releases.aspose.com/words/net/).
- 开发环境：您需要一个像 Visual Studio 这样的开发环境。
- Word 文档：本教程中我们将使用 Word 文档（例如“Rendering.docx”）。
- 基本 C# 知识：对 C# 的基本了解将帮助您跟上进度。

好了，现在一切准备就绪，让我们开始讨论细节！

## 导入命名空间

首先，让我们导入必要的命名空间。此步骤确保我们可以访问所需的所有 Aspose.Words 功能。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 步骤 1：初始化文档目录

在开始操作文档之前，我们需要指定存储文档的目录。这对于访问文件至关重要。

```csharp
//文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`使用您的 Word 文档所在的实际路径。

## 第 2 步：加载 Word 文档

接下来，我们需要加载要转换为 PDF 的 Word 文档。在此示例中，我们使用名为“Rendering.docx”的文档。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

这行代码将文档加载到内存中，准备进行进一步处理。

## 步骤 3：配置 PDF 保存选项

现在到了神奇的部分！我们将配置 PDF 保存选项以避免嵌入核心字体。这是有助于减小 PDF 文件大小的关键步骤。

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    UseCoreFonts = true
};
```

环境`UseCoreFonts`到`true`确保核心字体（如 Arial 和 Times New Roman）不会嵌入到 PDF 中，从而显著减小文件大小。

## 步骤 4：将文档保存为 PDF

最后，我们使用配置的保存选项将 Word 文档保存为 PDF。此步骤生成的 PDF 文件不包含核心字体。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.AvoidEmbeddingCoreFonts.pdf", saveOptions);
```

就这样！您的 PDF 文件现在已保存在指定的目录中，并且没有那些笨重的核心字体。

## 结论

使用 Aspose.Words for .NET 可以轻松减小 PDF 文件大小。通过避免嵌入核心字体，您可以显著减小文件大小，从而更轻松地共享和存储文档。我希望本教程对您有所帮助，并让您清楚地了解该过程。请记住，小调整可以带来大不同！

## 常见问题解答

### 为什么应该避免在 PDF 中嵌入核心字体？
避免嵌入核心字体可减小文件大小，使其更易于共享和存储。

### 即使没有嵌入核心字体，我还能正确查看 PDF 吗？
是的，大多数系统上通常都提供 Arial 和 Times New Roman 等核心字体。

### 如果我需要嵌入自定义字体怎么办？
您可以自定义`PdfSaveOptions`根据需要嵌入特定字体。

### Aspose.Words for .NET 可以免费使用吗？
 Aspose.Words for .NET 需要许可证。您可以免费试用[这里](https://releases.aspose.com/).

### 在哪里可以找到有关 Aspose.Words for .NET 的更多文档？
您可以找到详细的文档[这里](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
