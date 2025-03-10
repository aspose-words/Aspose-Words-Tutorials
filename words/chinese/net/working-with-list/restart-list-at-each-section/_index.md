---
title: 在每个部分重新启动列表
linktitle: 在每个部分重新启动列表
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文档的每个部分重新启动列表。按照我们详细的分步指南有效地管理列表。
weight: 10
url: /zh/net/working-with-list/restart-list-at-each-section/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在每个部分重新启动列表

## 介绍

创建结构化且组织良好的文档有时感觉就像解决一个复杂的难题。这个难题的一部分是有效地管理列表，特别是当您希望它们在每个部分重新启动时。使用 Aspose.Words for .NET，您可以无缝地实现这一点。让我们深入了解如何使用 Aspose.Words for .NET 在 Word 文档的每个部分重新启动列表。

## 先决条件

在开始之前，请确保您已准备好以下内容：

1.  Aspose.Words for .NET：从以下网站下载并安装最新版本[Aspose 版本](https://releases.aspose.com/words/net/)页。
2. .NET 环境：安装 .NET 后设置您的开发环境。
3. 对 C# 的基本了解：建议熟悉 C# 编程语言。
4.  Aspose 许可证：您可以选择[临时执照](https://purchase.aspose.com/temporary-license/)如果你没有。

## 导入命名空间

在编写代码之前，请确保导入必要的命名空间：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

现在，让我们将该过程分解为多个步骤，以使其易于遵循。

## 步骤 1：初始化文档

首先，您需要创建一个新的文档实例。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
```

## 第 2 步：添加编号列表

接下来，向文档添加编号列表。此列表将遵循默认编号格式。

```csharp
doc.Lists.Add(ListTemplate.NumberDefault);
```

## 步骤 3：访问列表并设置重新启动属性

检索刚刚创建的列表并设置其`IsRestartAtEachSection`财产`true`.这确保列表在每个新部分重新开始编号。

```csharp
List list = doc.Lists[0];
list.IsRestartAtEachSection = true;
```

## 步骤 4：创建文档生成器并关联列表

创建一个`DocumentBuilder`将内容插入文档并将其与列表关联。

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.ListFormat.List = list;
```

## 步骤 5：添加列表项并插入分节符

现在，将项目添加到列表中。为了说明重新启动功能，我们将在一定数量的项目后插入分节符。

```csharp
for (int i = 1; i < 45; i++)
{
    builder.Writeln($"List item {i}");

    if (i == 15)
        builder.InsertBreak(BreakType.SectionBreakNewPage);
}
```

## 步骤 6：保存文档

最后，使用适当的选项保存文档以确保合规。

```csharp
OoxmlSaveOptions options = new OoxmlSaveOptions { Compliance = OoxmlCompliance.Iso29500_2008_Transitional };
doc.Save(dataDir + "WorkingWithList.RestartListAtEachSection.docx", options);		
```

## 结论

就这样！按照这些步骤，您可以使用 Aspose.Words for .NET 轻松地在 Word 文档的每个部分重新启动列表。此功能对于创建结构良好的文档非常有用，这些文档需要单独的部分并带有自己的列表编号。使用 Aspose.Words，处理此类任务变得轻而易举，让您专注于制作高质量的内容。

## 常见问题解答

### 我可以在每个部分为不同列表类型重新启动列表吗？
是的，Aspose.Words for .NET 允许您重新启动各种列表类型，包括项目符号和编号列表。

### 如果我想自定义编号格式怎么办？
您可以通过修改`ListTemplate`创建列表时的属性。

### 列表中项目的数量有限制吗？
不，使用 Aspose.Words for .NET 时列表中的项目数量没有具体限制。

### 我可以在其他文档格式（例如 PDF）中使用此功能吗？
是的，您可以使用 Aspose.Words 将 Word 文档转换为 PDF 等其他格式，同时保留列表结构。

### 如何免费试用 Aspose.Words for .NET？
您可以从[Aspose 版本](https://releases.aspose.com/)页。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
