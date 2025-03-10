---
title: 在 Word 文档中加载加密文件
linktitle: 在 Word 文档中加载加密文档
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 加载和保存加密的 Word 文档。轻松使用新密码保护您的文档。包含分步指南。
weight: 10
url: /zh/net/programming-with-loadoptions/load-encrypted-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文档中加载加密文件

## 介绍

在本教程中，您将学习如何使用 Aspose.Words for .NET 加载加密的 Word 文档并使用新密码保存它。处理加密文档对于维护文档安全至关重要，尤其是在处理敏感信息时。

## 先决条件

开始之前，请确保您已准备好以下物品：

1. 已安装 Aspose.Words for .NET 库。您可以从以下位置下载[这里](https://downloads.aspose.com/words/net).
2. 有效的 Aspose 许可证。您可以免费试用或从以下网站购买[这里](https://purchase.aspose.com/buy).
3. Visual Studio 或任何其他 .NET 开发环境。

## 导入命名空间

首先，确保已将必要的命名空间导入到项目中：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 步骤 1：加载加密文档

首先，您将使用`LoadOptions`类。此类允许您指定打开文档所需的密码。

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENTS DIRECTORY";

//使用指定密码加载加密文档
Document doc = new Document(dataDir + "Encrypted.docx", new LoadOptions("password"));
```

## 步骤 2：使用新密码保存文档

接下来，您将加载的文档保存为 ODT 文件，这次使用`OdtSaveOptions`班级。

```csharp
//使用新密码保存加密文档
doc.Save(dataDir + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newpassword"));
```

## 结论

通过遵循本教程中概述的步骤，您可以使用 Aspose.Words for .NET 轻松加载和保存加密的 Word 文档。这可确保您的文档保持安全，并且只有授权人员才能访问。

## 常见问题解答

### 我可以使用 Aspose.Words 加载和保存其他文件格式吗？
是的，Aspose.Words 支持多种文件格式，包括 DOC、DOCX、PDF、HTML 等。

### 如果我忘记了加密文档的密码该怎么办？
不幸的是，如果您忘记了密码，您将无法加载文档。请确保安全存储密码。

### 是否可以从文档中删除加密？
是的，通过保存文档而不指定密码，您可以删除加密。

### 我可以应用不同的加密设置吗？
是的，Aspose.Words 提供了各种加密文档的选项，包括指定不同类型的加密算法。

### 加密文档的大小有限制吗？
不是，Aspose.Words 可以处理任何大小的文档，但要受到系统内存的限制。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
