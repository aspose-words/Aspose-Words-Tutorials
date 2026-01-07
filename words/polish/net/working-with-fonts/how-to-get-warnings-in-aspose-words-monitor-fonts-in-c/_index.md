---
category: general
date: 2026-01-06
description: Dowiedz się, jak otrzymywać ostrzeżenia podczas ładowania dokumentów
  i jak monitorować czcionki przy użyciu Aspose.Words. Ten przewodnik obejmuje wywołania
  zwrotne ostrzeżeń oraz śledzenie podstawiania czcionek.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: pl
og_description: Jak uzyskać ostrzeżenia w Aspose.Words? Postępuj zgodnie z tym samouczkiem
  krok po kroku, aby monitorować czcionki i przechwytywać komunikaty o zastąpieniu
  podczas ładowania dokumentów.
og_title: Jak uzyskać ostrzeżenia w Aspose.Words – monitorowanie czcionek
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Jak uzyskać ostrzeżenia w Aspose.Words – monitorowanie czcionek w C#
url: /pl/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak uzyskać ostrzeżenia w Aspose.Words – monitorowanie czcionek w C#

Zastanawiałeś się kiedyś **jak uzyskać ostrzeżenia**, gdy dokument Word zawiera czcionki, których nie masz zainstalowanych? To częsty problem — aplikacja cicho podmienia brakujące czcionki i nie wiesz, co się zmieniło. Dobrą wiadomością jest to, że możesz podłączyć się do systemu ostrzeżeń Aspose.Words i **monitorować czcionki** w czasie rzeczywistym.

W tym tutorialu pokażemy dokładnie, jak przechwycić te ostrzeżenia o podmianie czcionek, dlaczego ma to znaczenie i co zrobić z uzyskanymi informacjami. Bez zewnętrznych dokumentów, tylko kompletny, gotowy do uruchomienia przykład, który możesz wkleić od razu do Visual Studio.

> **Pro tip:** Jeśli budujesz pipeline konwersji dokumentów, wczesne logowanie brakujących czcionek chroni Cię przed nieprzyjemnymi niespodziankami w układzie na dalszych etapach.

---

## Co będzie potrzebne

- **Aspose.Words for .NET** (najnowsza wersja; API nie zmieniło się od v23.10)
- Środowisko programistyczne .NET (Visual Studio, Rider lub VS Code z rozszerzeniem C#)
- Przykładowy plik `.docx`, który odwołuje się do czcionki, której nie masz zainstalowanej (np. **„NonExistentFont”**)

To wszystko — żadnych dodatkowych pakietów NuGet poza Aspose.Words.

---

## Krok 1 – Utworzenie kolektora ostrzeżeń (Primary Keyword in Header)

Pierwszą rzeczą, której potrzebujesz, jest miejsce do przechowywania ostrzeżeń w miarę ich pojawiania się. Aspose.Words udostępnia właściwość `WarningCallback` w klasie `LoadOptions` właśnie w tym celu.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Dlaczego to ważne:**  
Gdy biblioteka napotka brakującą czcionkę, nie rzuca wyjątku; emituje obiekt `WarningInfo`. Podłączając kolektor, zyskujesz pełną widoczność każdego zdarzenia podmiany, co pozwala **monitorować czcionki** bez zanieczyszczania konsoli niepowiązanymi komunikatami.

---

## Krok 2 – Załadowanie dokumentu z włączonymi ostrzeżeniami

Teraz faktycznie odczytujemy plik. `LoadOptions`, które przygotowaliśmy w poprzednim kroku, zapewniają, że wszystkie ostrzeżenia związane z czcionkami zostaną przechwycone.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**Co dzieje się pod maską?**  
Aspose.Words parsuje plik Word, rozwiązuje czcionki i za każdym razem, gdy nie może znaleźć żądanej czcionki, przechodzi na substytut (zwykle Arial). Ta podmiana wywołuje ostrzeżenie `WarningType.FontSubstitution`, które trafia do `warningCollector`.

---

## Krok 3 – Przeglądanie zebranych ostrzeżeń (Primary Keyword Appears Again)

Po załadowaniu dokumentu po prostu iterujemy po `warningCollector` i wypisujemy wszystkie komunikaty o podmianie czcionek.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Oczekiwany wynik** (zakładając, że brakująca czcionka to *„FancyScript”*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Jeśli dokument zawiera wiele nieznanych czcionek, zobaczysz jedną linię na każdą podmianę — idealne do logowania lub powiadamiania.

---

## Krok 4 – Opcjonalnie: Zalogowanie lub zapisanie informacji o ostrzeżeniach

W produkcji prawdopodobnie będziesz potrzebował czegoś więcej niż `Console.WriteLine`. Oto szybki przykład, który zapisuje ostrzeżenia do pliku JSON do późniejszej analizy.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Teraz masz trwały zapis, który możesz podać do dashboardu monitorującego, a nawet wyzwolić automatyczne żądanie brakujących plików czcionek.

---

## Krok 5 – Weryfikacja wyniku i sprzątanie

Uruchom program. Jeśli zobaczysz komunikaty o podmianie, udało Ci się **uzyskać ostrzeżenia** i teraz aktywnie **monitorujesz czcionki**. Jeśli nic się nie pojawi, sprawdź ponownie, czy testowy dokument naprawdę odwołuje się do czcionki, której nie ma na maszynie.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

Liczba zerowa zazwyczaj oznacza jedną z dwóch sytuacji:

1. Wszystkie czcionki zostały rozwiązane (być może czcionka *jest* zainstalowana lokalnie), lub
2. Dokument nie zawierał żadnych odwołań do czcionek wymagających podmiany.

---

## Typowe pułapki i jak ich unikać

| Pułapka | Dlaczego się pojawia | Rozwiązanie |
|---------|----------------------|-------------|
| **Brak ostrzeżeń** | Czcionka faktycznie istnieje w systemie lub dokument używa tylko wbudowanych czcionek. | Zmień nazwę czcionki w pliku źródłowym na coś niemożliwego (np. `XYZ123`) i spróbuj ponownie. |
| **Zbyt wiele ostrzeżeń (szum)** | Ładujesz wiele dokumentów w pętli bez czyszczenia kolektora. | Utwórz nowy `WarningInfoCollection` dla każdego dokumentu lub wywołaj `warningCollector.Clear()` po przetworzeniu. |
| **Wpływ na wydajność** | Nadmierne logowanie na dysk może spowolnić przetwarzanie wsadowe. | Buforuj ostrzeżenia w pamięci i zapisuj je partiami, lub użyj asynchronicznego I/O. |
| **Brak `using Aspose.Words.Loading;`** | Klasa `LoadOptions` znajduje się w tej przestrzeni nazw. | Dodaj brakujący dyrektyw `using`, jak pokazano w Kroku 1. |

---

## Rozszerzanie rozwiązania – monitorowanie innych typów ostrzeżeń

Choć podmiana czcionek jest najbardziej widoczna, Aspose.Words może emitować ostrzeżenia dla:

- **Przestarzałych funkcji** (`WarningType.Deprecated`),
- **Potencjalnej utraty danych** (`WarningType.DataLoss`),
- **Nieobsługiwanych formatów plików** (`WarningType.UnsupportedFileFormat`).

Możesz rozszerzyć filtr w Kroku 3, aby przechwytywać także te typy:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

W ten sposób nie tylko **dowiesz się, jak monitorować czcionki**, ale także **jak uzyskać ostrzeżenia** dla każdego scenariusza, z którym może spotkać się Twoja aplikacja.

---

## Pełny działający przykład (Gotowy do kopiowania)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Uruchom:** Zbuduj projekt, wykonaj go, a zobaczysz ostrzeżenia wypisane i zapisane. To kompletną odpowiedź na **jak uzyskać ostrzeżenia** i **jak monitorować czcionki** przy użyciu Aspose.Words.

---

## Podsumowanie

Teraz wiesz **jak uzyskać ostrzeżenia** z Aspose.Words, szczególnie w scenariuszach podmiany czcionek, oraz **jak monitorować czcionki** podczas procesu ładowania dokumentu. Poprzez podłączenie `WarningCallback`, iterowanie zebranych obiektów `WarningInfo` i opcjonalne zapisywanie danych, zyskujesz pełną przejrzystość zdarzeń brakujących czcionek — kluczową funkcję dla każdego pipeline przetwarzania dokumentów.

Co dalej? Spróbuj rozszerzyć filtr ostrzeżeń, aby obejmował utratę danych lub ostrzeżenia o przestarzałych funkcjach, albo zintegrować log JSON z dashboardem monitorującym, takim jak Grafana. Ten sam wzorzec działa dla wszystkich typów ostrzeżeń, więc będziesz dobrze przygotowany, by śledzić każdy problem, który Aspose.Words Ci zgłosi.

Miłego kodowania i niech Twoje dokumenty zawsze renderują się dokładnie tak, jak tego oczekujesz! 

---

<img src="font-warnings.png" alt="how to get warnings in Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}