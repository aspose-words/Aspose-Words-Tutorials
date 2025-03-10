---
title: 取消連結頁眉頁腳
linktitle: 取消連結頁眉頁腳
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 取消連結 Word 文件中的頁首和頁尾。請按照我們詳細的逐步指南來掌握文件操作。
weight: 10
url: /zh-hant/net/join-and-append-documents/unlink-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 取消連結頁眉頁腳

## 介紹

在文件處理領域，保持頁首和頁尾一致有時是一個挑戰。無論您是要合併文件還是只是希望為不同的部分提供不同的頁首和頁腳，了解如何取消它們的連結至關重要。今天，我們將深入探討如何使用 Aspose.Words for .NET 來實現這一目標。我們將逐步分解它，以便您可以輕鬆地進行操作。準備好掌握文件操作了嗎？讓我們開始吧！

## 先決條件

在我們深入了解細節之前，您需要滿足以下條件：

-  Aspose.Words for .NET Library：您可以從[Aspose 發佈頁面](https://releases.aspose.com/words/net/).
- .NET Framework：確保您安裝了相容的 .NET 框架。
- IDE：Visual Studio 或任何其他 .NET 相容的整合開發環境。
- 對 C# 的基本了解：您需要對 C# 程式語言有基本的了解。

## 導入命名空間

首先，請確保在專案中匯入必要的命名空間。這將使您能夠存取 Aspose.Words 庫及其功能。

```csharp
using Aspose.Words;
```

讓我們將流程分解為可管理的步驟，以協助您取消 Word 文件中的頁首和頁尾的連結。

## 第 1 步：設定您的項目

首先，您需要設定專案環境。開啟 IDE 並建立一個新的 .NET 專案。新增對您先前下載的 Aspose.Words 函式庫的參考。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步驟2：載入來源文檔

接下來，您需要載入要修改的來源文件。該文件的頁首和頁尾將取消連結。

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## 第 3 步：載入目標文檔

現在，載入目標文檔，在取消連結頁首和頁尾後，您將在其中附加來源文檔。

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## 步驟 4：取消頁首和頁尾的鏈接

這一步至關重要。若要取消來源文件的頁首和頁尾與目標文件的頁首和頁尾的鏈接，您將使用`LinkToPrevious`方法。此方法可確保頁首和頁尾不會保留到附加文件中。

```csharp
//取消連結來源文件中的頁首和頁尾以阻止此行為
//繼續目標文件的頁首和頁尾。
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## 第 5 步：附加來源文檔

取消頁首和頁尾的連結後，您可以將來源文件附加到目標文件。使用`AppendDocument`方法並將匯入格式模式設為`KeepSourceFormatting`保持來源文件的原始格式。

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## 第 6 步：儲存最終文檔

最後，儲存新建立的文檔。該文檔會將來源文檔的內容附加到目標文檔，但頁首和頁尾未連結。

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.UnlinkHeadersFooters.docx");
```

## 結論

現在你就擁有了！透過執行這些步驟，您已成功取消來源文件中頁首和頁尾的鏈接，並使用 Aspose.Words for .NET 將其附加到目標文件。當您處理不同部分需要不同頁首和頁尾的複雜文件時，此技術特別有用。快樂編碼！

## 常見問題解答

### 什麼是 Aspose.Words for .NET？  
Aspose.Words for .NET 是一個功能強大的程式庫，用於在 .NET 應用程式中處理 Word 文件。它允許開發人員以程式設計方式建立、修改、轉換和列印文件。

### 我可以僅取消特定部分的頁首和頁尾連結嗎？  
是的，您可以透過造訪取消連結特定部分的頁首和頁腳`HeadersFooters`所需部分的屬性並使用`LinkToPrevious`方法。

### 是否可以保持來源文件的原始格式？  
是的，附加來源文件時，請使用`ImportFormatMode.KeepSourceFormatting`保留原始格式的選項。

### 我可以將 Aspose.Words for .NET 與 C# 以外的其他 .NET 語言一起使用嗎？  
絕對地！ Aspose.Words for .NET 可與任何 .NET 語言一起使用，包括 VB.NET 和 F#。

### 在哪裡可以找到有關 Aspose.Words for .NET 的更多文件和支援？  
您可以在以下位置找到全面的文檔[Aspose.Words for .NET 文件頁面](https://reference.aspose.com/words/net/) ，並且支援可在[Aspose論壇](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
