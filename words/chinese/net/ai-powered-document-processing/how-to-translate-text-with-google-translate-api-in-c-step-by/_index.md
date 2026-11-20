---
category: general
date: 2026-11-15
description: 学习如何在 C# 中使用 Google 翻译文本。本教程展示了一个 Google 翻译示例，涵盖多语言处理和最佳实践。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: zh
lastmod: 2026-11-15
og_description: 如何在 C# 中使用完整的 Google 翻译示例进行文本翻译。请按照本教程安全地翻译多种语言。
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: 如何使用 C# 中的 Google 翻译 API 翻译文本 – 快速教程
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
title: 如何在 C# 中使用 Google 翻译 API 翻译文本——逐步指南
url: /zh/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用 Google Translate API 翻译文本 – 步骤指南

如果您需要在 .NET 应用程序中 **翻译文本**，Google Cloud Translation API 提供了可靠的、语言无关的解决方案。在本教程中，您将看到一个 **Google Translate 示例**，它可以翻译一个简单的字符串，扩展为 **翻译多种语言**，并遵循 API 密钥和错误处理的最佳实践。

您将获得一个可直接运行的 C# 控制台程序，对 **使用 Google 翻译文本** 有清晰的理解，并有信心将代码适配到更大的项目中。

## 本教程涵盖内容

* 设置 Google Cloud 项目并获取 API 密钥。  
* 安装 `Google.Cloud.Translation.V2` NuGet 包。  
* 编写干净、可重用的代码，使用官方 SDK **翻译文本**。  
* 将解决方案扩展为一次调用 **翻译多种语言**。  
* 常见陷阱及生产级实现的技巧。

### 前置条件

* .NET 6.0 SDK 或更高版本（代码可在 .NET Core 和 .NET Framework 上编译）。  
* 拥有已启用 **Cloud Translation API** 的 Google Cloud 账户。  
* 具备 C# 和控制台应用的基本知识。  

---

## 第一步：安装 Google Cloud Translation 客户端库

官方客户端库抽象了 HTTP 调用并为您处理身份验证。

```bash
dotnet add package Google.Cloud.Translation.V2
```

运行该命令会将 `Google.Cloud.Translation.V2` 包添加到您的项目中，使您能够访问本指南中始终使用的 `TranslationClient` 类。

> **此步骤重要原因** – 使用 SDK 可避免手动构建请求，减少错误，并确保您使用的是 Google 最新的 API 版本。

## 第二步：创建可重用的翻译助手

将翻译逻辑封装在静态类中可以使代码可重用，并且将 API 密钥的处理隔离开来。

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

> **我们返回字典的原因** – 当您需要 **翻译多种语言** 时，按语言代码组织结果可以让后续处理更加简洁。

## 第三步：构建使用该助手的控制台应用程序

下面是完整的 `Program.cs` 示例，演示了单文本翻译和批量翻译两种情况。

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

**预期的控制台输出**

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

> **为什么要使用 try/catch 块？** – 网络错误、配额限制或无效的 API 密钥都会抛出异常。优雅地处理它们可以提升用户体验并保持应用程序的稳定性。

## 第四步：保护您的 API 密钥

如上所示将 API 密钥硬编码在代码中仅适用于快速演示，生产环境中不推荐。请遵循以下做法：

* 将密钥存储在环境变量 (`GOOGLE_API_KEY`) 中，并在运行时读取：  
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* 在 Google Cloud（App Engine、Cloud Run 等）上运行时，使用 **Google Application Default Credentials** 替代 API 密钥。
* 在 Google Cloud 控制台中将密钥限制为仅可访问 Translation API，并将使用限制在特定 IP 地址或引用来源。

## 第五步：将解决方案扩展到真实场景

### 处理语言检测

如果您需要了解源语言，响应对象中包含 `DetectedSourceLanguage`：

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### 翻译大文档

API 每次请求支持最高 30 KB。对于更大的文本，需要将内容拆分为块，分别翻译每个块，然后再将结果拼接起来。保持句子边界完整，以避免出现别扭的表达。

### 限流与配额

Google 对每分钟的请求数量有限制。实现带指数退避的重试策略，以遵守配额限制并避免出现 `429 Too Many Requests` 错误。

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## 常见问题与边缘情况

**Q: 我可以翻译整个 HTML 页面吗？**  
A: 可以。在调用 `TranslateText` 时使用 `Format` 参数（`"text"` 或 `"html"`）。SDK 通过接受 `TranslateTextRequest` 的 `TranslateText` 重载公开了此功能。

**Q: 如果某种语言不受支持怎么办？**  
A: API 会返回错误。在发起请求前，请使用 `client.ListSupportedLanguages()` 返回的列表验证语言代码。

**Q: API 是否按字符计费？**  
A: Google 按翻译的字符数计费。可使用定价页面估算费用，并考虑缓存常用翻译以降低成本。

---

## 结论

您现在已经了解了如何在 C# 中使用官方的 Google Translate API **翻译文本**。本教程涵盖了 **Google 翻译示例**，演示了 **翻译多种语言**，并强调了生产就绪的实践，如 API 密钥安全和错误处理。通过复用 `Translator` 助手，您可以将翻译功能集成到任何 .NET 服务、桌面应用或微服务中。

**后续步骤**

* 探索 **Google Translate 教程**，了解词汇表和自定义模型等高级功能。  
* 将此代码与 ASP.NET Core 结合，创建多语言 Web API。  
* 尝试对 CSV 文件进行批量翻译，以自动化本地化流水线。

祝编码愉快，尽情构建面向全球的应用！

## 接下来您应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在自己的项目中探索替代实现方案。

- [如何在 C# 中使用 Google AI 保存已翻译的 Word 文档](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}