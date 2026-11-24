---
category: general
date: 2026-11-15
description: Learn how to translate text with Google Translate API in C#. This tutorial shows a complete Google Translate example, handling multiple languages and best practices.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: en
lastmod: 2026-11-15
og_description: How to translate text with Google Translate API in C# using a complete example. Follow this tutorial to translate multiple languages safely.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: How to translate text with Google Translate API in C# – quick tutorial
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to translate text with Google Translate API in C#. This tutorial shows a Google Translate example, handling multiple languages and best practices.
  headline: How to translate text with Google Translate API in C# – step‑by‑step guide
  type: TechArticle
- description: Learn how to translate text with Google Translate API in C#. This tutorial shows a Google Translate example, handling multiple languages and best practices.
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
  - answer: 'Google bills per character. Estimate costs using the pricing
      page and consider caching frequent translations. --- ## Conclusion You now know
      **how to translate text** in C# using the official Google Translate API. The
      tutorial covered a **Google translate example**, demonstrated **transla'
    question: Does the API charge per character?
  type: FAQPage
tags:
- Google Cloud
- C#
- Translation API
title: Use Google Translate API to translate text in C# – step‑by‑step guide
url: /net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to translate text with Google Translate API in C# – step‑by‑step guide

If you need to **how to translate text** in a .NET application, the Google Cloud Translation API offers a reliable, language‑agnostic solution. In this tutorial you’ll see a **Google Translate example** that translates a simple string, expands to **translate multiple languages**, and follows best practices for API keys and error handling.

You’ll walk away with a ready‑to‑run C# console program, a clear understanding of **translate text with Google**, and the confidence to adapt the code for larger projects.

## What this tutorial covers

* Setting up a Google Cloud project and obtaining an API key.  
* Installing the `Google.Cloud.Translation.V2` NuGet package.  
* Writing clean, reusable code that **how to translate text** using the official SDK.  
* Extending the solution to **translate multiple languages** in a single call.  
* Common pitfalls and tips for production‑grade implementations.

### Prerequisites

* .NET 6.0 SDK or later (the code compiles with .NET Core and .NET Framework).  
* A Google Cloud account with the **Cloud Translation API** enabled.  
* Basic familiarity with C# and console applications.  

---

## Step 1: Install the Google Cloud Translation client library

The official client library abstracts HTTP calls and handles authentication for you.

```bash
dotnet add package Google.Cloud.Translation.V2
```

Running the command adds the `Google.Cloud.Translation.V2` package to your project, giving you access to the `TranslationClient` class used throughout this guide.

> **Why this step matters** – Using the SDK avoids manual request construction, reduces bugs, and ensures you’re aligned with Google’s latest API version.

## Step 2: Create a reusable translation helper

Encapsulating the translation logic in a static class makes the code reusable and isolates API‑key handling.

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

> **Why we return a dictionary** – When you need to **translate multiple languages**, organizing results by language code makes downstream processing straightforward.

Below is a corrected version of the helper that uses the exact method names provided by the V2 client library and includes the necessary namespaces:

```csharp
using Google.Cloud.Translation.V2;
using System;
using System.Collections.Generic;
using System.Linq;

namespace GoogleTranslateDemo
{
    public static class Translator
    {
        public static string Translate(string sourceText, string targetLanguage, string apiKey)
        {
            var client = TranslationClient.CreateFromApiKey(apiKey);
            var response = client.TranslateText(sourceText, targetLanguage);
            return response.TranslatedText;
        }

        public static Dictionary<string, string[]> TranslateMultiple(string[] sourceTexts,
                                                                    string[] targetLanguages,
                                                                    string apiKey)
        {
            var client = TranslationClient.CreateFromApiKey(apiKey);
            var result = new Dictionary<string, string[]>();

            foreach (var lang in targetLanguages)
            {
                // Correct method name for translating multiple texts
                var translations = client.TranslateText(sourceTexts, lang);
                result[lang] = translations.Select(t => t.TranslatedText).ToArray();
            }

            return result;
        }
    }
}
```

> **Why the corrected version matters** – The V2 SDK provides `TranslateText(IEnumerable<string>, string)` for batch translation. Using the proper method name prevents runtime errors and aligns with the official API reference.

## Step 3: Build the console application that uses the helper

Below is a complete `Program.cs` that demonstrates both a single‑text translation and a batch translation.

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

**Expected console output**

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

> **Why the try/catch blocks?** – Network errors, quota limits, or an invalid API key raise exceptions. Handling them gracefully improves the user experience and keeps your application stable.

## Step 4: Secure your API key

Hard‑coding the API key, as shown above, is acceptable for a quick demo but not for production. Follow these practices:

* Store the key in an environment variable (`GOOGLE_API_KEY`) and read it at runtime:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Use **Google Application Default Credentials** instead of an API key when running on Google Cloud (App Engine, Cloud Run, etc.).
* Restrict the key to the Translation API in the Google Cloud console and limit usage to specific IP addresses or referrers.

## Step 5: Extend the solution for real‑world scenarios

### Handling language detection

If you need to know the source language, the response object contains `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Translating large documents

The API supports up to 30 KB per request. For larger texts, split the content into chunks, translate each chunk, and then concatenate the results. Keep sentence boundaries intact to avoid awkward phrasing.

### Rate‑limiting and quotas

Google enforces per‑minute request limits. Implement a retry policy with exponential back‑off to respect quota limits and avoid `429 Too Many Requests` errors.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Common questions and edge cases

**Q: Can I translate a whole HTML page?**  
A: Yes. Use the `Format` parameter (`"text"` or `"html"`) when calling `TranslateText`. The SDK exposes this via the `TranslateText` overload that accepts a `TranslateTextRequest`.

**Q: What if a language isn’t supported?**  
A: The API returns an error. Validate language codes against the list returned by `client.ListSupportedLanguages()` before making a request.

**Q: Does the API charge per character?**  
A: Google bills per character translated. Estimate costs using the pricing page and consider caching frequent translations.

---

## Conclusion

You now know **how to translate text** in C# using the official Google Translate API. The tutorial covered a **Google translate example**, demonstrated **translate multiple languages**, and highlighted production‑ready practices such as API‑key security and error handling. By reusing the `Translator` helper, you can integrate translation into any .NET service, desktop app, or microservice.

**Next steps**

* Explore the **Google Translate tutorial** for advanced features like glossaries and custom models.  
* Combine this code with ASP.NET Core to create a multilingual web API.  
* Experiment with batch translation of CSV files to automate localization pipelines.

Happy coding, and enjoy building globally accessible applications!


## What should you learn next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to save translated Word document in C# with Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}