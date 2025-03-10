---
title: 在 Word 文档中显示隐藏书签内容
linktitle: 在 Word 文档中显示隐藏书签内容
second_title: Aspose.Words 文档处理 API
description: 通过本详细的分步指南了解如何使用 Aspose.Words for .NET 显示和隐藏 Word 文档中的书签内容。
weight: 10
url: /zh/net/programming-with-bookmarks/show-hide-bookmarked-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文档中显示隐藏书签内容

## 介绍

准备好使用 Aspose.Words for .NET 深入文档操作的世界了吗？无论您是希望自动化文档任务的开发人员，还是只是对以编程方式处理 Word 文件感到好奇的人，您都来对地方了。今天，我们将探索如何使用 Aspose.Words for .NET 在 Word 文档中显示和隐藏书签内容。本分步指南将使您成为基于书签控制内容可见性的专家。让我们开始吧！

## 先决条件

在我们讨论细节之前，您需要准备一些东西：

1. Visual Studio：任何与 .NET 兼容的版本。
2.  Aspose.Words for .NET：下载[这里](https://releases.aspose.com/words/net/).
3. 对 C# 的基本了解：如果您可以编写一个简单的“Hello World”程序，那么就可以开始了。
4. 带有书签的 Word 文档：在本教程中，我们将使用带有书签的示例文档。

## 导入命名空间

首先，让我们导入必要的命名空间。这确保我们拥有完成任务所需的所有工具。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

有了这些命名空间，我们就可以开始我们的旅程了。

## 步骤 1：设置项目

好的，让我们首先在 Visual Studio 中设置我们的项目。

### 创建新项目

打开 Visual Studio 并创建一个新的控制台应用程序（.NET Core）项目。将其命名为一些吸引人的名字，例如“BookmarkVisibilityManager”。

### 添加 Aspose.Words for .NET

您需要将 Aspose.Words for .NET 添加到您的项目中。您可以通过 NuGet 包管理器执行此操作。

1. 转到工具>NuGet 包管理器>管理解决方案的 NuGet 包。
2. 搜索“Aspose.Words”。
3. 安装该包。

太棒了！现在我们的项目已经设置好了，让我们继续加载我们的文档。

## 步骤 2：加载文档

我们需要加载包含书签的 Word 文档。在本教程中，我们将使用名为“Bookmarks.docx”的示例文档。

```csharp
//文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

此代码片段设置文档目录的路径，并将文档加载到`doc`目的。

## 步骤 3：显示/隐藏已加书签的内容

现在到了有趣的部分——根据书签显示或隐藏内容。我们将创建一个名为`ShowHideBookmarkedContent`来处理这个问题。

以下方法可以切换书签内容的可见性：

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### 方法详解

- 书签检索：`Bookmark bm = doc.Range.Bookmarks[bookmarkName];`获取书签。
- 节点遍历：我们遍历书签内的节点。
- 可见性切换：如果节点是`Run`（连续的文本），我们将其设置为`Hidden`财产。

## 步骤 4：应用该方法

有了我们的方法，让我们应用它来根据书签显示或隐藏内容。

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

这行代码将隐藏名为“MyBookmark1”的书签内的内容。

## 步骤5：保存文档

最后，让我们保存修改后的文档。

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

这将保存我们所做更改的文档。

## 结论

就这样！您刚刚学会了如何使用 Aspose.Words for .NET 显示和隐藏 Word 文档中的书签内容。无论您是自动化报告、创建模板还是只是修改 Word 文件，这款功能强大的工具都让文档操作变得轻而易举。祝您编码愉快！

## 常见问题解答

### 我可以一次切换多个书签吗？
是的，您可以致电`ShowHideBookmarkedContent`方法。

### 隐藏内容会影响文档的结构吗？
不会，隐藏内容只会影响其可见性。内容仍保留在文档中。

### 我可以将此方法用于其他类型的内容吗？
此方法专门用于切换文本运行。对于其他内容类型，您需要修改节点遍历逻辑。

### Aspose.Words for .NET 免费吗？
 Aspose.Words 提供免费试用[这里](https://releases.aspose.com/)，但生产使用需要完整许可证。您可以购买[这里](https://purchase.aspose.com/buy).

### 如果我遇到问题，如何获得支持？
您可以从 Aspose 社区获得支持[这里](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
