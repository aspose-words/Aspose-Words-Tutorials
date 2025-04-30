---
"description": "使用 Aspose.Words for .NET 和 Google AI 提升您的文件處理能力，輕鬆建立簡潔的摘要。"
"linktitle": "使用 Google AI 模型"
"second_title": "Aspose.Words文件處理API"
"title": "使用 Google AI 模型"
"url": "/zh-hant/net/ai-powered-document-processing/working-with-google-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Google AI 模型

## 介紹

在本文中，我們將逐步探討如何使用 Aspose.Words 和 Google 的 AI 模型來總結文件。無論您是想濃縮一份冗長的報告還是從多個來源提取見解，我們都能滿足您的需求。

## 先決條件

在深入實際操作之前，讓我們先確保您已做好成功的準備。您需要準備以下物品：

1. C# 和 .NET 的基礎知識：熟悉程式設計概念將幫助您更好地掌握範例。
   
2. Aspose.Words for .NET Library：這個強大的程式庫可讓您無縫地建立和操作 Word 文件。你可以 [點此下載](https://releases。aspose.com/words/net/).

3. Google AI 模型的 API 金鑰：要使用 AI 模型，您需要一個 API 金鑰進行驗證。將其安全地儲存在您的環境變數中。

4. 開發環境：確保您已設定可用的 .NET 環境（Visual Studio 或任何其他 IDE）。

5. 範例文件：您需要範例 Word 文件（例如「Big document.docx」、「Document.docx」）來測試摘要。

現在我們已經介紹了基礎知識，讓我們深入研究程式碼！

## 導入包

要使用 Aspose.Words 並整合 Google AI 模型，您需要匯入必要的命名空間。您可以按照以下步驟操作：

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

現在您已經匯入了必要的套件，讓我們逐步分解匯總文件的過程。

## 步驟 1：設定文檔目錄

在我們處理文件之前，我們需要指定文件所在的位置。此步驟對於確保 Aspose.Words 可以存取文件至關重要。

```csharp
// 您的文件目錄
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// 您的 ArtifactsDir 目錄
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

代替 `"YOUR_DOCUMENT_DIRECTORY"` 和 `"YOUR_ARTIFACTS_DIRECTORY"` 與您系統中儲存文件的實際路徑。這將作為閱讀和保存文件的基準。

## 步驟2：載入文檔

接下來，我們需要載入我們想要匯總的文檔。在這種情況下，您將載入我們之前指定的兩個文件。

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

這 `Document` Aspose.Words 中的類別可讓您將 Word 檔案載入到記憶體中。確保檔案名稱與目錄中的實際文件相匹配，否則您將遇到文件未找到錯誤！

## 步驟 3：檢索 API 金鑰

要使用 AI 模型，您需要檢索您的 API 金鑰。這是您存取 Google AI 服務的通行證。

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

這行程式碼會取得您儲存在環境變數中的 API 金鑰。出於安全原因，最好將 API 金鑰等敏感資訊保留在程式碼之外。

## 步驟4：建立AI模型實例

現在，是時候建立 AI 模型的實例了。您可以在此處選擇要使用的模型—在此範例中，我們選擇 GPT-4 Mini 模型。

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

此行設定了您將用於文件摘要的 AI 模型。請務必諮詢 [文件](https://reference.aspose.com/words/net/) 了解不同型號及其功能的詳細資訊。

## 步驟5：總結單一文檔

讓我們重點總結一下第一份文件。我們可以選擇在這裡獲取簡短的摘要。

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

在此步驟中，我們使用 `Summarize` 方法從AI模型實例中取得第一個文件的濃縮。摘要長度設定為短，但您可以根據需要自訂。最後，將匯總的文件儲存到您的工件目錄中。

## 步驟 6：彙整多個文檔

想要一次匯總多個文件嗎？ Aspose.Words 也讓這件事變得簡單！

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

在這裡，我們稱之為 `Summarize` 方法，但這次使用文檔數組。這將為您提供一份概括這兩個文件精髓的長篇摘要。與先前一樣，結果保存在指定的工件目錄中。

## 結論

就是這樣！您已成功設定使用 Aspose.Words for .NET 和 Google 的 AI 模型來彙總文件的環境。從載入文件到建立簡潔的摘要，這些步驟提供了一種有效管理大量文字的簡化方法。

## 常見問題解答

### 什麼是 Aspose.Words？
Aspose.Words 是一個功能強大的函式庫，可以使用 .NET 建立、修改和轉換 Word 文件。

### 如何取得 Google AI 的 API 金鑰？
您通常可以透過註冊 Google Cloud 並啟用必要的 API 服務來取得 API 金鑰。

### 我可以一次匯總多個文件嗎？
是的！如所示，您可以將文件陣列傳遞給摘要方法。

### 我可以建立哪些類型的摘要？
您可以根據需要選擇短摘要、中摘要和長摘要。

### 在哪裡可以找到更多 Aspose.Words 資源？
查看 [文件](https://reference.aspose.com/words/net/) 以獲取更多範例和指導。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}