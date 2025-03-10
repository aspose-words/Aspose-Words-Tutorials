---
title: 新增 刪除評論 回复
linktitle: 新增 刪除評論 回复
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文件中新增和刪除評論回應。透過此逐步指南增強您的文件協作。
weight: 10
url: /zh-hant/net/working-with-comments/add-remove-comment-reply/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 新增 刪除評論 回复

## 介紹

在 Word 文件中使用註解及其回覆可以顯著增強文件審閱過程。透過 Aspose.Words for .NET，您可以自動執行這些任務，讓您的工作流程更加有效率且簡化。本教學將引導您新增和刪除評論回复，並提供掌握此功能的逐步指南。

## 先決條件

在深入研究程式碼之前，請確保您具備以下條件：

-  Aspose.Words for .NET：從以下位置下載並安裝它[這裡](https://releases.aspose.com/words/net/).
- 開發環境：Visual Studio 或任何其他支援.NET 的IDE。
- C# 基礎知識：熟悉 C# 程式設計至關重要。

## 導入命名空間

首先，在您的 C# 專案中匯入必要的命名空間：

```csharp
using System;
using Aspose.Words;
```

## 第 1 步：載入 Word 文檔

首先，您需要載入包含要管理的註解的 Word 文件。對於此範例，我們假設您的目錄中有一個名為「Comments.docx」的文件。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

## 第 2 步：造訪第一則評論

接下來，請訪問文件中的第一條評論。該評論將作為新增和刪除回應的目標。

```csharp
Comment comment = (Comment)doc.GetChild(NodeType.Comment, 0, true);
```

## 步驟 3：刪除現有回复

如果該評論已有回复，您可能需要刪除一條回复。刪除評論的第一條回應的方法如下：

```csharp
comment.RemoveReply(comment.Replies[0]);
```

## 步驟 4： 新增回复

現在，讓我們為評論添加新回應。您可以指定作者姓名、縮寫、回覆日期和時間以及回覆文字。

```csharp
comment.AddReply("John Doe", "JD", new DateTime(2017, 9, 25, 12, 15, 0), "New reply");
```

## 步驟5：儲存更新後的文檔

最後，將修改後的文件儲存到您的目錄中。

```csharp
doc.Save(dataDir + "WorkingWithComments.AddRemoveCommentReply.docx");
```

## 結論

以程式設計方式管理 Word 文件中的評論回應可以節省大量時間和精力，尤其是在處理大量評論時。 Aspose.Words for .NET 讓這個過程簡單而有效率。透過遵循本指南中概述的步驟，您可以輕鬆新增和刪除評論回复，從而增強您的文件協作體驗。

## 常見問題解答

### 如何為單一評論添加多個回應？

您可以透過呼叫以下命令來為單一評論新增多個回复`AddReply`對同一個評論對像多次使用方法。

### 我可以自訂每個回應的作者詳細資訊嗎？

是的，您可以在使用時指定作者姓名、縮寫以及每次回覆的日期和時間`AddReply`方法。

### 是否可以一次刪除評論中的所有回應？

要刪除所有回复，您需要循環`Replies`收集評論並單獨刪除每一則。

### 我可以存取文件特定部分中的評論嗎？

是的，您可以使用以下命令瀏覽文件的各個部分並存取每個部分中的註釋`GetChild`方法。

### Aspose.Words for .NET 支援其他評論相關功能嗎？

是的，Aspose.Words for .NET 為各種評論相關功能提供了廣泛的支持，包括新增評論、設定評論屬性等等。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
