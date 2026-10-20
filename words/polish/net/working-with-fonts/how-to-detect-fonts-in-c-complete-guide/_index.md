---
category: general
date: 2026-04-02
description: Jak wykrywać czcionki w dokumentach C# przy użyciu Aspose.Words. Dowiedz
  się, jak konfigurować ustawienia czcionek i efektywnie obsługiwać brakujące czcionki.
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: pl
og_description: Jak wykrywać czcionki w dokumentach C# przy użyciu Aspose.Words. Ten
  przewodnik pokazuje, jak skonfigurować ustawienia czcionek i obsłużyć brakujące
  czcionki.
og_title: Jak wykrywać czcionki w C# – Kompletny przewodnik
tags:
- C#
- Aspose.Words
- Document Processing
title: Jak wykrywać czcionki w C# – Kompletny przewodnik
url: /pl/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wykrywać czcionki w C# – Kompletny przewodnik

Zastanawiałeś się kiedyś **jak wykrywać czcionki**, które są brakujące lub podstawiane podczas ładowania dokumentu Word w .NET? Nie jesteś sam — programiści często napotykają problem, gdy dokument odwołuje się do czcionki, której nie ma zainstalowanej na serwerze. Dobrą wiadomością jest to, że Aspose.Words oferuje czysty, programowy sposób na wykrycie tych luk.

W tym tutorialu przeprowadzimy praktyczny przykład, który nie tylko pokaże **jak wykrywać czcionki**, ale także zademonstruje **konfigurację ustawień czcionek** oraz **obsługę brakujących czcionek** w elegancki sposób. Na koniec otrzymasz gotowy fragment kodu, który wypisuje każde ostrzeżenie o podstawieniu czcionki, dzięki czemu możesz logować, alarmować lub zamieniać czcionki według potrzeb.

---

## Czego będziesz potrzebować

- **Aspose.Words for .NET** (najlepiej najnowsza wersja; poniższy kod celuje w .NET 6+)
- Środowisko programistyczne .NET (Visual Studio, Rider lub VS Code)
- Przykładowy plik `.docx`, który odwołuje się do czcionki, której nie masz zainstalowanej (idealny do testów)

Nie są wymagane dodatkowe pakiety NuGet poza Aspose.Words, a rozwiązanie działa na Windows, Linux i macOS.

---

## Krok 1: Zainstaluj i odwołaj się do Aspose.Words

Najpierw dodaj bibliotekę do swojego projektu. Komenda NuGet jest prosta:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Jeśli pracujesz na serwerze CI, przypnij wersję pakietu, aby uniknąć nieoczekiwanych zmian łamiących kompatybilność.

---

## Krok 2: Skonfiguruj ustawienia czcionek (i przygotuj opcje ładowania)

Zanim otworzysz dokument, możesz powiedzieć Aspose.Words, gdzie szukać czcionek zapasowych. To jest część **konfiguracji ustawień czcionek**, która zapobiega cichej zamianie czcionek, których nie chcesz.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

Po co to robić? Jeśli dokument odwołuje się do *Comic Sans*, a Twój serwer ma tylko *Calibri*, Aspose.Words podstawi *Calibri* i wygeneruje ostrzeżenie. Konfigurując ścieżkę wyszukiwania, ograniczasz niepożądane niespodzianki.

---

## Krok 3: Załaduj dokument z przygotowanymi opcjami

Teraz faktycznie otwieramy plik. `LoadOptions`, które zbudowaliśmy w poprzednim kroku, przekazywane są bezpośrednio do konstruktora `Document`.

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

Jeśli plik nie zostanie znaleziony lub będzie uszkodzony, zostanie rzucony wyjątek — warto więc otoczyć ten kod blokiem try/catch w kodzie produkcyjnym.

---

## Krok 4: Przeskanuj ostrzeżenia dokumentu pod kątem podstawień czcionek

Aspose.Words zbiera listę ostrzeżeń podczas parsowania. Wśród nich, `FontSubstitutionWarning` informuje dokładnie, która czcionka została podmieniona.

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

Kolekcja `Warnings` może zawierać także inne elementy (np. `DocumentStructureWarning`). Filtrując pod kątem `FontSubstitutionWarning`, zapewniasz, że raportujesz wyłącznie scenariusz **obsługi brakujących czcionek**, który nas interesuje.

---

## Krok 5: Połącz wszystko – kompletny, uruchamialny przykład

Poniżej pełny program. Skopiuj‑wklej go do nowej aplikacji konsolowej i uruchom; zobaczysz każdą brakującą czcionkę wypisaną w konsoli.

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**Oczekiwany wynik** (przykład):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

Jeśli dokument używa wyłącznie czcionek dostępnych na maszynie, zamiast tego zobaczysz linię „No font substitutions detected”.

---

## Przypadki brzegowe i najczęstsze pytania

### Co jeśli dokument nie zawiera **żadnych ostrzeżeń**?

To po prostu oznacza, że każda odwołana czcionka została znaleziona w skonfigurowanych folderach. Flaga `anySubstitutions` w przykładzie obsługuje ten scenariusz.

### Czy mogę **logować** ostrzeżenia do pliku zamiast do konsoli?

Oczywiście. Zamień wywołania `Console.WriteLine` na logger według własnego wyboru (Serilog, NLog itp.). Obiekt `WarningInfo` udostępnia także `WarningType` i `WarningMessage`, jeśli potrzebujesz więcej szczegółów.

### Jak **zignorować** niektóre czcionki, np. firmową czcionkę marki, której nigdy nie należy podmieniać?

Możesz dodać własną regułę podstawiania:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

Teraz Aspose.Words podstawi *MyBrandFont* wyłącznie wymienionymi alternatywami, a Ty nadal otrzymasz ostrzeżenie, na które możesz zareagować.

### Czy to działa w kontenerach **Linux**?

Tak — wystarczy zamontować folder z wymaganymi plikami `.ttf`/`.otf` i wskazać go w `SetFontsFolder`. Aspose.Words nie polega na czcionkach zainstalowanych w systemie operacyjnym.

---

## Przegląd wizualny

![diagram wykrywania czcionek](detect-fonts.png "Diagram przedstawiający kroki wykrywania czcionek w dokumencie")

*Tekst alternatywny obrazu:* **diagram wykrywania czcionek** ilustrujący konfigurację, ładowanie i inspekcję ostrzeżeń.

---

## Podsumowanie – czego się nauczyliśmy

- **Jak wykrywać czcionki** brakujące lub podstawiane przy użyciu ostrzeżeń Aspose.Words.  
- Jak **konfigurować ustawienia czcionek**, aby wskazywały na własne foldery i ustawiały domyślną czcionkę zapasową.  
- Strategie **obsługi brakujących czcionek**, od logowania po własne reguły podstawiania.

Wszystko to mieści się w kompaktowej, samodzielnej aplikacji konsolowej, którą możesz wrzucić do dowolnego rozwiązania .NET.

---

## Kolejne kroki i tematy powiązane

- **Osadzanie czcionek** bezpośrednio w dokumencie wyjściowym, aby uniknąć przyszłych podstawień (`SaveOptions` z `EmbedFullFonts`).  
- **Programowe zastępowanie czcionek** – zamień brakujące czcionki na konkretną alternatywę przed zapisem.  
- **Optymalizacja wydajności** – buforuj `FontSettings` przy przetwarzaniu wielu dokumentów w partii.  

Jeśli interesują Cię te tematy, wyszukaj *configure font settings* i *handle missing fonts* — prowadzą do głębszych artykułów o zarządzaniu czcionkami w Aspose.Words.

---

Miłego kodowania! Masz dziwny przypadek czcionki? zostaw komentarz, a pomożemy rozwiązać problem.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}