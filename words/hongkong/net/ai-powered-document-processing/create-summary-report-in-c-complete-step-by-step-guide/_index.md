---
category: general
date: 2026-06-24
description: 使用 OpenAI 與 Google AI 在 C# 中建立摘要報告。學習如何摘要 Word 檔案、在 C# 載入 Word 檔，並快速顯示
  AI 摘要。
draft: false
keywords:
- create summary report
- how to summarize word
- summarize docx google
- display ai summary
- load word file c#
language: zh-hant
og_description: 在 C# 中載入 Word 檔案，使用 OpenAI 或 Google AI 產生摘要報告。請依照本指南在您的控制台顯示 AI 摘要。
og_title: 在 C# 中建立摘要報告 – 完整程式設計教學
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create summary report in C# using OpenAI and Google AI. Learn how to
    summarize Word files, load word file c#, and display AI summary quickly.
  headline: Create summary report in C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create summary report in C# using OpenAI and Google AI. Learn how to
    summarize Word files, load word file c#, and display AI summary quickly.
  name: Create summary report in C# – Complete Step‑by‑Step Guide
  steps:
  - name: Loads a `.docx` file from disk.
    text: Loads a `.docx` file from disk.
  - name: Generates two separate summaries – one with OpenAI, the other with Google
      AI.
    text: Generates two separate summaries – one with OpenAI, the other with Google
      AI.
  - name: Prints both summaries so you can compare the results.
    text: Prints both summaries so you can compare the results.
  type: HowTo
tags:
- C#
- AI‑summarization
- Word‑automation
title: 使用 C# 建立摘要報表 – 完整逐步指南
url: /zh-hant/net/ai-powered-document-processing/create-summary-report-in-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中建立摘要報告 – 完整逐步指南

有沒有想過 **如何自動摘要 Word** 文件，而不必手動複製貼上段落？你並非唯一有此需求的人。無論你是需要為冗長的報告快速簡報，或是想為儀表板提供精簡的洞見，程式化 **create summary report** 的能力都能節省數小時的人工工作。

在本教學中，我們將逐步說明如何 **load word file c#**、呼叫 OpenAI 與 Google AI 兩種模型，最後在主控台 **display AI summary**。不會有模糊的說明——只提供可直接執行的範例、每個部份為何重要的說明，以及處理常見問題的技巧。

## 我們將建立的功能

1. 從磁碟載入 `.docx` 檔案。  
2. 產生兩個獨立的摘要——一個使用 OpenAI，另一個使用 Google AI。  
3. 列印兩個摘要，以便比較結果。  

你還會看到如何微調摘要模型、在來源檔案遺失時捕捉錯誤，以及擴充程式碼以進行自訂後處理。

> **專業提示：** 同樣的模式同樣適用於其他文件類型（PDF、HTML），只要你選擇的函式庫支援 `Summarize` 方法即可。

---

## 步驟 1 – 載入 Word 檔案 C#（拼圖的第一塊）

在任何 AI 發揮魔法之前，必須先將文件載入記憶體。我們將使用 **Aspose.Words for .NET**，這是一套能理解 `.docx` 結構並提供便利 `Document` 類別的熱門函式庫。

```csharp
using System;
using Aspose.Words;               // NuGet: Aspose.Words
using Aspose.Words.Summarization; // Hypothetical namespace for summarization

// Path to the source Word file – adjust to your environment
const string sourcePath = @"C:\Reports\LongReport.docx";

Document document;
try
{
    // This line actually **load word file c#** style – it throws if the file is missing
    document = new Document(sourcePath);
    Console.WriteLine($"✅ Loaded document: {sourcePath}");
}
catch (Exception ex)
{
    Console.WriteLine($"❌ Failed to load document: {ex.Message}");
    return; // Exit early – no point continuing without a source
}
```

**為什麼這很重要：**  
- `Aspose.Words` 會處理複雜的 Word 功能（表格、註腳），讓摘要器看到 *真實* 內容。  
- 將載入動作包在 `try/catch` 中，可防止因檔案路徑錯誤而導致程式崩潰——這是自動化報告時常見的邊緣情況。

---

## 步驟 2 – 使用 OpenAI 摘要 Word

現在文件已在記憶體中，我們可以請 LLM 將其壓縮。`Summarize` 擴充方法接受 `ISummarizationModel` 的實作。以下是一個最小的 OpenAI 包裝器：

```csharp
// OpenAI model wrapper – replace "YOUR_API_KEY" with a real key
class OpenAiModel : ISummarizationModel
{
    private readonly string _apiKey = "YOUR_API_KEY";

    public string Summarize(string text)
    {
        // In a real app you'd call the OpenAI ChatCompletion endpoint.
        // For brevity, this is a stub showing intent.
        return $"[OpenAI summary of {text.Length} characters]";
    }
}

// Generate the summary
var openAiModel = new OpenAiModel();
var openAiSummary = document.Summarize(openAiModel);
Console.WriteLine("\n--- OpenAI Summary ---");
Console.WriteLine(openAiSummary.Text);
```

**為什麼選擇 OpenAI？**  
OpenAI 的模型擅長在保留關鍵術語的同時抽取高層次主題。若需要中性語氣或想控制 temperature，可在 `OpenAiModel` 中公開這些設定。

---

## 步驟 3 – 使用 Google AI 摘要 docx （Google 模型）

Google 的 Gemini（或 PaLM）常會產生更精簡的項目式輸出。只要實例化實作相同介面的不同類別，即可輕鬆切換模型。

```csharp
// Google AI model wrapper – replace with your actual credentials
class GoogleAiModel : ISummarizationModel
{
    private readonly string _apiKey = "YOUR_GOOGLE_API_KEY";

    public string Summarize(string text)
    {
        // Stub for illustration – call the Google Generative AI endpoint here.
        return $"[Google summary of {text.Length} characters]";
    }
}

// Generate the Google summary
var googleModel = new GoogleAiModel();
var googleSummary = document.Summarize(googleModel);
Console.WriteLine("\n--- Google AI Summary ---");
Console.WriteLine(googleSummary.Text);
```

**為什麼這很重要：**  
同時取得 **summarize docx google** 與 OpenAI 的結果，讓你可以比較語氣、長度與事實忠實度。在正式環境中，甚至可以將兩個輸出混合，以產生更豐富的最終報告。

---

## 步驟 4 – 顯示 AI 摘要 – 讓結果可見

我們已經把摘要印出，但讓我們將顯示邏輯封裝成可重用的方法。此步驟強調 **display ai summary** 概念，並讓主流程保持整潔。

```csharp
static void ShowSummary(string title, string content)
{
    Console.WriteLine($"\n--- {title} ---");
    Console.WriteLine(content);
    Console.WriteLine(new string('-', 40));
}

// Use the helper for both summaries
ShowSummary("OpenAI Generated Summary", openAiSummary.Text);
ShowSummary("Google AI Generated Summary", googleSummary.Text);
```

**額外提示：** 若日後想把摘要寫回 Word 檔或透過電子郵件發送，只需將 `Console.WriteLine` 替換為檔案 I/O 或 SMTP 程式碼即可。

---

## 步驟 5 – 整合所有程式 – 完整可執行範例

以下是完整的主控台應用程式。將它複製貼上到新的 `.csproj`（目標 .NET 6 或更新版本），還原 NuGet 套件後執行。程式會使用兩個 AI 服務 **create summary report** 給予的 Word 文件。

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Summarization;

namespace SummaryReportDemo
{
    // Interface shared by all summarization providers
    public interface ISummarizationModel
    {
        string Summarize(string text);
    }

    // ---------- OpenAI implementation ----------
    class OpenAiModel : ISummarizationModel
    {
        private readonly string _apiKey = "YOUR_OPENAI_API_KEY";

        public string Summarize(string text)
        {
            // Real implementation would POST to https://api.openai.com/v1/chat/completions
            // Here we simulate a response for demonstration.
            return $"[OpenAI summary of {text.Length} characters]";
        }
    }

    // ---------- Google AI implementation ----------
    class GoogleAiModel : ISummarizationModel
    {
        private readonly string _apiKey = "YOUR_GOOGLE_API_KEY";

        public string Summarize(string text)
        {
            // Real implementation would POST to Google's Generative AI endpoint.
            return $"[Google summary of {text.Length} characters]";
        }
    }

    // ---------- Helper to display summaries ----------
    static class ConsoleHelper
    {
        public static void ShowSummary(string title, string content)
        {
            Console.WriteLine($"\n--- {title} ---");
            Console.WriteLine(content);
            Console.WriteLine(new string('-', 40));
        }
    }

    class Program
    {
        static void Main()
        {
            const string sourcePath = @"C:\Reports\LongReport.docx";

            // Load the Word document – **load word file c#** step
            Document document;
            try
            {
                document = new Document(sourcePath);
                Console.WriteLine($"✅ Loaded: {sourcePath}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"❌ Could not load file: {ex.Message}");
                return;
            }

            // Generate OpenAI summary
            var openAi = new OpenAiModel();
            var openAiSummary = document.Summarize(openAi);

            // Generate Google summary
            var googleAi = new GoogleAiModel();
            var googleSummary = document.Summarize(googleAi);

            // **display ai summary** for both providers
            ConsoleHelper.ShowSummary("OpenAI Generated Summary", openAiSummary.Text);
            ConsoleHelper.ShowSummary("Google AI Generated Summary", googleSummary.Text);
        }
    }

    // Extension method that bridges Aspose.Words with our model interface
    public static class SummarizationExtensions
    {
        public static SummaryResult Summarize(this Document doc, ISummarizationModel model)
        {
            // Extract raw text from the Word document
            string rawText = doc.GetText();

            // Ask the model to summarize it
            string summary = model.Summarize(rawText);

            // Wrap into a simple result object
            return new SummaryResult { Text = summary };
        }
    }

    // Lightweight container for summary text
    public class SummaryResult
    {
        public string Text { get; set; }
    }
}
```

**預期輸出（模擬）**

```
✅ Loaded: C:\Reports\LongReport.docx

--- OpenAI Generated Summary ---
[OpenAI summary of 15234 characters]
----------------------------------------

--- Google AI Generated Summary ---
[Google summary of 15234 characters]
----------------------------------------
```

將佔位的 `Summarize` 方法換成實際呼叫相應 API 的 HTTP 程式碼，即可擁有可投入生產的 **create summary report** 工具。

---

## 常見問題與邊緣情況

| 問題 | 答案 |
|----------|--------|
| *如果文件包含表格或圖片呢？* | `Aspose.Words` 會從表格中提取純文字，但會忽略圖片。若需要圖片說明，請在摘要前先預處理文件，為圖片加入 alt 文字。 |
| *我可以控制摘要長度嗎？* | 大多數 LLM API 接受 `max_tokens` 或 `temperature` 參數。可擴充 `OpenAiModel`/`GoogleAiModel` 以傳遞這些值。 |
| *當 API 金鑰無效時會發生什麼事？* | `Summarize` 呼叫會拋出例外。請將呼叫包在 `try/catch` 中，並在失敗時退回簡單的啟發式方法（例如，取前 N 句）。 |
| *是否有上限* |  |

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並在此基礎上進一步擴展。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [從 Word 建立 Markdown – 完整 C# 教學](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)
- [建立可存取的 PDF 並將 Word 轉換為 Markdown – 完整 C# 教學](/words/english/net/programming-with-markdownsaveoptions/create-accessible-pdf-and-convert-word-to-markdown-full-c-gu/)
- [使用 Aspose.Words 建立含表格的 Word 文件](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}