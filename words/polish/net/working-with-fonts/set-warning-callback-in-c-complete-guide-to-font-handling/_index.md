---
category: general
date: 2026-02-10
description: Ustaw funkcję zwrotną ostrzeżeń, aby monitorować zmiany czcionek podczas
  konfigurowania domyślnej czcionki i ustawiania domyślnej czcionki importu w Aspose.Words.
  Poznaj pełne rozwiązanie krok po kroku.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: pl
og_description: Ustaw callback ostrzeżeń, aby monitorować zmiany czcionek podczas
  konfigurowania domyślnej czcionki i ustawiania domyślnej czcionki importu. Zapoznaj
  się z pełnym samouczkiem Aspose.Words.
og_title: Ustaw callback ostrzeżenia w C# – Kompletny przewodnik
tags:
- Aspose.Words
- C#
- Document Import
title: Ustaw funkcję zwrotną ostrzeżenia w C# – Kompletny przewodnik po obsłudze czcionek
url: /pl/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ustaw callback ostrzeżeń w C# – Kompletny przewodnik po obsłudze czcionek

Czy kiedykolwiek potrzebowałeś **set warning callback** podczas ładowania dokumentu Word i zastanawiałeś się, jak jednocześnie *configure default font*? Nie jesteś sam. W wielu rzeczywistych projektach — takich jak automatyczne generatory raportów czy potoki konwersji dokumentów — brakujące czcionki mogą cicho zepsuć układ, a jedynym sposobem na wykrycie tych problemów jest **monitor font changes** za pomocą callbacku ostrzeżeń.

W tym tutorialu przeprowadzimy Cię przez praktyczny przykład, który pokaże, jak **set warning callback**, **configure default font**, a nawet **set default import font** przy użyciu Aspose.Words dla .NET. Po zakończeniu będziesz mieć gotowy do uruchomienia fragment kodu, zrozumiesz, dlaczego każdy element ma znaczenie, i będziesz wiedział, jak dostosować go do przypadków brzegowych, takich jak własne foldery czcionek czy ciche podstawienia.

---

## Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również na .NET Framework 4.6+)  
- Pakiet NuGet Aspose.Words dla .NET (`Install-Package Aspose.Words`)  
- Folder zawierający czcionkę zapasową, której chcesz użyć (np. `fonts/Arial.ttf`)  
- Podstawowa znajomość aplikacji konsolowych C#  

Nie są wymagane dodatkowe biblioteki.

---

## Krok 1: Utwórz LoadOptions i **configure default font**

Pierwszą rzeczą, którą robisz, gdy chcesz kontrolować obsługę czcionek, jest zbudowanie instancji `LoadOptions`. Ten obiekt informuje Aspose.Words, jak traktować brakujące czcionki podczas importu.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Dlaczego to jest ważne:**  
Jeśli dokument źródłowy odwołuje się do czcionki, której nie ma zainstalowanej na serwerze, Aspose.Words spojrzy na folder, który podałeś. To jest sedno **set default import font** — wyraźnie informujesz bibliotekę, gdzie znaleźć zamiennik, zanim pojawią się jakiekolwiek ostrzeżenia.

---

## Krok 2: **Set warning callback** do **monitor font changes**

Aspose.Words emituje `WarningInfoCollection` za każdym razem, gdy musi podstawić czcionkę, między innymi. Dołączając obsługę, możesz logować lub reagować na każde podstawienie.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Dlaczego to jest ważne:**  
Samo **configure default font** nie wystarczy, jeśli potrzebujesz audytować, które czcionki zostały faktycznie zamienione. Callback zapewnia log w czasie rzeczywistym, spełniając wymóg **monitor font changes** i pomagając wykrywać nieoczekiwane zamienniki wcześnie w pipeline CI.

---

## Krok 3: Załaduj dokument z przygotowanymi opcjami

Teraz, gdy opcje ładowania są w pełni przygotowane, możesz bezpiecznie załadować dowolny plik `.docx`. Callback uruchomi się automatycznie, jeśli nastąpi podstawienie.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**Co zobaczysz:**  
Jeśli źródło używa czcionki, której nie ma, konsola wydrukuje coś w stylu:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Ten wynik potwierdza, że pomyślnie **set warning callback** oraz że **default import font** zadziałał.

---

## Krok 4: (Opcjonalnie) Dostosuj zachowanie podstawiania czcionek

Czasami możesz chcieć zastąpić *wszystkie* brakujące czcionki jedną rodziną, niezależnie od pierwotnego żądania. Aspose.Words pozwala ustawić *fallback font* globalnie.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**Kiedy używać:**  
Jeśli generujesz PDF‑y dla marki, która dopuszcza tylko ograniczony zestaw czcionek, zapewnia to spójność we wszystkich dokumentach, nawet jeśli źródło próbuje użyć czegoś egzotycznego.

---

## Krok 5: Zapisz lub dalej przetwarzaj dokument

Po załadowaniu możesz kontynuować dowolne przetwarzanie — edycję, konwersję do PDF, wyciąganie tekstu itp. Oto szybki przykład zapisu dokumentu jako PDF przy zachowaniu podstawionych czcionek.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

Wynikowy PDF wyświetli czcionkę zapasową wszędzie tam, gdzie nastąpiło podstawienie, dając wizualne potwierdzenie, że **set warning callback** działało zgodnie z oczekiwaniami.

---

## Częste pułapki i wskazówki profesjonalistów

| Problem | Dlaczego się pojawia | Rozwiązanie |
|---------|----------------------|-------------|
| **Callback nigdy nie uruchamia się** | `LoadOptions.WarningCallback` nie został przypisany *przed* załadowaniem dokumentu. | Zawsze podłącz callback **przed** wywołaniem `new Document(...)`. |
| **Nieprawidłowy folder czcionek** | Błąd w ścieżce lub brak uprawnień do odczytu. | Sprawdź, czy folder istnieje i aplikacja ma dostęp `Read`. Używaj ścieżek bezwzględnych dla niezawodności. |
| **Wiele podstawień, hałaśliwy output** | Duże dokumenty z wieloma brakującymi czcionkami. | Filtruj ostrzeżenia po `WarningType.FontSubstitution` (jak pokazano) lub zapisz je do pliku logu zamiast na konsolę. |
| **Czcionka zapasowa nie zastosowana** | Czcionka zapasowa nie jest zainstalowana na maszynie. | Umieść plik `.ttf`/`.otf` w folderze przekazanym do `SetFontsFolder`. Aspose.Words ładuje go bezpośrednio, nie wymaga instalacji w systemie. |

**Pro tip:** Gdy uruchamiasz to w pipeline CI/CD, przekieruj wyjście konsoli do artefaktu builda. Dzięki temu masz ślad audytu każdego podstawienia czcionki, które miało miejsce podczas budowania.

---

## Pełny działający przykład (gotowy do kopiowania i wklejania)

Poniżej znajduje się kompletny program, który możesz wkleić do nowego projektu aplikacji konsolowej. Zawiera wszystkie kroki, dyrektywy using oraz komentarze, których potrzebujesz.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Oczekiwany output konsoli** (zakładając, że `Times New Roman` był brakujący):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Uruchom program, otwórz `output.pdf` i zobaczysz dokument renderowany czcionką zapasową tam, gdzie to konieczne.

---

## Zakończenie

Masz teraz solidny, gotowy do produkcji wzorzec, jak **set warning callback** w C#, **configure default font**, **monitor font changes** i **set default import font** przy pracy z Aspose.Words. Poprzez podłączenie zbieracza ostrzeżeń przed ładowaniem, skierowanie `FontSettings` do niezawodnego folderu czcionek oraz opcjonalne wymuszenie globalnego fallbacku, zyskujesz pełną widoczność i kontrolę nad podstawieniami czcionek — dokładnie to, czego potrzebuje każde solidne przetwarzanie dokumentów.

Gotowy na kolejny poziom? Spróbuj połączyć to podejście z:

- **Dynamic font loading** z bazy danych (użyj `FontSettings.SetFontsFolder` w czasie działania).  
- **Custom warning handlers** zapisujące do strukturalnego logu (JSON lub CSV) dla analiz.  
- **Parallel document processing**, w którym każdy wątek otrzymuje własny `LoadOptions`, aby uniknąć konfliktów.

Śmiało eksperymentuj, dostosowuj kod do własnej architektury i dziel się odkryciami w komentarzach. Szczęśliwego kodowania!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}