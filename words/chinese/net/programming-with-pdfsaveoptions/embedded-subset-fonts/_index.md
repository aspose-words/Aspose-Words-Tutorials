---
title: 在 PDF 文档中嵌入子集字体
linktitle: 在 PDF 文档中嵌入子集字体
second_title: Aspose.Words 文档处理 API
description: 使用 Aspose.Words for .NET 仅嵌入必要的字体子集，从而减小 PDF 文件大小。按照我们的分步指南，有效优化您的 PDF。
weight: 10
url: /zh/net/programming-with-pdfsaveoptions/embedded-subset-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 PDF 文档中嵌入子集字体

## 介绍

您是否注意到，即使包含相似的内容，某些 PDF 文件也比其他文件大得多？罪魁祸首往往在于字体。在 PDF 中嵌入字体可确保它在任何设备上看起来都一样，但也会使文件大小膨胀。幸运的是，Aspose.Words for .NET 提供了一个方便的功能，可以仅嵌入必要的字体子集，从而使您的 PDF 保持精简和高效。本教程将逐步指导您完成该过程。

## 先决条件

在开始之前，请确保您已准备好以下内容：

-  Aspose.Words for .NET：您可以下载它[这里](https://releases.aspose.com/words/net/).
- .NET 环境：确保您有一个可运行的 .NET 开发环境。
- C# 基础知识：熟悉 C# 编程将帮助您跟上。

## 导入命名空间

要使用 Aspose.Words for .NET，您需要在项目中导入必要的命名空间。将这些添加到 C# 文件的顶部：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 步骤 1：加载文档

首先，我们需要加载要转换为 PDF 的 Word 文档。这是使用`Document`Aspose.Words 提供的类。

```csharp
//文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

此代码片段加载位于`dataDir` 确保更换`"YOUR DOCUMENT DIRECTORY"`使用您的文档的实际路径。

## 步骤 2：配置 PDF 保存选项

接下来，我们配置`PdfSaveOptions`以确保只嵌入必要的字体子集。通过设置`EmbedFullFonts`到`false`，我们告诉 Aspose.Words 仅嵌入文档中使用的字形。

```csharp
//输出 PDF 将包含文档中字体的子集。
// PDF 字体仅包含文档中使用的字形。
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

这个小但关键的步骤有助于显著减少 PDF 文件的大小。

## 步骤 3：将文档保存为 PDF

最后，我们使用`Save`方法，应用配置的`PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

此代码将生成一个名为`WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf`在指定的目录中，仅嵌入必要的字体子集。

## 结论

就这样！通过遵循这些简单的步骤，您可以使用 Aspose.Words for .NET 仅嵌入必要的字体子集，从而有效地减小 PDF 文件的大小。这不仅可以节省存储空间，还可以确保更快的加载时间和更好的性能，尤其是对于具有大量字体的文档。

## 常见问题解答

### 为什么我应该在 PDF 中嵌入字体子集？
仅嵌入必要的字体子集可以显著减少 PDF 文件大小，而不会影响文档的外观和可读性。

### 如果需要，我可以恢复嵌入完整字体吗？
是的，你可以。只需设置`EmbedFullFonts`财产`true`在`PdfSaveOptions`.

### Aspose.Words for .NET 是否支持其他 PDF 优化功能？
当然！Aspose.Words for .NET 提供了一系列用于优化 PDF 的选项，包括图像压缩和删除未使用的对象。

### 使用 Aspose.Words for .NET 可以嵌入哪些类型的字体子集？
Aspose.Words for .NET 支持文档中使用的所有 TrueType 字体的子集嵌入。

### 我如何验证我的 PDF 中嵌入了哪些字体？
您可以在 Adobe Acrobat Reader 中打开 PDF，并检查“字体”选项卡下的属性以查看嵌入的字体。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
