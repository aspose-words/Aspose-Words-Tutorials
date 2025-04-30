---
"description": "学习如何使用 Aspose.Words for .NET 签署加密的 Word 文档，本指南一步步详尽。非常适合开发人员。"
"linktitle": "签名加密的 Word 文档"
"second_title": "Aspose.Words文档处理API"
"title": "签名加密的 Word 文档"
"url": "/zh/net/programming-with-digital-signatures/signing-encrypted-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 签名加密的 Word 文档

## 介绍

有没有想过如何对加密的 Word 文档进行签名？今天，我们将使用 Aspose.Words for .NET 演示这个过程。系好安全带，准备好迎接这个详细、引人入胜、趣味十足的教程吧！

## 先决条件

在深入研究代码之前，请确保您已准备好所需的一切：

1. Aspose.Words for .NET：从以下位置下载并安装 [这里](https://releases。aspose.com/words/net/).
2. Visual Studio：确保您已安装它。
3. 有效证书：您需要一个 .pfx 证书文件。
4. 基本 C# 知识：了解基础知识将使本教程更加顺畅。

## 导入命名空间

首先，我们导入必要的命名空间。这些对于访问 Aspose.Words 功能至关重要。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.DigitalSignatures;
```

现在，让我们将这个过程分解为简单、易于管理的步骤。

## 步骤 1：设置项目

首先，设置你的 Visual Studio 项目。打开 Visual Studio 并创建一个新的 C# 控制台应用程序。将其命名为“SignEncryptedWordDoc”。

## 第 2 步：将 Aspose.Words 添加到您的项目

接下来，我们需要将 Aspose.Words 添加到您的项目中。有几种方法可以做到这一点，但使用 NuGet 是最简单的。 

1. 从“工具”>“NuGet 包管理器”>“包管理器控制台”打开 NuGet 包管理器控制台。
2. 运行以下命令：

```powershell
Install-Package Aspose.Words
```

## 步骤3：准备文档目录

您需要一个目录来存储您的 Word 文档和证书。让我们创建一个。

1. 在您的计算机上创建一个目录。为了简单起见，我们将其命名为“DocumentDirectory”。
2. 将您的 Word 文档（例如“Document.docx”）和 .pfx 证书（例如“morzal.pfx”）放在此目录中。

## 步骤4：编写代码

现在，让我们深入研究代码。打开你的 `Program.cs` 文件并首先设置文档目录的路径并初始化 `SignOptions` 以及解密密码。

```csharp
// 文档目录的路径。
string dataDir = "YOUR DOCUMENTS DIRECTORY";
SignOptions signOptions = new SignOptions { DecryptionPassword = "decryptionPassword" };
```

## 步骤5：加载证书

接下来，使用 `CertificateHolder` 类。这将需要您的 .pfx 文件的路径和证书的密码。

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## 第六步：签署文件

最后，使用 `DigitalSignatureUtil.Sign` 方法来对加密的 Word 文档进行签名。此方法需要输入文件、输出文件、证书持有者和签名选项。

```csharp
DigitalSignatureUtil.Sign(
    dataDir + "Document.docx",
    dataDir + "DigitallySignedDocument.docx",
    certHolder,
    signOptions);
```

## 步骤 7：运行代码

保存文件并运行项目。如果一切设置正确，您应该会在指定目录中看到已签名的文档。

## 结论

就这样！您已成功使用 Aspose.Words for .NET 签署了一份加密的 Word 文档。有了这个强大的库，即使是加密文件，数字签名也变得轻而易举。祝您编码愉快！

## 常见问题解答

### 我可以使用不同类型的证书吗？
是的，Aspose.Words 支持各种证书类型，只要它们的格式正确。

### 可以一次签署多份文件吗？
当然！您可以循环遍历一系列文档，并以编程方式对每个文档进行签名。

### 如果我忘记了解密密码怎么办？
不幸的是，如果没有解密密码，您将无法签署该文档。

### 我可以在文件上添加可见的签名吗？
是的，Aspose.Words 也允许您添加可见的数字签名。

### 有没有办法验证签名？
是的，您可以使用 `DigitalSignatureUtil.Verify` 方法来验证签名。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}