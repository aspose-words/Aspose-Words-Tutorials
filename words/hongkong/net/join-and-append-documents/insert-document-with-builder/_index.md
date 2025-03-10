---
title: 使用生成器插入文檔
linktitle: 使用生成器插入文檔
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 合併兩個 Word 文件。使用 DocumentBuilder 插入文件並保留格式的逐步指南。
weight: 10
url: /zh-hant/net/join-and-append-documents/insert-document-with-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用生成器插入文檔

## 介紹

因此，您有兩個 Word 文檔，並且您希望將它們合併為一個。您可能會想，“有沒有一種簡單的方法可以透過程式設計來完成此操作？”絕對地！今天，我將引導您完成使用 Aspose.Words for .NET 程式庫將一個文件插入另一個文件的過程。這種方法非常方便，特別是當您處理大型文件或需要自動化流程時。讓我們開始吧！

## 先決條件

在開始之前，讓我們確保您已擁有所需的一切：

1.  Aspose.Words for .NET：如果還沒有，您可以從以下位置下載：[這裡](https://releases.aspose.com/words/net/).
2. 開發環境：確保安裝了 Visual Studio 或任何其他適當的 IDE。
3. C# 基礎：稍微熟悉一下 C# 會有很大幫助。

## 導入命名空間

首先，您需要匯入必要的命名空間來存取 Aspose.Words 庫功能。您可以這樣做：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

現在我們已經具備了先決條件，讓我們逐步分解這個過程。

## 第 1 步：設定您的文件目錄

在開始編碼之前，您需要設定文件目錄的路徑。這是儲存來源文件和目標文件的位置。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`與您的文件所在的實際路徑。這將幫助程式輕鬆找到您的文件。

## 第 2 步：載入來源文檔和目標文檔

接下來，我們需要載入我們想要使用的文件。在此範例中，我們有一個來源文件和一個目標文件。

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

在這裡，我們使用的是`Document` Aspose.Words 庫中的類別來載入我們的文件。確保檔案名稱與目錄中的檔案名稱相符。

## 第 3 步：建立 DocumentBuilder 對象

這`DocumentBuilder`類別是Aspose.Words 函式庫中的一個強大工具。它允許我們導航和操作文件。

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

在這一步中，我們創建了一個`DocumentBuilder`我們的目標文檔的物件。這將幫助我們將內容插入到文件中。

## 第 4 步：移至文件末尾

在插入來源文件之前，我們需要將建構器遊標移至目標文件的末端。

```csharp
builder.MoveToDocumentEnd();
```

這可確保將來源文件插入到目標文件的末端。

## 第 5 步：插入分頁符

為了保持整潔，我們在插入來源文件之前添加一個分頁符號。這將在新頁面上開始來源文件的內容。

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

分頁符號可確保來源文件內容從新頁面開始，使合併的文件看起來很專業。

## 步驟 6：插入來源文檔

現在是令人興奮的部分 - 實際上將來源文件插入目標文件中。

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

使用`InsertDocument`方法，我們可以將整個來源文件插入目標文件中。這`ImportFormatMode.KeepSourceFormatting`確保保留來源文件的格式。

## 步驟7：儲存合併的文檔

最後，讓我們儲存合併的文檔。這會將來源文檔和目標文檔合併到一個文件中。

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

透過儲存文檔，我們完成了合併兩個文檔的過程。您的新文件現已準備就緒並保存在指定的目錄中。

## 結論

現在你就擁有了！您已使用 Aspose.Words for .NET 成功將一個文件插入到另一個文件中。這種方法不僅高效，而且保留了兩個文件的格式，確保無縫合併。無論您正在處理一次性專案還是需要自動化文件處理，Aspose.Words for .NET 都能滿足您的需求。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？  
Aspose.Words for .NET 是一個功能強大的程式庫，可讓開發人員以程式設計方式建立、編輯、轉換和操作 Word 文件。

### 我可以保留來源文件的格式嗎？  
是的，透過使用`ImportFormatMode.KeepSourceFormatting`，當來源文件插入目標文件時，會保留來源文件的格式。

### 我需要許可證才能使用 Aspose.Words for .NET 嗎？  
是的，Aspose.Words for .NET 需要完整功能的授權。你可以獲得一個[臨時執照](https://purchase.aspose.com/temporary-license/)進行評估。

### 我可以自動化這個流程嗎？  
絕對地！所描述的方法可以合併到更大的應用程式中以自動化文件處理任務。

### 我可以在哪裡找到更多資源和支援？  
欲了解更多信息，您可以查看[文件](https://reference.aspose.com/words/net/)，或訪問[支援論壇](https://forum.aspose.com/c/words/8)尋求幫助。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
