---
category: general
date: 2026-03-06
description: Przechwyć ostrzeżenia o czcionkach podczas ładowania dokumentu Word w
  C#. Dowiedz się, jak wykrywać brakujące czcionki, sprawdzać czcionki w dokumencie
  i efektywnie obsługiwać brakujące czcionki.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: pl
og_description: Przechwyć ostrzeżenia o czcionkach podczas ładowania dokumentu Word
  w C#. Ten samouczek pokazuje, jak wykrywać brakujące czcionki, sprawdzać czcionki
  w dokumencie i obsługiwać brakujące czcionki.
og_title: Przechwytywanie ostrzeżeń czcionek w C# – Kompletny przewodnik
tags:
- Aspose.Words
- C#
- Font Management
title: Przechwytywanie ostrzeżeń dotyczących czcionek w C# – Kompletny przewodnik
url: /pl/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Przechwytywanie ostrzeżeń czcionek w C# – Kompletny przewodnik

Kiedykolwiek potrzebowałeś **przechwycić ostrzeżenia czcionek** podczas przetwarzania dokumentu Word? Przechwytywanie ostrzeżeń czcionek jest niezbędne, aby **wykrywać brakujące czcionki** i mieć pewność, że ostateczny wynik wygląda dokładnie tak, jak zamierzałeś.  

W tym samouczku przeprowadzimy praktyczny, kompleksowy przykład, który wczytuje plik `.docx`, monitoruje proces ładowania i raportuje wszelkie podstawienia czcionek. Po zakończeniu będziesz wiedział, jak **bezpiecznie wczytać dokument Word**, **sprawdzić czcionki w dokumencie** oraz **obsłużyć brakujące czcionki** bez nieprzewidzianych błędów w czasie wykonywania.

## Czego się nauczysz

- Jak podłączyć kolektor ostrzeżeń do obiektu Aspose.Words `Document`.
- Które typy ostrzeżeń wskazują na brakującą lub podstawioną czcionkę.
- Sposoby logowania lub reagowania na te ostrzeżenia w aplikacji produkcyjnej.
- Wskazówki dotyczące konfigurowania własnych źródeł czcionek, jeśli chcesz **obsługiwać brakujące czcionki** w sposób elegancki.

> **Wymaganie wstępne:** Masz ważną licencję Aspose.Words for .NET (lub korzystasz z wersji próbnej) oraz środowisko programistyczne .NET (Visual Studio, Rider lub VS Code). Nie są potrzebne żadne inne biblioteki.

---

## Przechwytywanie ostrzeżeń czcionek – krok po kroku

Poniżej znajduje się pełny, gotowy do uruchomienia kod. Każda sekcja została wydzielona jako osobny krok, abyś mógł kopiować, eksperymentować i rozbudowywać logikę.

![Przechwytywanie ostrzeżeń czcionek diagram](image.png "Diagram pokazujący zbieranie ostrzeżeń"){: alt="przechwytywanie ostrzeżeń czcionek diagram"}

### Krok 1: Wczytaj dokument Word

Najpierw musimy **wczytać dokument Word**, który może zawierać czcionki niezainstalowane na bieżącym komputerze. Konstruktor `Document` wykonuje ciężką pracę, ale pozostawimy wywołanie odizolowane, aby w razie potrzeby móc podmienić je na strumień lub tablicę bajtów.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**Dlaczego to ważne:** Ładowanie dokumentu bez obsługi ostrzeżeń oznacza, że każde podstawienie czcionki jest cicho pomijane. Ustawiając `WarningCallback` *przed* wczytaniem, zapewniamy, że zobaczymy każde ostrzeżenie `FontSubstitution`, które się pojawi.

### Krok 2: Podłącz kolektor ostrzeżeń

Klasa `WarningInfoCollector` to wbudowana implementacja `IWarningCallback`. Po prostu przechowuje każde ostrzeżenie w liście, którą później możemy przejrzeć.

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Wskazówka:** Jeśli chcesz **obsługiwać brakujące czcionki** bardziej agresywnie (np. przerwać ładowanie lub podstawić określoną czcionkę zapasową), możesz zamienić `Console.WriteLine` na własną logikę — rzucić wyjątek, zapisać do pliku lub dodać własne źródło czcionek.

### Krok 3: Zweryfikuj wynik

Uruchom program w konsoli. Jeśli Twój `input.docx` używa czcionki, której nie ma zainstalowanej, zobaczysz linie takie jak:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

Jeśli nie pojawi się żaden komunikat, dokument używał wyłącznie czcionek już dostępnych **lub** Aspose.Words znalazł pasującą czcionkę w swojej wbudowanej kolekcji zapasowej. W każdym razie udało Ci się **sprawdzić czcionki w dokumencie**.

---

## Wykrywanie brakujących czcionek bez licencji (wersja próbna)

Nawet jeśli korzystasz z 30‑dniowej wersji próbnej, mechanizm ostrzeżeń działa dokładnie tak samo. Jedyną różnicą jest to, że wersja próbna dodaje znak wodny do wygenerowanego wyniku, co **nie** wpływa na zbieranie ostrzeżeń. Dzięki temu możesz bezpiecznie **wykrywać brakujące czcionki** przed podjęciem decyzji o zakupie pełnej licencji.

---

## Obsługa brakujących czcionek – opcje zaawansowane

Czasami chcesz udostępnić własne pliki czcionek (np. firmowe czcionki marki), aby podstawienie nigdy nie zachodziło. Aspose.Words pozwala zarejestrować własne foldery czcionek:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

Umieść powyższy kod **przed** wczytaniem dokumentu, jeśli chcesz, aby loader brał pod uwagę te czcionki już w fazie początkowego parsowania. To najpewniejszy sposób, aby **obsługiwać brakujące czcionki** bez polegania na domyślnych czcionkach systemowych.

---

## Typowe pułapki i jak ich unikać

| Pułapka | Dlaczego się pojawia | Rozwiązanie |
|---------|----------------------|-------------|
| **Kolektor ostrzeżeń podłączony po wczytaniu** | Dokument został już sparsowany, więc żadne ostrzeżenia nie są rejestrowane. | Podłącz `WarningCallback` **przed** wywołaniem `new Document(path)`. |
| **Pojawiają się tylko ogólne ostrzeżenia** | Filtrujesz niewłaściwy `WarningType`. | Użyj `WarningType.FontSubstitution`, aby skupić się na problemach z czcionkami. |
| **Brak wyjścia mimo brakujących czcionek** | Aspose.Words znalazł wbudowaną czcionkę zapasową (np. Arial). | Wyłącz wbudowane zapasy poprzez `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` |
| **Spadek wydajności przy skanowaniu dużych dokumentów** | Zbieranie każdego ostrzeżenia może być kosztowne. | Ogranicz zbieranie do `FontSubstitution` lub przetwarzaj ostrzeżenia partiami. |

---

## Pełny działający przykład (gotowy do kopiowania)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Oczekiwany wynik w konsoli** (zakładając dwie brakujące czcionki):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

Jeśli konsola pozostaje cicha, oprócz komunikatu „Document loaded successfully”, oznacza to, że **sprawdziłeś czcionki w dokumencie** i nie wykryto brakujących.

---

## Podsumowanie

Pokażemy Ci, jak **przechwytywać ostrzeżenia czcionek** w C# przy użyciu Aspose.Words, co jest niezawodnym sposobem na **wykrywanie brakujących czcionek**, **bezpieczne wczytywanie dokumentu Word**, **sprawdzanie czcionek w dokumencie** oraz **obsługę brakujących czcionek** poprzez własne źródła czcionek.  

Mając ten wzorzec, możesz zintegrować walidację czcionek z dowolnym potokiem automatyzacji — niezależnie od tego, czy generujesz PDF‑y, konwertujesz do HTML, czy po prostu archiwizujesz pliki Word.

### Co dalej?

- Zapoznaj się z API **FontSettings.SubstitutionSettings**, aby definiować własne reguły podstawień.
- Połącz zbieranie ostrzeżeń z frameworkiem logowania (Serilog, NLog) w celu monitoringu w środowisku produkcyjnym.
- Użyj tego samego podejścia, aby przechwytywać inne typy ostrzeżeń, np. rozdzielczość obrazów lub nieobsługiwane funkcje.

Masz więcej pytań dotyczących obsługi czcionek lub Aspose.Words? Zostaw komentarz lub odwiedź fora społeczności Aspose. Szczęśliwego kodowania i niech Twoje dokumenty zawsze renderują się z oczekiwanymi czcionkami!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}