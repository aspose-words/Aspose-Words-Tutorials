---
title: 使用“跳过嵌入的 Arial 和 Times Roman 字体”优化 PDF 大小
linktitle: 使用“跳过嵌入的 Arial 和 Times Roman 字体”优化 PDF 大小
second_title: Aspose.Words 文档处理 API
description: 使用 Aspose.Words for .NET 跳过嵌入的 Arial 和 Times Roman 字体来优化 PDF 大小。按照此分步指南简化您的 PDF 文件。
weight: 10
url: /zh/net/programming-with-pdfsaveoptions/skip-embedded-arial-and-times-roman-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用“跳过嵌入的 Arial 和 Times Roman 字体”优化 PDF 大小

## 介绍

您是否遇到过 PDF 文件过大的情况？这就像打包行李准备度假，却发现行李箱已经快要塞满。您知道自己需要减轻一些负担，但要放弃什么呢？处理 PDF 文件时，尤其是从 Word 文档转换而来的 PDF 文件时，嵌入的字体会使文件大小膨胀。幸运的是，Aspose.Words for .NET 提供了一个精简的解决方案，让您的 PDF 保持精简。在本教程中，我们将深入探讨如何通过跳过嵌入的 Arial 和 Times Roman 字体来优化 PDF 大小。让我们开始吧！

## 先决条件

在我们讨论细节之前，您需要准备一些东西：
-  Aspose.Words for .NET：请确保您已安装此强大的库。如果没有，您可以从以下位置下载[这里](https://releases.aspose.com/words/net/).
- 对 C# 的基本了解：这将帮助您理解代码片段。
- Word 文档：我们将使用示例文档来演示该过程。 

## 导入命名空间

首先，确保您已导入必要的命名空间。这为访问 Aspose.Words 功能奠定了基础。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

好吧，让我们一步一步地分解这个过程。

## 步骤 1：设置您的环境

首先，您需要设置开发环境。打开您最喜欢的 C# IDE（例如 Visual Studio）并创建一个新项目。

## 第 2 步：加载 Word 文档

下一步是加载要转换为 PDF 的 Word 文档。确保您的文档位于正确的目录中。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

在此代码片段中，替换`"YOUR DOCUMENT DIRECTORY"`使用您的文档目录的路径。

## 步骤 3：配置 PDF 保存选项

现在，我们需要配置 PDF 保存选项来控制字体的嵌入方式。默认情况下，所有字体都是嵌入的，这会增加文件大小。我们将更改此设置。

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};
```

## 步骤 4：将文档保存为 PDF

最后，使用指定的保存选项将文档保存为 PDF。这就是奇迹发生的地方。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SkipEmbeddedArialAndTimesRomanFonts.pdf", saveOptions);
```

此命令将您的文档作为名为“OptimizedPDF.pdf”的PDF保存在指定目录中。

## 结论

就这样！您刚刚学会了如何使用 Aspose.Words for .NET 跳过嵌入 Arial 和 Times Roman 字体来优化 PDF 文件大小。这个简单的调整可以显著减少文件大小，使它们更易于共享和存储。这就像去健身房锻炼您的 PDF，减掉不必要的体重，同时保持所有基本功能不变。

## 常见问题解答

### 为什么我应该跳过嵌入 Arial 和 Times Roman 字体？
跳过这些常用字体可以减小 PDF 文件大小，因为大多数系统已经安装了这些字体。

### 这会影响我的 PDF 的外观吗？
不会。由于 Arial 和 Times Roman 是标准字体，因此在不同系统上的外观保持一致。

### 我也可以跳过嵌入其他字体吗？
是的，您可以配置保存选项以跳过嵌入其他字体（如果需要）。

### Aspose.Words for .NET 免费吗？
 Aspose.Words for .NET 提供免费试用版，您可以下载[这里](https://releases.aspose.com/)，但要获得完整访问权限，您需要购买许可证[这里](https://purchase.aspose.com/buy).

### 在哪里可以找到有关 Aspose.Words for .NET 的更多教程？
您可以找到全面的文档和教程[这里](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
