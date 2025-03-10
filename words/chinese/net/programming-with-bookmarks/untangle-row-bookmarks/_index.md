---
title: 解开 Word 文档中的行书签
linktitle: 解开 Word 文档中的行书签
second_title: Aspose.Words 文档处理 API
description: 使用 Aspose.Words for .NET 轻松理清 Word 文档中错综复杂的行书签。本指南将引导您完成更清洁、更安全的书签管理过程。
weight: 10
url: /zh/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 解开 Word 文档中的行书签

## 介绍

您是否遇到过这样的情况：删除 Word 文档中书签所在的行会弄乱相邻行中的其他书签？这可能非常令人沮丧，尤其是在处理复杂的表格时。幸运的是，Aspose.Words for .NET 提供了一个强大的解决方案：解开行书签。 

本指南将引导您使用 Aspose.Words for .NET 解开 Word 文档中的行书签。我们将代码分解为易于理解的步骤并解释每个函数的用途，使您能够自信地解决那些棘手的书签问题。

## 先决条件

在深入研究之前，您需要准备一些东西：

1.  Aspose.Words for .NET：这个商业库提供了以编程方式处理 Word 文档的功能。2. 您可以从以下位置下载免费试用版[下载链接](https://releases.aspose.com/words/net/)或从购买许可证[买](https://purchase.aspose.com/buy).
3. C# 开发环境：Visual Studio 或任何其他 C# IDE 均可完美运行。
4. 带有行书签的 Word 文档：我们将使用名为“表格列书签.docx”的示例文档进行演示。

## 导入命名空间

第一步涉及将必要的命名空间导入到您的 C# 项目中。这些命名空间提供对我们将从 Aspose.Words for .NET 中使用的类和功能的访问：

```csharp
using Aspose.Words;
using System;
```

## 步骤 1：加载 Word 文档

我们首先加载包含缠结行书签的 Word 文档。`Document`类处理 Aspose.Words 中的文档操作。加载文档的方法如下：

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; //替换为您的文档位置
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

记得更换`"YOUR DOCUMENT DIRECTORY"`使用“Table column bookmarks.docx”文件的实际路径。

## 第 2 步：解开书签行

这就是奇迹发生的地方！`Untangle`函数负责解开行书签。让我们分解一下它的功能：

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   //获取书签和书签结尾的父行
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   //检查行是否有效且相邻
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //将书签结尾移动到顶行最后一个单元格的最后一段
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

以下是代码功能的逐步解释：

我们使用`foreach`环形。
对于每个书签，我们检索书签起始行的父行（`bookmark.BookmarkStart`）和书签结束（`bookmark.BookmarkEnd` ）使用`GetAncestor`方法。
然后我们检查是否找到了两行（`row1 != null`和`row2 != null`）并且如果它们是相邻行（`row1.NextSibling == row2`）。这确保我们只修改跨越相邻行的书签。
如果满足条件，我们将书签结束节点移动到顶行最后一个单元格中最后一段的末尾 (`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`) 有效地解开它们。

## 步骤 3：按书签删除行

现在书签已经解开了，我们可以使用书签名称安全地删除行。`DeleteRowByBookmark`函数处理这个任务：

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

以下是此功能的详细说明：

我们取书签名称（`bookmarkName`）作为输入。
我们使用以下方法检索相应的书签对象`doc.Range.Bookmarks[bookmarkName]`.
然后我们获取书签的父行开始使用`GetAncestor`（类似于`Untangle`功能）。
最后，我们检查书签和行是否存在（`bookmark != null`和

## 步骤 4：确认解开

虽然`Untangle`函数应该确保其他书签的安全，验证它始终是一种很好的做法。下面是我们如何检查解开过程是否意外删除了另一个书签的末尾：

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

此代码片段检查在删除带有“ROW2”书签的行后，名为“ROW1”的书签的末尾是否仍然存在。如果它为空，则抛出异常，表示解开过程存在问题。 

## 步骤 5：保存文档

最后，在解开书签并可能删除行之后，使用`Save`方法：

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

这会将包含解开的书签和所有已删除的行的文档保存在新文件名“WorkingWithBookmarks.UntangleRowBookmarks.docx”下。 

## 结论

通过遵循以下步骤并利用`Untangle`功能，您可以使用 Aspose.Words for .NET 有效地解开 Word 文档中的行书签。这可确保按书签删除行不会对相邻行中的其他书签造成意外后果。请记住将占位符替换为`"YOUR DOCUMENT DIRECTORY"`替换为您的实际路径和文件名。

## 常见问题解答

### Aspose.Words for .NET 免费吗？

 Aspose.Words for .NET 是一个商业库，可免费试用。您可以从以下位置下载[下载链接](https://releases.aspose.com/words/net/).

### 我可以在 Word 中手动解开行书签吗？

虽然技术上可行，但手动解开 Word 中的书签可能很繁琐且容易出错。Aspose.Words for .NET 可自动执行此过程，为您节省时间和精力。

### 如果`Untangle` function encounters an error?

代码包含一个异常处理程序，如果解开过程意外删除了另一个书签的末尾，则会引发异常。您可以自定义此错误处理以满足您的特定需求。

### 我可以使用此代码来解开不相邻行之间的书签吗？

目前，代码主要专注于解开跨相邻行的书签。修改代码以处理非相邻行需要额外的逻辑来识别和处理这些情况。

### 使用此方法有什么限制吗？

此方法假设书签在表格单元格内定义明确。如果书签放置在单元格之外或意外位置，则解开过程可能无法按预期进行。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
