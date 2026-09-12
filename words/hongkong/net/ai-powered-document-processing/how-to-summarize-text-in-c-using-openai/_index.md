---
category: general
date: 2026-09-11
description: 學習如何在 C# 中摘要文字，透過讀取 API 金鑰、呼叫 OpenAI，並產生 Word 文件的簡潔摘要。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: zh-hant
lastmod: 2026-09-11
og_description: 如何在 C# 中摘要文字？本教學將示範如何讀取 API 金鑰、呼叫 OpenAI，並為 Word 文件建立摘要。
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: 使用 OpenAI 在 C# 中進行文字摘要 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  headline: How to summarize text in C# using OpenAI
  type: TechArticle
- description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  name: How to summarize text in C# using OpenAI
  steps:
  - name: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
    text: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
  - name: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
    text: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
  - name: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
    text: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
  - name: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
    text: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
  type: HowTo
tags:
- C#
- OpenAI
- Document processing
- AI summarization
title: 如何在 C# 中使用 OpenAI 摘要文字
url: /zh-hant/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用 OpenAI 摘要文本

如果你需要在 .docx 檔案中 **how to summarize text**，本指南會提供一個完整、可直接執行的解決方案。你將學習如何從環境變數讀取 API 金鑰、如何在 C# 中呼叫 OpenAI（或 Google），以及如何為 Word 文件產生簡潔的摘要。

為 Word 文件生成摘要是報告產出、電子郵件摘要或知識庫抽取的常見需求。完成本教學後，你將擁有一個命令列程式，能夠印出任意 `.docx` 檔案的五句摘要。

## 前置條件

- .NET 6.0 SDK 或更新版本（從 [dotnet.microsoft.com](https://dotnet.microsoft.com/download) 下載）
- 一個有效的 OpenAI API 金鑰，儲存在名為 `OPENAI_API_KEY` 的環境變數中（你會看到 **read api key** 的實作）
- 用於讀取 `.docx` 檔案的 `DocumentFormat.OpenXml` NuGet 套件
- `OpenAI` NuGet 套件（如果你偏好 Google 提供者，則使用 `Google.AI`）

## 步驟 1：設定專案並安裝相依套件

建立一個新的 console 專案，並加入所需的套件：

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **Pro tip:** 若日後加入更多相依套件，請將相關套件放在同一個 `<ItemGroup>` 中，以保持 `csproj` 整潔。

## 步驟 2：安全地讀取 API 金鑰

硬編碼機密資訊是不安全的。本教學示範了從環境變數 **read api key** 的正確做法。

```csharp
using System;

/// <summary>
/// Retrieves the OpenAI API key from the environment.
/// Throws an exception if the variable is missing.
/// </summary>
static string GetOpenAIApiKey()
{
    var key = Environment.GetEnvironmentVariable("OPENAI_API_KEY");
    if (string.IsNullOrWhiteSpace(key))
    {
        throw new InvalidOperationException(
            "OPENAI_API_KEY environment variable not set. " +
            "Set it before running the program.");
    }
    return key;
}
```

## 步驟 3：載入要摘要的 Word 文件

以下程式碼示範了如何透過從 OpenXML 結構中擷取純文字，**how to summarize word document** 內容。

```csharp
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

/// <summary>
/// Extracts raw text from a .docx file.
/// </summary>
static string ExtractTextFromDocx(string path)
{
    using var wordDoc = WordprocessingDocument.Open(path, false);
    var body = wordDoc.MainDocumentPart.Document.Body;
    return body.InnerText;
}
```

## 步驟 4：建立可重複使用的摘要類別

此類別封裝了 **how to call openai**（或 Google）的呼叫方式，並實作 **how to create summary** 的邏輯。它同時允許你僅透過一個 enum 值切換提供者。

```csharp
using System.Threading.Tasks;
using OpenAI;
using OpenAI.Chat;

/// <summary>
/// Supported AI providers for summarization.
/// </summary>
enum SummarizerProvider { OpenAI, Google }

/// <summary>
/// Provides a method to summarize a document using the selected provider.
/// </summary>
static class DocumentSummarizer
{
    public static async Task<string> SummarizeAsync(
        string text,
        SummarizerProvider provider,
        int maxSentences = 5)
    {
        return provider switch
        {
            SummarizerProvider.OpenAI => await SummarizeWithOpenAIAsync(text, maxSentences),
            SummarizerProvider.Google => await SummarizeWithGoogleAsync(text, maxSentences),
            _ => throw new NotSupportedException($"Provider {provider} is not supported.")
        };
    }

    // ---------- OpenAI implementation ----------
    private static async Task<string> SummarizeWithOpenAIAsync(string text, int maxSentences)
    {
        var apiKey = GetOpenAIApiKey(); // re‑use the method from Step 2
        var client = new OpenAIClient(new OpenAIAuthentication(apiKey));

        var prompt = $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}";
        var chatRequest = new ChatRequest(new[] { new ChatMessage(ChatMessageRole.System, prompt) });

        var response = await client.ChatEndpoint.GetCompletionAsync(chatRequest);
        return response.FirstChoice.Message.Content.Trim();
    }

    // ---------- Google implementation (optional) ----------
    private static async Task<string> SummarizeWithGoogleAsync(string text, int maxSentences)
    {
        // Placeholder for Google AI call.
        // Replace with actual Google client code if you have the package.
        await Task.Yield();
        return "Google summarization not implemented in this demo.";
    }
}
```

### 為何此結構重要

- **關注點分離（Separation of concerns）：** 載入文件、讀取 API 金鑰、呼叫 AI 服務皆被分離到各自的方法中，讓程式碼更易於測試與擴充。
- **提供者彈性（Provider flexibility）：** 透過 enum，你可以在 OpenAI 與 Google 之間切換，而不需修改呼叫程式碼，這直接回應了 **how to call openai** 與 **how to create summary** 的可重複使用方式。
- **錯誤處理（Error handling）：** 若缺少 API 金鑰會拋出明確的例外，避免靜默失敗。

## 步驟 5：在 `Program.cs` 中整合所有程式碼

```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        if (args.Length != 1)
        {
            Console.WriteLine("Usage: SummarizerDemo <path-to-docx>");
            return;
        }

        string docPath = args[0];

        // 1️⃣ Load the source document
        string rawText = ExtractTextFromDocx(docPath);

        // 2️⃣ Summarize the document using OpenAI (you can switch to Google)
        string summary = await DocumentSummarizer.SummarizeAsync(
            rawText,
            SummarizerProvider.OpenAI, // change to SummarizerProvider.Google if needed
            maxSentences: 5);

        // 3️⃣ Output the generated summary
        Console.WriteLine("Summary:");
        Console.WriteLine(summary);
    }

    // Include the helper methods from Steps 2‑4 here
    // (GetOpenAIApiKey, ExtractTextFromDocx, DocumentSummarizer, etc.)
}
```

### 預期輸出

使用範例文件執行程式時：

```bash
dotnet run -- "sample/input.docx"
```

可能會產生以下結果：

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## 步驟 6：常見變化與邊緣情況

| 情況 | 建議調整 |
|-----------|------------------------|
| **大型文件**（> 10 KB） | 將文字切分為多個區塊，分別摘要後再合併結果。 |
| **非英語內容** | 在提示詞中加入語言提示，例如 “Summarize the following French text …”。 |
| **Google 提供者** | 將 `SummarizeWithOpenAIAsync` 呼叫換成相應的 Google API 客戶端；保持相同的 enum 介面。 |
| **自訂摘要長度** | 呼叫 `SummarizeAsync` 時調整 `maxSentences` 參數。 |
| **缺少 API 金鑰** | `GetOpenAIApiKey` 方法已會拋出明確例外；若想顯示更友善訊息，可在 `Main` 中捕捉。 |

## 生產環境使用的專業技巧

1. **快取 API 金鑰** – 每次從環境變數讀取開銷極小，但若在同一個程序中多次呼叫摘要器，可將其存於 static readonly 欄位。  
2. **限制請求速率** – OpenAI 會施加請求上限；若遭遇 `429 Too Many Requests`，請實作指數退避機制。  
3. **清理輸入** – 在將文字送至外部 AI 服務前，移除個人可識別資訊。  
4. **為抽取邏輯撰寫單元測試** – 使用 mock 的 `WordprocessingDocument`，驗證 `ExtractTextFromDocx` 在不同文件結構下的運作。

## 結論

現在你已掌握在 C# 中 **how to summarize text** 的方法，透過安全讀取 API 金鑰、呼叫 OpenAI，並為 Word 文件產生簡潔摘要。相同的模式也能讓你 **how to call openai** 其他提供者、為不同內容類型實作 **how to create summary** 邏輯，並安全地從環境變數 **read api key**。可嘗試更長的文件、不同的提供者或自訂提示詞，以符合你的特定領域需求。

---

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並在此基礎上延伸。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [在 C# 中使用 Aspose.Words API 摘要 Word 文件 – 完整 AI 驅動指南](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [如何從 Word 建立 PDF – 完整 C# 指南](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Word 文件 - 如何移除內容](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}