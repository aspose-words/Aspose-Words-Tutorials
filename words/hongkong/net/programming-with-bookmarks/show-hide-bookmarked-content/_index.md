---
"description": "透過本詳細的逐步指南了解如何使用 Aspose.Words for .NET 顯示和隱藏 Word 文件中的書籤內容。"
"linktitle": "在 Word 文件中顯示隱藏書籤內容"
"second_title": "Aspose.Words文件處理API"
"title": "在 Word 文件中顯示隱藏書籤內容"
"url": "/zh-hant/net/programming-with-bookmarks/show-hide-bookmarked-content/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文件中顯示隱藏書籤內容

## 介紹

準備好使用 Aspose.Words for .NET 深入文件操作的世界了嗎？無論您是希望自動執行文件任務的開發人員，還是只是對以程式設計方式處理 Word 文件感到好奇的人，您都來到了正確的地方。今天，我們將探討如何使用 Aspose.Words for .NET 在 Word 文件中顯示和隱藏書籤內容。本逐步指南將使您成為基於書籤控制內容可見性的專家。讓我們開始吧！

## 先決條件

在我們深入討論細節之前，您需要準備一些東西：

1. Visual Studio：任何與 .NET 相容的版本。
2. Aspose.Words for .NET：下載 [這裡](https://releases。aspose.com/words/net/).
3. 對 C# 的基本了解：如果您可以編寫一個簡單的「Hello World」程序，那麼就可以開始了。
4. 帶有書籤的 Word 文件：在本教程中，我們將使用帶有書籤的範例文件。

## 導入命名空間

首先，讓我們導入必要的命名空間。這確保我們擁有完成任務所需的所有工具。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

有了這些命名空間，我們就可以開始我們的旅程了。

## 步驟 1：設定項目

好吧，讓我們開始在 Visual Studio 中設定我們的專案。

### 建立新專案

開啟 Visual Studio 並建立一個新的控制台應用程式（.NET Core）專案。給它一個朗朗上口的名字，例如「BookmarkVisibilityManager」。

### 新增 Aspose.Words for .NET

您需要將 Aspose.Words for .NET 新增到您的專案中。您可以透過 NuGet 套件管理器執行此操作。

1. 前往工具>NuGet 套件管理器>管理解決方案的 NuGet 套件。
2. 搜尋“Aspose.Words”。
3. 安裝該包。

偉大的！現在我們的專案已經設定好了，讓我們繼續載入我們的文件。

## 步驟2：載入文檔

我們需要載入包含書籤的 Word 文件。在本教學中，我們將使用名為「Bookmarks.docx」的範例文件。

```csharp
// 文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

此程式碼片段設定文檔目錄的路徑並將文檔載入到 `doc` 目的。

## 步驟 3：顯示/隱藏已加入書籤的內容

現在到了有趣的部分——根據書籤顯示或隱藏內容。我們將建立一個名為 `ShowHideBookmarkedContent` 來處理這個問題。

以下是切換書籤內容可見性的方法：

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

### 方法分解

- 書籤檢索： `Bookmark bm = doc.Range.Bookmarks[bookmarkName];` 獲取書籤。
- 節點遍歷：我們遍歷書籤內的節點。
- 可見性切換：如果節點是 `Run` （連續的文字），我們將其設定為 `Hidden` 財產。

## 步驟4：應用方法

有了我們的方法，讓我們應用它來根據書籤顯示或隱藏內容。

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

這行程式碼將隱藏名為「MyBookmark1」的書籤中的內容。

## 步驟5：儲存文檔

最後，讓我們儲存修改後的文件。

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

這將保存我們所做更改的文檔。

## 結論

就是這樣！您剛剛學習如何使用 Aspose.Words for .NET 在 Word 文件中顯示和隱藏書籤內容。這個強大的工具使文件操作變得輕而易舉，無論您是自動執行報告、建立範本還是只是修改 Word 文件。編碼愉快！

## 常見問題解答

### 我可以一次切換多個書籤嗎？
是的，您可以致電 `ShowHideBookmarkedContent` 方法適用於您想要切換的每個書籤。

### 隱藏內容會影響文件的結構嗎？
不，隱藏內容只會影響其可見度。內容保留在文件中。

### 我可以將此方法用於其他類型的內容嗎？
此方法專門切換文字運行。對於其他內容類型，您需要修改節點遍歷邏輯。

### Aspose.Words for .NET 免費嗎？
Aspose.Words 提供免費試用 [這裡](https://releases.aspose.com/)，但生產使用需要完整許可證。您可以購買 [這裡](https://purchase。aspose.com/buy).

### 如果遇到問題，如何獲得支援？
您可以從 Aspose 社區獲得支持 [這裡](https://forum。aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}