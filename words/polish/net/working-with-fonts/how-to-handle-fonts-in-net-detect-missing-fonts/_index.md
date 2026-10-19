---
category: general
date: 2026-06-02
description: Jak obsługiwać czcionki w .NET – wykrywać brakujące czcionki i śledzić
  zmiany czcionek przy użyciu LoadOptions i FontSettings. Poznaj kompletną, działającą
  wersję rozwiązania.
draft: false
keywords:
- how to handle fonts
- detect missing fonts
- track font changes
language: pl
og_description: Jak obsługiwać czcionki w .NET – wykrywać brakujące czcionki i śledzić
  zmiany czcionek. Postępuj zgodnie z tym przewodnikiem krok po kroku, aby uzyskać
  kompletną, gotową do uruchomienia rozwiązanie.
og_title: jak obsługiwać czcionki w .NET – wykrywać brakujące czcionki
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: how to handle fonts in .NET – detect missing fonts and track font changes
    using LoadOptions and FontSettings. Learn a complete, runnable solution.
  headline: how to handle fonts in .NET – detect missing fonts
  type: TechArticle
tags:
- .NET
- Aspose.Words
- FontSettings
title: Jak obsługiwać czcionki w .NET – wykrywać brakujące czcionki
url: /pl/net/working-with-fonts/how-to-handle-fonts-in-net-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# jak obsługiwać czcionki w .NET – wykrywać brakujące czcionki

Zastanawiałeś się kiedyś **jak obsługiwać czcionki**, gdy dokument Word odwołuje się do kroju pisma, który nie jest zainstalowany na komputerze? Nie jesteś jedyny. Brakujące czcionki mogą zamienić dopracowany raport w nieczytelny bałagan, a bez odpowiednich ostrzeżeń możesz nigdy nie dowiedzieć się, co zostało zamienione.  

W tym samouczku pokażemy Ci dokładnie **jak obsługiwać czcionki**, wykrywając brakujące czcionki **i** śledząc zmiany czcionek w czasie wykonywania. Po zakończeniu będziesz mieć samodzielną aplikację konsolową, która rejestruje każdą zamianę, więc nigdy nie będziesz zaskoczony tajemniczą Helvetica pojawiającą się tam, gdzie powinna być Times New Roman.

> **Co otrzymasz:** kompletny, gotowy do skopiowania i wklejenia przykład kodu, wyjaśnienie każdego wiersza, wskazówki dla projektów w rzeczywistym świecie oraz szybki przegląd przypadków brzegowych, na które możesz natrafić.

## Wymagania wstępne

- .NET 6.0 lub nowszy (przykład używa pliku `Program.cs` na najwyższym poziomie dla zwięzłości)  
- Aspose.Words for .NET 23.9 lub nowszy – możesz go pobrać z NuGet za pomocą `dotnet add package Aspose.Words`  
- Dokument Word, który celowo odwołuje się do czcionki, której nie masz (np. `MissingFont.docx`)  

Nie są wymagane żadne inne biblioteki.

![Diagram przedstawiający, jak LoadOptions przepływa do FontSettings i zdarzenia ostrzeżenia o zamianie – przykład obsługi czcionek w .NET](https://example.com/images/font‑handling‑flow.png "przykład obsługi czcionek w .NET")

## Krok 1: Konfiguracja LoadOptions z FontSettings  

Pierwszą rzeczą, której potrzebujemy, jest obiekt `LoadOptions`, który instruuje Aspose.Words, aby monitorował problemy z czcionkami.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

// Create LoadOptions and attach a fresh FontSettings instance.
var loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

**Dlaczego to ważne:** `LoadOptions` jest strażnikiem, gdy dokument jest odczytywany z dysku. Dostarczając własny `FontSettings`, uzyskujemy dostęp do wewnętrznego silnika rozpoznawania czcionek, co jest jedynym sposobem **wykrywania brakujących czcionek** przed renderowaniem dokumentu.

## Krok 2: Subskrypcja zdarzenia SubstitutionWarning  

Aspose.Words wywołuje zdarzenie `SubstitutionWarning` za każdym razem, gdy nie może znaleźć dokładnej czcionki, o którą poprosiłeś. Zalogujemy szczegóły, abyś mógł zobaczyć, które czcionki zostały żądane i które faktycznie użyto.

```csharp
// Hook into the warning event – this is where we “track font changes”.
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.RequestedFontName – the name the document asked for.
    // e.SubstitutedFontName – the name Aspose.Words fell back to.
    // e.WarningType – tells you why the substitution happened.
    Console.WriteLine(
        $"[Font Substitution] Requested: {e.RequestedFontName}, " +
        $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
};
```

**Dlaczego słuchamy:** Bez tego nasłuchiwacza nigdy nie dowiesz się, że doszło do zamiany. Zdarzenie dostarcza pełny ślad audytu, spełniając wymóg „śledzenia zmian czcionek”.

## Krok 3: Załaduj dokument przy użyciu skonfigurowanych opcji  

Teraz faktycznie odczytujemy plik. Ponieważ przekazaliśmy `loadOptions`, Aspose.Words wywoła zdarzenie ostrzeżenia dla każdej napotkanej brakującej czcionki.

```csharp
// Replace the path with the location of your test document.
string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

Document doc = new Document(docPath, loadOptions);
```

To wszystko – dokument został załadowany, a wszelkie problemy z czcionkami już zostały wypisane na konsolę.

## Krok 4: (Opcjonalnie) Zweryfikuj zamienione czcionki w dokumencie  

Jeśli chcesz podwójnie sprawdzić, które czcionki znalazły się w ostatecznym PDF lub DOCX, możesz przejść przez kolekcję czcionek dokumentu:

```csharp
Console.WriteLine("\n--- Fonts actually used in the document ---");
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
}
```

Uruchomienie tego po załadowaniu wyświetli każdą czcionkę, którą silnik postanowił osadzić lub odwołać. Przydatne, gdy musisz wygenerować raport dla zespołów QA.

## Pełny działający przykład  

Skopiuj poniższy blok do nowego projektu konsolowego (`dotnet new console`) i uruchom go. Program wypisze każdą zamianę, a następnie wyświetli czcionki, które przetrwały ładowanie.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions with FontSettings.
        // -------------------------------------------------
        var loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Step 2: Hook the substitution warning event.
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"[Font Substitution] Requested: {e.RequestedFontName}, " +
                $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
        };

        // -------------------------------------------------
        // Step 3: Load the document (this triggers warnings).
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // Step 4 (optional): List fonts actually used.
        // -------------------------------------------------
        Console.WriteLine("\n--- Fonts actually used in the document ---");
        foreach (FontInfo fontInfo in doc.FontInfos)
        {
            Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
        }

        Console.WriteLine("\nDone. Press any key to exit.");
        Console.ReadKey();
    }
}
```

### Oczekiwany wynik  

Jeśli `MissingFont.docx` żąda *„Comic Sans MS”* (który nie jest zainstalowany), zobaczysz coś podobnego:

```
[Font Substitution] Requested: Comic Sans MS, Used: Arial, Reason: FontNotFound
[Font Substitution] Requested: Times New Roman, Used: Times New Roman, Reason: None

--- Fonts actually used in the document ---
Arial – Regular
Times New Roman – Regular
```

Pierwsza linia dowodzi, że **wykrywamy brakujące czcionki** i **śledzimy zmiany czcionek**. Druga linia pokazuje zamianę, która nie była konieczna (brak ostrzeżenia, ponieważ czcionka istniała).

## Typowe pułapki i profesjonalne wskazówki  

| Pułapka | Co się dzieje | Jak naprawić / uniknąć |
|---------|--------------|--------------------|
| **Brak wywołań zdarzeń ostrzeżenia** | Możesz pomyśleć, że API jest zepsute. | Upewnij się, że *przypisujesz* `FontSettings` do `LoadOptions` **przed** załadowaniem dokumentu. Hak zdarzenia musi być podłączony **przed** wywołaniem `new Document(...)`. |
| **Zamienione czcionki nadal wyglądają nieprawidłowo** | Aspose.Words przechodzi na czcionkę domyślną, która nie pasuje do stylu. | Podaj własny folder czcionek za pomocą `fontSettings.SetFontsFolder(@"C:\MyFonts", true)`. Daje to silnikowi więcej opcji, zanim przejdzie do czcionki domyślnej. |
| **Spadek wydajności przy dużych dokumentach** | Skanowanie każdej czcionki może dodać kilka milisekund. | Zachowaj w pamięci obiekt `FontSettings`, jeśli ładujesz wiele dokumentów po kolei. Ponowne użycie tej samej instancji unika ponownego odczytywania tabel czcionek systemowych. |
| **Wyjście konsoli ginie w aplikacjach GUI** | Nie zobaczysz ostrzeżeń. | Przekieruj zdarzenie do loggera (np. `Serilog`) lub zapisz do pliku: `File.AppendAllText("font-warnings.log", …)`. |

## Rozszerzanie rozwiązania  

- **Eksport do PDF z osadzonymi czcionkami** – po załadowaniu wywołaj `doc.Save("output.pdf", SaveOptions.CreateSaveOptions(SaveFormat.Pdf));` i upewnij się, że ustawiono `PdfSaveOptions.FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll;`.  
- **Przetwarzanie wsadowe** – otocz logikę ładowania w pętli `foreach` po folderze plików DOCX. Zapisuj ostrzeżenia każdego pliku do pliku CSV w celach audytowych.  
- **Przyjazny interfejs użytkownika** – udostępnij tę samą logikę za przyciskiem w aplikacji WinForms/WPF, wyświetlając ostrzeżenia w `ListBox`.

## Podsumowanie  

Przeszliśmy przez **jak obsługiwać czcionki** w .NET, konfigurując `LoadOptions`, subskrybując zdarzenie `SubstitutionWarning` i w końcu ładując dokument. Przykład nie tylko **wykrywa brakujące czcionki**, ale także **śledzi zmiany czcionek**, dzięki czemu możesz audytować każdą zamianę.  

Wypróbuj go na własnych dokumentach, dostosuj ścieżkę folderu czcionek i nigdy nie zostaniesz zaskoczony nieoczekiwaną zamianą czcionki. Jeśli uznałeś ten przewodnik za przydatny, rozważ zgłębienie powiązanych tematów, takich jak *„osadzanie własnych czcionek w PDF przy użyciu Aspose.Words”* lub *„tworzenie strategii awaryjnej czcionek dla aplikacji .NET wieloplatformowych”.*  

Szczęśliwego kodowania i niech Twoje dokumenty zawsze renderują się dokładnie tak, jak zamierzałeś!

## Co warto nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak załadować DOCX i wykrywać brakujące czcionki – kompletny przewodnik C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Jak wykrywać czcionki w Aspose.Words – obsługa ostrzeżeń i ustawień](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Jak używać LoadOptions w Aspose.Words – kompletny przewodnik](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}