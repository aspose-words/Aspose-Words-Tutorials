---
"description": "通过我们详细的分步指南，学习如何使用 Aspose.Words for .NET 将一个 Word 文档无缝插入到另一个 Word 文档中。非常适合希望简化文档处理的开发人员。"
"linktitle": "在替换处插入文档"
"second_title": "Aspose.Words文档处理API"
"title": "在替换处插入文档"
"url": "/zh/net/clone-and-combine-documents/insert-document-at-replace/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在替换处插入文档

## 介绍

嗨，文档大师们！您是否曾经深陷代码泥潭，苦苦思索如何将一个 Word 文档无缝插入另一个文档？别担心，今天我们将深入探索 Aspose.Words for .NET 的世界，让这项任务变得轻而易举。我们将逐步讲解如何使用这个强大的库在查找和替换操作的特定位置插入文档。准备好成为 Aspose.Words 的专家了吗？让我们开始吧！

## 先决条件

在我们进入代码之前，您需要做好以下几件事：

- Visual Studio：请确保您的计算机上已安装 Visual Studio。如果您还没有安装，可以从 [这里](https://visualstudio。microsoft.com/).
- Aspose.Words for .NET：您需要 Aspose.Words 库。您可以从 [Aspose 网站](https://releases。aspose.com/words/net/).
- 基本 C# 知识：对 C# 和 .NET 的基本了解将帮助您学习本教程。

好了，解决了这些问题之后，让我们开始编写一些代码吧！

## 导入命名空间

首先，我们需要导入使用 Aspose.Words 所需的命名空间。这就像在开始项目之前准备好所有工具一样。在 C# 文件的顶部添加以下 using 指令：

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

现在我们已经满足了先决条件，让我们将整个过程分解成几个小步骤。每一步都至关重要，它们将帮助我们更接近目标。

## 步骤 1：设置文档目录

首先，我们需要指定文档的存储目录。这就像大型演出前的准备工作一样。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替 `"YOUR DOCUMENT DIRECTORY"` 指向目录的路径。这是您的文档的存放位置。

## 步骤 2：加载主文档

接下来，我们加载要插入另一个文档的主文档。这可以视为所有操作发生的主阶段。

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

此代码从指定目录加载主文档。

## 步骤 3：设置查找和替换选项

为了找到文档插入的具体位置，我们使用查找和替换功能。这就像使用地图来找到新添加内容的准确位置一样。

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

在这里，我们将方向设置为向后，并指定接下来定义的自定义回调处理程序。

## 步骤4：执行替换操作

现在，我们告诉主文档查找特定的占位符文本并将其替换为空，同时使用自定义回调插入另一个文档。

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

此代码执行查找和替换操作，然后保存更新的文档。

## 步骤 5：创建自定义替换回调处理程序

我们的自定义回调处理程序正是奇迹发生的地方。该处理程序将定义在查找和替换操作期间如何执行文档插入。

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // 在包含匹配文本的段落后插入文档。
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // 删除包含匹配文本的段落。
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

在这里，我们加载要插入的文档，然后调用辅助方法来执行插入。

## 步骤6：定义插入文档方法

我们的难题的最后一部分是将文档实际插入指定位置的方法。

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // 检查插入目标是否为段落或表格
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // 创建 NodeImporter 以从源文档导入节点
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // 循环遍历源文档各部分中的所有块级节点
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // 跳过章节的最后一个空白段落
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // 导入节点并将其插入到目标中
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

此方法负责从要插入的文档中导入节点并将它们放置在主文档中的正确位置。

## 结论

就是这样！这是使用 Aspose.Words for .NET 将一个文档插入另一个文档的全面指南。按照以下步骤，您可以轻松地自动化文档组装和操作任务。无论您是构建文档管理系统，还是仅仅需要简化文档处理工作流程，Aspose.Words 都是您值得信赖的伙伴。

## 常见问题解答

### 什么是 Aspose.Words for .NET？
Aspose.Words for .NET 是一个功能强大的库，用于以编程方式操作 Word 文档。它允许您轻松地创建、修改、转换和处理 Word 文档。

### 我可以一次插入多个文档吗？
是的，您可以修改回调处理程序，通过遍历文档集合来处理多个插入。

### 有免费试用吗？
当然！你可以从 [这里](https://releases。aspose.com/).

### 如何获得 Aspose.Words 的支持？
您可以通过访问 [Aspose.Words论坛](https://forum。aspose.com/c/words/8).

### 我可以保留插入文档的格式吗？
是的， `NodeImporter` 类允许您指定在从一个文档向另一个文档导入节点时如何处理格式。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}