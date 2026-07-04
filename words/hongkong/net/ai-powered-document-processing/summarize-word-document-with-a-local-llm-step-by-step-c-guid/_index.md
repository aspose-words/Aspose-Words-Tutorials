---
category: general
date: 2026-04-24
description: 使用 Aspose.Words 摘要 Word 文件並在本地執行 LLM。了解如何連接本地 LLM、生成文件摘要，並在幾分鐘內呼叫本地 LLM。
draft: false
keywords:
- summarize word document
- connect to local llm
- run llm locally
- generate document summary
- how to call local llm
language: zh-hant
og_description: 即時摘要 Word 文件，連接本地 LLM。本指南示範如何在本地執行 LLM，並使用 Aspose.Words 產生文件摘要。
og_title: 使用本地大型語言模型摘要 Word 文件 – 完整 C# 教學
tags:
- Aspose.Words
- C#
- LLM
- AI
title: 使用本地大型語言模型摘要 Word 文件 – C# 步驟指南
url: /zh-hant/net/ai-powered-document-processing/summarize-word-document-with-a-local-llm-step-by-step-c-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用本地 LLM 摘要 Word 文件 – 完整 C# 教學

曾經需要 **自動摘要 Word 文件**，但公司又不允許把資料傳到雲端嗎？你並不孤單。在許多受規範限制的環境中，唯一安全的做法就是 **在本機執行 LLM**，讓它在本地端完成繁重的運算。本教學將一步步示範如何 **連接本地 LLM**、將 Word 檔案交給 Aspose.Words，並在幾行 C# 程式碼內 **產生文件摘要**。

我們會完整說明前置條件、程式碼、原理，甚至可能遇到的坑。完成後，你就能從 C# 呼叫本地 LLM，為任何 `.docx` 檔案產生簡潔摘要，且全程不離開你的機器。

## 需要的條件

- **.NET 6+**（或若偏好傳統執行環境，可使用 .NET Framework 4.7+）  
- **Aspose.Words for .NET** NuGet 套件 (`Aspose.Words`)  
- **Aspose.Words.AI** NuGet 套件 (`Aspose.Words.AI`) – 提供 `DocumentAI` 輔助類別。  
- 一個 **本地 LLM 端點**，提供相容 OpenAI API 的服務（例如 Ollama、LM Studio，或自行部署的 vLLM）。端點需能在 `http://localhost:5000` 取得。  
- 一個範例 Word 檔 (`input.docx`)，放在程式碼可參照的資料夾內。

> **小技巧**：若尚未有本地 LLM，可執行 `ollama run llama3` – 會在 `localhost:11434` 啟動伺服器。之後可用簡易的 Nginx 代理到 `5000`，或在支援的工具上使用 `--port` 參數直接指定。

## 解決方案概觀

1. 使用 Aspose.Words 載入來源 Word 文件。  
2. 建立指向本機 LLM 的 `LocalLargeLanguageModel` 物件。  
3. 呼叫 `DocumentAI.Summarize`，讓 AI 讀取文件並回傳簡短摘要。  
4. 將結果印到主控台（或儲存到其他地方）。

就這四個步驟，每一步都會在下方說明。

## 步驟 1 – 載入要摘要的 Word 文件

首先，我們建立一個 `Document` 實例，代表磁碟上的 `.docx` 檔案。Aspose.Words 會將檔案解析成豐富的物件模型，讓我們可以存取段落、表格、圖片與中繼資料。

```csharp
using Aspose.Words;

// Step 1: Load the source document you want to summarize
// Replace "YOUR_DIRECTORY" with the actual path where input.docx lives.
string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
Document doc = new Document(inputPath);
```

**為什麼這很重要：**  
在本機載入文件可確保原始內容永不外流。Aspose.Words 也會正規化文字（移除隱藏字元、處理 Unicode），讓 LLM 接收到乾淨的輸入。

## 步驟 2 – 建立連線到本地 LLM 端點

接下來需要一個物件，負責與執行於本機的 LLM 通訊。`LocalLargeLanguageModel` 是一個薄包裝的 HTTP 客戶端，遵循 OpenAI API 規範。

```csharp
using Aspose.Words.AI;

// Step 2: Create a connection to your local Large Language Model endpoint
// The URL should point to the base address of the API (e.g., http://localhost:5000/v1)
var llm = new LocalLargeLanguageModel("http://localhost:5000");
```

**為什麼這很重要：**  
明確指定端點後，你就 **how to call local llm**，且相容任何符合規範的伺服器——Ollama、LM Studio，或自訂的 Flask 包裝。如果端點需要 API 金鑰，只要在建構子第二個參數傳入即可：`new LocalLargeLanguageModel(url, "my‑api‑key")`。

## 步驟 3 – 使用 DocumentAI 產生簡潔摘要

現在魔法發生了。`DocumentAI.Summarize` 會把文件文字串流至 LLM，請求產出短摘要，最後以字串回傳。

```csharp
// Step 3: Generate a concise summary of the document using DocumentAI
string summary = DocumentAI.Summarize(doc, llm);
```

**為什麼這很重要：**  
`DocumentAI` 會在背後處理分塊（將大型文件切成可管理的片段）與提示工程。開發者不必擔心 token 限制或格式問題，只要呼叫 `Summarize` 就能得到可讀的段落。

### 客製化提示（可選）

若需要特定語氣或長度，可傳入 `SummarizationOptions` 物件：

```csharp
var options = new SummarizationOptions
{
    MaxTokens = 150,                 // limit the summary size
    Temperature = 0.3,               // keep it deterministic
    Prompt = "Provide a bullet‑point summary in plain English."
};

string customSummary = DocumentAI.Summarize(doc, llm, options);
```

## 步驟 4 – 顯示或儲存產生的摘要

最後，我們把摘要輸出。實務上可能會寫入資料庫、寄送 Email，或以註解的方式嵌回原始 Word 文件。

```csharp
// Step 4: Display the generated summary
Console.WriteLine("=== Document Summary ===");
Console.WriteLine(summary);
```

**預期輸出**（以 2 頁的行銷簡報為例）：

```
=== Document Summary ===
The brief outlines a Q3 product launch targeting millennials, emphasizing social media outreach, influencer partnerships, and a limited‑edition colorway. Key milestones include design finalization by June 15, production start July 1, and a soft rollout on August 10.
```

若使用上方的客製化選項，則會看到項目符號而非單一段落。

## 完整範例程式

以下是一個可直接貼到 Visual Studio 或 VS Code 的單檔 Console 應用程式。

```csharp
// Program.cs
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.AI;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document you want to summarize
        // -------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // -------------------------------------------------
        // Step 2: Connect to your locally running LLM
        // -------------------------------------------------
        var llm = new LocalLargeLanguageModel("http://localhost:5000");

        // -------------------------------------------------
        // Step 3: Ask the AI to summarize the document
        // -------------------------------------------------
        string summary = DocumentAI.Summarize(doc, llm);

        // -------------------------------------------------
        // Step 4: Show the result (or store it somewhere)
        // -------------------------------------------------
        Console.WriteLine("=== Document Summary ===");
        Console.WriteLine(summary);
    }
}
```

**執行方式**

1. `dotnet new console -n Summarizer`  
2. `cd Summarizer`  
3. `dotnet add package Aspose.Words`  
4. `dotnet add package Aspose.Words.AI`  
5. 用上述程式碼取代 `Program.cs`，並自行調整 `YOUR_DIRECTORY`。  
6. 確認 LLM 伺服器已啟動（`curl http://localhost:5000/v1/models` 應回傳 JSON）。  
7. `dotnet run`

執行後，終端機會顯示摘要內容。

## 常見問題與邊緣情況

### 文件大小超過模型的 token 限制怎麼辦？

`DocumentAI` 會自動將文字切成符合模型上下文窗口的區塊，然後合併各段摘要。若想自行控制，可傳入自訂的 `ChunkingOptions` 物件。

### LLM 回傳「model not found」錯誤，該如何處理？

請確認你指向的端點確實提供名為 `default` 的模型。以 Ollama 為例，可在請求主體內指定模型，或使用 `llm = new LocalLargeLanguageModel("http://localhost:5000", "my‑model")`。

### 能把摘要寫回原始 Word 文件嗎？

當然可以。使用 Aspose.Words 的 `Comment` 類別：

```csharp
doc.Comments.Add(new Comment(doc, "AI", "Summary", DateTime.Now) { Text = summary });
doc.Save("output_with_summary.docx");
```

這樣摘要就會以「便利貼」的形式存在文件內。

### 如何保護本地 LLM 的通訊？

若端點支援 HTTPS，請改用 `https://localhost:5000`。也可以在建立 `LocalLargeLanguageModel` 時加入 Bearer Token。

## 產線使用小技巧

- **快取摘要**：以檔案雜湊為鍵，將結果存入資料庫，避免對未變更的檔案重複摘要。  
- **限制呼叫頻率**：即使是本機模型也會消耗 CPU/GPU，簡易的 semaphore 可防止過載。  
- **日誌**：記錄原始請求/回應（對敏感文字脫敏）以便除錯。  
- **錯誤處理**：將 `DocumentAI.Summarize` 包在 try/catch，若 LLM 無法使用，可退回簡易的啟始段落抽取策略。

## 結語

現在你已掌握如何 **摘要 Word 文件**，只要 **連接本地 LLM**、呼叫 Aspose.Words AI API，並在乾淨的 C# Console 應用程式中處理結果。此方式讓你 **在本機執行 LLM**、資料留在本地，同時仍能受惠於強大的自然語言摘要功能。

接下來可以嘗試將 `Summarize` 改為 `ExtractKeyPhrases` 或 `TranslateDocument`——這兩個功能同樣在 `DocumentAI` 中提供。也可以換用不同的 LLM（例如 `phi‑3`、`gemma‑2b`）比較品質與延遲。流程不變：載入 → 連線 → 呼叫 → 消費。

祝開發順利，歡迎在留言區分享使用心得或提出後續問題！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}