---
category: general
date: 2026-01-03
description: Jak wykrywać czcionki w Aspose.Words i obsługiwać ostrzeżenia przy użyciu
  ustawień czcionek Aspose – przewodnik krok po kroku dla programistów.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: pl
og_description: Jak wykrywać czcionki w Aspose.Words i konfigurować ostrzeżenia za
  pomocą ustawień czcionek Aspose. Poznaj pełny przepływ pracy w kilka minut.
og_title: Jak wykrywać czcionki w Aspose.Words – obsługa ostrzeżeń
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak wykrywać czcionki w Aspose.Words – obsługa ostrzeżeń i ustawień
url: /pl/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wykrywać czcionki w Aspose.Words – Obsługa ostrzeżeń i ustawień

Zastanawiałeś się kiedyś **jak wykrywać czcionki** w dokumencie Word przed jego wdrożeniem? Nie jesteś jedyny. Brakujące czcionki mogą powodować koszmary układu, a bez odpowiednich ostrzeżeń możesz wydać uszkodzony PDF lub DOCX, nie zdając sobie z tego sprawy.  

W tym samouczku pokażemy, **jak wykrywać czcionki** przy użyciu Aspose.Words, **jak obsługiwać ostrzeżenia** oraz jak dostosować **ustawienia czcionek Aspose**, aby **konfigurować ostrzeżenia** dokładnie tak, jak potrzebujesz. Na końcu będziesz mieć gotowy fragment kodu, który wypisuje każdą zamianę czcionki wykonywaną przez Aspose, oraz będziesz wiedział, jak go dostosować do własnych projektów.

## Wymagania wstępne

- .NET 6+ (lub .NET Framework 4.6+).  
- Aspose.Words for .NET zainstalowany przez NuGet (`Install-Package Aspose.Words`).  
- Plik Word, który celowo odwołuje się do brakującej czcionki (np. *DocumentWithMissingFonts.docx*).  

Jeśli już masz te elementy, świetnie — przejdźmy do rzeczy.

![zrzut ekranu wykrywania czcionek](https://example.com/detect-fonts.png "przykładowy wynik wykrywania czcionek")

## Jak wykrywać czcionki przy użyciu Aspose.Words

Pierwszym krokiem jest poinformowanie Aspose.Words, że zależy Ci na zdarzeniach związanych z zamianą czcionek. Robi się to, dostarczając własny callback ostrzeżeń poprzez **ustawienia czcionek Aspose**. Callback otrzymuje obiekt `WarningInfo` dla każdej zamiany, co pozwala **wykrywać czcionki** w czasie wykonywania.

### Krok 1: Utwórz klasę callbacka ostrzeżeń

Zaimplementuj interfejs `IWarningCallback`. W metodzie `Warning` filtruj zdarzenia `WarningType.FontSubstitution` i loguj szczegóły.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **Pro tip:** Ciąg znaków `info.Description` zawiera zarówno nazwę brakującej czcionki, jak i zamiennik wybrany przez Aspose. Możesz go sparsować, jeśli potrzebujesz ustrukturyzowanego raportu.

### Krok 2: Skonfiguruj LoadOptions z ustawieniami czcionek Aspose

Utwórz instancję `LoadOptions`, dołącz nowy obiekt `FontSettings` i ustaw `WarningCallback` na nasz handler. To mówi Aspose, **jak konfigurować ostrzeżenia**.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

Jeśli masz prywatny folder z czcionkami, możesz go dodać w ten sposób:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

Ten wiersz pokazuje kolejny aspekt **ustawień czcionek Aspose** — kontrolujesz dokładnie, gdzie Aspose szuka czcionek, zanim zdecyduje się na zamianę.

### Krok 3: Załaduj dokument i wywołaj callback

Teraz załaduj docelowy dokument przy użyciu `loadOptions`. Podczas parsowania pliku przez Aspose, każda brakująca czcionka wywoła handler ostrzeżeń, skutecznie **wykrywając czcionki** w locie.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

Po uruchomieniu programu zobaczysz wyjście podobne do:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### Krok 4: (Opcjonalnie) Zbieraj ostrzeżenia do późniejszego użycia

Jeśli potrzebujesz przechować dane o zamianach w raporcie, zmodyfikuj handler, aby gromadził komunikaty w liście.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Później możesz zapisać `handler.Substitutions` do pliku JSON, wysłać je do usługi logującej lub wyświetlić w interfejsie użytkownika.

### Krok 5: Zweryfikuj wynik programowo

Czasami chcesz upewnić się, że *nie* doszło do żadnej zamiany (np. w buildzie CI). Oto szybka kontrola:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

Ten fragment kodu demonstruje, **jak obsługiwać ostrzeżenia** w sposób deterministyczny, dając pełną kontrolę nad pipeline'em budowania.

## Najczęściej zadawane pytania (i przypadki brzegowe)

**Co zrobić, jeśli chcę zignorować niektóre zamiany?**  
Możesz dodać warunkową logikę wewnątrz `Warning` i po prostu zwrócić, nie logując czcionek, które uznasz za akceptowalne.

**Czy mogę wyłączyć wszystkie ostrzeżenia i otrzymać tylko wartość bool?**  
Tak — ustaw `loadOptions.WarningCallback = null`, a potem sprawdź `doc.FontInfo` po załadowaniu (choć utracisz szczegółowy log).

**Czy to działa przy konwersji do PDF?**  
Oczywiście. Ten sam mechanizm ostrzeżeń uruchamia się, gdy wywołasz `doc.Save("out.pdf")`. Callback przechwyci wszystkie zamiany czcionek wykonane podczas konwersji.

**Czy to wpływa na wydajność?**  
Obciążenie jest minimalne — tylko kilka dodatkowych wywołań metod na brakującą czcionkę. Przy dużych partiach warto rozważyć buforowanie wyników.

## Podsumowanie: Co omówiliśmy

- **Jak wykrywać czcionki** poprzez implementację własnego `IWarningCallback`.  
- **Jak obsługiwać ostrzeżenia** za pomocą `LoadOptions.WarningCallback`.  
- Dostosowywanie **ustawień czcionek Aspose** (dodawanie własnych folderów czcionek, włączanie/wyłączanie ostrzeżeń).  
- **Jak konfigurować ostrzeżenia** zarówno dla natychmiastowego wyjścia w konsoli, jak i późniejszej analizy.  

Mając te elementy, możesz pewnie przetwarzać dokumenty Word, zapewniając, że brakujące czcionki zostaną oznaczone, i utrzymać spójność wyników w różnych środowiskach.

## Kolejne kroki

- Zbadaj `FontSettings.SubstitutionSettings` dla bardziej szczegółowej kontroli (np. mapowanie konkretnych brakujących czcionek na wybrane zamienniki).  
- Połącz to podejście z Aspose.PDF, aby generować PDF‑y zachowujące dokładną typografię.  
- Zautomatyzuj sprawdzanie ostrzeżeń w pipeline CI/CD, aby blokować wydania zawierające problemy z czcionkami — idealne dla zespołów, które **obsługują ostrzeżenia** jako część bramek jakości.

Masz więcej pytań dotyczących **ustawień czcionek Aspose** lub potrzebujesz pomocy przy integracji tego rozwiązania w większej usłudze? zostaw komentarz poniżej i powodzenia w kodowaniu!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}