---
title: 使用目标机器的字体
linktitle: 使用目标机器的字体
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文档中使用目标机器的字体。按照我们的分步指南进行无缝字体集成。
weight: 10
url: /zh/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用目标机器的字体

## 介绍

您准备好进入 Aspose.Words for .NET 的迷人世界了吗？系好安全带，因为我们将带您踏上字体的神奇之旅。今天，我们将重点介绍如何在处理 Word 文档时使用目标机器上的字体。无论在哪里查看，这个巧妙的功能都可以确保您的文档看起来完全符合您的预期。让我们开始吧！

## 先决条件

在我们讨论细节之前，让我们先确保您已准备好所需的一切：

1.  Aspose.Words for .NET：确保已安装 Aspose.Words for .NET 库。如果尚未安装，可以下载[这里](https://releases.aspose.com/words/net/).
2. 开发环境：您应该设置一个 .NET 开发环境，例如 Visual Studio。
3. 要使用的文档：准备好一个 Word 文档以供测试。我们将使用名为“带有替代字体的要点.docx”的文档。

现在我们已经介绍了基础知识，让我们深入研究代码！

## 导入命名空间

首先，我们需要导入必要的命名空间。这是我们项目的骨干，连接所有点。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 步骤 1：加载 Word 文档

本教程的第一步是加载 Word 文档。一切从这里开始。我们将使用`Document`来自 Aspose.Words 库的类来实现这一点。

### 步骤 1.1：定义文档路径

首先，我们来定义文档目录的路径。这是您的 Word 文档所在的位置。

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

### 步骤 1.2：加载文档

现在，我们使用`Document`班级。

```csharp
//加载 Word 文档
Document doc = new Document(dataDir + "Bullet points with alternative font.docx");
```

## 步骤 2：配置保存选项

接下来，我们需要配置保存选项。此步骤至关重要，因为它可确保文档中使用的字体是目标机器的字体。

我们将创建一个实例`HtmlFixedSaveOptions`并设置`UseTargetMachineFonts`财产`true`.

```csharp
//使用“使用目标机器的字体”功能配置备份选项
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions
{
    UseTargetMachineFonts = true
};
```

## 步骤 3：保存文档

最后，我们将文档保存为固定的 HTML 文件。这就是奇迹发生的地方！

我们将使用`Save`方法使用配置的保存选项保存文档。

```csharp
//将文档转换为固定 HTML
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html", saveOptions);
```

## 步骤 4：验证输出

最后但同样重要的是，验证输出总是一个好主意。打开保存的 HTML 文件并检查字体是否从目标机器正确应用。

导航到保存 HTML 文件的目录并在 Web 浏览器中打开它。

```csharp
//通过打开 HTML 文件验证输出
System.Diagnostics.Process.Start(dataDir + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html");
```

就这样！您已成功使用 Aspose.Words for .NET 在 Word 文档中使用了目标机器的字体。

## 结论

使用目标机器的字体可确保您的 Word 文档无论在何处查看都看起来一致且专业。Aspose.Words for .NET 使此过程变得简单而高效。通过学习本教程，您已经学会了如何加载文档、配置保存选项以及使用所需的字体设置保存文档。祝您编码愉快！

## 常见问题解答

### 我可以将此方法用于其他文档格式吗？
是的，Aspose.Words for .NET 支持各种文档格式，您可以为不同的格式配置类似的保存选项。

### 如果目标机器没有所需的字体怎么办？
如果目标机器没有所需的字体，文档可能无法按预期呈现。必要时嵌入字体总是一个好主意。

### 如何在文档中嵌入字体？
嵌入字体可以使用`FontSettings`Aspose.Words for .NET 中的类。请参阅[文档](https://reference.aspose.com/words/net/)了解更多详情。

### 有没有办法在保存之前预览文档？
是的，您可以使用`DocumentRenderer`类用于在保存之前预览文档。查看 Aspose.Words for .NET[文档](https://reference.aspose.com/words/net/)了解更多信息。

### 我可以进一步自定义 HTML 输出吗？
当然！`HtmlFixedSaveOptions`类提供了各种属性来自定义 HTML 输出。探索[文档](https://reference.aspose.com/words/net/)所有可用选项。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
