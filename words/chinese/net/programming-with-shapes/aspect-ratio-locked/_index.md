---
title: 长宽比已锁定
linktitle: 长宽比已锁定
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 锁定 Word 文档中形状的纵横比。按照此分步指南保持图像和形状的比例。
weight: 10
url: /zh/net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 长宽比已锁定

## 介绍

您是否曾想过如何在 Word 文档中保持图像和形状的完美比例？有时，您需要确保图像和形状在调整大小时不会变形。这时锁定纵横比就派上用场了。在本教程中，我们将探讨如何使用 Aspose.Words for .NET 设置 Word 文档中形状的纵横比。我们将把它分解为易于遵循的步骤，确保您可以自信地将这些技能应用到您的项目中。

## 先决条件

在深入研究代码之前，让我们先了解一下入门所需的内容：

- Aspose.Words for .NET 库：您需要安装 Aspose.Words for .NET。如果尚未安装，您可以[点击下载](https://releases.aspose.com/words/net/).
- 开发环境：确保已设置 .NET 开发环境。Visual Studio 是一种流行的选择。
- C# 基础知识：熟悉 C# 编程将会有所帮助。

## 导入命名空间

首先，让我们导入必要的命名空间。这些命名空间将使我们能够访问处理 Word 文档和形状所需的类和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 步骤 1：设置文档目录

在开始操作形状之前，我们需要设置一个用于存储文档的目录。为了简单起见，我们将使用占位符`YOUR DOCUMENT DIRECTORY`将其替换为您的文档目录的实际路径。

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 第 2 步：创建新文档

接下来，我们将使用 Aspose.Words 创建一个新 Word 文档。该文档将作为我们添加形状和图像的画布。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

在这里，我们创建一个实例`Document`类并使用`DocumentBuilder`来帮助我们构建文档内容。

## 步骤 3：插入图片

现在，让我们将图像插入到文档中。我们将使用`InsertImage`方法`DocumentBuilder`类。确保在指定的目录中有一个图像。

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

代替`dataDir + "Transparent background logo.png"`与您的图像文件的路径一起。

## 步骤 4：锁定长宽比

插入图像后，我们可以锁定其纵横比。锁定纵横比可确保图像的比例在调整大小时保持不变。

```csharp
shape.AspectRatioLocked = true;
```

环境`AspectRatioLocked`到`true`确保图像保持其原始的纵横比。

## 步骤 5：保存文档

最后，我们将文档保存到指定的目录。此步骤将我们对文档文件所做的所有更改写入其中。

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## 结论

恭喜！您已成功了解如何使用 Aspose.Words for .NET 设置 Word 文档中形状的纵横比。通过遵循这些步骤，您可以确保图像和形状保持其比例，使您的文档看起来专业而精致。请随意尝试不同的图像和形状，以了解纵横比锁定功能在各种情况下的工作原理。

## 常见问题解答

### 锁定宽高比后还能解锁吗？
是的，你可以通过设置解锁宽高比`shape.AspectRatioLocked = false`.

### 如果我调整锁定纵横比的图像大小会发生什么情况？
图像将按比例调整大小，保持其原始的宽高比。

### 除了图像，我还能将其应用于其他形状吗？
当然可以！长宽比锁定功能可应用于任何形状，包括矩形、圆形等。

### Aspose.Words for .NET 是否与 .NET Core 兼容？
是的，Aspose.Words for .NET 同时支持 .NET Framework 和 .NET Core。

### 在哪里可以找到有关 Aspose.Words for .NET 的更多文档？
您可以找到全面的文档[这里](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
