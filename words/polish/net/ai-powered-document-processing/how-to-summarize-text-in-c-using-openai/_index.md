---
category: general
date: 2026-09-11
description: Dowiedz się, jak podsumować tekst w C#, odczytując klucz API, wywołując
  OpenAI i generując zwięzłe podsumowanie dokumentu Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: pl
lastmod: 2026-09-11
og_description: Jak podsumować tekst w C#? Ten tutorial pokazuje, jak odczytać klucz
  API, wywołać OpenAI i stworzyć podsumowanie dokumentu Word.
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: Jak podsumować tekst w C# przy użyciu OpenAI – przewodnik krok po kroku
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
title: Jak podsumować tekst w C# przy użyciu OpenAI
url: /pl/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak podsumować tekst w C# przy użyciu OpenAI

Jeśli potrzebujesz **jak podsumować tekst** w pliku .docx, ten przewodnik pokaże Ci kompletną, gotową do uruchomienia rozwiązanie. Nauczysz się, jak odczytać klucz API ze swojego środowiska, jak wywołać OpenAI (lub Google) z C#, oraz jak stworzyć zwięzłe podsumowanie dokumentu Word.

Podsumowywanie dokumentu Word jest częstym wymaganiem przy generowaniu raportów, podsumowaniach e‑mailowych lub ekstrakcji bazy wiedzy. Po zakończeniu tego samouczka będziesz mieć program wiersza poleceń, który wypisze pięciozdaniowe podsumowanie dowolnego pliku `.docx`, który dostarczysz.

## Prerequisites

- .NET 6.0 SDK lub nowszy (pobierz z [dotnet.microsoft.com](https://dotnet.microsoft.com/download))
- Ważny klucz OpenAI API przechowywany w zmiennej środowiskowej o nazwie `OPENAI_API_KEY` (zobaczysz **odczytać klucz API** w działaniu)
- pakiet NuGet `DocumentFormat.OpenXml` do odczytywania plików `.docx`
- pakiet NuGet `OpenAI` (lub `Google.AI`, jeśli wolisz dostawcę Google)

## Krok 1: Skonfiguruj projekt i zainstaluj zależności

Utwórz nowy projekt konsolowy i dodaj wymagane pakiety:

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

**Wskazówka:** Utrzymuj plik `csproj` w porządku, grupując powiązane pakiety w `<ItemGroup>`, jeśli później dodasz więcej zależności.

## Krok 2: Bezpieczne odczytywanie klucza API

Hard‑kodowanie sekretów jest niebezpieczne. Samouczek demonstruje właściwy sposób **odczytania klucza API** ze zmiennych środowiskowych.

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

## Krok 3: Załaduj dokument Word, który chcesz podsumować

Poniższy kod pokazuje **jak podsumować dokument Word** poprzez wyodrębnienie zwykłego tekstu ze struktury OpenXML.

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

## Krok 4: Zbuduj wielokrotnego użytku klasę podsumowującą

Ta klasa kapsułkuje **jak wywołać openai** (lub Google) i implementuje logikę **jak utworzyć podsumowanie**. Pozwala również przełączać dostawców przy użyciu jednej wartości wyliczeniowej.

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

### Dlaczego ta struktura ma znaczenie

- **Rozdzielenie odpowiedzialności:** Ładowanie dokumentu, odczytywanie klucza API i wywoływanie usługi AI są izolowane w osobnych metodach. Dzięki temu kod jest łatwiejszy do testowania i rozbudowy.
- **Elastyczność dostawcy:** Dzięki użyciu wyliczenia możesz przełączać się między OpenAI a Google bez modyfikacji kodu wywołującego, co bezpośrednio odpowiada na **jak wywołać openai** i **jak utworzyć podsumowanie** w sposób wielokrotnego użytku.
- **Obsługa błędów:** Brakujące klucze API generują wyraźny wyjątek, zapobiegając cichym awariom.

## Krok 5: Połącz wszystko w `Program.cs`

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

### Oczekiwany wynik

Uruchomienie programu z przykładowym dokumentem:

```bash
dotnet run -- "sample/input.docx"
```

może wygenerować:

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## Krok 6: Typowe wariacje i przypadki brzegowe

| Sytuacja | Zalecana modyfikacja |
|-----------|------------------------|
| **Duże dokumenty** ( > 10 KB ) | Podziel tekst na fragmenty i podsumuj każdy fragment, a następnie połącz wyniki. |
| **Treść nie‑angielska** | Przekaż wskazówkę językową w zapytaniu, np. „Podsumuj następujący francuski tekst …”. |
| **Dostawca Google** | Zastąp wywołanie `SummarizeWithOpenAIAsync` odpowiednim klientem API Google; zachowaj tę samą interfejs wyliczeniowy. |
| **Niestandardowa długość podsumowania** | Zmień argument `maxSentences` przy wywoływaniu `SummarizeAsync`. |
| **Brak klucza API** | Metoda `GetOpenAIApiKey` już rzuca wyraźny wyjątek; przechwyć go w `Main`, jeśli chcesz bardziej przyjazny komunikat. |

## Wskazówki produkcyjne

1. **Cache'uj klucz API** – odczytywanie go ze środowiska przy każdym wywołaniu dodaje znikomy narzut, ale możesz przechowywać go w statycznym polu readonly, jeśli wywołujesz podsumowywacz wiele razy w jednym procesie.
2. **Ogranicz częstotliwość żądań** – OpenAI wymusza limity żądań; zaimplementuj wykładniczy back‑off, jeśli napotkasz `429 Too Many Requests`.
3. **Sanityzuj dane wejściowe** – usuń informacje osobiste przed wysłaniem tekstu do zewnętrznej usługi AI.
4. **Testuj jednostkowo logikę ekstrakcji** – mockuj `WordprocessingDocument`, aby zweryfikować, że `ExtractTextFromDocx` działa z różnymi strukturami dokumentu.

## Zakończenie

Teraz wiesz, **jak podsumować tekst** w C# poprzez bezpieczne odczytywanie klucza API, wywoływanie OpenAI i generowanie zwięzłego podsumowania dokumentu Word. Ten sam wzorzec pozwala Ci **jak wywołać openai** z innymi dostawcami, **jak utworzyć podsumowanie** dla różnych typów treści oraz bezpiecznie **odczytać klucz API** ze środowiska. Eksperymentuj z dłuższymi dokumentami, różnymi dostawcami lub własnymi zapytaniami, aby dostosować podsumowanie do swojej konkretnej dziedziny.

---

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Podsumuj dokument Word w C# z API Aspose.Words – Kompletny przewodnik AI](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [jak stworzyć pdf z Word – Kompletny przewodnik C#](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Dokument Word – Jak usunąć zawartość](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}