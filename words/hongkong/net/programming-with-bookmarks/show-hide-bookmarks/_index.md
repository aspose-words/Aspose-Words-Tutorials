---
title: 在 Word 文件中顯示隱藏書籤
linktitle: 在 Word 文件中顯示隱藏書籤
second_title: Aspose.Words 文件處理 API
description: 透過我們的逐步指南，了解如何使用 Aspose.Words for .NET 在 Word 文件中動態顯示或隱藏書籤。非常適合開發人員。
weight: 10
url: /zh-hant/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文件中顯示隱藏書籤

## 介紹

您是否曾經發現自己需要動態隱藏或顯示 Word 文件的某些部分？嗯，你很幸運！透過 Aspose.Words for .NET，您可以輕鬆管理文件中書籤內容的可見性。本教學將引導您完成使用 Aspose.Words for .NET 在 Word 文件中顯示和隱藏書籤的過程。我們將逐步分解程式碼，因此無論您是經驗豐富的開發人員還是新手，您都會發現本指南很容易遵循。

## 先決條件

在我們深入研究程式碼之前，讓我們確保您擁有所需的一切：

1.  Aspose.Words for .NET：請確定您已安裝 Aspose.Words for .NET 程式庫。如果沒有的話可以下載[這裡](https://releases.aspose.com/words/net/).
2. 開發環境：像Visual Studio這樣的IDE。
3. C# 基礎：熟悉 C# 程式設計將會很有幫助。
4. Word 文件：帶有書籤的範例 Word 文件。

## 導入命名空間

在開始編寫程式碼之前，您需要匯入必要的命名空間。在 C# 檔案的開頭加入以下內容：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## 第 1 步：載入您的文檔

首先，您需要載入包含書籤的 Word 文件。您可以這樣做：

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### 解釋

- dataDir：這是您的Word文件所在的目錄路徑。
- 文件 doc：這會初始化一個新實例`Document`類別與您指定的文件。

## 步驟 2：顯示或隱藏新增書籤的內容

接下來，我們將定義一個方法來顯示或隱藏新增書籤的內容。這是完整的方法：

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD 書籤}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### 解釋

- Bookmark bm：從文件中取得書籤。
- DocumentBuilder 建構器：協助導覽和修改文件。
- Field欄位：插入IF欄位來檢查書籤的情況。
- 節點currentNode：遍歷節點找到欄位的開始和結束。

## 第三步：執行顯示/隱藏功能

現在，您需要致電`ShowHideBookmarkedContent`方法，傳遞文件、書籤名稱和可見性標誌：

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### 解釋

- doc：您的文件物件。
- “MyBookmark1”：您要顯示/隱藏的書籤的名稱。
- false：可見性標誌（true 表示顯示，false 表示隱藏）。

## 第 4 步：儲存您的文檔

最後儲存修改後的文件：

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### 解釋

- dataDir +「WorkingWithBookmarks.ShowHideBookmarks.docx」：將儲存變更的新文件的路徑和名稱。

## 結論

現在你就得到它了！您已經成功學習如何使用 Aspose.Words for .NET 在 Word 文件中顯示和隱藏書籤。該技術對於動態產生具有條件內容的文件非常有用。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的文件處理庫，可讓開發人員以程式設計方式建立、修改和轉換 Word 文件。

### 如何取得 Aspose.Words for .NET？
您可以從以下位置下載 Aspose.Words for .NET[這裡](https://releases.aspose.com/words/net/)。還提供免費試用。

### 我可以將此方法用於其他類型的書籤嗎？
是的，可以調整此方法來管理 Word 文件中任何書籤的可見性。

### 如果我的文件不包含指定的書籤怎麼辦？
如果書籤不存在，該方法將拋出錯誤。在嘗試顯示/隱藏書籤之前，請確保該書籤存在。

### 如果遇到問題，我該如何獲得支援？
您可以從 Aspose 社區獲得支持[這裡](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
