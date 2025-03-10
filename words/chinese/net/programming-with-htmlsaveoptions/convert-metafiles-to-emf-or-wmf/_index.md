---
title: 将图元文件转换为 Emf 或 Wmf
linktitle: 将图元文件转换为 Emf 或 Wmf
second_title: Aspose.Words 文档处理 API
description: 使用 Aspose.Words for .NET 将文档转换为 HTML 时，将元文件转换为 EMF 或 WMF 格式的分步指南。
weight: 10
url: /zh/net/programming-with-htmlsaveoptions/convert-metafiles-to-emf-or-wmf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将图元文件转换为 Emf 或 Wmf

## 介绍

欢迎再次深入探索 Aspose.Words for .NET 的世界。今天，我们将介绍一个巧妙的技巧：将 Word 文档中的 SVG 图像转换为 EMF 或 WMF 格式。这听起来可能有点技术性，但不用担心。在本教程结束时，您将成为这方面的专家。无论您是经验丰富的开发人员还是刚刚开始使用 Aspose.Words for .NET，本指南都将逐步引导您了解您需要了解的一切。

## 先决条件

在深入研究代码之前，让我们确保已完成所有设置。以下是您需要的内容：

1.  Aspose.Words for .NET Library：请确保您拥有最新版本。如果没有，您可以从以下网址下载[这里](https://releases.aspose.com/words/net/).
2. .NET Framework：确保您的机器上安装了 .NET Framework。
3. 开发环境：像 Visual Studio 这样的 IDE 将使您的生活更轻松。
4. C# 基础知识：您不需要成为专家，但基本的了解会有所帮助。

都准备好了吗？太棒了！让我们开始吧。

## 导入命名空间

首先，我们需要导入必要的命名空间。这很关键，因为它告诉我们的程序在哪里可以找到我们将要使用的类和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

这些命名空间涵盖了本教程所需的从基本系统功能到特定 Aspose.Words 功能的所有内容。

## 步骤 1：设置文档目录

首先，我们来定义文档目录的路径。转换图元文件后，Word 文档将保存在此目录中。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`与您想要保存文档的实际路径。

## 第 2 步：使用 SVG 创建 HTML 字符串

接下来，我们需要一个包含要转换的 SVG 图像的 HTML 字符串。这是一个简单的例子：

```csharp
string html = 
    @"<html>
        <svg xmlns='http://www.w3.org/2000/svg' 宽度='500' 高度='40' viewBox='0 0 500 40'>
            <text x='0' y='35' font-family='Verdana' font-size='35'>Hello world!</text>
        </svg>
    </html>";
```

此 HTML 片段包含一个基本的 SVG，即“Hello world!”。

## 步骤 3：使用 ConvertSvgToEmf 选项加载 HTML

现在，我们使用`HtmlLoadOptions`指定我们如何在 HTML 中处理 SVG 图像。设置`ConvertSvgToEmf`到`true`确保 SVG 图像转换为 EMF 格式。

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { ConvertSvgToEmf = true };
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

此代码片段创建一个新的`Document`通过使用指定的加载选项将 HTML 字符串加载到对象中。

## 步骤 4：为图元文件格式设置 HtmlSaveOptions

为了使用正确的图元文件格式保存文档，我们使用`HtmlSaveOptions`。在这里，我们设置`MetafileFormat`到`HtmlMetafileFormat.Png`，但你可以将其更改为`Emf`或者`Wmf`根据您的需要。

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { MetafileFormat = HtmlMetafileFormat.Png };
```

## 步骤 5：保存文档

最后，我们使用指定的保存选项保存文档。

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToPng.html", saveOptions);
```

这会将文档以按照定义转换的图元文件格式保存在指定的目录中。

## 结论

就这样！按照这些步骤，您已成功使用 Aspose.Words for .NET 将 Word 文档中的 SVG 图像转换为 EMF 或 WMF 格式。此方法非常方便，可确保兼容性并维护文档在不同平台上的视觉完整性。祝您编码愉快！

## 常见问题解答

### 我可以使用此方法转换其他图像格式吗？
是的，您可以通过相应地调整加载和保存选项来转换各种图像格式。

### 是否必须使用特定 .NET Framework 版本？
Aspose.Words for .NET 支持多个 .NET Framework 版本，但为了获得最佳兼容性和功能，最好使用最新版本。

### 将 SVG 转换为 EMF 或 WMF 有什么好处？
将 SVG 转换为 EMF 或 WMF 可确保矢量图形在可能不完全支持 SVG 的环境中得以正确保存和呈现。

### 我可以对多个文档自动执行这一过程吗？
当然可以！您可以循环遍历多个 HTML 文件，应用相同的过程来自动执行批处理转换。

### 在哪里可以找到有关 Aspose.Words for .NET 的更多资源和支持？
您可以找到全面的文档[这里](https://reference.aspose.com/words/net/)并获得 Aspose 社区的支持[这里](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
