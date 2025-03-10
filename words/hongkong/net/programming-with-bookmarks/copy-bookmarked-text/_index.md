---
title: 在 Word 文件中複製添加書籤的文本
linktitle: 在 Word 文件中複製添加書籤的文本
second_title: Aspose.Words 文件處理 API
description: 使用 Aspose.Words for .NET 在 Word 文件之間輕鬆複製書籤文字。透過此逐步指南了解具體操作方法。
weight: 10
url: /zh-hant/net/programming-with-bookmarks/copy-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文件中複製添加書籤的文本

## 介紹

您是否曾經發現自己需要將一個 Word 文件中的特定部分複製到另一個 Word 文件？嗯，你很幸運！在本教學中，我們將引導您了解如何使用 Aspose.Words for .NET 將帶有書籤的文字從一個 Word 文件複製到另一個 Word 文件。無論您是建立動態報告還是自動產生文檔，本指南都將為您簡化流程。

## 先決條件

在我們深入之前，請確保您具備以下條件：

-  Aspose.Words for .NET Library：您可以從以下位置下載它[這裡](https://releases.aspose.com/words/net/).
- 開發環境：Visual Studio 或任何其他.NET 開發環境。
- C#基礎：熟悉C#程式設計和.NET框架。

## 導入命名空間

首先，請確保您的專案中導入了必要的命名空間：

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## 第 1 步：載入來源文檔

首先，您需要載入包含要複製的書籤文字的來源文件。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

這裡，`dataDir`是文檔目錄的路徑，並且`Bookmarks.docx`是來源文檔。

## 第 2 步：識別書籤

接下來，確定您要從來源文件複製的書籤。

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

代替`"MyBookmark1"`與您書籤的實際名稱。

## 第 3 步：建立目標文檔

現在，建立一個新文檔，將複製新增書籤的文字。

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## 第 4 步：匯入新增書籤的內容

為了確保保留樣式和格式，請使用`NodeImporter`將新增書籤的內容從來源文件匯入到目標文件。

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## 第 5 步：定義 AppendBookmarkedText 方法

這就是奇蹟發生的地方。定義一個方法來處理書籤文字的複製：

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

## 步驟 6：儲存目標文檔

最後儲存目標文件以驗證複製的內容。

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## 結論

就是這樣！您已使用 Aspose.Words for .NET 成功將帶有書籤的文字從一個 Word 文件複製到另一個 Word 文件。此方法對於自動化文件操作任務非常有用，使您的工作流程更加有效率和簡化。

## 常見問題解答

### 我可以一次複製多個書籤嗎？
是的，您可以迭代多個書籤並使用相同的方法複製每個書籤。

### 如果找不到書籤會怎樣？
這`Range.Bookmarks`財產將歸還`null`，因此請確保處理這種情況以避免異常。

### 我可以保留原始書籤的格式嗎？
絕對地！使用`ImportFormatMode.KeepSourceFormatting`確保保留原始格式。

### 書籤文字的大小有限制嗎？
沒有具體限制，但效能可能會因文件非常大而有所不同。

### 我可以在不同的 Word 文件格式之間複製文字嗎？
是的，Aspose.Words 支援各種 Word 格式，並且該方法適用於這些格式。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
