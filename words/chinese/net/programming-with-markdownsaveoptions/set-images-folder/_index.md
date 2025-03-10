---
title: 设置图像文件夹
linktitle: 设置图像文件夹
second_title: Aspose.Words 文档处理 API
description: 使用 Aspose.Words for .NET 将 Word 文档转换为具有正确表格对齐的 Markdown。按照我们的详细指南可获得完美结果。
weight: 10
url: /zh/net/programming-with-markdownsaveoptions/set-images-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 设置图像文件夹

## 介绍

您是否曾想将 Word 文档导出为 Markdown 格式，同时确保表格和内容完美对齐？Aspose.Words for .NET 是您完成此任务的首选解决方案。在本文中，我们将引导您完成设置 Aspose.Words、准备文档以及以正确的表格内容对齐方式将其导出到 Markdown 的过程。我们将分解每个步骤，使其易于遵循和理解。所以，让我们深入研究并将您的 Word 文档转换为精美对齐的 Markdown 文件！

## 先决条件

在开始之前，请确保您已准备好以下物品：

-  Aspose.Words for .NET：您可以下载它[这里](https://releases.aspose.com/words/net/).
- 有效的许可证：获得免费试用[这里](https://releases.aspose.com/)或临时执照[这里](https://purchase.aspose.com/temporary-license/).
- Visual Studio：或任何其他支持.NET 开发的 IDE。
- C# 基础知识：了解 C# 编程语言。

## 导入命名空间

首先，您需要在 C# 项目中导入必要的命名空间。这些命名空间将允许您访问 Aspose.Words 功能。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;
```

## 步骤 1：设置你的项目

首先，在 IDE 中设置 .NET 项目。创建一个新的控制台应用程序并添加对 Aspose.Words for .NET 的引用。

### 1.1 创建新项目

打开 Visual Studio 并创建一个新的控制台应用程序项目。将其命名为“MarkdownExporter”或类似名称。

### 1.2 添加 Aspose.Words 引用

要将 Aspose.Words 添加到您的项目中，您可以从[Aspose 网站](https://releases.aspose.com/words/net/)并手动添加，或者使用 NuGet 包管理器：

```bash
Install-Package Aspose.Words
```

## 步骤 2：编写导出为 Markdown 的代码

现在，让我们编写代码来读取 Word 文档并将其保存为具有适当表格对齐的 Markdown 文件。

### 2.1 定义文档路径

设置您的 Word 文档的路径和您想要保存图像的文件夹。

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

### 2.2 加载文档

使用 Aspose.Words 加载您的 Word 文档。

```csharp
Document doc = new Document(dataDir + "Image bullet points.docx");
```

### 2.3 配置 Markdown 保存选项

配置`MarkdownSaveOptions`指定图像的存储位置。

```csharp
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    ImagesFolder = dataDir + "Images"
};
```

### 2.4 将文档保存为 Markdown

使用`MemoryStream`将文档保存为 Markdown 格式。

```csharp
using (MemoryStream stream = new MemoryStream())
{
    doc.Save(stream, saveOptions);
}
```

## 结论

按照以下步骤使用 Aspose.Words for .NET 将 Word 文档导出为具有表格内容对齐的 Markdown 非常简单。只需几行代码，您就可以自动执行转换过程并确保内容格式正确。现在，您可以轻松地以 Markdown 格式共享文档，并且知道它们看起来很棒并且保持其结构。

## 常见问题解答

### 我可以将 Aspose.Words for .NET 与其他编程语言一起使用吗？

是的，Aspose.Words for .NET 可以与任何与 .NET 兼容的语言一起使用，例如 VB.NET、F# 等。

### 如何获取 Aspose.Words 的临时许可证？

您可以获得临时驾照[这里](https://purchase.aspose.com/temporary-license/).

### 我可以将哪些类型的文档转换为 Markdown？

您可以转换各种 Word 文档，包括 .doc、.docx、.rtf 等。

### Aspose.Words 试用版有什么限制吗？

试用版有一些限制，例如输出文件中有水印。您可以免费试用[这里](https://releases.aspose.com/).

### 在哪里可以找到 Aspose.Words 的更多示例和文档？

您可以在[Aspose 网站](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
