---
"description": "使用 Aspose.Words for .NET 和 OpenAI 強大的模型實現高效率的文件摘要。立即深入了解這份綜合指南。"
"linktitle": "使用開放的人工智慧模型"
"second_title": "Aspose.Words文件處理API"
"title": "使用開放的人工智慧模型"
"url": "/zh-hant/net/ai-powered-document-processing/working-with-open-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用開放的人工智慧模型

## 介紹

在當今的數位世界中，內容為王。無論您是學生、商務人士還是熱心作家，高效地操作、總結和產生文件的能力都是無價的。這就是 Aspose.Words for .NET 函式庫發揮作用的地方，它允許您像專業人士一樣管理文件。在本綜合教程中，我們將深入探討如何利用 Aspose.Words 結合 OpenAI 模型來有效地總結文件。準備好釋放您的文件管理潛力了嗎？讓我們開始吧！

## 先決條件

在我們捲起袖子並深入研究程式碼之前，您需要準備好一些必需品：

### .NET 框架
確保您執行的 .NET 框架版本與 Aspose.Words 相容。一般來說，.NET 5.0 及以上版本應該可以完美運作。

### Aspose.Words for .NET 函式庫
您需要下載並安裝 Aspose.Words 函式庫。您可以從 [此連結](https://releases。aspose.com/words/net/).

### OpenAI API 金鑰
要整合 OpenAI 的語言模型進行文件摘要，您需要一個 API 金鑰。您可以透過在 OpenAI 平台上註冊並從您的帳戶設定中檢索您的金鑰來獲取它。

### 開發IDE
擁有像 Visual Studio 這樣的整合開發環境 (IDE) 對於開發 .NET 應用程式來說是理想的。

### 基本程式設計知識
對 C# 和物件導向程式設計的基本了解將幫助您更輕鬆地掌握概念。

## 導入包

現在我們已經準備好一切，讓我們導入我們的包裹。開啟您的 Visual Studio 專案並新增必要的庫。您可以按照以下步驟操作：

### 加入 Aspose.Words 包

您可以透過 NuGet 套件管理器新增 Aspose.Words 套件。以下是操作方法：
- 前往工具->NuGet 套件管理器->管理解決方案的 NuGet 套件。
- 搜尋“Aspose.Words”並點擊安裝。

### 新增系統環境

確保包含 `System` 命名空間來處理環境變數：
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### 加入 Aspose.Words

然後，在 C# 檔案中包含 Aspose.Words 命名空間：
```csharp
using Aspose.Words;
```

### 新增 OpenAI 庫

如果您使用庫與 OpenAI 互動（如 REST 用戶端），請確保也將其包含在內。您可能需要透過 NuGet 添加它，就像我們添加 Aspose.Words 一樣。

現在我們已經準備好環境並導入了必要的套件，讓我們逐步分解文件摘要流程。

## 步驟 1：定義文件目錄

在開始處理文件之前，您需要設定文件和工件所在的目錄：

```csharp
// 您的文件目錄
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// 您的 Artifacts 目錄
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
這使得您的程式碼更易於管理，因為您可以根據需要輕鬆更改路徑。這 `MyDir` 是儲存輸入文件的地方，而 `ArtifactsDir` 是您保存產生的摘要的地方。

## 第 2 步：載入文檔

接下來，您將載入想要匯總的文件。使用 Aspose.Words 非常簡單：

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
確保您的文件名稱與您想要使用的名稱相匹配，否則您將遇到錯誤！

## 步驟 3：取得您的 API 金鑰

現在您的文件已加載，是時候提取您的 OpenAI API 金鑰了。您可以從環境變數中獲取它以確保其安全：
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
安全地管理您的 API 金鑰對於阻止未經授權的使用者至關重要。

## 步驟 4：建立 OpenAI 模型實例

準備好 API 金鑰後，您現在可以建立 OpenAI 模型的實例。對於文件摘要，我們將使用 Gpt4OMini 模型：

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
此步驟實質上設定了總結文件所需的腦力，讓您可以進行人工智慧驅動的總結。

## 步驟5：總結單一文檔

我們先來總結一下第一份文件。這就是奇蹟發生的地方：

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
這裡我們使用 `Summarize` 模型的方法。這 `SummaryLength.Short` 參數指定我們想要一個簡短的摘要——非常適合快速概覽！

## 步驟 6：彙整多個文檔

有雄心壯志嗎？您可以一次匯總多個文件。看看它有多簡單：

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
此功能對於比較多個文件特別方便。也許您正在準備會議並需要幾份冗長的報告的簡明筆記。這是你最好的新朋友！

## 結論

使用 Aspose.Words for .NET 和 OpenAI 總結文件不僅是一項有益的技能；這非常有力。遵循本指南，您可以將冗長複雜的文字轉換為簡潔的摘要，從而節省您的時間和精力。無論您是在確保為客戶提供清晰的資訊還是在準備重要的演示，您現在都擁有了高效能完成工作的工具。

那麼，您還在等什麼呢？自信地深入研究您的文檔，讓技術完成繁重的工作！

## 常見問題解答

### 什麼是 Aspose.Words for .NET？  
Aspose.Words for .NET 是一個強大的程式庫，使開發人員能夠以程式設計方式建立、操作和轉換文件。

### 我需要 OpenAI 的 API 金鑰嗎？  
是的，您必須擁有有效的 OpenAI API 金鑰才能使用其模型存取摘要功能。

### 我可以一次匯總多個文件嗎？  
絕對地！您可以在一次呼叫中匯總多個文檔，這對於大量報告來說是理想的。

### 如何安裝 Aspose.Words？  
您可以透過 Visual Studio 中的 NuGet 套件管理器搜尋「Aspose.Words」來安裝它。

### Aspose.Words 有免費試用版嗎？  
是的，您可以透過他們的 [網站](https://releases。aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}