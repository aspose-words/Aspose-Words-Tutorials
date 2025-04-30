---
"description": "使用 Aspose.Words for .NET 对图像进行下采样，从而减小 PDF 文档大小。优化您的 PDF，加快上传和下载速度。"
"linktitle": "通过降低图像采样率来减小 PDF 文档大小"
"second_title": "Aspose.Words文档处理API"
"title": "通过降低图像采样率来减小 PDF 文档大小"
"url": "/zh/net/programming-with-pdfsaveoptions/downsampling-images/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 通过降低图像采样率来减小 PDF 文档大小

## 介绍

PDF 是数字世界中不可或缺的一部分，可用于从共享文档到创建电子书等各种用途。然而，它们的大小有时会成为一大障碍，尤其是在处理包含大量图像的内容时。这时，图像降采样就派上用场了。通过降低 PDF 中图像的分辨率，您可以显著减小文件大小，而不会过多地影响质量。在本教程中，我们将逐步讲解如何使用 Aspose.Words for .NET 实现此目标。

## 先决条件

在我们进入代码之前，让我们确保您拥有所需的一切：

1. Aspose.Words for .NET：确保已安装 Aspose.Words 库。如果没有，可以下载 [这里](https://releases。aspose.com/words/net/).
2. 开发环境：任何 .NET 开发环境，如 Visual Studio。
3. C# 基础知识：了解 C# 编程的基础知识将会有所帮助。
4. 示例文档：Word 文档（例如， `Rendering.docx`) 并把图像转换为 PDF。

## 导入命名空间

首先，你需要导入必要的命名空间。在代码文件的顶部添加以下内容：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

现在，让我们将这个过程分解为易于管理的步骤。

## 步骤 1：加载文档

第一步是加载你的Word文档。在这里你需要指定文档目录的路径。

```csharp
// 文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

在此步骤中，我们将从指定目录加载 Word 文档。请确保替换 `"YOUR DOCUMENT DIRECTORY"` 使用您的文档所在的实际路径。

## 步骤 2：配置下采样选项

接下来，我们需要配置下采样选项。这涉及设置图像的分辨率和分辨率阈值。

```csharp
// 我们可以设置下采样的最小阈值。
// 该值将阻止输入文档中的第二幅图像被下采样。
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    DownsampleOptions = { Resolution = 36, ResolutionThreshold = 128 }
};
```

在这里，我们创建一个新的实例 `PdfSaveOptions` 并设置 `Resolution` 至 36 DPI 和 `ResolutionThreshold` 至 128 DPI。这意味着任何分辨率高于 128 DPI 的图像都将被下采样至 36 DPI。

## 步骤 3：将文档保存为 PDF

最后，我们将文档保存为具有配置选项的 PDF。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DownsamplingImages.pdf", saveOptions);
```

在最后一步中，我们将文档以 PDF 格式保存在同一目录中，并使用指定的下采样选项。

## 结论

就这样！您已成功使用 Aspose.Words for .NET 对图像进行下采样，从而减小了 PDF 的大小。这不仅使您的 PDF 更易于管理，还有助于加快上传和下载速度，并提供更流畅的浏览体验。

## 常见问题解答

### 什么是下采样？
下采样是降低图像分辨率的过程，这有助于减小包含这些图像的文档的文件大小。

### 下采样会影响图像质量吗？
是的，降采样会降低图像质量。但是，影响取决于分辨率降低的程度。这需要在文件大小和图像质量之间进行权衡。

### 我可以选择对哪些图像进行下采样吗？
是的，通过设置 `ResolutionThreshold`，您可以根据图像的原始分辨率控制哪些图像被下采样。

### 下采样的理想分辨率是多少？
理想的分辨率取决于您的具体需求。通常，72 DPI 用于网页图像，而更高的分辨率则用于打印质量。

### Aspose.Words for .NET 免费吗？
Aspose.Words for .NET 是一款商业产品，但您可以下载免费试用版 [这里](https://releases.aspose.com/) 或申请 [临时执照](https://purchase。aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}