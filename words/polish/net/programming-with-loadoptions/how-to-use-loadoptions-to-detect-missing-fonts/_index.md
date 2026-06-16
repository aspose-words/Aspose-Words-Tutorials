---
category: general
date: 2026-06-08
description: Dowiedz się, jak używać LoadOptions w Aspose.Words, aby wykrywać brakujące
  czcionki podczas importu dokumentu. Przewodnik krok po kroku z kodem, wyjaśnieniami
  i najlepszymi praktykami.
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: pl
og_description: Jak używać LoadOptions w Aspose.Words i wykrywać brakujące czcionki
  podczas ładowania dokumentu. Kompletny przewodnik z kodem i praktycznymi wskazówkami.
og_title: Jak używać LoadOptions do wykrywania brakujących czcionek
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: Jak używać LoadOptions do wykrywania brakujących czcionek
url: /pl/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak używać LoadOptions do wykrywania brakujących czcionek

Zastanawiałeś się kiedyś **jak używać LoadOptions** przy ładowaniu dokumentu Word przy pomocy Aspose.Words? W tym tutorialu pokażemy dokładnie **jak używać LoadOptions**, aby **wykrywać brakujące czcionki** i obsługiwać je w sposób elegancki. Niezależnie od tego, czy tworzysz usługę konwersji dokumentów, czy silnik raportowania, brakujące czcionki mogą powodować niespodziewane zmiany układu, więc ich wczesne wykrycie jest niezbędne.

Przejdziemy przez każdy krok — od podłączenia callbacku ostrzeżeń po interpretację wyników — tak abyś zakończył z w pełni działającym przykładem C#, który możesz wkleić do dowolnego projektu .NET. Bez zewnętrznych dokumentów, tylko samodzielne rozwiązanie. Po zakończeniu będziesz wiedział, dlaczego istnieje system ostrzeżeń, jak go włączyć i co zrobić, gdy callback zostanie wywołany.

## Wymagania wstępne

- **Aspose.Words for .NET** (dowolna aktualna wersja; API którego używamy jest stabilne od 2022).
- Środowisko programistyczne .NET (Visual Studio, Rider lub VS Code z rozszerzeniem C#).
- Przykładowy plik Word (`input.docx`), który odwołuje się do czcionki, której *nie* masz zainstalowanej na komputerze.

To wszystko — żadnych dodatkowych pakietów NuGet poza Aspose.Words.

## Jak używać LoadOptions z Aspose.Words

Klasa **LoadOptions** jest bramą do dostosowywania sposobu odczytu dokumentu. Podłączając do niej callback ostrzeżeń, możesz **wykrywać brakujące czcionki** w momencie, gdy Aspose.Words analizuje plik. Rozbijmy to na części.

### Krok 1: Utwórz obsługę ostrzeżeń

Aspose.Words używa interfejsu `IWarningCallback`, aby powiadomić Cię o niekrytycznych problemach, takich jak podstawianie czcionek. Zaimplementuj interfejs i zdecyduj, co zrobić, gdy pojawi się ostrzeżenie.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**Dlaczego to ważne:**  
Bez callbacku Aspose.Words cicho zamienia brakujące czcionki na domyślną (zwykle Arial). Przechwytując ostrzeżenie `FontSubstitution`, możesz zalogować problem, powiadomić użytkownika lub nawet zastąpić brakującą czcionkę własnym zamiennikiem.

### Krok 2: Dołącz obsługę do LoadOptions

Teraz tworzymy instancję `LoadOptions` i wskazujemy, aby używała naszego `FontWarningHandler`. To moment, w którym **jak używać LoadOptions** naprawdę błyszczy.

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**Dlaczego to ważne:**  
`LoadOptions` to jedyne miejsce, w którym można ustawić wiele opcji importu (kodowanie, hasło itp.). Ustawiając `WarningCallback`, włączasz lekki, zdarzeniowy mechanizm, który działa dla każdego dokumentu ładowanego z tymi opcjami.

### Krok 3: Załaduj dokument używając skonfigurowanych opcji

Na koniec przekazujemy `LoadOptions` do konstruktora `Document`. Jeśli plik źródłowy odwołuje się do czcionki, która nie jest zainstalowana, Aspose.Words wywoła ostrzeżenie, a nasz handler wydrukuje komunikat.

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Co zobaczysz:**  
Zakładając, że `input.docx` używa czcionki o nazwie *„MyCustomFont”*, której nie ma na komputerze, wyjście w konsoli będzie wyglądało tak:

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

Jeśli wszystkie czcionki są dostępne, callback pozostaje cichy — brak wyjścia, brak wpływu na wydajność.

## Wykrywanie brakujących czcionek za pomocą callbacku ostrzeżeń (Drugie słowo kluczowe w akcji)

Fraza **detect missing fonts** pojawia się naturalnie w powyższym nagłówku, wzmacniając drugie słowo kluczowe. Przyjrzyjmy się kilku wariacjom, które możesz napotkać w rzeczywistych projektach.

### Wiele dokumentów w pętli

Często przetwarzasz partię plików. Ta sama instancja `LoadOptions` może być ponownie użyta, ale pamiętaj, że `WarningCallback` utrzymuje się pomiędzy ładowaniami. Jeśli potrzebujesz izolacji na poziomie dokumentu, utwórz nową `LoadOptions` dla każdej iteracji.

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### Własna logika podstawiania czcionek

Zamiast jedynie logować, możesz chcieć podstawić konkretną brakującą czcionkę alternatywą zatwierdzoną przez firmę. Rozszerz handler:

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

Teraz nie tylko **detect missing fonts**, ale także decydujesz, jak je zastąpić.

### Wyciszanie niechcianych ostrzeżeń

Jeśli zależy Ci tylko na problemach z czcionkami i chcesz zablokować wszystkie inne, filtruj po `WarningType` jak pokazano. Odwrotnie, aby logować *wszystkie* ostrzeżenia, usuń warunek `if` i wypisz `info.WarningType` razem z `info.Description`.

## Pełny, gotowy do uruchomienia przykład

Łącząc wszystko razem, oto kompletny program, który możesz skompilować i uruchomić. Zastąp `"YOUR_DIRECTORY/input.docx"` ścieżką do swojego pliku testowego.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Oczekiwany wynik w konsoli (gdy czcionka jest brakująca):**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Jeśli nie brakuje żadnych czcionek, zobaczysz po prostu:

```
Document loaded successfully.
```

## Częste pułapki i wskazówki profesjonalistów

- **Pułapka:** Zapomnienie o ustawieniu `WarningCallback`. API nadal podstawi czcionki, ale nigdy się nie dowiesz, że to się stało.  
  **Wskazówka pro:** Zawsze dołączaj handler, gdy potrzebna jest wierność czcionkom; kosztuje to praktycznie nic.

- **Pułapka:** 

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak wykrywać czcionki w Aspose.Words – obsługa ostrzeżeń i ustawień](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Jak przechwytywać czcionki w Aspose.Words – kompletny przewodnik](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [Jak ładować DOCX i wykrywać brakujące czcionki – kompletny przewodnik C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}