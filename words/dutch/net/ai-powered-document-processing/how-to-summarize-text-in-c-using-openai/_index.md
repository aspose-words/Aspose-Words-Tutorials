---
category: general
date: 2026-09-11
description: Leer hoe je tekst kunt samenvatten in C# door de API‑sleutel te lezen,
  OpenAI aan te roepen en een beknopte samenvatting van een Word‑document te genereren.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: nl
lastmod: 2026-09-11
og_description: Hoe tekst samenvatten in C#? Deze tutorial laat zien hoe je de API‑sleutel
  leest, OpenAI aanroept en een samenvatting van een Word‑document maakt.
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: Hoe tekst samenvatten in C# met OpenAI – stapsgewijze handleiding
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
title: Hoe tekst samenvatten in C# met OpenAI
url: /nl/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe tekst samenvatten in C# met OpenAI

Als je **how to summarize text** in een .docx‑bestand moet doen, laat deze gids je een complete, kant‑klaar oplossing zien. Je leert hoe je de API‑sleutel uit je omgeving leest, hoe je OpenAI (of Google) vanuit C# aanroept, en hoe je een beknopte samenvatting van een Word‑document maakt.

Het samenvatten van een Word‑document is een veelvoorkomende behoefte voor rapportgeneratie, e‑mail‑samenvattingen of kennisbank‑extractie. Aan het einde van deze tutorial heb je een opdracht‑regelprogramma dat een samenvatting van vijf zinnen afdrukt van elk `.docx`‑bestand dat je opgeeft.

## Vereisten

- .NET 6.0 SDK of later (download van [dotnet.microsoft.com](https://dotnet.microsoft.com/download))
- Een geldige OpenAI API‑sleutel opgeslagen in een omgevingsvariabele met de naam `OPENAI_API_KEY` (je ziet **read api key** in actie)
- Het `DocumentFormat.OpenXml` NuGet‑pakket voor het lezen van `.docx`‑bestanden
- Het `OpenAI` NuGet‑pakket (of `Google.AI` als je de Google‑provider verkiest)

## Stap 1: Het project opzetten en afhankelijkheden installeren

Maak een nieuw console‑project aan en voeg de benodigde pakketten toe:

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **Pro tip:** Houd je `csproj` overzichtelijk door gerelateerde pakketten onder een `<ItemGroup>` te groeperen als je later meer afhankelijkheden toevoegt.

## Stap 2: De API‑sleutel veilig lezen

Hard‑coderen van geheimen is onveilig. De tutorial toont de juiste manier om **read api key** uit omgevingsvariabelen te lezen.

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

## Stap 3: Laad het Word‑document dat je wilt samenvatten

De onderstaande code laat zien **how to summarize word document** inhoud door platte tekst uit de OpenXML‑structuur te extraheren.

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

## Stap 4: Bouw een herbruikbare summarizer‑klasse

Deze klasse omsluit **how to call openai** (of Google) en implementeert de **how to create summary**‑logica. Het stelt je ook in staat om van provider te wisselen met één enum‑waarde.

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

### Waarom deze structuur belangrijk is

- **Separation of concerns:** Het laden van het document, het lezen van de API‑sleutel en het aanroepen van de AI‑service zijn geïsoleerd in eigen methoden. Dit maakt de code makkelijker te testen en uit te breiden.
- **Provider flexibility:** Door een enum te gebruiken kun je tussen OpenAI en Google wisselen zonder de aanroepende code aan te passen, wat direct antwoord geeft op **how to call openai** en **how to create summary** op een herbruikbare manier.
- **Error handling:** Ontbrekende API‑sleutels werpen een duidelijke uitzondering, waardoor stille fouten worden voorkomen.

## Stap 5: Alles samenvoegen in `Program.cs`

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

### Verwachte output

Het programma uitvoeren met een voorbeeld‑document:

```bash
dotnet run -- "sample/input.docx"
```

kan bijvoorbeeld opleveren:

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## Stap 6: Veelvoorkomende variaties en randgevallen

| Situatie | Aanbevolen aanpassing |
|-----------|------------------------|
| **Large documents** ( > 10 KB ) | Splits de tekst in stukken en vat elk stuk samen, combineer daarna de resultaten. |
| **Non‑English content** | Geef de taalanwijzing mee in de prompt, bv. “Summarize the following French text …”. |
| **Google provider** | Vervang de `SummarizeWithOpenAIAsync`‑aanroep door de juiste Google API‑client; behoud dezelfde enum‑interface. |
| **Custom summary length** | Wijzig het `maxSentences`‑argument bij het aanroepen van `SummarizeAsync`. |
| **Missing API key** | De `GetOpenAIApiKey`‑methode werpt al een duidelijke uitzondering; vang deze op in `Main` als je een vriendelijkere melding wilt. |

## Pro‑tips voor productiegebruik

1. **Cache de API‑sleutel** – elke keer lezen uit de omgeving voegt een verwaarloosbare overhead toe, maar je kunt deze opslaan in een static readonly‑veld als je de summarizer vaak in één proces aanroept.
2. **Rate‑limit verzoeken** – OpenAI hanteert limieten; implementeer exponentiële back‑off als je `429 Too Many Requests` krijgt.
3. **Sanitiseer invoer** – verwijder persoonlijk identificeerbare informatie voordat je tekst naar een externe AI‑service stuurt.
4. **Unit‑test de extractielogica** – mock `WordprocessingDocument` om te verifiëren dat `ExtractTextFromDocx` werkt met verschillende documentstructuren.

## Conclusie

Je weet nu **how to summarize text** in C# door veilig de API‑sleutel te lezen, OpenAI aan te roepen, en een beknopte samenvatting van een Word‑document te genereren. Hetzelfde patroon stelt je in staat om **how to call openai** met andere providers te gebruiken, **how to create summary**‑logica voor verschillende inhoudstypen te implementeren, en veilig **read api key**‑waarden uit de omgeving te halen. Experimenteer met langere documenten, andere providers, of aangepaste prompts om de samenvatting af te stemmen op jouw specifieke domein.

---

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Samenvatten van Word‑document in C# met Aspose.Words API – Complete AI‑Powered Guide](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [Hoe een PDF maken vanuit Word – Complete C# Guide](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Word‑document – Hoe inhoud verwijderen](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}