---
"description": "了解如何使用 Aspose.Words for .NET 将 Word 文档保存为 HTML 格式，并导出 CSS 和字体等资源。请按照我们的分步指南操作。"
"linktitle": "出口资源"
"second_title": "Aspose.Words文档处理API"
"title": "出口资源"
"url": "/zh/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 出口资源

## 介绍

嗨，科技爱好者们！如果您需要将 Word 文档转换为 HTML，那么您来对地方了。今天，我们将深入探索 Aspose.Words for .NET 的精彩世界。这个强大的库让您能够轻松地以编程方式处理 Word 文档。在本教程中，我们将逐步讲解如何使用 Aspose.Words for .NET 将 Word 文档保存为 HTML 格式时导出字体和 CSS 等资源。系好安全带，开启一段充满乐趣和知识的旅程吧！

## 先决条件

在深入代码之前，我们先来确认一下你已经准备好了一切准备就绪。以下是一份快速检查清单：

1. Visual Studio：确保您的计算机上已安装 Visual Studio。您可以从 [Visual Studio 网站](https://visualstudio。microsoft.com/).
2. Aspose.Words for .NET：您需要 Aspose.Words for .NET 库。如果您还没有，可以免费试用 [Aspose 版本](https://releases.aspose.com/words/net/) 或从 [Aspose 商店](https://purchase。aspose.com/buy).
3. C# 基础知识：对 C# 的基本了解将帮助您理解代码示例。

明白了吗？太棒了！接下来我们导入必要的命名空间。

## 导入命名空间

要使用 Aspose.Words for .NET，您需要在项目中包含相关的命名空间。操作方法如下：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

这些命名空间对于访问我们将在教程中使用的 Aspose.Words 类和方法至关重要。

让我们分解一下将 Word 文档保存为 HTML 时导出资源的流程。我们将逐步讲解，以便于理解。

## 步骤 1：设置文档目录

首先，您需要指定文档目录的路径。这是您的 Word 文档所在的位置，也是 HTML 文件的保存位置。

```csharp
// 文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替 `"YOUR DOCUMENT DIRECTORY"` 使用目录的实际路径。

## 第 2 步：加载 Word 文档

接下来，让我们加载要转换为 HTML 的 Word 文档。在本教程中，我们将使用名为 `Rendering。docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

这行代码从指定目录加载文档。

## 步骤 3：配置 HTML 保存选项

要导出 CSS 和字体等资源，您需要配置 `HtmlSaveOptions`。此步骤对于确保您的 HTML 输出结构良好并包含必要的资源至关重要。

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/resources”
};
```

让我们分解一下每个选项的作用：
- `CssStyleSheetType = CssStyleSheetType.External`：此选项指定 CSS 样式应保存在外部样式表中。
- `ExportFontResources = true`：这可以导出字体资源。
- `ResourceFolder = dataDir + "Resources"`：指定将保存资源（如字体和 CSS 文件）的本地文件夹。
- `ResourceFolderAlias = "http://example.com/resources"`：设置资源文件夹的别名，该别名将在HTML文件中使用。

## 步骤 4：将文档保存为 HTML

配置完保存选项后，最后一步是将文档保存为 HTML 文件。操作方法如下：

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

这行代码将文档与导出的资源一起以 HTML 格式保存。

## 结论

就这样！您已成功使用 Aspose.Words for .NET 将 Word 文档保存为 HTML 格式，并导出了资源。借助这个强大的库，以编程方式处理 Word 文档变得轻而易举。无论您是在开发 Web 应用程序，还是只需要将文档转换为离线使用，Aspose.Words 都能满足您的需求。

## 常见问题解答

### 我可以将图像与字体和 CSS 一起导出吗？
是的，可以！Aspose.Words for .NET 也支持导出图像。只需确保配置 `HtmlSaveOptions` 因此。

### 有没有办法嵌入 CSS 而不是使用外部样式表？
当然。你可以设置 `CssStyleSheetType` 到 `CssStyleSheetType.Embedded` 如果您更喜欢嵌入式样式。

### 如何自定义输出 HTML 文件的名称？
您可以在 `doc.Save` 方法。例如， `doc。Save(dataDir + "CustomFileName.html", saveOptions);`.

### Aspose.Words 除了 HTML 之外还支持其他格式吗？
是的，它支持多种格式，包括 PDF、DOCX、TXT 等。查看 [文档](https://reference.aspose.com/words/net/) 以获取完整列表。

### 我可以在哪里获得更多支持和资源？
如需更多帮助，请访问 [Aspose.Words 支持论坛](https://forum.aspose.com/c/words/8)您还可以在 [Aspose 网站](https://reference。aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}