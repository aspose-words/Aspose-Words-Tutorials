---
category: general
date: 2026-11-15
description: Naučte se, jak překládat text pomocí Google v C#. Tento tutoriál ukazuje
  příklad Google Translate, práci s více jazyky a osvědčené postupy.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: cs
lastmod: 2026-11-15
og_description: Jak přeložit text pomocí Google v C# pomocí kompletního příkladu Google
  Translate. Sledujte tento tutoriál, abyste bezpečně překládali do více jazyků.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Jak přeložit text pomocí Google Translate API v C# – rychlý tutoriál
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
title: Jak přeložit text pomocí Google Translate API v C# – průvodce krok za krokem
url: /cs/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak přeložit text pomocí Google Translate API v C# – krok za krokem průvodce

Pokud potřebujete **jak přeložit text** v .NET aplikaci, Google Cloud Translation API nabízí spolehlivé, jazykově nezávislé řešení. V tomto tutoriálu uvidíte **příklad Google Translate**, který překládá jednoduchý řetězec, rozšiřuje se na **překlad více jazyků** a dodržuje osvědčené postupy pro API klíče a zpracování chyb.

Získáte připravený spustitelný C# konzolový program, jasné pochopení **překladu textu s Google**, a jistotu přizpůsobit kód pro větší projekty.

## Co tento tutoriál pokrývá

* Nastavení projektu Google Cloud a získání API klíče.  
* Instalace NuGet balíčku `Google.Cloud.Translation.V2`.  
* Psaní čistého, znovupoužitelného kódu, který **jak přeložit text** pomocí oficiálního SDK.  
* Rozšíření řešení na **překlad více jazyků** v jednom volání.  
* Běžné úskalí a tipy pro implementace produkční úrovně.

### Předpoklady

* .NET 6.0 SDK nebo novější (kód se kompiluje s .NET Core a .NET Framework).  
* Účet Google Cloud s povoleným **Cloud Translation API**.  
* Základní znalost C# a konzolových aplikací.  

---

## Krok 1: Instalace knihovny Google Cloud Translation client

Oficiální klientská knihovna abstrahuje HTTP volání a zajišťuje autentizaci za vás.

```bash
dotnet add package Google.Cloud.Translation.V2
```

Spuštěním příkazu se do vašeho projektu přidá balíček `Google.Cloud.Translation.V2`, který vám poskytne přístup ke třídě `TranslationClient` používané v celém tomto průvodci.

> **Proč je tento krok důležitý** – Použití SDK eliminuje ruční tvorbu požadavků, snižuje chyby a zajišťuje, že jste v souladu s nejnovější verzí API od Google.

## Krok 2: Vytvořte znovupoužitelný překladový pomocník

Zabalení překladové logiky do statické třídy činí kód znovupoužitelným a izoluje zpracování API klíče.

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

> **Proč vracíme slovník** – Když potřebujete **překládat do více jazyků**, organizace výsledků podle kódu jazyka usnadňuje následné zpracování.

## Krok 3: Vytvořte konzolovou aplikaci, která používá pomocníka

Níže je kompletní `Program.cs`, který demonstruje jak překlad jednoho textu, tak hromadný překlad.

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

**Očekávaný výstup v konzoli**

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

> **Proč jsou zde bloky try/catch?** – Síťové chyby, limity kvóty nebo neplatný API klíč vyvolají výjimky. Jejich elegantní zpracování zlepšuje uživatelský zážitek a udržuje aplikaci stabilní.

## Krok 4: Zabezpečte svůj API klíč

Pevné zakódování API klíče, jak je uvedeno výše, je přijatelné pro rychlou ukázku, ale ne pro produkci. Dodržujte tyto postupy:

* Uložte klíč do proměnné prostředí (`GOOGLE_API_KEY`) a načtěte jej za běhu:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Použijte **Google Application Default Credentials** místo API klíče při běhu na Google Cloud (App Engine, Cloud Run, atd.).
* Omezte klíč na Translation API v konzoli Google Cloud a omezte používání na konkrétní IP adresy nebo referrery.

## Krok 5: Rozšíření řešení pro reálné scénáře

### Detekce jazyka

Pokud potřebujete znát zdrojový jazyk, objekt odpovědi obsahuje `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Překlad velkých dokumentů

API podporuje až 30 KB na požadavek. Pro delší texty rozdělte obsah na úseky, přeložte každý úsek a poté je spojte. Zachovejte hranice vět, aby nedošlo k nepřirozenému znění.

### Omezení rychlosti a kvóty

Google vynucuje limity požadavků za minutu. Implementujte politiku opakování s exponenciálním zpětným odkladem, abyste respektovali limity kvóty a vyhnuli se chybám `429 Too Many Requests`.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Časté otázky a okrajové případy

**Q: Můžu přeložit celou HTML stránku?**  
A: Ano. Použijte parametr `Format` (`"text"` nebo `"html"`) při volání `TranslateText`. SDK to zpřístupňuje přes přetížení `TranslateText`, které přijímá `TranslateTextRequest`.

**Q: Co když jazyk není podporován?**  
A: API vrátí chybu. Ověřte kódy jazyků vůči seznamu vrácenému metodou `client.ListSupportedLanguages()` před odesláním požadavku.

**Q: Účtuje API poplatek za znak?**  
A: Google účtuje za každý přeložený znak. Odhadněte náklady pomocí stránky s cenami a zvažte cachování častých překladů.

## Závěr

Nyní víte **jak přeložit text** v C# pomocí oficiálního Google Translate API. Tutoriál pokryl **příklad Google translate**, předvedl **překlad do více jazyků** a zdůraznil produkčně připravené postupy, jako je zabezpečení API klíče a zpracování chyb. Opětovným použitím pomocníka `Translator` můžete integrovat překlad do jakékoli .NET služby, desktopové aplikace nebo mikroservisu.

**Další kroky**

- Prozkoumejte **Google Translate tutoriál** pro pokročilé funkce jako glosáře a vlastní modely.  
- Spojte tento kód s ASP.NET Core a vytvořte vícejazyčné webové API.  
- Experimentujte s hromadným překladem CSV souborů pro automatizaci lokalizačních pipeline.

Šťastné programování a užívejte si tvorbu globálně přístupných aplikací!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak uložit přeložený Word dokument v C# s Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [Přeložit řetězec do španělštiny v C# s Aspose.Words AI](/words/english/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}