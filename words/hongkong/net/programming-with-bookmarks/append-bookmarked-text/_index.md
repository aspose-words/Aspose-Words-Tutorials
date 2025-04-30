---
"description": "透過本逐步指南了解如何使用 Aspose.Words for .NET 在 Word 文件中附加書籤文字。非常適合開發人員。"
"linktitle": "在 Word 文件中附加書籤文本"
"second_title": "Aspose.Words文件處理API"
"title": "在 Word 文件中附加書籤文本"
"url": "/zh-hant/net/programming-with-bookmarks/append-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文件中附加書籤文本

## 介紹

嘿！是否曾嘗試從 Word 文件中的書籤部分附加文字並發現這很棘手？你真幸運！本教學將引導您完成使用 Aspose.Words for .NET 的過程。我們將把它分解為簡單的步驟，以便您可以輕鬆遵循。讓我們深入研究並像專業人士一樣附加已加書籤的文本！

## 先決條件

在我們開始之前，請確保您已準備好所需的一切：

- Aspose.Words for .NET：確保您已安裝它。如果沒有，你可以 [點此下載](https://releases。aspose.com/words/net/).
- 開發環境：任何 .NET 開發環境，如 Visual Studio。
- C# 基礎知識：了解基本的 C# 程式設計概念將會有所幫助。
- 帶有書籤的 Word 文檔：設定了書籤的 Word 文檔，我們將使用它來附加文字。

## 導入命名空間

首先，讓我們導入必要的命名空間。這將確保我們擁有所需的所有工具。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

讓我們將範例分解為詳細步驟。

## 步驟 1：載入文件並初始化變數

好的，讓我們先載入我們的 Word 文件並初始化我們需要的變數。

```csharp
// 載入來源文檔和目標文檔。
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// 初始化文檔導入器。
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// 在來源文檔中尋找書籤。
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## 第 2 步：確定開始和結束段落

現在，讓我們找到書籤開始和結束的段落。這很關鍵，因為我們需要處理這些範圍內的文字。

```csharp
// 這是包含書籤開頭的段落。
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// 這是包含書籤結尾的段落。
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## 步驟 3：驗證段落父級

我們需要確保開始段落和結束段落具有相同的父段落。這是一個簡單的場景，以使事情變得簡單。

```csharp
// 將我們自己限制在一個相當簡單的場景中。
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## 步驟 4：確定要停止的節點

接下來，我們需要確定停止複製文字的節點。這將是緊接在結束段落之後的節點。

```csharp
// 我們希望複製從起始段落到結束段落（包括結束段落）的所有段落，
// 因此我們停止的節點是結束段落之後的一個節點。
Node endNode = endPara.NextSibling;
```

## 步驟 5：將書籤文字附加到目標文檔

最後，讓我們循環遍歷從起始段落到結束段落之後的節點，並將它們附加到目標文件。

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // 這將創建當前節點的副本並將其導入上下文（使其有效）
    // 目標文檔。匯入意味著正確調整樣式和清單標識符。
    Node newNode = importer.ImportNode(curNode, true);

    // 將導入的節點附加到目標文件。
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// 將附加的文字儲存到目標文件中。
dstDoc.Save("appended_document.docx");
```

## 結論

就是這樣！您已成功使用 Aspose.Words for .NET 從 Word 文件中的書籤部分附加文字。這個強大的工具讓文件操作變得輕而易舉，現在您又多了一個技巧。編碼愉快！

## 常見問題解答

### 我可以一次性添加多個書籤中的文字嗎？
是的，您可以對每個書籤重複此過程並相應地附加文字。

### 如果開始和結束段落有不同的父級怎麼辦？
目前範例假設它們有相同的父級。對於不同的父母，需要更複雜的處理。

### 我可以保留附加文字的原始格式嗎？
絕對地！這 `ImportFormatMode.KeepSourceFormatting` 確保保留原始格式。

### 是否可以將文字附加到目標文件中的特定位置？
是的，您可以透過導覽至目標文件中的所需節點將文字附加到任何位置。

### 如果我需要將書籤中的文字附加到新部分怎麼辦？
您可以在目標文件中建立一個新的部分並將文字附加到那裡。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}