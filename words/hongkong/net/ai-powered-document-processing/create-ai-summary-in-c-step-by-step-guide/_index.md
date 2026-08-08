---
category: general
date: 2026-08-07
description: 使用 C# 建立 AI 摘要，快速利用 OpenAI 為 Word 文件生成摘要。了解如何設定 OpenAI API 金鑰及自動化文件摘要。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create AI summary
- summarize Word document
- set OpenAI API key
- generate summary OpenAI
- automate document summarization
language: zh-hant
lastmod: 2026-08-07
og_description: 使用 C# 建立 AI 摘要，即時為 Word 文件生成摘要。請依照本教學設定 OpenAI API 金鑰、產生 OpenAI 摘要，並自動化文件摘要。
og_image_alt: Console window displaying the generated AI summary of a Word document
og_title: 使用 C# 建立 AI 摘要 – 開發者完整指南
schemas:
- author: GroupDocs
  dateModified: '2026-08-07'
  description: Create AI summary in C# to quickly summarize a Word document using
    OpenAI. Learn how to set OpenAI API key and automate document summarization.
  headline: Create AI summary in C# – step‑by‑step guide
  type: TechArticle
tags:
- AI
- C#
- Document processing
- OpenAI
- Automation
title: 在 C# 中建立 AI 摘要 – 逐步指南
url: /zh-hant/net/ai-powered-document-processing/create-ai-summary-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 建立 AI 摘要 – 步驟指南

如果您需要 **建立 AI 摘要** 針對大型 Word 檔案，本教學將完整示範如何使用 C# 及 GroupDocs AI SDK 來完成。您將學會如何 **摘要 Word 文件** 內容、**設定 OpenAI API 金鑰**，以及 **自動化文件摘要** 以建立可重複的工作流程。

我們將逐步說明每個必要步驟，解釋每個環節的重要性，並提供完整可執行的主控台應用程式。完成後，您將擁有一個可直接嵌入任何 .NET 專案的獨立解決方案。

## 前置條件

* 已安裝 .NET 6.0 SDK 或更新版本  
* 有效的 OpenAI API 金鑰（若偏好亦可使用 Google Gemini 金鑰）  
* 取得 GroupDocs AI for .NET 的 NuGet 套件  

您可以使用以下指令安裝套件：

```bash
dotnet add package GroupDocs.AI.Summarizer
```

> **小技巧：** 請使用 *user‑secret* 或環境變數來儲存 API 金鑰，而非硬編碼。

## 使用 GroupDocs AI SDK 建立 AI 摘要

此解決方案的核心是 `DocumentSummarizer` 類別，它接受 `Document` 物件與 `AiSummarizerOptions` 實例。這些選項告訴 SDK 使用哪個提供者以及從何處取得認證資訊。

```csharp
using System;
using GroupDocs.AI.Summarizer;
using GroupDocs.AI.Summarizer.Options;
using GroupDocs.AI.Summarizer.Providers;

class Program
{
    static void Main()
    {
        // Step 1: Load the source Word document
        Document doc = new Document("YOUR_DIRECTORY/LongReport.docx");

        // Step 2: Configure the summarizer (choose provider and supply API key)
        AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
        {
            Provider = AiProvider.OpenAi,          // or AiProvider.Google
            ApiKey   = "YOUR_OPENAI_API_KEY"
        };

        // Step 3: Generate the summary using the configured options
        string reportSummary = DocumentSummarizer.Summarize(doc, summarizerOptions);

        // Step 4: Display the resulting summary
        Console.WriteLine("Summary:\n" + reportSummary);
    }
}
```

### 為什麼這樣可行

* **載入文件** 會將 `.docx` 檔案轉換為 AI 引擎可讀取的格式。  
* **AiSummarizerOptions** 告訴 SDK 呼叫哪個 LLM 提供者，並提供驗證令牌——這裡即是 **設定 OpenAI API 金鑰** 的位置。  
* **DocumentSummarizer.Summarize** 將文件文字傳送至所選提供者，並回傳簡潔的摘要。  
* **Console.WriteLine** 輸出結果，您之後可將其導入檔案、電子郵件或資料庫。

## 為摘要設定 OpenAI API 金鑰

硬編碼金鑰可用於快速示範，但正式環境的程式碼應避免將機密寫入原始碼管理。SDK 會讀取 `ApiKey` 屬性，因此您可以從環境變數取得金鑰值：

```csharp
AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
{
    Provider = AiProvider.OpenAi,
    ApiKey   = Environment.GetEnvironmentVariable("OPENAI_API_KEY")
};
```

將變數加入系統中：

```bash
# Windows PowerShell
$Env:OPENAI_API_KEY = "sk-xxxxxxxxxxxxxxxxxxxx"

# macOS / Linux
export OPENAI_API_KEY="sk-xxxxxxxxxxxxxxxxxxxx"
```

> **為何重要：** 安全儲存金鑰可防止意外外洩，並符合大多數企業的安全政策。

## 使用 Generate summary OpenAI 摘要 Word 文件

`DocumentSummarizer` 內部會呼叫 **Generate summary OpenAI** 端點。若您想微調請求，可透過 `AiSummarizerOptions` 傳入額外參數：

```csharp
AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
{
    Provider = AiProvider.OpenAi,
    ApiKey   = Environment.GetEnvironmentVariable("OPENAI_API_KEY"),
    Temperature = 0.3,          // Lower temperature for more deterministic output
    MaxTokens   = 250           // Limit the length of the summary
};
```

這些設定可讓您控制回傳文字的詳盡程度與創意度，對於在大量檔案上 **自動化文件摘要** 時相當有用。

## 在主控台應用程式中自動化文件摘要

若要在無需人工干預的情況下處理多個檔案，可將邏輯包在迴圈中，並從資料夾讀取檔案路徑：

```csharp
string inputFolder = @"YOUR_DIRECTORY";
foreach (var filePath in Directory.GetFiles(inputFolder, "*.docx"))
{
    Document doc = new Document(filePath);
    string summary = DocumentSummarizer.Summarize(doc, summarizerOptions);

    string outputPath = Path.ChangeExtension(filePath, ".summary.txt");
    File.WriteAllText(outputPath, summary);
    Console.WriteLine($"Summarized {Path.GetFileName(filePath)} → {Path.GetFileName(outputPath)}");
}
```

### 此功能的增益

* **批次處理** – 您可將任意數量的 Word 檔案放入資料夾，系統會為每個檔案產生 `.summary.txt`。  
* **錯誤處理** – 您可在迴圈外加上 `try/catch`，跳過損毀檔案並記錄問題。  
* **可擴充性** – 由於 SDK 會對每份文件發送 HTTP 請求，若您的 OpenAI 配額允許，可使用 `Parallel.ForEach` 進行平行處理。

## 預期輸出

執行程式並使用範例 `LongReport.docx` 時，主控台會輸出類似以下內容：

```
Summary:
The report outlines the quarterly performance of the sales department, highlighting a 12% increase in revenue driven by new product launches. Key challenges include supply‑chain constraints and rising operational costs. Recommendations focus on expanding the digital sales channel and optimizing inventory management.
```

產生的 `.summary.txt` 檔案包含相同的文字，可直接供後續使用（例如電子郵件通知、知識庫匯入或 UI 顯示）。

## 常見陷阱與避免方法

| 症狀 | 原因 | 解決方案 |
|---------|-------|-----|
| *摘要為空* | 文件僅包含無法提取文字的圖片或表格。 | 在摘要前使用 `doc.ExtractText()`，或將圖片轉換為支援 OCR 的文字。 |
| *驗證錯誤* | API 金鑰錯誤或缺失。 | 檢查 `OPENAI_API_KEY` 環境變數，並確保金鑰具備所需權限。 |
| *速率限制回應* | 超過 OpenAI 請求配額。 | 在請求間加入延遲 (`Task.Delay(1000)`) 或向 OpenAI 申請更高配額。 |
| *語言不符* | 提供者預設為英文，但來源文件為其他語言。 | 設定 `summarizerOptions.Language = "es"`（或相應的 ISO 代碼）以強制目標語言。 |

## 完整原始碼供複製貼上

```csharp
using System;
using System.IO;
using GroupDocs.AI.Summarizer;
using GroupDocs.AI.Summarizer.Options;
using GroupDocs.AI.Summarizer.Providers;

class Program
{
    static void Main()
    {
        // Configure summarizer options (set OpenAI API key)
        AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
        {
            Provider = AiProvider.OpenAi,
            ApiKey   = Environment.GetEnvironmentVariable("OPENAI_API_KEY"),
            Temperature = 0.3,
            MaxTokens   = 250
        };

        // Folder containing Word documents to summarize
        string inputFolder = @"YOUR_DIRECTORY";

        foreach (var filePath in Directory.GetFiles(inputFolder, "*.docx"))
        {
            try
            {
                Document doc = new Document(filePath);
                string summary = DocumentSummarizer.Summarize(doc, summarizerOptions);

                string outputPath = Path.ChangeExtension(filePath, ".summary.txt");
                File.WriteAllText(outputPath, summary);

                Console.WriteLine($"Summarized {Path.GetFileName(filePath)} → {Path.GetFileName(outputPath)}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Failed to process {Path.GetFileName(filePath)}: {ex.Message}");
            }
        }
    }
}
```

> **注意：** 請將 `YOUR_DIRECTORY` 替換為存放 `.docx` 檔案之資料夾的絕對路徑。

![顯示 Word 文件產生的 AI 摘要之主控台輸出](console-output.png)

## 結論

現在您已了解如何使用 GroupDocs AI SDK 在 C# 中 **建立 Word 檔案的 AI 摘要**、如何 **設定 OpenAI API 金鑰**，以及如何 **自動化文件摘要** 以處理任意數量的檔案。此方法同時支援 OpenAI 與 Google 提供者，讓您可調整產生參數，且能順利整合至現有的 .NET 解決方案。

**下一步**

* 探索 **summarize Word document** 功能，使用自訂提示詞調整語氣或長度。  
* 結合 **Azure Functions** 或 **AWS Lambda**，打造無伺服器的摘要服務。  
* 將主控台輸出改為使用 ASP.NET Core 的 REST API，以提供即時摘要服務。

祝開發順利，並體驗 AI 驅動的摘要為您的文件工作流程帶來的效率提升！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並在此基礎上延伸技術。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [建立新 Word 文件](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [使用 Aspose.Words for .NET 建立 Word 文件](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [在 .NET 中建立帶目錄的 Word 文件](/words/english/net/add-content-using-document-builder/insert-table-contents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}