---
category: general
date: 2026-02-12
description: Utwórz obsługę ostrzeżeń czcionek, aby wykrywać brakujące czcionki i
  śledzić je w Aspose.Words. Dowiedz się, jak efektywnie rejestrować ostrzeżenia.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: pl
og_description: Utwórz obsługę ostrzeżeń dotyczących czcionek w C#, aby wykrywać brakujące
  czcionki i dowiedz się, jak rejestrować ostrzeżenia, gdy Aspose.Words podmienia
  czcionki.
og_title: Utwórz obsługę ostrzeżeń czcionek – wykryj brakujące czcionki
tags:
- Aspose.Words
- C#
- Document Processing
title: Utwórz obsługę ostrzeżeń czcionek – wykryj brakujące czcionki w C#
url: /pl/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz obsługę ostrzeżeń o czcionkach – wykrywanie brakujących czcionek w C#

Czy kiedykolwiek musiałeś **utworzyć obsługę ostrzeżeń o czcionkach**, ponieważ dokument Word cicho zamienił czcionkę, której się nie spodziewałeś? Nie jesteś sam. Gdy Aspose.Words ładuje plik DOCX, który odwołuje się do czcionki nieobecnej na serwerze, cicho przełącza się na czcionkę domyślną — co subtelnie psuje układ.

W tym samouczku pokażemy dokładnie, jak **wykrywać brakujące czcionki**, **śledzić brakujące czcionki** oraz **logować ostrzeżenia**, abyś mógł zauważyć te zamiany, zanim sprawią problemy. Na koniec będziesz mieć wielokrotnego użytku handler ostrzeżeń, który wypisuje każde zdarzenie zamiany czcionki na konsolę (lub dowolny logger, którego używasz). Bez tajemnic, tylko przejrzysty, praktyczny kod.

## Wymagania wstępne

- .NET 6.0 lub nowszy (API jest takie samo dla .NET Framework 4.6+)
- Aspose.Words for .NET zainstalowany (`dotnet add package Aspose.Words`)
- Plik Word, który odwołuje się do czcionki niezainstalowanej w systemie (np. `MissingFont.docx`)

Jeśli już to masz, świetnie — przejdźmy do działania.

## Krok 1: Skonfiguruj LoadOptions z wywołaniem zwrotnym ostrzeżeń  

Pierwszą rzeczą, którą robisz, gdy chcesz **utworzyć obsługę ostrzeżeń o czcionkach**, jest poinformowanie Aspose.Words, aby wywoływał callback za każdym razem, gdy napotka problem. `LoadOptions` jest kontenerem tej konfiguracji.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Dlaczego to ważne:**  
`LoadOptions` to jedyne miejsce, w którym możesz podłączyć `IWarningCallback`. Bez tego Aspose.Words zapisuje ostrzeżenia wewnętrznie, ale nigdy ich nie zobaczysz. Przypisując `FontWarningHandler`, zyskujesz pełną kontrolę nad tym, co się dzieje, gdy brakująca czcionka zostaje zastąpiona.

## Krok 2: Zaimplementuj klasę FontWarningHandler  

Teraz faktycznie **tworzymy kod obsługi ostrzeżeń o czcionkach**. Klasa implementuje `IWarningCallback` i otrzymuje obiekt `WarningInfo` dla każdego ostrzeżenia zgłaszanego przez Aspose.Words.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Wyjaśnienie:**  
- `info.Type` informuje nas o kategorii ostrzeżenia. Interesuje nas `WarningType.FontSubstitution`, ponieważ to właśnie wskazuje na brakującą czcionkę.  
- `info.Description` zawiera czytelną wiadomość, np. *„Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- Poprzez zapis do `Console.WriteLine` **logujemy ostrzeżenia** natychmiast. W rzeczywistej aplikacji możesz zamienić to na `ILogger`, zapis do pliku lub usługę telemetryczną.

> **Pro tip:** Jeśli potrzebujesz zebrać wszystkie brakujące czcionki do późniejszego raportu, przechowuj `info.Description` w `List<string>` zamiast je drukować.

## Krok 3: Załaduj dokument przy użyciu skonfigurowanego LoadOptions  

Gdy callback jest już ustawiony, ładowanie dokumentu automatycznie wywoła nasz handler przy każdej brakującej czcionce.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Co zobaczysz:**  
Uruchomienie programu wypisze coś podobnego do:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Ten wiersz potwierdza, że **wykryłeś brakujące czcionki** i teraz **śledzisz brakujące czcionki** w czasie rzeczywistym.

## Krok 4: Zweryfikuj działanie handlera w różnych scenariuszach  

Łatwo założyć, że handler działa tylko dla plików DOCX, ale Aspose.Words obsługuje wiele formatów. Spróbuj załadować PDF, który odwołuje się do osadzonej czcionki, lub starszy plik `.doc`. Ten sam callback uruchamia się dla każdego formatu, który przechodzi przez pipeline rozwiązywania czcionek.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

Jeśli PDF odwołuje się do czcionki, której nie ma zainstalowanej, otrzymasz ten sam komunikat w konsoli. To pokazuje, że twoje **utworzone rozwiązanie obsługi ostrzeżeń o czcionkach** jest niezależne od formatu.

## Krok 5: Rozszerzenie handlera – logowanie do pliku  

Wypisywanie na konsolę jest wygodne w demonstracjach, ale w kodzie produkcyjnym zazwyczaj zapisuje się do pliku logu. Oto szybka modyfikacja.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Teraz przy każdej zamianie czcionki wiadomość jest dopisywana do `font-warnings.log`. To spełnia część **jak logować ostrzeżenia** i zapewnia trwały zapis zdarzeń.

## Krok 6: Wszystko razem – kompletny, uruchamialny przykład  

Poniżej pełny program, który możesz skopiować i wkleić do aplikacji konsolowej. Nie brakuje żadnych fragmentów; wystarczy podmienić ścieżkę do pliku na własny dokument.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Oczekiwany rezultat:**  

- Konsola wypisuje każdą linię zamiany.  
- `font-warnings.log` zawiera teraz znacznik czasowy dla każdego zdarzenia brakującej czcionki.  
- Plik `output.pdf` zostaje utworzony przy użyciu zamienionych czcionek, zapewniając pomyślną konwersję, nawet gdy oryginalne czcionki są niedostępne.

## Często zadawane pytania i przypadki brzegowe  

| Pytanie | Odpowiedź |
|----------|-----------|
| *Co zrobić, jeśli chcę zignorować niektóre czcionki?* | Wewnątrz `Warning` sprawdź `info.Description` pod kątem nazwy czcionki i `return;` wcześnie dla czcionek, które uznasz za dopuszczalne. |
| *Czy handler uruchomi się dla czcionek osadzonych?* | Nie — czcionki osadzone są zawsze dostępne dla dokumentu, więc ostrzeżenie o zamianie nie wystąpi. |
| *Czy mogę przechwytywać inne typy ostrzeżeń (np. problemy z rozdzielczością obrazów)?* | Oczywiście. Usuń warunek `if (info.Type == WarningType.FontSubstitution)` lub dodaj dodatkowe bloki `if` dla `WarningType.ImageResolution`. |
| *Czy handler jest bezpieczny wątkowo?* | Pokazana domyślna implementacja zapisuje do pliku bez synchronizacji. W scenariuszach wielowątkowych warto otoczyć zapisy do pliku blokadą lub użyć współbieżnego loggera. |

## Kolejne kroki  

Teraz, gdy wiesz **jak logować ostrzeżenia** o brakujących czcionkach, możesz:

- **Wykrywać brakujące czcionki** podczas procesu importu wsadowego i generować podsumowujący raport.  
- **Śledzić brakujące czcionki** w wielu dokumentach i wysyłać alert e‑mailowy, gdy dana czcionka pojawia się często.  
- **Zintegrować się z systemem monitoringu** (np. Azure Application Insights), aby wyświetlać trendy zamian czcionek w czasie.  

Wszystkie te rozszerzenia opierają się na tej samej bazie `IWarningCallback`, którą stworzyliśmy.

---

*Miłego kodowania! Jeśli napotkasz dziwności — np. własny folder czcionek lub udział sieciowy — zostaw komentarz poniżej. Społeczność (i ja) zawsze chętnie pomoże dopracować twoją strategię obsługi ostrzeżeń o czcionkach.* 

![przykład utworzenia obsługi ostrzeżeń o czcionkach](image-placeholder.png "przykład utworzenia obsługi ostrzeżeń o czcionkach")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}