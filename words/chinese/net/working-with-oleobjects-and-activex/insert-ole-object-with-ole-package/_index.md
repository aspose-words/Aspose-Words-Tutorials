---
title: 使用 Ole 包在 Word 中插入 Ole 对象
linktitle: 使用 Ole 包在 Word 中插入 Ole 对象
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文档中插入 OLE 对象。按照我们详细的分步指南无缝嵌入文件。
weight: 10
url: /zh/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Ole 包在 Word 中插入 Ole 对象

## 介绍

如果您曾经想将文件嵌入 Word 文档，那么您来对地方了。无论是 ZIP 文件、Excel 工作表还是任何其他文件类型，将其直接嵌入 Word 文档都非常有用。想象一下，这就像在您的文档中有一个秘密隔间，您可以在其中存放各种宝藏。今天，我们将介绍如何使用 Aspose.Words for .NET 来实现这一点。准备好成为 Word 大师了吗？让我们开始吧！

## 先决条件

在开始之前，请确保您已准备好以下内容：

1. Aspose.Words for .NET：如果你还没有，请从[这里](https://releases.aspose.com/words/net/).
2. 开发环境：Visual Studio 或任何其他 .NET 开发环境。
3. 对 C# 的基本了解：您不需要成为专家，但了解 C# 会有所帮助。
4. 文档目录：您可以存储和检索文档的文件夹。

## 导入命名空间

首先，让我们理清命名空间。您需要在项目中包含以下命名空间：

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

让我们将其分解成小步骤，这样就很容易理解了。

## 步骤 1：设置文档

想象一下，您是一位拥有空白画布的艺术家。首先，我们需要一张空白画布，也就是我们的 Word 文档。设置方法如下：

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

此代码初始化一个新的 Word 文档并设置一个 DocumentBuilder，我们将使用它来将内容插入到我们的文档中。

## 第 2 步：读取 Ole 对象

接下来，让我们读取要嵌入的文件。想象一下拿起你想藏在秘密隔间的宝藏：

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

此行从 ZIP 文件中读取所有字节并将它们存储在字节数组中。

## 步骤 3：插入 Ole 对象

现在到了神奇的部分。我们将把文件嵌入到我们的 Word 文档中：

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

在这里，我们从字节数组创建一个内存流，并使用`InsertOleObject`方法将其嵌入到文档中。我们还为嵌入的对象设置了文件名和显示名称。

## 步骤 4：保存文档

最后，让我们保存我们的杰作：

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

这会将嵌入文件的文档保存在指定的目录中。

## 结论

就这样！您已成功使用 Aspose.Words for .NET 将 OLE 对象嵌入 Word 文档。这就像在文档中添加了一颗随时可以揭开的隐藏宝石。从技术文档到动态报告，这种技术对于各种应用程序都非常有用。 

## 常见问题解答

### 我可以使用此方法嵌入其他文件类型吗？
是的，您可以嵌入各种文件类型，例如 Excel 表、PDF 和图像。

### 我需要 Aspose.Words 的许可证吗？
是的，您需要有效的执照。您可以获得[临时执照](https://purchase.aspose.com/temporary-license/)进行评估。

### 如何自定义 OLE 对象的显示名称？
您可以设置`DisplayName`的财产`OlePackage`进行自定义。

### Aspose.Words 与 .NET Core 兼容吗？
是的，Aspose.Words 同时支持 .NET Framework 和 .NET Core。

### 我可以编辑 Word 文档中嵌入的 OLE 对象吗？
不可以，您无法直接在 Word 中编辑 OLE 对象。您需要在其本机应用程序中打开它。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
