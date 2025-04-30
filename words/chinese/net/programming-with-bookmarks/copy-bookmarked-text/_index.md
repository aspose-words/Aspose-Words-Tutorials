---
"description": "使用 Aspose.Words for .NET 轻松在 Word 文档之间复制已添加书签的文本。通过本分步指南学习如何操作。"
"linktitle": "在 Word 文档中复制书签文本"
"second_title": "Aspose.Words文档处理API"
"title": "在 Word 文档中复制书签文本"
"url": "/zh/net/programming-with-bookmarks/copy-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文档中复制书签文本

## 介绍

您是否曾经需要将特定部分从一个 Word 文档复制到另一个 Word 文档？好吧，您很幸运！在本教程中，我们将指导您如何使用 Aspose.Words for .NET 将书签文本从一个 Word 文档复制到另一个 Word 文档。无论您是要构建动态报表还是自动生成文档，本指南都能为您简化流程。

## 先决条件

在深入研究之前，请确保您具备以下条件：

- Aspose.Words for .NET Library：您可以从 [这里](https://releases。aspose.com/words/net/).
- 开发环境：Visual Studio 或任何其他 .NET 开发环境。
- C#基础知识：熟悉C#编程和.NET框架。

## 导入命名空间

首先，确保您已在项目中导入必要的命名空间：

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## 步骤 1：加载源文档

首先，您需要加载包含要复制的书签文本的源文档。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

这里， `dataDir` 是文档目录的路径，并且 `Bookmarks.docx` 是源文档。

## 第 2 步：识别书签

接下来，确定您想要从源文档复制的书签。

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

代替 `"MyBookmark1"` 使用您的书签的实际名称。

## 步骤 3：创建目标文档

现在，创建一个新文档，将书签文本复制到其中。

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## 步骤 4：导入书签内容

为了确保样式和格式得以保留，请使用 `NodeImporter` 将源文档中的书签内容导入目标文档。

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## 步骤5：定义AppendBookmarkedText方法

神奇的事情就在这里发生。定义一个方法来处理书签文本的复制：

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## 步骤 6：保存目标文档

最后，保存目标文档以验证复制的内容。

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## 结论

就这样！您已成功使用 Aspose.Words for .NET 将书签文本从一个 Word 文档复制到另一个文档。此方法功能强大，可自动执行文档操作任务，使您的工作流程更加高效、流畅。

## 常见问题解答

### 我可以一次复制多个书签吗？
是的，您可以遍历多个书签并使用相同的方法复制每个书签。

### 如果找不到书签会发生什么？
这 `Range.Bookmarks` 财产将归还 `null`，因此请确保处理这种情况以避免出现异常。

### 我可以保留原始书签的格式吗？
当然！使用 `ImportFormatMode.KeepSourceFormatting` 确保保留原始格式。

### 书签文本的大小有限制吗？
没有具体的限制，但对于极大的文档，性能可能会有所不同。

### 我可以在不同的 Word 文档格式之间复制文本吗？
是的，Aspose.Words 支持各种 Word 格式，并且该方法适用于这些格式。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}