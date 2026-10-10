---
category: general
date: 2026-10-10
description: 在 Java 中创建签名选项并使用 XAdES EPES 对 Word 文档进行签名。通过几个清晰的步骤学习如何使用证书对 Office
  文档进行签名。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: zh
lastmod: 2026-10-10
og_description: 在 Java 中创建签名选项并使用 XAdES EPES 对 Word 文档进行签名。本指南展示了如何使用证书安全地对 Office
  文档进行签名。
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: 创建签名选项并使用 XAdES EPES 对 Word 文档进行签名
schemas:
- author: GroupDocs
  dateModified: '2026-10-10'
  description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  headline: Create signature options and sign a Word doc with XAdES EPES
  type: TechArticle
- description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  name: Create signature options and sign a Word doc with XAdES EPES
  steps:
  - name: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
    text: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
  - name: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
    text: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
  - name: The signature is embedded into the DOCX package, preserving the original
      document layout.
    text: The signature is embedded into the DOCX package, preserving the original
      document layout.
  - name: Open `SignedXades.docx` in Word.
    text: Open `SignedXades.docx` in Word.
  - name: Click **File → Info → View signatures**.
    text: Click **File → Info → View signatures**.
  - name: Word should display a green checkmark indicating a valid digital signature.
    text: Word should display a green checkmark indicating a valid digital signature.
  type: HowTo
tags:
- digital signature
- Java
- XAdES
title: 创建签名选项并使用 XAdES EPES 对 Word 文档进行签名
url: /zh/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建签名选项并使用 XAdES EPES 对 Word 文档进行签名

如果您需要 **创建签名选项** 用于 DOCX 文件，本指南将展示如何在 Java 中使用 XAdES‑EPES 级别对 Word 文档进行签名。您将获得一个完整、可运行的示例，仅需几行代码即可使用 PFX 证书对 Office 文档进行签名。

对 Office 文档进行签名是法律工作流、自动化合同处理以及安全文档交换的常见需求。在本教程中，您将学习：

* 如何为 XAdES‑EPES 配置 `SignatureOptions`。
* 如何调用 `DigitalSignatureUtil.sign` 来 **签署 word doc** 文件。
* 如何处理常见的陷阱，如证书加载和密码错误。

> **前置条件** – Java 17 或更高版本、GroupDocs.Signature for Java 库（或兼容的 XAdES 库），以及有效的 `.pfx` 证书文件。

---

## 您需要的内容

| 项目 | 原因 |
|------|--------|
| Java 17+ | 现代语言特性和更好的安全 API |
| GroupDocs.Signature for Java（或等效库） | 提供 `SignatureOptions`、`XmlDsigLevel` 和 `DigitalSignatureUtil` |
| PFX 证书（`.pfx`） | 为数字签名提供私钥 |
| 证书密码 | 用于解锁私钥 |
| 未签名的 DOCX 文件（`Unsigned.docx`） | 您想要 **签署 office 文档** 的源文件 |

确保库 JAR 已加入 classpath：

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

---

## 第一步：导入所需类

首先导入处理签名和文件 I/O 的类。

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

这些导入让您能够访问用于 **创建签名选项** 的 API 并执行实际的签名操作。

---

## 第二步：创建签名选项

`SignatureOptions` 对象保存签名过程所需的所有配置，例如签名级别、可视外观和时间戳设置。

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

创建一个全新的 `SignatureOptions` 实例是 **如何签署 docx** 文件的第一步，因为它可以将每个签名请求隔离，防止跨文档的副作用。

---

## 第三步：指定 XAdES EPES 签名级别

XAdES‑EPES（基于显式策略的电子签名）是 Office 文档签名的广泛接受的策略。设置级别告诉库使用哪种加密配置文件。

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

为什么选择 XAdES‑EPES？它将签名策略直接嵌入签名中，使签署的文档自包含并符合众多电子签名法规。

---

## 第四步：签署 DOCX 文件

现在调用 `DigitalSignatureUtil.sign`。该方法读取源文件、应用签名并写入签名后的输出。

```java
// Step 4: Sign the document using the provided certificate
try {
    DigitalSignatureUtil.sign(
        "YOUR_DIRECTORY/Unsigned.docx",   // input file
        "YOUR_DIRECTORY/SignedXades.docx", // output file
        "YOUR_DIRECTORY/mycert.pfx",      // certificate file
        "password",                       // certificate password
        signatureOptions                  // options configured above
    );
    System.out.println("Document signed successfully: SignedXades.docx");
} catch (IOException e) {
    System.err.println("Failed to sign the document: " + e.getMessage());
}
```

**内部发生了什么？**  
1. 库加载 `.pfx` 文件并使用提供的密码提取私钥。  
2. 创建符合 XAdES‑EPES 配置的 XML‑DSig 结构。  
3. 将签名嵌入 DOCX 包中，保持原始文档布局不变。  

如果证书密码错误或文件无法读取，将抛出 `IOException`，请按示例进行处理。

---

## 第五步：验证签名文档（可选）

签署后，您可能想确认签名是否存在且有效。GroupDocs 提供验证 API，但也可以通过 Microsoft Word 手动快速检查：

1. 在 Word 中打开 `SignedXades.docx`。  
2. 点击 **文件 → 信息 → 查看签名**。  
3. Word 应显示绿色对勾，表示数字签名有效。

使用库进行自动化验证的代码如下：

```java
import com.groupdocs.signature.VerificationResult;

VerificationResult result = DigitalSignatureUtil.verify(
    "YOUR_DIRECTORY/SignedXades.docx",
    signatureOptions
);

if (result.isSuccessful()) {
    System.out.println("Signature verification succeeded.");
} else {
    System.out.println("Signature verification failed: " + result.getErrorMessage());
}
```

运行验证步骤可让您以编程方式确认 **签署 office 文档** 已成功。

---

## 完整、可运行的示例

将所有代码片段组合在一起，下面是一个可自行复制、粘贴并运行的 Java 类。

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import com.groupdocs.signature.VerificationResult;
import java.io.IOException;

/**
 * Demonstrates how to create signature options and sign a DOCX file with XAdES EPES.
 */
public class XadesSignatureDemo {

    public static void main(String[] args) {
        // Paths – update these to match your environment
        String inputPath = "YOUR_DIRECTORY/Unsigned.docx";
        String outputPath = "YOUR_DIRECTORY/SignedXades.docx";
        String certPath = "YOUR_DIRECTORY/mycert.pfx";
        String certPassword = "password";

        // 1️⃣ Create signature options
        SignatureOptions signatureOptions = new SignatureOptions();

        // 2️⃣ Set XAdES EPES level
        signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 3️⃣ Sign the document
        try {
            DigitalSignatureUtil.sign(inputPath, outputPath, certPath, certPassword, signatureOptions);
            System.out.println("Document signed successfully: " + outputPath);
        } catch (IOException e) {
            System.err.println("Signing failed: " + e.getMessage());
            return;
        }

        // 4️⃣ (Optional) Verify the signature
        VerificationResult verification = DigitalSignatureUtil.verify(outputPath, signatureOptions);
        if (verification.isSuccessful()) {
            System.out.println("Signature verification succeeded.");
        } else {
            System.out.println("Signature verification failed: " + verification.getErrorMessage());
        }
    }
}
```

**预期输出**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

如果出现任何问题，控制台会显示明确的错误信息，帮助您排查证书或文件路径相关的问题。

---

## 常见问题与边缘情况处理

| 问题 | 解答 |
|----------|--------|
| **我可以使用其他签名级别吗？** | 可以。将 `XmlDsigLevel.XAdES_EPES` 替换为 `XAdES_BES`、`XAdES_T` 等，具体取决于合规需求。 |
| **如果我的证书存放在 keystore 而不是 .pfx 文件中怎么办？** | 手动加载 `KeyStore`，提取 `PrivateKey` 和 `Certificate`，然后将它们传递给接受 `KeyStore` 对象的 `sign` 重载方法。 |
| **如何添加可见的签名图片？** | 在调用 `sign` 之前使用 `signatureOptions.setSignatureImage("path/to/image.png")`。 |
| **签名过程是否线程安全？** | `DigitalSignatureUtil.sign` 方法是无状态的；只要每个线程使用自己的 `SignatureOptions` 实例，就可以安全地并发调用。 |
| **如果 DOCX 已经包含签名怎么办？** | 库会在签名包中追加新条目，保留已有签名。请确认签名策略允许多重签名（如有需要）。 |

---

## 提示与最佳实践（E‑E‑A‑T）

* **专业提示：** 将证书密码存放在安全金库（如 Azure Key Vault）中，而不是硬编码。  
* **注意：** Windows 的文件路径分隔符是 (`\`) 而 Unix 为 (`/`)。使用 `Paths.get(...)` 构建平台无关的路径。  
* **性能：** 对大型 DOCX 文件进行签名可能受 I/O 限制；如果批量处理大量文档，考虑使用流式输入。  
* **合规性：** XAdES‑EPES 符合欧盟 eIDAS 法规；在选择签名级别前请确认本地法律要求。

---

## 结论

本教程教您如何使用 Java 的 XAdES‑EPES 级别 **创建签名选项** 并 **签署 Word 文档**。完整示例涵盖证书加载、选项配置、签名调用以及可选的验证步骤，为您在生产环境中实现 **如何签署 docx** 文件提供了即用的解决方案。

## 接下来您可以学习什么？

以下教程与本指南紧密相关，帮助您进一步掌握 API 功能并探索替代实现方式：

- [Create Load Options in Java – Detect Missing Fonts & How to Load DOCX](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [How to Create Editable Ranges in Read-Only Documents Using Aspose.Words for Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}