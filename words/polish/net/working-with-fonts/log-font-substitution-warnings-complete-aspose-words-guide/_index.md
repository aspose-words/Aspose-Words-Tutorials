---
category: general
date: 2026-01-14
description: Rejestruj ostrzeżenia o zastępowaniu czcionek podczas ładowania dokumentów
  Word przy użyciu Aspose.Words. Dowiedz się, jak wykrywać brakujące czcionki i jak
  przechwytywać brakujące czcionki w C#.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: pl
og_description: Rejestruj ostrzeżenia o podstawianiu czcionek podczas ładowania dokumentów
  Word za pomocą Aspose.Words. Dowiedz się, jak wykrywać brakujące czcionki i przechwytywać
  brakujące czcionki w C#.
og_title: Rejestrowanie ostrzeżeń o podstawianiu czcionek – Kompletny przewodnik Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Ostrzeżenia o podstawianiu czcionek w logu – Kompletny przewodnik Aspose.Words
url: /pl/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Logowanie ostrzeżeń o podstawianiu czcionek – Kompletny przewodnik Aspose.Words

Log font substitution warnings jest niezbędne, gdy musisz zapewnić, że dokument Word wygląda dokładnie tak samo po załadowaniu przez Aspose.Words. Jeśli kiedykolwiek zastanawiałeś się, jak **detect missing fonts** lub chcesz wiedzieć, **how to capture missing fonts**, jesteś we właściwym miejscu.  

W tym samouczku przeprowadzimy Cię przez rzeczywisty scenariusz, pokażemy kompletny kod C#, i wyjaśnimy, dlaczego każda linia ma znaczenie. Po zakończeniu będziesz mógł logować każde zdarzenie podstawiania czcionki i reagować na nie — żadne tajemnicze ostrzeżenia nie pozostaną niewykryte.

![Przykład logowania ostrzeżeń o podstawianiu czcionek](/images/font-warnings.png "Zrzut ekranu pokazujący wyjście konsoli logowania ostrzeżeń o podstawianiu czcionek")

## Czego się nauczysz

- Jak skonfigurować `LoadOptions`, aby Aspose.Words generował typowane ostrzeżenia o podstawianiu czcionek.  
- Dokładne kroki do **detect missing fonts** podczas ładowania dokumentu.  
- Czysty sposób na **capture missing fonts** i zapisanie ich do własnego logu lub systemu monitoringu.  
- Obsługa przypadków brzegowych (np. gdy dokument zawiera czcionkę, która nie jest zainstalowana na serwerze).  

### Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+).  
- Ważna licencja Aspose.Words for .NET (lub wersja próbna).  
- Podstawowa znajomość C# i aplikacji konsolowych.  

Jeśli już je masz, zanurzmy się.

## Krok 1 – Skonfiguruj LoadOptions, aby generować typowane ostrzeżenia

Sednem rozwiązania jest `LoadOptions.FontSubstitutionWarning`. Przełączając go na `RaiseTypedWarnings`, informujesz Aspose.Words, aby wywoływał zdarzenie **za każdym razem**, gdy nie może znaleźć dokładnie żądanej czcionki.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Dlaczego to ważne:**  
> Domyślne zachowanie cicho zamienia brakującą czcionkę na najbliższą pasującą, co może prowadzić do problemów z układem, których nie przewidzisz. Generowanie typowanych ostrzeżeń daje pełną widoczność.

## Krok 2 – Subskrybuj zdarzenie ostrzeżenia

Teraz podłączamy się do `loadOptions.FontSubstitutionWarning`. Lambda otrzymuje obiekt `e`, który dokładnie informuje, której czcionki brakowało i jaka została użyta zamiast niej.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Pro tip:** Jeśli uruchamiasz to na serwerze www, zamień `Console.WriteLine` na strukturalny logger (Serilog, NLog itp.), aby móc później zapytać o dane.

## Krok 3 – Załaduj dokument przy użyciu skonfigurowanych opcji

Mając mechanizm ostrzeżeń w miejscu, po prostu załaduj dokument tak, jak zwykle. Zdarzenie wyzwala się automatycznie dla każdej brakującej czcionki.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Oczekiwany wynik w konsoli

Jeśli `input.docx` odwołuje się do czcionki o nazwie *MyFancyFont*, która nie jest zainstalowana, zobaczysz:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Każda linia odpowiada zdarzeniu **detect missing fonts**, dając pełny ślad audytu.

## Krok 4 – Obsługa przypadków brzegowych i scenariuszy zaawansowanych

### 4.1 Gdy nie zachodzi podstawienie

Czasami dokument używa tylko czcionek systemowych, które już są dostępne. W takim przypadku zdarzenie ostrzeżenia nigdy nie wyzwala się i otrzymasz czystą konsolę bez wyjścia. To dobry znak — Twoje środowisko ma już wszystkie wymagane czcionki.

### 4.2 Zbieranie ostrzeżeń do późniejszej analizy

Jeśli musisz przechowywać ostrzeżenia do nocnego raportu, zbierz je na liście:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

Po załadowaniu możesz serializować `missingFonts` do JSON, zapisać do bazy danych lub wysłać podsumowanie e‑mailem.

### 4.3 Praca z PDF‑ami lub innymi formatami

To samo podejście `LoadOptions` działa dla wywołań `Load` na PDF‑ach, RTF i nawet plikach HTML. Po prostu przekaż tę samą instancję opcji, a Aspose.Words wygeneruje ostrzeżenia dla każdej czcionki, której nie może dopasować.

## Krok 5 – Zweryfikuj wynik programowo

Jeśli wolisz test automatyczny zamiast ręcznego sprawdzania konsoli, asercja, że lista zawiera oczekiwane wpisy:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Ten fragment pokazuje **how to capture missing fonts** w kodzie, nie tylko w logach.

## Typowe pułapki i jak ich uniknąć

| Pułapka | Dlaczego się dzieje | Rozwiązanie |
|---------|----------------------|-------------|
| Zapomnienie o ustawieniu `RaiseTypedWarnings` | Domyślnie jest `DoNotRaise`, więc żadne zdarzenia nie są wyzwalane. | Jawnie ustaw `FontSubstitutionWarning` jak pokazano w Kroku 1. |
| Używanie `Console.WriteLine` w aplikacji webowej | Wyjście konsoli znika w IIS/ASP.NET Core. | Przejdź na trwały logger (np. Serilog). |
| Ładowanie dokumentu ze względną ścieżką | Katalog roboczy może się różnić w czasie wykonywania. | Użyj ścieżek bezwzględnych lub `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Ignorowanie `SubstitutedFontName` | Tracisz wgląd w to, jaka czcionka zastępcza została wybrana. | Zawsze loguj zarówno `FontName`, jak i `SubstitutedFontName`. |

## Bonus: Automatyzacja instalacji czcionek

Jeśli kontrolujesz środowisko wdrożeniowe, możesz wstępnie zainstalować brakujące czcionki przy użyciu skryptu PowerShell:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Uruchomienie tego przed startem aplikacji eliminuje większość ostrzeżeń **detect missing fonts**.

## Podsumowanie

Omówiliśmy wszystko, co potrzebne, aby **log font substitution warnings** przy ładowaniu dokumentów Word przy użyciu Aspose.Words. Konfigurując `LoadOptions`, subskrybując zdarzenie ostrzeżenia i opcjonalnie przechowując wyniki, możesz niezawodnie **detect missing fonts** i zrozumieć **how to capture missing fonts** dla dowolnego projektu .NET.

Weź kod, dostosuj logger do swojego stosu i nigdy nie będziesz zaskoczony cichym podstawieniem czcionki. Następne kroki mogą obejmować:

- Integrację listy ostrzeżeń z pipeline CI/CD, aby przerywać buildy, gdy brak krytycznych czcionek.  
- Rozszerzenie podejścia w celu monitorowania użycia czcionek w całej flocie dokumentów.  
- Badanie API `FontSettings` Aspose.Words w celu zapewnienia własnych czcionek zastępczych.  

Masz pytania lub trudny scenariusz? Dodaj komentarz, a wspólnie rozwiążemy problem. Szczęśliwego kodowania!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}