---
category: general
date: 2026-09-11
description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
  and generating a concise summary of a Word document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: en
lastmod: 2026-09-11
og_description: How to summarize text in C#? This tutorial shows you how to read the
  API key, call OpenAI, and create a summary of a Word document.
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: How to summarize text in C# with OpenAI – step‑by‑step guide
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
title: How to summarize text in C# using OpenAI
url: /net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to summarize text in C# using OpenAI

If you need to **how to summarize text** in a .docx file, this guide shows you a complete, ready‑to‑run solution. You’ll learn how to read the API key from your environment, how to call OpenAI (or Google) from C#, and how to create a concise summary of a Word document.

Summarizing a Word document is a common requirement for report generation, email digests, or knowledge‑base extraction. By the end of this tutorial you will have a command‑line program that prints a five‑sentence summary of any `.docx` file you provide.

## Prerequisites

- .NET 6.0 SDK or later (download from [dotnet.microsoft.com](https://dotnet.microsoft.com/download))
- A valid OpenAI API key stored in an environment variable named `OPENAI_API_KEY` (you’ll see **read api key** in action)
- The `DocumentFormat.OpenXml` NuGet package for reading `.docx` files
- The `OpenAI` NuGet package (or `Google.AI` if you prefer the Google provider)

## Step 1: Set up the project and install dependencies

Create a new console project and add the required packages:

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **Pro tip:** Keep your `csproj` tidy by grouping related packages under a `<ItemGroup>` if you later add more dependencies.

## Step 2: Read the API key securely

Hard‑coding secrets is unsafe. The tutorial demonstrates the proper way to **read api key** from environment variables.

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

## Step 3: Load the Word document you want to summarize

The code below shows **how to summarize word document** content by extracting plain text from the OpenXML structure.

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

## Step 4: Build a reusable summarizer class

This class encapsulates **how to call openai** (or Google) and implements **how to create summary** logic. It also lets you switch providers with a single enum value.

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

### Why this structure matters

- **Separation of concerns:** Loading the document, reading the API key, and calling the AI service are isolated into their own methods. This makes the code easier to test and extend.
- **Provider flexibility:** By using an enum you can switch between OpenAI and Google without touching the calling code, which directly answers **how to call openai** and **how to create summary** in a reusable way.
- **Error handling:** Missing API keys throw a clear exception, preventing silent failures.

## Step 5: Put everything together in `Program.cs`

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

### Expected output

Running the program with a sample document:

```bash
dotnet run -- "sample/input.docx"
```

might produce:

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## Step 6: Common variations and edge cases

| Situation | Recommended adjustment |
|-----------|------------------------|
| **Large documents** ( > 10 KB ) | Split the text into chunks and summarize each chunk, then combine the results. |
| **Non‑English content** | Pass the language hint in the prompt, e.g., “Summarize the following French text …”. |
| **Google provider** | Replace the `SummarizeWithOpenAIAsync` call with the appropriate Google API client; keep the same enum interface. |
| **Custom summary length** | Change the `maxSentences` argument when calling `SummarizeAsync`. |
| **Missing API key** | The `GetOpenAIApiKey` method already throws a clear exception; catch it in `Main` if you want a friendlier message. |

## Pro tips for production use

1. **Cache the API key** – reading from the environment each call adds negligible overhead, but you can store it in a static readonly field if you call the summarizer many times in one process.
2. **Rate‑limit requests** – OpenAI enforces request limits; implement exponential back‑off if you hit `429 Too Many Requests`.
3. **Sanitize input** – remove personally identifiable information before sending text to an external AI service.
4. **Unit test the extraction logic** – mock `WordprocessingDocument` to verify `ExtractTextFromDocx` works with different document structures.

## Conclusion

You now know **how to summarize text** in C# by securely reading the API key, calling OpenAI, and generating a concise summary of a Word document. The same pattern lets you **how to call openai** with other providers, **how to create summary** logic for different content types, and safely **read api key** values from the environment. Experiment with longer documents, different providers, or custom prompts to tailor the summarization to your specific domain.

---


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Summarize Word Document in C# with Aspose.Words API – Complete AI‑Powered Guide](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [how to create pdf from Word – Complete C# Guide](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Word Document - How to Remove Content](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}