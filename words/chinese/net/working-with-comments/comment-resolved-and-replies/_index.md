---
"description": "使用 Aspose.Words for .NET 自动解析并回复 Word 文档中的注释。附带分步指南。"
"linktitle": "评论已解决并回复"
"second_title": "Aspose.Words文档处理API"
"title": "评论已解决并回复"
"url": "/zh/net/working-with-comments/comment-resolved-and-replies/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 评论已解决并回复

## 介绍

如果您正在使用 Word 文档，您可能处理过注释。注释对于协作非常有用，但管理起来却很麻烦。使用 Aspose.Words for .NET，您可以自动化处理和回复注释的过程。本指南将引导您完成操作步骤。

## 先决条件

在深入研究之前，请确保您已具备以下条件：

1. Aspose.Words for .NET：您可以从 [这里](https://releases。aspose.com/words/net/).
2. 开发环境：使用.NET Framework设置。
3. C# 基础知识：熟悉语法和概念。

## 导入命名空间

首先，让我们导入必要的命名空间。这确保我们需要的所有类和方法都随时可用。

```csharp
using Aspose.Words;
using Aspose.Words.Comments;
```

让我们将这个过程分解成几个简单易懂的步骤。每个步骤都能帮助你理解代码及其功能。

## 步骤 1：加载文档

首先，加载包含注释的 Word 文档。使用 `Document` 为此课程。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

这行代码初始化了一个新的 `Document` 对象以及您的 Word 文档的路径。

## 第 2 步：检索评论

接下来，我们需要获取文档中的所有评论。我们将使用 `GetChildNodes` 方法来检索 `Comment` 节点。

```csharp
NodeCollection comments = doc.GetChildNodes(NodeType.Comment, true);
```

此代码检索文档中的所有注释并将其存储在 `NodeCollection`。

## 步骤 3：访问家长评论

在我们的示例中，我们将关注集合中的第一条评论。这将是我们的父评论。

```csharp
Comment parentComment = (Comment)comments[0];
```

在这里，我们将集合中的第一个节点转换为 `Comment` 目的。

## 步骤 4：循环回复

现在，让我们循环遍历父评论的回复。我们将使用 `foreach` 循环迭代每个回复。

```csharp
foreach (Comment childComment in parentComment.Replies)
{
    Console.WriteLine(childComment.Ancestor.Id);
    Console.WriteLine(childComment.Done);

    childComment.Done = true;
}
```

在这个循环中，我们打印祖先评论的 ID 及其状态（无论是否完成）。然后，我们将每个回复标记为已完成。

## 步骤5：保存文档

最后，将修改后的文档保存到您的目录中。

```csharp
doc.Save(dataDir + "WorkingWithComments.CommentResolvedAndReplies.docx");
```

此代码将更改保存到新文档，确保原始文件保持不变。

## 结论

处理 Word 文档中的注释不再是一项繁琐的手动工作。使用 Aspose.Words for .NET，您可以自动化这一流程，节省时间并减少错误。按照本指南操作，即可高效地处理和回复文档中的注释。

## 常见问题解答

### 我可以使用 Aspose.Words for .NET 自动执行其他与评论相关的任务吗？  
是的，您可以自动执行各种任务，例如添加、删除和修改评论。

### Aspose.Words for .NET 是否与 .NET Core 兼容？  
是的，Aspose.Words for .NET 同时支持 .NET Framework 和 .NET Core。

### 如何免费试用 Aspose.Words for .NET？  
您可以从下载免费试用版 [这里](https://releases。aspose.com/).

### 我可以使用 Aspose.Words for .NET 处理其他文档类型吗？  
是的，Aspose.Words 支持各种格式，包括 DOCX、PDF、HTML 等。

### 在哪里可以找到 Aspose.Words for .NET 的详细文档？  
您可以访问文档 [这里](https://reference。aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}