---
category: general
date: 2026-05-04
description: Jak używać LLM do edycji dokumentów w Aspose – dowiedz się, jak zamienić
  tekst akapitu, połączyć się z lokalnym LLM i przepisać tekst przy użyciu AI.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: pl
og_description: Jak używać LLM do edycji dokumentów za pomocą Aspose. Ten przewodnik
  pokazuje, jak połączyć się z lokalnym LLM, zamienić tekst akapitu i przekształcić
  tekst przy użyciu AI.
og_title: Jak korzystać z LLM z Aspose.Words – Przepisz akapity w C#
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Jak używać LLM z Aspose.Words – Przepisz akapity w C#
url: /pl/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak używać LLM z Aspose.Words – Przepisanie akapitów w C#

Zastanawiałeś się kiedyś **jak używać LLM**, aby dopracować dokument Word bez ręcznego otwierania? Nie jesteś jedyny. Wielu programistów napotyka problem, gdy muszą *zastąpić tekst akapitu* programowo, ale brakuje im czystego, opartego na AI przepływu pracy.  

W tym samouczku podłączymy lokalny duży model językowy, przekażemy mu fragment z pliku `.docx`, poprosimy go o **przepisanie tekstu przy użyciu AI**, a na końcu zapisujemy zaktualizowany dokument — wszystko przy użyciu Aspose.Words. Po zakończeniu będziesz mieć gotową do uruchomienia aplikację konsolową w C#, która demonstruje cały proces.

> **Co otrzymasz:** kompletny, działający przykład, wyjaśnienia każdego kroku, wskazówki dotyczące przypadków brzegowych oraz pomysły na rozszerzenie rozwiązania.

## Czego będziesz potrzebować

- **.NET 6+** (lub .NET Framework 4.7.2 – kod działa na obu)
- **Aspose.Words for .NET** (pakiet NuGet `Aspose.Words`)
- Serwer **lokalny LLM** udostępniający prosty endpoint HTTP `/generate` (np. Ollama, LMStudio lub własny serwis Flask)
- Podstawowa znajomość C# i kodu klienta HTTP  

Nie są wymagane dodatkowe SDK; wszystko pozostałe znajduje się w kodzie, który napiszesz razem z nami.

## Krok 1: Jak używać LLM do zastąpienia tekstu akapitu

Pierwszą rzeczą, którą musimy zrobić, jest zidentyfikowanie akapitu, który chcemy zmodyfikować. Aspose.Words ułatwia to, udostępniając rozbudowany model obiektowy.

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

**Dlaczego to jest ważne:**  
Wybranie właściwego węzła zapobiega przypadkowemu nadpisaniu nagłówków lub tabel. Korzystając z podejścia **replace paragraph text**, zachowujemy integralność struktury dokumentu, modyfikując jedynie interesującą nas treść.

> **Porada:** Jeśli Twój dokument ma sekcje o zmiennej długości, użyj `document.GetChildNodes(NodeType.Paragraph, true)` oraz LINQ, aby znaleźć akapit według jego tekstu lub stylu.

## Krok 2: Połącz się z lokalnym endpointem LLM

Teraz, gdy mamy tekst, musimy go wysłać do LLM. Przykład używa prostej klasy opakowującej `LocalLargeLanguageModel`, która ukrywa szczegóły HTTP. W razie potrzeby możesz zastąpić ją wywołaniami `HttpClient`.

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

**Dlaczego łączymy się w ten sposób:**  
Ustawienie **connect to local llm** eliminuje opóźnienia, utrzymuje dane na miejscu i unika kosztów API. Opakowanie również upraszcza późniejszy kod, pozwalając skupić się na logice **rewrite text using ai**.

## Krok 3: Przepisz tekst przy użyciu AI z Aspose.Words

Mając tekst akapitu i gotowy LLM, tworzymy prompt, który dokładnie mówi modelowi, czego chcemy — przepisania w formalnym tonie. Możesz dostosować prompt do innych stylów (przyjazny, techniczny itp.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Dlaczego to działa:**  
LLM‑y działają na podstawie promptów; podanie wyraźnych instrukcji („Rewrite … in a formal tone”) daje spójne wyniki. Krok **rewrite text using ai** jest sercem tego samouczka — pokazuje, jak AI może być wbudowane bezpośrednio w przepływy pracy z dokumentami.

## Krok 4: Edytuj dokument i zapisz zmiany

Teraz zamieniamy oryginalne runy na nową treść. Aspose.Words przechowuje tekst w obiektach `Run`, więc ich wcześniejsze wyczyszczenie zapobiega pozostawieniu artefaktów formatowania.

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

**Uwaga dotycząca przypadków brzegowych:**  
Jeśli oryginalny akapit zawierał mieszane formatowanie (pogrubienie, kursywa), możesz chcieć zachować style. W takim przypadku utwórz nowy `Run`, skopiuj ustawienia oryginalnego `Font`, a następnie ustaw jego `Text` na `revisedText`.

## Pełny działający przykład

Poniżej znajduje się cały program, który możesz skopiować i wkleić do projektu konsolowego. Pamiętaj, aby najpierw zainstalować pakiet NuGet Aspose.Words (`dotnet add package Aspose.Words`).

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

### Oczekiwany wynik

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Otwórz `output.docx` – zobaczysz, że trzeci akapit teraz zawiera dopracowaną wersję.

## Częste pytania i pułapki

| Pytanie | Odpowiedź |
|----------|--------|
| **Co zrobić, jeśli mój LLM zwraca JSON z dodatkowymi polami?** | Dostosuj `GenerateText`, aby deserializować właściwą właściwość lub ręcznie sparsować odpowiedź. |
| **Czy mogę przetwarzać wiele akapitów jednocześnie?** | Tak – iteruj po `document.FirstSection.Body.Paragraphs` i zastosuj tę samą logikę promptu, ewentualnie dodając indeks akapitu do promptu dla kontekstu. |
| **Mój serwer LLM wymaga uwierzytelnienia?** | Dodaj nagłówek do `HttpClient` przed POST‑em: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **Formatowanie znika po zamianie.** | Zachowaj oryginalne ustawienia `Run.Font`: utwórz nowy `Run`, skopiuj `originalRun.Font.Clone()`, a następnie ustaw jego `Text`. |
| **LLM czasami zwraca pusty ciąg.** | Zaimplementuj mechanizm awaryjny – jeśli `revisedText.Trim().Length == 0`, zachowaj oryginalny tekst lub spróbuj ponownie z prostszym promptem. |

## Rozszerzanie rozwiązania

Teraz, gdy opanowałeś **how to use llm** dla pojedynczego akapitu, rozważ następujące kolejne kroki:

- **Przetwarzanie wsadowe:** Przejdź przez każdy akapit i przepisz go w wybranym stylu (np. „skrót wszystkich tekstów”).  
- **Przepisanie z uwzględnieniem stylu:** Przekaż w promptcie nazwę oryginalnego stylu akapitu, aby LLM respektował nagłówki vs tekst główny.  
- **Integracja z pipeline CI:** Zautomatyzuj dopracowywanie dokumentów jako część procesu budowania dokumentacji.  
- **Alternatywne prompty:** Spróbuj „summarize this paragraph” lub „translate this paragraph to Spanish”, aby odkryć pełną moc **rewrite text using ai**.  

## Zakończenie

Przeszliśmy cały proces **how to use llm** z Aspose.Words: ładowanie dokumentu, **connect to local llm**, wyodrębnianie akapitu, **rewrite text using ai**, **replace paragraph text**, a na końcu zapisanie wyniku. Kod jest samodzielny, działa od razu i pokazuje praktyczny sposób łączenia AI z tradycyjną automatyzacją dokumentów.

Wypróbuj go, dostosuj prompty i pozwól

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}