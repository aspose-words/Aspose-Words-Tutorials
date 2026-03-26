---
category: general
date: 2026-03-25
description: Utwórz wywołanie zwrotne ostrzeżenia, aby załadować dokument Word i wykryć
  brakujące czcionki. Dowiedz się, jak skonfigurować ustawienia czcionek w Aspose.Words
  dla .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: pl
og_description: Utwórz wywołanie zwrotne ostrzeżenia przy ładowaniu dokumentu Word,
  wykrywając brakujące czcionki. Ten przewodnik pokazuje, jak skonfigurować ustawienia
  czcionek w Aspose.Words.
og_title: Utwórz wywołanie zwrotne ostrzeżenia – Wczytaj dokument Word i wykryj brakujące
  czcionki
tags:
- Aspose.Words
- C#
- Font handling
title: Utwórz wywołanie zwrotne ostrzeżenia przy ładowaniu dokumentów Word – Kompletny
  przewodnik
url: /pl/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz callback ostrzeżenia – Ładuj dokument Word i wykrywaj brakujące czcionki

Czy kiedykolwiek potrzebowałeś **utworzyć callback ostrzeżenia** podczas ładowania dokumentu Word i zastanawiałeś się, dlaczego niektóre czcionki po prostu znikają? Nie jesteś jedyny. W wielu aplikacjach korporacyjnych brakujące czcionki powodują katastrofy układu, a bez odpowiedniego callbacku możesz nigdy nie zauważyć problemu.  

Dobra wiadomość? Z Aspose.Words for .NET możesz **załadować dokument Word**, **wykrywać brakujące czcionki** i **konfigurować ustawienia czcionek** w kilku zgrabnych linijkach kodu. W tym tutorialu przeprowadzimy Cię przez kompletny, działający przykład, wyjaśnimy, dlaczego każdy element ma znaczenie, i pokażemy, jak zweryfikować, że callback ostrzeżenia wykonuje swoją pracę.

> **Co wyniesiesz z tego tutorialu**  
> * Pełny program w C#, który ładuje plik DOCX, raportuje wszelkie podstawienia czcionek i pozwala dostosować ścieżki wyszukiwania czcionek.  
> * Zrozumienie klas `FontSettings`, `LoadOptions` oraz `IWarningCallback`.  
> * Wskazówki dotyczące obsługi przypadków brzegowych, takich jak osadzone czcionki czy systemowe foldery czcionek.

---

## Wymagania wstępne

- .NET 6+ (lub .NET Framework 4.7.2+) z kompilatorem C#.  
- Pakiet NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Przykładowy plik Word (`input.docx`), który używa przynajmniej jednej czcionki niezainstalowanej na maszynie (np. *Calibri Light* w minimalnym kontenerze Windows).  
- Podstawowa znajomość aplikacji konsolowych w C#.

Nie są wymagane dodatkowe biblioteki; wszystko znajduje się w obrębie Aspose.Words.

---

## Krok 1: Utwórz callback ostrzeżenia, aby wykrywać brakujące czcionki

**Primary** element tej układanki to klasa implementująca `IWarningCallback`. Aspose.Words wywoła ten callback, gdy napotka sytuację wymagającą ostrzeżenia – najczęściej jest to podstawienie czcionki.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Dlaczego to ważne** – Bez callbacku musiałbyś przeszukiwać logi po fakcie. Obsługując ostrzeżenia w czasie rzeczywistym, możesz zdecydować, czy przerwać ładowanie, zastąpić brakującą czcionkę zapasową, czy po prostu zalogować problem do późniejszej analizy.

---

## Krok 2: Skonfiguruj FontSettings dla własnego zarządzania czcionkami

Zanim faktycznie załadujemy dokument, możemy poinformować Aspose.Words, gdzie szukać czcionek nieobecnych w systemie. W tym miejscu wkracza `FontSettings`.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Dlaczego to ważne** – Wskazując Aspose.Words folder zawierający brakujące czcionki, często unikamy podstawień całkowicie. Gdy nie jest to możliwe, rozsądny domyślny wybór (np. *Arial*) utrzymuje czytelność dokumentu.

---

## Krok 3: Ładuj dokument Word z skonfigurowanym callbackiem ostrzeżenia

Teraz łączymy wszystko: tworzymy `LoadOptions`, podpinamy nasze `FontSettings` i `FontWarningHandler`, a na końcu ładujemy dokument.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Dlaczego to ważne** – `LoadOptions` to jedyne miejsce, w którym konfigurujesz *sposób* odczytu dokumentu. Dostarczając zarówno konfigurację czcionek, jak i callback ostrzeżenia, zapewniamy, że każda brakująca czcionka zostanie zarówno wyszukiwana we właściwych miejscach, **jak i** natychmiast zgłoszona.

---

## Krok 4: Zweryfikuj wynik – co powinieneś zobaczyć?

Uruchom program w konsoli. Jeśli `input.docx` używa czcionki, która nie jest zainstalowana i nie znajduje się w `C:\SharedFonts`, zobaczysz coś w stylu:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Jeśli wszystkie czcionki są dostępne, linia ostrzeżenia po prostu się nie pojawi. Ta natychmiastowa pętla sprzężenia zwrotnego jest nieoceniona w zautomatyzowanych pipeline'ach przetwarzania dokumentów, gdzie ciche podstawienia czcionek mogą naruszyć wytyczne brandingowe.

---

## Krok 5: Częste pułapki i wskazówki najlepszych praktyk

| Pułapka | Jak jej uniknąć |
|---------|-----------------|
| **Zapomniano dodać referencję `Aspose.Words.Fonts`** | Upewnij się, że na początku masz `using Aspose.Words.Fonts;`; w przeciwnym razie kompilator zgłosi brakujące typy. |
| **Ścieżka do folderu czcionek jest nieprawidłowa** | Podwójnie sprawdź ścieżkę i ustaw `recursive: true`, jeśli masz podfoldery. Użyj `Path.GetFullPath` do debugowania. |
| **Wiele callbacków ostrzeżeń** | Aspose.Words honoruje tylko ostatni przypisany `WarningCallback`. Trzymaj pojedynczy handler, który deleguje, jeśli potrzebna jest bardziej złożona logika. |
| **Uruchamianie na serwerze bez UI** | Zapis do konsoli jest w porządku, ale w aplikacjach webowych warto logować do pliku lub systemu monitoringu zamiast `Console.WriteLine`. |
| **Duże dokumenty powodują spadek wydajności** | Ponownie używaj jednej instancji `FontSettings` przy wielu ładowaniach; tworzenie jej wielokrotnie może być kosztowne. |

**Pro tip:** Jeśli potrzebujesz *zbierać* ostrzeżenia do późniejszej analizy, przechowuj je w `List<string>` wewnątrz handlera zamiast od razu wypisywać.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Możesz potem przejrzeć `handler.Messages` po załadowaniu dokumentu.

---

## Krok 6: Rozszerzanie rozwiązania – co zrobić, jeśli muszę osadzić czcionkę zapasową?

Czasami chcesz, aby brakująca czcionka była *osadzona* w wyjściowym PDF, tak aby downstreamowi odbiorcy widzieli dokładny wygląd. Po załadowaniu dokumentu możesz wymusić osadzenie:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Ten fragment pokazuje, jak to samo **configure font settings** podejście można rozszerzyć poza samym ładowaniem.

---

## Pełny przykład gotowy do uruchomienia

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do nowego projektu aplikacji konsolowej. Zawiera wszystkie elementy omówione powyżej.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Oczekiwany wynik** (gdy występuje brakująca czcionka):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

Jeśli nie nastąpi podstawienie, pojawią się wyłącznie komunikaty sukcesu.

---

## Zakończenie

Właśnie **utworzyliśmy callback ostrzeżenia**, który niezawodnie **wykrywa brakujące czcionki** podczas **ładowania dokumentu Word** przy użyciu Aspose.Words, i pokazaliśmy, jak **konfigurować ustawienia czcionek**, aby kontrolować, gdzie biblioteka szuka czcionek i jaką zapasową używać. Łącząc `FontSettings` i `LoadOptions`, zyskujesz pełną widoczność problemów związanych z czcionkami — koniec z cichymi błędami układu.

Co dalej? Spróbuj zamienić `FontWarningHandler` na logger zapisujący do bazy danych lub poeksperymentuj z **regułami podstawiania czcionek**, aby mapować konkretne brakujące czcionki na zatwierdzone przez markę alternatywy. Możesz także zbadać **dynamiczne ładowanie czcionek** z chmury, jeśli Twoja aplikacja działa w środowisku kontenerowym.

Masz pytania dotyczące konkretnego przypadku brzegowego — np. obsługi funkcji OpenType lub pracy z zaszyfrowanymi plikami DOCX? Zostaw komentarz poniżej i powodzenia w kodowaniu!  

---

![Create warning callback diagram](https://example.com/images/create-warning-callback.png "Create warning callback diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}