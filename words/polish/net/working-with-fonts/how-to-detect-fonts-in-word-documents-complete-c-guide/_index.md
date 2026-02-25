---
category: general
date: 2026-02-24
description: Jak wykrywać czcionki w dokumencie Word przy użyciu Aspose.Words. Dowiedz
  się, jak ustawić wywołanie zwrotne i załadować dokument Word z pełnym przykładem
  kodu.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: pl
og_description: Jak wykrywać czcionki w dokumencie Word przy użyciu wywołania zwrotnego
  ostrzeżenia. Ten przewodnik pokazuje, jak ustawić wywołanie zwrotne i załadować
  dokument Word przy użyciu Aspose.Words.
og_title: Jak wykrywać czcionki w dokumentach Word – samouczek C# krok po kroku
tags:
- C#
- Aspose.Words
- Document Processing
title: Jak wykrywać czcionki w dokumentach Word – Kompletny przewodnik C#
url: /pl/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

paragraph after image: "*The screenshot shows the console output when a missing font is substituted. The alt text contains the primary keyword for SEO.*" translate.

Next heading ## Conclusion translate to "## Zakończenie". Paragraph.

Translate rest.

Make sure to keep shortcodes at end.

Now produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wykrywać czcionki w dokumentach Word – Kompletny przewodnik C#

Zastanawiałeś się kiedyś **how to detect fonts**, które brakuje po załadowaniu pliku Word? Być może natrafiłeś na dokument, który w edytorze wygląda poprawnie, ale wygenerowany PDF podmienia kilka krojów pisma „za kulisami”. To klasyczny objaw substytucji czcionek i wykrycie tego wcześnie może uchronić Cię przed nieprzyjemnymi niespodziankami w układzie.

W tym tutorialu przejdziemy przez praktyczne rozwiązanie: użycie **Aspose.Words** do wczytania pliku `.docx`, podłączenia callbacku ostrzeżeń oraz **how to set callback**, który raportuje każdą substytucję czcionki. Po zakończeniu nie tylko będziesz wiedział **how to detect fonts** programowo, ale także zrozumiesz **how to set callback** prawidłowo i **load word document** bezpiecznie — wszystko w jednym, gotowym do uruchomienia przykładzie C#.

> **What you’ll get**
> * Gotowy do skopiowania i wklejenia fragment kodu  
> * Szczegółowe wyjaśnienie każdego wiersza krok po kroku  
> * Wskazówki dotyczące obsługi przypadków brzegowych, takich jak wiele brakujących czcionek czy własne foldery z czcionkami  
> * Przykładowy output w konsoli, abyś mógł zweryfikować działanie

---

## Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również z .NET Core)  
- Pakiet NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)  
- Plik Word, który celowo odwołuje się do czcionki, której nie masz zainstalowanej (np. `MissingFont.docx`)  
- Visual Studio, Rider lub dowolny ulubiony edytor

Innych bibliotek nie potrzebujesz; wszystko, co jest potrzebne, znajduje się w standardowym środowisku .NET.

---

## Jak wykrywać czcionki w dokumencie Word

### Krok 1: Utwórz opcje ładowania i podłącz callback ostrzeżeń

Pierwsze, co robimy, to informujemy Aspose.Words, że chcemy być powiadamiani o wszelkich problemach pojawiających się podczas ładowania pliku. To właśnie tutaj wchodzi **how to set callback**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**Dlaczego to ma znaczenie:**  
`LoadOptions` to brama do dostosowywania procesu ładowania. Przypisując instancję `FontWarningCollector` do `WarningCallback`, Aspose.Words wywoła naszą metodę `Warning` za każdym razem, gdy zastąpi brakującą czcionkę domyślną. To jest sedno **how to detect fonts**, które nie są dostępne na maszynie.

---

### Krok 2: Przygotuj instancję LoadOptions

Teraz tworzymy obiekt `LoadOptions` i podpinamy nasz callback.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Wskazówka:** Jeśli potrzebujesz kontrolować, *gdzie* Aspose szuka zamienników czcionek, możesz także ustawić `loadOptions.FontSettings`. Jest to przydatne, gdy na serwerze masz prywatny folder z czcionkami.

---

### Krok 3: Załaduj dokument Word

Mając gotowe opcje, w końcu **load word document**. To moment, w którym Aspose analizuje DOCX i, jeśli jakieś czcionki brakują, nasz callback zostaje wywołany.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**Co się dzieje pod maską?**  
Aspose.Words odczytuje części XML pliku DOCX, rozwiązuje każde odwołanie `<w:font>` i sprawdza kolekcję czcionek systemowych. Gdy odniesienie nie może zostać spełnione, podstawia pierwszą pasującą czcionkę zastępczą i generuje ostrzeżenie `FontSubstitution`.

---

### Krok 4: Zweryfikuj wynik

Uruchom program i obserwuj konsolę. Dla każdej brakującej czcionki zobaczysz wiersz podobny do:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

Jeśli dokument nie zawiera brakujących czcionek, konsola pozostaje cicha — co oznacza, że **how to detect fonts** nie zwróciło żadnych wyników.

---

### Krok 5: Pełny działający przykład (aplikacja konsolowa)

Poniżej znajduje się samodzielny plik `Program.cs`, który możesz wrzucić do nowego projektu konsolowego. Zawiera wszystkie elementy, o których rozmawialiśmy, oraz mały pomocnik, który utrzymuje okno konsoli otwarte podczas debugowania.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**Przykładowy output w konsoli** (przykład):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

Jeśli zamienisz `MissingFont.docx` na plik używający wyłącznie zainstalowanych czcionek, zobaczysz jedynie wiersz „Press any key…”, co potwierdza, że logika wykrywania działa prawidłowo.

---

## Częste pytania i przypadki brzegowe

### Co zrobić, jeśli chcę przechwycić *wszystkie* ostrzeżenia, a nie tylko substytucję czcionek?

Po prostu usuń warunek `if (info.Type == WarningType.FontSubstitution)`. Obiekt `WarningInfo` zawiera enum `Type`, na którym możesz przełączać się w innych scenariuszach (np. `DocumentStructure`, `ImageLoading`).

### Czy mogę zapisywać ostrzeżenia do pliku zamiast wypisywać je w konsoli?

Oczywiście. Zastąp `Console.WriteLine` wywołaniem dowolnego frameworka logującego (`Serilog`, `NLog` itp.). Callback działa w tym samym wątku, w którym ładowany jest dokument, więc upewnij się, że Twój logger jest bezpieczny wątkowo.

### Jak to zachowuje się w aplikacji webowej?

W ASP.NET Core zazwyczaj wstrzykujesz singletonową implementację `IWarningCallback` i przekazujesz ją przez `LoadOptions`. Pamiętaj, aby nie pisać bezpośrednio do strumienia odpowiedzi — lepiej logować do bazy danych lub kolekcji w pamięci, którą później udostępnisz przez endpoint API.

### A co z własnymi czcionkami przechowywanymi w folderze spoza systemu?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

Teraz Aspose.Words najpierw przeszuka `C:\MyCustomFonts`, zanim sięgnie po czcionki systemowe, co zmniejszy liczbę ostrzeżeń o substytucję.

---

## Wizualne podsumowanie

![Wykrywanie czcionek - callback ostrzeżeń w Aspose.Words](/images/font-warning-callback.png "Jak wykrywać czcionki przy użyciu callbacka ostrzeżeń")

*Zrzut ekranu pokazuje output w konsoli, gdy brakująca czcionka zostaje zastąpiona. Tekst alternatywny zawiera główne słowo kluczowe pod kątem SEO.*

---

## Zakończenie

Masz teraz solidny, gotowy do produkcji wzorzec **how to detect fonts** w dowolnym pliku Word, który ładowany jest przy pomocy Aspose.Words. Dzięki **how to set callback** uzyskasz w czasie rzeczywistym wgląd w brakujące lub zastąpione kroje pisma, a także nauczyłeś się prawidłowo **load word document**, zachowując czysty i łatwy do utrzymania kod.

Co dalej? Spróbuj rozbudować callback, aby zbierał ostrzeżenia w listę, a następnie wyświetlał je w interfejsie użytkownika lub w automatycznym raporcie. Możesz także przyjrzeć się `FontSettings.SubstitutionSettings`, aby kontrolować, *które* czcionki są wybierane jako zamienniki.

Śmiało eksperymentuj — podmieniaj dokumenty, dodawaj kolejne brakujące czcionki lub integruj logikę z większym potokiem przetwarzania dokumentów. Jeśli napotkasz problemy, zostaw komentarz poniżej lub napisz do mnie na GitHubie.

Miłego kodowania i niech Twoje dokumenty zawsze renderują się z oczekiwanymi czcionkami!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}