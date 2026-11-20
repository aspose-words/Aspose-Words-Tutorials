---
category: general
date: 2026-11-15
description: Lär dig hur du översätter text med Google i C#. Den här handledningen
  visar ett Google Translate‑exempel, hanterar flera språk och bästa praxis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: sv
lastmod: 2026-11-15
og_description: Hur man översätter text med Google i C# med ett komplett Google Translate‑exempel.
  Följ den här handledningen för att säkert översätta flera språk.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Hur man översätter text med Google Translate API i C# – snabb handledning
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
title: Hur man översätter text med Google Translate API i C# – steg‑för‑steg‑guide
url: /sv/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man översätter text med Google Translate API i C# – steg‑för‑steg guide

Om du behöver **hur man översätter text** i en .NET‑applikation, erbjuder Google Cloud Translation API en pålitlig, språk‑agnostisk lösning. I den här handledningen kommer du att se ett **Google Translate‑exempel** som översätter en enkel sträng, utökas till **översätta flera språk**, och följer bästa praxis för API‑nycklar och felhantering.

Du kommer att gå därifrån med ett färdigt C#‑konsolprogram, en klar förståelse för **översätta text med Google**, och förtroendet att anpassa koden för större projekt.

## Vad den här handledningen täcker

* Skapa ett Google Cloud‑projekt och skaffa en API‑nyckel.  
* Installera NuGet‑paketet `Google.Cloud.Translation.V2`.  
* Skriva ren, återanvändbar kod som **hur man översätter text** med den officiella SDK:n.  
* Utöka lösningen för att **översätta flera språk** i ett enda anrop.  
* Vanliga fallgropar och tips för produktionsklassade implementationer.

### Förutsättningar

* .NET 6.0 SDK eller senare (koden kompileras med .NET Core och .NET Framework).  
* Ett Google Cloud‑konto med **Cloud Translation API** aktiverat.  
* Grundläggande kunskap om C# och konsolapplikationer.  

---

## Steg 1: Installera Google Cloud Translation‑klientbiblioteket

Det officiella klientbiblioteket abstraherar HTTP‑anrop och hanterar autentisering åt dig.

```bash
dotnet add package Google.Cloud.Translation.V2
```

Att köra kommandot lägger till paketet `Google.Cloud.Translation.V2` i ditt projekt, vilket ger dig åtkomst till klassen `TranslationClient` som används genom hela guiden.

> **Varför detta steg är viktigt** – Att använda SDK:n undviker manuell begäransbyggnad, minskar buggar och säkerställer att du är i linje med Googles senaste API‑version.

## Steg 2: Skapa en återanvändbar översättningshjälpare

Att kapsla in översättningslogiken i en statisk klass gör koden återanvändbar och isolerar hanteringen av API‑nyckeln.

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

> **Varför vi returnerar en dictionary** – När du behöver **översätta flera språk**, gör organisering av resultat efter språkkod efterföljande bearbetning enkel.

## Steg 3: Bygg konsolapplikationen som använder hjälparen

Nedan är en komplett `Program.cs` som demonstrerar både en enkel‑textöversättning och en batch‑översättning.

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

**Förväntad konsolutdata**

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

> **Varför try/catch‑blocken?** – Nätverksfel, kvotgränser eller en ogiltig API‑nyckel kastar undantag. Att hantera dem på ett smidigt sätt förbättrar användarupplevelsen och håller din applikation stabil.

## Steg 4: Säkra din API‑nyckel

Att hårdkoda API‑nyckeln, som visas ovan, är acceptabelt för en snabb demo men inte för produktion. Följ dessa metoder:

* Spara nyckeln i en miljövariabel (`GOOGLE_API_KEY`) och läs den vid körning:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Använd **Google Application Default Credentials** istället för en API‑nyckel när du kör på Google Cloud (App Engine, Cloud Run, osv.).
* Begränsa nyckeln till Translation API i Google Cloud‑konsolen och begränsa användning till specifika IP‑adresser eller refererare.

## Steg 5: Utöka lösningen för verkliga scenarier

### Hantera språkdetektering

Om du behöver veta källspråket, innehåller svarobjektet `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Översätta stora dokument

API:n stöder upp till 30 KB per begäran. För längre texter, dela upp innehållet i delar, översätt varje del och sammanfoga sedan resultaten. Behåll meningsgränser intakta för att undvika besvärliga formuleringar.

### Hastighetsbegränsning och kvoter

Google upprätthåller per‑minut begäransgränser. Implementera en återförsökspolicy med exponentiell back‑off för att respektera kvotgränser och undvika `429 Too Many Requests`‑fel.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Vanliga frågor och edge‑cases

**Q: Kan jag översätta en hel HTML‑sida?**  
A: Ja. Använd `Format`‑parametern (`"text"` eller `"html"`) när du anropar `TranslateText`. SDK:n exponerar detta via `TranslateText`‑överladdningen som accepterar en `TranslateTextRequest`.

**Q: Vad händer om ett språk inte stöds?**  
A: API:n returnerar ett fel. Validera språkkoder mot listan som returneras av `client.ListSupportedLanguages()` innan du gör en begäran.

**Q: Debiterar API:n per tecken?**  
A: Google fakturerar per översatt tecken. Uppskatta kostnader med hjälp av pris‑sidan och överväg att cachea frekventa översättningar.

---

## Slutsats

Du vet nu **hur man översätter text** i C# med den officiella Google Translate‑API:n. Handledningen täckte ett **Google translate‑exempel**, demonstrerade **översätta flera språk**, och lyfte fram produktionsklara metoder såsom API‑nyckel‑säkerhet och felhantering. Genom att återanvända `Translator`‑hjälparen kan du integrera översättning i vilken .NET‑tjänst, skrivbordsapp eller mikrotjänst som helst.

**Nästa steg**

* Utforska **Google Translate‑handledningen** för avancerade funktioner som ordlistor och anpassade modeller.  
* Kombinera denna kod med ASP.NET Core för att skapa ett flerspråkigt webb‑API.  
* Experimentera med batch‑översättning av CSV‑filer för att automatisera lokalisering‑pipelines.

Lycka till med kodandet, och njut av att bygga globalt tillgängliga applikationer!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [översätt docx till franska med Aspose.Words och Google API](/words/english/net/ai-powered-document-processing/translate-docx-to-french-with-aspose-words-and-google-api/)
- [Hur man sparar översatt Word‑dokument i C# med Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}