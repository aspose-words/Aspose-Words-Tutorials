---
title: 使用 AI 模型
linktitle: 使用 AI 模型
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 透過 AI 總結文件。增強文件管理的簡單步驟。
weight: 10
url: /zh-hant/net/ai-powered-document-processing/working-with-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 AI 模型

## 介紹

歡迎來到 Aspose.Words for .NET 的迷人世界！如果您曾經希望將文件管理提升到一個新的水平，那麼您來對地方了。想像一下，只需幾行程式碼就能自動總結大型文件。聽起來很神奇，對吧？在本指南中，我們將深入探討如何使用 Aspose.Words 使用 OpenAI 的 GPT 等強大的 AI 語言模型來產生文件摘要。無論您是希望增強應用程式的開發人員還是渴望學習新知識的技術愛好者，本教學都能滿足您的需求。

## 先決條件

在我們捲起袖子開始編碼之前，您需要準備好一些必需品：

1. 已安裝 Visual Studio：確保您的電腦上安裝了 Visual Studio。如果您還沒有，可以免費下載。
  
2. .NET Framework：確保您使用的是 Aspose.Words 的相容版本的 .NET Framework。它支援 .NET Framework 和 .NET Core。

3.  Aspose.Words for .NET：您需要下載並安裝Aspose.Words。您可以取得最新版本[這裡](https://releases.aspose.com/words/net/).

4. AI 模型的 API 金鑰：要利用 AI 匯總，您需要存取 AI 模型。從 OpenAI 或 Google 等平台取得 API 金鑰。

5. C# 基礎知識：要充分利用本教學課程，必須對 C# 程式設計有基本的了解。

東西都齊全了嗎？驚人的！讓我們進入有趣的部分 - 導入我們所需的套件。

## 導入包

為了利用 Aspose.Words 的強大功能並使用 AI 模型，我們首先導入必要的套件。操作方法如下：

### 建立一個新項目

首先，啟動 Visual Studio 並建立一個新的控制台應用程式專案。

1. 打開視覺工作室。
2. 按一下“建立新專案”。
3. 根據您的設定選擇「控制台應用程式 (.NET Framework)」或「控制台應用程式 (.NET Core)」。
4. 為您的項目命名並指定位置。

### 安裝Aspose.Words和AI模型包

要使用 Aspose.Words，您需要透過 NuGet 安裝套件。

1. 在解決方案資源管理器中以滑鼠右鍵按一下您的項目，然後選擇「管理 NuGet 套件」。
2. 搜尋“Aspose.Words”並點擊“安裝”。
3. 如果您正在使用任何特定的 AI 模型套件（例如 OpenAI），請確保也安裝了它們。
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```
恭喜！準備好包後，讓我們更深入地研究我們的實現。

## 第 1 步：設定您的文件目錄

在我們的程式碼中，我們將定義目錄來管理文件的儲存位置以及輸出的去向。 

```csharp
//您的文件目錄
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
//您的 ArtifactsDir 目錄
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

- 在這裡，替換`YOUR_DOCUMENT_DIRECTORY`以及您的文件的儲存位置以及`YOUR_ARTIFACTS_DIRECTORY`您要儲存摘要文件的位置。

## 第 2 步：載入文檔

接下來，我們將把要總結的文檔載入到我們的程式中。這就像餡餅一樣簡單！方法如下：

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

- 將檔案名稱調整為您儲存的名稱。此範例假設您有兩個名為「Big document.docx」和「Document.docx」的文件。

## 第三步：初始化AI模型

我們的下一步是與人工智慧模型建立連結。這就是您之前獲得的 API 金鑰發揮作用的地方。

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

- 確保將您的 API 金鑰儲存為環境變數。這就像保證您的秘密醬汁的安全！

## 步驟 4：產生第一個文件的摘要

現在，讓我們為第一個文檔建立摘要。我們還將設定參數來定義摘要長度。

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

- 此程式碼片段總結了第一個文件並將輸出保存在您指定的工件目錄中。您可以根據自己的喜好隨意更改摘要長度！

## 步驟 5：產生多個文件的摘要

想要冒險嗎？您也可以一次匯總多個文件！操作方法如下：

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

- 就像這樣，您同時總結了兩個文件！談論效率，對嗎？

## 結論

現在你就擁有了！透過遵循本指南，您已經掌握了使用 Aspose.Words for .NET 和強大的 AI 模型總結文件的技巧。這是一項令人興奮的功能，無論是個人使用還是整合到專業應用程式中，都可以為您節省大量時間。現在就開始吧，釋放自動化的力量，見證您的生產力飆升！

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的程式庫，使開發人員能夠以程式設計方式建立、修改、轉換和渲染 Word 文件。

### 如何取得 AI 模型的 API 金鑰？
您可以從 OpenAI 或 Google 等 AI 供應商取得 API 金鑰。確保建立帳戶並按照他們的說明產生您的金鑰。

### 我可以將 Aspose.Words 用於其他文件格式嗎？
是的！ Aspose.Words 支援各種文件格式，包括 DOCX、RTF 和 HTML，提供了超出文字文件的廣泛功能。

### Aspose.Words 有免費版本嗎？
Aspose 提供免費試用版，讓您測試其功能。您可以從他們的網站下載它。

### 在哪裡可以找到有關 Aspose.Words 的更多資源？
你可以查看文檔[這裡](https://reference.aspose.com/words/net/)獲取全面的指南和見解。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
