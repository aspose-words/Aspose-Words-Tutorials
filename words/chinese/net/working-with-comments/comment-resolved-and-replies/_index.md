---
title: 评论已解决并回复
linktitle: 评论已解决并回复
second_title: Aspose.Words 文档处理 API
description: 使用 Aspose.Words for .NET 自动解析和回复 Word 文档中的注释。 包含分步指南。
weight: 10
url: /zh/net/working-with-comments/comment-resolved-and-replies/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 评论已解决并回复

## 介绍

如果您正在使用 Word 文档，那么您可能已经处理过评论。它们对于协作非常有用，但管理它们可能很麻烦。使用 Aspose.Words for .NET，您可以自动完成解决和回复评论的过程。本指南将引导您完成执行此操作的步骤。

## 先决条件

在深入研究之前，请确保您已准备好以下事项：

1.  Aspose.Words for .NET：你可以从以下网址下载[这里](https://releases.aspose.com/words/net/).
2. 开发环境：使用.NET Framework 设置。
3. C# 基础知识：熟悉语法和概念。

## 导入命名空间

首先，让我们导入必要的命名空间。这确保我们需要的所有类和方法都随时可用。

```csharp
using Aspose.Words;
using Aspose.Words.Comments;
```

让我们将这个过程分解成简单易懂的步骤。每个步骤都将帮助您理解代码及其功能。

## 步骤 1：加载文档

首先，加载包含注释的 Word 文档。使用`Document`为此课程。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

这行代码初始化了一个新的`Document`对象与您的 Word 文档的路径。

## 第 2 步：检索评论

接下来，我们需要获取文档中的所有评论。我们将使用`GetChildNodes`方法来检索`Comment`节点。

```csharp
NodeCollection comments = doc.GetChildNodes(NodeType.Comment, true);
```

此代码检索文档中的所有评论并将它们存储在`NodeCollection`.

## 步骤 3：访问家长评论

在我们的示例中，我们将重点关注集合中的第一个评论。这将是我们的父评论。

```csharp
Comment parentComment = (Comment)comments[0];
```

在这里，我们将集合中的第一个节点转换为`Comment`目的。

## 步骤 4：循环回复

现在，让我们循环遍历对父评论的回复。我们将使用`foreach`循环迭代每个答复。

```csharp
foreach (Comment childComment in parentComment.Replies)
{
    Console.WriteLine(childComment.Ancestor.Id);
    Console.WriteLine(childComment.Done);

    childComment.Done = true;
}
```

在这个循环中，我们打印祖先评论的 ID 及其状态（是否已完成）。然后，我们将每个回复标记为已完成。

## 步骤 5：保存文档

最后，将修改后的文档保存到您的目录中。

```csharp
doc.Save(dataDir + "WorkingWithComments.CommentResolvedAndReplies.docx");
```

此代码将更改保存到新文档，确保原始文件保持不变。

## 结论

处理 Word 文档中的注释不必是手动操作。使用 Aspose.Words for .NET，您可以自动化该过程，从而节省时间并减少错误。按照本指南操作，可以高效地解决和回复文档中的注释。

## 常见问题解答

### 我可以使用 Aspose.Words for .NET 自动执行其他与评论相关的任务吗？  
是的，您可以自动执行各种任务，例如添加、删除和修改评论。

### Aspose.Words for .NET 是否与 .NET Core 兼容？  
是的，Aspose.Words for .NET 同时支持 .NET Framework 和 .NET Core。

### 如何免费试用 Aspose.Words for .NET？  
您可以从下载免费试用版[这里](https://releases.aspose.com/).

### 我可以使用 Aspose.Words for .NET 处理其他文档类型吗？  
是的，Aspose.Words 支持各种格式，包括 DOCX、PDF、HTML 等。

### 在哪里可以找到 Aspose.Words for .NET 的详细文档？  
您可以访问文档[这里](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
