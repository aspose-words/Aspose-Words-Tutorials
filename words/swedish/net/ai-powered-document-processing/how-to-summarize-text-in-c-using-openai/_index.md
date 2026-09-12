---
category: general
date: 2026-09-11
description: Lär dig hur du sammanfattar text i C# genom att läsa API-nyckeln, anropa
  OpenAI och generera en koncis sammanfattning av ett Word‑dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: sv
lastmod: 2026-09-11
og_description: Hur sammanfattar man text i C#? Den här handledningen visar hur du
  läser API-nyckeln, anropar OpenAI och skapar en sammanfattning av ett Word-dokument.
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: Hur man sammanfattar text i C# med OpenAI – steg‑för‑steg guide
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
title: Hur man sammanfattar text i C# med OpenAI
url: /sv/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man sammanfattar text i C# med OpenAI

Om du behöver **hur man sammanfattar text** i en .docx‑fil, visar den här guiden en komplett, färdig‑att‑köra‑lösning. Du kommer att lära dig hur du läser API‑nyckeln från din miljö, hur du anropar OpenAI (eller Google) från C#, och hur du skapar en koncis sammanfattning av ett Word‑dokument.

Att sammanfatta ett Word‑dokument är ett vanligt behov för rapportgenerering, e‑post‑sammanfattningar eller kunskapsbasutdrag. I slutet av den här tutorialen har du ett kommandoradsprogram som skriver ut en fem‑menings‑sammanfattning av vilken `.docx`‑fil du än anger.

## Förutsättningar

- .NET 6.0 SDK eller senare (ladda ner från [dotnet.microsoft.com](https://dotnet.microsoft.com/download))
- En giltig OpenAI API‑nyckel lagrad i en miljövariabel med namnet `OPENAI_API_KEY` (du kommer att se **läsa api‑nyckel** i aktion)
- NuGet‑paketet `DocumentFormat.OpenXml` för att läsa `.docx`‑filer
- NuGet‑paketet `OpenAI` (eller `Google.AI` om du föredrar Google‑leverantören)

## Steg 1: Ställ in projektet och installera beroenden

Skapa ett nytt konsolprojekt och lägg till de nödvändiga paketen:

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **Proffstips:** Håll din `csproj` snygg genom att gruppera relaterade paket under ett `<ItemGroup>` om du senare lägger till fler beroenden.

## Steg 2: Läs API‑nyckeln säkert

Att hårdkoda hemligheter är osäkert. Tutorialen visar det korrekta sättet att **läsa api‑nyckel** från miljövariabler.

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

## Steg 3: Läs in Word‑dokumentet du vill sammanfatta

Koden nedan visar **hur man sammanfattar word‑dokument**‑innehåll genom att extrahera vanlig text från OpenXML‑strukturen.

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

## Steg 4: Bygg en återanvändbar summarizer‑klass

Denna klass kapslar in **hur man anropar openai** (eller Google) och implementerar logik för **hur man skapar sammanfattning**. Den låter dig också byta leverantör med ett enda enum‑värde.

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

### Varför den här strukturen är viktig

- **Separation of concerns:** Laddning av dokumentet, läsning av API‑nyckeln och anrop av AI‑tjänsten är isolerade i egna metoder. Detta gör koden enklare att testa och utöka.
- **Provider flexibility:** Genom att använda ett enum kan du växla mellan OpenAI och Google utan att röra anropskoden, vilket direkt svarar på **hur man anropar openai** och **hur man skapar sammanfattning** på ett återanvändbart sätt.
- **Error handling:** Saknade API‑nycklar kastar ett tydligt undantag, vilket förhindrar tysta fel.

## Steg 5: Sätt ihop allt i `Program.cs`

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

### Förväntat resultat

Att köra programmet med ett exempel‑dokument:

```bash
dotnet run -- "sample/input.docx"
```

kan ge:

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## Steg 6: Vanliga variationer och kantfall

| Situation | Rekommenderad justering |
|-----------|------------------------|
| **Stora dokument** ( > 10 KB ) | Dela upp texten i delar och sammanfatta varje del, kombinera sedan resultaten. |
| **Icke‑engelskt innehåll** | Skicka språk‑hint i prompten, t.ex. “Summarize the following French text …”. |
| **Google‑leverantör** | Ersätt anropet `SummarizeWithOpenAIAsync` med motsvarande Google‑API‑klient; behåll samma enum‑gränssnitt. |
| **Anpassad sammanfattningslängd** | Ändra argumentet `maxSentences` när du anropar `SummarizeAsync`. |
| **Saknad API‑nyckel** | Metoden `GetOpenAIApiKey` kastar redan ett tydligt undantag; fånga det i `Main` om du vill ha ett vänligare meddelande. |

## Proffstips för produktion

1. **Cache API‑nyckeln** – att läsa från miljön för varje anrop ger försumbar overhead, men du kan lagra den i ett statiskt readonly‑fält om du anropar summarizern många gånger i samma process.  
2. **Rate‑limit requests** – OpenAI har begränsningar för förfrågningar; implementera exponentiell back‑off om du får `429 Too Many Requests`.  
3. **Sanitize input** – ta bort personligt identifierbar information innan du skickar text till en extern AI‑tjänst.  
4. **Unit test the extraction logic** – mocka `WordprocessingDocument` för att verifiera att `ExtractTextFromDocx` fungerar med olika dokumentstrukturer.  

## Slutsats

Du vet nu **hur man sammanfattar text** i C# genom att säkert läsa API‑nyckeln, anropa OpenAI och generera en koncis sammanfattning av ett Word‑dokument. Samma mönster låter dig **hur man anropar openai** med andra leverantörer, **hur man skapar sammanfattning**‑logik för olika innehållstyper, och säkert **läsa api‑nyckel**‑värden från miljön. Experimentera med längre dokument, olika leverantörer eller anpassade prompts för att skräddarsy sammanfattningen till din specifika domän.

---

## Vad bör du lära dig härnäst?

De följande tutorialerna täcker närliggande ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Sammanfatta Word‑dokument i C# med Aspose.Words API – Komplett AI‑driven guide](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [hur man skapa pdf från Word – Komplett C#‑guide](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Word‑dokument – Hur man tar bort innehåll](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}