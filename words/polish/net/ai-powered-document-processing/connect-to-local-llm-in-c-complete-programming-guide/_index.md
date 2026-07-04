---
category: general
date: 2026-04-28
description: Połącz się z lokalnym LLM z poziomu C# i poproś duży model językowy o
  załadowanie dokumentu Word, wywołaj lokalny LLM i automatycznie przepisz tekst.
  Dołączony kod krok po kroku.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: pl
og_description: Połącz się z lokalnym LLM z poziomu C# i zobacz, jak zadawać polecenia
  dużemu modelowi językowemu, wczytywać dokument Word, wywoływać lokalny LLM i automatycznie
  przekształcać tekst w ciągu kilku minut.
og_title: Połącz się z lokalnym LLM w C# – Kompletny przewodnik programistyczny
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: Połącz się z lokalnym LLM w C# – Kompletny przewodnik programistyczny
url: /pl/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Połącz się z lokalnym LLM w C# – Kompletny przewodnik programistyczny

Czy kiedykolwiek potrzebowałeś **połączyć się z lokalnym llm** z aplikacji .NET i zastanawiałeś się, jak sprawić, by rozmawiał z plikiem Word? Nie jesteś sam. W tym przewodniku przeprowadzimy Cię przez cały proces — połączenie z lokalnym llm, **prompt large language model**, załadowanie dokumentu Word, **call local llm**, a na końcu **rewrite text automatically**. Po zakończeniu będziesz mieć działający przykład, który przekształca dowolny akapit w formalny ton bez użycia zewnętrznych kluczy API.

## Co obejmuje ten tutorial

Zaczniemy od zainstalowania niezbędnych pakietów NuGet, a następnie uruchomimy prosty lokalny punkt końcowy LLM (np. Ollama na porcie 11434). Następnie załadujemy plik `.docx` przy użyciu Aspose.Words, wyślemy akapit do LLM, otrzymamy przepisana wersję i zapisujemy ją z powrotem do tego samego dokumentu. Zobaczysz także, jak radzić sobie z typowymi pułapkami — pustymi akapitami, asynchronicznym zwalnianiem zasobów i problemami z kodowaniem — aby kod działał w produkcji, a nie tylko w demonstracji.

### Wymagania wstępne

- .NET 6.0 SDK lub nowszy (możesz także używać .NET 8, jeśli chcesz)
- Visual Studio 2022 lub VS Code z rozszerzeniem C#
- **Aspose.Words for .NET** (bezpłatna wersja próbna działa)
- Lokalnie hostowany LLM obsługujący kontrakt `/api/generate` (np. Ollama, LMStudio)
- Podstawowa znajomość async/await w C#

> **Wskazówka:** Jeśli nie zainstalowałeś jeszcze Ollama, uruchom `ollama serve` i pobierz model za pomocą `ollama pull llama3`. Domyślny punkt końcowy HTTP będzie `http://localhost:11434/api/generate`.

---

## Krok 1: Zainstaluj wymagane pakiety

Najpierw dodaj pakiety NuGet Aspose.Words i Aspose.Words.AI do swojego projektu.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Te biblioteki zapewniają nam możliwość **load word document** oraz cienką warstwę do **call local llm** bez ręcznego tworzenia żądań HTTP.

---

## Krok 2: Połącz się z lokalnym punktem końcowym LLM

Połączenie z lokalnie hostowanym modelem jest tak proste, jak stworzenie instancji `LocalLargeLanguageModel`. Konstruktor oczekuje pełnego URL punktu końcowego generacji.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

Dlaczego opakowujemy punkt końcowy w klasie? `LocalLargeLanguageModel` zajmuje się serializacją JSON, ponawianiem prób i strumieniowaniem odpowiedzi — dzięki temu możesz skupić się na logice promptu, zamiast majstrować przy `HttpClient`.

---

## Krok 3: Załaduj źródłowy dokument Word

Następnie wczytujemy dokument do pamięci. Aspose.Words obsługuje praktycznie każdy format Word, więc `Document` sparsuje `input.docx` bez konieczności instalacji Office.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Jeśli potrzebujesz pracować ze strumieniem (np. plik przesłany przez ASP.NET), po prostu zamień ścieżkę pliku na `MemoryStream` i przekaż go do konstruktora `Document`.

---

## Krok 4: Wyodrębnij bieżący tekst akapitu

Użyjemy `DocumentBuilder` do nawigacji po dokumencie. W tym przykładzie przepisujemy **pierwszy akapit**, ale możesz iterować po `sourceDocument.GetChildNodes(NodeType.Paragraph, true)`, aby przetworzyć wiele.

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

Operator `?.` zapobiega `NullReferenceException`, jeśli dokument okaże się pusty. To jeden z tych **edge cases**, które potykają początkujących.

---

## Krok 5: Prompt the LLM to Rewrite the Paragraph

Teraz faktycznie **prompt large language model**. Prompt jest w zwykłym angielskim; wrapper wyśle go jako JSON do lokalnego punktu końcowego.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

Dlaczego formułujemy zapytanie w ten sposób? LLM najlepiej reagują na jasne, jednowątkowe instrukcje. Dodanie nowej linii po dwukropku oddziela instrukcję od treści, zmniejszając ryzyko, że model odzwierciedli sam prompt.

**Oczekiwany wynik** – Jeśli `originalParagraph` było `"Hey, what's up?"`, LLM może zwrócić:

> “Good day, how may I assist you?”

Możesz zweryfikować wynik, wypisując go:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## Krok 6: Wstaw przepisany tekst z powrotem do dokumentu

Mając nowy tekst, zastępujemy stary akapit. `DocumentBuilder.Writeln` zapisuje nową linię i przesuwa kursor do przodu, co jest idealne przy dopisywaniu. Jeśli potrzebujesz *zastąpić* dokładnie ten sam akapit, możesz użyć `docBuilder.CurrentParagraph.RemoveAllChildren()` przed zapisaniem.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Oba podejścia są pokazane, abyś mógł wybrać to, które pasuje do Twojego przepływu pracy.

---

## Krok 7: Zapisz zaktualizowany dokument

Na koniec zapisujemy zmiany do nowego pliku. Aspose.Words automatycznie wybiera format na podstawie rozszerzenia pliku.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Otwórz `output.docx` w Wordzie, a zobaczysz, że akapit jest teraz w formalnym tonie.

---

## Pełny działający przykład

Poniżej znajduje się **kompletny, samodzielny program**. Skopiuj i wklej go do projektu konsolowego, przywróć pakiety NuGet i uruchom — nie wymaga dodatkowej konfiguracji poza uruchomionym lokalnym LLM.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### Czego się spodziewać po uruchomieniu

1. Konsola wypisuje oryginalny i przepisany akapit.  
2. `output.docx` pojawia się obok `input.docx`.  
3. Otwierając plik, widzisz nowy formalny akapit wstawiony po oryginalnym (lub zastąpiony, jeśli użyłeś alternatywnego kodu).

---

## Obsługa typowych przypadków brzegowych

| Situation | Solution |
|-----------|----------|
| **Pusty lub zawierający tylko białe znaki akapit** | Sprawdź `string.IsNullOrWhiteSpace` przed wywołaniem promptu (zobacz Krok 3). |
| **LLM zwraca błąd lub pusty ciąg** | Opakuj `PromptAsync` w `try/catch` i w razie potrzeby użyj oryginalnego tekstu. |
| **Wiele akapitów wymaga przepisania** | Iteruj po `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` i zastosuj tę samą logikę promptu. |
| **Duże dokumenty powodują opóźnienia** | Grupuj akapity i wyślij je w jednym żądaniu (prompt do 4 KB na wywołanie). |
| **Znaki nie‑ASCII są zniekształcone** | Upewnij się, że punkt końcowy LLM używa UTF‑8 (większość nowoczesnych modeli tak robi). |

---

## Kolejne kroki i powiązane tematy

- **Prompt large language model** z bardziej rozbudowanymi instrukcjami (np. przewodniki stylu, limity długości).  
- Użyj **call local llm** w API webowym, aby udostępnić automatyzację dokumentów jako usługę.  
- Zbadaj **load word document** w równoległych strumieniach dla scenariuszy wysokiej przepustowości.  
- Połącz to podejście z **rewrite text automatically** dla masowej generacji e‑maili lub standaryzacji raportów.  

Jeśli chcesz zagłębić się bardziej, sprawdź dokumentację Aspose dotyczącą **document merging** oraz referencję API Ollama w celu dostosowania parametrów próbkowania.

---

## Podsumowanie

Właśnie pokazaliśmy, jak **connect to local llm** z C#, **prompt large language model**, **load word document**, **call local llm** i **rewrite text automatically** — wszystko w jednym, uruchamialnym programie konsolowym. Ten wzorzec skaluje się: zamień prompt, iteruj po akapitach lub udostępnij logikę przez endpoint ASP.NET. Najważniejsze wnioski to fakt, że lokalne modele AI mogą być ściśle zintegrowane z klasycznymi bibliotekami przetwarzania dokumentów, dając potężną automatyzację bez opuszczania zaufanego środowiska on‑prem.

Masz pytania dotyczące wątków,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}