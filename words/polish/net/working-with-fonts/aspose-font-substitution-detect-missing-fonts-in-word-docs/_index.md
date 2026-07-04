---
category: general
date: 2026-05-04
description: Dowiedz się, jak używać substytucji czcionek Aspose, aby wykrywać brakujące
  czcionki podczas ładowania dokumentu Word i uzyskać szczegóły brakujących czcionek
  — przewodnik krok po kroku.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: pl
og_description: Opanuj zamianę czcionek Aspose, aby wykrywać brakujące czcionki podczas
  ładowania dokumentu Word i uzyskać informacje o brakujących czcionkach przy użyciu
  pełnego kodu C#.
og_title: Zastępowanie czcionek Aspose – Wykrywanie brakujących czcionek w dokumentach
  Word
tags:
- Aspose.Words
- C#
- Font Management
title: 'Zastępowanie czcionek Aspose: wykrywanie brakujących czcionek w dokumentach
  Word'
url: /pl/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Wykrywanie brakujących czcionek w dokumentach Word

Zastanawiałeś się kiedyś, dlaczego dokument Word wygląda niepoprawnie na innym komputerze? Często winowajcą jest brakująca czcionka, a **Aspose font substitution** jest narzędziem, które pozwala wykryć te luki, zanim staną się wizualną katastrofą. W tym samouczku przeprowadzimy Cię przez to, jak **detect missing fonts** w momencie **load a Word document**, a następnie **retrieve missing font** szczegóły, abyś mógł je naprawić lub zastąpić.

Omówimy wszystko, od konfiguracji callbacku ostrzeżeń po pobranie czystej listy brakujących czcionek. Po zakończeniu będziesz mieć gotowy do uruchomienia fragment C# informujący dokładnie, które czcionki nie zostały znalezione, oraz zrozumiesz, dlaczego ma to znaczenie dla integralności dokumentu.

---

## Wymagania wstępne – Co potrzebujesz przed rozpoczęciem

- **Aspose.Words for .NET** (v23.12 lub nowsza zalecana).  
- Środowisko programistyczne .NET (Visual Studio, Rider lub `dotnet` CLI).  
- Przykładowy plik DOCX, który celowo używa czcionki, której nie masz zainstalowanej — nazwij go `DocumentWithMissingFont.docx`.  
- Podstawowa znajomość C# — nic skomplikowanego, tylko możliwość uruchomienia aplikacji konsolowej.

Jeśli coś z tego jest Ci nieznane, zatrzymaj się i zainstaluj pakiet NuGet:

```bash
dotnet add package Aspose.Words
```

To wszystko. Bez dodatkowych czcionek, bez usług zewnętrznych.

---

## Krok 1: Załaduj dokument Word (i wywołaj sprawdzanie czcionek)

Pierwszą rzeczą, którą robisz, jest **load a Word document**. Aspose.Words parsuje plik i, jeśli nie może znaleźć odwołanej czcionki, dodaje ostrzeżenie *FontSubstitution*. Oto kod, który wykonuje ładowanie:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Dlaczego to ważne:** Wczesne ładowanie dokumentu daje Aspose możliwość przeszukania każdego fragmentu tekstu, stylu i osadzonego obiektu. Jeśli czcionka nie zostanie znaleziona w systemie lub w niestandardowym folderze czcionek, otrzymasz ostrzeżenie później.

---

## Krok 2: Dołącz callback ostrzeżeń, aby przechwycić zdarzenia podstawiania

Aspose.Words używa mechanizmu callback, aby informować Cię o problemach, takich jak brakujące czcionki. Przypisując implementację `IWarningCallback` do `doc.WarningCallback`, możesz przechwycić każde ostrzeżenie w momencie jego wystąpienia.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Wskazówka:** Możesz dołączyć wiele callbacków (np. logowanie, aktualizacje UI) poprzez ich opakowanie w wzorzec kompozytowy, ale w tym samouczku pojedynczy callback utrzymuje przejrzystość.

---

## Krok 3: Zaimplementuj callback ostrzeżenia o podstawianiu czcionek

Teraz definiujemy klasę, która faktycznie wykonuje pracę. Callback otrzymuje obiekt `WarningInfo`; filtrujemy pod kątem `WarningType.FontSubstitution` i zapisujemy opis do późniejszego użycia.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **Co się dzieje:** Gdy Aspose napotyka brakującą czcionkę, tworzy ostrzeżenie typu „Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” Nasz callback wypisuje tę linię i zapisuje ją.

---

## Krok 4: Przetwórz dokument (opcjonalnie) i zbierz brakujące czcionki

Jeśli potrzebujesz jedynie **detect missing fonts**, krok ładowania wystarczy — ostrzeżenia są generowane automatycznie. Jednak wielu programistów potrzebuje także **retrieve missing font** informacji po wykonaniu pewnych operacji (np. zapisywanie, konwersja). Poniżej wymuszamy małą operację — zapis do PDF — aby zapewnić emisję wszystkich ostrzeżeń, a następnie pobieramy zebrane komunikaty.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Oczekiwany wynik w konsoli** (przykład):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Zauważ, że każda linia wyraźnie podaje oryginalną czcionkę oraz zastępczą, którą wybrało Aspose. To jest sedno raportowania **aspose font substitution**.

---

## Krok 5: Zaawansowane – Używanie własnych źródeł czcionek w celu zmniejszenia podstawień

Czasami *masz* brakujące czcionki, ale nie znajdują się w domyślnym folderze systemowym. Aspose.Words pozwala wskazać własny katalog za pomocą `FontSettings`. Dodanie tego kroku może znacząco zmniejszyć liczbę ostrzeżeń o podstawianiu.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **Dlaczego to dodać?** Jeśli dystrybuujesz dokumenty na różnych maszynach, dołączenie wymaganych czcionek w znanym folderze zapewnia spójny wygląd wszędzie. Dodatkowo sprawia, że Twoja procedura **detect missing fonts** jest dokładniejsza, ponieważ Aspose najpierw sprawdza ten folder przed użyciem zastępczej czcionki.

---

## Kompletny działający przykład

Łącząc wszystko razem, oto gotowy do skopiowania program konsolowy. Zapisz go jako `Program.cs` i uruchom poleceniem `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**Co powinieneś zobaczyć:** Jeśli źródłowy DOCX odwołuje się do czcionek, których nie masz, konsola wypisze każdą linię podstawienia, a następnie zwięzłe podsumowanie. Jeśli wszystkie czcionki są dostępne, otrzymasz komunikat „No missing fonts were detected.”

---

## Częste pułapki i jak ich uniknąć

| Problem | Dlaczego się pojawia | Rozwiązanie |
|-------|----------------|-----|
| **Brak ostrzeżeń** | Dokument używa wyłącznie czcionek systemowych lub już dodałeś niestandardowy folder zawierający brakujące czcionki. | Sprawdź, czy DOCX rzeczywiście odwołuje się do niedostępnej czcionki. Możesz otworzyć go w Wordzie i zmienić akapit na rzadką czcionkę (np. „Papyrus”). |
| **Zduplikowane komunikaty** | Ta sama czcionka jest używana w wielu fragmentach, co powoduje wielokrotne ostrzeżenia. | Usuń duplikaty z listy przy pomocy `Distinct()`, jeśli potrzebujesz tylko unikalnego zestawu. |
| **Spadek wydajności przy dużych dokumentach** | Każde ostrzeżenie jest przetwarzane na wątku UI. | Uruchom ładowanie w zadaniu w tle lub użyj `Parallel.ForEach` do przetwarzania po zakończeniu. |
| **Nieprawidłowa czcionka zastępcza** | Domyślna czcionka zastępcza Aspose może nie pasować do Twojej marki. | Ustaw `FontSettings.SubstitutionSettings.DefaultFontName` na preferowaną czcionkę zastępczą (np. „Calibri”). |

---

## Rozszerzanie rozwiązania – Eksportowanie brakujących czcionek do JSON

Jeśli tworzysz usługę webową, która musi zgłaszać brakujące czcionki klientowi, serializacja listy jest prosta:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Teraz Twoje API może zwrócić czysty ładunek JSON, który może przetworzyć inny system.

---

## Zakończenie

W tym przewodniku pokazaliśmy **Aspose font substitution** od początku do końca: ładowanie dokumentu Word, dołączanie callbacku ostrzeżeń, przechwytywanie każdego zdarzenia *detect missing fonts* oraz ostatecznie **retrieve missing font** informacji do raportowania lub naprawy. Dodając opcjonalne niestandardowe foldery czcionek, możesz zmniejszyć listę podstawień, a kilka dodatkowych linii pozwala nawet wyeksportować wyniki jako JSON.

Pamiętaj, że integralność wizualna Twoich dokumentów zależy od używanych czcionek. Dzięki przedstawionej technice nie zostaniesz zaskoczony nieoczekiwaną czcionką zastępczą.  
Gotowy na kolejny krok? Spróbuj zintegrować tę logikę z większym potokiem przetwarzania dokumentów lub odkryj inne funkcje Aspose.Words, takie jak osadzanie czcionek (`doc.FontSettings.EmbeddedFonts`). Możliwości są nieograniczone, a Twoi użytkownicy podziękują Ci za dopracowany efekt.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}