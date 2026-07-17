---
category: general
date: 2026-07-16
description: 使用 C# 以 AI 摘要文字。學習如何從 Word 產生摘要，並在 C# 中載入 Word 文件，只需幾個步驟。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- summarize text with ai
- generate summary from word
- load word document c#
- ai summarizer c#
- word document processing c#
- text summarization api
language: zh-hant
lastmod: 2026-07-16
og_description: 使用 C# 及 AI 進行文字摘要。按照本指南從 Word 檔案產生摘要，並快速學習如何在 C# 中載入 Word 檔案。
og_image_alt: Screenshot of C# code that loads a Word document and produces an AI‑generated
  summary
og_title: 使用 C# AI 摘要文字 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Summarize text with AI using C#. Learn how to generate summary from
    Word and load Word document C# in just a few steps.
  headline: Summarize Text with AI in C# – Complete Programming Guide
  type: TechArticle
tags:
- C#
- AI
- Word
title: 使用 AI 在 C# 中摘要文字 – 完整程式設計指南
url: /zh-hant/net/ai-powered-document-processing/summarize-text-with-ai-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 AI 在 C# 中摘要文字 – 完整程式指南

有沒有想過在不離開 IDE 的情況下 **使用 AI 摘要文字**？也許你手頭有一堆 *.docx* 報告，需要快速的執行摘要。好消息是，你可以全部在 C# 中完成——載入 Word 文件、呼叫 AI 摘要服務，並列印出整潔的五句概述。

在本教學中，我們會一步步示範真實案例，教你如何 **從 Word 產生摘要**，以及 **load Word document C#** 程式碼，支援 OpenAI 與 Google 兩種模型。完成後，你將擁有一個可直接放入任何 .NET 專案的獨立主控台應用程式。

> **你將學會的內容**  
> • 完整可執行的 C# 程式，能讀取 *.docx* 檔案。  
> • 可重複使用的 `Summarize` 方法，與 AI 服務溝通。  
> • 處理檔案遺失、模型選擇與 token 限制的技巧。

---

## Prerequisites — 開始前需要的條件

| 必要條件 | 為什麼重要 |
|----------|------------|
| .NET 6 或更新版本 | 現代語言功能與 `async` 支援。 |
| NuGet 套件：`Aspose.Words`（或 `DocumentFormat.OpenXml`）、`System.Net.Http.Json` | `Aspose.Words` 提供本文示例中使用的 `Document` 類別；`HttpClient` 處理 API 呼叫。 |
| OpenAI 或 Google Vertex AI 的 API 金鑰 | 摘要服務需要模型端點；你需要在程式碼中填入金鑰。 |
| 一個可供參考的範例 Word 檔案（`report.docx`）放在資料夾中 | 本教學使用 `load word document c#` 來示範檔案 I/O。 |

如果缺少上述任一項，請立即安裝——步驟簡單，不會有困難。

---

## Step 1 – Load the Word Document in C#  

首先要 **load Word document C#**。使用 Aspose.Words，只要建立指向磁碟檔案的 `Document` 實例即可。

```csharp
using Aspose.Words;
using System;
using System.IO;

// Ensure the file exists before we try to open it.
string filePath = Path.Combine(Environment.CurrentDirectory, "report.docx");
if (!File.Exists(filePath))
{
    Console.Error.WriteLine($"❌ File not found: {filePath}");
    return;
}

// Step 1: Load the source document
Document doc = new Document(filePath);
Console.WriteLine("✅ Document loaded successfully.");
```

**Why this matters:**  
* `Document` 物件抽象了 *.docx* 後面的 XML，讓我們之後可以把內容當作純文字處理。  
* 先檢查檔案是否存在，可避免在生產腳本中常見的 `FileNotFoundException`，這也是 **load word document c#** 時的常見陷阱。

---

## Step 2 – Extract Plain Text for Summarization  

AI 模型無法直接理解 Word 的內部標記，需要乾淨的文字。Aspose 提供 `Document.GetText()`，會回傳整個文件的字串。

```csharp
// Extract raw text – this strips out tables, images, and formatting.
string rawText = doc.GetText();
if (string.IsNullOrWhiteSpace(rawText))
{
    Console.Error.WriteLine("⚠️ Document appears empty after extraction.");
    return;
}
Console.WriteLine($"📝 Extracted {rawText.Length:N0} characters of text.");
```

**Pro tip:** 若需要保留標題，可遍歷 `doc.GetChildNodes(NodeType.Paragraph, true)`，僅串接樣式為 “Heading” 的段落。如此摘要才能尊重文件的結構。

---

## Step 3 – Define Summarization Options  

現在進入本教學的核心：**summarize text with AI**。我們會把選項封裝成小型 POCO，讓你在不修改 HTTP 呼叫的前提下，調整模型、最大句數與 temperature。

```csharp
public enum SummarizationModel
{
    OpenAI,
    Google
}

public class SummarizationOptions
{
    public int MaxSentences { get; set; } = 5;
    public SummarizationModel Model { get; set; } = SummarizationModel.OpenAI;
    public double Temperature { get; set; } = 0.7; // Controls creativity
}
```

接著即可建立一個選項實例，告訴 AI 你想要的摘要內容：

```csharp
// Step 2: Define summarization options (e.g., limit to 5 sentences, choose a model)
SummarizationOptions options = new SummarizationOptions
{
    MaxSentences = 5,
    Model = SummarizationModel.OpenAI   // switch to Google if you prefer
};
```

**Why we expose these settings:**  
* 不同專案對簡潔度的需求不同——有的需要兩句 TL;DR，有的則需要五句執行摘要。  
* 只要切換一個 enum 值，即可在 `OpenAI` 與 `Google` 模型間切換，方便進行 A/B 測試。

---

## Step 4 – Implement the `Summarize` Method  

以下提供 **完整、可執行** 的實作，會呼叫 OpenAI 的 `chat/completions` 端點或 Google Vertex AI 的 `text-bison` 模型。程式碼使用 `HttpClient` 搭配 `System.Net.Http.Json`，寫法簡潔。

```csharp
using System.Net.Http;
using System.Net.Http.Json;
using System.Threading.Tasks;

public static class AiSummarizer
{
    private static readonly HttpClient http = new HttpClient();

    public static async Task<string> SummarizeAsync(string text, SummarizationOptions opts)
    {
        // Choose endpoint and payload based on the selected model.
        if (opts.Model == SummarizationModel.OpenAI)
        {
            // OpenAI expects a messages array; we use a system prompt to enforce sentence limit.
            var request = new
            {
                model = "gpt-4o-mini",
                temperature = opts.Temperature,
                messages = new[]
                {
                    new { role = "system", content = $"Summarize the following text in no more than {opts.MaxSentences} sentences." },
                    new { role = "user", content = text }
                },
                max_tokens = 500
            };

            http.DefaultRequestHeaders.Authorization =
                new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", Environment.GetEnvironmentVariable("OPENAI_API_KEY"));

            var response = await http.PostAsJsonAsync("https://api.openai.com/v1/chat/completions", request);
            response.EnsureSuccessStatusCode();

            var json = await response.Content.ReadFromJsonAsync<dynamic>();
            return (string)json.choices[0].message.content;
        }
        else // Google Vertex AI
        {
            var request = new
            {
                instances = new[] { new { content = text } },
                parameters = new
                {
                    temperature = opts.Temperature,
                    maxOutputTokens = 500,
                    topK = 40,
                    topP = 0.95,
                    // Vertex AI doesn’t have a built‑in sentence limit, so we post‑process later.
                }
            };

            http.DefaultRequestHeaders.Authorization =
                new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", Environment.GetEnvironmentVariable("GOOGLE_API_KEY"));

            var response = await http.PostAsJsonAsync(
                "https://us-central1-aiplatform.googleapis.com/v1/projects/YOUR_PROJECT/locations/us-central1/publishers/google/models/text-bison-001:predict",
                request);
            response.EnsureSuccessStatusCode();

            var json = await response.Content.ReadFromJsonAsync<dynamic>();
            string raw = (string)json.predictions[0].content;
            // Simple post‑processing: keep only the first N sentences.
            return string.Join(' ', raw.Split('.').Take(opts.MaxSentences)).Trim() + ".";
        }
    }
}
```

**Explanation of the “why”**  
* **Model‑agnostic design** – 同一個方法同時支援 OpenAI 與 Google，讓程式碼庫保持整潔。  
* **Environment variables for keys** – 硬寫 API 金鑰會有安全風險；使用 `Environment.GetEnvironmentVariable` 符合最佳實踐。  
* **Sentence‑limit enforcement** – OpenAI 可直接在系統提示中設定句數上限；Google 需在回傳後自行截斷，因為其 API 本身不支援句數上限。

---

## Step 5 – Wire Everything Together and Output the Summary  

現在把各個部件組合起來：讀取文件、將文字傳給 `SummarizeAsync`，最後印出結果。

```csharp
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // Load the document (Step 1)
        string filePath = Path.Combine(Environment.CurrentDirectory, "report.docx");
        if (!File.Exists(filePath))
        {
            Console.Error.WriteLine($"❌ Cannot find {filePath}");
            return;
        }
        Document doc = new Document(filePath);

        // Extract raw text (Step 2)
        string rawText = doc.GetText();

        // Define options (Step 3)
        SummarizationOptions options = new SummarizationOptions
        {
            MaxSentences = 5,
            Model = SummarizationModel.OpenAI   // Change to Google if you prefer
        };

        // Generate the summary (Step 4)
        string summary = await AiSummarizer.SummarizeAsync(rawText, options);

        // Step 5: Output the generated summary
        Console.WriteLine("\n=== AI‑Generated Summary ===\n");
        Console.WriteLine(summary);
    }
}
```

### Expected Output

假設 `report.docx` 包含兩頁的商業分析，主控台可能會顯示：

```
=== AI‑Generated Summary ===

The quarterly sales increased by 12% YoY, driven primarily by the new product line. Customer churn fell to 3%, the lowest in five years. Marketing spend rose 8% but delivered a 15% lift in brand awareness. Operational efficiencies saved $1.2M, mainly through supply‑chain automation. The outlook for Q3 remains positive, with projected growth of 10‑15%.
```

若將 `options.Model` 改為 `SummarizationModel.Google`，你會看到類似的精簡段落，只是表述風格不同。

---

## Handling Edge Cases & Common Pitfalls  

| 情境 | 需注意事項 | 快速解決方案 |
|------|------------|--------------|
| **Huge documents (>10 k tokens)** | API 可能會拒絕請求或截斷輸出。 | 將文字依章節（例如依標題）切分成多段，分別摘要後再合併。 |
| **Missing or invalid API key** | 401 Unauthorized 錯誤。 | 確認環境變數 `OPENAI_API_KEY` / `GOOGLE_API_KEY` 已設定，或於本機開發時使用 `appsettings.json`。 |
| **Non‑English Word files** | Summar |  |

---

## What Should You Learn Next?

以下教學與本指南的技巧密切相關，能幫助你進一步掌握 API 功能，並在自己的專案中探索其他實作方式。每篇資源皆提供完整可執行的程式碼範例與逐步說明。

- [Word 文件 - 尋找與取代文字](/words/english/net/find-and-replace-text/)
- [範圍取得文字於 Word 文件](/words/english/net/programming-with-ranges/ranges-get-text/)
- [複製書籤文字於 Word 文件](/words/english/net/programming-with-bookmarks/copy-bookmarked-text/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}