---
"description": "了解如何使用 Aspose.Words for .NET 在 Word 文件中新增和刪除評論回應。透過本逐步指南增強您的文件協作。"
"linktitle": "新增刪除評論回复"
"second_title": "Aspose.Words文件處理API"
"title": "新增刪除評論回复"
"url": "/zh-hant/net/working-with-comments/add-remove-comment-reply/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 新增刪除評論回复

## 介紹

在 Word 文件中使用註解及其回覆可以顯著增強您的文件審閱過程。使用 Aspose.Words for .NET，您可以自動執行這些任務，讓您的工作流程更有效率和簡化。本教學將引導您新增和刪除評論回复，並提供掌握此功能的逐步指南。

## 先決條件

在深入研究程式碼之前，請確保您已具備以下條件：

- Aspose.Words for .NET：從以下位置下載並安裝 [這裡](https://releases。aspose.com/words/net/).
- 開發環境：Visual Studio 或任何其他支援 .NET 的 IDE。
- C# 基礎知識：熟悉 C# 程式設計至關重要。

## 導入命名空間

首先，在 C# 專案中導入必要的命名空間：

```csharp
using System;
using Aspose.Words;
```

## 步驟1：載入Word文檔

首先，您需要載入包含要管理的評論的 Word 文件。對於此範例，我們假設您的目錄中有一個名為「Comments.docx」的文件。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

## 第 2 步：造訪第一則評論

接下來，請訪問文件中的第一個評論。此評論將成為新增和刪除回應的目標。

```csharp
Comment comment = (Comment)doc.GetChild(NodeType.Comment, 0, true);
```

## 步驟 3：刪除現有回复

如果該評論已有回复，您可能需要刪除一條回复。刪除評論第一條回應的方法如下：

```csharp
comment.RemoveReply(comment.Replies[0]);
```

## 步驟 4：新增回复

現在，讓我們為該評論添加新的回應。您可以指定作者的姓名、姓名首字母、回覆的日期和時間以及回覆文字。

```csharp
comment.AddReply("John Doe", "JD", new DateTime(2017, 9, 25, 12, 15, 0), "New reply");
```

## 步驟5：儲存更新後的文檔

最後，將修改後的文件儲存到您的目錄中。

```csharp
doc.Save(dataDir + "WorkingWithComments.AddRemoveCommentReply.docx");
```

## 結論

以程式設計方式管理 Word 文件中的評論回應可以節省您大量的時間和精力，尤其是在處理大量評論時。 Aspose.Words for .NET 讓這個過程變得簡單又有效率。透過按照本指南中概述的步驟，您可以輕鬆新增和刪除評論回复，從而增強您的文件協作體驗。

## 常見問題解答

### 如何為一則評論添加多個回應？

您可以透過調用 `AddReply` 對同一個評論對像多次呼叫該方法。

### 我可以自訂每個回應的作者詳細資訊嗎？

是的，您可以在使用 `AddReply` 方法。

### 是否可以一次刪除一則評論的所有回應？

要刪除所有回复，您需要循環遍歷 `Replies` 收集評論並單獨刪除每一則評論。

### 我可以存取文件特定部分的評論嗎？

是的，您可以使用 `GetChild` 方法。

### Aspose.Words for .NET 是否支援其他與評論相關的功能？

是的，Aspose.Words for .NET 為各種與評論相關的功能提供了廣泛的支持，包括添加新評論、設定評論屬性等。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}