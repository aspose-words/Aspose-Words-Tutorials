---
title: 使用開放人工智慧模型
linktitle: 使用開放人工智慧模型
second_title: Aspose.Words 文件處理 API
description: 使用 Aspose.Words for .NET 和 OpenAI 強大的模型來解鎖高效的文件摘要。現在就深入了解這份綜合指南。
weight: 10
url: /zh-hant/net/ai-powered-document-processing/working-with-open-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用開放人工智慧模型

## 介紹

在當今的數位世界，內容為王。無論您是學生、商業專業人士還是狂熱的作家，高效操作、總結和產生文件的能力都是非常寶貴的。這就是 Aspose.Words for .NET 函式庫發揮作用的地方，它允許您像專業人士一樣管理文件。在這個綜合教程中，我們將深入探討如何利用 Aspose.Words 結合 OpenAI 模型來有效地總結文件。準備好釋放您的文件管理潛力了嗎？讓我們開始吧！

## 先決條件

在我們捲起袖子深入研究程式碼之前，您需要滿足一些要點：

### .NET框架
確保您執行的 .NET 框架版本與 Aspose.Words 相容。一般來說，.NET 5.0以上版本應該可以完美運作。

### Aspose.Words for .NET 函式庫
您需要下載並安裝 Aspose.Words 函式庫。你可以從[這個連結](https://releases.aspose.com/words/net/).

### OpenAI API 金鑰
要整合 OpenAI 的語言模型以進行文件摘要，您需要一個 API 金鑰。您可以透過在 OpenAI 平台上註冊並從帳戶設定中檢索金鑰來取得它。

### IDE 開發
設定像 Visual Studio 這樣的整合開發環境 (IDE) 是開發 .NET 應用程式的理想選擇。

### 基礎程式設計知識
對 C# 和物件導向程式設計的基本了解將幫助您更輕鬆地掌握這些概念。

## 導入包

現在我們已經把所有東西都準備好了，讓我們導入我們的包。開啟 Visual Studio 專案並新增必要的庫。您可以這樣做：

### 加入Aspose.Words包

您可以透過 NuGet 套件管理器新增 Aspose.Words 套件。操作方法如下：
- 前往工具 -> NuGet 套件管理器 -> 管理解決方案的 NuGet 套件。
- 搜尋“Aspose.Words”並點擊“安裝”。

### 新增系統環境

確保包括`System`處理環境變數的命名空間：
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### 加入Aspose.Words

然後，在 C# 檔案中包含 Aspose.Words 命名空間：
```csharp
using Aspose.Words;
```

### 新增 OpenAI 庫

如果您使用庫與 OpenAI 互動（如 REST 用戶端），請確保也包含該程式庫。您可能需要透過 NuGet 添加它，就像我們添加 Aspose.Words 一樣。

現在我們已經準備好了環境並導入了必要的套件，讓我們逐步分解文件摘要流程。

## 第 1 步：定義您的文件目錄

在開始使用文件之前，您需要設定文件和工件所在的目錄：

```csharp
//您的文件目錄
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
//您的文物目錄
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
這使您的程式碼更易於管理，因為您可以根據需要輕鬆更改路徑。這`MyDir`是您輸入文件的儲存位置，而`ArtifactsDir`是您儲存產生的摘要的位置。

## 第 2 步：載入您的文檔

接下來，您將載入要總結的文件。這對 Aspose.Words 來說很簡單：

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
確保您的文件名稱與您打算使用的名稱相匹配，否則，您將遇到錯誤！

## 步驟 3： 取得您的 API 金鑰

現在您的文件已加載，是時候提取您的 OpenAI API 金鑰了。您將從環境變數中獲取它以確保其安全：
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
安全地管理您的 API 金鑰對於防止未經授權的使用者至關重要。

## 步驟4：建立OpenAI模型實例

準備好 API 金鑰後，您現在可以建立 OpenAI 模型的實例。對於文件摘要，我們將使用 Gpt4OMini 模型：

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
此步驟本質上是建立總結文件所需的智力，讓您能夠存取人工智慧驅動的摘要。

## 第 5 步：總結單一文檔

我們先來總結一下第一個文檔。這就是魔法發生的地方：

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
在這裡，我們使用的是`Summarize`模型的方法。這`SummaryLength.Short`參數指定我們需要一個簡短的摘要 - 非常適合快速概述！

## 第 6 步：總結多個文檔

感覺雄心勃勃嗎？您可以一次總結多個文件。看看它是多麼容易：

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
此功能對於比較多個文件特別方便。也許您正在準備一次會議，需要從幾份冗長的報告中獲得簡潔的筆記。這是你最好的新朋友！

## 結論

使用 Aspose.Words for .NET 和 OpenAI 總結文件不僅是一項有益的技能，而且是一項有益的技能。這是非常有力量的。透過遵循本指南，您可以將冗長、複雜的文字轉化為簡潔的摘要，從而節省時間和精力。無論您是要確保客戶的清晰度還是準備重要的演示，您現在都可以使用工具來有效地完成任務。

那麼，您還在等什麼呢？充滿信心地深入研究您的文檔，讓技術完成繁重的工作！

## 常見問題解答

### 什麼是 Aspose.Words for .NET？  
Aspose.Words for .NET 是一個功能強大的程式庫，使開發人員能夠以程式設計方式建立、操作和轉換文件。

### OpenAI 需要 API 金鑰嗎？  
是的，您必須擁有有效的 OpenAI API 金鑰才能使用其模型存取摘要功能。

### 我可以同時總結多個文件嗎？  
絕對地！您可以在一次呼叫中匯總多個文檔，這非常適合產生大量報告。

### 如何安裝 Aspose.Words？  
您可以透過 Visual Studio 中的 NuGet 套件管理器搜尋「Aspose.Words」來安裝它。

### Aspose.Words 有免費試用版嗎？  
是的，您可以透過他們的網站免費試用 Aspose.Words[網站](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
