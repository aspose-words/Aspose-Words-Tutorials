---
"description": "了解如何使用 Aspose.Words for .NET 渲染 Word 文档时指定默认字体。确保跨平台文档外观一致。"
"linktitle": "渲染时指定默认字体"
"second_title": "Aspose.Words文档处理API"
"title": "渲染时指定默认字体"
"url": "/zh/net/working-with-fonts/specify-default-font-when-rendering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 渲染时指定默认字体

## 介绍

确保您的 Word 文档在不同平台上正确呈现可能是一项挑战，尤其是在处理字体兼容性时。保持一致外观的一种方法是在将文档渲染为 PDF 或其他格式时指定默认字体。在本教程中，我们将探讨如何使用 Aspose.Words for .NET 设置默认字体，以便您的文档无论在何处查看都能呈现美观。

## 先决条件

在深入研究代码之前，让我们先介绍一下学习本教程所需的内容：

- Aspose.Words for .NET：请确保您已安装最新版本。您可以下载 [这里](https://releases。aspose.com/words/net/).
- 开发环境：Visual Studio 或任何其他 .NET 开发环境。
- C# 基础知识：本教程假设您熟悉 C# 编程。

## 导入命名空间

首先，您需要导入必要的命名空间。这将允许您访问使用 Aspose.Words 所需的类和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

现在，让我们将指定默认字体的过程分解为易于遵循的步骤。

## 步骤 1：设置文档目录

首先，定义文档目录的路径。这是存储输入和输出文件的地方。

```csharp
// 文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 第 2 步：加载文档

接下来，加载要渲染的文档。在本例中，我们将使用名为“Rendering.docx”的文件。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 步骤3：配置字体设置

创建一个实例 `FontSettings` 并指定默认字体。如果在渲染过程中找不到定义的字体，Aspose.Words 将使用机器上最接近的可用字体。

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";
```

## 步骤 4：将字体设置应用于文档

将配置的字体设置分配给您的文档。

```csharp
doc.FontSettings = fontSettings;
```

## 步骤5：保存文档

最后，将文档保存为所需的格式。在本例中，我们将其保存为 PDF。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SpecifyDefaultFontWhenRendering.pdf");
```

## 结论

通过遵循以下步骤，您可以确保 Word 文档以指定的默认字体呈现，从而在不同平台上保持一致性。这对于广泛共享或在字体可用性不同的系统上查看的文档尤其有用。


## 常见问题解答

### 为什么要在 Aspose.Words 中指定默认字体？
指定默认字体可确保您的文档在不同平台上显示一致，即使原始字体不可用。

### 如果在渲染过程中找不到默认字体会发生什么？
Aspose.Words 将使用机器上最接近的可用字体来尽可能保持文档的外观。

### 我可以指定多个默认字体吗？
不可以，您只能指定一种默认字体。不过，您可以使用 `FontSettings` 班级。

### Aspose.Words for .NET 是否与所有版本的 Word 文档兼容？
是的，Aspose.Words for .NET 支持多种 Word 文档格式，包括 DOC、DOCX、RTF 等。

### 如果遇到问题，我可以在哪里获得支持？
您可以从 Aspose 社区和开发人员处获得支持 [Aspose.Words 支持论坛](https://forum。aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}