---
"description": "了解如何使用 Aspose.Words for .NET 将 Word 文档转换为 1Bpp 索引图像。按照我们的分步指南轻松完成转换。"
"linktitle": "格式 1Bpp 索引"
"second_title": "Aspose.Words文档处理API"
"title": "格式 1Bpp 索引"
"url": "/zh/net/programming-with-imagesaveoptions/format-1bpp-indexed/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 格式 1Bpp 索引

## 介绍

有没有想过如何只用几行代码就能将Word文档保存为黑白图像？好吧，你很幸运！今天，我们将深入探讨一个巧妙的小技巧，使用Aspose.Words for .NET，您可以将文档转换为1Bpp的索引图像。这种格式非常适合某些类型的数字存档、打印或需要节省空间的情况。我们将分解每个步骤，使其变得非常简单。准备好了吗？让我们开始吧！

## 先决条件

在我们开始之前，您需要做好以下几件事：

- Aspose.Words for .NET：请确保您已安装该库。您可以 [点击此处下载](https://releases。aspose.com/words/net/).
- .NET 开发环境：Visual Studio 是一个不错的选择，但您可以使用任何您喜欢的环境。
- C# 基础知识：别担心，我们会尽量简单，但稍微熟悉一下 C# 会有所帮助。
- Word 文档：准备一个要转换的示例 Word 文档。

## 导入命名空间

首先，我们需要导入必要的命名空间。这至关重要，因为它允许我们从 Aspose.Words 访问所需的类和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 步骤 1：设置文档目录

您需要指定文档目录的路径。这是存储 Word 文档以及转换后图像的位置。

```csharp
// 文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 第 2 步：加载 Word 文档

现在，让我们将 Word 文档加载到 Aspose.Words `Document` 对象。此对象代表您的 Word 文件并允许您对其进行操作。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 步骤3：配置图像保存选项

接下来，我们需要设置 `ImageSaveOptions`。这就是奇迹发生的地方。我们将配置它以 1Bpp 索引颜色模式将图像保存为 PNG 格式。

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png：这指定我们要将文档保存为 PNG 图像。
- PageSet(1)：这表示我们只转换第一页。
- ImageColorMode.BlackAndWhite：将图像设置为黑白色。
- ImagePixelFormat.Format1bppIndexed：将图像格式设置为 1Bpp 索引。

## 步骤 4：将文档保存为图像

最后，我们使用 `Save` 方法 `Document` 目的。

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## 结论

就这样！只需几行代码，您就使用 Aspose.Words for .NET 将 Word 文档转换为 1Bpp 的索引图像。此方法对于从文档创建高对比度、节省空间的图像非常有用。现在，您可以轻松地将其集成到您的项目和工作流程中。祝您编码愉快！

## 常见问题解答

### 什么是 1Bpp 索引图像？
1Bpp（每像素 1 位）索引图像是一种黑白图像格式，其中每个像素由一个位（0 或 1）表示。这种格式非常节省空间。

### 我可以一次转换 Word 文档的多页吗？
是的，你可以。修改 `PageSet` 财产 `ImageSaveOptions` 包括多页或整个文档。

### 我需要许可证才能使用 Aspose.Words for .NET 吗？
是的，Aspose.Words for .NET 需要许可证才能使用全部功能。您可以获取 [此处为临时驾照](https://purchase。aspose.com/temporary-license/).

### 我可以将 Word 文档转换为哪些其他图像格式？
Aspose.Words 支持多种图像格式，包括 JPEG、BMP 和 TIFF。只需更改 `SaveFormat` 在 `ImageSaveOptions`。

### 在哪里可以找到有关 Aspose.Words for .NET 的更多文档？
您可以找到有关 [Aspose.Words for .NET 文档页面](https://reference。aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}