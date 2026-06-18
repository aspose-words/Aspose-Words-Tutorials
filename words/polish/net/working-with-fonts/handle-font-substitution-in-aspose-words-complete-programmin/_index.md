---
category: general
date: 2026-06-17
description: Obsłuż zamianę czcionek w Aspose.Words i szybko wykryj brakujące czcionki
  dzięki temu samouczkowi krok po kroku dla programistów .NET.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: pl
og_description: Obsłuż podstawianie czcionek w Aspose.Words i dowiedz się, jak wykrywać
  brakujące czcionki w swoich dokumentach, korzystając z przejrzystych przykładów
  kodu.
og_title: Obsługa podstawiania czcionek w Aspose.Words – pełny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Obsługa podstawiania czcionek w Aspose.Words – Kompletny przewodnik programistyczny
url: /pl/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Obsługa podstawiania czcionek w Aspose.Words – Kompletny przewodnik programistyczny

Zastanawiałeś się kiedyś, jak **obsługiwać podstawianie czcionek**, gdy dokument Word odwołuje się do czcionki, której nie ma zainstalowanej na serwerze? Nie jesteś sam. W wielu rzeczywistych aplikacjach — pomyśl o generatorach faktur czy usługach automatycznego generowania raportów — brakujące czcionki powodują ciche podstawienia, które psują układ.  

Dobrą wiadomością jest to, że Aspose.Words udostępnia wbudowany system ostrzeżeń, który pozwala **wykrywać brakujące czcionki** i reagować w dowolny sposób. W tym samouczku przeprowadzimy Cię przez rejestrację obsługi ostrzeżeń, wczytanie dokumentu i wyodrębnienie dokładnych zdarzeń podstawiania czcionek, o których musisz wiedzieć. Na końcu zobaczysz także, jak odpowiedzieć na klasyczne pytanie „**jak wykrywać brakujące czcionki**?” przy użyciu czystego, gotowego do produkcji kodu.

## Co obejmuje ten samouczek

* Konfigurowanie Aspose.Words, aby generowało ostrzeżenia przy każdym podstawieniu czcionki.
* Przechwytywanie tych ostrzeżeń w niestandardowym handlerze, aby móc logować, zamieniać lub przerywać.
* Wykorzystanie przechwyconych danych do **wykrywania brakujących czcionek** przed zapisaniem lub renderowaniem dokumentu.
* Wskazówki dotyczące rozwiązywania problemów w przypadkach brzegowych — np. gdy czcionka zastępcza jest wybierana cicho.
* Pełny, gotowy do uruchomienia przykład, który możesz wkleić do dowolnej aplikacji konsolowej .NET.

> **Wymagania wstępne** – Będziesz potrzebować aktualnego .NET SDK (6.0+ działa dobrze), ważnej licencji Aspose.Words for .NET (lub tymczasowego klucza ewaluacyjnego) oraz przykładowego pliku DOCX, który celowo odwołuje się do czcionki niezainstalowanej w systemie. Nie są wymagane inne biblioteki firm trzecich.

---

## ## Obsługa podstawiania czcionek przy użyciu własnego handlera ostrzeżeń

Aspose.Words generuje obiekt `WarningInfo` za każdym razem, gdy nie może znaleźć żądanej czcionki. Domyślnie te ostrzeżenia są ignorowane, dlatego często nie zauważasz podstawienia. Aby **obsłużyć podstawianie czcionek**, zamieniasz domyślny handler ostrzeżeń na taki, który rzeczywiście coś robi.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### Dlaczego to działa

* `FontSettings.DefaultWarningHandler` jest globalną właściwością statyczną — po jej ustawieniu, **każda** operacja Aspose.Words w bieżącym AppDomain używa Twojego delegata.
* `WarningInfoCollectionHandler` otrzymuje obiekt `WarningInfo`, który zawiera `WarningType` oraz czytelny dla człowieka `Description`. Filtrowanie po `WarningType.FontSubstitution` zapewnia, że widzisz tylko interesujące Cię zdarzenia.
* Wywołanie `doc.Save` wymusza, aby biblioteka rozwiązała wszystkie czcionki, co powoduje wyzwolenie ostrzeżeń. Jeśli potrzebujesz jedynie przejrzeć dokument bez zapisywania, możesz zamiast tego wywołać `doc.UpdatePageLayout()`.

**Oczekiwany output konsoli** (zakładając, że brakująca czcionka to „Papyrus”):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

Ta linia jest dowodem, że biblioteka **wykryła brakujące czcionki** i wybrała zastępczą.

---

## ## Wykrywanie brakujących czcionek przed renderowaniem

Czasami chcesz całkowicie zatrzymać proces, jeśli wymagana czcionka jest brakująca — być może dlatego, że wytyczne marki wymagają dokładnej typografii. Handler ostrzeżeń można rozszerzyć, aby zbierał wszystkie komunikaty o brakujących czcionkach do listy, a następnie podjąć decyzję.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### Jak to odpowiada na pytanie „jak wykrywać brakujące czcionki”

* Lista `missingFonts` pełni rolę rejestru każdego zdarzenia podstawienia.
* Po wywołaniu `UpdatePageLayout` możesz przejrzeć listę i zdecydować, czy kontynuować, logować, czy rzucić wyjątek.
* Ten wzorzec działa dla dowolnego formatu wyjściowego (PDF, HTML, obrazy), ponieważ system ostrzeżeń jest niezależny od formatu.

## ## Zaawansowana wskazówka: Zastąp brakujące czcionki określoną zamienną

Jeśli masz firmową czcionkę, której musisz używać, możesz poinstruować Aspose.Words, aby automatycznie zastępował każdą brakującą czcionkę Twoją czcionką zastępczą. Jest to przydatne, gdy chcesz, aby dokument *nadal* wyglądał akceptowalnie bez ręcznego przetwarzania pośredniego.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

Umieść powyższy fragment **przed** wczytaniem dokumentu. Teraz każda brakująca czcionka — niezależnie od jej pierwotnej nazwy — zostanie zamieniona na „Calibri” (lub „Arial”, jeśli Calibri nie jest dostępne). Nadal otrzymasz ostrzeżenie, ale dokument zostanie wyrenderowany z czcionką, którą kontrolujesz.

## ## Częste pułapki i jak ich unikać

| Pułapka | Dlaczego się dzieje | Rozwiązanie |
|---------|---------------------|-------------|
| **Ostrzeżenia znikają po pierwszym wywołaniu** | Statyczny `DefaultWarningHandler` jest nadpisywany później w aplikacji. | Ustaw handler **jednokrotnie** przy starcie aplikacji lub przechowuj referencję i ponownie przypisz, jeśli go zmieniasz. |
| **Zgłaszana jest tylko pierwsza brakująca czcionka** | Niektóre API grupują ostrzeżenia; musisz wywołać `UpdatePageLayout` lub `Save`, aby opróżnić kolejkę. | Wymuś aktualizację układu lub zapisz w formacie, który zamierzasz wygenerować. |
| **Podstawienie nadal zachodzi nawet po przerwaniu** | Handler ostrzeżeń działa *po* tym, jak podstawienie już nastąpiło. | Użyj handlera do **logowania**, a następnie rzuć wyjątek, aby zatrzymać dalsze przetwarzanie. |
| **Brakujące czcionki w kontenerach Linux** | Linux często nie posiada katalogu czcionek Windows, co prowadzi do wielu podstawień. | Zamontuj wymagane czcionki w kontenerze lub użyj `FontSettings.SetFontsFolder`, aby wskazać niestandardowy katalog czcionek. |

## ## Wykrywanie podstawiania czcionek w scenariuszu Web API

Jeśli udostępniasz dokumenty za pośrednictwem ASP.NET Core, prawdopodobnie nie chcesz zapisywać do konsoli. Zamiast tego zbieraj ostrzeżenia i zwracaj je jako część odpowiedzi HTTP.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

Teraz API **wykrywa brakujące czcionki** i zwraca przejrzysty ładunek JSON przed wygenerowaniem jakiegokolwiek PDF. To praktyczna ilustracja „jak wykrywać brakujące czcionki” w usłudze gotowej do produkcji.

## ## Testowanie implementacji

1. **Utwórz testowy DOCX**, który odwołuje się do czcionki, której wiesz, że nie ma na maszynie (np. „Comic Sans MS” w minimalnym obrazie Docker).  
2. Uruchom aplikację konsolową lub punkt końcowy API.  
3. Sprawdź, czy konsola (lub odpowiedź HTTP) wyświetla ostrzeżenie o podstawieniu.  
4. Opcjonalnie otwórz wygenerowany PDF i sprawdź właściwości czcionki — Aspose.Words powinien pokazać czcionkę zastępczą, którą skonfigurowałeś.

Jeśli zobaczysz ostrzeżenie, ale PDF nadal używa nieoczekiwanej czcionki, sprawdź ponownie kolejność w `SubstitutionSettings`; pierwsze dopasowanie wygrywa.

## ## Zakończenie

Omówiliśmy wszystko, co potrzebne, aby **obsługiwać podstawianie czcionek** w Aspose.Words, od rejestracji handlera ostrzeżeń po programowe **wykrywanie brakujących czcionek** i nawet ich zamianę na firmową czcionkę. Korzystając z wbudowanego systemu ostrzeżeń, zyskujesz pełną widoczność każdego zdarzenia „czcionka nie znaleziona”, co bezpośrednio odpowiada na pytanie „**jak wykrywać brakujące czcionki**?”, które każdy programista zadaje przy automatyzacji generowania dokumentów.

Co dalej? Spróbuj połączyć tę logikę z **dynamicznym ładowaniem czcionek** (`FontSettings.SetFontsFolder`), aby obsługiwać czcionki przesyłane przez użytkowników w locie, lub rozbuduj handler ostrzeżeń, aby zapisywał wpisy w centralnej usłudze logowania, takiej jak Serilog. Im lepiej instrumentujesz obsługę czcionek, tym bardziej niezawodny staje się Twój pipeline dokumentów.

Masz trudny scenariusz podstawiania czcionek, z którym się mierzysz? Dodaj komentarz poniżej, a wspólnie znajdziemy rozwiązanie. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak wykrywać czcionki w Aspose.Words – Obsługa ostrzeżeń i ustawień](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Włącz ostrzeżenia o podstawianiu czcionek w Aspose.Words – Kompletny przewodnik](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Jak wczytać DOCX i wykrywać brakujące czcionki – Kompletny przewodnik C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}