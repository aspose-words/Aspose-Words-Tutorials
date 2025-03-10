---
title: 評論已解決並回复
linktitle: 評論已解決並回复
second_title: Aspose.Words 文件處理 API
description: 使用 Aspose.Words for .NET 自動解決和回覆 Word 文件中的註解。包括逐步指南。
weight: 10
url: /zh-hant/net/working-with-comments/comment-resolved-and-replies/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 評論已解決並回复

## 介紹

如果您正在處理 Word 文檔，您可能已經處理過註釋。它們非常適合協作，但管理它們可能很麻煩。使用 Aspose.Words for .NET，您可以自動化解決和回覆評論的過程。本指南將引導您完成此操作的步驟。

## 先決條件

在投入之前，請確保您具備以下條件：

1.  Aspose.Words for .NET：您可以從以下位置下載它[這裡](https://releases.aspose.com/words/net/).
2. 開發環境：使用.NET Framework建置。
3. C# 基礎知識：熟悉文法和概念。

## 導入命名空間

首先，讓我們導入必要的名稱空間。這確保了我們需要的所有類別和方法都隨時可用。

```csharp
using Aspose.Words;
using Aspose.Words.Comments;
```

讓我們將這個過程分解為簡單、易於遵循的步驟。每個步驟都將幫助您理解程式碼及其功能。

## 第 1 步：載入文檔

首先，載入包含註解的 Word 文件。使用`Document`為此類。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

這行程式碼初始化一個新的`Document`物件與您的 Word 文件的路徑。

## 第 2 步：檢索評論

接下來，我們需要取得文件中的所有註釋。我們將使用`GetChildNodes`檢索集合的方法`Comment`節點。

```csharp
NodeCollection comments = doc.GetChildNodes(NodeType.Comment, true);
```

此程式碼會檢索文件中的所有註釋並將它們儲存在`NodeCollection`.

## 第 3 步：訪問家長評論

對於我們的範例，我們將重點關注集合中的第一條評論。這將是我們家長的評論。

```csharp
Comment parentComment = (Comment)comments[0];
```

在這裡，我們將集合中的第一個節點轉換為`Comment`目的。

## 第 4 步：循環回复

現在，讓我們循環瀏覽對父親評論的回應。我們將使用一個`foreach`循環迭代每個回复。

```csharp
foreach (Comment childComment in parentComment.Replies)
{
    Console.WriteLine(childComment.Ancestor.Id);
    Console.WriteLine(childComment.Done);

    childComment.Done = true;
}
```

在此循環中，我們列印祖先註釋的 ID 及其狀態（無論是否完成）。然後，我們將每個回應標記為已完成。

## 第 5 步：儲存文檔

最後，將修改後的文件儲存到您的目錄中。

```csharp
doc.Save(dataDir + "WorkingWithComments.CommentResolvedAndReplies.docx");
```

此程式碼將變更儲存到新文檔，確保原始文件保持不變。

## 結論

處理 Word 文件中的註解不一定是一項手動工作。使用 Aspose.Words for .NET，您可以自動化該過程，從而節省時間並減少錯誤。請按照本指南有效解決和回覆文件中的評論。

## 常見問題解答

### 我可以使用 Aspose.Words for .NET 自動執行其他與評論相關的任務嗎？  
是的，您可以自動執行各種任務，例如新增、刪除和修改評論。

### Aspose.Words for .NET 與 .NET Core 相容嗎？  
是的，Aspose.Words for .NET 支援 .NET Framework 和 .NET Core。

### 如何獲得 Aspose.Words for .NET 的免費試用版？  
您可以從以下位置下載免費試用版[這裡](https://releases.aspose.com/).

### 我可以使用 Aspose.Words for .NET 處理其他文件類型嗎？  
是的，Aspose.Words 支援各種格式，包括 DOCX、PDF、HTML 等。

### 在哪裡可以找到 Aspose.Words for .NET 的詳細文件？  
您可以存取文檔[這裡](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
