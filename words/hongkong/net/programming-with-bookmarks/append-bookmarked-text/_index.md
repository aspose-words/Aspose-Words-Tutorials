---
title: 在 Word 文件中附加添加書籤的文本
linktitle: 在 Word 文件中附加添加書籤的文本
second_title: Aspose.Words 文件處理 API
description: 透過此逐步指南，了解如何使用 Aspose.Words for .NET 在 Word 文件中附加書籤文字。非常適合開發人員。
weight: 10
url: /zh-hant/net/programming-with-bookmarks/append-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文件中附加添加書籤的文本

## 介紹

嘿！您是否曾經嘗試過從 Word 文件中添加書籤的部分添加文本，但發現這很棘手？你很幸運！本教學將引導您完成使用 Aspose.Words for .NET 的過程。我們會將其分解為簡單的步驟，以便您可以輕鬆地進行操作。讓我們深入了解並像專業人士一樣附加書籤文字！

## 先決條件

在開始之前，讓我們確保您擁有所需的一切：

-  Aspose.Words for .NET：確保您已安裝它。如果沒有，您可以[在這裡下載](https://releases.aspose.com/words/net/).
- 開發環境：任何 .NET 開發環境，例如 Visual Studio。
- C# 基礎知識：了解基本 C# 程式設計概念將會有所幫助。
- 帶有書籤的 Word 文件：設定了書籤的 Word 文檔，我們將用它來附加文字。

## 導入命名空間

首先，讓我們導入必要的名稱空間。這將確保我們觸手可及所需的所有工具。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

讓我們將範例分解為詳細步驟。

## 第 1 步：載入文件並初始化變數

好吧，讓我們先載入 Word 文件並初始化我們需要的變數。

```csharp
//載入來源文檔和目標文檔。
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

//初始化文檔導入器。
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

//在來源文檔中找到書籤。
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## 第 2 步：確定開始和結束段落

現在，讓我們找到書籤開始和結束的段落。這很重要，因為我們需要處理這些範圍內的文字。

```csharp
//這是包含書籤開頭的段落。
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

//這是包含書籤結尾的段落。
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## 第 3 步：驗證段落父級

我們需要確保開始和結束段落具有相同的父級。這是一個簡單的場景，讓事情變得簡單。

```csharp
//將我們限制在一個相當簡單的場景。
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## 步驟 4：確定要停止的節點

接下來，我們需要確定停止複製文字的節點。這將是緊接結束段落之後的節點。

```csharp
//我們想要複製從開始段落到（並包括）結束段落的所有段落，
//因此，我們停止的節點是結束段落之後的節點。
Node endNode = endPara.NextSibling;
```

## 步驟 5：將新增書籤的文字附加到目標文檔

最後，讓我們循環遍歷從起始段落到結束段落之後的節點，並將它們附加到目標文件。

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    //這將創建當前節點的副本並將其導入到上下文中（使其有效）
    //目標文檔的。導入意味著調整樣式並正確列出標識符。
    Node newNode = importer.ImportNode(curNode, true);

    //將導入的節點附加到目標文件。
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

//儲存帶有附加文字的目標文件。
dstDoc.Save("appended_document.docx");
```

## 結論

現在你就擁有了！您已使用 Aspose.Words for .NET 成功從 Word 文件中的書籤部分附加文字。這個強大的工具使文件操作變得輕而易舉，現在您還有一個錦囊妙計。快樂編碼！

## 常見問題解答

### 我可以一次性添加多個書籤中的文字嗎？
是的，您可以對每個書籤重複此過程並相應地附加文字。

### 如果開始段落和結束段落有不同的父親段落怎麼辦？
目前的範例假設它們具有相同的父級。對於不同的家長來說，需要更複雜的處理。

### 我可以保留附加文字的原始格式嗎？
絕對地！這`ImportFormatMode.KeepSourceFormatting`確保保留原始格式。

### 是否可以將文字附加到目標文件中的特定位置？
是的，您可以透過導覽至目標文件中的所需節點將文字附加到任何位置。

### 如果我需要將書籤中的文字附加到新部分怎麼辦？
您可以在目標文件中建立一個新部分並在其中附加文字。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
