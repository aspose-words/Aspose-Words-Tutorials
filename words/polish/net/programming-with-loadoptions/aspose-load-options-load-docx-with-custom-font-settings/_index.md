---
category: general
date: 2025-12-29
description: Opcje ładowania Aspose umożliwiają wczytywanie plików DOCX z dostosowywaniem
  ustawień czcionek i wykrywaniem brakujących czcionek. Dowiedz się, jak ładować pliki
  docx z pełną kontrolą.
draft: false
keywords:
- aspose load options
- how to load docx
- custom font settings
- load word document
- detect missing fonts
language: pl
og_description: Opcje ładowania Aspose umożliwiają wczytywanie plików DOCX z dostosowywaniem
  ustawień czcionek i wykrywaniem brakujących czcionek. Dowiedz się, jak wczytać docx
  z pełną kontrolą.
og_title: Opcje ładowania Aspose – Ładowanie DOCX z niestandardowymi ustawieniami
  czcionki
tags:
- Aspose.Words
- C#
- Document Processing
title: Opcje ładowania Aspose – Ładowanie DOCX z niestandardowymi ustawieniami czcionek
url: /pl/net/programming-with-loadoptions/aspose-load-options-load-docx-with-custom-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Opcje ładowania Aspose – Ładowanie DOCX z niestandardowymi ustawieniami czcionek

Zastanawiałeś się kiedyś, jak wczytać plik DOCX w C# bez problemów z brakującymi czcionkami? Nie jesteś sam. **Opcje ładowania Aspose** dają Ci możliwość precyzyjnego kontrolowania, w jaki sposób dokument Word jest otwierany, umożliwiając ustawienie niestandardowych ustawień czcionek oraz wykrycie brakujących czcionek, zanim staną się problemem.

W tym samouczku przejdziemy krok po kroku przez cały proces ładowania DOCX przy użyciu Aspose.Words, skonfigurujemy **niestandardowe ustawienia czcionek** oraz podłączymy wywołanie zwrotne ostrzeżenia, które poinformuje Cię, które czcionki są brakujące. Po zakończeniu będziesz mógł **ładować dokumenty Word** z pełnym przekonaniem, niezależnie od tego, jakich czcionek użył pierwotny autor.

> **Wymaganie wstępne** – Potrzebujesz Aspose.Words dla .NET (najnowsza wersja) dodaną do projektu oraz podstawowej znajomości C#. Nie są wymagane żadne inne biblioteki.

## Czego się nauczysz

- Jak utworzyć obiekt `LoadOptions` i podłączyć wywołanie zwrotne ostrzeżenia.  
- Jak skonfigurować `FontSettings` dla **niestandardowych ustawień czcionek**.  
- Jak faktycznie **załadować docx** i zweryfikować, że brakujące czcionki są zgłaszane.  
- Porady dotyczące obsługi przypadków brzegowych, takich jak osadzone czcionki czy foldery czcionek dostępne w sieci.

## Krok 1: Zainstaluj Aspose.Words i przygotuj projekt

Na początek upewnij się, że Aspose.Words jest zainstalowany. Najłatwiej zrobić to przez NuGet:

```bash
dotnet add package Aspose.Words
```

Po dodaniu pakietu utwórz nowy projekt konsolowy C# (lub wstaw kod do istniejącej aplikacji). Nasz kod działa z .NET 6+ oraz .NET Framework 4.7.2+, więc masz pokrycie w obu przypadkach.

> **Pro tip:** Jeśli tworzysz aplikację na .NET Core, dodaj `using System;` na początku pliku; IDE zazwyczaj wstawi to automatycznie.

## Krok 2: Skonfiguruj Opcje ładowania Aspose z wywołaniem zwrotnym ostrzeżenia

Teraz przechodzimy do sedna – **opcji ładowania Aspose**. Klasa `LoadOptions` pozwala dostosować sposób parsowania dokumentu. Użyjemy jej, aby:

1. Podłączyć wywołanie zwrotne, które uruchamia się za każdym razem, gdy loader nie może znaleźć żądanej czcionki.  
2. Przypisać instancję `FontSettings`, którą później można dostosować do **niestandardowych ustawień czcionek**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Step 2.1 – Create LoadOptions and a FontSettings object
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // FontSettings is where you control where Aspose looks for fonts.
        // You could point it at a folder, a collection, or even a stream.
        FontSettings fontSettings = new FontSettings();

        // --------------------------------------------------------------
        // Step 2.2 – Register a warning callback to detect missing fonts
        // --------------------------------------------------------------
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            // This will be called for each missing font.
            // args.FontInfo can be null, so we guard against it.
            string missingFont = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missingFont}");
        };

        // Attach the FontSettings to the LoadOptions.
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Step 2.3 – (Optional) Add a custom font folder
        // --------------------------------------------------------------
        // If you have a folder with corporate fonts, tell Aspose to use it.
        // Replace "C:\\MyFonts" with the actual path on your machine.
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
```

**Dlaczego to ważne:** Bez wywołania zwrotnego ostrzeżenia Aspose cicho podmienia brakujące czcionki, co może prowadzić do nieoczekiwanych zmian układu później. Podłączając się do tego wywołania, **wykrywasz brakujące czcionki** wcześnie i możesz zdecydować, czy wstawić zamiennik, czy poprosić użytkownika o zainstalowanie brakującego fontu.

## Krok 3: Załaduj DOCX przy użyciu skonfigurowanych opcji

Gdy `LoadOptions` jest gotowy, załadowanie DOCX to jednowierszowy kod. Konstruktor `Document` przyjmuje ścieżkę do pliku oraz opcje, które właśnie zbudowaliśmy.

```csharp
        // --------------------------------------------------------------
        // Step 3 – Load the DOCX file while respecting our custom settings
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";

        // The Document constructor will invoke the warning callback
        // for any font it cannot resolve.
        Document doc = new Document(inputPath, loadOptions);

        Console.WriteLine("Document loaded successfully.");
```

Jeśli źródłowy plik odwołuje się do czcionki, której nie ma w systemie ani w niestandardowym folderze, zobaczysz wyjście podobne do:

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
```

Ta natychmiastowa informacja zwrotna jest nieoceniona, gdy budujesz potok przetwarzania wsadowego, który musi zapewnić wizualną wierność.

## Krok 4: Zweryfikuj załadowany dokument (opcjonalnie, ale przydatnie)

Po załadowaniu możesz chcieć potwierdzić, że zawartość dokumentu jest dostępna. Dla szybkiego sprawdzenia wypiszmy tekst pierwszego akapitu.

```csharp
        // --------------------------------------------------------------
        // Step 4 – Quick sanity check: print the first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");
    }
}
```

Uruchomienie programu teraz daje:

```
[Warning] Missing font: Times New Roman
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

## Krok 5: Przypadki brzegowe i zaawansowane wskazówki

### 5.1 Obsługa osadzonych czcionek

Niektóre pliki DOCX osadzają wymagane czcionki bezpośrednio. Aspose.Words automatycznie ich używa, więc nie zobaczysz ostrzeżeń. Jednak jeśli celowo **ładować dokumenty Word**, które usuwają osadzone czcionki (np. po konwersji), możesz potrzebować dostarczyć brakujące czcionki poprzez `SetFontsFolder`, jak pokazano wcześniej.

### 5.2 Użycie strumienia pamięci zamiast ścieżki do pliku

Jeśli Twój DOCX znajduje się w bazie danych lub pochodzi z żądania HTTP, możesz wczytać go ze `MemoryStream`:

```csharp
using (var stream = new MemoryStream(byteArrayFromDb))
{
    Document docFromStream = new Document(stream, loadOptions);
    // Continue processing...
}
```

Te same **opcji ładowania Aspose** mają zastosowanie, a wywołanie zwrotne ostrzeżenia nadal działa.

### 5.3 Globalne nadpisywanie podstawiania czcionek

Jeśli wolisz zastąpić brakujące czcionki konkretnym zamiennikiem (np. Arial), możesz dodać regułę podstawiania:

```csharp
fontSettings.SubstitutionSettings.FontSubstitution.AddSubstitutes("MissingFontName", new[] { "Arial" });
```

Połącz to z wywołaniem zwrotnym ostrzeżenia, aby logować zdarzenie podstawienia i utrzymać spójność wyjścia.

## Krok 6: Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do skopiowania program, który zawiera wszystkie powyższe kroki. Zapisz go jako `Program.cs`, przywróć pakiety NuGet i uruchom.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Create LoadOptions with custom font settings and warning callback
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        FontSettings fontSettings = new FontSettings();

        // Warn about missing fonts
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            string missing = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missing}");
        };

        // Optional: point to a folder with corporate fonts
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

        // Attach settings to load options
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Load the DOCX file
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";
        Document doc = new Document(inputPath, loadOptions);
        Console.WriteLine("Document loaded successfully.");

        // --------------------------------------------------------------
        // Quick sanity check – print first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");

        // --------------------------------------------------------------
        // (Optional) Demonstrate loading from a stream
        // --------------------------------------------------------------
        // byte[] bytes = File.ReadAllBytes(inputPath);
        // using var ms = new MemoryStream(bytes);
        // Document docFromStream = new Document(ms, loadOptions);
        // Console.WriteLine("Loaded from stream.");
    }
}
```

### Oczekiwane wyjście

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

Jeśli nie brakuje żadnych czcionek, linie ostrzeżeń po prostu się nie pojawią.

## Przegląd wizualny

![aspose load options example](/images/aspose-load-options.png "Diagram showing Aspose Load Options workflow")

*Diagram ilustruje, jak **Opcje ładowania Aspose** znajdują się pomiędzy źródłem pliku a obiektem `Document`, obsługując rozwiązywanie czcionek i wykrywanie brakujących czcionek.*

## Zakończenie

Przeszliśmy przez kompletną metodę dla **opcji ładowania Aspose**, pokazując dokładnie **jak ładować docx** przy jednoczesnym stosowaniu **niestandardowych ustawień czcionek** oraz **wykrywaniu brakujących czcionek**. Konfigurując wywołanie zwrotne ostrzeżenia i opcjonalnie wskazując Aspose niestandardowy folder czcionek, zyskujesz pełną widoczność problemów z czcionkami, zanim wpłyną na renderowanie.  

Od tego momentu możesz eksplorować tematy pokrewne, takie jak **konwersja dokumentu Word do PDF**, dodawanie znaków wodnych czy przetwarzanie wsadowe dziesiątek plików w folderze. Ten sam wzorzec – utwórz `LoadOptions`, podłącz wywołania zwrotne i wywołaj `new Document(...)` – działa w całym API Aspose.Words.

Masz pytania dotyczące konkretnego przypadku brzegowego, np. obsługi języków od prawej do lewej lub zaszyfrowanych plików DOCX? Zostaw komentarz lub sprawdź dokumentację Aspose.Words, aby zgłębić temat. Szczęśliwego kodowania i niech Twoje dokumenty zawsze renderują się dokładnie tak, jak zamierzałeś!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}