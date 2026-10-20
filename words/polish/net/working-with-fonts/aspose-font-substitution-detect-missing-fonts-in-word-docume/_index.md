---
category: general
date: 2026-04-05
description: Przewodnik Aspose dotyczący zamiany czcionek, aby wykrywać brakujące
  czcionki podczas ładowania dokumentu Word. Dowiedz się, jak konfigurować ustawienia
  czcionek i efektywnie obsługiwać brakujące czcionki.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: pl
og_description: Przewodnik Aspose dotyczący podstawiania czcionek w celu wykrycia
  brakujących czcionek podczas ładowania dokumentu Word. Dowiedz się, jak konfigurować
  ustawienia czcionek i efektywnie obsługiwać brakujące czcionki.
og_title: Zastępowanie czcionek Aspose – Wykrywanie brakujących czcionek w dokumentach
  Word
tags:
- Aspose.Words
- C#
- Font Management
title: Zastępowanie czcionek Aspose – wykrywanie brakujących czcionek w dokumentach
  Word
url: /pl/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Wykrywanie brakujących czcionek w dokumentach Word

Czy zdarzyło Ci się, że plik Word wygląda idealnie na jednym komputerze, a na innym wyświetla dziwne zmiany czcionek? To klasyczny problem **aspose font substitution**, który zazwyczaj oznacza brak niektórych czcionek w systemie docelowym. W tym samouczku pokażemy Ci krok po kroku, jak **wykrywać brakujące czcionki** podczas **ładowania dokumentu Word**, jak **konfigurować ustawienia czcionek** oraz co zrobić, aby **obsługiwać brakujące czcionki** w elegancki sposób.

Przejdziemy przez kompletny, gotowy do uruchomienia przykład w C#, wyjaśnimy, dlaczego każda linia ma znaczenie, i pokażemy oczekiwany wynik w konsoli. Po zakończeniu będziesz w stanie wykrywać zamiany czcionek w momencie ładowania dokumentu — bez domysłów.

## Czego się nauczysz

- Jak włączyć diagnostyczny kolektor ostrzeżeń czcionek w Aspose.Words.  
- Dokładny kod potrzebny do **ładowania dokumentu Word** z niestandardowymi **ustawieniami czcionek**.  
- Jak iterować po obiektach `WarningInfo`, aby wypisać każdą zamienioną czcionkę.  
- Wskazówki, jak tłumić niechciane ostrzeżenia lub dostarczać czcionki zapasowe.  
- Gotowy do uruchomienia przykład, który możesz skopiować i wkleić do Visual Studio.

### Wymagania wstępne

- .NET 6.0 lub nowszy (API działa tak samo na .NET Framework).  
- Aspose.Words for .NET (pakiet NuGet `Aspose.Words`).  
- Plik Word, który odwołuje się do czcionki, której nie masz zainstalowanej (np. `MissingFont.docx`).  

Jeśli masz to wszystko, zanurzmy się.

## Krok 1 – Włączenie diagnostycznego kolektora (Konfiguracja ustawień czcionek)

Na początek: Aspose.Words rejestruje ostrzeżenia o zamianie czcionek tylko wtedy, gdy mu to zlecisz. Robi się to poprzez utworzenie obiektu `FontSettings` i przypisanie go do instancji `LoadOptions`. Pomyśl o tym jak o włączeniu „świateł debugowania” dla obsługi czcionek.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**Dlaczego?**  
Bez obiektu `FontSettings` kolektor ostrzeżeń pozostaje cichy i nigdy nie dowiesz się, które czcionki zostały zamienione. Inicjalizując go pustym, pozwalamy Aspose używać domyślnych czcionek systemowych *i* śledzić wszystkie zamiany.

**Wskazówka:** Jeśli wiesz, że konkretny folder zawiera firmowe czcionki, wskaż go w `FontSettings` za pomocą `SetFontsFolder("path")`. To może zmniejszyć liczbę ostrzeżeń o brakujących czcionkach.

## Krok 2 – Ładowanie dokumentu z skonfigurowanymi opcjami (Load Word Document)

Teraz, gdy kolektor jest aktywny, załaduj swój plik `.docx` używając tych samych `LoadOptions`. To moment, w którym Aspose skanuje dokument, wyszukuje wszystkie odwołania do czcionek i decyduje, czy wymagana jest zamiana.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**Dlaczego to ma znaczenie?**  
Jeśli po prostu wywołałbyś `new Document("MissingFont.docx")`, zastosowane byłyby ustawienia domyślne *i* lista ostrzeżeń pozostałaby pusta. Przekazanie `loadOptions` zapewnia, że diagnostyczny kolektor jest podłączony do procesu ładowania.

## Krok 3 – Pobieranie i wyświetlanie ostrzeżeń o zamianie czcionek (Wykrywanie brakujących czcionek)

Po załadowaniu dokumentu do pamięci, Aspose przechowuje wszystkie ostrzeżenia w `document.WarningCallback.Warnings`. Przejdź pętlą po tej kolekcji, przefiltruj elementy typu `WarningType.FontSubstitution` i wypisz opis. Każdy opis informuje, której czcionki brakowało i jaka została użyta zamiast niej.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Oczekiwany wynik w konsoli**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

Ten wynik dokładnie informuje, które czcionki brakuje na maszynie uruchamiającej kod. Teraz możesz zdecydować, czy zainstalować brakujące czcionki, osadzić je w dokumencie, czy pozostawić zamianę.

![Wynik w konsoli pokazujący ostrzeżenia o zamianie czcionek Aspose](/images/aspose-font-substitution-console.png)

*Tekst alternatywny obrazu:* aspose font substitution – wynik w konsoli wymieniający zamienione czcionki

## Krok 4 – Opcjonalnie: Dostosowanie zachowania zamiany (Obsługa brakujących czcionek)

Czasami nie wystarczy wiedzieć *że* doszło do zamiany — chcesz kontrolować *jak* ona nastąpiła. Aspose.Words pozwala zarejestrować własną regułę `IFontSubstitutionRule`. Poniżej szybki przykład, który wymusza, aby każda brakująca czcionka przechodziła na `Tahoma`.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**Kiedy mógłbyś tego użyć?**  
Jeśli generujesz PDF-y dla usługi internetowej i wiesz, że każdy klient potrafi renderować `Tahoma`, wymuszenie zapasowej czcionki zapewnia spójność wizualną bez konieczności dystrybuowania dziesiątek plików czcionek.

## Pełny działający przykład (wszystkie kroki razem)

Oto cały program, który możesz wkleić do nowego projektu konsolowego. Kompiluje się bez zmian, pod warunkiem że zainstalowałeś pakiet NuGet Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

Uruchom program, obserwuj konsolę i zobaczysz wypisane wszystkie zdarzenia brakujących czcionek. Następnie możesz zdecydować, czy zainstalować brakujące czcionki, osadzić je, czy zachować zapasową.

## Najczęściej zadawane pytania

**Q: Czy to działa przy konwersji do PDF?**  
**A:** Tak. Gdy później wywołasz `doc.Save("output.pdf")`, wszystkie czcionki, które zostały zamienione podczas ładowania, będą osadzone w PDF-ie. Dlatego wczesne wykrycie ostrzeżeń pomaga uniknąć niespodziewanych zmian czcionek w ostatecznym PDF-ie.

**Q: Co zrobić, jeśli mam wiele dokumentów do przetworzenia?**  
Umieść logikę ładowania w bloku try‑catch i ponownie używaj jednej instancji `FontSettings` dla wszystkich dokumentów. To zmniejsza narzut i utrzymuje kolektor ostrzeżeń aktywnym dla każdego pliku.

**Q: Czy mogę całkowicie wyciszyć ostrzeżenia?**  
Możesz ustawić `loadOptions.WarningCallback = null;` przed ładowaniem, ale stracisz możliwość **wykrywania brakujących czcionek** — co zazwyczaj nie jest pożądane.

## Zakończenie

Omówiliśmy wszystko, co potrzebne, aby opanować **aspose font substitution**: włączenie diagnostycznego kolektora, ładowanie pliku Word z niestandardowymi **ustawieniami czcionek**, wyodrębnianie listy brakujących czcionek oraz nadpisanie domyślnej reguły zamiany, aby **obsługiwać brakujące czcionki** po swojemu. Dzięki kilku linijkom C# uzyskasz pełną widoczność problemów z czcionkami, które w przeciwnym razie ukrywałyby się za subtelnymi zmianami układu.

Co dalej? Spróbuj osadzić oryginalne czcionki w dokumencie za pomocą `FontSettings.SetFontsFolder` lub zbadaj `FontSourceBase`, aby ładować czcionki z bazy danych. Możesz także poeksperymentować z kolekcją `Document.BuiltInStyle`, aby zobaczyć, jak zmiany czcionek na poziomie stylu się rozprzestrzeniają.

Masz więcej pytań dotyczących Aspose.Words lub zarządzania czcionkami? Dodaj komentarz, zapoznaj się z oficjalną dokumentacją Aspose lub uruchom nowy projekt i poeksperymentuj z powyższym kodem. Szczęśliwego kodowania i niech Twoje dokumenty zawsze renderują się dokładnie tak, jak zamierzasz!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}