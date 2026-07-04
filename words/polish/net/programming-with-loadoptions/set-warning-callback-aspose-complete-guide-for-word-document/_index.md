---
category: general
date: 2026-05-23
description: Ustaw callback ostrzeżeń Aspose, aby przechwytywać ostrzeżenia o podstawianiu
  czcionek w Aspose.Words. Poznaj LoadOptions, FontSettings i implementację IWarningCallback.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: pl
og_description: Ustaw callback ostrzeżeń Aspose, aby monitorować podstawianie czcionek
  w Aspose.Words. Ten tutorial pokazuje użycie LoadOptions, FontSettings oraz implementację
  obsługi ostrzeżeń.
og_title: Ustaw ostrzeżenie zwrotne aspose – przewodnik krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: Ustawienie funkcji zwrotnej ostrzeżeń Aspose – Kompletny przewodnik po ładowaniu
  dokumentu Word
url: /pl/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set warning callback aspose – Kompletny przewodnik ładowania dokumentów Word

Zastanawiałeś się kiedyś, jak **set warning callback aspose**, aby nigdy nie przegapić alertu o podstawieniu czcionki? Nie jesteś sam. Gdy plik DOCX odwołuje się do czcionki, która nie jest zainstalowana, Aspose.Words cicho ją zamienia, a bez odpowiedniego callbacku możesz nigdy nie dowiedzieć się, że coś się zmieniło.

W tym tutorialu przeprowadzimy Cię przez pełny, gotowy do uruchomienia przykład, który dokładnie pokazuje, jak przechwycić te ostrzeżenia. Po zakończeniu zrozumiesz **Aspose.Words LoadOptions**, jak skonfigurować **FontSettings** oraz dlaczego implementacja **IWarningCallback** jest najczystszym sposobem, aby być na bieżąco. Bez zbędnych dodatków — tylko kod, który możesz od razu wkleić do projektu .NET.

## What You’ll Learn

- Jak **set warning callback aspose** na instancji `LoadOptions`.  
- Rola **Aspose.Words LoadOptions** przy otwieraniu dokumentu.  
- Konfigurowanie obsługi **Aspose fonts substitution** za pomocą `FontSettings`.  
- Tworzenie własnej implementacji **IWarningCallback** w celu logowania problemów z czcionkami.  
- Bezpieczne ładowanie dokumentu zgodnie z najlepszymi praktykami **Aspose document loading**.

### Prerequisites

- .NET 6.0 lub nowszy (kod działa także na .NET Framework 4.5+).  
- Ważna licencja Aspose.Words for .NET lub klucz trial.  
- Visual Studio, Rider lub dowolny edytor C#, którego używasz.  
- Przykładowy DOCX (`fontTest.docx`) odwołujący się do brakującej czcionki (opcjonalny, ale przydatny).

> **Pro tip:** Jeśli nie masz DOCX z brakującą czcionką, po prostu zmień nazwę czcionki w stylu dokumentu i obserwuj, jak pojawia się ostrzeżenie.

---

## How to set warning callback aspose for document loading

Poniżej znajduje się kompletny, samodzielny program. Zapisz go jako `Program.cs`, przywróć pakiety NuGet i uruchom. Konsola wypisze każde ostrzeżenie o podstawieniu czcionki generowane przez Aspose.Words podczas ładowania pliku.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### Expected console output

Jeśli `fontTest.docx` odwołuje się do czcionki, której nie ma zainstalowanej, zobaczysz coś takiego:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

Jeśli wszystkie czcionki są dostępne, jedyną wypisaną linią będzie *Document loaded successfully* — bez ostrzeżeń, bez szumu.

![przykład set warning callback aspose](image.png "set warning callback aspose example")

---

## Understanding LoadOptions in Aspose.Words

`LoadOptions` to brama do wszystkich ustawień, które możesz wprowadzić przy **aspose document loading**. Pozwala on na:

1. **Określenie własnego `FontSettings`** – przydatne, gdy aplikacja dostarcza własne czcionki.  
2. **Dołączenie callbacku ostrzeżeń** – dokładnie to, co zrobiliśmy, aby przechwycić podstawienia czcionek.  
3. Kontrolę wykrywania formatu dokumentu, obsługi haseł i wiele więcej.

Ponieważ `LoadOptions` jest przekazywany do konstruktora `Document`, ustawienia są stosowane **jednorazowo**, w momencie parsowania pliku. Dlatego możemy zagwarantować, że nasz handler ostrzeżeń zobaczy każde podstawienie, zanim dokument zostanie w pełni załadowany do pamięci.

### When to use a custom LoadOptions

- **Batch processing** wielu plików, gdzie potrzebna jest jednolita strategia logowania.  
- **Cloud services**, które muszą zgłaszać brakujące czcionki zwracając je wywołującemu.  
- **Testing pipelines**, które weryfikują, czy dokumenty spełniają firmową politykę czcionek.

---

## Configuring FontSettings for Aspose fonts substitution

Obiekt `FontSettings` kontroluje, jak Aspose.Words rozwiązuje czcionki. Domyślnie przeszukuje foldery systemowe, a następnie korzysta z wbudowanych substytutów. Możesz doprecyzować to zachowanie:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

Te linie są opcjonalne w podstawowym scenariuszu „set warning callback aspose”, ale ilustrują, jak można **zredukować** liczbę ostrzeżeń o podstawieniach, dostarczając odpowiednie czcionki z wyprzedzeniem.

---

## Implementing IWarningCallback for font substitution warnings

Interfejs `IWarningCallback` jest niewielki — zawiera tylko jedną metodę `Warning`. Mimo to daje **pełną kontrolę** nad tym, jak obsługujesz ostrzeżenia:

- **Logowanie do pliku** zamiast konsoli.  
- **Zbieranie ostrzeżeń** w liście do późniejszej analizy.  
- **Rzucanie wyjątków** przy krytycznych ostrzeżeniach (np. gdy wymagana czcionka jest brakująca).

Oto szybki przykład, który przechowuje ostrzeżenia w `List<string>`:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Możesz potem sprawdzić `handler.Messages` po załadowaniu dokumentu, aby zdecydować, czy przerwać przetwarzanie.

---

## Loading a document with custom warning handling (full workflow)

Łącząc wszystko razem, ostateczny wzorzec, którego prawdopodobnie będziesz używać, wygląda tak:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

Ten fragment demonstruje przepływ **aspose document loading**, którego użyjesz w produkcji: konfiguracja, ładowanie, a następnie reakcja. Wzorzec skaluje się zarówno przy przetwarzaniu jednego pliku, jak i przy iteracji po tysiącach.

---

## Common Questions & Edge Cases

**Co zrobić, jeśli dokument jest zabezpieczony hasłem?**  
Dodaj `Password = "secret"` do inicjalizatora `LoadOptions`. Callback ostrzeżeń nadal działa po odszyfrowaniu pliku.

**Czy callback uruchomi się dla innych typów ostrzeżeń?**  
Tak — `WarningInfo.Type` może być `DocumentStructure`, `UnsupportedFileFormat` itp. W naszym przykładzie filtrujemy tylko `FontSubstitution`, ale możesz logować wszystko, usuwając warunek `if`.

**Czy to wpływa na wydajność?**  
Znikomo. Callback jest wywoływany wyłącznie w momencie wystąpienia ostrzeżenia, co jest znacznie rzadsze niż standardowe kroki parsowania.

**Czy mogę całkowicie wyłączyć podstawianie czcionek?**  
Możesz ustawić `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;`, ale wtedy Aspose.Words rzuci wyjątek przy brakujących czcionkach zamiast je zamienić.

---

## Conclusion

Teraz wiesz dokładnie, jak **set warning callback aspose**, aby monitorować zdarzenia podstawiania czcionek podczas przetwarzania **Aspose.Words LoadOptions**. Konfigurując `FontSettings`, implementując lekki `IWarningCallback` i ładując dokument z tymi opcjami, uzyskasz pełną widoczność wszelkich zmian czcionek wprowadzanych przez Aspose „za kulisami”.

Od tego momentu możesz:

- Rozszerzyć handler ostrzeżeń, aby zapisywał je w centralnym serwisie logowania.  
- Połączyć callback z własną strategią awaryjnego wyboru czcionek.  
- Użyć tego wzorca przy budowie API w chmurze, które waliduje dokumenty przesyłane przez klientów.

Wypróbuj to na własnych plikach DOCX, dostosuj `FontSettings` i obserwuj, jak konsola informuje Cię dokładnie, które czcionki zostały zamienione. Szczęśliwego kodowania i niech Twoje dokumenty zawsze renderują się tak, jak zamierzasz!

## Related Tutorials

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}