---
category: general
date: 2026-07-16
description: Vat tekst samen met AI in C#. Leer hoe je een samenvatting genereert
  vanuit Word en een Word‑document laadt in C# in slechts een paar stappen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- summarize text with ai
- generate summary from word
- load word document c#
- ai summarizer c#
- word document processing c#
- text summarization api
language: nl
lastmod: 2026-07-16
og_description: Vat tekst samen met AI in C#. Volg deze gids om een samenvatting te
  genereren uit Word‑bestanden en leer hoe je een Word‑document snel kunt laden in
  C#.
og_image_alt: Screenshot of C# code that loads a Word document and produces an AI‑generated
  summary
og_title: Tekst samenvatten met AI in C# – Stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Summarize text with AI using C#. Learn how to generate summary from
    Word and load Word document C# in just a few steps.
  headline: Summarize Text with AI in C# – Complete Programming Guide
  type: TechArticle
tags:
- C#
- AI
- Word
title: Tekst samenvatten met AI in C# – Complete programmeergids
url: /nl/net/ai-powered-document-processing/summarize-text-with-ai-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Samenvatten van Tekst met AI in C# – Complete Programmeergids

Heb je je ooit afgevraagd hoe je **tekst kunt samenvatten met AI** zonder je IDE te verlaten? Misschien heb je een stapel rapporten in *.docx* en heb je snel een executive brief nodig. Het goede nieuws: je kunt het allemaal in C# doen—laad het Word‑document, roep een AI‑samenvatter aan en print een nette samenvatting van vijf zinnen.

In deze tutorial lopen we een real‑world voorbeeld door dat laat zien hoe je **een samenvatting genereert uit Word**‑bestanden en **Word‑document C#**‑code laadt die werkt met zowel OpenAI‑ als Google‑modellen. Aan het einde heb je een zelfstandige console‑app die je in elk .NET‑project kunt plaatsen.

> **Wat je zult meenemen**  
> • Een volledig uitvoerbaar C#‑programma dat een *.docx*‑bestand leest.  
> • Een herbruikbare `Summarize`‑methode die met een AI‑service communiceert.  
> • Tips voor het omgaan met ontbrekende bestanden, modelkeuze en token‑limieten.

---

## Prerequisites — Wat je nodig hebt voordat je begint

| Requirement | Why it matters |
|-------------|----------------|
| .NET 6 of later | Moderne taalfeatures en `async`‑ondersteuning. |
| NuGet‑pakketten: `Aspose.Words` (of `DocumentFormat.OpenXml`), `System.Net.Http.Json` | `Aspose.Words` geeft ons de `Document`‑klasse die in de snippet staat; `HttpClient` handelt de API‑call af. |
| API‑sleutels voor OpenAI of Google Vertex AI | De samenvatter heeft een model‑endpoint nodig; je plaatst de sleutel in de code. |
| Een voorbeeld‑Word‑bestand (`report.docx`) in een map die je kunt refereren | De tutorial gebruikt `load word document c#` om bestands‑I/O te demonstreren. |

Als je een van deze mist, installeer ze nu—geen probleem, de stappen zijn eenvoudig.

---

## Stap 1 – Laad het Word‑document in C#  

Het eerste wat je moet doen is **Word‑document laden C#**‑stijl. Met Aspose.Words is het zo simpel als een `Document`‑instantie maken die naar het bestand op schijf wijst.

```csharp
using Aspose.Words;
using System;
using System.IO;

// Ensure the file exists before we try to open it.
string filePath = Path.Combine(Environment.CurrentDirectory, "report.docx");
if (!File.Exists(filePath))
{
    Console.Error.WriteLine($"❌ File not found: {filePath}");
    return;
}

// Step 1: Load the source document
Document doc = new Document(filePath);
Console.WriteLine("✅ Document loaded successfully.");
```

**Waarom dit belangrijk is:**  
* Het `Document`‑object abstraheert de XML achter *.docx*‑bestanden, zodat we later de inhoud als platte tekst kunnen behandelen.  
* Controleren op bestaan voorkomt een `FileNotFoundException`, een veelvoorkomende valkuil bij het **load word document c#** in productiescripts.

---

## Stap 2 – Haal platte tekst op voor samenvatting  

AI‑modellen begrijpen de interne markup van Word niet; ze hebben schone tekst nodig. Aspose geeft ons `Document.GetText()` dat het hele document als een string retourneert.

```csharp
// Extract raw text – this strips out tables, images, and formatting.
string rawText = doc.GetText();
if (string.IsNullOrWhiteSpace(rawText))
{
    Console.Error.WriteLine("⚠️ Document appears empty after extraction.");
    return;
}
Console.WriteLine($"📝 Extracted {rawText.Length:N0} characters of text.");
```

**Pro tip:** Als je koppen wilt behouden, kun je itereren over `doc.GetChildNodes(NodeType.Paragraph, true)` en alleen die met een stijl “Heading” samenvoegen. Zo respecteert je samenvatting de structuur van het document.

---

## Stap 3 – Definieer Samenvattingsopties  

Nu komen we bij het hart van de tutorial: **tekst samenvatten met AI**. We verpakken de opties in een kleine POCO zodat je het model, het maximale aantal zinnen en de temperature kunt aanpassen zonder in de HTTP‑call te duiken.

```csharp
public enum SummarizationModel
{
    OpenAI,
    Google
}

public class SummarizationOptions
{
    public int MaxSentences { get; set; } = 5;
    public SummarizationModel Model { get; set; } = SummarizationModel.OpenAI;
    public double Temperature { get; set; } = 0.7; // Controls creativity
}
```

Je kunt nu een opties‑instantie maken die de AI precies vertelt wat je wilt:

```csharp
// Step 2: Define summarization options (e.g., limit to 5 sentences, choose a model)
SummarizationOptions options = new SummarizationOptions
{
    MaxSentences = 5,
    Model = SummarizationModel.OpenAI   // switch to Google if you prefer
};
```

**Waarom we deze instellingen blootleggen:**  
* Verschillende projecten hebben verschillende beknoptheids‑eisen—sommigen hebben een twee‑zinnen TL;DR nodig, anderen een vijf‑zinnen executive brief.  
* Overschakelen tussen `OpenAI`‑ en `Google`‑modellen is zo simpel als één enum‑waarde wijzigen, ideaal voor A/B‑testing.

---

## Stap 4 – Implementeer de `Summarize`‑methode  

Hieronder vind je een **complete, uitvoerbare** implementatie die praat met ofwel OpenAI’s `chat/completions`‑endpoint of Google Vertex AI’s `text-bison`‑model. Het gebruikt `HttpClient` met `System.Net.Http.Json` voor beknoptheid.

```csharp
using System.Net.Http;
using System.Net.Http.Json;
using System.Threading.Tasks;

public static class AiSummarizer
{
    private static readonly HttpClient http = new HttpClient();

    public static async Task<string> SummarizeAsync(string text, SummarizationOptions opts)
    {
        // Choose endpoint and payload based on the selected model.
        if (opts.Model == SummarizationModel.OpenAI)
        {
            // OpenAI expects a messages array; we use a system prompt to enforce sentence limit.
            var request = new
            {
                model = "gpt-4o-mini",
                temperature = opts.Temperature,
                messages = new[]
                {
                    new { role = "system", content = $"Summarize the following text in no more than {opts.MaxSentences} sentences." },
                    new { role = "user", content = text }
                },
                max_tokens = 500
            };

            http.DefaultRequestHeaders.Authorization =
                new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", Environment.GetEnvironmentVariable("OPENAI_API_KEY"));

            var response = await http.PostAsJsonAsync("https://api.openai.com/v1/chat/completions", request);
            response.EnsureSuccessStatusCode();

            var json = await response.Content.ReadFromJsonAsync<dynamic>();
            return (string)json.choices[0].message.content;
        }
        else // Google Vertex AI
        {
            var request = new
            {
                instances = new[] { new { content = text } },
                parameters = new
                {
                    temperature = opts.Temperature,
                    maxOutputTokens = 500,
                    topK = 40,
                    topP = 0.95,
                    // Vertex AI doesn’t have a built‑in sentence limit, so we post‑process later.
                }
            };

            http.DefaultRequestHeaders.Authorization =
                new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", Environment.GetEnvironmentVariable("GOOGLE_API_KEY"));

            var response = await http.PostAsJsonAsync(
                "https://us-central1-aiplatform.googleapis.com/v1/projects/YOUR_PROJECT/locations/us-central1/publishers/google/models/text-bison-001:predict",
                request);
            response.EnsureSuccessStatusCode();

            var json = await response.Content.ReadFromJsonAsync<dynamic>();
            string raw = (string)json.predictions[0].content;
            // Simple post‑processing: keep only the first N sentences.
            return string.Join(' ', raw.Split('.').Take(opts.MaxSentences)).Trim() + ".";
        }
    }
}
```

**Uitleg van het “waarom”**  
* **Model‑agnostisch ontwerp** – Dezelfde methode werkt voor zowel OpenAI als Google, waardoor je codebase netjes blijft.  
* **Omgevingsvariabelen voor sleutels** – Het hard‑coderen van API‑geheimen is een beveiligingsrisico; `Environment.GetEnvironmentVariable` volgen best practices.  
* **Handhaving van zins‑limiet** – OpenAI kan direct in de system‑prompt een limiet krijgen; Google heeft een snelle post‑process nodig omdat de API geen zins‑cap ondersteunt.

---

## Stap 5 – Koppel alles samen en geef de samenvatting weer  

Nu combineren we de onderdelen: lees het document, geef de tekst door aan `SummarizeAsync`, en print het resultaat.

```csharp
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // Load the document (Step 1)
        string filePath = Path.Combine(Environment.CurrentDirectory, "report.docx");
        if (!File.Exists(filePath))
        {
            Console.Error.WriteLine($"❌ Cannot find {filePath}");
            return;
        }
        Document doc = new Document(filePath);

        // Extract raw text (Step 2)
        string rawText = doc.GetText();

        // Define options (Step 3)
        SummarizationOptions options = new SummarizationOptions
        {
            MaxSentences = 5,
            Model = SummarizationModel.OpenAI   // Change to Google if you prefer
        };

        // Generate the summary (Step 4)
        string summary = await AiSummarizer.SummarizeAsync(rawText, options);

        // Step 5: Output the generated summary
        Console.WriteLine("\n=== AI‑Generated Summary ===\n");
        Console.WriteLine(summary);
    }
}
```

### Verwachte Output

Als `report.docx` een 2‑pagina zakelijke analyse bevat, kan de console bijvoorbeeld tonen:

```
=== AI‑Generated Summary ===

The quarterly sales increased by 12% YoY, driven primarily by the new product line. Customer churn fell to 3%, the lowest in five years. Marketing spend rose 8% but delivered a 15% lift in brand awareness. Operational efficiencies saved $1.2M, mainly through supply‑chain automation. The outlook for Q3 remains positive, with projected growth of 10‑15%.
```

Als je `options.Model` wijzigt naar `SummarizationModel.Google`, zie je een soortgelijke beknopte alinea—maar met een andere formulatiestijl.

---

## Edge Cases & Veelvoorkomende Valkuilen  

| Situation | What to Watch For | Quick Fix |
|-----------|-------------------|-----------|
| **Enorme documenten (>10 k tokens)** | API kan het verzoek afwijzen of output afkappen. | Splits de tekst in logische secties (bijv. per heading) en vat elk deel apart samen, combineer daarna. |
| **Ontbrekende of ongeldige API‑sleutel** | 401 Unauthorized‑fouten. | Controleer of `OPENAI_API_KEY` / `GOOGLE_API_KEY` zijn ingesteld in je omgeving of gebruik een `appsettings.json`‑bestand voor lokale ontwikkeling. |
| **Niet‑Engelse Word‑bestanden** | Summar

## Wat je hierna moet leren


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑features onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Word Document - Find And Replace Text](/words/english/net/find-and-replace-text/)
- [Ranges Get Text In Word Document](/words/english/net/programming-with-ranges/ranges-get-text/)
- [Copy Bookmarked Text In Word Document](/words/english/net/programming-with-bookmarks/copy-bookmarked-text/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}