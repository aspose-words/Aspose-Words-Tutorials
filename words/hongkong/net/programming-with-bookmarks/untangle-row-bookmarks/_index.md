---
title: 解開Word文檔中的行書籤
linktitle: 解開Word文檔中的行書籤
second_title: Aspose.Words 文件處理 API
description: 使用 Aspose.Words for .NET 輕鬆理清 Word 文件中纏結的行書籤。本指南將引導您完成更乾淨、更安全的書籤管理流程。
weight: 10
url: /zh-hant/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 解開Word文檔中的行書籤

## 介紹

您是否曾經遇到過這樣的情況：透過書籤刪除Word文件中的一行會弄亂相鄰行中的其他書籤？這可能會非常令人沮喪，尤其是在處理複雜的表格時。值得慶幸的是，Aspose.Words for .NET 提供了一個強大的解決方案：理清行書籤。 

本指南將引導您完成使用 Aspose.Words for .NET 理清 Word 文件中的行書籤的過程。我們將把程式碼分解為易於理解的步驟，並解釋每個函數的用途，使您能夠自信地解決那些討厭的書籤問題。

## 先決條件

在開始之前，您需要一些東西：

1.  Aspose.Words for .NET：這個商業函式庫提供了以程式設計方式處理 Word 文件的功能。 2. 您可以從以下位置下載免費試用版[下載連結](https://releases.aspose.com/words/net/)或從以下位置購買許可證[買](https://purchase.aspose.com/buy).
3. C# 開發環境：Visual Studio 或任何其他 C# IDE 都可以完美運作。
4. 帶有行書籤的 Word 文件：我們將使用名為「Table column bookmarks.docx」的範例文件進行示範。

## 導入命名空間

第一步涉及將必要的命名空間匯入到您的 C# 專案中。這些命名空間提供對我們將從 Aspose.Words for .NET 使用的類別和功能的存取：

```csharp
using Aspose.Words;
using System;
```

## 第 1 步：載入 Word 文檔

我們首先載入包含纏結行書籤的 Word 文件。這`Document`類別處理 Aspose.Words 中的文件操作。載入文檔的方法如下：

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; //替換為您的文件位置
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

記得更換`"YOUR DOCUMENT DIRECTORY"`與「Table column bookmarks.docx」檔案的實際路徑。

## 第 2 步：解開行書籤

這就是魔法發生的地方！這`Untangle`函數負責解開行書籤。讓我們來分解一下它的功能：

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   //取得書籤和書籤末尾的父行
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   //檢查行是否有效且相鄰
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //將書籤結尾移到頂行最後一個儲存格的最後一段
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

以下是該程式碼功能的逐步說明：

我們使用 a 迭代文件中的所有書籤`foreach`環形。
對於每個書籤，我們檢索書籤開始的父行（`bookmark.BookmarkStart`) 和書籤末尾 (`bookmark.BookmarkEnd` ）使用`GetAncestor`方法。
然後我們檢查是否找到兩行（`row1 != null`和`row2 != null`）並且如果它們是相鄰行（`row1.NextSibling == row2`）。這確保我們只修改跨相鄰行的書籤。
如果滿足條件，我們將書籤結束節點移動到頂行最後一個單元格中最後一段的末尾（`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`）有效地解開它們。

## 步驟3：按書籤刪除行

現在書籤已解開，我們可以使用書籤稱安全地刪除行。這`DeleteRowByBookmark`函數處理這個任務：

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

下面是這個函數的分解：

我們採用書籤名（`bookmarkName`）作為輸入。
我們使用以下方法檢索對應的書籤對象`doc.Range.Bookmarks[bookmarkName]`.
然後我們開始使用書籤的父行`GetAncestor`（類似`Untangle`功能）。
最後，我們檢查書籤和行是否存在（`bookmark != null`和

## 第 4 步：驗證解開情況

雖然`Untangle`函數應該確保其他書籤的安全，驗證總是好的做法。我們可以透過以下方法檢查解開過程是否意外刪除了另一個書籤的末尾：

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

此程式碼片段檢查刪除帶有“ROW2”書籤的行後，名為“ROW1”的書籤末尾是否仍然存在。如果為 null，則會引發異常，表示解纏過程出現問題。 

## 第 5 步：儲存文檔

最後，在解開書籤並可能刪除行後，使用以下命令保存修改後的文檔`Save`方法：

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

這會將文件與解開的書籤和任何已刪除的行保存在新檔案名稱「WorkingWithBookmarks.UntangleRowBookmarks.docx」下。 

## 結論

透過遵循這些步驟並利用`Untangle`功能，您可以使用 Aspose.Words for .NET 有效地理清 Word 文件中的行書籤。這可確保透過書籤刪除行不會對相鄰行中的其他書籤造成意外後果。請記住替換佔位符，例如`"YOUR DOCUMENT DIRECTORY"`與您的實際路徑和檔案名稱。

## 常見問題解答

### Aspose.Words for .NET 是免費的嗎？

 Aspose.Words for .NET 是一個商業庫，可以免費試用。您可以從以下位置下載：[下載連結](https://releases.aspose.com/words/net/).

### 我可以在 Word 中手動解開行書籤嗎？

雖然技術上可行，但在 Word 中手動解開書籤可能很乏味且容易出錯。 Aspose.Words for .NET 可以自動執行此流程，從而節省您的時間和精力。

### 如果發生什麼情況`Untangle` function encounters an error?

程式碼包含一個異常處理程序，如果解開過程意外刪除了另一個書籤的末尾，該異常處理程序將引發異常。您可以自訂此錯誤處理以滿足您的特定需求。

### 我可以使用此程式碼來解開非相鄰行之間的書籤嗎？

目前，該程式碼的重點是理清跨相鄰行的書籤。修改程式碼以處理不相鄰的行將需要額外的邏輯來識別和處理這些情況。

### 使用這種方法有限制嗎？

此方法假設書籤在表格儲存格內定義良好。如果書籤放置在儲存格外部或意外位置，則解開過程可能無法如預期進行。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
