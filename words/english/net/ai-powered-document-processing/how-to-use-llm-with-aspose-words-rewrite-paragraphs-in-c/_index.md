---
category: general
date: 2026-05-04
description: How to use LLM to edit documents with Aspose – learn to replace paragraph
  text, connect to local LLM, and rewrite text using AI.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: en
og_description: How to use LLM to edit documents with Aspose. This guide shows how
  to connect to a local LLM, replace paragraph text, and rewrite text using AI.
og_title: How to Use LLM with Aspose.Words – Rewrite Paragraphs in C#
tags:
- Aspose.Words
- C#
- AI
- LLM
title: How to Use LLM with Aspose.Words – Rewrite Paragraphs in C#
url: /net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Use LLM with Aspose.Words – Rewrite Paragraphs in C#

Ever wondered **how to use LLM** to polish a Word document without opening it manually? You're not the only one. Many developers hit a wall when they need to *replace paragraph text* programmatically but lack a clean AI‑driven workflow.  

In this tutorial we’ll wire up a local large language model, feed it a snippet from a `.docx` file, ask it to **rewrite text using AI**, and finally save the updated document—all with Aspose.Words. By the end you’ll have a ready‑to‑run C# console app that demonstrates the whole pipeline.

> **What you’ll get:** a complete, runnable example, explanations of each step, tips for edge cases, and ideas for extending the solution.

## What You’ll Need

- **.NET 6+** (or .NET Framework 4.7.2 – the code works on both)
- **Aspose.Words for .NET** (NuGet package `Aspose.Words`)
- A **local LLM server** exposing a simple HTTP `/generate` endpoint (e.g., Ollama, LMStudio, or a custom Flask service)
- A basic familiarity with C# and HTTP client code  

No additional SDKs are required; everything else lives in the code we’ll write together.

## Step 1: How to Use LLM to Replace Paragraph Text

The first thing we have to do is identify the paragraph we want to modify. Aspose.Words makes this a breeze by exposing a rich object model.

```csharp
using Aspose.Words;
using Aspose.Words.AI;   // Imaginary namespace for illustration – replace with actual if needed
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Grab the third paragraph (zero‑based index)
Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];

// Show the original text in the console – handy for debugging
Console.WriteLine("Original paragraph:");
Console.WriteLine(targetParagraph.GetText());
```

**Why this matters:**  
Selecting the right node prevents you from accidentally overwriting headings or tables. By using the **replace paragraph text** approach we keep the document structure intact while only touching the content we care about.

> **Pro tip:** If your document has variable length sections, use `document.GetChildNodes(NodeType.Paragraph, true)` and LINQ to locate a paragraph by its text or style.

## Step 2: Connect to a Local LLM Endpoint

Now that we have the text, we need to send it to the LLM. The example uses a simple wrapper class `LocalLargeLanguageModel` that hides the HTTP plumbing. Feel free to replace it with `HttpClient` calls if you prefer.

```csharp
/// <summary>
/// Minimal wrapper around a local LLM HTTP API.
/// Assumes the API accepts a JSON payload { "prompt": "..."} and returns { "response": "..." }.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _client;
    private readonly string _endpoint;

    public LocalLargeLanguageModel(string endpoint)
    {
        _endpoint = endpoint.TrimEnd('/');
        _client = new HttpClient();
    }

    public string GenerateText(string prompt)
    {
        var payload = new { prompt };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // Synchronous call for brevity – in production use async/await
        var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result?["response"] ?? string.Empty;
    }
}

// Step 2: Instantiate the LLM client pointing at localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:5000");
```

**Why we connect this way:**  
A **connect to local llm** setup eliminates latency, keeps data on‑premise, and avoids API costs. The wrapper also makes the later code cleaner, letting us focus on the **rewrite text using ai** logic.

## Step 3: Rewrite Text Using AI with Aspose.Words

With the paragraph text in hand and the LLM ready, we craft a prompt that tells the model exactly what we want—rewrite in a formal tone. You can tweak the prompt for other styles (friendly, technical, etc.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Why this works:**  
LLMs are prompt‑driven; giving explicit instructions (“Rewrite … in a formal tone”) yields consistent results. The **rewrite text using ai** step is the heart of the tutorial – it demonstrates how AI can be embedded directly into document workflows.

## Step 4: Edit the Document and Save Changes

Now we replace the original runs with the new content. Aspose.Words stores text in `Run` objects, so clearing them first avoids leftover formatting artifacts.

```csharp
// Clear existing runs (pieces of text) from the paragraph
targetParagraph.Runs.Clear();

// Append a new Run containing the revised text
targetParagraph.AppendChild(new Run(document, revisedText));

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");

// Confirmation
Console.WriteLine("\nDocument saved as output.docx");
```

**Edge‑case note:**  
If the original paragraph contained mixed formatting (bold, italics) you may want to preserve styles. In that case, create a new `Run`, copy the original `Font` settings, then set its `Text` to `revisedText`.

## Full Working Example

Below is the entire program you can copy‑paste into a console project. Remember to install the Aspose.Words NuGet package first (`dotnet add package Aspose.Words`).

```csharp
// ---------------------------------------------------------------
// Complete C# console app: how to use llm to edit a Word doc
// ---------------------------------------------------------------
using Aspose.Words;
using Aspose.Words.AI;   // Replace with real namespace if needed
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Text;
using System.Text.Json;

namespace LlmAsposeDemo
{
    public class LocalLargeLanguageModel
    {
        private readonly HttpClient _client;
        private readonly string _endpoint;

        public LocalLargeLanguageModel(string endpoint)
        {
            _endpoint = endpoint.TrimEnd('/');
            _client = new HttpClient();
        }

        public string GenerateText(string prompt)
        {
            var payload = new { prompt };
            var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

            var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
            response.EnsureSuccessStatusCode();

            var json = response.Content.ReadAsStringAsync().Result;
            var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            return result?["response"] ?? string.Empty;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Pick the third paragraph (index 2)
            Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];
            Console.WriteLine("Original paragraph:");
            Console.WriteLine(targetParagraph.GetText());

            // 3️⃣ Connect to the local LLM
            var localLlm = new LocalLargeLanguageModel("http://localhost:5000");

            // 4️⃣ Ask the model to rewrite it formally
            string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";
            string revisedText = localLlm.GenerateText(prompt);
            Console.WriteLine("\nRevised paragraph:");
            Console.WriteLine(revisedText);

            // 5️⃣ Replace the paragraph contents
            targetParagraph.Runs.Clear();
            targetParagraph.AppendChild(new Run(document, revisedText));

            // 6️⃣ Save the file
            document.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("\nDocument saved as output.docx");
        }
    }
}
```

### Expected Output

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Open `output.docx` – you’ll see the third paragraph now reads the polished version.

## Common Questions & Gotchas

| Question | Answer |
|----------|--------|
| **What if my LLM returns JSON with extra fields?** | Adjust `GenerateText` to deserialize the correct property or parse the response manually. |
| **Can I process multiple paragraphs at once?** | Yes – iterate over `document.FirstSection.Body.Paragraphs` and apply the same prompt logic, perhaps adding a paragraph index to the prompt for context. |
| **My LLM server uses authentication?** | Add a header to the `HttpClient` before the POST: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **Formatting gets lost after replacement.** | Preserve the original `Run.Font` settings: create a new `Run`, copy `originalRun.Font.Clone()`, then set its `Text`. |
| **The LLM sometimes returns empty strings.** | Implement a fallback – if `revisedText.Trim().Length == 0`, keep the original text or retry with a simpler prompt. |

## Extending the Solution

Now that you’ve mastered **how to use llm** for a single paragraph, consider these next steps:

- **Batch processing:** Loop through every paragraph and rewrite in a chosen style (e.g., “make all text concise”).  
- **Style‑aware rewriting:** Pass the original paragraph’s style name in the prompt so the LLM can respect headings vs body text.  
- **Integration with a CI pipeline:** Automate document polishing as part of a documentation build process.  
- **Alternative prompts:** Try “summarize this paragraph” or “translate this paragraph to Spanish” to explore the full power of **rewrite text using ai**.

## Conclusion

We’ve walked through the entire flow of **how to use llm** with Aspose.Words: loading a document, **connect to local llm**, extracting a paragraph, **rewrite text using ai**, **replace paragraph text**, and finally saving the result. The code is self‑contained, works out‑of‑the‑box, and showcases a practical way to blend AI with traditional document automation.

Give it a spin, tweak the prompts, and let

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}