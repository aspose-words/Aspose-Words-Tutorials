---
category: general
date: 2026-06-05
description: Skonfiguruj opcje ładowania dokumentu w C#, aby obsługiwać ostrzeżenia
  o podstawianiu czcionek i dostosować zachowanie ładowania przy użyciu funkcji zwrotnej
  ostrzeżeń.
draft: false
keywords:
- configure document load options
- warning callback
- font substitution warning
- LoadOptions usage
- Aspose.Words document loading
- C# document loading options
language: pl
og_description: Skonfiguruj opcje ładowania dokumentu w C#, aby zarządzać ostrzeżeniami
  o zamianie czcionek i precyzyjnie dostroić ładowanie dokumentu przy użyciu wywołania
  zwrotnego ostrzeżenia.
og_title: Skonfiguruj opcje ładowania dokumentu w C# – Kompletny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  headline: Configure document load options in C# – Complete Guide
  type: TechArticle
- description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  name: Configure document load options in C# – Complete Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Framework 4.6+ as well).
      - Aspose.Words for .NET installed (`dotnet add package Aspose.Words`). - Basic
      familiarity with C# syntax.'
  - name: Implement a Warning Callback for Font Substitution
    text: First things first—what’s a **warning callback**? In Aspose.Words it’s a
      delegate that gets invoked whenever the library encounters something worth flagging,
      like a missing font. By catching `WarningType.FontSubstitution` we can log the
      exact font the engine swapped out.
  - name: Set Up LoadOptions with the Callback
    text: Now that we have a callback, we need to **configure document load options**
      to actually use it. `LoadOptions` is a lightweight container that tells Aspose.Words
      how to behave during the `Document` constructor call.
  - name: Load the Document Using the Configured Options
    text: With the callback wired up, the final act is to actually **load the document**.
      The `Document` constructor accepts a file path and the `LoadOptions` we just
      prepared.
  - name: Optional – Verify Loaded Fonts (Edge Case Handling)
    text: Sometimes you might want to *pre‑validate* the document before loading it
      fully, especially in batch processing scenarios. Aspose.Words offers the `FontSettings`
      class that can enumerate required fonts.
  - name: What if the warning callback throws an exception?
    text: The callback runs on the same thread that loads the document. Throwing inside
      the delegate will abort the load and propagate the exception. Wrap your logic
      in a `try/catch` if you need resilience.
  - name: Can I suppress *all* warnings instead of handling them?
    text: Yes—set `loadOptions.WarningCallback = null;` or provide a callback that
      does nothing. Be aware you’ll lose visibility into potential problems.
  - name: Does this work with encrypted DOCX files?
    text: Absolutely. Just add `Password = "yourPassword"` to `LoadOptions` before
      creating the `Document`. The warning callback will still fire for font issues.
  - name: How does this differ from using `DocumentBuilder`?
    text: '`DocumentBuilder` is for *creating* or *modifying* a document after it’s
      loaded. **Configure document load options** influences the *initial* parsing
      stage, which is where font substitution decisions are made.'
  type: HowTo
tags:
- C#
- Aspose.Words
- LoadOptions
- DocumentProcessing
title: Skonfiguruj opcje ładowania dokumentu w C# – Kompletny przewodnik
url: /pl/net/programming-with-loadoptions/configure-document-load-options-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konfiguracja opcji ładowania dokumentu w C# – Kompletny przewodnik

Czy kiedykolwiek potrzebowałeś **konfigurować opcje ładowania dokumentu** w C#, ponieważ domyślne zachowanie ładowania po prostu nie wystarczało? Być może widzisz nieoczekiwane podstawienia czcionek lub chcesz rejestrować każde ostrzeżenie, które pojawia się podczas importu pliku. W tym samouczku przeprowadzimy Cię przez praktyczne, kompleksowe rozwiązanie, które nie tylko ustawia te opcje, ale także demonstruje **callback ostrzeżenia** dla ostrzeżeń o podstawieniu czcionki.

Omówimy wszystko, od małego fragmentu kodu tworzącego callback, po moment, w którym w końcu otwierasz dokument z własnymi ustawieniami. Po zakończeniu będziesz mieć wzorzec, który możesz wstawić do dowolnego projektu Aspose.Words, niezależnie od tego, czy przetwarzasz faktury, umowy prawne, czy proste raporty.

## Co się nauczysz

- Jak **konfigurować opcje ładowania dokumentu** przy użyciu `LoadOptions`.
- Jak zaimplementować **callback ostrzeżenia**, który przechwytuje alerty `FontSubstitution`.
- Dlaczego obsługa **ostrzeżenia o podstawieniu czcionki** we wczesnym etapie może uchronić Cię przed niespodziewanymi problemami z układem.
- Obsługa przypadków brzegowych dla brakujących czcionek i jak elegancko przejść do alternatywy.
- Pełny, gotowy do skopiowania i wklejenia przykład kodu, który możesz uruchomić już dziś.

### Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+).
- Aspose.Words for .NET zainstalowany (`dotnet add package Aspose.Words`).
- Podstawowa znajomość składni C#.

Jeśli masz to wszystko, zanurzmy się.

## Konfiguracja opcji ładowania dokumentu – krok po kroku

Poniżej znajduje się pełny przepływ pracy podzielony na cztery wyraźne kroki. Każdy krok jest wyjaśniony, a następnie podany jest zwięzły fragment kodu, który możesz wkleić bezpośrednio do Visual Studio.

### Krok 1: Implementacja callbacka ostrzeżenia dla podstawienia czcionki

Najpierw – czym jest **callback ostrzeżenia**? W Aspose.Words jest to delegat wywoływany za każdym razem, gdy biblioteka napotka coś wartego zgłoszenia, np. brakującą czcionkę. Przechwytując `WarningType.FontSubstitution`, możemy zalogować dokładnie, jaką czcionkę silnik zamienił.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Define a warning callback that reports font substitution warnings
var fontWarningCallback = new IWarningCallback(
    warningInfo =>
    {
        // Check if the warning is about font substitution
        if (warningInfo.WarningType == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or telemetry system
            Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
        }
    });
```

**Dlaczego to ważne:** Bez callbacka biblioteka cicho zastępuje brakujące czcionki, co może prowadzić do zniekształconego tekstu w końcowym PDF lub DOCX. Udostępniając ostrzeżenie, zyskujesz widoczność i możesz zdecydować, czy osadzić brakującą czcionkę, przełączyć się na alternatywę, czy powiadomić użytkownika.

> **Pro tip:** Jeśli potrzebujesz przechwycić *wszystkie* ostrzeżenia, usuń sprawdzenie `if`. Po prostu loguj `warningInfo.Description` dla każdego zdarzenia.

### Krok 2: Konfiguracja LoadOptions z callbackiem

Teraz, gdy mamy callback, musimy **konfigurować opcje ładowania dokumentu**, aby go faktycznie używać. `LoadOptions` to lekki kontener, który informuje Aspose.Words, jak zachowywać się podczas wywołania konstruktora `Document`.

```csharp
// Step 2: Attach the callback to the LoadOptions object
var loadOptions = new LoadOptions
{
    WarningCallback = fontWarningCallback,
    // Optional: enforce strict loading mode (throws on any warning)
    // LoadFormat = LoadFormat.Docx,
    // LoadOptions.LoadFormat can be left null to auto-detect based on file extension
};
```

**Dlaczego to ważne:** Przypisując `WarningCallback`, każde ostrzeżenie wygenerowane w fazie ładowania przechodzi przez nasz delegat. Możesz także dostosować inne właściwości `LoadOptions` – np. `LoadFormat`, jeśli znasz dokładny typ pliku, lub `Password` dla dokumentów zaszyfrowanych.

### Krok 3: Ładowanie dokumentu przy użyciu skonfigurowanych opcji

Z callbackiem podłączonym, ostatnim krokiem jest faktyczne **załadowanie dokumentu**. Konstruktor `Document` przyjmuje ścieżkę do pliku oraz `LoadOptions`, które właśnie przygotowaliśmy.

```csharp
// Step 3: Load the document with our custom options
string inputPath = @"C:\Docs\input.docx";   // Adjust to your environment
Document doc = new Document(inputPath, loadOptions);
```

Jeśli plik źródłowy odwołuje się do czcionki, której nie ma zainstalowanej na maszynie, zobaczysz w konsoli linię podobną do:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

Ta natychmiastowa informacja zwrotna pozwala zdecydować, czy dołączyć brakującą czcionkę do aplikacji, czy zastąpić ją programowo.

### Krok 4: Opcjonalnie – weryfikacja załadowanych czcionek (obsługa przypadków brzegowych)

Czasami możesz chcieć *wstępnie zweryfikować* dokument przed pełnym załadowaniem, szczególnie w scenariuszach przetwarzania wsadowego. Aspose.Words udostępnia klasę `FontSettings`, która może wyliczyć wymagane czcionki.

```csharp
// Optional: Check required fonts before full load
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
loadOptions.FontSettings = fontSettings;

// Re-load the document now that we have a custom font folder
Document docWithCustomFonts = new Document(inputPath, loadOptions);
```

**Kiedy to używać:** Jeśli utrzymujesz prywatne repozytorium czcionek (np. firmowe czcionki brandowe), skierowanie `FontSettings` do tego folderu zapewnia, że silnik znajdzie właściwe kroje bez przechodzenia do czcionek ogólnych.

## Pełny działający przykład

Poniżej znajduje się cały program – po prostu skopiuj, wklej i uruchom. Demonstruje wszystko, od tworzenia callbacka po ostateczne ładowanie dokumentu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // 1️⃣ Define the warning callback
        var fontWarningCallback = new IWarningCallback(
            warningInfo =>
            {
                if (warningInfo.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
                }
            });

        // 2️⃣ Configure LoadOptions with the callback
        var loadOptions = new LoadOptions
        {
            WarningCallback = fontWarningCallback,
            // Uncomment the next line to point to a custom font folder
            // FontSettings = new FontSettings { SetFontsFolder(@"C:\MyFonts", true) }
        };

        // 3️⃣ Load the document using the custom options
        string inputFile = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputFile, loadOptions);

        // 4️⃣ (Optional) Save as PDF to verify everything works
        string outputFile = @"YOUR_DIRECTORY/output.pdf";
        doc.Save(outputFile);
        Console.WriteLine($"Document loaded and saved to {outputFile}");
    }
}
```

**Oczekiwany wynik**

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Document loaded and saved to C:\Your\Path\output.pdf
```

Jeśli nie ma brakujących czcionek, callback po prostu pozostaje cichy – nie ma się czym martwić.

## Częste pytania i przypadki brzegowe

### Co się stanie, jeśli callback ostrzeżenia rzuci wyjątek?

Callback działa w tym samym wątku, w którym ładowany jest dokument. Rzucenie wyjątku wewnątrz delegata przerwie ładowanie i przekaże wyjątek dalej. Owiń swoją logikę w `try/catch`, jeśli potrzebujesz odporności.

### Czy mogę wyciszyć *wszystkie* ostrzeżenia zamiast je obsługiwać?

Tak – ustaw `loadOptions.WarningCallback = null;` lub podaj callback, który nic nie robi. Pamiętaj, że utracisz widoczność potencjalnych problemów.

### Czy to działa z zaszyfrowanymi plikami DOCX?

Oczywiście. Wystarczy dodać `Password = "yourPassword"` do `LoadOptions` przed utworzeniem `Document`. Callback ostrzeżenia nadal będzie wywoływany w przypadku problemów z czcionkami.

### Jak to się różni od użycia `DocumentBuilder`?

`DocumentBuilder` służy do *tworzenia* lub *modyfikacji* dokumentu po jego załadowaniu. **Konfiguracja opcji ładowania dokumentu** wpływa na *początkowy* etap parsowania, czyli moment, w którym podejmowane są decyzje o podstawieniu czcionek.

## Wizualny przegląd

![Diagram przedstawiający przepływ konfiguracji opcji ładowania dokumentu](https://example.com/images/load-options-flow.png "Diagram przedstawiający przepływ konfiguracji opcji ładowania dokumentu")

*Obraz ilustruje przepływ: callback → LoadOptions → konstruktor Document → obsługa ostrzeżeń.*

## Zakończenie

Teraz wiesz, jak **konfigurować opcje ładowania dokumentu** w C#, aby przechwytywać ostrzeżenia o podstawieniu czcionki, wstrzykiwać własne foldery czcionek i mieć pełną kontrolę nad procesem ładowania. Ten wzorzec daje Ci pewność, że każda brakująca czcionka zostanie zgłoszona, co pozwala utrzymać integralność dokumentu w dowolnym środowisku.

Co dalej? Spróbuj zamienić logowanie w konsoli na bardziej zaawansowany system telemetrii lub połącz to podejście z `DocumentBuilder`, aby automatycznie zastępować brakujące czcionki domyślną czcionką firmową. Możesz także zbadać inne wartości `WarningType`, takie jak `DocumentStructure`, aby uzyskać jeszcze głębszy wgląd.

Miłego kodowania i niech Twoje dokumenty zawsze renderują się dokładnie tak, jak tego oczekujesz!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne, działające przykłady kodu wraz z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Opanuj opcje ładowania Markdown w Aspose.Words w Pythonie dla zaawansowanego przetwarzania dokumentów](/words/english/python-net/document-operations/aspose-words-markdown-load-options-python/)
- [Optymalizacja ładowania dokumentów przy użyciu opcji HTML, RTF i TXT](/words/english/java/word-processing/optimizing-document-loading-options/)
- [Używanie opcji i ustawień dokumentu w Aspose.Words dla Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}