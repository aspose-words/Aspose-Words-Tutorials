---
title: 通过对图像进行下采样来减小 PDF 文档大小
linktitle: 通过对图像进行下采样来减小 PDF 文档大小
second_title: Aspose.Words 文档处理 API
description: 使用 Aspose.Words for .NET 对图像进行下采样，从而减小 PDF 文档大小。优化您的 PDF，以加快上传和下载时间。
weight: 10
url: /zh/net/programming-with-pdfsaveoptions/downsampling-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 通过对图像进行下采样来减小 PDF 文档大小

## 介绍

PDF 是数字世界中的必备品，可用于从共享文档到创建电子书等各种用途。然而，它们的大小有时会成为障碍，尤其是在处理富含图像的内容时。这就是图像下采样发挥作用的地方。通过降低 PDF 中图像的分辨率，您可以显著减小文件大小，而不会过多地影响质量。在本教程中，我们将逐步介绍使用 Aspose.Words for .NET 实现此目的的步骤。

## 先决条件

在我们进入代码之前，让我们确保您拥有所需的一切：

1.  Aspose.Words for .NET：确保已安装 Aspose.Words 库。如果没有，您可以下载它[这里](https://releases.aspose.com/words/net/).
2. 开发环境：任何 .NET 开发环境，如 Visual Studio。
3. C# 基础知识：了解 C# 编程的基础知识将会有所帮助。
4. 示例文档：Word 文档（例如，`Rendering.docx`) 并把图像转换为 PDF。

## 导入命名空间

首先，你需要导入必要的命名空间。在代码文件顶部添加以下内容：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

现在，让我们将这个过程分解为易于管理的步骤。

## 步骤 1：加载文档

第一步是加载您的 Word 文档。在这里指定文档目录的路径。

```csharp
//文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

在此步骤中，我们从指定目录加载 Word 文档。确保替换`"YOUR DOCUMENT DIRECTORY"`与您的文档所在的实际路径。

## 步骤 2：配置下采样选项

接下来，我们需要配置下采样选项。这涉及设置图像的分辨率和分辨率阈值。

```csharp
//我们可以设置下采样的最小阈值。
//该值将阻止输入文档中的第二个图像被下采样。
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    DownsampleOptions = { Resolution = 36, ResolutionThreshold = 128 }
};
```

在这里，我们创建一个新的实例`PdfSaveOptions`并设置`Resolution`至 36 DPI 和`ResolutionThreshold`至 128 DPI。这意味着任何分辨率高于 128 DPI 的图像都将被下采样至 36 DPI。

## 步骤 3：将文档保存为 PDF

最后，我们使用配置的选项将文档保存为 PDF。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DownsamplingImages.pdf", saveOptions);
```

在此最后一步中，我们将使用指定的下采样选项将文档保存为同一目录中的 PDF。

## 结论

就这样！您已成功通过使用 Aspose.Words for .NET 对图像进行下采样来减小 PDF 的大小。这不仅使您的 PDF 更易于管理，而且还有助于加快上传、下载速度并提供更流畅的观看体验。

## 常见问题解答

### 什么是下采样？
下采样是降低图像分辨率的过程，这有助于减小包含这些图像的文档的文件大小。

### 下采样会影响图像质量吗？
是的，降采样会降低图像质量。但是，影响取决于分辨率降低的程度。这是文件大小和图像质量之间的权衡。

### 我可以选择对哪些图像进行下采样吗？
是的，通过设置`ResolutionThreshold`，您可以根据图像的原始分辨率控制哪些图像需要下采样。

### 下采样的理想分辨率是多少？
理想的分辨率取决于您的具体需求。通常，72 DPI 用于网页图像，而更高的分辨率用于打印质量。

### Aspose.Words for .NET 免费吗？
 Aspose.Words for .NET 是一款商业产品，但您可以下载免费试用版[这里](https://releases.aspose.com/)或申请[临时执照](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
