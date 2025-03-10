---
title: Word 文档中不受限制的部分
linktitle: Word 文档中不受限制的部分
second_title: Aspose.Words 文档处理 API
description: 按照本分步指南使用 Aspose.Words for .NET 解锁 Word 文档中的特定部分。非常适合保护敏感内容。
weight: 10
url: /zh/net/document-protection/unrestricted-section/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文档中不受限制的部分

## 介绍

大家好！准备好进入 Aspose.Words for .NET 的世界了吗？今天，我们将解决一个非常实用的问题：如何解锁 Word 文档中的特定部分，同时保护其他部分。如果您曾经需要保护文档的某些部分，但保留其他部分以供编辑，那么本教程适合您。让我们开始吧！

## 先决条件

在我们讨论细节之前，请确保您已准备好所需的一切：

-  Aspose.Words for .NET：如果你还没有，你可以[点击下载](https://releases.aspose.com/words/net/).
- Visual Studio：或任何其他与 .NET 兼容的 IDE。
- 对 C# 的基本了解：对 C# 有一点熟悉将帮助您轻松完成本教程。
-  Aspose 许可证：获取[免费试用](https://releases.aspose.com/)或者得到[临时执照](https://purchase.aspose.com/temporary-license/)如果您需要它进行测试。

## 导入命名空间

在开始编码之前，请确保已在 C# 项目中导入了必要的命名空间：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

现在，让我们一步一步地分解！

## 步骤 1：设置你的项目

### 初始化您的文档目录

首先，您需要设置文档目录的路径。这是您的 Word 文件保存的位置。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`替换为您想要保存文档的实际路径。这很重要，因为它可以确保您的文件存储在正确的位置。

### 创建新文档

接下来，我们将使用 Aspose.Words 创建一个新文档。该文档将成为我们施展魔法的画布。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

这`Document`类初始化一个新文档，并且`DocumentBuilder`帮助我们轻松地向文档添加内容。

## 步骤 2：插入部分

### 添加不受保护的部分

让我们首先添加第一部分，该部分将保持不受保护。

```csharp
builder.Writeln("Section 1. Unprotected.");
```

这行代码将文本“第 1 节。不受保护。”添加到文档中。很简单，对吧？

### 添加受保护部分

现在，让我们添加第二个部分并插入分节符以将其与第一个部分分开。

```csharp
builder.InsertBreak(BreakType.SectionBreakContinuous);
builder.Writeln("Section 2. Protected.");
```

这`InsertBreak`方法插入连续的分节符，允许我们对每个节进行不同的设置。

## 步骤 3：保护文档

### 启用文档保护

为了保护文档，我们将使用`Protect`方法。此方法确保只有表单字段可编辑，除非另有规定。

```csharp
doc.Protect(ProtectionType.AllowOnlyFormFields, "password");
```

在这里，文档受密码保护，只有表单字段可以编辑。记得替换`"password"`使用您想要的密码。

### 取消保护特定部分

默认情况下，所有部分都受到保护。我们需要选择性地关闭第一部分的保护。

```csharp
doc.Sections[0].ProtectedForForms = false;
```

此行确保第一部分保持不受保护，同时文档的其余部分受到保护。

## 步骤 4：保存并加载文档

### 保存文档

现在，是时候保存已应用保护设置的文档了。

```csharp
doc.Save(dataDir + "DocumentProtection.UnrestrictedSection.docx");
```

这会将文档保存在指定目录中，名称为`DocumentProtection.UnrestrictedSection.docx`.

### 加载文档

最后，我们加载文档来验证一切设置是否正确。

```csharp
doc = new Document(dataDir + "DocumentProtection.UnrestrictedSection.docx");
```

此步骤可确保文档正确保存并可重新加载而不会丢失保护设置。

## 结论

就这样！按照这些步骤，您已成功使用 Aspose.Words for .NET 创建了一个包含受保护和不受保护部分的 Word 文档。当您需要锁定文档的某些部分而使其他部分可编辑时，此方法非常有用。

## 常见问题解答

### 我可以保护多个部分吗？
是的，您可以根据需要有选择地保护和取消保护多个部分。

### 保存文档后可以更改保护类型吗？
是的，您可以重新打开文档并根据需要修改保护设置。

### Aspose.Words 中还有哪些其他保护类型？
 Aspose.Words 支持多种保护类型，包括`ReadOnly`, `Comments`， 和`TrackedChanges`.

### 我可以不使用密码来保护文档吗？
是的，您无需指定密码即可保护文档。

### 我如何检查某个部分是否受到保护？
您可以检查`ProtectedForForms`属性来确定某个部分是否受到保护。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
