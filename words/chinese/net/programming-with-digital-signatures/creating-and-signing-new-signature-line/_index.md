---
"description": "通过本分步教程，学习如何使用 Aspose.Words for .NET 在 Word 文档中创建签名行并进行数字签名。非常适合文档自动化。"
"linktitle": "创建并签署新的签名行"
"second_title": "Aspose.Words文档处理API"
"title": "创建并签署新的签名行"
"url": "/zh/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 创建并签署新的签名行

## 介绍

嘿！您有一个 Word 文档，需要添加签名行并进行数字签名。听起来很棘手？一点也不！借助 Aspose.Words for .NET，您只需几行代码即可无缝实现。在本教程中，我们将引导您完成从设置环境到使用全新签名保存文档的整个过程。准备好了吗？让我们开始吧！

## 先决条件

在我们进入代码之前，让我们确保您拥有所需的一切：
1. Aspose.Words for .NET - 您可以 [点击此处下载](https://releases。aspose.com/words/net/).
2. 强烈推荐.NET 开发环境 - Visual Studio。
3. 要签署的文件 - 创建一个简单的 Word 文档或使用现有的文档。
4. 证书文件 - 这是数字签名所必需的。您可以使用 `.pfx` 文件。
5. 签名行图像 - 可选，签名的图像文件。

## 导入命名空间

首先，我们需要导入必要的命名空间。这一步至关重要，因为它设置了使用 Aspose.Words 功能的环境。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## 步骤1：设置文档目录

每个项目都需要一个好的开始。让我们设置文档目录的路径。这是保存和检索文档的位置。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步骤2：创建新文档

现在，让我们使用 Aspose.Words 创建一个新的 Word 文档。这将是我们添加签名行的画布。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步骤 3：插入签名行

这就是奇迹发生的地方。我们使用 `DocumentBuilder` 班级。

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## 步骤 4：保存带有签名行的文档

签名完成后，我们需要保存文档。这是签署前的中间步骤。

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## 步骤 5：设置签名选项

现在，让我们设置文档签名的选项。这包括指定签名行 ID 和要使用的图像。

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## 步骤6：加载证书

数字签名需要证书。在这里，我们加载用于签名文档的证书文件。

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## 步骤7：签署文件

这是最后一步。我们使用 `DigitalSignatureUtil` 类来对文档进行签名。签名后的文档将以新名称保存。

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## 结论

就这样！通过这些步骤，您已成功创建了一个新的 Word 文档，添加了签名行，并使用 Aspose.Words for .NET 对其进行了数字签名。这是一个强大的工具，可轻松实现文档自动化。无论您处理的是合同、协议还是其他正式文件，此方法都能确保它们得到安全签名和验证。

## 常见问题解答

### 我可以使用其他图像格式作为签名行吗？
是的，您可以使用各种图像格式，如 PNG、JPG、BMP 等。

### 是否有必要使用 `.pfx` 申请证书？
是的， `.pfx` 文件是存储包括证书和私钥在内的加密信息的常用格式。

### 我可以在一份文档中添加多个签名行吗？
当然！您可以重复插入步骤，插入多个签名行。

### 如果我没有数字证书怎么办？
您需要从受信任的证书颁发机构获取数字证书或使用 OpenSSL 等工具生成数字证书。

### 如何验证文档中的数字签名？
您可以在Word中打开签名的文档并转到签名详细信息以验证签名的真实性和完整性。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}