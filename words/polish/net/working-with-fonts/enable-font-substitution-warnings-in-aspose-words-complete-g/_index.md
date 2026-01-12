---
category: general
date: 2026-01-11
description: Włącz ostrzeżenia o podstawianiu czcionek, aby wykrywać brakujące czcionki
  w dokumentach .NET. Dowiedz się, jak uzyskać nazwę brakującej czcionki i wyświetlić
  listę brakujących czcionek przy użyciu Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: pl
og_description: Włącz ostrzeżenia o podstawianiu czcionek w Aspose.Words, aby wykrywać
  brakujące czcionki, uzyskać nazwę brakującej czcionki i wyświetlać listę brakujących
  czcionek w dokumentach.
og_title: Włącz ostrzeżenia o zamianie czcionek – samouczek C# krok po kroku
tags:
- Aspose.Words
- C#
- Document Processing
title: Włącz ostrzeżenia o podstawianiu czcionek w Aspose.Words – Kompletny przewodnik
url: /pl/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Włącz ostrzeżenia o podstawianiu czcionek – Kompletny przewodnik

Zastanawiałeś się kiedyś, dlaczego dokument Word wygląda nieco inaczej po załadowaniu na serwer? Najprawdopodobniej czcionka użyta przez pierwotnego autora nie jest dostępna na twoim komputerze, a Aspose.Words cicho podmieniła ją na najbliższą pasującą. **Włącz ostrzeżenia o podstawianiu czcionek** i od razu dowiesz się, które czcionki są brakujące, czym zostały zastąpione i jak postąpić z tą informacją.

W tym samouczku przeprowadzimy Cię przez praktyczny, kompleksowy przykład, który pokaże, jak **wykrywać brakujące czcionki**, uzyskać **nazwę brakującej czcionki**, a nawet **wyświetlić listę brakujących czcionek** do raportowania. Bez zbędnych wstępów, po prostu jasne rozwiązanie, które możesz wstawić do dowolnego projektu .NET już dziś.

---

## Czego się nauczysz

- Jak skonfigurować `LoadOptions`, aby Aspose.Words generowało szczegółowe ostrzeżenia.
- Dokładny kod potrzebny do załadowania dokumentu i wyliczenia ostrzeżeń związanych z czcionkami.
- Sposoby wyodrębnienia nazwy brakującej czcionki i jej podstawienia, a następnie wygenerowania przejrzystego raportu.
- Wskazówki dotyczące obsługi przypadków brzegowych, takich jak dokumenty z dziesiątkami brakujących czcionek lub własne foldery czcionek.

### Wymagania wstępne

- .NET 6+ (kod działa również z .NET Framework 4.7+)
- Aspose.Words dla .NET 23.10 lub nowszy (można go pobrać z NuGet)
- Przykładowy plik DOCX, który odwołuje się do czcionki niezainstalowanej na twoim komputerze (nazwijmy go `MissingFont.docx`)

Jeśli masz te podstawy, zanurzmy się.

---

## Krok 1: Skonfiguruj LoadOptions, aby włączyć ostrzeżenia o podstawianiu czcionek  

Pierwszą rzeczą, którą musisz zrobić, jest poinformowanie Aspose.Words, że zależy Ci na brakujących czcionkach. Domyślnie biblioteka zapisuje ostrzeżenia jedynie wewnętrznie. Ustawienie `SubstitutionWarningLevel` na `Typical` (lub `All` dla najbardziej szczegółowego wyjścia) przełącza tę funkcję.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Dlaczego to jest ważne:**  
Gdy `SubstitutionWarningLevel` jest ustawione, za każdym razem, gdy Aspose.Words nie może znaleźć odwołanej czcionki, dodaje `FontSubstitutionWarning` do kolekcji `Warnings` dokumentu. Ta kolekcja jest jedynym niezawodnym sposobem na **wykrywanie brakujących czcionek** bez ręcznego parsowania dokumentu.

> **Pro tip:** Jeśli pracujesz z zestawem dokumentów i chcesz mieć pewność, że przechwycisz każde podstawienie, użyj `FontSubstitutionWarningLevel.All`. Jest to nieco głośniejsze, ale zapewnia, że żadne ostrzeżenie nie zostanie pominięte.

---

## Krok 2: Załaduj dokument przy użyciu skonfigurowanych opcji  

Teraz, gdy system ostrzeżeń jest przygotowany, załaduj swój plik DOCX przy użyciu `LoadOptions`, które właśnie przygotowaliśmy. Ścieżka może być bezwzględna lub względna; po prostu upewnij się, że plik istnieje.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**Co się dzieje w tle?**  
Aspose.Words parsuje XML dokumentu, rozwiązuje każdy element `<w:font>` i sprawdza katalog czcionek systemowych (plus wszelkie własne foldery, które możesz dodać do `FontSettings`). Gdy nie może znaleźć czcionki, zapisuje ostrzeżenie — dokładnie to, czego potrzebujemy, aby później **wyświetlić listę brakujących czcionek**.

---

## Krok 3: Iteruj po ostrzeżeniach i wyodrębnij szczegóły brakującej czcionki  

Gdy dokument jest w pamięci, kolekcja `Warnings` zawiera każde `FontSubstitutionWarning`. Przejdziemy ją w pętli, odfiltrujemy odpowiedni typ i wydrukujemy przyjazny raport.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Oczekiwany wynik** (zakładając, że dokument źródłowy odwołuje się do `MyCustomFont`, której nie ma zainstalowanej):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Zauważ, że każdy wpis podaje zarówno **nazwę brakującej czcionki** (`MyCustomFont`), jak i zapasową (`Arial`). To dokładnie informacje, które potrzebujesz, aby zdecydować, czy osadzić oryginalną czcionkę, poprosić autora o zamiennik, czy po prostu zaakceptować podstawienie.

---

## Krok 4: Opcjonalnie – Zbierz dane w listę do dalszego przetwarzania  

Jeśli potrzebujesz wyeksportować raport do CSV, wysłać go przez API lub po prostu przechować w pamięci na później, możesz umieścić ostrzeżenia w silnie typowanej liście.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Teraz masz **listę brakujących czcionek** w formacie, który może wykorzystać każdy system downstream. Niezależnie od tego, czy zasilasz dashboard, czy generujesz dziennik audytu, dane są gotowe.

---

## Krok 5: Obsługa przypadków brzegowych i typowych pułapek  

### Wiele brakujących czcionek w jednym uruchomieniu  

Duże szablony korporacyjne często odwołują się do dziesiątek własnych czcionek. Kolekcja ostrzeżeń może stać się obszerna, ale przedstawiony powyżej wzorzec iteracji skaluje się liniowo, więc wydajność nie jest problemem. Pamiętaj tylko, aby utrzymać czytelność wyjścia — grupowanie według strony lub stylu może być pomocne, jeśli potrzebna jest głębsza analiza.

### Własne foldery czcionek  

Jeśli przechowujesz czcionki w niestandardowym katalogu (np. udostępnionym zasobie sieciowym), poinformuj Aspose.Words, gdzie ich szukać:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Ustawienie tego *przed* załadowaniem dokumentu daje bibliotece szansę na znalezienie czcionek, co może całkowicie wyeliminować niektóre ostrzeżenia.

### Tłumienie konkretnych ostrzeżeń  

Czasami wiesz, że konkretne podstawienie jest akceptowalne (np. dekoracyjna czcionka, którą nie masz nic przeciwko zamianie). Możesz odfiltrować je po fakcie:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Zgodność wersji  

Enum `FontSubstitutionWarningLevel` jest stabilny od wersji Aspose.Words 20.12. Jeśli używasz starszej wersji, może być konieczna aktualizacja, aby uzyskać dostęp do funkcji poziomu ostrzeżeń.

---

## Pełny działający przykład  

Poniżej znajduje się kompletny, gotowy do uruchomienia program, który zawiera wszystkie powyższe kroki. Wklej go do nowego projektu konsolowego, dodaj pakiet Aspose.Words z NuGet i wskaż `docPath` na dokument, który odwołuje się do brakującej czcionki.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

Uruchomienie tego programu **włączy ostrzeżenia o podstawianiu czcionek**, **wykryje brakujące czcionki**, **pobierze nazwę brakującej czcionki** oraz **wyświetli listę brakujących czcionek** zarówno w konsoli, jak i w pliku CSV.

---

## Podsumowanie  

Właśnie omówiliśmy wszystko, co potrzebne, aby **włączyć ostrzeżenia o podstawianiu czcionek** w Aspose.Words, od początkowej konfiguracji po wyodrębnienie czystej listy brakujących czcionek. Postępując zgodnie z powyższymi krokami, będziesz mógł audytować swoje dokumenty, zapewnić spójność wizualną i uniknąć nieprzyjemnych niespodzianek podczas renderowania na serwerze.

Następnie możesz rozważyć:

- **Osadzanie brakujących czcionek** bezpośrednio w wyjściowym PDF lub DOCX (użyj `FontSettings.EmbeddedFonts`).
- **Automatyzacja instalacji czcionek** na agentach budowania na podstawie wygenerowanego raportu.
- **Integracja z pipeline'ami CI** w celu niepowodzenia buildów, gdy krytyczne czcionki są nieobecne.

Wypróbuj je, a zamienisz prosty system ostrzeżeń w pełnoprawny przepływ zarządzania czcionkami.

Szczęśliwego kodowania i niech wszystkie Twoje czcionki zostaną odnalezione!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}