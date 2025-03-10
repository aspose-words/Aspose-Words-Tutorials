---
title: 导出 Mhtml 资源的 Cid Url
linktitle: 导出 Mhtml 资源的 Cid Url
second_title: Aspose.Words 文档处理 API
description: 在本分步教程中学习如何使用 Aspose.Words for .NET 导出 MHTML 资源的 Cid URL。适合所有级别的开发人员。
weight: 10
url: /zh/net/programming-with-htmlsaveoptions/export-cid-urls-for-mhtml-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 导出 Mhtml 资源的 Cid Url

## 介绍

您准备好掌握使用 Aspose.Words for .NET 导出 MHTML 资源的 Cid URL 的技巧了吗？无论您是经验丰富的开发人员还是刚刚入门，本综合指南都将引导您完成每一步。在本文结束时，您将清楚地了解如何有效地处理 Word 文档中的 MHTML 资源。让我们开始吧！

## 先决条件

在开始之前，请确保您已准备好所需的一切：

-  Aspose.Words for .NET：请确保您已安装最新版本的 Aspose.Words for .NET。如果没有，您可以从以下网址下载[这里](https://releases.aspose.com/words/net/).
- 开发环境：开发环境，例如 Visual Studio。
- C# 基础知识：虽然我会指导您完成每个步骤，但对 C# 的基本了解将会很有益。

## 导入命名空间

首先，让我们导入必要的命名空间。此步骤为我们的教程奠定了基础：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

现在，让我们将流程分解为简单易行的步骤。每个步骤都会有详细的说明，以确保您能轻松完成。

## 步骤 1：设置项目

### 步骤 1.1：创建新项目
打开 Visual Studio 并创建一个新的 C# 项目。选择“控制台应用程序”模板以简化操作。

### 步骤1.2：添加Aspose.Words for .NET引用
要使用 Aspose.Words for .NET，您需要添加对 Aspose.Words 库的引用。您可以通过 NuGet 包管理器执行此操作：

1. 在解决方案资源管理器中右键单击您的项目。
2. 选择“管理 NuGet 包”。
3. 搜索“Aspose.Words”并安装。

## 第 2 步：加载 Word 文档

### 步骤2.1：指定文档目录
定义文档目录的路径。这是您的 Word 文档所在的位置。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`与您的目录的实际路径一致。

### 步骤 2.2：加载文档
将您的 Word 文档加载到项目中。

```csharp
Document doc = new Document(dataDir + "Content-ID.docx");
```

## 步骤 3：配置 HTML 保存选项

创建一个实例`HtmlSaveOptions`自定义如何将文档保存为 MHTML。

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Mhtml)
{
    PrettyFormat = true,
    ExportCidUrlsForMhtmlResources = true
};
```

- `SaveFormat.Mhtml`指定输出格式为 MHTML。
- `PrettyFormat = true`确保输出格式整齐。
- `ExportCidUrlsForMhtmlResources = true`启用 MHTML 资源的 Cid URL 导出。

### 步骤 4：将文档另存为 MHTML

步骤 4.1：保存文档
使用配置的选项将您的文档保存为 MHTML 文件。

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
```

## 结论

恭喜！您已成功使用 Aspose.Words for .NET 导出 MHTML 资源的 Cid URL。本教程将指导您设置项目、加载 Word 文档、配置 HTML 保存选项以及将文档保存为 MHTML。现在，您可以将这些步骤应用到您自己的项目中并增强您的文档管理任务。

## 常见问题解答

### 导出 MHTML 资源的 Cid URL 有什么用处？
导出 MHTML 资源的 Cid URL 可确保正确引用 MHTML 文件中嵌入的资源，从而提高文档的可移植性和完整性。

### 我可以进一步自定义输出格式吗？
是的，Aspose.Words for .NET 提供了广泛的自定义选项来保存文档。请参阅[文档](https://reference.aspose.com/words/net/)了解更多详情。

### 我需要许可证才能使用 Aspose.Words for .NET 吗？
是的，您需要许可证才能使用 Aspose.Words for .NET。您可以获得免费试用版[这里](https://releases.aspose.com/)或购买许可证[这里](https://purchase.aspose.com/buy).

### 我可以对多个文档自动执行这一过程吗？
当然！您可以创建一个脚本来自动执行多个文档的处理，利用 Aspose.Words for .NET 的强大功能高效地处理批处理操作。

### 如果我遇到问题，可以在哪里获得支持？
如果您需要支持，请访问 Aspose 支持论坛[这里](https://forum.aspose.com/c/words/8)寻求社区和 Aspose 开发人员的帮助。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
