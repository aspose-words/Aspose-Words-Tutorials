---
title: 设置字体文件夹优先级
linktitle: 设置字体文件夹优先级
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文档中设置优先字体文件夹。我们的指南可确保您的文档每次都能完美呈现。
weight: 10
url: /zh/net/working-with-fonts/set-fonts-folders-with-priority/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 设置字体文件夹优先级

## 介绍

在文档处理领域，设置自定义字体文件夹可以大大提高文档的呈现效果，无论在何处查看。今天，我们将深入介绍如何使用 Aspose.Words for .NET 在 Word 文档中优先设置字体文件夹。本综合指南将引导您完成每个步骤，使流程尽可能顺利。

## 先决条件

在我们开始之前，让我们确保我们已经准备好了所有需要的东西。以下是一份快速检查清单：

-  Aspose.Words for .NET：您需要安装此库。如果您还没有安装，您可以[点击下载](https://releases.aspose.com/words/net/).
- 开发环境：确保您有一个可运行的 .NET 开发环境，例如 Visual Studio。
- 文档目录：确保您的文档有一个目录。在我们的示例中，我们将使用`"YOUR DOCUMENT DIRECTORY"`作为此路径的占位符。

## 导入命名空间

首先，我们需要导入必要的命名空间。这些命名空间对于访问 Aspose.Words 提供的类和方法至关重要。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

现在，让我们分解优先设置字体文件夹的每个步骤。

## 步骤 1：设置字体源

首先，您需要定义字体源。这是您告诉 Aspose.Words 在哪里查找字体的地方。您可以指定多个字体文件夹，甚至可以设置它们的优先级。

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";

FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
    new SystemFontSource(), 
    new FolderFontSource("C:\\MyFonts\\", true, 1)
});
```

在此示例中，我们设置了两个字体源：
- SystemFontSource：这是默认字体源，包含系统上安装的所有字体。
-  FolderFontSource：这是一个自定义字体文件夹，位于`C:\\MyFonts\\`。 这`true`参数指定应递归扫描此文件夹，并且`1`设置其优先级。

## 步骤 2：加载文档

接下来，加载您要处理的文档。确保文档位于您指定的目录中。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

这行代码加载一个名为`Rendering.docx`来自您的文档目录。

## 步骤 3：使用新字体设置保存文档

最后，保存您的文档。当您保存文档时，Aspose.Words 将使用您指定的字体设置。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

这会将文档保存为 PDF 格式，保存在文档目录中，名称为`WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## 结论

就这样！您已成功使用 Aspose.Words for .NET 设置了具有优先级的字体文件夹。通过指定自定义字体文件夹和优先级，您可以确保您的文档无论在何处查看都能一致地呈现。这在默认情况下未安装特定字体的环境中尤其有用。

## 常见问题解答

### 为什么我需要设置自定义字体文件夹？
设置自定义字体文件夹可确保您的文档正确呈现，即使它们使用在查看的系统上未安装的字体。

### 我可以设置多个自定义字体文件夹吗？
是的，您可以指定多个字体文件夹。Aspose.Words 允许您设置每个文件夹的优先级，确保首先找到最重要的字体。

### 如果所有指定的来源都缺少某种字体，会发生什么情况？
如果所有指定的源都缺少某种字体，Aspose.Words 将使用后备字体来确保文档仍然可读。

### 我可以更改系统字体的优先级吗？
默认情况下始终包含系统字体，但您可以相对于自定义字体文件夹设置它们优先级。

### 是否可以对自定义字体文件夹使用网络路径？
是的，您可以将网络路径指定为自定义字体文件夹，从而允许您将字体资源集中在网络位置上。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
