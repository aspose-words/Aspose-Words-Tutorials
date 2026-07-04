---
category: general
date: 2026-06-24
description: Lokalny samouczek LLM, który pokazuje, jak wywołać lokalny LLM, załadować
  dokument Word i przeprowadzić sprawdzanie gramatyki przy użyciu AI w języku C#.
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: pl
og_description: Lokalny samouczek LLM wyjaśnia krok po kroku, jak wywołać lokalny
  LLM, załadować dokument Word i przeprowadzić kontrolę gramatyki AI w C#.
og_title: Samouczek lokalnego LLM – Wywołaj lokalny LLM i przeprowadź sprawdzanie
  gramatyki
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  headline: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  type: TechArticle
- description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  name: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  steps:
  - name: How to Run
    text: 1. Open a terminal in the project folder. 2. Run `dotnet run`. 3. Watch
      the console print the corrected text.
  - name: Can I use a different LLM brand?
    text: Absolutely. As long as the server respects the OpenAI v1 API schema, just
      change `Endpoint` and pick the corresponding `AiModelType` enum value (e.g.,
      `AiModelType.Llama2`). The rest of the code stays identical.
  - name: What if my document is huge (10 MB+)?
    text: Large payloads can exceed the default request size of many servers. Split
      the document into sections and call `CheckGrammar` per section, then concatenate
      the results. This also reduces the chance of a timeout.
  - name: How do I write the corrected output back to a `.docx` file?
    text: 'The `Document` class usually provides a `Save(string path, string content)`
      method. After you get `result.CorrectedText`, call:'
  - name: Is the dummy API key a security risk?
    text: No. The key is ignored by self‑hosted endpoints, but some SDKs enforce a
      non‑null string. Using a placeholder like `"dummy"` satisfies the SDK without
      exposing any secrets.
  type: HowTo
tags:
- LLM
- C#
- GrammarCheck
- AI
title: Samouczek lokalnego LLM – Jak wywołać lokalny LLM i przeprowadzić sprawdzanie
  gramatyki
url: /pl/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Samouczek lokalnego LLM – Wywołaj lokalny LLM i przeprowadź sprawdzanie gramatyki

Zastanawiałeś się kiedyś, jak **przeprowadzić sprawdzanie gramatyki** w pliku Word bez wysyłania czegokolwiek do chmury? W tym **samouczku lokalnego LLM** podłączymy samodzielnie hostowany duży model językowy, wczytamy plik `.docx` i pozwolimy AI uporządkować tekst. Bez kluczy API, bez zewnętrznego ruchu — tylko Twój własny komputer wykonuje ciężką pracę.

Przejdziemy przez każdy wiersz kodu, wyjaśnimy, dlaczego każdy element ma znaczenie, i pokażemy, jak radzić sobie z typowymi pułapkami (takimi jak brakujące pliki czy nieosiągalny punkt końcowy). Po zakończeniu będziesz mieć gotową do uruchomienia aplikację konsolową w C#, która wykonuje **ai grammar check** przy użyciu lokalnie hostowanego modelu.

> **Co otrzymasz:** kompletny, działający program, jasne wyjaśnienie każdego kroku oraz wskazówki, jak skalować rozwiązanie na większe dokumenty lub różne dostawców LLM.

![diagram samouczka lokalnego LLM](https://example.com/local-llm-tutorial-diagram.png "Diagram ilustrujący przepływ samouczka lokalnego LLM")

## Wymagania wstępne

- .NET 6.0 SDK lub nowszy (możesz pobrać go ze strony Microsoftu)
- Lokalnie uruchomiony serwer LLM udostępniający punkt końcowy zgodny z OpenAI (np. Ollama, LM Studio lub własny wrapper FastAPI)
- Pakiet NuGet `AiGrammar` (lub dowolna biblioteka dostarczająca klasy `LocalLargeLanguageModel`, `Document` i `AiModelType`)
- Przykładowy dokument Word (`input.docx`) umieszczony w folderze, do którego odwołasz się później

To wszystko — nie są wymagane dodatkowe poświadczenia do chmury.

## Krok 1: Samouczek lokalnego LLM – Konfiguracja punktu końcowego

Pierwszą rzeczą, której potrzebujemy, jest obiekt **call local llm**, który wie, dokąd wysyłać żądania. Pomyśl o nim jak o numerze telefonu, który wybierasz, zanim rozpoczniesz rozmowę.

```csharp
using System;
using AiGrammar;   // Hypothetical library containing the LLM helpers

// Step 1: Configure a local large language model (LLM) endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",
    ApiKey = "dummy"   // Not required for self‑hosted models, but the property is mandatory
};
```

**Dlaczego to jest ważne:**  
Większość SDK LLM oczekuje punktu końcowego HTTP, który spełnia kontrakt API OpenAI. Wskazując `Endpoint` na `http://localhost:8000/v1`, informujemy bibliotekę, aby **call local llm** zamiast łączyć się z serwerami OpenAI. Dummy API key to tylko placeholder — niektóre klienty odrzucają wartość null, więc podajemy coś nieszkodliwego.

> **Pro tip:** Jeśli uruchamiasz LLM za reverse proxy, ustaw `Endpoint` na URL proxy i pozwól proxy obsłużyć zakończenie TLS. Dzięki temu Twoja aplikacja konsolowa pozostaje prosta i bezpieczna.

## Krok 2: Wczytaj dokument Word do sprawdzania gramatyki

Teraz, gdy model jest dostępny, musimy **load word document** do pamięci. Klasa `Document` abstrahuje parsowanie `.docx` za nas.

```csharp
// Step 2: Load the document you want to check
var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";
if (!System.IO.File.Exists(docPath))
{
    Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
    return;
}

var doc = new Document(docPath);
```

**Dlaczego to jest ważne:**  
Bezpośrednie podanie binarnego pliku `.docx` LLM wprowadziłoby go w błąd. Pomocnicza klasa `Document` wyodrębnia surowy tekst, zachowując podziały akapitów, co daje **ai grammar check** czyste dane wejściowe. Sprawdzenie istnienia pliku zapobiega nieprzyjemnemu `FileNotFoundException`, które w przeciwnym razie spowodowałoby awarię aplikacji.

## Krok 3: Uruchom sprawdzanie gramatyki przy użyciu LLM

Oto serce samouczka: prosimy lokalny model o korektę tekstu. Metoda `CheckGrammar` ukrywa całą obsługę HTTP i zwraca obiekt wyniku.

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**Dlaczego to jest ważne:**  
`AiModelType.Gpt4` to jedynie etykieta, która informuje zdalną usługę, którego szablonu promptu użyć. Jeśli masz mniejszy model (np. `Llama2`), zamień go odpowiednio. Biblioteka serializuje tekst dokumentu, wysyła go do `http://localhost:8000/v1/completions` i parsuje poprawiony wynik.

> **Edge case:** Jeśli LLM przekroczy limit czasu, `CheckGrammar` rzuca `TimeoutException`. Owiń wywołanie w blok `try/catch`, jeśli spodziewasz się dużych dokumentów lub obciążonego serwera.

## Krok 4: Wyświetl poprawiony tekst

Na koniec wyświetlamy wyczyszczoną wersję. W prawdziwej aplikacji możesz zapisać ją do nowego pliku `.docx`, ale w tym samouczku wystarczy wypisanie w konsoli.

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**Oczekiwany wynik** (zakładając, że oryginalny plik zawierał kilka celowych błędów):

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

Jeśli LLM nie znalazł żadnych błędów, wynik będzie identyczny z wejściem, co i tak jest użytecznym sygnałem.

## Pełny działający przykład

Łącząc wszystko razem, oto kompletny program, który możesz skopiować i wkleić do nowego projektu konsolowego:

```csharp
using System;
using AiGrammar;   // Replace with the actual namespace of your grammar library

namespace LocalLlmGrammarDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Configure the local LLM endpoint
            var llm = new LocalLargeLanguageModel
            {
                Endpoint = "http://localhost:8000/v1",
                ApiKey = "dummy"
            };

            // Path to the Word document you want to check
            var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";

            // Verify the file exists before proceeding
            if (!System.IO.File.Exists(docPath))
            {
                Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
                return;
            }

            // Load the document (this also extracts plain text)
            var doc = new Document(docPath);

            // Perform the AI grammar check using the local LLM
            GrammarCheckResult result;
            try
            {
                result = doc.CheckGrammar(llm, AiModelType.Gpt4);
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Grammar check failed: {ex.Message}");
                return;
            }

            // Show the corrected text
            Console.WriteLine("=== Corrected Text ===");
            Console.WriteLine(result.CorrectedText);
        }
    }
}
```

### Jak uruchomić

1. Otwórz terminal w folderze projektu.  
2. Uruchom `dotnet run`.  
3. Obserwuj, jak konsola wyświetla poprawiony tekst.

To cały **local llm tutorial** w mniej niż 100 linijkach kodu.

## Najczęściej zadawane pytania (FAQ)

### Czy mogę użyć innej marki LLM?

Oczywiście. Pod warunkiem, że serwer respektuje schemat API OpenAI v1, wystarczy zmienić `Endpoint` i wybrać odpowiednią wartość wyliczenia `AiModelType` (np. `AiModelType.Llama2`). Reszta kodu pozostaje identyczna.

### Co zrobić, jeśli mój dokument jest ogromny (10 MB+)?

Duże ładunki mogą przekraczać domyślny rozmiar żądania wielu serwerów. Podziel dokument na sekcje i wywołuj `CheckGrammar` dla każdej sekcji, a następnie połącz wyniki. To także zmniejsza ryzyko przekroczenia limitu czasu.

### Jak zapisać poprawiony wynik z powrotem do pliku `.docx`?

Klasa `Document` zazwyczaj udostępnia metodę `Save(string path, string content)`. Po otrzymaniu `result.CorrectedText` wywołaj:

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

Sprawdź dokumentację biblioteki, aby poznać dokładną sygnaturę.

### Czy dummy API key stanowi ryzyko bezpieczeństwa?

Nie. Klucz jest ignorowany przez samodzielnie hostowane punkty końcowe, ale niektóre SDK wymagają nie‑nullowego ciągu. Użycie placeholdera takiego jak `"dummy"` spełnia wymagania SDK bez ujawniania jakichkolwiek sekretów.

## Kolejne kroki i powiązane tematy

- **Dostrój swój lokalny LLM** pod kątem gramatyki specyficznej dla domeny (np. prawniczej lub medycznej).  
- **Uruchom zadanie wsadowe**, które przetwarza cały folder plików Word — świetne dla pipeline'ów wydawniczych.  
- Zbadaj **odpowiedzi strumieniowe**, jeśli chcesz sugestie w czasie rzeczywistym, gdy użytkownik pisze.  
- Połącz to z **bibliotekami sprawdzania pisowni** dla podwójnej warstwy kontroli jakości.

Każda z tych idei opiera się na podstawowych koncepcjach omówionych w tym **local llm tutorial**, więc napotkasz te same wzorce — **call local llm**, **load word document**, **run grammar check** i **handle results** — powtarzające się w całym materiale.

---

*Miłego kodowania! Jeśli napotkasz problem, zostaw komentarz poniżej, a pomożemy go rozwiązać.*

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne, działające przykłady kodu wraz z krok‑po‑kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Wczytaj z kodowaniem w dokumencie Word](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Wczytaj zaszyfrowany dokument Word](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [Odzyskaj uszkodzony DOCX – otwórz i wczytaj dokument Word](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}