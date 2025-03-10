---
title: 保留旧版控制字符
linktitle: 保留旧版控制字符
second_title: Aspose.Words 文档处理 API
description: 通过本分步指南了解如何使用 Aspose.Words for .NET 在 Word 文档中保留旧式控制字符。
weight: 10
url: /zh/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 保留旧版控制字符

## 介绍

您是否曾对 Word 文档中那些奇怪的、看不见的控制字符感到困惑？它们就像微小的隐藏小精灵，会弄乱格式和功能。幸运的是，Aspose.Words for .NET 提供了一个方便的功能，可以在保存文档时保持这些旧控制字符的完整性。在本教程中，我们将深入探讨如何使用 Aspose.Words for .NET 管理这些控制字符。我们将逐步分解，确保您掌握每个细节。准备好开始了吗？让我们开始吧！

## 先决条件

在开始之前，请确保您已准备好以下内容：

1.  Aspose.Words for .NET：下载并安装[这里](https://releases.aspose.com/words/net/).
2. 有效的 Aspose 许可证：您可以获取临时许可证[这里](https://purchase.aspose.com/temporary-license/).
3. 开发环境：Visual Studio 或任何其他支持.NET 的 IDE。
4. C# 基础知识：熟悉 C# 编程语言将会有所帮助。

## 导入命名空间

在编写代码之前，您需要导入必要的命名空间。将以下几行添加到 C# 文件的顶部：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 步骤 1：设置项目

首先，您需要在 Visual Studio（或您喜欢的 IDE）中设置您的项目。 

1. 创建一个新的 C# 项目：打开 Visual Studio 并创建一个新的 C# 控制台应用程序项目。
2. 安装 Aspose.Words for .NET：使用 NuGet 包管理器安装 Aspose.Words for .NET。在解决方案资源管理器中右键单击您的项目，选择“管理 NuGet 包”，搜索“Aspose.Words”，然后安装它。

## 步骤 2：加载文档

接下来，您将加载包含旧版控制字符的 Word 文档。

1. 指定文档路径：设置文档目录的路径。
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2. 加载文档：使用`Document`类来加载你的文档。

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## 步骤 3：配置保存选项

现在，让我们配置保存选项以保持传统的控制字符不变。

1. 创建保存选项：初始化一个实例`OoxmlSaveOptions`并设置`KeepLegacyControlChars`财产`true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## 步骤 4：保存文档

最后，使用配置的保存选项保存文档。

1. 保存文档：使用`Save`方法`Document`类使用指定的保存选项保存文档。

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## 结论

就这样！按照这些步骤，您可以确保在 Aspose.Words for .NET 中处理 Word 文档时保留旧版控制字符。此功能可以拯救您的生命，尤其是在处理控制字符起着关键作用的复杂文档时。 

## 常见问题解答

### 什么是传统控制字符？

旧式控制字符是旧文档中用来控制格式和布局的非打印字符。

### 我可以删除这些控制字符而不是保留它们吗？

是的，如果需要，您可以使用 Aspose.Words for .NET 删除或替换这些字符。

### 所有版本的 Aspose.Words for .NET 都提供此功能吗？

此功能在最新版本中可用。请确保使用最新版本来访问所有功能。

### 我需要许可证才能使用 Aspose.Words for .NET 吗？

是的，您需要有效的许可证。您可以获取临时许可证以进行评估。[这里](https://purchase.aspose.com/temporary-license/).

### 在哪里可以找到有关 Aspose.Words for .NET 的更多文档？

您可以找到详细的文档[这里](https://reference.aspose.com/words/net/).
 
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
