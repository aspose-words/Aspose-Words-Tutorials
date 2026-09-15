---
category: general
date: 2026-09-14
description: 使用 C# 以 AI 摘要 Word 文件——學習如何使用 OpenAI 或 Google 服務產生精簡摘要，並看看只需幾行程式碼即可用
  AI 摘要文字。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- summarize word document
- summarize text with ai
- document summarization google
language: zh-hant
lastmod: 2026-09-14
og_description: 使用 AI 在 C# 中摘要 Word 文件。本教學示範如何呼叫 OpenAI 或 Google 的摘要服務提供者，並獲得簡潔的結果。
og_image_alt: Console window displaying a short AI‑generated summary of a Word document
og_title: 使用 AI 摘要 Word 文件 – 快速 C# 指南
schemas:
- author: GroupDocs
  dateModified: '2026-09-14'
  description: Summarize Word document using AI in C# – learn to generate concise
    summaries with OpenAI or Google providers and see how to summarize text with AI
    in just a few lines.
  headline: Summarize Word document with AI in C#
  type: TechArticle
- description: Summarize Word document using AI in C# – learn to generate concise
    summaries with OpenAI or Google providers and see how to summarize text with AI
    in just a few lines.
  name: Summarize Word document with AI in C#
  steps:
  - name: Load the source `.docx` file.
    text: Load the source `.docx` file.
  - name: Define summarization options (provider and sentence limit).
    text: Define summarization options (provider and sentence limit).
  - name: Call the summarizer to produce a short text.
    text: Call the summarizer to produce a short text.
  - name: Write the result to the console.
    text: Write the result to the console.
  type: HowTo
tags:
- AI summarization
- C#
- Word processing
title: 在 C# 中使用 AI 摘要 Word 文件
url: /zh-hant/net/ai-powered-document-processing/summarize-word-document-with-ai-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 AI 在 C# 中摘要 Word 文件

如果您需要自動 **摘要 Word 文件** 內容，本指南將為您展示一個完整、可直接執行的解決方案。您將看到如何載入 `.docx` 檔案、設定摘要請求，並使用 OpenAI 或 Google 作為 AI 供應商取得簡潔的摘要。

此範例使用流行的 `GroupDocs.Summarization` 函式庫，但相同的模式也適用於任何提供 `DocumentSummarizer` API 的函式庫。完成本教學後，您只需幾行 C# 程式碼即可 **使用 AI 摘要文字**。

## 您將學習到

- 安裝所需的 NuGet 套件。
- 將 Word 文件（`.docx`）載入記憶體。
- 選擇摘要供應商（OpenAI 或 Google）並設定句子上限。
- 產生摘要並在主控台顯示。
- 處理常見錯誤，例如檔案遺失或不支援的供應商。

> **先決條件：** .NET 6 或更新版本、基本的 C# 知識，以及所選供應商的 API 金鑰（OpenAI 或 Google）。

## 安裝摘要函式庫

首先，將 `GroupDocs.Summarization` 套件加入您的專案：

```bash
dotnet add package GroupDocs.Summarization
```

此套件包含稍後程式碼中會使用的 `Document`、`SummarizerOptions` 與 `DocumentSummarizer` 類型。

## Word 文件摘要 – 概觀

核心工作流程包含四個步驟：

1. 載入來源 `.docx` 檔案。
2. 定義摘要選項（供應商與句子上限）。
3. 呼叫摘要器產生簡短文字。
4. 將結果寫入主控台。

以下將逐一詳細說明每個步驟。

## 步驟 1：載入來源文件

```csharp
using System;
using GroupDocs.Summarization;
using GroupDocs.Summarization.Options;

class Program
{
    static void Main()
    {
        // Replace with the actual path to your .docx file
        const string inputPath = @"C:\Docs\input.docx";

        // Verify that the file exists before attempting to load it
        if (!System.IO.File.Exists(inputPath))
        {
            Console.Error.WriteLine($"Error: The file \"{inputPath}\" was not found.");
            return;
        }

        // Load the Word document into a Document object
        Document doc = new Document(inputPath);
        Console.WriteLine("Document loaded successfully.");
```

**為什麼重要：** 將檔案載入 `Document` 物件可抽象化底層的 Word 格式，使摘要器能以純文字處理，無論文件中包含表格、影像或註腳。

## 步驟 2：定義摘要選項（選擇供應商與限制句子數）

```csharp
        // Configure summarization settings
        SummarizerOptions options = new SummarizerOptions
        {
            // Switch between OpenAI and Google providers as needed
            Provider = SummarizerProvider.OpenAI,   // or SummarizerProvider.Google
            MaxSentences = 5                        // Desired number of sentences in the summary
        };

        Console.WriteLine($"Summarization will use {options.Provider} and return up to {options.MaxSentences} sentences.");
```

**為什麼重要：**  
- **供應商選擇** 決定使用哪個 AI 服務來處理文字。OpenAI 與 Google 模型皆接受相同的輸入，但在價格、延遲與語言支援上有所不同。  
- **`MaxSentences`** 讓您控制輸出長度，當您只需要快速預覽而非完整摘要時，這點尤為重要。

## 步驟 3：使用選定的 AI 供應商產生摘要

```csharp
        try
        {
            // The static Summarize method contacts the chosen AI service and returns a concise summary
            string summary = DocumentSummarizer.Summarize(doc, options);
            Console.WriteLine("\nSummary:");
            Console.WriteLine(summary);
        }
        catch (Exception ex)
        {
            // Provide a clear error message for common failure points
            Console.Error.WriteLine($"Summarization failed: {ex.Message}");
        }
    }
}
```

**為什麼重要：** `Summarize` 呼叫會處理所有繁重工作——分詞、模型推論與後處理——讓您不必自行撰寫提示詞或管理 HTTP 請求。`try/catch` 區塊可確保網路錯誤、驗證問題或不支援的文件功能能清楚回報。

## 步驟 4：將產生的摘要輸出至主控台

前一步的 `Console.WriteLine` 陳述已經顯示結果，但您也可以將摘要寫入檔案以供日後分析：

```csharp
        // Optional: save the summary to a .txt file
        const string outputPath = @"C:\Docs\summary.txt";
        System.IO.File.WriteAllText(outputPath, summary);
        Console.WriteLine($"\nSummary saved to \"{outputPath}\".");
```

**為什麼重要：** 儲存摘要可支援批次處理流程，讓您能為數十份文件產生摘要並與原始檔案一起保存。

## 使用 OpenAI 以 AI 摘要文字

如果您想使用 OpenAI 的 GPT‑4 模型，請明確設定供應商：

```csharp
options.Provider = SummarizerProvider.OpenAI;
```

請確保環境變數 `OPENAI_API_KEY` 已設定，或以程式方式配置金鑰：

```csharp
SummarizerOptions.ApiKey = "sk-YourOpenAIKey";
```

OpenAI 通常產出更流暢的文字，適合用於行銷文案或主管簡報。

## Google 文件摘要 – 使用 Google 供應商

對於已在 Google Cloud 投入的組織，可切換至 Google 供應商：

```csharp
options.Provider = SummarizerProvider.Google;
```

設定 Google API 金鑰：

```csharp
SummarizerOptions.ApiKey = "AIzaYourGoogleKey";
```

Google 的 PaLM 模型在多語言摘要方面表現優異，且對於大量工作負載而言成本更具效益。

## 邊緣情況與最佳實踐技巧

| Situation | Recommended handling |
|-----------|----------------------|
| **大型文件 (>10 MB)** | 增加 `MaxSentences`，或將文件分割成多個章節，分別摘要，以避免 token 限制。 |
| **缺少 API 金鑰** | 函式庫會拋出 `AuthenticationException`。在呼叫 `Summarize` 前先驗證金鑰。 |
| **不支援的檔案格式** | `Document` 只支援 `.docx`、`.pdf` 與純文字。請先使用轉換函式庫將其他格式（例如 `.doc`）轉為 `.docx`。 |
| **網路延遲** | 若應用程式必須保持回應，請將呼叫包裝成非同步版本（`SummarizeAsync`）。 |

**專業提示：** 為不常變動的文件快取摘要。儲存檔案內容的雜湊值，並重複使用快取結果，以避免不必要的 API 呼叫。

## 完整、可執行的範例

以下是完整程式碼，您可直接複製貼上至新的主控台專案（`dotnet new console`），在安裝 NuGet 套件並設定 API 金鑰後執行。

```csharp
using System;
using GroupDocs.Summarization;
using GroupDocs.Summarization.Options;

namespace WordSummarizer
{
    class Program
    {
        static void Main()
        {
            const string inputPath = @"C:\Docs\input.docx";
            const string outputPath = @"C:\Docs\summary.txt";

            if (!System.IO.File.Exists(inputPath))
            {
                Console.Error.WriteLine($"Error: The file \"{inputPath}\" was not found.");
                return;
            }

            Document doc = new Document(inputPath);
            Console.WriteLine("Document loaded successfully.");

            SummarizerOptions options = new SummarizerOptions
            {
                Provider = SummarizerProvider.OpenAI, // change to Google if preferred
                MaxSentences = 5
            };

            // Set your API key (environment variable or direct assignment)
            // SummarizerOptions.ApiKey = "YOUR_API_KEY";

            try
            {
                string summary = DocumentSummarizer.Summarize(doc, options);
                Console.WriteLine("\nSummary:");
                Console.WriteLine(summary);

                System.IO.File.WriteAllText(outputPath, summary);
                Console.WriteLine($"\nSummary saved to \"{outputPath}\".");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Summarization failed: {ex.Message}");
            }
        }
    }
}
```

**預期輸出（範例）：**

```
Document loaded successfully.
Summarization will use OpenAI and return up to 5 sentences.

Summary:
The report outlines Q3 revenue growth of 12% driven by new product launches. Customer churn decreased to 3%, the lowest in two years. Marketing spend rose by 8% to support brand awareness. The executive team recommends expanding into the APAC market. Risks include supply‑chain delays and regulatory changes.
```

## 結論

您現在已擁有一套完整、可投入生產環境的 **使用 AI 摘要 Word 文件** 內容的方法。只要將 `SummarizerProvider.OpenAI` 換成 `SummarizerProvider.Google`，即可在不修改其他程式碼的情況下執行 **Google 風格的文件摘要**。可嘗試不同的 `MaxSentences` 設定、批次處理，或將摘要整合至更大的工作流程，例如電子郵件通知或知識庫更新。

**下一步**  
- 探索非同步 API（`SummarizeAsync`）以應對高吞吐量情境。  
- 結合摘要與關鍵字抽取，建立可搜尋的索引。  
- 使用相同模式，從純 `.txt` 檔案或網頁 **使用 AI 摘要文字**。

## 接下來您應該學習什麼？

以下教學涵蓋與本指南緊密相關的主題，並在此基礎上延伸。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [Summarize Word Document in C# with Aspose.Words API – Complete AI‑Powered Guide](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [Word Document - Find And Replace Text](/words/english/net/find-and-replace-text/)
- [Ranges Get Text In Word Document](/words/english/net/programming-with-ranges/ranges-get-text/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}