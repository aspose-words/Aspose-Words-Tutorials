---
"description": "使用 Aspose.Words for .NET 自動解析和回覆 Word 文件中的註解。包含逐步指南。"
"linktitle": "評論已解決並回复"
"second_title": "Aspose.Words文件處理API"
"title": "評論已解決並回复"
"url": "/zh-hant/net/working-with-comments/comment-resolved-and-replies/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 評論已解決並回复

## 介紹

如果您正在使用 Word 文檔，您可能已經處理過註釋。它們非常適合協作，但管理它們可能會很麻煩。使用 Aspose.Words for .NET，您可以自動執行解決和回覆評論的過程。本指南將引導您完成此操作的步驟。

## 先決條件

在深入研究之前，請確保您已具備以下條件：

1. Aspose.Words for .NET：您可以從 [這裡](https://releases。aspose.com/words/net/).
2. 開發環境：使用.NET Framework設定。
3. C# 基礎知識：熟悉文法和概念。

## 導入命名空間

首先，讓我們導入必要的命名空間。這確保我們需要的所有類別和方法都隨時可用。

```csharp
using Aspose.Words;
using Aspose.Words.Comments;
```

讓我們將這個過程分解為簡單、易於遵循的步驟。每個步驟都會幫助您理解程式碼及其功能。

## 步驟 1：載入文檔

首先，載入包含註解的 Word 文件。使用 `Document` 為此課程。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

這行程式碼初始化了一個新的 `Document` 物件以及您的 Word 文件的路徑。

## 第 2 步：檢索評論

接下來我們需要取得文件中的所有評論。我們將使用 `GetChildNodes` 方法來檢索 `Comment` 節點。

```csharp
NodeCollection comments = doc.GetChildNodes(NodeType.Comment, true);
```

此程式碼會檢索文件中的所有註釋並將其儲存在 `NodeCollection`。

## 步驟 3：訪問家長評論

對於我們的例子，我們將重點放在集合中的第一個評論。這將是我們的家長評論。

```csharp
Comment parentComment = (Comment)comments[0];
```

在這裡，我們將集合中的第一個節點轉換為 `Comment` 目的。

## 步驟 4：循環回复

現在，讓我們循環查看對父評論的回應。我們將使用 `foreach` 循環迭代每個回复。

```csharp
foreach (Comment childComment in parentComment.Replies)
{
    Console.WriteLine(childComment.Ancestor.Id);
    Console.WriteLine(childComment.Done);

    childComment.Done = true;
}
```

在這個循環中，我們列印祖先註釋的 ID 及其狀態（是否完成）。然後，我們將每個回應標記為已完成。

## 步驟5：儲存文檔

最後，將修改後的文件儲存到您的目錄中。

```csharp
doc.Save(dataDir + "WorkingWithComments.CommentResolvedAndReplies.docx");
```

此程式碼將變更儲存到新文檔，確保原始文件保持不變。

## 結論

處理 Word 文件中的註解不一定是手動操作。使用 Aspose.Words for .NET，您可以自動化該過程，節省時間並減少錯誤。按照本指南可以有效地解決和回覆文件中的評論。

## 常見問題解答

### 我可以使用 Aspose.Words for .NET 自動執行其他與評論相關的任務嗎？  
是的，您可以自動執行各種任務，例如新增、刪除和修改評論。

### Aspose.Words for .NET 是否與 .NET Core 相容？  
是的，Aspose.Words for .NET 同時支援 .NET Framework 和 .NET Core。

### 如何免費試用 Aspose.Words for .NET？  
您可以從下載免費試用版 [這裡](https://releases。aspose.com/).

### 我可以使用 Aspose.Words for .NET 處理其他文件類型嗎？  
是的，Aspose.Words 支援各種格式，包括 DOCX、PDF、HTML 等。

### 在哪裡可以找到 Aspose.Words for .NET 的詳細文件？  
您可以存取文檔 [這裡](https://reference。aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}