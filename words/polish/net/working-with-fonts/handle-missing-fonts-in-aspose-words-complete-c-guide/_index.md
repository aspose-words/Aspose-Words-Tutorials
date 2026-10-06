---
category: general
date: 2026-03-14
description: Szybko radź sobie z brakującymi czcionkami w Aspose.Words. Dowiedz się,
  jak przechwytywać ostrzeżenia o zamianie czcionek, konfigurować LoadOptions i unikać
  problemów z renderowaniem.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: pl
og_description: Obsługa brakujących czcionek w Aspose.Words przy użyciu kolektora
  ostrzeżeń. Ten samouczek pokazuje krok po kroku, jak wykrywać i rejestrować podstawienia
  czcionek.
og_title: Obsługa brakujących czcionek w Aspose.Words – Kompletny przewodnik C#
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: Obsługa brakujących czcionek w Aspose.Words – Kompletny przewodnik C#
url: /pl/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Obsługa brakujących czcionek w Aspose.Words – Kompletny przewodnik C#

Czy kiedykolwiek musiałeś **obsługiwać brakujące czcionki** podczas ładowania dokumentu Word i zastanawiałeś się, dlaczego wynikowy PDF lub obraz wygląda nieprawidłowo? Nie jesteś w tym sam. Brakujące pliki czcionek są cichym sprawcą problemów, który może zamienić perfekcyjnie zaprojektowany raport w zniekształcony bałagan.  

Dobra wiadomość? Aspose.Words oferuje czysty sposób na przechwycenie zdarzeń podstawiania czcionek, ich logowanie i nawet zamianę na czcionkę zapasową, jeśli tego potrzebujesz. W tym tutorialu przeprowadzimy Cię przez kompletny, gotowy do uruchomienia przykład, który dokładnie pokazuje, jak skonfigurować kolektor ostrzeżeń, podłączyć go do `LoadOptions` i wczytać dokument, który może zawierać brakujące czcionki.

Po zakończeniu tego przewodnika będziesz w stanie:

* Wykrywać każde podstawienie czcionki, które występuje podczas ładowania dokumentu.  
* Wyświetlać przyjazny komunikat w konsoli (lub kierować go do loggera) dla każdej brakującej czcionki.  
* Rozszerzyć rozwiązanie o zamianę czcionek, jeśli zajdzie taka potrzeba.  

**Wymagania wstępne** – będziesz potrzebować:

* .NET 6.0 lub nowszy (kod działa również z .NET Core i .NET Framework).  
* Pakiet NuGet Aspose.Words for .NET (obecna wersja 23.11).  
* Plik Word, który celowo odwołuje się do czcionki, której nie masz zainstalowanej – nazwijmy go `doc-with-missing-font.docx`.  

Jeśli już czujesz się pewnie w C# i masz gotowy projekt, możesz od razu przejść do kodu. W przeciwnym razie czytaj dalej; najpierw omówimy małe kroki konfiguracji.

---

## Dlaczego obsługa brakujących czcionek ma znaczenie

Kiedy Aspose.Words ładuje dokument, próbuje dopasować każdy glif do czcionki zainstalowanej w systemie. Jeśli nie znajdzie dokładnej czcionki, cicho podstawia najbliższą pasującą. To podstawienie może zmienić wysokość linii, kerning i nawet spowodować zniknięcie znaków. Przechwytując zdarzenie `WarningType.FontSubstitution`, uzyskasz przejrzysty wgląd w **co** zostało zamienione i **dlaczego**, co jest niezbędne do:

* Utrzymania spójności marki (Twoja firmowa czcionka musi wyglądać dokładnie tak, jak zaprojektowano).  
* Debugowania problemów z konwersją PDF — często winowajcą jest brakująca czcionka.  
* Budowania zautomatyzowanych potoków dokumentów, w których musisz oznaczyć problematyczne pliki do ręcznej weryfikacji.

Teraz, gdy „dlaczego” jest jasne, przejdźmy do **jak**.

---

## Krok 1 – Konfiguracja kolektora ostrzeżeń

Pierwszą rzeczą, której potrzebujemy, jest obiekt, który może nasłuchiwać ostrzeżeń Aspose.Words. `DocumentWarnings` implementuje `IWarningCallback`, co pozwala nam reagować za każdym razem, gdy biblioteka zgłosi ostrzeżenie.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**Co się dzieje?**  
* `DocumentWarnings` jest cienką warstwą wokół interfejsu callback.  
* Lambda sprawdza `e.WarningType`, więc ignorujemy niepowiązane ostrzeżenia (np. przestarzałe funkcje).  
* `e.WarningInfo` zawiera nazwę brakującej czcionki, którą wypisujemy w konsoli.  

*Pro tip*: Zamień `Console.WriteLine` na strukturalny logger (Serilog, NLog) w środowisku produkcyjnym — w ten sposób otrzymasz automatycznie znaczniki czasu i poziomy logów.

---

## Krok 2 – Podłączenie kolektora do LoadOptions

`LoadOptions` jest strażnikiem przy każdym otwieraniu dokumentu w Aspose.Words. Przypisując naszą instancję `fontWarnings` do właściwości `WarningCallback`, zapewniamy, że kolektor jest aktywny podczas procesu ładowania.

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**Dlaczego używać LoadOptions?**  
Poza ostrzeżeniami, `LoadOptions` pozwala kontrolować obsługę haseł, kodowanie i nawet własne ładowanie zasobów. Tutaj skupiamy się na części związanej z ostrzeżeniami, ale ten sam wzorzec działa dla innych callbacków.

---

## Krok 3 – Ładowanie dokumentu z skonfigurowanymi opcjami

Teraz w końcu wczytujemy dokument do pamięci. Jeśli jakakolwiek czcionka będzie brakować, nasz kolektor wyzwoli się i zobaczysz linię w konsoli dla każdego podstawienia.

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

Jeśli uruchomisz ten fragment z dokumentem, który odwołuje się np. do *Calibri Light*, podczas gdy Twoja maszyna testowa ma tylko *Calibri*, otrzymasz wyjście podobne do:

```
Font 'Calibri Light' was substituted.
```

To cały cykl wykrywania — prosty, a jednocześnie potężny.

---

## Krok 4 – (Opcjonalnie) Zastąp brakujące czcionki znanym zamiennikiem

Czasami nie chcesz tylko logować problemu; chcesz wymusić czcionkę zapasową, aby renderowany wynik wyglądał spójnie. Aspose.Words pozwala dostarczyć własny obiekt `FontSettings`, który mapuje brakujące czcionki na zamiennik.

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**Wyjaśnienie**  
* Symbol wieloznaczny `"*"` mówi Aspose.Words, aby traktował *dowolną* brakującą czcionkę w ten sam sposób.  
* Możesz także mapować konkretne czcionki indywidualnie, jeśli potrzebujesz precyzyjnej kontroli.  
* Po ustawieniu `document.FontSettings`, każde kolejne renderowanie (PDF, obraz, HTML) respektuje to podstawienie.

---

## Pełny działający przykład

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do aplikacji konsolowej. Zawiera wszystkie wymagane dyrektywy `using`, obsługę błędów i komentarze dla przejrzystości.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**Oczekiwane wyjście** (gdy wykryta zostanie brakująca czcionka):

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

Jeśli dokument źródłowy już zawiera wszystkie wymagane czcionki, linia ostrzeżenia po prostu się nie pojawi — nie ma się czym martwić.

---

## Częste pytania i przypadki brzegowe

| Pytanie | Odpowiedź |
|----------|--------|
| **Co zrobić, jeśli chcę tylko logować, a nie zamieniać czcionki?** | Pomiń cały blok `FontSettings`; sam kolektor ostrzeżeń wystarczy. |
| **Czy mogę przekierować ostrzeżenia do pliku?** | Tak — zamień `Console.WriteLine` na `File.AppendAllText("font-warnings.log", …)`. |
| **Czy to działa dla DOC, DOCX i ODT?** | Absolutnie. `LoadOptions` obowiązuje dla wszystkich formatów obsługiwanych przez Aspose.Words. |
| **A co z własnymi czcionkami osadzonymi w dokumencie?** | Osadzone czcionki omijają mechanizm podstawiania; są używane tak, jak są. |
| **Czy to wpływa na wydajność?** | Narzut jest minimalny — wywoływany jest tylko jeden callback na brakującą czcionkę. W przypadku dużych partii rozważ agregowanie ostrzeżeń zamiast zapisywania przy każdym zdarzeniu. |

---

## Podsumowanie

Pokazaliśmy **jak obsługiwać brakujące czcionki** w Aspose.Words, podłączając kolektor `DocumentWarnings` do `LoadOptions`, opcjonalnie zamieniając je na czcionkę zapasową i zapisując wynik. Ten wzorzec daje pełną widoczność zdarzeń podstawiania czcionek, pomagając utrzymać wizualną spójność przy konwersjach do PDF, obrazu lub HTML.

Kolejne kroki, które możesz rozważyć:

* Zintegruj kolektor ostrzeżeń z centralnym frameworkiem logowania.  
* Zbuduj pulpit UI, który wyświetla listę dokumentów z brakującymi czcionkami do przetwarzania wsadowego.  
* Połącz to podejście z Aspose.PDF, aby zweryfikować, że generowane PDF-y rzeczywiście używają czcionki zapasowej.  

Śmiało eksperymentuj — zamień `"Arial"` na `"Tahoma"` lub wczytaj inny zestaw dokumentów. Główna idea pozostaje niezmienna: przechwyć ostrzeżenie, zareaguj na nie i utrzymaj dokumenty w dokładnie takim stanie, w jakim zostały zaprojektowane.

Szczęśliwego kodowania! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}