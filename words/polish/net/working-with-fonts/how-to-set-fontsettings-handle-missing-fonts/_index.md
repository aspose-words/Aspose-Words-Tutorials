---
category: general
date: 2026-05-29
description: Dowiedz się, jak ustawić FontSettings w Aspose.Words i elegancko obsługiwać
  brakujące czcionki. Przewodnik krok po kroku z kompletnym kodem i najlepszymi praktykami.
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: pl
og_description: Jak ustawić FontSettings w Aspose.Words i szybko obsłużyć brakujące
  czcionki. Skorzystaj z tego przewodnika, aby uzyskać kompletną, gotową do uruchomienia
  rozwiązanie.
og_title: Jak ustawić FontSettings – obsługa brakujących czcionek
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: Jak ustawić FontSettings – Obsługa brakujących czcionek
url: /pl/net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak ustawić FontSettings – Obsługa brakujących czcionek

Zastanawiałeś się kiedyś **jak ustawić FontSettings** podczas pracy z Aspose.Words i nagle natrafiłeś na dokument, który odwołuje się do czcionki, której nie masz zainstalowanej? To częsty problem, szczególnie przy przetwarzaniu plików dostarczonych przez klienta na serwerze, który ma tylko minimalny zestaw czcionek. Dobra wiadomość? Możesz wykrywać te braki i **obsługiwać brakujące czcionki** bez awarii aplikacji czy generowania nieestetycznych PDF‑ów.

W tym samouczku przeprowadzimy Cię przez realistyczny scenariusz: wczytanie pliku DOCX, który wymaga „Calibri”, podczas gdy Twój kontener Linux zawiera tylko „DejaVu Sans”. Zobaczysz dokładnie, jak skonfigurować FontSettings, subskrybować ostrzeżenia o podstawianiu oraz dostarczyć czcionki zapasowe, aby dokument renderował się tak, jak zamierzył autor. Bez zbędnych wstępów — po prostu kod, który możesz od razu wkleić do swojego projektu.

## Prerequisites

- .NET 6.0 lub nowszy (API działa tak samo na .NET Framework 4.7+)
- Aspose.Words for .NET 23.10 lub nowszy (nazwa pakietu NuGet to `Aspose.Words`)
- Podstawowe środowisko programistyczne C# (Visual Studio, Rider lub VS Code)

Jeśli masz te elementy, zanurzmy się.

## Step 1: Create FontSettings and Listen for Substitution Events

Serce rozwiązania stanowi obiekt `FontSettings`. Przez podłączenie obsługi do zdarzenia `FontSubstitutionWarning` otrzymasz bieżący raport za każdym razem, gdy Aspose.Words będzie musiał zastąpić brakującą czcionkę.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Subscribe to the warning event so we can log substitutions
fontSettings.FontSubstitutionWarning += (sender, e) =>
{
    // e.FontFamilyName – the name requested in the source document
    // e.SubstitutedFontFamilyName – the font actually used by the engine
    Console.WriteLine(
        $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
};
```

**Dlaczego to ważne:**  
Gdy silnik nie może znaleźć *Calibri*, może cicho przejść na *Arial*. Słuchając ostrzeżenia, zachowujesz przejrzysty ślad audytu — idealny do debugowania lub raportowania zgodności.

> **Pro tip:** Jeśli uruchamiasz to na serwerze CI, przekieruj wyjście do pliku logu, aby móc później przejrzeć, które czcionki były brakujące po przetworzeniu partii.

## Step 2: Attach FontSettings to LoadOptions

`LoadOptions` jest bramą kontrolującą sposób parsowania dokumentu. Przypisując do niego skonfigurowane `FontSettings`, każde kolejne wczytanie `Document` będzie respektować naszą logikę podstawiania.

```csharp
// Step 2 – wire FontSettings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Co się dzieje pod maską?**  
Podczas wywołania konstruktora `Document` Aspose.Words odczytuje XML DOCX‑a, rozwiązuje odwołania do czcionek i — jeśli czcionka nie zostanie znaleziona — wyzwala ostrzeżenie, które ustawiliśmy wcześniej. Bez tego hakowania nigdy nie dowiesz się, że doszło do podstawienia.

## Step 3: Load the Document and (Optionally) Define Fallback Fonts

Teraz w końcu wczytujemy plik do pamięci. Jeśli masz już folder z czcionkami zapasowymi (np. katalog czcionek OpenType dostarczany razem z aplikacją), wskaż `FontSettings`, gdzie ich szukać. Ten krok jest opcjonalny, ale najczęściej najczystszym sposobem na **obsługę brakujących czcionek**.

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**Uwaga na przypadki brzegowe:**  
Jeśli dokument zawiera własną czcionkę osadzoną jako strumień binarny, Aspose.Words użyje jej automatycznie — nie będzie potrzebne podstawienie. Ostrzeżenie pojawia się wyłącznie dla *brakujących* czcionek systemowych.

### Verifying the Result

Po wczytaniu możesz zapisać dokument jako PDF lub Word, aby potwierdzić, że wszystko wygląda poprawnie.

```csharp
// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

Po uruchomieniu programu w konsoli pojawią się linie podobne do:

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

Jeśli zobaczysz te komunikaty, udało Ci się **obsłużyć brakujące czcionki** i wiesz dokładnie, które podstawienia miały miejsce.

## Step 4: Advanced – Custom Font Substitution Rules (Optional)

Czasami potrzebne są deterministyczne mapowania, np. zawsze zamieniać *Times New Roman* na *Liberation Serif*. Można to osiągnąć przy pomocy `FontSettings.SubstitutionTable`.

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });
```

**Po co to robić?**  
Jawne reguły dają kontrolę nad typografią, zapewniając spójność marki w generowanych PDF‑ach, szczególnie gdy tworzysz materiały marketingowe.

## Common Pitfalls & How to Avoid Them

| Pitfall | Symptom | Fix |
|---------|---------|-----|
| **No warning output** | Myślisz, że czcionki są w porządku, ale dokument wygląda niepoprawnie. | Upewnij się, że `FontSubstitutionWarning` jest podłączone **przed** wczytaniem dokumentu. |
| **Fallback folder not scanned** | Podstawienia wciąż spadają na domyślne czcionki systemowe. | Wywołaj `SetFontsFolder(path, true)` z drugim argumentem `true`, aby przeszukać podfoldery. |
| **Performance hit on large batches** | Ładowanie 10 k dokumentów staje się wolne. | Cache’uj jedną instancję `FontSettings` i używaj jej wielokrotnie; unikaj tworzenia nowej przy każdym ładowaniu. |
| **Embedded fonts ignored** | Oczekiwałeś użycia własnej czcionki osadzonej, ale nastąpiło podstawienie. | Sprawdź, czy źródłowy DOCX rzeczywiście osadza czcionkę (Word → Plik → Informacje → Czcionki). |

## Full Working Example

Poniżej kompletny, gotowy do skopiowania program. Demonstruje wszystko — od obsługi zdarzeń po zapis końcowego PDF‑a.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings with a warning handler
        FontSettings fontSettings = new FontSettings();
        fontSettings.FontSubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
        };

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // 2️⃣ Attach FontSettings to LoadOptions
        LoadOptions loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**Przykładowe wyjście w konsoli** (przykład):

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

Uruchom program, otwórz `Output.pdf` i zobaczysz tekst wyrenderowany czcionkami zapasowymi — bez pustych kwadratów, bez awarii.

## Conclusion

Masz teraz solidny, gotowy do produkcji wzorzec **jak ustawić FontSettings** w Aspose.Words i **elegancko obsługiwać brakujące czcionki**. Dzięki podłączeniu zdarzenia `FontSubstitutionWarning`, wskazaniu katalogu czcionek zapasowych oraz (w razie potrzeby) zdefiniowaniu wyraźnych reguł podstawiania, zyskujesz pełną widoczność i kontrolę nad typografią w zautomatyzowanych pipeline’ach dokumentów.

Co dalej? Spróbuj dodać własną kolekcję czcionek specyficznych dla marki lub zbadaj API `FontSourceBase`, aby ładować czcionki z bazy danych lub chmury. Te same zasady mają zastosowanie — wystarczy podłączyć inny źródło do `FontSettings`.

Masz pytania o przypadki brzegowe, np. obsługę skryptów od prawej do lewej lub czcionek emoji? zostaw komentarz poniżej i powodzenia w kodowaniu!

## What Should You Learn Next?

- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}