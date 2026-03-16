---
category: general
date: 2026-03-16
description: Dowiedz się, jak używać FontSettings w Aspose.Words, aby elegancko obsługiwać
  brakujące czcionki — kompletny kod, obsługa zdarzeń i wskazówki najlepszych praktyk.
draft: false
keywords:
- how to use fontsettings
- handle missing fonts
- Aspose.Words font substitution
- missing font detection C#
- document loading options
language: pl
og_description: Jak używać FontSettings w Aspose.Words do obsługi brakujących czcionek
  — przewodnik krok po kroku z pełnym przykładem w C# i praktycznymi wskazówkami.
og_title: Jak używać FontSettings do obsługi brakujących czcionek w Aspose.Words
tags:
- Aspose.Words
- C#
- Font Management
title: Jak używać FontSettings do obsługi brakujących czcionek w Aspose.Words
url: /pl/net/working-with-fonts/how-to-use-fontsettings-to-handle-missing-fonts-in-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak używać FontSettings do obsługi brakujących czcionek w Aspose.Words

Zastanawiałeś się kiedyś **jak używać FontSettings**, gdy Twoje dokumenty Word odwołują się do czcionek, które nie są zainstalowane na serwerze? Nie jesteś sam. Brakujące czcionki mogą powodować nieestetyczne zastępstwa lub nawet wyrzucać wyjątki, a większość programistów po prostu ignoruje problem, dopóki nie pojawi się w produkcji.  

W tym samouczku pokażemy Ci dokładnie **jak używać FontSettings**, aby **obsługiwać brakujące czcionki** w Aspose.Words, przechwytywać szczegółowe ostrzeżenia i zapewnić przewidywalne renderowanie dokumentu. Po zakończeniu będziesz mieć gotowy do uruchomienia przykład w C#, zrozumiesz, dlaczego każda linia ma znaczenie, i będziesz wiedział, jak dostosować rozwiązanie do większych projektów.

## Co obejmuje ten przewodnik

- Konfigurowanie **FontSettings** i subskrypcja zdarzenia `SubstitutionWarning`.  
- Dołączanie ustawień do `LoadOptions`, aby były respektowane podczas ładowania dokumentu.  
- Uruchomienie dokumentu testowego, który celowo nie zawiera czcionek i odczytanie wyjścia konsoli.  
- Wskazówki dotyczące logowania, wyłączania automatycznej substytucji oraz obsługi przypadków brzegowych, takich jak wiele brakujących czcionek.  

Nie wymagana jest żadna zewnętrzna dokumentacja — wszystko, czego potrzebujesz, znajduje się tutaj.

## Wymagania wstępne

- .NET 6+ (lub .NET Framework 4.6.2+).  
- Aspose.Words for .NET 23.9 lub nowszy (API, którego używamy, jest stabilne w najnowszych wersjach).  
- Prosty plik `.docx`, który odwołuje się do czcionki, o której wiesz, że nie jest zainstalowana (np. *Comic Sans MS* w kontenerze Linux).  

To wszystko — nie potrzebujesz dodatkowych pakietów NuGet poza Aspose.Words.

## Dlaczego obsługa brakujących czcionek ma znaczenie

Gdy dokument odwołuje się do czcionki, której środowisko nie może znaleźć, Aspose.Words automatycznie zastępuje ją najbliższym dopasowaniem. Takie zastąpienie jest często akceptowalne, ale czasami trzeba **zalogować**, które czcionki były brakujące (w celu zgodności) lub **zapobiec** zastąpieniu w całości (np. w przypadku PDF‑ów specyficznych dla marki). Korzystając z `FontSettings.SubstitutionWarning`, uzyskujesz pełną widoczność i kontrolę.

## Krok 1: Utwórz FontSettings i subskrybuj zdarzenie Substitution‑Warning

Pierwszą rzeczą, którą robisz, jest utworzenie instancji `FontSettings`. Ten obiekt przechowuje wszystkie konfiguracje związane z czcionkami dla biblioteki. Kluczową częścią jest podłączenie zdarzenia `SubstitutionWarning`, które wyzwala się **za każdym razem**, gdy Aspose.Words nie może znaleźć żądanej czcionki.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – Initialise FontSettings and listen for missing‑font warnings
FontSettings fontSettings = new FontSettings();

// The lambda receives detailed info about the missing font and the chosen substitute.
fontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.MissingFontName  → the name Aspose.Words tried to load.
    // e.SubstitutedFontName → the font that was actually used instead.
    // e.WarningType → the enum describing why the warning was raised.
    Console.WriteLine($"Missing font: {e.MissingFontName}");
    Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
    Console.WriteLine($"Reason: {e.WarningType}");
};
```

**Dlaczego to ma znaczenie:**  
- **Widoczność:** Natychmiast wiesz, które czcionki są nieobecne.  
- **Audytowalność:** Konsola (lub logger) może być przekierowana do pliku w celu raportów zgodności.  
- **Kontrola:** Później możesz zdecydować się na zastąpienie substytucji własną czcionką.

> **Pro tip:** Jeśli wolisz framework do logowania (Serilog, NLog, itp.), zamień wywołania `Console.WriteLine` na `logger.Information(...)`.

## Krok 2: Dołącz FontSettings do LoadOptions

`LoadOptions` jest mechanizmem, który informuje Aspose.Words, jak traktować plik w trakcie fazy ładowania. Przypisując obiekt `FontSettings`, zapewniasz, że obsługa ostrzeżeń jest aktywna *przed* parsowaniem jakiejkolwiek zawartości.

```csharp
// Step 2 – Bind FontSettings to LoadOptions so the loader knows about our event handler
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Dlaczego to ma znaczenie:**  
- Jeśli załadujesz dokument bez przekazania `LoadOptions`, domyślna obsługa czcionek zostanie użyta i przegapisz ostrzeżenia.  
- To podejście pozwala także dostosować inne zachowania podczas ładowania (np. ochronę hasłem) w tym samym obiekcie.

## Krok 3: Załaduj dokument z skonfigurowanymi opcjami

Teraz w końcu odczytujemy plik Word. Ścieżka może być bezwzględna lub względna; Aspose.Words będzie respektować `LoadOptions`, które właśnie przygotowaliśmy.

```csharp
// Step 3 – Load the document while applying our FontSettings
string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";   // <-- adjust to your environment
Document document = new Document(docPath, loadOptions);
```

Jeśli dokument zawiera czcionkę, która nie jest zainstalowana, zdarzenie `SubstitutionWarning` zostanie wywołane i zobaczysz wyjście podobne do przykładu poniżej.

### Oczekiwany wynik w konsoli

```
Missing font: Comic Sans MS
Substituted with: Arial
Reason: FontSubstitution
```

Dokładny zamiennik może się różnić w zależności od łańcucha zastępowania czcionek w systemie operacyjnym, ale **nazwa brakującej czcionki** zawsze zostanie zgłoszona.

## Krok 4: Zweryfikuj wynik (opcjonalne renderowanie)

Często chcesz mieć pewność, że dokument nadal wygląda poprawnie po zastąpieniu. Szybkim sposobem jest zapisanie go jako PDF i otwarcie wyniku.

```csharp
// Optional: Save as PDF to visually confirm the substitution
document.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
Console.WriteLine("Document saved as PDF – check the rendering.");
```

Jeśli potrzebujesz **całkowicie zapobiec** zastąpieniu, ustaw `FontSettings.SubstitutionSettings.TableSubstitution = false` przed ładowaniem. Wtedy Aspose.Words wyrzuci wyjątek dla brakujących czcionek, który możesz przechwycić i obsłużyć.

```csharp
// Disable automatic substitution – will raise an exception on missing fonts
fontSettings.SubstitutionSettings.TableSubstitution = false;
```

## Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do uruchomienia program. Wklej go do aplikacji konsolowej, dostosuj ścieżkę do pliku i naciśnij **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create FontSettings and hook the warning event
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionWarning += (sender, e) =>
            {
                Console.WriteLine($"Missing font: {e.MissingFontName}");
                Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
                Console.WriteLine($"Reason: {e.WarningType}");
            };

            // 2️⃣ Attach FontSettings to LoadOptions
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings
                // Uncomment the next line to *disable* substitution and force an exception
                // , FontSettings = { SubstitutionSettings = { TableSubstitution = false } }
            };

            // 3️⃣ Load the document
            string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save as PDF to see the visual result
            doc.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
            Console.WriteLine("Processing complete. Check the console for missing‑font warnings.");
        }
    }
}
```

### Czego się spodziewać

- Konsola wypisuje każdą brakującą czcionkę wraz z wybranym zamiennikiem.  
- Wynikowy PDF (jeśli zachowałeś opcjonalny zapis) wyświetla dokument przy użyciu czcionki zastępczej, zapewniając integralność układu.

## Częste pytania i przypadki brzegowe

| Question | Answer |
|----------|--------|
| **Co jeśli brakuje wielu czcionek?** | Zdarzenie wyzwala się raz dla każdej brakującej czcionki, więc otrzymasz osobną linię logu dla każdej. |
| **Czy mogę zastąpić zamiennik własną czcionką?** | Tak. Wewnątrz obsługi zdarzenia możesz wywołać `e.SubstitutedFont = new FontInfo("MyCustomFont")`. |
| **Czy ostrzeżenie jest generowane dla osadzonych czcionek, które nie udało się załadować?** | Zdecydowanie — niezależnie od tego, czy czcionka jest zewnętrzna, czy osadzona, mechanizm ostrzeżenia jest taki sam. |
| **Czy muszę zwolnić zasoby `Document`?** | `Document` implementuje `IDisposable`. Owiń użycie w blok `using`, jeśli ładujesz wiele plików w pętli. |
| **Czy to będzie działać w kontenerach Linux?** | Tak długo, jak Aspose.Words może zlokalizować systemowe czcionki (np. za pomocą `fontconfig`), ten sam mechanizm zdarzeń działa. |

## Najlepsze praktyki i wskazówki

- **Centralizuj logowanie:** Utwórz metodę pomocniczą, która zapisuje zarówno do konsoli, jak i do trwałego pliku logu.  
- **Przetwarzanie wsadowe:** Przy konwertowaniu dziesiątek dokumentów, używaj jednego egzemplarza `FontSettings`, aby uniknąć powtarzających się subskrypcji zdarzeń.  
- **Wydajność:** Ostrzeżenia o substytucji dodają znikomy narzut, ale jeśli przetwarzasz tysiące plików, rozważ ich wyłączenie po zweryfikowaniu zestawu czcionek.  
- **Bezpieczeństwo wersji:** API `SubstitutionWarning` jest stabilne od wersji Aspose.Words 16.0, więc możesz na nim polegać przy przyszłych aktualizacjach.

## Zakończenie

Przeprowadziliśmy Cię przez **sposób użycia FontSettings** w Aspose.Words, aby **elegancko obsługiwać brakujące czcionki**. Tworząc obiekt `FontSettings`, subskrybując `SubstitutionWarning` i ładując dokumenty za pomocą `LoadOptions`, uzyskasz pełną widoczność problemów z czcionkami i możesz zdecydować, czy logować, zastępować, czy przerywać przy brakujących czcionkach.

Od prostego wyjścia w konsoli po własną logikę substytucji, wzorzec skaluje się do dużych potoków przetwarzania dokumentów, zapewniając spójność i możliwość audytu wyników.

**Next steps:**  

- Zbadaj **niestandardową substytucję czcionek**, przypisując `e.SubstitutedFont` wewnątrz zdarzenia.  
- Połącz to podejście z **renderowaniem dokumentu do obrazów** w celu generowania miniatur.  
- Sprawdź **Aspose.PDF**, jeśli potrzebujesz osadzić zastąpione czcionki bezpośrednio w finalnym PDF‑ie, aby zapewnić pełną przenośność.

Szczęśliwego kodowania i niech Twoje dokumenty nigdy nie cierpią z powodu niechcianej brakującej czcionki!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}