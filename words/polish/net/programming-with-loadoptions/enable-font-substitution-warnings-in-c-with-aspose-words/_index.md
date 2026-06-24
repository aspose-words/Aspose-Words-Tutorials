---
category: general
date: 2026-06-20
description: Włącz ostrzeżenia o podstawianiu czcionek w C# przy użyciu Aspose.Words.
  Dowiedz się, jak skonfigurować LoadOptions, przechwytywać ostrzeżenia i skutecznie
  obsługiwać brakujące czcionki.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: pl
og_description: Włącz ostrzeżenia o podstawianiu czcionek w C# z Aspose.Words. Ten
  przewodnik pokazuje, jak skonfigurować LoadOptions, odczytać WarningInfo i wyświetlić
  komunikaty o brakujących czcionkach.
og_title: Włącz ostrzeżenia o zamianie czcionek w C# – Kompletny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Włącz ostrzeżenia o podstawianiu czcionek w C# z Aspose.Words
url: /pl/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Włącz ostrzeżenia o podstawianiu czcionek w C# z Aspose.Words

Zastanawiałeś się kiedyś, jak **włączyć ostrzeżenia o podstawianiu czcionek**, gdy dokument Word odwołuje się do czcionki, której nie ma zainstalowanej na serwerze? Nie jesteś sam. Brakujące czcionki mogą po cichu psuć układ generowanych PDF‑ów lub obrazów, a jedynym sposobem, aby wykryć to wcześnie, jest nasłuchiwanie ostrzeżeń emitowanych przez Aspose.Words.

W tym samouczku przeprowadzimy Cię przez praktyczny przykład, który pokaże dokładnie, jak włączyć te ostrzeżenia, pobrać je z kolekcji `WarningInfo` i wypisać czytelne komunikaty na konsolę. Po zakończeniu będziesz wiedział, jak skonfigurować **Aspose.Words LoadOptions**, obsłużyć **C# font substitution warnings** i utrzymać swoją linię przetwarzania dokumentów w pełnej gotowości.

Poruszymy także kilka przypadków brzegowych — co się stanie, jeśli wyciszysz ostrzeżenia lub jeśli będziesz musiał je logować zamiast wypisywać — oraz udostępnimy kompletny, gotowy do skopiowania kod, działający z najnowszą wersją Aspose.Words for .NET (od wersji 24.10).

## Czego będziesz potrzebować

- .NET 6.0 lub nowszy (kod działa również na .NET Framework 4.7+)
- Odwołanie NuGet do `Aspose.Words` (zainstaluj poleceniem `dotnet add package Aspose.Words`)
- Plik Word, który odwołuje się do czcionki, której **nie** masz zainstalowanej (np. `DocumentWithMissingFont.docx`)
- Porządne IDE (Visual Studio, Rider lub VS Code)

To wszystko — żadnych dodatkowych usług, żadnych zamkniętych narzędzi. Gotowy? Zanurzmy się.

## Krok 1: Włącz ostrzeżenia o podstawianiu czcionek

Pierwszą rzeczą, którą musisz zrobić, jest poinformowanie Aspose.Words, że chcesz być powiadamiany, gdy podstawia brakującą czcionkę. Robi się to poprzez właściwość `FontSettings` obiektu `LoadOptions`. Domyślnie ostrzeżenia są **wyłączone**, aby API było ciche, więc musimy przełączyć przełącznik sami.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Dlaczego to działa:** Gdy `FontSettings` nie jest `null`, biblioteka automatycznie wypełnia `Document.WarningInfo` wpisami `WarningType.FontSubstitution`, które napotka podczas ładowania dokumentu. To jak włączenie „trybu debugowania” dla czcionek.

## Krok 2: Załaduj dokument z skonfigurowanymi opcjami

Teraz, gdy kolekcja ostrzeżeń jest aktywna, załaduj dokument używając przygotowanego `LoadOptions`. Jeśli dokument zawiera brakującą czcionkę, Aspose.Words podstawi zamiennik i doda ostrzeżenie do listy `WarningInfo`.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Porada:** Jeśli przetwarzasz wiele plików w pętli, używaj tego samego egzemplarza `LoadOptions` — utworzenie go raz oszczędza kilka milisekund na iterację.

## Krok 3: Przejdź przez WarningInfo i wyświetl komunikaty o podstawianiu czcionek

Po załadowaniu dokumentu kolekcja `WarningInfo` zawiera każde ostrzeżenie, które wystąpiło podczas ładowania. Interesują nas tylko wpisy `WarningType.FontSubstitution`, więc filtrujemy je odpowiednio.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Uruchomienie powyższego fragmentu przeciwko dokumentowi odwołującemu się do brakującej czcionki „Papyrus” może dać wynik podobny do:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

To są **komunikaty o podstawianiu czcionek**, których szukałeś — jasne, konkretne i gotowe do zalogowania lub wysłania do systemu alarmowego.

## Pełny działający przykład

Poniżej znajduje się samodzielny program konsolowy, który łączy wszystkie elementy. Skopiuj‑wklej go do nowego projektu `.csproj` i naciśnij **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Oczekiwany wynik

Jeśli dokument odwołuje się do czcionek, które nie są zainstalowane, zobaczysz coś podobnego do:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Jeśli wszystkie czcionki są dostępne na maszynie, program po prostu wypisze:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Typowe pułapki i porady ekspertów

| Problem | Dlaczego się pojawia | Jak naprawić / uniknąć |
|---------|----------------------|------------------------|
| **Ostrzeżenia znikają** | Wyczyściłeś `FontSettings` lub użyłeś `LoadOptions` bez niej. | Zawsze twórz `FontSettings`, nawet jeśli nie modyfikujesz żadnych właściwości. |
| **Zbyt wiele ostrzeżeń** | Dokument używa wielu egzotycznych czcionek. | Rozważ dodanie własnego folderu z czcionkami do `FontSettings` za pomocą `SetFontsFolder`, aby zmniejszyć liczbę podstawień. |
| **Spadek wydajności w pętli** | Ponowne tworzenie `LoadOptions` w każdej iteracji dodaje narzut. | Ponownie używaj jednej instancji `LoadOptions` dla wszystkich dokumentów. |
| **Brak wyjścia na konsolę** | Aplikacja GUI ignoruje `Console.WriteLine`. | Przekieruj ostrzeżenia do loggera (`ILogger`) lub zapisz je do pliku. |

### Obsługa ostrzeżeń w rzeczywistym serwisie

W API webowym prawdopodobnie nie chcesz pisać do konsoli. Zamiast tego, przekaż ostrzeżenia do strukturalnego logu:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

W ten sposób zachowujesz **obsługę ostrzeżeń dokumentu**, jednocześnie utrzymując usługę w czystości.

## Rozszerzanie przykładu

- **Przechwytywanie innych typów ostrzeżeń** (np. `WarningType.UnknownFileFormat`) poprzez usunięcie filtru `if`.
- **Zapis raportu** ze wszystkimi ostrzeżeniami do JSON‑a dla dalszej analizy.
- **Wymuszenie konkretnej czcionki zapasowej** poprzez ustawienie `FontSettings.SubstitutionSettings.DefaultFontName`.

Wszystko to naturalne rozszerzenia po opanowaniu **włączania ostrzeżeń o podstawianiu czcionek**.

## Podsumowanie

Pokazaliśmy, jak **włączyć ostrzeżenia o podstawianiu czcionek** w C# przy użyciu Aspose.Words, od konfiguracji `LoadOptions` po iterację po `WarningInfo` i wypisywanie przyjaznych komunikatów. Postępując zgodnie z powyższymi krokami, możesz zabezpieczyć swoje pipeline’y przetwarzania dokumentów przed cichymi zmianami układu spowodowanymi brakującymi czcionkami.

Następnie spróbuj dodać własny folder czcionek, logować ostrzeżenia do pliku lub nawet wysyłać je do dashboardu monitorującego. Ten sam wzorzec działa w każdym scenariuszu **obsługi ostrzeżeń dokumentu**, niezależnie od tego, czy konwertujesz do PDF, renderujesz obrazy, czy wykonujesz mail‑merge.

Masz pytania dotyczące **C# font substitution warnings** lub chcesz podzielić się sprytnym obejściem? zostaw komentarz poniżej — miłego kodowania!


## Co powinieneś nauczyć się dalej?


Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}