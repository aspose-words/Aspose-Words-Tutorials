---
category: general
date: 2026-11-15
description: 學習如何在 C# 中使用 Google 進行文字翻譯。本教學示範 Google 翻譯範例，涵蓋多語言處理與最佳實踐。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: zh-hant
lastmod: 2026-11-15
og_description: 如何在 C# 中使用完整的 Google 翻譯範例透過 Google 進行文字翻譯。跟隨本教學安全地翻譯多種語言。
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: 如何使用 Google 翻譯 API 在 C# 中翻譯文字 – 快速教學
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  headline: How to translate text with Google Translate API in C# – step‑by‑step guide
  type: TechArticle
- description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  name: How to translate text with Google Translate API in C# – step‑by‑step guide
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 SDK or later (the code compiles with .NET Core and .NET Framework).
      * A Google Cloud account with the **Cloud Translation API** enabled. * Basic
      familiarity with C# and console applications.'
  - name: Handling language detection
    text: 'If you need to know the source language, the response object contains `DetectedSourceLanguage`:'
  - name: Translating large documents
    text: The API supports up to 30 KB per request. For larger texts, split the content
      into chunks, translate each chunk, and then concatenate the results. Keep sentence
      boundaries intact to avoid awkward phrasing.
  - name: Rate‑limiting and quotas
    text: Google enforces per‑minute request limits. Implement a retry policy with
      exponential back‑off to respect quota limits and avoid `429 Too Many Requests`
      errors.
  type: HowTo
- questions:
  - answer: Yes. Use the `Format` parameter (`"text"` or `"html"`) when calling `TranslateText`.
      The SDK exposes this via the `TranslateText` overload that accepts a `TranslateTextRequest`.
    question: Can I translate a whole HTML page?
  - answer: The API returns an error. Validate language codes against the list returned
      by `client.ListSupportedLanguages()` before making a request.
    question: What if a language isn’t supported?
  - answer: 'Google bills per character translated. Estimate costs using the pricing
      page and consider caching frequent translations. --- ## Conclusion You now know
      **how to translate text** in C# using the official Google Translate API. The
      tutorial covered a **Google translate example**, demonstrated **transla'
    question: Does the API charge per character?
  type: FAQPage
tags:
- Google Cloud
- C#
- Translation API
title: 如何在 C# 中使用 Google 翻譯 API 進行文字翻譯 – 一步一步指南
url: /zh-hant/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Google Translate API 在 C# 中翻譯文字 – 步驟指南

如果您需要在 .NET 應用程式中 **how to translate text**，Google Cloud Translation API 提供可靠且語言無關的解決方案。在本教學中，您將看到一個 **Google Translate example**，它會翻譯簡單字串，擴充為 **translate multiple languages**，並遵循 API 金鑰與錯誤處理的最佳實踐。

您將獲得一個可直接執行的 C# 主控台程式，清楚了解 **translate text with Google**，並有信心將程式碼套用到更大的專案中。

## 本教學涵蓋內容

* 設定 Google Cloud 專案並取得 API 金鑰。  
* 安裝 `Google.Cloud.Translation.V2` NuGet 套件。  
* 編寫乾淨且可重用的程式碼，使用官方 SDK **how to translate text**。  
* 將解決方案擴充為一次呼叫即可 **translate multiple languages**。  
* 常見陷阱與生產等級實作的技巧。

### 前置條件

* .NET 6.0 SDK 或更新版本（程式碼可在 .NET Core 與 .NET Framework 上編譯）。  
* 具備已啟用 **Cloud Translation API** 的 Google Cloud 帳號。  
* 基本了解 C# 與主控台應用程式。  

---

## 步驟 1：安裝 Google Cloud Translation 客戶端函式庫

官方客戶端函式庫會抽象化 HTTP 呼叫，並為您處理驗證。

```bash
dotnet add package Google.Cloud.Translation.V2
```

執行此指令會將 `Google.Cloud.Translation.V2` 套件加入您的專案，讓您取得在本指南中廣泛使用的 `TranslationClient` 類別。

> **此步驟的重要性** – 使用 SDK 可避免手動建構請求、減少錯誤，並確保與 Google 最新的 API 版本保持一致。

## 步驟 2：建立可重用的翻譯輔助工具

將翻譯邏輯封裝於靜態類別中，可使程式碼可重用，且將 API 金鑰的處理隔離。

```csharp
using Google.Cloud.Translation.V2;
using System;

namespace GoogleTranslateDemo
{
    /// <summary>
    /// Provides simple methods to translate text using the Google Cloud Translation API.
    /// </summary>
    public static class Translator
    {
        /// <summary>
        /// Translates a single string into the specified target language.
        /// </summary>
        /// <param name="sourceText">The text you want to translate.</param>
        /// <param name="targetLanguage">ISO‑639‑1 language code (e.g., "fr" for French).</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>The translated text.</returns>
        public static string Translate(string sourceText, string targetLanguage, string apiKey)
        {
            // Initialise the client with the provided API key.
            var client = TranslationClient.CreateFromApiKey(apiKey);

            // Perform the translation. The API automatically detects the source language.
            var response = client.TranslateText(sourceText, targetLanguage);
            return response.TranslatedText;
        }

        /// <summary>
        /// Translates a collection of texts into several languages at once.
        /// </summary>
        /// <param name="sourceTexts">Array of strings to translate.</param>
        /// <param name="targetLanguages">Array of ISO‑639‑1 codes (e.g., "es", "de").</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>A dictionary keyed by language code containing the translated results.</returns>
        public static Dictionary<string, string[]> TranslateMultiple(string[] sourceTexts,
                                                                    string[] targetLanguages,
                                                                    string apiKey)
        {
            var client = TranslationClient.CreateFromApiKey(apiKey);
            var result = new Dictionary<string, string[]>();

            foreach (var lang in targetLanguages)
            {
                var translations = client.TranslateTexts(sourceTexts, lang);
                result[lang] = translations.Select(t => t.TranslatedText).ToArray();
            }

            return result;
        }
    }
}
```

> **為何回傳字典** – 當您需要 **translate multiple languages** 時，依語言代碼整理結果可讓後續處理更為直接。

## 步驟 3：建立使用輔助工具的主控台應用程式

以下是一個完整的 `Program.cs`，示範單一文字翻譯與批次翻譯。

```csharp
using System;
using GoogleTranslateDemo; // Namespace from the helper class

class Program
{
    static void Main()
    {
        // ---- Single translation (Google Translate example) ----
        string sourceText = "Hello, world!";
        string targetLanguage = "fr"; // French
        string apiKey = "YOUR_GOOGLE_API_KEY"; // Replace with your actual key

        try
        {
            string translated = Translator.Translate(sourceText, targetLanguage, apiKey);
            Console.WriteLine($"[Single] English → French: {translated}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Translation failed: {ex.Message}");
        }

        // ---- Translate multiple languages (translate multiple languages) ----
        string[] texts = { "Good morning", "How are you?" };
        string[] languages = { "es", "de", "ja" }; // Spanish, German, Japanese

        try
        {
            var batchResult = Translator.TranslateMultiple(texts, languages, apiKey);
            foreach (var kvp in batchResult)
            {
                Console.WriteLine($"\n[Batch] Language: {kvp.Key}");
                for (int i = 0; i < texts.Length; i++)
                {
                    Console.WriteLine($"  {texts[i]} → {kvp.Value[i]}");
                }
            }
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Batch translation failed: {ex.Message}");
        }
    }
}
```

**預期的主控台輸出**

```
[Single] English → French: Bonjour le monde!

[Batch] Language: es
  Good morning → Buenos días
  How are you? → ¿Cómo estás?

[Batch] Language: de
  Good morning → Guten Morgen
  How are you? → Wie geht es Ihnen?

[Batch] Language: ja
  Good morning → おはようございます
  How are you? → お元気ですか？
```

> **為何使用 try/catch 區塊？** – 網路錯誤、配額限制或無效的 API 金鑰都會拋出例外。妥善處理可提升使用者體驗，並保持應用程式穩定。

## 步驟 4：保護您的 API 金鑰

如上所示將 API 金鑰硬編碼在程式中，僅適用於快速示範，正式環境不可採用。請遵循以下做法：

* 將金鑰存放於環境變數 (`GOOGLE_API_KEY`) 並於執行時讀取：  
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* 在 Google Cloud（App Engine、Cloud Run 等）上執行時，使用 **Google Application Default Credentials** 取代 API 金鑰。  
* 在 Google Cloud 控制台將金鑰限制於 Translation API，並將使用範圍限制於特定 IP 位址或 Referrer。

## 步驟 5：將解決方案延伸至實務情境

### 處理語言偵測

若需得知來源語言，回應物件會包含 `DetectedSourceLanguage`：

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### 翻譯大型文件

API 每次請求支援最高 30 KB。若文字較大，請將內容切分為多個區塊，分別翻譯後再串接結果。保持句子邊界完整，以免產生不自然的語句。

### 限速與配額

Google 會對每分鐘的請求數量設有限制。請實作具指數退避的重試策略，以遵守配額並避免 `429 Too Many Requests` 錯誤。

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## 常見問題與邊緣情況

**Q: 我可以翻譯整個 HTML 頁面嗎？**  
A: 可以。呼叫 `TranslateText` 時使用 `Format` 參數（`"text"` 或 `"html"`）。SDK 透過接受 `TranslateTextRequest` 的 `TranslateText` 重載提供此功能。

**Q: 若語言不受支援該怎麼辦？**  
A: API 會回傳錯誤。請在發送請求前，使用 `client.ListSupportedLanguages()` 取得的清單驗證語言代碼。

**Q: API 是否依字元收費？**  
A: Google 依翻譯的字元數計費。可使用定價頁面估算成本，並考慮快取常用翻譯。

---

## 結論

您現在已了解如何在 C# 中使用官方 Google Translate API **how to translate text**。本教學涵蓋了 **Google translate example**、示範 **translate multiple languages**，並強調了如 API 金鑰安全與錯誤處理等上線就緒的實踐。透過重複使用 `Translator` 輔助工具，您可以將翻譯整合至任何 .NET 服務、桌面應用程式或微服務中。

**下一步**

* 探索 **Google Translate tutorial**，了解如詞彙表與自訂模型等進階功能。  
* 將此程式碼與 ASP.NET Core 結合，建立多語系 Web API。  
* 嘗試批次翻譯 CSV 檔案，以自動化本地化流程。

祝開發順利，盡情打造全球可存取的應用程式！

## 接下來該學什麼？

以下教學涵蓋與本指南技術密切相關的主題，並以完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [如何在 C# 中使用 Google AI 儲存已翻譯的 Word 文件](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}