---
"date": "2025-03-28"
"description": "了解如何使用 Aspose.Words 将数字签名功能无缝集成到您的 Java 应用程序中。本指南涵盖数字签名的加载、验证、签名和删除。"
"title": "使用 Aspose.Words 掌握 Java 中的数字签名——综合指南"
"url": "/zh/java/security-protection/master-digital-signatures-aspose-words-java/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# 使用 Aspose.Words API 掌握 Java 中的数字签名

数字签名对于安全文档处理、确保真实性和完整性至关重要。Aspose.Words for Java 库支持将数字签名功能无缝集成到您的应用程序中。本指南将指导您使用 Aspose.Words for Java 加载、验证、签名和删除数字签名。

## 介绍

在当今数字化的世界里，文档安全比以往任何时候都更加重要。无论是处理合同、报告还是官方文件，确保其真实性都至关重要。借助 Aspose.Words Java 库，您可以高效地管理 Java 应用程序中的数字签名。本指南将帮助您掌握使用 Aspose.Words 处理数字签名的方法，涵盖加载和验证现有签名、签署新文档以及在必要时删除签名。

**您将学到什么：**
- 如何从文件和流加载数字签名。
- 验证数字签名文档的技术。
- 在 Java 应用程序中添加和删除数字签名的步骤。
- 处理带有数字签名的加密文档的最佳实践。

让我们深入了解开始所需的先决条件！

## 先决条件

要遵循本教程，您需要：

- **Java 开发工具包 (JDK)：** 确保您的系统上安装了 JDK 8 或更高版本。
- **Aspose.Words库：** 您将使用 Aspose.Words for Java 版本 25.3。
- **Maven 或 Gradle 构建工具：** 本指南包含 Maven 和 Gradle 用户的依赖信息。
- **对 Java I/O 操作的基本了解：** 熟悉 Java 中的文件处理至关重要。

## 设置 Aspose.Words

首先，请确保已设置必要的依赖项。以下是使用 Maven 或 Gradle 添加 Aspose.Words 的方法：

**Maven：**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle：**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### 许可证获取

Aspose.Words 是一个商业库，但您可以先免费试用或申请临时许可证来探索其全部功能。

1. **免费试用：** 从以下位置下载 Aspose.Words JAR [这里](https://releases.aspose.com/words/java/) 并将其包含在您的项目中。
2. **临时执照：** 访问以下网址获取完全访问权限的临时许可证 [此链接](https://purchase。aspose.com/temporary-license/).
3. **购买：** 如需长期使用，请考虑从 [Aspose的购买页面](https://purchase。aspose.com/buy).

### 基本初始化

设置好库后，请在 Java 应用程序中初始化它：

```java
// 确保在获得许可证后包含此行
com.aspose.words.License license = new com.aspose.words.License();
license.setLicense("path/to/your/license/file");
```

## 实施指南

本节针对您要实现的每个功能分为几个逻辑步骤。

### 从文件加载签名

#### 概述

从文件加载数字签名可确保文档自签名以来未被更改。此步骤可验证文档是否经过数字签名，并有助于维护其完整性。

**步骤 1：导入所需的类**

```java
import com.aspose.words.DigitalSignatureCollection;
import com.aspose.words.DigitalSignatureUtil;
```

**步骤 2：从文件路径加载签名**

```java
DigitalSignatureCollection digitalSignatures =
        DigitalSignatureUtil.loadSignatures("YOUR_DOCUMENT_DIRECTORY/Digitally signed.docx");

if (digitalSignatures.getCount() > 0) {
    System.out.println("Document is digitally signed.");
}
```

**解释：** 这 `loadSignatures` 方法检索指定文档中的所有签名。集合的计数有助于确定是否存在任何签名。

### 从流中加载签名

#### 概述

使用流加载签名提供了灵活性，特别是在处理未存储在磁盘上的文档时。

**步骤 1：导入所需的类**

```java
import java.io.FileInputStream;
import java.io.InputStream;
```

**步骤 2：创建输入流并加载签名**

```java
InputStream stream = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/Digitally signed.docx");
try {
    DigitalSignatureCollection digitalSignatures =
            DigitalSignatureUtil.loadSignatures(stream);

    if (digitalSignatures.getCount() > 0) {
        System.out.println("Document is digitally signed.");
    }
} finally {
    if (stream != null) stream.close();
}
```

**解释：** 此方法演示了如何通过 InputStream 读取文档，从而允许您处理来自各种来源的文件。

### 使用文件路径删除所有签名

#### 概述

撤销先前的批准或修改文档内容时可能需要删除数字签名。

**步骤 1：导入所需类**

```java
import com.aspose.words.DigitalSignatureUtil;
```

**第 2 步：使用 `removeAllSignatures` 方法**

```java
DigitalSignatureUtil.removeAllSignatures(
        "YOUR_DOCUMENT_DIRECTORY/Digitally signed.docx",
        "YOUR_OUTPUT_DIRECTORY/UnsignedDocument.docx");
```

**解释：** 此命令清除指定文档中的所有数字签名并将其保存为新文件。

### 使用流删除所有签名

#### 概述

对于需要基于流的处理的应用程序，通过 InputStream 和 OutputStream 删除签名会很有利。

**步骤 1：导入所需的类**

```java
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.InputStream;
import java.io.OutputStream;
```

**步骤 2：使用流删除签名**

```java
InputStream streamIn = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/Digitally signed.docx");
try {
    OutputStream streamOut = new FileOutputStream(
            "YOUR_OUTPUT_DIRECTORY/UnsignedDocumentFromStream.docx");

    try {
        DigitalSignatureUtil.removeAllSignatures(streamIn, streamOut);
    } finally {
        if (streamOut != null) streamOut.close();
    }
} finally {
    if (streamIn != null) streamIn.close();
}
```

**解释：** 这种方法允许您动态处理文档，而无需直接访问文件系统。

### 签署文件

#### 概述

对文档进行数字签名对于验证其来源和完整性至关重要。此步骤涉及使用以 PKCS#12 格式存储的 X.509 证书。

**步骤 1：导入所需的类**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;
import java.util.Date;
```

**步骤 2：创建证书持有者并签署文档**

```java
CertificateHolder certificateHolder = CertificateHolder.create(
        "YOUR_DOCUMENT_DIRECTORY/morzal.pfx", "aw");

SignOptions signOptions = new SignOptions();
signOptions.setComments("My comment");
signOptions.setSignTime(new Date());

InputStream streamIn = new FileInputStream(
        "YOUR_DOCUMENT_DIRECTORY/Document.docx");
try {
    OutputStream streamOut = new FileOutputStream(
            "YOUR_OUTPUT_DIRECTORY/SignedDocument.docx");

    try {
        DigitalSignatureUtil.sign(streamIn, streamOut, certificateHolder, signOptions);
    } finally {
        if (streamOut != null) streamOut.close();
    }
} finally {
    if (streamIn != null) streamIn.close();
}
```

**解释：** 这 `create` 方法根据 PKCS#12 文件初始化一个 CertificateHolder。SignOptions 类允许您指定其他签名详细信息。

### 签署加密文档

#### 概述

签署加密文档需要先解密，这可以通过在签名选项中设置解密密码来实现。

**步骤 1：导入所需的类**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;
import java.util.Date;
```

**步骤2：使用解密密码对加密文档进行签名**

```java
CertificateHolder certificateHolder = CertificateHolder.create(
        "YOUR_DOCUMENT_DIRECTORY/morzal.pfx", "aw");

SignOptions signOptions = new SignOptions();
signOptions.setComments("My comment on encrypted document");
signOptions.setDecryptionPassword("your-password-here");
signOptions.setSignTime(new Date());

InputStream streamIn = new FileInputStream(
        "YOUR_DOCUMENT_DIRECTORY/EncryptedDocument.docx");
try {
    OutputStream streamOut = new FileOutputStream(
            "YOUR_OUTPUT_DIRECTORY/SignedEncryptedDocument.docx");

    try {
        DigitalSignatureUtil.sign(streamIn, streamOut, certificateHolder, signOptions);
    } finally {
        if (streamOut != null) streamOut.close();
    }
} finally {
    if (streamIn != null) streamIn.close();
}
```

**解释：** 签署加密文档时，在 `SignOptions` 允许 Aspose.Words 解密并签署文档。

## 最佳实践

- **保护您的证书：** 始终保证证书的安全并避免在代码中硬编码密码。
- **版本兼容性：** 通过彻底测试确保与不同版本的 Aspose.Words 兼容。
- **错误处理：** 实施强大的错误处理来管理签名过程中的异常。
- **测试：** 定期测试您的实施以确保可靠性和安全性。

通过遵循本指南，您可以使用 Aspose.Words 将数字签名功能有效地集成到您的 Java 应用程序中。

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}