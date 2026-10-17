---
category: general
date: 2026-04-07
description: Dowiedz się, jak wykrywać czcionki i jak przechwytywać ostrzeżenia podczas
  obsługi brakujących czcionek w C# przy użyciu Aspose.Words. Dołączony kod krok po
  kroku.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: pl
og_description: Jak wykrywać czcionki w Aspose.Words? Skorzystaj z tego samouczka,
  aby przechwytywać ostrzeżenia i łatwo obsługiwać brakujące czcionki.
og_title: Jak wykrywać czcionki w Aspose.Words – Kompletny przewodnik
tags:
- Aspose.Words
- C#
- Font handling
title: Jak wykrywać czcionki w Aspose.Words – Kompletny przewodnik
url: /pl/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wykrywać czcionki w Aspose.Words – Kompletny przewodnik

Zastanawiałeś się kiedyś **jak wykrywać czcionki**, które brakuje w dokumencie Word przed wdrożeniem go do produkcji? Nie jesteś sam. W wielu scenariuszach korporacyjnych niepożądana czcionka może zepsuć potok konwersji PDF lub spowodować nieprofesjonalne artefakty układu. Dobrą wiadomością jest to, że Aspose.Words oferuje wbudowany sposób na wykrycie brakujących krojów pisma i wyświetlenie czytelnych ostrzeżeń.

W tym samouczku przejdziemy krok po kroku przez **wykrywanie czcionek**, **przechwytywanie ostrzeżeń** oraz najlepsze praktyki **obsługi brakujących czcionek**, aby Twoja aplikacja była odporna. Bez zewnętrznych narzędzi, bez zgadywania — czysty kod C#, który możesz od razu wkleić do swojego projektu.

> **Szybki podgląd:** Po zakończeniu będziesz mieć wielokrotnego użytku `FontSubstitutionWarningCollector`, który zbiera wszystkie komunikaty o podstawianiu czcionek podczas ładowania dokumentu, oraz będziesz wiedział, jak zareagować, gdy czcionka nie zostanie znaleziona.

---

## Czego się nauczysz

- Jak skonfigurować `LoadOptions`, aby nasłuchiwał ostrzeżeń o podstawianiu czcionek.  
- Jak przechwycić te ostrzeżenia w własnej klasie kolektora.  
- Jak przetworzyć zebrane ostrzeżenia i zdecydować, czy przerwać, zalogować, czy podmienić czcionki.  
- Obsługa przypadków brzegowych dla dokumentów odwołujących się do zdalnych lub osadzonych czcionek.  

**Wymagania wstępne:** .NET 6+ (lub .NET Framework 4.6+), Aspose.Words for .NET (najnowsza wersja) oraz podstawowa znajomość C#. Jeśli nigdy nie używałeś Aspose.Words, nie martw się — ten przewodnik zakłada jedynie kilka minut konfiguracji.

---

## Jak wykrywać czcionki przy użyciu Aspose.Words LoadOptions

Pierwszym krokiem do wykrycia brakujących czcionek jest poinstruowanie Aspose.Words, aby je zgłaszał. Robi się to poprzez właściwość `LoadOptions.WarningCallback`, która przyjmuje dowolną klasę implementującą `IWarningCallback`. Poniżej tworzymy mały kolektor, który przechowuje każde ostrzeżenie do późniejszej analizy.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**Dlaczego to ważne:** Bez callbacku ostrzeżeń Aspose.Words cicho podmienia brakujące czcionki domyślną, a Ty nigdy nie dowiesz się, że problem istnieje. Przechwycając `WarningType.FontSubstitution`, uzyskasz pełną widoczność — dokładnie te dane, których potrzebujesz, aby **wykrywać czcionki**, które nie są dostępne na maszynie hosta.

Teraz podpinamy kolektor do `LoadOptions` i ładujemy dokument:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **Porada:** Jeśli pracujesz z wieloma dokumentami w partii, używaj tego samego egzemplarza `FontSubstitutionWarningCollector`, ale pamiętaj, aby wywołać `Clear()` pomiędzy ładowaniami, aby nie mieszać ostrzeżeń z różnych plików.

---

## Przechwytywanie ostrzeżeń podczas ładowania dokumentu

Po załadowaniu dokumentu kolektor już zawiera wszystkie ostrzeżenia związane z czcionkami. Następne logiczne pytanie brzmi: *Jak przechwycić ostrzeżenia* w sposób łatwy do logowania lub wyświetlania?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

Typowy wynik wygląda tak:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**Co to oznacza:** Każda linia ujawnia pierwotną nazwę czcionki oraz zamiennik, który wybrało Aspose.Words. Mając te informacje, możesz zdecydować, czy zamiennik jest akceptowalny, czy musisz ręcznie osadzić brakującą czcionkę.

---

## Elegancka obsługa brakujących czcionek

Wykrywanie i przechwytywanie ostrzeżeń to dopiero połowa walki. Prawdziwa wartość pojawia się, gdy **obsługujesz brakujące czcionki** w gotowy do produkcji sposób. Poniżej trzy popularne strategie:

1. **Loguj i kontynuuj** – Odpowiednie dla przetwarzania wsadowego, gdy potrzebny jest jedynie ślad audytu.  
2. **Przerwij przy krytycznych czcionkach** – Rzuć wyjątek, jeśli brak konkretnej czcionki (np. specyficznego kroju marki).  
3. **Osadź czcionkę w locie** – Załaduj brakującą czcionkę z określonego folderu i zarejestruj ją w Aspose.Words przed ponownym wczytaniem dokumentu.

### Przykład: Przerwanie przy krytycznej czcionce

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### Przykład: Automatyczne osadzanie brakujących czcionek

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**Dlaczego te wzorce pomagają:** Decydując wyraźnie, co zrobić, gdy czcionka jest nieobecna, eliminujesz ciche podstawienia, które mogłyby zaszkodzić identyfikacji wizualnej lub czytelności. To istota **obsługi brakujących czcionek** w kontrolowany sposób.

---

## Kompletny działający przykład

Łącząc wszystko w jedną całość, oto prosty program gotowy do uruchomienia, który demonstruje **wykrywanie czcionek**, **przechwytywanie ostrzeżeń** oraz prostą politykę **obsługi brakujących czcionek** poprzez ich logowanie.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**Oczekiwany rezultat:** Po uruchomieniu programu przeciwko dokumentowi, który odwołuje się do czcionki nieobecnej na maszynie, konsola wypisze każde ostrzeżenie o podstawieniu. Jeśli któreś ostrzeżenie dotyczy czcionki z zestawu `critical`, program zakończy się wcześniej, zapobiegając wygenerowaniu wadliwego PDF‑a.

---

## Najczęściej zadawane pytania (FAQ)

| Pytanie | Odpowiedź |
|----------|-----------|
| *Czy potrzebna jest licencja na Aspose.Words, aby używać tego kodu?* | Tak, ważna licencja Aspose.Words usuwa znak wodny wersji ewaluacyjnej i odblokowuje pełną funkcjonalność. |
| *Czy to podejście wykrywa czcionki osadzone w dokumencie?* | Czcionki osadzone są już częścią pliku, więc Aspose.Words nie zgłosi ostrzeżenia o podstawieniu. W razie potrzeby możesz sprawdzić `Document.FontInfos`, aby wyliczyć osadzone czcionki. |
| *Co zrobić, gdy brakująca czcionka jest systemowa w Windows, a nie w Linux?* | To samo ostrzeżenie pojawi się w Linux, ponieważ czcionka nie jest tam zainstalowana. Skorzystaj ze strategii „obsługi brakujących czcionek”, aby dołączyć wymagane pliki `.ttf` do aplikacji. |
| *Czy kolektor ostrzeżeń jest wątkowo‑bezpieczny* | {{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}