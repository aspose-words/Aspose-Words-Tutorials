---
category: general
date: 2026-03-30
description: jak przechwytywać ostrzeżenia podczas ładowania pliku DOCX – dowiedz
  się, jak wykrywać brakujące czcionki, konfigurować ustawienia czcionek i ustawiać
  opcje ładowania w C#
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: pl
og_description: Jak przechwytywać ostrzeżenia podczas ładowania pliku DOCX – krok
  po kroku przewodnik wykrywania brakujących czcionek i konfigurowania ustawień czcionek
  w C#.
og_title: jak przechwytywać ostrzeżenia – skonfiguruj opcje ładowania brakujących
  czcionek
tags:
- Aspose.Words
- C#
- Font management
title: jak przechwytywać ostrzeżenia – skonfiguruj opcje ładowania brakujących czcionek
url: /pl/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# jak przechwytywać ostrzeżenia – konfigurowanie opcji ładowania dla brakujących czcionek

Zastanawiałeś się kiedyś **jak przechwytywać ostrzeżenia**, które pojawiają się, gdy dokument próbuje użyć czcionki, której nie masz zainstalowanej? To sytuacja, która sprawia trudności wielu programistom pracującym z bibliotekami do przetwarzania tekstu, szczególnie gdy musisz **wykrywać brakujące czcionki**, zanim zepsują one Twój pipeline eksportu PDF.  

W tym tutorialu pokażemy praktyczne, gotowe do uruchomienia rozwiązanie, które **konfiguruje ustawienia czcionek**, **ustawia opcje ładowania** i wypisuje każde ostrzeżenie o substytucji na konsolę. Po zakończeniu będziesz dokładnie wiedział, **jak obsługiwać brakujące czcionki** w sposób zapewniający stabilność aplikacji i zadowolenie użytkowników.

## Co się nauczysz

- Jak **ustawić opcje ładowania**, aby biblioteka zgłaszała problemy z czcionkami zamiast cicho je podmieniać.  
- Dokładne kroki **konfiguracji ustawień czcionek** w celu przechwytywania ostrzeżeń.  
- Sposoby **wykrywania brakujących czcionek** programowo i reagowania na nie.  
- Kompletny przykład C# typu copy‑paste, działający z najnowszą wersją Aspose.Words for .NET (v24.10 w momencie pisania).  
- Wskazówki, jak rozbudować rozwiązanie o logowanie ostrzeżeń, fallback do własnych czcionek lub przerwanie przetwarzania, gdy krytyczne czcionki są nieobecne.

> **Wymaganie wstępne:** Musisz mieć zainstalowany pakiet NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`). Nie są wymagane inne zewnętrzne zależności.

---

## Krok 1: Importuj przestrzenie nazw i przygotuj projekt

Najpierw dodaj niezbędne dyrektywy `using`. To nie jest tylko szablon; informuje kompilator, gdzie znajdują się `LoadOptions`, `FontSettings` i `Document`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **Pro tip:** Jeśli używasz .NET 6+, możesz włączyć *global using* statements, aby nie powtarzać tych linii w każdym pliku.

---

## Krok 2: Ustaw opcje ładowania i włącz ostrzeżenia o substytucji czcionek

Sednem **jak przechwytywać ostrzeżenia** jest obiekt `LoadOptions`. Tworząc nową instancję `FontSettings` i podłączając obsługę zdarzenia do `SubstitutionWarning`, informujesz bibliotekę, aby zgłaszała każde nieodnalezienie żądanej czcionki.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**Dlaczego to ważne:** Bez subskrypcji zdarzenia Aspose.Words cicho przełącza się na domyślną czcionkę i nigdy nie dowiesz się, które glify zostały podmienione. Nasłuchując `SubstitutionWarning`, otrzymujesz pełny ślad audytu — kluczowy w środowiskach o wysokich wymaganiach zgodności.

---

## Krok 3: Załaduj dokument przy użyciu skonfigurowanych opcji

Teraz, gdy ostrzeżenia są podłączone, załaduj swój plik DOCX (lub inny obsługiwany format) przy pomocy `loadOptions`, które właśnie przygotowałeś. Konstruktor `Document` natychmiast uruchomi logikę sprawdzania czcionek.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

Jeśli plik odwołuje się, powiedzmy, do *„Comic Sans MS”* na maszynie, która ma tylko *„Arial”*, zobaczysz coś w stylu:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

Ten wiersz jest wypisywany bezpośrednio na konsolę dzięki wcześniej podłączonemu handlerowi.

---

## Krok 4: Zweryfikuj i zareaguj na przechwycone ostrzeżenia

Przechwycenie ostrzeżeń to dopiero połowa walki; często trzeba zdecydować, co zrobić dalej. Poniżej szybki wzorzec, który zapisuje ostrzeżenia w liście do późniejszej analizy — idealny, jeśli chcesz je zalogować do pliku lub przerwać import, gdy brakują krytyczne czcionki.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**Obsługa przypadków brzegowych:**  
- **Wiele brakujących czcionek:** Lista będzie zawierała po jeden wpis na każdą substytucję, więc możesz iterować i tworzyć szczegółowy raport.  
- **Własne czcionki zastępcze:** Jeśli masz własne pliki czcionek, dodaj je do `FontSettings` przed załadowaniem: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. Ostrzeżenia pokażą wtedy własny fallback zamiast domyślnego systemowego.  

---

## Krok 5: Pełny działający przykład (gotowy do kopiowania)

Łącząc wszystko razem, oto samodzielna aplikacja konsolowa, którą możesz skompilować i uruchomić od razu.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**Oczekiwany wynik w konsoli** (gdy DOCX odwołuje się do brakującej czcionki):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

Jeśli brakująca czcionka jest *krytyczna*, np. „Times New Roman”, zobaczysz komunikat o przerwaniu zamiast tego.

---

## Częste pytania i pułapki

| Pytanie | Odpowiedź |
|----------|--------|
| **Czy muszę wywołać `SetFontsFolder`, aby przechwycić ostrzeżenia?** | Nie. Zdarzenie ostrzeżenia działa z domyślnymi czcionkami systemowymi. Użyj `SetFontsFolder` tylko wtedy, gdy chcesz dodać dodatkowe czcionki zastępcze. |
| **Czy to zadziała na .NET Core / .NET 5+?** | Absolutnie. Aspose.Words 24.10 obsługuje wszystkie nowoczesne środowiska .NET. Upewnij się tylko, że pakiet NuGet odpowiada Twojemu docelowemu frameworkowi. |
| **Co zrobić, jeśli chcę logować ostrzeżenia do pliku zamiast na konsolę?** | Zamień `Console.WriteLine(msg);` na wywołanie dowolnego frameworka logującego, np. `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **Czy mogę wyciszyć ostrzeżenia dla konkretnych czcionek?** | Tak. Wewnątrz obsługi zdarzenia możesz filtrować: `if (e.FontName == "SomeFont") return;`. Daje to precyzyjną kontrolę. |
| **Czy istnieje sposób, aby traktować brakujące czcionki jako błędy?** | Rzuć ręcznie wyjątek wewnątrz handlera, gdy spełniony zostanie określony warunek, lub ustaw flagę i przerwij po konstrukcji `Document`, jak pokazano w przykładzie. |

---

## Podsumowanie

Masz teraz solidny, gotowy do produkcji wzorzec **jak przechwytywać ostrzeżenia**, które pojawiają się podczas ładowania dokumentów z brakującymi czcionkami. Dzięki **wykrywaniu brakujących czcionek**, **konfiguracji ustawień czcionek** i **ustawianiu opcji ładowania** w odpowiedni sposób, uzyskasz pełną widoczność zdarzeń substytucji czcionek i będziesz mógł zdecydować, czy je logować, używać fallbacku, czy przerywać proces.  

Zrób kolejny krok, integrując tę logikę z pipeline'em konwersji do PDF, dodając własne czcionki zastępcze lub przekazując listę ostrzeżeń do systemu monitoringu. Podejście skaluje się od małych narzędzi po usługi przetwarzania dokumentów klasy enterprise.

---

### Dalsza lektura i kolejne kroki

- **Zbadaj więcej funkcji FontSettings** – osadzanie własnych czcionek, kontrola kolejności fallbacku i kwestie licencyjne.  
- **Połącz z konwersją do PDF** – po przechwyceniu ostrzeżeń wywołaj `doc.Save("output.pdf");` i sprawdź, czy PDF używa oczekiwanych czcionek.  
- **Automatyzuj testy** – napisz testy jednostkowe, które ładują dokumenty ze znanymi brakującymi czcionkami i asercjonują, że lista ostrzeżeń zawiera oczekiwane komunikaty.  

Jeśli napotkasz jakiekolwiek problemy lub masz pomysły na ulepszenia, zostaw komentarz. Szczęśliwego kodowania!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}