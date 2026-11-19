---
category: general
date: 2026-11-15
description: Naucz się tłumaczyć tekst przy użyciu Google w C#. Ten tutorial prezentuje
  przykład Google Translate, obsługę wielu języków oraz najlepsze praktyki.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: pl
lastmod: 2026-11-15
og_description: Jak tłumaczyć tekst przy użyciu Google w C# korzystając z pełnego
  przykładu Google Translate. Postępuj zgodnie z tym samouczkiem, aby bezpiecznie
  tłumaczyć wiele języków.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Jak tłumaczyć tekst przy użyciu Google Translate API w C# – szybki samouczek
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
title: Jak tłumaczyć tekst przy użyciu Google Translate API w C# – przewodnik krok
  po kroku
url: /pl/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak tłumaczyć tekst przy użyciu Google Translate API w C# – przewodnik krok po kroku

Jeśli potrzebujesz **jak tłumaczyć tekst** w aplikacji .NET, Google Cloud Translation API oferuje niezawodne, językowo‑agnostyczne rozwiązanie. W tym samouczku zobaczysz **przykład Google Translate**, który tłumaczy prosty ciąg znaków, rozszerza się do **tłumaczenia wielu języków**, oraz stosuje najlepsze praktyki dotyczące kluczy API i obsługi błędów.

Uzyskasz gotowy do uruchomienia program konsolowy w C#, jasne zrozumienie **tłumaczenia tekstu przy użyciu Google**, oraz pewność, że możesz dostosować kod do większych projektów.

## Co obejmuje ten samouczek

* Konfigurowanie projektu Google Cloud i uzyskanie klucza API.  
* Instalowanie pakietu NuGet `Google.Cloud.Translation.V2`.  
* Pisanie czystego, wielokrotnego użytku kodu, który **jak tłumaczyć tekst** przy użyciu oficjalnego SDK.  
* Rozszerzanie rozwiązania o **tłumaczenie wielu języków** w jednym wywołaniu.  
* Typowe pułapki i wskazówki dla implementacji w wersji produkcyjnej.

### Wymagania wstępne

* .NET 6.0 SDK lub nowszy (kod kompiluje się z .NET Core i .NET Framework).  
* Konto Google Cloud z włączonym **Cloud Translation API**.  
* Podstawowa znajomość C# i aplikacji konsolowych.  

---

## Krok 1: Zainstaluj bibliotekę kliencką Google Cloud Translation

Oficjalna biblioteka kliencka abstrahuje wywołania HTTP i obsługuje uwierzytelnianie za Ciebie.

```bash
dotnet add package Google.Cloud.Translation.V2
```

Uruchomienie polecenia dodaje pakiet `Google.Cloud.Translation.V2` do Twojego projektu, dając dostęp do klasy `TranslationClient` używanej w całym przewodniku.

> **Dlaczego ten krok ma znaczenie** – Korzystanie z SDK eliminuje ręczne budowanie żądań, zmniejsza liczbę błędów i zapewnia zgodność z najnowszą wersją API Google.

## Krok 2: Utwórz wielokrotnego użytku pomocnika tłumaczeń

Ujęcie logiki tłumaczenia w statycznej klasie sprawia, że kod jest wielokrotnego użytku i izoluje obsługę klucza API.

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

> **Dlaczego zwracamy słownik** – Gdy potrzebujesz **tłumaczyć wiele języków**, organizowanie wyników według kodu języka upraszcza dalsze przetwarzanie.

## Krok 3: Zbuduj aplikację konsolową wykorzystującą pomocnika

Poniżej znajduje się kompletny plik `Program.cs`, który demonstruje zarówno tłumaczenie pojedynczego tekstu, jak i tłumaczenie wsadowe.

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

**Oczekiwany wynik w konsoli**

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

> **Dlaczego bloki try/catch?** – Błędy sieciowe, limity kwot, lub nieprawidłowy klucz API generują wyjątki. Ich elegancka obsługa poprawia doświadczenie użytkownika i utrzymuje stabilność aplikacji.

## Krok 4: Zabezpiecz swój klucz API

Wstawianie klucza API na stałe w kodzie, jak pokazano powyżej, jest dopuszczalne w szybkim demo, ale nie w produkcji. Stosuj następujące praktyki:

* Przechowuj klucz w zmiennej środowiskowej (`GOOGLE_API_KEY`) i odczytuj go w czasie wykonywania:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Używaj **Google Application Default Credentials** zamiast klucza API podczas uruchamiania w Google Cloud (App Engine, Cloud Run itp.).
* Ogranicz klucz do Translation API w konsoli Google Cloud i ogranicz użycie do konkretnych adresów IP lub odsyłaczy.

## Krok 5: Rozszerz rozwiązanie na scenariusze rzeczywiste

### Obsługa wykrywania języka

Jeśli potrzebujesz znać język źródłowy, obiekt odpowiedzi zawiera `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Tłumaczenie dużych dokumentów

API obsługuje do 30 KB na żądanie. Dla większych tekstów podziel zawartość na fragmenty, przetłumacz każdy fragment, a następnie połącz wyniki. Zachowaj granice zdań, aby uniknąć niezgrabnych sformułowań.

### Ograniczanie szybkości i limity kwot

Google wymusza limity żądań na minutę. Zaimplementuj politykę ponownych prób z wykładniczym opóźnieniem, aby respektować limity kwot i unikać błędów `429 Too Many Requests`.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Częste pytania i przypadki brzegowe

**Q: Czy mogę przetłumaczyć całą stronę HTML?**  
A: Tak. Użyj parametru `Format` (`"text"` lub `"html"`) przy wywoływaniu `TranslateText`. SDK udostępnia to poprzez przeciążenie `TranslateText`, które przyjmuje `TranslateTextRequest`.

**Q: Co zrobić, jeśli język nie jest obsługiwany?**  
A: API zwraca błąd. Zweryfikuj kody języków względem listy zwróconej przez `client.ListSupportedLanguages()` przed wykonaniem żądania.

**Q: Czy API nalicza opłatę za znak?**  
A: Google rozlicza się za przetłumaczony znak. Oszacuj koszty korzystając ze strony cenowej i rozważ buforowanie częstych tłumaczeń.

---

## Podsumowanie

Teraz wiesz **jak tłumaczyć tekst** w C# przy użyciu oficjalnego Google Translate API. Samouczek przedstawił **przykład Google translate**, zademonstrował **tłumaczenie wielu języków** oraz podkreślił praktyki gotowe do produkcji, takie jak bezpieczeństwo klucza API i obsługa błędów. Dzięki ponownemu użyciu pomocnika `Translator` możesz zintegrować tłumaczenia z dowolną usługą .NET, aplikacją desktopową lub mikrousługą.

**Kolejne kroki**

* Przeglądaj **samouczek Google Translate** w celu poznania zaawansowanych funkcji, takich jak glosariusze i modele niestandardowe.  
* Połącz ten kod z ASP.NET Core, aby stworzyć wielojęzyczne API webowe.  
* Eksperymentuj z tłumaczeniem wsadowym plików CSV, aby zautomatyzować procesy lokalizacji.

Miłego kodowania i ciesz się tworzeniem aplikacji dostępnych na całym świecie!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak zapisać przetłumaczony dokument Word w C# przy użyciu Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}