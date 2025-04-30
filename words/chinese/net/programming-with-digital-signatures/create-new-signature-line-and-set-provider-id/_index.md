---
"description": "了解如何使用 Aspose.Words for .NET 在 Word 文档中创建新的签名行并设置提供商 ID。分步指南。"
"linktitle": "创建新的签名行并设置提供商 ID"
"second_title": "Aspose.Words文档处理API"
"title": "创建新的签名行并设置提供商 ID"
"url": "/zh/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 创建新的签名行并设置提供商 ID

## 介绍

嗨，科技爱好者们！想知道如何以编程方式在 Word 文档中添加签名行吗？今天，我们将使用 Aspose.Words for .NET 深入探讨这个问题。本指南将引导您完成每个步骤，让您轻松在 Word 文档中创建新签名行并设置提供商 ID。无论您是想实现文档处理自动化，还是只想简化工作流程，本教程都能满足您的需求。

## 先决条件

在我们开始动手之前，让我们先确保我们已经准备好了我们需要的一切：

1. Aspose.Words for .NET：如果您还没有下载，请下载 [这里](https://releases。aspose.com/words/net/).
2. 开发环境：Visual Studio 或任何其他 C# 开发环境。
3. .NET Framework：确保您已安装 .NET Framework。
4. PFX 证书：要签署文档，您需要 PFX 证书。您可以从受信任的证书颁发机构获取。

## 导入命名空间

首先，让我们在 C# 项目中导入必要的命名空间：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

好了，我们开始吧。以下是创建新签名行和设置提供商 ID 的每个步骤的详细分解。

## 步骤 1：创建新文档

首先，我们需要创建一个新的Word文档。这将是我们签名行的画布。

```csharp
// 文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

在这个代码片段中，我们初始化一个新的 `Document` 和一个 `DocumentBuilder`。 这 `DocumentBuilder` 帮助我们向文档添加元素。

## 第 2 步：定义签名行选项

接下来，我们定义签名行的选项。这包括签名者的姓名、职务、电子邮件和其他详细信息。

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

这些选项可以个性化签名行，使其清晰、专业。

## 步骤 3：插入签名行

设置完选项后，我们现在可以将签名行插入到文档中。

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

在这里， `InsertSignatureLine` 方法添加签名行，我们为其分配一个唯一的提供者ID。

## 步骤4：保存文档

插入签名行后，我们保存文档。

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

这将保存您的文档以及新添加的签名行。

## 步骤 5：设置签名选项

现在，我们需要设置文档签名的选项。这包括签名行 ID、提供商 ID、注释和签名时间。

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

这些选项确保文档使用正确的详细信息进行签名。

## 步骤 6：创建证书持有者

为了签署文档，我们将使用 PFX 证书。让我们为其创建一个证书持有者。

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

确保更换 `"morzal.pfx"` 与您的实际证书文件和 `"aw"` 使用您的证书密码。

## 步骤 7：签署文件

最后，我们使用数字签名实用程序对文档进行签名。

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

这将对文档进行签名并将其保存为新文件。

## 结论

就这样！您已成功使用 Aspose.Words for .NET 在 Word 文档中创建了新的签名行并设置了提供者 ID。这个强大的库让文档处理任务的管理和自动化变得异常简单。不妨尝试一下，看看它如何简化您的工作流程。

## 常见问题解答

### 我可以自定义签名行的外观吗？
当然！您可以在 `SignatureLineOptions` 以满足您的需求。

### 如果我没有 PFX 证书怎么办？
您需要从受信任的证书颁发机构获取一个证书。这对于数字签名文档至关重要。

### 我可以在一份文档中添加多个签名行吗？
是的，您可以通过使用不同的选项重复插入过程来添加所需数量的签名行。

### Aspose.Words for .NET 是否与 .NET Core 兼容？
是的，Aspose.Words for .NET 支持 .NET Core，使其适用于不同的开发环境。

### 数字签名有多安全？
只要您使用有效且可信的证书，使用 Aspose.Words 创建的数字签名就非常安全。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}