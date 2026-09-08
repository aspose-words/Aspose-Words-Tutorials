---
category: general
date: 2026-09-08
description: 如何使用数字签名的 docx 工作流对 Word 文档进行签名，加载 pfx 证书，并在 C# 中创建 XAdES 签名。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to sign word
- digital signature docx
- load pfx certificate
- digitally sign word
- create xades signature
language: zh
lastmod: 2026-09-08
og_description: 如何使用数字签名的 docx 流签署 Word 文档，加载 pfx 证书，并在 C# 中创建 XAdES 签名。请参阅完整示例。
og_image_alt: Screenshot showing a Word document signed with XAdES EPES digital signature
og_title: 如何在 C# 中使用 XAdES EPES 对 Word 文档进行签名——一步步指南
schemas:
- author: GroupDocs
  dateModified: '2026-09-08'
  description: How to sign word documents using a digital signature docx workflow,
    load pfx certificate, and create XAdES signature in C#.
  headline: How to sign word documents with XAdES EPES in C#
  type: TechArticle
tags:
- digital-signature
- C#
- Word
- XAdES
title: 如何在 C# 中使用 XAdES EPES 对 Word 文档进行签名
url: /zh/net/programming-with-digital-signatures/how-to-sign-word-documents-with-xades-epes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用 XAdES EPES 对 Word 文档进行签名

如果您需要以编程方式 **how to sign word** 文件，本指南为您提供完整的、可投入生产的解决方案。您将学习如何加载 PFX 证书、配置 digital signature docx，并创建可由 Microsoft Word 和第三方验证器验证的 XAdES‑EPES 签名。

示例使用 GroupDocs.Signature for .NET 库，但这些概念适用于任何支持 XAdES 的 API。教程结束时，您将拥有一个已签名的 `Signed_XAdES_EPES.docx`，可供分发。

## 您需要的条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.7+）
- 包含私钥的有效 PFX 证书文件（`.pfx`）
- PFX 文件的密码
- 您想要签名的 Word 文档（`.docx`）
- NuGet 包 **GroupDocs.Signature**（使用 `dotnet add package GroupDocs.Signature` 安装）

## 步骤 1：安装所需的 NuGet 包

```bash
dotnet add package GroupDocs.Signature
```

该包提供 `Document` 类、`XadesSignatureOptions` 类以及用于创建 **digitally sign word** 文件的辅助类型。

## 步骤 2：加载未签名的 Word 文档

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;
using System;
using System.Security.Cryptography.X509Certificates;

...

// Load the original Word file (must be a .docx)
var documentPath = @"C:\Docs\Unsigned.docx";
Document document = new Document(documentPath);
```

加载文档后，您将获得一个对象模型，可在应用签名之前进行操作。

## 步骤 3：加载 PFX 证书（load pfx certificate）

```csharp
// Load the certificate that holds the private key
var certPath = @"C:\Certificates\mycert.pfx";
var certPassword = "yourPassword";          // keep this secret!
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword);
```

> **专业提示：** 如果证书存储在 Windows 证书存储区，您可以使用 `X509Store` 检索，而不是加载文件。`load pfx certificate` 方法在任何平台上均可工作，包括 Linux 容器。

## 步骤 4：（可选）添加可视签名行

可视提示帮助接收者看到签名在 Word 中出现的位置。

```csharp
// Create a signature line that will be displayed in the document
SignatureLine signatureLine = new SignatureLine(document);
signatureLine.Id = Guid.NewGuid().ToString();
signatureLine.Signer = "John Smith";
signatureLine.Title = "Approved";

// Append the line to the first paragraph of the first section
document.FirstSection.Body.FirstParagraph.AppendChild(signatureLine);
```

如果您更倾向于不可见签名，可以跳过此步骤。**digital signature docx** 仍然在密码学上是有效的。

## 步骤 5：配置 XAdES‑EPES 选项（create xades signature）

```csharp
// Set up XAdES‑EPES options – this creates a “qualified” electronic signature
XadesSignatureOptions signOptions = new XadesSignatureOptions
{
    SignatureType = XadesSignatureType.XAdES_EPES,
    // Optional: add a custom signing reason or location
    Reason = "Document approval",
    Location = "New York, USA"
};
```

`XadesSignatureType.XAdES_EPES` 标志指示库根据 EPES（基于显式策略的电子签名）配置嵌入签名，该配置已被欧盟 e‑IDAS 规定广泛接受。

## 步骤 6：应用数字签名

```csharp
// Sign the document with the loaded certificate and options
document.DigitalSignatures.Sign(certificate, signOptions);
```

`Sign` 方法执行所有密码学工作：对文档各部分进行哈希、创建 XML‑DSig 结构，并将 XAdES 包嵌入 Word 文件。

## 步骤 7：保存已签名的文档

```csharp
// Save the signed file – you can overwrite or create a new file
var signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
document.Save(signedPath);
Console.WriteLine($"Document signed and saved to: {signedPath}");
```

保存后，在 Microsoft Word 中打开 `Signed_XAdES_EPES.docx`。您应该能看到签名行（如果您添加了）以及显示文件已签名且签名有效的 **digitally sign word** 状态栏。

## 完整、可运行的示例

下面是完整的程序代码，您可以复制粘贴到控制台应用程序中。

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

namespace WordXadesSigner
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the unsigned Word document
            string docPath = @"C:\Docs\Unsigned.docx";
            Document document = new Document(docPath);

            // 2️⃣ Load the signing certificate (load pfx certificate)
            string pfxPath = @"C:\Certificates\mycert.pfx";
            string pfxPassword = "yourPassword";
            X509Certificate2 cert = new X509Certificate2(pfxPath, pfxPassword);

            // 3️⃣ (Optional) Add a visual signature line
            SignatureLine sigLine = new SignatureLine(document)
            {
                Id = Guid.NewGuid().ToString(),
                Signer = "John Smith",
                Title = "Approved"
            };
            document.FirstSection.Body.FirstParagraph.AppendChild(sigLine);

            // 4️⃣ Configure XAdES‑EPES options (create xades signature)
            XadesSignatureOptions xadesOptions = new XadesSignatureOptions
            {
                SignatureType = XadesSignatureType.XAdES_EPES,
                Reason = "Document approval",
                Location = "New York, USA"
            };

            // 5️⃣ Apply the digital signature (digitally sign word)
            document.DigitalSignatures.Sign(cert, xadesOptions);

            // 6️⃣ Save the signed document
            string signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
            document.Save(signedPath);

            Console.WriteLine($"Signed document saved to: {signedPath}");
        }
    }
}
```

### 预期输出

```
Signed document saved to: C:\Docs\Signed_XAdES_EPES.docx
```

在 Word 中打开文件会显示绿色的 “Signed” 横幅，如果您添加了可视行，签名行会出现在您指定的位置。

## 处理常见问题

| 问题 | 产生原因 | 解决方案 |
|------|----------|----------|
| **证书密码错误** | `X509Certificate2` 构造函数抛出 `CryptographicException`。 | 验证密码，或使用安全的密钥管理服务（Azure Key Vault、AWS Secrets Manager）。 |
| **Word 显示 “Signature is invalid”** | 签名后文档被修改，或缺少签名策略。 | 确保文件在签名 **后** 保存且不再编辑。如监管机构要求，嵌入正确的 XAdES 策略。 |
| **签名行不可见** | 文档使用了不同的节布局。 | 将 `SignatureLine` 追加到正确的段落，或在添加之前创建新段落。 |
| **大型文档性能下降** | XAdES 签名对包的每个部分进行哈希。 | 使用流式 API（`SignAsync`）或为非常大的文件（>50 MB）增加机器资源。 |

## 扩展方案

- **Multiple signers** – 多次使用不同证书调用 `Sign`，并设置 `SignatureId` 以区分每个签署者。  
- **Timestamping** – 将 `TimestampOptions` 对象添加到 `XadesSignatureOptions` 中，以嵌入可信时间戳。  
- **Custom policies** – 通过 `XadesSignatureOptions.PolicyFilePath` 提供 XML 策略文件，以符合特定标准。

## 结论

您现在已经了解如何使用 GroupDocs.Signature 以编程方式 **how to sign word** 文档、如何 **load pfx certificate**，以及如何 **create xades signature**。本教程涵盖了从加载文档到保存已签名输出的每一步，并提供了常见边缘情况的实用技巧。  

接下来，探索相关主题，例如 **digitally sign word** PDF、集成 **digital signature docx** 验证，或添加 **timestamp** 支持以满足高级合规要求。祝签名愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南紧密相关的主题，基于本指南展示的技术。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方法。

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Signing Existing Signature Line In Word Document](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)
- [Access And Verify Signature In Word Document](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}