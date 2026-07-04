---
category: general
date: 2026-04-24
description: Jak wykrywać podstawianie brakujących czcionek w Aspose.Words przy użyciu
  C#. Ten przewodnik pokazuje, jak niezawodnie obsługiwać brakujące czcionki za pomocą
  ostrzeżeń FontSettings.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: pl
og_description: Jak wykrywać podstawianie brakujących czcionek w Aspose.Words przy
  użyciu C#. Dowiedz się, jak obsługiwać brakujące czcionki za pomocą ostrzeżeń FontSettings.
og_title: Jak wykrywać podstawienia w Aspose.Words – Kompletny przewodnik
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Jak wykrywać podstawianie w Aspose.Words – obsługa brakujących czcionek
url: /pl/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wykrywać podstawianie czcionek w Aspose.Words – Obsługa brakujących czcionek

Zastanawiałeś się kiedyś **jak wykrywać podstawianie**, gdy dokument próbuje użyć czcionki, której nie ma zainstalowanej na Twoim serwerze? To powszechny problem, szczególnie przy generowaniu plików PDF lub Word w zautomatyzowanym potoku. Dobrą wiadomością jest to, że Aspose.Words udostępnia wbudowany mechanizm, który pozwala wykryć taką sytuację, a także **obsługiwać brakujące czcionki** w elegancki sposób.

W tym samouczku przejdziemy przez praktyczny przykład, który pokazuje **jak wykrywać podstawianie** za pomocą zdarzenia `FontSettings.Warning`, oraz wyjaśnimy, jak **obsługiwać brakujące czcionki** bez przerywania przepływu przetwarzania. Po zakończeniu będziesz mieć gotowy fragment kodu, jasne zrozumienie, dlaczego każda linia ma znaczenie, oraz kilka wskazówek, jak uniknąć typowych pułapek.

## Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa także na .NET Framework)  
- Aspose.Words for .NET (pakiet NuGet `Aspose.Words`) – wersja 23.11 lub nowsza  
- Przykładowy dokument odwołujący się do czcionki, której nie masz zainstalowanej (np. `MissingFont.docx`)  
- Visual Studio, VS Code lub dowolne IDE C#, którego używasz  

Nie wymaga dodatkowej konfiguracji poza dodaniem pakietu NuGet.

---

## Jak wykrywać podstawianie przy użyciu FontSettings

Podstawą **jak wykrywać podstawianie** jest zdarzenie `FontSettings.Warning`. Gdy Aspose.Words nie może znaleźć żądanej czcionki, generuje ostrzeżenie `WarningType.FontSubstitution`. Subskrybując to zdarzenie, otrzymujesz powiadomienie w czasie rzeczywistym, zawierające oryginalną nazwę czcionki oraz czcionkę używaną jako zamiennik.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Dlaczego to działa:**  
- `LoadOptions.FontSettings` informuje Aspose.Words, aby użył obiektu `FontSettings`, który właśnie utworzyłeś.  
- Subskrypcja `Warning` daje jedno miejsce do monitorowania *wszystkich* problemów związanych z czcionkami, nie tylko brakujących.  
- Filtr `WarningType.FontSubstitution` zapewnia, że reagujesz wyłącznie na dokładnie taki scenariusz, który Cię interesuje – istota **jak wykrywać podstawianie**.

### Oczekiwany wynik

Uruchomienie powyższego kodu z dokumentem odwołującym się do nieistniejącej czcionki wypisze coś w stylu:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Jeśli dokument używa wyłącznie zainstalowanych czcionek, konsola pozostaje cicha – wyraźny sygnał, że **jak wykrywać podstawianie** zakończyło się sukcesem bez fałszywych alarmów.

## Elegancka obsługa brakujących czcionek

Wykrycie podstawienia to dopiero połowa sukcesu; potrzebujesz także strategii, aby **obsługiwać brakujące czcionki**, tak by końcowy wynik wyglądał zgodnie z oczekiwaniami. Poniżej trzy praktyczne podejścia, które możesz łączyć.

### 1. Udostępnij folder z czcionkami zapasowymi

Aspose.Words może przeszukiwać dodatkowe katalogi w poszukiwaniu czcionek. Wskazując mu folder zawierający najczęściej używane czcionki, zmniejszasz ryzyko podstawienia.

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**Dlaczego:** Gdy oryginalna czcionka jest nieobecna, Aspose.Words ma teraz znany zestaw alternatyw, co często daje bardziej przewidywalny rezultat wizualny.

### 2. Zastąp brakujące czcionki programowo

Jeśli potrzebujesz pełnej kontroli, możesz po wykryciu zamienić brakującą czcionkę na konkretną.

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**Dlaczego:** Dzięki temu silnik dokładnie wie, które czcionki ma wypróbować, co pozwala egzekwować firmowe standardy brandingowe lub dostępności.

### 3. Loguj i przerywaj (gdy podstawienie jest nieakceptowalne)

Czasami brakująca czcionka oznacza, że dokument jest nieważny w Twoim scenariuszu (np. formularze prawne). W takim wypadku możesz od razu rzucić wyjątek, gdy tylko wystąpi podstawienie.

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**Dlaczego:** Natychmiastowa awaria zapobiega błędom w dalszych etapach, takim jak nieprawidłowo wyrównane tabele czy uszkodzone podpisy.

## Pełny działający przykład – wszystkie kroki razem

Poniżej znajduje się pojedynczy, gotowy do skopiowania program, który demonstruje **jak wykrywać podstawianie** *oraz* różne sposoby **obsługi brakujących czcionek**. Śmiało zakomentuj sekcje, których nie potrzebujesz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Czego się spodziewać:**  
- Jeśli `MissingFont.docx` odwołuje się do czcionki, której nie ma na maszynie, konsola wypisze ostrzeżenie o podstawieniu.  
- Zapisany `Processed.docx` użyje czcionki zapasowej, którą skonfigurowałeś (lub domyślnej biblioteki).  
- Nie pojawią się nieobsłużone wyjątki, chyba że celowo przerwiesz działanie przy podstawieniu.

## Częste pytania i przypadki brzegowe

| Pytanie | Odpowiedź |
|----------|--------|
| *Co zrobić, jeśli dokument zawiera wiele brakujących czcionek?* | Zdarzenie ostrzeżenia uruchamia się dla **każdego** podstawienia, więc zobaczysz wiele linii. Możesz je zagregować w listę i przygotować raport podsumowujący. |
| *Czy to działa przy konwersji do PDF?* | Zdecydowanie tak. Te same `FontSettings` są respektowane przy wywołaniu `doc.Save("out.pdf")`. Ostrzeżenie o podstawieniu nadal się pojawia, pozwalając zweryfikować wizualną wierność PDF‑a. |
| *Czy mogę wykrywać podstawienie po załadowaniu dokumentu?* | Nie bezpośrednio. Ostrzeżenie jest generowane **podczas** ładowania lub zapisywania. Jeśli potrzebna jest analiza po załadowaniu, przechwyć ostrzeżenia w kolekcji w fazie ładowania. |
| *A co z własnymi czcionkami osadzonymi w DOCX?* | Osadzone czcionki są traktowane jako dostępne, więc nie dochodzi do podstawienia. Jeśli osadzona czcionka jest uszkodzona, Aspose.Words i tak generuje ostrzeżenie, które możesz przechwycić w ten sam sposób. |
| *Czy to wpływa na wydajność?* | Minimalnie. Sprawdzanie ostrzeżeń jest lekkie; prawdziwy koszt to ładowanie dokumentu. Dodanie folderu z czcionkami może nieco wydłużyć czas wyszukiwania, ale tylko przy pierwszym ładowaniu. |

## Porady ekspertów i pułapki, których należy unikać

- **Porada eksperta:** Zawsze ustaw `recursive: true`, gdy wskazujesz folder z wieloma czcionkami; w przeciwnym razie podfoldery zostaną pominięte.  
- **Uwaga:** Wrażliwość na wielkość liter w Linuksie. Nazwy czcionek są niewrażliwe na wielkość liter w Windows, ale nie w Linuksie, więc używaj dokładnej nazwy lub dodaj obie warianty.  
- **Pamiętaj:** Jeśli działasz w środowisku kontenerowym, upewnij się, że folder z czcionkami jest częścią obrazu lub zamontowany w czasie działania.  
- **Wskazówka:** Przechowuj ostrzeżenia w `List<string>`, jeśli potrzebujesz przedstawić podsumowanie użytkownikom końcowym lub zalogować je w systemie monitoringu.  

## Zakończenie

Omówiliśmy **jak wykrywać podstawianie** brakujących czcionek w Aspose.Words, przedstawiliśmy kilka metod **obsługi brakujących czcionek** oraz dostarczyliśmy kompletny, gotowy do uruchomienia przykład, który możesz wkleić do dowolnego projektu .NET. Dzięki wykorzystaniu zdarzenia `FontSettings.Warning` zyskujesz wgląd w problemy z czcionkami w czasie rzeczywistym, a dzięki folderom zapasowym lub regułom zamiany zapewniasz, że wynik wygląda dokładnie tak, jak tego oczekujesz.

Gotowy na kolejny krok? Spróbuj rozszerzyć rozwiązanie o automatyczne osadzanie czcionki zapasowej w generowanym PDF lub podłącz obsługę ostrzeżeń do scentralizowanego systemu logowania w dużych potokach dokumentów. Wzorce, które dziś omówiliśmy – wykrywanie zdarzeniowe, elegancka alternatywa i wyraźne obsługiwanie błędów – mają zastosowanie w wielu innych API Aspose, więc jesteś już przygotowany, by stawić czoła wyzwaniom związanym z czcionkami w całym ekosystemie.

Masz więcej pytań dotyczących obsługi czcionek, konwersji PDF lub trików w Aspose.Words? Zostaw komentarz poniżej i powodzenia w kodowaniu!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}