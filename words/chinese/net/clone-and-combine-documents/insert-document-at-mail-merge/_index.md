---
"description": "在本全面的分步教程中学习如何使用 Aspose.Words for .NET 在邮件合并字段中插入文档。"
"linktitle": "在邮件合并中插入文档"
"second_title": "Aspose.Words文档处理API"
"title": "在邮件合并中插入文档"
"url": "/zh/net/clone-and-combine-documents/insert-document-at-mail-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在邮件合并中插入文档

## 介绍

欢迎来到 Aspose.Words for .NET 文档自动化的世界！您是否想过如何在邮件合并操作期间将文档动态插入主文档中的特定字段？那么您来对地方了。本教程将逐步指导您使用 Aspose.Words for .NET 在邮件合并字段中插入文档。这就像拼凑一个拼图，每一块都完美地拼凑在一起。那么，让我们开始吧！

## 先决条件

在开始之前，请确保您具备以下条件：

1. Aspose.Words for .NET：您可以 [点击此处下载最新版本](https://releases.aspose.com/words/net/)。如果您需要购买许可证，您可以这样做 [这里](https://purchase.aspose.com/buy)。或者，您可以获得 [临时执照](https://purchase.aspose.com/temporary-license/) 或者尝试一下 [免费试用](https://releases。aspose.com/).
2. 开发环境：Visual Studio 或任何其他 C# IDE。
3. C# 基础知识：熟悉 C# 编程将使本教程变得轻而易举。

## 导入命名空间

首先，你需要导入必要的命名空间。它们就像项目的基石。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

让我们将整个流程分解成易于管理的步骤。每个步骤都以前一步为基础，最终引导您找到完整的解决方案。

## 步骤 1：设置目录

在开始插入文档之前，您需要定义文档目录的路径。这是存储文档的位置。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步骤2：加载主文档

接下来，您将加载主文档。该文档包含将插入其他文档的合并字段。

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## 步骤3：设置字段合并回调

为了处理合并过程，您需要设置一个回调函数。该函数将负责在指定的合并字段处插入文档。

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## 步骤4：执行邮件合并

现在是时候执行邮件合并了。这就是奇迹发生的地方。您需要指定合并字段以及应插入此字段的文档。

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## 步骤5：保存文档

邮件合并完成后，您将保存修改后的文档。新文档将包含插入的内容，并显示在您想要的位置。

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## 步骤 6：创建回调处理程序

回调处理程序是一个针对合并字段进行特殊处理的类。它加载字段值中指定的文档并将其插入到当前合并字段中。

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## 步骤7：插入文档

该方法将指定的文档插入到当前段落或表格单元格中。

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## 结论

就这样！您已成功使用 Aspose.Words for .NET 在邮件合并操作中将文档插入到特定字段。这项强大的功能可以为您节省大量时间和精力，尤其是在处理大量文档时。您可以将其想象成拥有一位私人助理，为您处理所有繁重的工作。所以，赶快尝试一下吧！祝您编码愉快！

## 常见问题解答

### 我可以在不同的合并字段插入多个文档吗？
是的，你可以。只需在 `MailMerge.Execute` 方法。

### 插入的文档的格式是否可以与主文档不同？
当然！您可以使用 `ImportFormatMode` 参数 `NodeImporter` 控制格式。

### 如果合并字段名称是动态的怎么办？
您可以通过将动态合并字段名称作为参数传递给回调处理程序来处理它们。

### 我可以将此方法用于不同的文件格式吗？
是的，Aspose.Words 支持各种文件格式，包括 DOCX、PDF 等。

### 如何处理文档插入过程中的错误？
在回调处理程序中实现错误处理来管理可能发生的任何异常。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}