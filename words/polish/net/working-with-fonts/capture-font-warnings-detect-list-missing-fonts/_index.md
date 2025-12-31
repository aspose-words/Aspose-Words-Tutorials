---
category: general
date: 2025-12-31
description: Przechwytuj ostrzeżenia o czcionkach w Aspose.Words, aby wykrywać brakujące
  czcionki i wyświetlać ich listę w aplikacji .NET. Poznaj krok po kroku rozwiązanie
  w C#.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: pl
og_description: Przechwytywanie ostrzeżeń o czcionkach w Aspose.Words w celu wykrycia
  brakujących czcionek i ich listy. Kompletny przewodnik C# z kodem i wskazówkami.
og_title: Zbieraj ostrzeżenia o czcionkach – wykryj i wymień brakujące czcionki
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Zbieraj ostrzeżenia o czcionkach – wykrywaj i wymieniaj brakujące czcionki
url: /pl/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Przechwytywanie ostrzeżeń o czcionkach – wykrywanie i listowanie brakujących czcionek

Kiedykolwiek potrzebowałeś **przechwycić ostrzeżenia o czcionkach** podczas ładowania dokumentu Word, ale nie wiedziałeś, jak wyświetlić szczegóły brakujących czcionek? Nie jesteś sam. W wielu rzeczywistych projektach brakujące czcionki powodują problemy z układem, a bez odpowiednich ostrzeżeń musisz ścigać się z nieistniejącymi błędami.  

W tym samouczku pokażemy, jak **wykrywać brakujące czcionki** i **listować brakujące czcionki** przy użyciu Aspose.Words dla .NET. Po zakończeniu będziesz mieć gotowy do uruchomienia fragment C#, który wypisuje każde ostrzeżenie o zamianie, dzięki czemu możesz logować, alarmować lub nawet automatycznie zastępować czcionki.

---

## Dlaczego przechwytywanie ostrzeżeń o czcionkach ma znaczenie

Gdy Aspose.Words otwiera plik DOCX, który odwołuje się do czcionki niezainstalowanej na serwerze, cicho podmienia ją na domyślną. Dokument wygląda w porządku, ale wierność wizualna jest naruszona — pomyśl o logo firmowym wyświetlonym w niewłaściwej czcionce.  

Przechwytywanie tych ostrzeżeń pozwala Ci:

* **Utrzymać spójność marki** – dokładnie wiesz, które czcionki są brakujące.  
* **Zautomatyzować naprawę** – programowo zastępować brakujące czcionki.  
* **Audytować zgodność** – generować raporty na potrzeby przeglądów prawnych lub projektowych.  

Krótko mówiąc, **przechwytywanie ostrzeżeń o czcionkach** to pierwsza linia obrony przed cichą zamianą czcionek.

---

## Konfiguracja LoadOptions w celu wykrycia brakujących czcionek

Kluczem do wyświetlania ostrzeżeń jest właściwość `LoadOptions.FontSubstitutionWarning`. Domyślnie jest ustawiona na `None`, co oznacza, że Aspose.Words połyka komunikaty. Przełączenie jej na `All` powoduje, że biblioteka zapisuje każde zdarzenie zamiany.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Wskazówka:** Jeśli masz własny folder z czcionkami, przypisz go metodą `FontSettings.SetFontsFolder("path")` przed załadowaniem dokumentu. Dzięki temu będziesz **wykrywać brakujące czcionki**, które nie znajdują się w katalogu systemowym.

---

## Załaduj dokument i wypisz brakujące czcionki

Gdy `LoadOptions` są gotowe, następnym krokiem jest załadowanie pliku Word. Konstruktor przyjmuje obiekt opcji, a każda zamiana zostanie zapisana w kolekcji `WarningInfoCollection` dokumentu.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Jeśli plik odwołuje się do czcionek, które nie są dostępne, każda brakująca czcionka generuje wpis `WarningInfo`. Możesz **listować brakujące czcionki**, iterując po tej kolekcji.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

Typowy wynik wygląda tak:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Każda linia informuje dokładnie której czcionki brakowało, spełniając wymaganie **listowania brakujących czcionek**.

---

## Odczyt i interpretacja WarningInfoCollection

`WarningInfoCollection` może zawierać różne typy ostrzeżeń (np. `DocumentStructure`, `ImageLoading`). Aby skupić się wyłącznie na problemach z czcionkami, przefiltruj po `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

Dlaczego filtrujemy? Ponieważ duży dokument może także generować ostrzeżenia o uszkodzonych obrazach lub nieobsługiwanych funkcjach. Ograniczając kolekcję, eliminujesz szum i utrzymujesz czysty wynik **przechwytywania ostrzeżeń o czcionkach**.

---

## Pełny działający przykład – przechwytywanie ostrzeżeń o czcionkach w praktyce

Poniżej kompletny, samodzielny program, który możesz wkleić do dowolnego projektu konsolowego .NET. Demonstracja obejmuje każdy krok od konfiguracji `LoadOptions` po wypisanie przejrzystej listy brakujących czcionek.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Oczekiwany wynik w konsoli**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Jeśli dokument nie zawiera brakujących czcionek, zobaczysz:

```
All referenced fonts are available – no warnings captured.
```

---

## Typowe przypadki brzegowe i jak sobie z nimi radzić

| Sytuacja | Dlaczego się pojawia | Zalecane rozwiązanie |
|-----------|----------------------|----------------------|
| **Dokument używa osadzonej czcionki OpenType** | Aspose.Words może odczytać osadzone czcionki, ale tylko jeśli plik nie jest uszkodzony. | Najpierw sprawdź DOCX w programie Word; w razie potrzeby ponownie osadź czcionkę. |
| **Duża liczba ostrzeżeń** (np. 200+ brakujących czcionek) | Importy masowe z systemów legacy często odwołują się do szerokiej palety czcionek. | Przetwarzaj ostrzeżenia partiami: zapisz je w bazie danych, a potem uruchom skrypt instalacji czcionek. |
| **WarningInfoCollection jest pusta** | Albo dokument ma wszystkie czcionki, albo `FontSubstitutionWarning` pozostało ustawione na `None`. | Sprawdź konfigurację `LoadOptions` i upewnij się, że ładowany jest właściwy plik. |
| **Własne czcionki znajdują się na udziale sieciowym** | Opóźnienia sieciowe mogą powodować timeouty podczas wyszukiwania czcionek. | Wstępnie załaduj czcionki do `FontSettings` przy pomocy `SetFontsFolder` i ustaw `CacheFontData = true`. |

Te wskazówki pomogą Ci **wykrywać brakujące czcionki** niezawodnie, nawet w złożonych środowiskach.

---

## Ilustracja

![przykład przechwytywania ostrzeżeń o czcionkach](https://example.com/images/capture-font-warnings.png "przykład przechwytywania ostrzeżeń o czcionkach")

*Zrzut ekranu pokazuje uruchomienie konsoli, w którym zgłoszono dwie brakujące czcionki.*

---

## Kolejne kroki – wyjście poza proste raportowanie

Teraz, gdy potrafisz **przechwytywać ostrzeżenia o czcionkach**, rozważ automatyzację naprawy:

1. **Automatyczna zamiana czcionek** – zastąp brakujące czcionki firmowym zamiennikiem, modyfikując `FontSettings.SubstitutionSettings`.  
2. **Logowanie do systemu monitoringu** – przekieruj komunikaty ostrzeżeń do Serilog, ELK lub Azure Application Insights.  
3. **Raporty dla użytkowników** – generuj podsumowanie w HTML lub PDF, aby projektanci mogli sprawdzić, które czcionki należy zainstalować.

Wszystkie te rozszerzenia opierają się na tej samej podstawie, którą omówiliśmy: konfiguracja `LoadOptions`, ładowanie dokumentu i odczyt `WarningInfoCollection`.

---

## Podsumowanie

Właśnie nauczyłeś się, jak **przechwytywać ostrzeżenia o czcionkach** w Aspose.Words, **wykrywać brakujące czcionki** oraz **listować brakujące czcionki** przy użyciu przejrzystego wyjścia konsolowego. Podejście jest proste, wymaga tylko kilku linii C# i działa z dowolną wersją .NET obsługującą Aspose.Words 23.x lub nowszą.  

Wypróbuj je na przykładowym DOCX, w którym celowo odinstalujesz jedną czcionkę – ostrzeżenia pojawią się natychmiast. Następnie zdecyduj, czy zainstalować brakujące kroje, podmienić je programowo, czy po prostu zalogować problem do późniejszej analizy.

Miłego kodowania i niech Twoje dokumenty zawsze renderują się z właściwymi czcionkami!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}