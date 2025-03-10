---
title: 使用 Google AI 模型
linktitle: 使用 Google AI 模型
second_title: Aspose.Words 文件處理 API
description: 使用 Aspose.Words for .NET 和 Google AI 提昇文件處理能力，輕鬆建立簡潔的摘要。
weight: 10
url: /zh-hant/net/ai-powered-document-processing/working-with-google-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Google AI 模型

## 介紹

在本文中，我們將逐步探索如何使用 Aspose.Words 和 Google 的 AI 模型來總結文件。無論您是想濃縮一份冗長的報告還是從多個來源提取見解，我們都能滿足您的需求。

## 先決條件

在深入實踐部分之前，讓我們確保您已做好成功的準備。這是您需要的：

1. C# 和 .NET 的基礎知識：熟悉程式設計概念將幫助您更好地掌握範例。
   
2.  Aspose.Words for .NET 函式庫：這個功能強大的函式庫可讓您無縫地建立和操作 Word 文件。你可以[在這裡下載](https://releases.aspose.com/words/net/).

3. Google AI 模型的 API 金鑰：要使用 AI 模型，您需要一個 API 金鑰進行驗證。將其安全地儲存在您的環境變數中。

4. 開發環境：確保您設定了有效的 .NET 環境（Visual Studio 或任何其他 IDE）。

5. 範例文件：您需要範例Word 文件（例如「Big document.docx」、「Document.docx」）來測試摘要。

現在我們已經介紹了基礎知識，讓我們深入研究程式碼！

## 導入包

要使用 Aspose.Words 並整合 Google AI 模型，您需要匯入必要的命名空間。您可以按照以下方法執行此操作：

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

現在您已經匯入了必要的套件，讓我們逐步分解總結文件的流程。

## 第 1 步：設定您的文件目錄

在處理文件之前，我們需要指定文件所在的位置。此步驟對於確保 Aspose.Words 可以存取文件至關重要。

```csharp
//您的文件目錄
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
//您的 ArtifactsDir 目錄
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

代替`"YOUR_DOCUMENT_DIRECTORY"`和`"YOUR_ARTIFACTS_DIRECTORY"`與系統上儲存文件的實際路徑。這將作為讀取和保存文件的基準。

## 第 2 步：載入文檔

接下來，我們需要載入我們想要總結的文檔。在本例中，您將載入我們先前指定的兩個文件。

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

這`Document` Aspose.Words 中的類別可讓您將 Word 檔案載入到記憶體中。確保檔案名稱與目錄中的實際文件匹配，否則您將遇到文件未找到錯誤！

## 第 3 步：檢索 API 金鑰

要使用 AI 模型，您需要檢索 API 金鑰。這是您存取 Google AI 服務的通行證。

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

這行程式碼會取得您儲存在環境變數中的 API 金鑰。出於安全原因，最好將 API 金鑰等敏感資訊保留在程式碼之外。

## 步驟4：建立AI模型實例

現在，是時候建立 AI 模型的實例了。您可以在此處選擇要使用的模型 - 在本例中，我們選擇 GPT-4 Mini 模型。

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

此行設定您將用於文件摘要的 AI 模型。一定要諮詢一下[文件](https://reference.aspose.com/words/net/)有關不同型號及其功能的詳細資訊。

## 第 5 步：總結單一文檔

讓我們重點總結一下第一個文件。我們可以選擇在這裡獲取簡短的摘要。

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

在這一步驟中，我們使用`Summarize`方法從 AI 模型實例取得第一個文件的壓縮。摘要長度設定為較短，但您可以根據需要進行自訂。最後，匯總文件將保存到您的工件目錄中。

## 第 6 步：總結多個文檔

想要一次總結多個文件？ Aspose.Words 也讓這件事變得簡單！

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

在這裡，我們稱之為`Summarize`再次使用方法，但這次使用文件數組。這將為您提供一個包含這兩個文件的本質的長摘要。就像以前一樣，結果保存在指定的工件目錄中。

## 結論

現在你就擁有了！您已成功設定了使用 Aspose.Words for .NET 和 Google 的 AI 模型來彙總文件的環境。從載入文件到建立簡明摘要，這些步驟提供了一種有效管理大量文字的簡化方法。

## 常見問題解答

### 什麼是 Aspose.Words？
Aspose.Words 是一個功能強大的程式庫，可使用 .NET 建立、修改和轉換 Word 文件。

### 如何取得 Google AI 的 API 金鑰？
您通常可以透過註冊 Google Cloud 並啟用必要的 API 服務來取得 API 金鑰。

### 我可以同時總結多個文件嗎？
是的！如所示，您可以將文件陣列傳遞給摘要方法。

### 我可以建立哪些類型的摘要？
您可以根據需要選擇短摘要、中摘要和長摘要。

### 在哪裡可以找到更多 Aspose.Words 資源？
查看[文件](https://reference.aspose.com/words/net/)取得更多範例和指導。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
