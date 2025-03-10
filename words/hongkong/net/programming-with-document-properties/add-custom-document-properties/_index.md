---
title: 新增自訂文件屬性
linktitle: 新增自訂文件屬性
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文件中新增自訂文件屬性。按照我們的逐步指南，使用附加元資料增強您的文件。
weight: 10
url: /zh-hant/net/programming-with-document-properties/add-custom-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 新增自訂文件屬性

## 介紹

嘿！您是否正在深入了解 Aspose.Words for .NET 的世界並想知道如何在 Word 文件中新增自訂文件屬性？那麼，您來對地方了！自訂屬性對於儲存內建屬性未涵蓋的其他元資料非常有用。無論是授權文件、新增修訂號，或是插入特定日期，自訂屬性都能滿足您的需求。在本教學中，我們將引導您完成使用 Aspose.Words for .NET 無縫新增這些屬性的步驟。準備好開始了嗎？讓我們深入了解吧！

## 先決條件

在我們進入程式碼之前，讓我們確保您已擁有所需的一切：

1.  Aspose.Words for .NET 函式庫：確保您擁有 Aspose.Words for .NET 函式庫。你可以下載它[這裡](https://releases.aspose.com/words/net/).
2. 開發環境：像Visual Studio這樣的IDE。
3. C# 基礎：本教學假設您對 C# 和 .NET 有基本了解。
4. 範例文檔：準備好範例 Word 文檔，命名為`Properties.docx`，您將對其進行修改。

## 導入命名空間

在開始編碼之前，我們需要導入必要的名稱空間。這是確保您的程式碼可以存取 Aspose.Words 提供的所有功能的關鍵步驟。

```csharp
using System;
using Aspose.Words;
```

## 第1步：設定文檔路徑

首先，我們需要設定文檔的路徑。我們將在此指定我們的位置`Properties.docx`文件。

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

在此程式碼片段中，替換`"YOUR DOCUMENT DIRECTORY"`與文檔的實際路徑。此步驟至關重要，因為它允許程式找到並開啟您的 Word 文件。

## 第 2 步：存取自訂文件屬性

接下來，讓我們存取 Word 文件的自訂文件屬性。這是儲存所有自訂元資料的位置。

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

透過這樣做，我們獲得了自訂屬性集合的句柄，我們將在以下步驟中使用它。

## 第 3 步：檢查現有屬性

在新增屬性之前，最好先檢查特定屬性是否已存在。這可以避免任何不必要的重複。

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

此行檢查屬性“Authorized”是否已存在。如果是這樣，程式將提前退出該方法以防止添加重複的屬性。

## 第 4 步：新增布爾屬性

現在，讓我們新增第一個自訂屬性 - 一個布林值來指示文件是否已授權。

```csharp
customDocumentProperties.Add("Authorized", true);
```

此行新增一個名為「Authorized」的自訂屬性，其值為`true`。簡單明了！

## 第 5 步：新增字串屬性

接下來，我們將新增另一個自訂屬性來指定誰授權了該文件。

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

在這裡，我們新增一個名為「Authorized By」的屬性，其值為「John Smith」。請隨意將“John Smith”替換為您喜歡的任何其他名稱。

## 第 6 步：新增日期屬性

讓我們新增一個屬性來儲存授權日期。這有助於追蹤文件的授權時間。

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

此程式碼片段新增一個名為「Authorized Date」的屬性，並將目前日期作為其值。這`DateTime.Today`屬性自動取得今天的日期。

## 第 7 步：新增修訂號

我們也可以新增一個屬性來追蹤文件的修訂號。這對於版本控制特別有用。

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

在這裡，我們新增一個名為「授權修訂版」的屬性，並為其指派文件的目前修訂版號。

## 第 8 步：新增數字屬性

最後，讓我們新增一個數字屬性來儲存授權金額。這可以是從預算數字到交易金額的任何內容。

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

此行新增一個名為「Authorized Amount」的屬性，其值為`123.45`。同樣，請隨意將其替換為適合您需求的任何數字。

## 結論

現在你就擁有了！您已使用 Aspose.Words for .NET 成功將自訂文件屬性新增至 Word 文件。這些屬性對於儲存特定於您的需求的附加元資料非常有用。無論您是追蹤授權詳細資訊、修訂號還是具體金額，自訂屬性都可以提供靈活的解決方案。

請記住，掌握 Aspose.Words for .NET 的關鍵是練習。因此，請繼續嘗試不同的屬性，看看它們如何增強您的文件。快樂編碼！

## 常見問題解答

### 什麼是自訂文件屬性？
自訂文件屬性是可以新增到 Word 文件中的元數據，用於儲存內建屬性未涵蓋的其他資訊。

### 我可以添加字串和數字以外的屬性嗎？
是的，您可以新增各種類型的屬性，包括布林值、日期，甚至自訂物件。

### 如何在 Word 文件中存取這些屬性？
可以使用 Aspose.Words 以程式設計方式存取自訂屬性，也可以透過文件屬性直接在 Word 中查看。

### 是否可以編輯或刪除自訂屬性？
是的，您可以使用 Aspose.Words 提供的類似方法輕鬆編輯或刪除自訂屬性。

### 可以使用自訂屬性來過濾文件嗎？
絕對地！自訂屬性非常適合根據特定元資料對文件進行分類和過濾。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
