---
title: 管理数字签名和真实性
linktitle: 管理数字签名和真实性
second_title: Aspose.Words Python 文档管理 API
description: 了解如何使用 Aspose.Words for Python 管理数字签名并确保文档真实性。带有源代码的分步指南。
weight: 17
url: /zh/python-net/document-combining-and-comparison/manage-digital-signatures/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 管理数字签名和真实性

## 数字签名简介

数字签名相当于手写签名的电子版本。它们提供了一种验证电子文档真实性、完整性和来源的方法。对文档进行数字签名时，会根据文档内容生成加密哈希。然后使用签名者的私钥加密此哈希，从而创建数字签名。任何拥有相应公钥的人都可以验证签名并确定文档的真实性。

## 为 Python 设置 Aspose.Words

要开始使用 Aspose.Words for Python 管理数字签名，请按照以下步骤操作：

1. 安装 Aspose.Words：您可以使用 pip 使用以下命令安装 Aspose.Words for Python：
   
   ```python
   pip install aspose-words
   ```

2. 导入所需模块：在 Python 脚本中导入必要的模块：
   
   ```python
   import aspose.words as aw
   ```

## 加载和访问文档

在添加或验证数字签名之前，您需要使用 Aspose.Words 加载文档：

```python
document = aw.Document("document.docx")
```

## 向文档添加数字签名

要向文档添加数字签名，您需要一个数字证书：

```python
certificate_holder = aw.digitalsignatures.CertificateHolder.create("certificate.pfx", "password")
```

现在，签署文件：

```python
aw.digitalsignatures.DigitalSignatureUtil.sign(MY_DIR + "Digitally signed.docx",
            ARTIFACTS_DIR + "Document.encrypted_document.docx", cert_holder, sign_options)
```

## 验证数字签名

使用 Aspose.Words 验证签名文档的真实性：

```python
for signature in document.digital_signatures:
    if signature.is_valid:
        print("Signature is valid.")
    else:
        print("Signature is invalid.")
```

## 自定义数字签名的外观

您可以自定义数字签名的外观：

```python
sign_options = aw.digitalsignatures.SignOptions()
sign_options.comments = 'Comment'
sign_options.sign_time = datetime.datetime.now()
```

## 结论

在当今的数字环境中，管理数字签名和确保文档真实性至关重要。Aspose.Words for Python 简化了添加、验证和自定义数字签名的过程，使开发人员能够增强其文档的安全性和可信度。

## 常见问题解答

### 数字签名如何工作？

数字签名使用加密技术根据文档内容生成唯一的哈希值，并使用签名者的私钥加密。

### 数字签名的文档会被篡改吗？

不，篡改数字签名的文档将导致签名无效，从而可能存在未经授权的更改。

### 一份文件可以添加多个签名吗？

是的，您可以向一份文档添加多个数字签名，每个签名都来自不同的签名者。

### 哪些类型的证书兼容？

Aspose.Words 支持 X.509 证书，包括 PFX 文件，常用于数字签名。

### 数字签名具有法律效力吗？

是的，数字签名在许多国家具有法律效力，并且通常被认为等同于手写签名。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
