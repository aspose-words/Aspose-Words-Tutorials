---
category: general
date: 2026-03-28
description: Jak przechwycić ostrzeżenia podczas ładowania pliku DOCX za pomocą Aspose.Words
  i uzyskać komunikaty ostrzegawcze o brakujących czcionkach. Dowiedz się, jak efektywnie
  obsługiwać brakujące czcionki.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: pl
og_description: Jak przechwycić ostrzeżenia podczas ładowania pliku DOCX w Aspose.Words,
  uzyskać komunikaty ostrzeżeń i obsłużyć brakujące czcionki przy użyciu praktycznych
  przykładów kodu.
og_title: Jak przechwytywać ostrzeżenia w Aspose.Words – Kompletny przewodnik C#
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak przechwytywać ostrzeżenia w Aspose.Words – Kompletny przewodnik C#
url: /pl/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak przechwycić ostrzeżenia w Aspose.Words – Kompletny przewodnik C#

Zastanawiałeś się kiedyś **jak przechwycić ostrzeżenia**, które pojawiają się podczas ładowania dokumentu Word przy użyciu Aspose.Words? Być może zauważasz dziwne zmiany czcionek i potrzebujesz dokładnie wiedzieć, dlaczego tak się dzieje. Krótko mówiąc, możesz podłączyć się do systemu ostrzeżeń biblioteki, **pobierać komunikaty ostrzeżeń** i nawet **obsługiwać brakujące czcionki**, zanim zepsują one układ.  

W tym samouczku przejdziemy przez realistyczny scenariusz: wczytanie pliku DOCX, zebranie każdego ostrzeżenia generowanego przez silnik oraz wypisanie szczegółów o wszelkich zamianach czcionek. Po zakończeniu będziesz mieć gotowy do uruchomienia przykład kodu, zrozumiesz „dlaczego” każdego kroku i będziesz wiedział, jak rozszerzyć podejście w własnych projektach.

## Czego się nauczysz

- Jak skonfigurować `LoadOptions`, aby ostrzeżenia były automatycznie przechwytywane.  
- Dokładny sposób **pobierania komunikatów ostrzeżeń** z `WarningInfoCollection`.  
- Jak zidentyfikować i zareagować na **brakujące czcionki** za pomocą flagi `WarningType.FontSubstitution`.  
- Wskazówki dotyczące rozwiązywania problemów w trudnych przypadkach, takich jak dokumenty z osadzonymi czcionkami lub własnymi folderami czcionek.  

Nie potrzebujesz zewnętrznych odnośników – wszystko, co potrzebne, znajduje się tutaj.

---

## Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również na .NET Framework 4.7+).  
- Pakiet NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Przykładowy plik DOCX (`input.docx`), który nie zawiera niektórych czcionek lub używa czcionek niezainstalowanych na twoim komputerze.  

To wszystko. Jeśli już czujesz się pewnie w C# i Visual Studio, możesz skopiować‑wkleić kod i od razu go uruchomić.

---

## Krok 1: Przygotuj Load Options i Callback ostrzeżeń

Pierwszą rzeczą, którą robi Aspose.Words, gdy wywołujesz `new Document(path, loadOptions)`, jest parsowanie pliku. Podczas parsowania może napotkać brakujące czcionki, nieobsługiwane funkcje lub przestarzały znacznik. Aby przechwycić te zdarzenia, potrzebny jest obiekt **warning callback**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Dlaczego to ważne:** Bez callbacku Aspose.Words cicho zapisuje ostrzeżenia w konsoli (lub je odrzuca), pozostawiając cię ślepym na zamiany czcionek, które mogą wpłynąć na układ. Dostarczając dedykowany `WarningInfoCollection`, uzyskujesz pełną widoczność.

> **Pro tip:** Jeśli zależy ci tylko na ostrzeżeniach związanych z czcionkami, możesz je później przefiltrować – ale zbieranie *wszystkich* ostrzeżeń daje bezpieczeństwo na przyszłe problemy.

---

## Krok 2: Załaduj dokument z skonfigurowanymi opcjami

Teraz, gdy callback jest gotowy, załaduj plik. Konstruktor `Document` automatycznie wywoła callback dla wszelkich napotkanych problemów.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**Co się dzieje pod maską?** Aspose.Words parsuje Open XML, rozwiązuje style i próbuje dopasować każde odwołanie do czcionki do czcionki zainstalowanej w systemie. Jeśli dopasowanie nie zostanie znalezione, tworzy wpis `WarningInfo` typu `FontSubstitution`.

---

## Krok 3: Pobierz i przeanalizuj zebrane ostrzeżenia

Po zakończeniu ładowania, twój `warningCollector` zawiera każde wystąpione ostrzeżenie. Wyciągnijmy je i skupmy się na komunikatach o zamianie czcionek.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Przykładowy wynik** (twoja konsola może wyświetlić coś podobnego):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Jeśli chcesz *wszystkie* ostrzeżenia, po prostu usuń warunek `if` lub loguj `warning.Type` dla każdego wpisu.

---

## Krok 4: Obsługa brakujących czcionek – poza samym logowaniem

Przechwytywanie ostrzeżeń jest przydatne, ale często trzeba **obsługiwać brakujące czcionki** programowo. Oto dwie popularne strategie:

### 4.1 Zamień brakujące czcionki na określoną czcionkę zapasową

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Teraz każda brakująca czcionka zostanie zamieniona na *Calibri* zamiast domyślnego zastępczego fontu biblioteki.

### 4.2 Dynamicznie osadź czcionkę zastępczą

Jeśli masz własny plik czcionki (np. `MyFallback.ttf`), możesz zarejestrować go w czasie działania:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

To podejście jest przydatne, gdy dystrybuujesz konkretną czcionkę firmową wraz z aplikacją.

> **Edge case:** Dokumenty, które już osadzają wymaganą czcionkę, zignorują reguły zamiany systemowej. W takim scenariuszu kolekcja ostrzeżeń będzie pusta dla tej czcionki, co jest dokładnie tym, czego potrzebujesz.

---

## Krok 5: Pełny działający przykład (gotowy do kopiowania‑wklejania)

Poniżej znajduje się samodzielny program, który demonstruje wszystko od początku do końca. Wystarczy zamienić `YOUR_DIRECTORY/input.docx` na ścieżkę do swojego pliku testowego.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Czego się spodziewać**

- Konsola wypisuje każde ostrzeżenie o zamianie czcionki, poprzedzone emoji ostrzeżenia dla lepszej widoczności.  
- Wynikowy plik DOCX (`output.docx`) używa *Calibri* wszędzie tam, gdzie wykryto brakującą czcionkę.  
- Brak nieobsłużonych wyjątków – system ostrzeżeń elegancko radzi sobie z każdą nieznaną czcionką.

---

## Częste pytania i odpowiedzi

**Q: Czy to zadziała z PDF‑ami generowanymi z Worda?**  
A: Tak. Aspose.Words traktuje PDF‑y jako kolejny format wyjściowy. Przechwytywanie ostrzeżeń odbywa się w fazie *ładowania*, więc jest niezależne od ostatecznego eksportu.

**Q: Co jeśli potrzebuję przechwytywać ostrzeżenia dla **wszystkich** operacji na dokumencie (zapis, konwersja itp.)?**  
A: Możesz ponownie użyć tego samego `WarningInfoCollection`, przypisując go do `Document.WarningCallback` po utworzeniu dokumentu. Każda kolejna operacja doda nowe wpisy do tej samej kolekcji.

**Q: Czy callback ostrzeżeń wpływa na wydajność?**  
A: Znikomo. Kolekcja po prostu przechowuje obiekty; chyba że przetwarzasz tysiące ostrzeżeń w ciasnej pętli, nie zauważysz spowolnienia.

**Q: Jak mogę zignorować ostrzeżenia, które mnie nie interesują?**  
A: Zaimplementuj własną klasę dziedziczącą po `IWarningCallback` i filtruj wewnątrz metody `Warning`. Wbudowany `WarningInfoCollection` jedynie przechowuje, nie filtruje.

---

## Porady i pułapki

- **Pro tip:** Zawsze sprawdzaj `Warning.Description` – zawiera dokładną nazwę czcionki, której brakowało. To może pomóc zdecydować, czy dołączyć czcionkę do aplikacji.  
- **Uważaj na osadzone czcionki:** Jeśli źródłowy DOCX już zawiera wymaganą czcionkę, Aspose.Words nie wyemituje ostrzeżenia o zamianie, nawet jeśli czcionka nie jest zainstalowana lokalnie.  
- **Bezpieczeństwo wątków:** `WarningInfoCollection` nie jest thread‑safe. Jeśli ładujesz wiele dokumentów równocześnie, przydziel każdemu wątkowi własną kolekcję.  
- **Sprawdzenie wersji:** API ostrzeżeń jest stabilne od Aspose.Words 20.8. Upewnij się, że używasz aktualnej wersji, aby nie przegapić nowszych typów ostrzeżeń.

---

## Zakończenie

Omówiliśmy **jak przechwycić ostrzeżenia** z Aspose.Words, pokazaliśmy **jak pobierać komunikaty ostrzeżeń** i przedstawiliśmy praktyczne sposoby **obsługi brakujących czcionek** poprzez czcionki zapasowe lub własne foldery czcionek. Pełny przykład jest gotowy do wstawienia w dowolnym projekcie .NET, a koncepcje skalują się do większych potoków automatyzacji.

Następnie możesz zbadać:

- Użycie `Document.WarningCallback` do przechwytywania ostrzeżeń podczas operacji **zapisu**.  
- Logowanie ostrzeżeń do pliku lub systemu telemetrycznego w celu monitorowania w produkcji.  
- Rozszerzenie callbacku, aby automatycznie zamieniać brakujące czcionki na czcionki specyficzne dla marki.

Śmiało eksperymentuj — zamień czcionkę zapasową, dodaj więcej dokumentów do partii lub zintegrować zbieracz ostrzeżeń z pipeline’em CI, który wykrywa regresje związane z czcionkami. Miłego kodowania i niech twoje dokumenty zawsze renderują się dokładnie tak, jak tego oczekujesz!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}