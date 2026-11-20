---
category: general
date: 2026-11-15
description: Leer hoe je tekst vertaalt met Google in C#. Deze tutorial toont een
  Google Translate-voorbeeld, behandelt meerdere talen en best practices.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: nl
lastmod: 2026-11-15
og_description: Hoe tekst te vertalen met Google in C# met een volledig Google Translate-voorbeeld.
  Volg deze tutorial om meerdere talen veilig te vertalen.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Hoe tekst te vertalen met de Google Translate API in C# – snelle tutorial
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
title: Hoe tekst vertalen met de Google Translate API in C# – stapsgewijze handleiding
url: /nl/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe tekst te vertalen met de Google Translate API in C# – stapsgewijze gids

Als je **tekst wilt vertalen** in een .NET‑applicatie, biedt de Google Cloud Translation API een betrouwbare, taal‑agnostische oplossing. In deze tutorial zie je een **Google Translate‑voorbeeld** dat een eenvoudige string vertaalt, uitbreidt naar **meerdere talen vertalen**, en de beste praktijken voor API‑sleutels en foutafhandeling volgt.

Je eindigt met een kant‑en‑klaar C# console‑programma, een duidelijk begrip van **tekst vertalen met Google**, en het vertrouwen om de code aan te passen voor grotere projecten.

## Wat deze tutorial behandelt

* Een Google Cloud‑project opzetten en een API‑sleutel verkrijgen.  
* De `Google.Cloud.Translation.V2` NuGet‑package installeren.  
* Schone, herbruikbare code schrijven die **tekst vertaalt** met de officiële SDK.  
* De oplossing uitbreiden om **meerdere talen te vertalen** in één oproep.  
* Veelvoorkomende valkuilen en tips voor productie‑klare implementaties.

### Vereisten

* .NET 6.0 SDK of later (de code compileert met .NET Core en .NET Framework).  
* Een Google Cloud‑account met de **Cloud Translation API** ingeschakeld.  
* Basiskennis van C# en console‑applicaties.  

---

## Stap 1: Installeer de Google Cloud Translation client‑bibliotheek

De officiële client‑bibliotheek abstraheert HTTP‑aanroepen en behandelt authenticatie voor je.

```bash
dotnet add package Google.Cloud.Translation.V2
```

Het uitvoeren van het commando voegt de `Google.Cloud.Translation.V2`‑package toe aan je project, waardoor je toegang krijgt tot de `TranslationClient`‑klasse die door de hele gids wordt gebruikt.

> **Waarom deze stap belangrijk is** – Het gebruik van de SDK voorkomt handmatige request‑constructie, vermindert bugs, en zorgt ervoor dat je up‑to‑date bent met de nieuwste API‑versie van Google.

## Stap 2: Maak een herbruikbare vertaal‑helper

Het encapsuleren van de vertaallogica in een statische klasse maakt de code herbruikbaar en isoleert de verwerking van de API‑sleutel.

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

> **Waarom we een dictionary retourneren** – Wanneer je **meerdere talen wilt vertalen**, maakt het organiseren van resultaten per taalcodes de verdere verwerking eenvoudig.

## Stap 3: Bouw de console‑applicatie die de helper gebruikt

Hieronder staat een volledige `Program.cs` die zowel een enkele‑tekstvertaling als een batch‑vertaling demonstreert.

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

**Verwachte console‑output**

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

> **Waarom de try/catch‑blokken?** – Netwerkfouten, quota‑limieten of een ongeldige API‑sleutel veroorzaken uitzonderingen. Deze op een nette manier afhandelen verbetert de gebruikerservaring en houdt je applicatie stabiel.

## Stap 4: Beveilig je API‑sleutel

Hard‑coderen van de API‑sleutel, zoals hierboven getoond, is acceptabel voor een snelle demo maar niet voor productie. Volg deze praktijken:

* Sla de sleutel op in een omgevingsvariabele (`GOOGLE_API_KEY`) en lees deze tijdens runtime:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Gebruik **Google Application Default Credentials** in plaats van een API‑sleutel wanneer je draait op Google Cloud (App Engine, Cloud Run, enz.).
* Beperk de sleutel tot de Translation API in de Google Cloud‑console en beperk het gebruik tot specifieke IP‑adressen of referrers.

## Stap 5: Breid de oplossing uit voor real‑world scenario's

### Taaldetectie afhandelen

Als je de brontaal moet weten, bevat het responsobject `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Grote documenten vertalen

De API ondersteunt tot 30 KB per request. Voor grotere teksten, splits de inhoud in stukken, vertaal elk stuk, en concateneer vervolgens de resultaten. Houd zinsgrenzen intact om ongemakkelijke formuleringen te vermijden.

### Rate‑limiting en quota's

Google handhaaft per‑minuut request‑limieten. Implementeer een retry‑beleid met exponentiële back‑off om quota‑limieten te respecteren en `429 Too Many Requests`‑fouten te vermijden.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Veelgestelde vragen en randgevallen

**Q: Kan ik een volledige HTML‑pagina vertalen?**  
A: Ja. Gebruik de `Format`‑parameter (`"text"` of `"html"`) bij het aanroepen van `TranslateText`. De SDK maakt dit beschikbaar via de `TranslateText`‑overload die een `TranslateTextRequest` accepteert.

**Q: Wat als een taal niet wordt ondersteund?**  
A: De API retourneert een fout. Valideer taalcodes tegen de lijst die wordt geretourneerd door `client.ListSupportedLanguages()` voordat je een request maakt.

**Q: Rekent de API per teken?**  
A: Google rekent per vertaald teken. Schat de kosten met behulp van de prijspagina en overweeg het cachen van veelvoorkomende vertalingen.

## Conclusie

Je weet nu **hoe je tekst kunt vertalen** in C# met de officiële Google Translate API. De tutorial behandelde een **Google Translate‑voorbeeld**, demonstreerde **meerdere talen vertalen**, en belichtte productie‑klare praktijken zoals API‑sleutelbeveiliging en foutafhandeling. Door de `Translator`‑helper opnieuw te gebruiken, kun je vertaling integreren in elke .NET‑service, desktop‑applicatie of microservice.

**Volgende stappen**

- Verken de **Google Translate‑tutorial** voor geavanceerde functies zoals glossaria en aangepaste modellen.  
- Combineer deze code met ASP.NET Core om een meertalige web‑API te maken.  
- Experimenteer met batch‑vertaling van CSV‑bestanden om lokalisatie‑pijplijnen te automatiseren.

Veel plezier met coderen, en geniet van het bouwen van wereldwijd toegankelijke applicaties!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [docx naar Frans vertalen met Aspose.Words en Google API](/words/english/net/ai-powered-document-processing/translate-docx-to-french-with-aspose-words-and-google-api/)
- [Hoe een vertaald Word‑document op te slaan in C# met Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}