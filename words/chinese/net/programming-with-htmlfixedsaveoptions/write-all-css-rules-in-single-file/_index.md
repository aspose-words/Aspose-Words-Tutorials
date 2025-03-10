---
title: 在单个文件中写入所有 CSS 规则
linktitle: 在单个文件中写入所有 CSS 规则
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 将 Word 文档转换为 HTML，并在单个文件中包含所有 CSS 规则，以获得更清晰的代码和更易于维护。
weight: 10
url: /zh/net/programming-with-htmlfixedsaveoptions/write-all-css-rules-in-single-file/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在单个文件中写入所有 CSS 规则

## 介绍

在将 Word 文档转换为 HTML 时，您是否发现自己被散落在各处的 CSS 规则所困扰？别担心！今天，我们将深入研究 Aspose.Words for .NET 的一项简洁功能，该功能可让您在一个文件中编写所有 CSS 规则。这不仅可以整理您的代码，还可以让您的生活变得轻松很多。系好安全带，让我们开始这段更干净、更高效的 HTML 输出之旅吧！

## 先决条件

在我们深入讨论细节之前，让我们先做好准备。以下是您需要做的准备：

1.  Aspose.Words for .NET：确保您拥有 Aspose.Words for .NET 库。如果您还没有，您可以[点击下载](https://releases.aspose.com/words/net/).
2. .NET 开发环境：您需要在机器上安装 .NET 开发环境。Visual Studio 是比较受欢迎的选择。
3. C# 基础知识：对 C# 编程的基本了解将会有所帮助。
4. Word 文档：准备好要转换的 Word 文档 (.docx)。

## 导入命名空间

首先，让我们在 C# 项目中导入必要的命名空间。这将使我们能够轻松访问 Aspose.Words 功能。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

好吧，让我们将流程分解为易于遵循的步骤。每个步骤将指导您完成流程的特定部分，以确保一切顺利进行。

## 步骤 1：设置文档目录

首先，我们需要定义文档目录的路径。这是存储 Word 文档的地方，也是保存转换后的 HTML 的地方。

```csharp
//访问文档目录的路径
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## 第 2 步：加载 Word 文档

接下来，我们加载要转换为 HTML 的 Word 文档。这是使用`Document`Aspose.Words 库中的类。

```csharp
//加载 Word 文档
Document doc = new Document(dataDir + "Document.docx");
```

## 步骤 3：配置 HTML 保存选项

现在，我们需要配置 HTML 保存选项。具体来说，我们希望启用将所有 CSS 规则写入单个文件的功能。这可以通过设置`SaveFontFaceCssSeparately`财产`false`.

```csharp
//使用“将所有 CSS 规则写入一个文件中”功能配置备份选项
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions 
{ 
    SaveFontFaceCssSeparately = false 
};
```

## 步骤 4：将文档转换为固定 HTML

最后，我们使用配置的保存选项将文档保存为 HTML 文件。此步骤可确保所有 CSS 规则都写入单个文件中。

```csharp
//将文档转换为固定 HTML
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.WriteAllCssRulesInSingleFile.html", saveOptions);
```

## 结论

就这样！只需几行代码，您就成功地将 Word 文档转换为 HTML，所有 CSS 规则都整齐地组织在一个文件中。这种方法不仅简化了 CSS 管理，还增强了 HTML 文档的可维护性。因此，下次您转换 Word 文档时，您就会知道如何保持整洁！

## 常见问题解答

### 为什么我应该对 HTML 输出使用单个 CSS 文件？
使用单个 CSS 文件可简化样式的管理和维护。它可让您的 HTML 更简洁、更高效。

### 如果需要，我可以分离字体 CSS 规则吗？
是的，通过设置`SaveFontFaceCssSeparately`到`true`，您可以将字体 CSS 规则分离到不同的文件中。

### Aspose.Words for .NET 可以免费使用吗？
 Aspose.Words 提供免费试用，您可以[点击此处下载](https://releases.aspose.com/)。如需继续使用，请考虑购买许可证[这里](https://purchase.aspose.com/buy).

### Aspose.Words for .NET 还可以转换为哪些其他格式？
Aspose.Words for .NET 支持各种格式，包括 PDF、TXT 和 JPEG 和 PNG 等图像格式。

### 在哪里可以找到有关 Aspose.Words for .NET 的更多资源？
查看[文档](https://reference.aspose.com/words/net/)获得全面的指南和 API 参考。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
