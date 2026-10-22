---
category: general
date: 2026-09-21
description: Learn how to build an ai document summarizer in C# that creates summary
  from Word files using OpenAI or Google APIs.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- ai document summarizer
- ai powered summarization
- create summary from word
- summarize docx with ai
- summarize using google
language: en
lastmod: 2026-09-21
og_description: ai document summarizer in C# lets you create summary from Word files
  quickly. Follow this guide to use OpenAI or Google for AI powered summarization.
og_image_alt: Diagram showing the workflow of an ai document summarizer processing
  a Word file
og_title: Build an ai document summarizer in C# – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to build an ai document summarizer in C# that creates summary
    from Word files using OpenAI or Google APIs.
  headline: How to use an ai document summarizer in C#
  type: TechArticle
- description: Learn how to build an ai document summarizer in C# that creates summary
    from Word files using OpenAI or Google APIs.
  name: How to use an ai document summarizer in C#
  steps:
  - name: Provider implementation details
    text: '```csharp static class DocumentSummarizer { public static string Summarize(string
      text, SummarizerProvider provider, int maxSentences = 5) { return provider switch
      { SummarizerProvider.OpenAI => SummarizeWithOpenAI(text, maxSentences), SummarizerProvider.Google
      => SummarizeWithGoogle(text, maxSenten'
  - name: Handling token limits and large documents
    text: If the source document exceeds the model’s token quota, split it into paragraphs
      and summarize each chunk separately, then combine the chunk summaries. This
      ensures you never hit the 8 k‑token limit for most models.
  - name: Expected output
    text: '``` Summary: The report highlights a 12% revenue increase driven by new
      product launches. Customer churn dropped to 3% after the recent support improvements.
      Marketing spend rose by 8% but delivered a 15% ROI. The upcoming quarter will
      focus on expanding into APAC markets. Overall, the company is on'
  type: HowTo
tags:
- AI
- C#
- Document Processing
title: How to use an ai document summarizer in C#
url: /net/ai-powered-document-processing/how-to-use-an-ai-document-summarizer-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to use an ai document summarizer in C#

If you need an **ai document summarizer** for .docx files, this guide shows you how to create a summary from Word using C#. You’ll see a complete, runnable example that works with either OpenAI or Google, giving you an **ai powered summarization** solution in minutes.

The tutorial covers everything from project setup to handling edge cases, so you can confidently **summarize docx with ai** in your own applications. No external scripts required—just a few NuGet packages and a short code snippet.

## What you’ll need

- .NET 6.0 or later (the code also works on .NET Core 3.1+)
- An OpenAI API key **or** a Google Cloud Vertex AI key
- The `DocX` NuGet package for reading Word files
- The `OpenAI` or `Google.Cloud.AIPlatform.V1` NuGet package for the chosen provider
- A development environment such as Visual Studio 2022 or VS Code

## Step 1: Set up the ai document summarizer environment

First, create a new console project and add the required packages:

```bash
dotnet new console -n AiSummarizerDemo
cd AiSummarizerDemo
dotnet add package DocX --version 1.0.0
dotnet add package OpenAI --version 2.5.0   # for OpenAI
dotnet add package Google.Cloud.AIPlatform.V1 --version 2.6.0   # for Google
```

> **Pro tip:** Keep your API keys in environment variables (`OPENAI_API_KEY`, `GOOGLE_APPLICATION_CREDENTIALS`) rather than hard‑coding them.

## Step 2: Load a Word document to **create summary from word**

The first functional line reads the source `.docx` file. Using `DocX` we extract plain text, which the AI model will later summarize.

```csharp
using System;
using System.IO;
using Xceed.Words.NET;   // DocX namespace

// Load the source document you want to summarize
Document document = Document.Load("input.docx");

// Extract raw text for the summarizer
string rawText = document.Text;
```

> **Why this step matters:** AI models work best with clean, linear text. Stripping out formatting avoids token‑limit surprises and improves summary relevance.

## Step 3: Choose an **ai powered summarization** provider

You can switch between OpenAI’s GPT‑4 or Google’s PaLM model by setting the `SummarizerProvider` enum. The enum abstracts the provider‑specific logic.

```csharp
enum SummarizerProvider
{
    OpenAI,
    Google
}

// Choose the provider (replace with your preference)
SummarizerProvider provider = SummarizerProvider.OpenAI; // or SummarizerProvider.Google
```

### Provider implementation details

```csharp
static class DocumentSummarizer
{
    public static string Summarize(string text, SummarizerProvider provider, int maxSentences = 5)
    {
        return provider switch
        {
            SummarizerProvider.OpenAI => SummarizeWithOpenAI(text, maxSentences),
            SummarizerProvider.Google => SummarizeWithGoogle(text, maxSentences),
            _ => throw new NotSupportedException("Unsupported summarizer provider.")
        };
    }

    private static string SummarizeWithOpenAI(string text, int maxSentences)
    {
        var apiKey = Environment.GetEnvironmentVariable("OPENAI_API_KEY")
                     ?? throw new InvalidOperationException("OpenAI API key missing.");
        var client = new OpenAIClient(apiKey);
        var request = new ChatRequest
        {
            Model = "gpt-4o-mini",
            Messages =
            {
                new ChatMessage(ChatMessageRole.System,
                    "You are a helpful assistant that creates concise summaries."),
                new ChatMessage(ChatMessageRole.User,
                    $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}")
            }
        };
        var response = client.ChatEndpoint.GetCompletionAsync(request).Result;
        return response.FirstChoice.Message.Content.Trim();
    }

    private static string SummarizeWithGoogle(string text, int maxSentences)
    {
        var client = new PredictionServiceClientBuilder
        {
            // Google credentials are read from GOOGLE_APPLICATION_CREDENTIALS env var
        }.Build();

        var request = new PredictRequest
        {
            // The model name depends on your Vertex AI deployment
            Endpoint = "projects/YOUR_PROJECT/locations/us-central1/publishers/google/models/text-bison",
            Instances = { new Value { StringValue = $"Summarize in {maxSentences} sentences: {text}" } }
        };

        var response = client.Predict(request);
        return response.Predictions[0].StringValue.Trim();
    }
}
```

> **Why we abstract the provider:** This pattern lets you **summarize using google** or OpenAI without changing the calling code—great for testing or switching providers later.

## Step 4: Generate a concise summary – **summarize docx with ai**

Now call the helper method, limiting the output to five sentences (adjustable via `maxSentences`).

```csharp
// Generate a concise summary with a maximum of 5 sentences
string summary = DocumentSummarizer.Summarize(rawText, provider, maxSentences: 5);
```

### Handling token limits and large documents

If the source document exceeds the model’s token quota, split it into paragraphs and summarize each chunk separately, then combine the chunk summaries. This ensures you never hit the 8 k‑token limit for most models.

```csharp
static string SummarizeLargeText(string fullText, SummarizerProvider provider, int maxSentences)
{
    const int chunkSize = 2000; // approximate token count
    var chunks = fullText
        .Split(new[] { "\n\n" }, StringSplitOptions.RemoveEmptyEntries)
        .Select(p => p.Trim())
        .Where(p => p.Length > 0)
        .ToList();

    var partialSummaries = new List<string>();
    var sb = new System.Text.StringBuilder();

    foreach (var paragraph in chunks)
    {
        sb.Append(paragraph);
        if (sb.Length > chunkSize)
        {
            partialSummaries.Add(Summarize(sb.ToString(), provider, maxSentences));
            sb.Clear();
        }
    }

    if (sb.Length > 0)
        partialSummaries.Add(Summarize(sb.ToString(), provider, maxSentences));

    // Final pass to merge chunk summaries
    return Summarize(string.Join(" ", partialSummaries), provider, maxSentences);
}
```

## Step 5: Display the resulting summary

Finally, write the summary to the console or store it wherever you need.

```csharp
// Display the resulting summary
Console.WriteLine("Summary:\n" + summary);
```

### Expected output

```
Summary:
The report highlights a 12% revenue increase driven by new product launches. Customer churn dropped to 3% after the recent support improvements. Marketing spend rose by 8% but delivered a 15% ROI. The upcoming quarter will focus on expanding into APAC markets. Overall, the company is on track to exceed its annual targets.
```

The exact phrasing varies with the AI provider, but the structure (≤ 5 sentences) remains consistent.

## Full runnable program

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Xceed.Words.NET;               // DocX
using OpenAI;                       // OpenAI SDK
using OpenAI.Chat;                  // Chat classes
using Google.Cloud.AIPlatform.V1;   // Google Vertex AI SDK
using Google.Protobuf;              // Value type

enum SummarizerProvider { OpenAI, Google }

static class DocumentSummarizer
{
    public static string Summarize(string text, SummarizerProvider provider, int maxSentences = 5)
        => provider switch
        {
            SummarizerProvider.OpenAI => SummarizeWithOpenAI(text, maxSentences),
            SummarizerProvider.Google => SummarizeWithGoogle(text, maxSentences),
            _ => throw new NotSupportedException("Unsupported provider.")
        };

    private static string SummarizeWithOpenAI(string text, int maxSentences)
    {
        var apiKey = Environment.GetEnvironmentVariable("OPENAI_API_KEY")
                     ?? throw new InvalidOperationException("OpenAI API key missing.");
        var client = new OpenAIClient(apiKey);
        var request = new ChatRequest
        {
            Model = "gpt-4o-mini",
            Messages =
            {
                new ChatMessage(ChatMessageRole.System,
                    "You are a helpful assistant that creates concise summaries."),
                new ChatMessage(ChatMessageRole.User,
                    $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}")
            }
        };
        var response = client.ChatEndpoint.GetCompletionAsync(request).Result;
        return response.FirstChoice.Message.Content.Trim();
    }

    private static string SummarizeWithGoogle(string text, int maxSentences)
    {
        var client = new PredictionServiceClientBuilder().Build();
        var request = new PredictRequest
        {
            Endpoint = "projects/YOUR_PROJECT/locations/us-central1/publishers/google/models/text-bison",
            Instances = { new Value { StringValue = $"Summarize in {maxSentences} sentences: {text}" } }
        };
        var response = client.Predict(request);
        return response.Predictions[0].StringValue.Trim();
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Load the source document you want to summarize
        var doc = Document.Load("input.docx");
        string rawText = doc.Text;

        // Step 2: Choose the AI provider for summarization (OpenAI or Google)
        SummarizerProvider provider = SummarizerProvider.OpenAI; // or SummarizerProvider.Google

        // Step 3: Generate a concise summary with a maximum of 5 sentences
        string summary = DocumentSummarizer.Summarize(rawText, provider, maxSentences: 5);

        // Step 4: Display the resulting summary
        Console.WriteLine("Summary:\n" + summary);
    }
}
```

Save the file as `Program.cs`, place an `


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Summarize Word Document in C# with Aspose.Words API – Complete AI‑Powered Guide](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}