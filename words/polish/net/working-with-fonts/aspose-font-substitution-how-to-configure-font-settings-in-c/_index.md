---
category: general
date: 2026-03-27
description: 'Łatwa zamiana czcionek Aspose: dowiedz się, jak konfigurować ustawienia
  czcionek, przechwytywać ostrzeżenia i obsługiwać brakujące czcionki w aplikacjach
  .NET.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: pl
og_description: Opanuj zamianę czcionek w Aspose, konfigurować ustawienia czcionek
  i obsługiwać brakujące czcionki za pomocą funkcji zwrotnej ostrzeżenia. Kompletny
  przewodnik C#.
og_title: Zastępowanie czcionek Aspose – Konfiguracja ustawień czcionek w C#
tags:
- Aspose.Words
- C#
- Font Management
title: Zastępowanie czcionek Aspose – Jak skonfigurować ustawienia czcionek w C#
url: /pl/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Kompletny przewodnik po konfigurowaniu ustawień czcionek

Czy kiedykolwiek natrafiłeś na dokument, który nagle zamienia twoją niestandardową czcionkę na coś ogólnego? To **aspose font substitution** wykonuje swoją pracę — zastępuje brakujące czcionki najbliższym dopasowaniem, które może znaleźć. To przydatne, ale jeśli musisz dokładnie wiedzieć, która czcionka została zamieniona, musisz skorzystać z systemu ostrzeżeń biblioteki i samodzielnie skonfigurować ustawienia czcionek.

W tym samouczku przeprowadzimy Cię przez rzeczywisty scenariusz: wczytanie pliku DOCX, który odwołuje się do czcionki, której nie masz, przechwycenie zdarzenia zamiany oraz wypisanie przyjaznej wiadomości na konsolę. Po zakończeniu będziesz swobodnie korzystać z **configure font settings**, podłączania **Aspose.Words warning callback** i rozszerzania przykładu do dowolnego przepływu pracy.

> **Co będzie potrzebne**  
> • .NET 6+ (or .NET Framework 4.7.2+)  
> • Aspose.Words for .NET (latest NuGet)  
> • DOCX, który odwołuje się do brakującej czcionki (nazwijmy go `MissingFont.docx`)  

Zanurzmy się.

---

## Krok 1: Zainstaluj Aspose.Words i przygotuj projekt

Zanim napiszemy jakikolwiek kod, upewnij się, że pakiet Aspose.Words jest dodany jako odwołanie:

```bash
dotnet add package Aspose.Words
```

> **Wskazówka:** Użyj najnowszej stabilnej wersji; od marca 2026 jest to 23.11.0. Nowsze wydania ulepszają algorytmy dopasowywania czcionek i dodają dodatkowe typy ostrzeżeń.

Utwórz nową aplikację konsolową (lub wstaw kod do istniejącego projektu) i dodaj standardowe dyrektywy `using`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Te przestrzenie nazw dają dostęp do `Document`, `LoadOptions` oraz klas związanych z czcionkami, których będziemy potrzebować.

## Krok 2: Skonfiguruj ustawienia czcionek za pomocą LoadOptions

Sednem kontroli **aspose font substitution** jest `LoadOptions.FontSettings`. Dostarczając pusty obiekt `FontSettings`, informujemy Aspose, aby używał domyślnych ścieżek wyszukiwania *i* zgłaszał każdą zamianę za pomocą callbacku ostrzeżeń.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

Dlaczego nie polegać po prostu na ustawieniach domyślnych? Ponieważ podłączenie callbacku ostrzeżeń (następny krok) działa tylko wtedy, gdy właściwość `FontSettings` nie jest null. Ta mała linijka daje nam punkt zaczepienia do procesu zamiany, nie zmieniając rzeczywistego zachowania wyszukiwania czcionek.

## Krok 3: Dołącz callback ostrzeżeń, aby przechwycić zamiany

Aspose.Words implementuje interfejs `IWarningCallback`. Za każdym razem, gdy zdarzy się coś godnego uwagi — np. brakująca czcionka — wywołuje naszą metodę `Warning`. Zaimplementujemy mały obsługujący kod, który filtruje `WarningType.FontSubstitution` i wypisuje opis.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

A oto sam handler:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Dlaczego to ważne** — Bez callbacku Aspose cicho zamienia czcionki i nigdy nie wiesz, której użyto. Callback czyni proces przejrzystym, co jest niezbędne przy raportowaniu zgodności lub debugowaniu problemów z układem.

## Krok 4: Wczytaj dokument używając skonfigurowanych opcji

Teraz w końcu wczytujemy dokument, przekazując `loadOptions`, które właśnie przygotowaliśmy. Jeśli plik źródłowy odwołuje się do czcionki, której nie ma zainstalowanej, nasz handler zostanie wywołany.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Zastąp `YOUR_DIRECTORY` rzeczywistą ścieżką, w której znajduje się `MissingFont.docx`. Po uruchomieniu programu powinieneś zobaczyć wyjście podobne do:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

Ten wiersz informuje dokładnie, której czcionki brakowało i jaką czcionkę zastępczą wybrało Aspose.

## Krok 5: (Opcjonalnie) Dostosuj ścieżki wyszukiwania czcionek

Jeśli masz prywatny folder z firmowymi czcionkami, możesz wskazać Aspose, gdzie szukać, zanim przejdzie do czcionek systemowych. To zaawansowane użycie **configure font settings**:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

Ustawienie `recursive: true` sprawia, że Aspose skanuje również podfoldery. Teraz biblioteka najpierw spróbuje użyć twoich prywatnych czcionek, zmniejszając ryzyko niepożądanej zamiany.

## Pełny działający przykład

Łącząc wszystko razem, oto kompletny, gotowy do uruchomienia program:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Oczekiwane wyjście** (gdy napotkano brakującą czcionkę):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

Jeśli wszystkie czcionki są dostępne, program działa cicho (bez ostrzeżeń) i nadal generuje PDF.

## Częste pytania i przypadki brzegowe

### Co zrobić, jeśli muszę *całkowicie* zapobiec zamianie?

Ustaw `FontSettings.SubstitutionSettings` na `null` lub użyj `FontSettings.FontSubstitutionSettings`, aby kontrolować zachowanie. Na przykład:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

Teraz Aspose wyrzuci wyjątek zamiast cichej zamiany, który można przechwycić i obsłużyć.

### Czy to działa z innymi formatami plików (np. .doc, .rtf)?

Zdecydowanie. Ten sam obiekt `LoadOptions` może być przekazany do dowolnego konstruktora `Document`, który przyjmuje ścieżkę do pliku. Callback ostrzeżeń zostanie wywołany dla wszystkich formatów, które korzystają z czcionek.

### Czy mogę przechwycić *dokładną* nazwę czcionki zastępczej?

Tak. Ciąg `info.Description` zawiera zarówno brakującą czcionkę, jak i zamiennik. Jeśli potrzebujesz nazwy programowo, możesz ją sparsować lub użyć obiektu `FontInfo` (dostępnego w nowszych wersjach).

### Jak to zachowuje się w środowisku wielowątkowym?

`FontSettings` nie jest **bezpieczny** wątkowo. Utwórz osobny `LoadOptions` (z własnym `FontSettings`) dla każdego wątku lub zabezpiecz dostęp przy pomocy blokady.

## Podsumowanie

Omówiliśmy wszystko, co potrzebne, aby opanować **aspose font substitution** i **configure font settings** w aplikacji C#:

1. Zainstaluj Aspose.Words i dodaj niezbędne dyrektywy `using`.  
2. Utwórz obiekt `LoadOptions` z nowym `FontSettings`.  
3. Dołącz własny `IWarningCallback`, aby wyświetlać zdarzenia zamiany.  
4. Wczytaj dokument, pozwalając callbackowi zgłaszać brakujące czcionki.  
5. (Opcjonalnie) Rozszerz ścieżkę wyszukiwania lub całkowicie wyłącz zamianę.

Mając ten wzorzec, możesz logować brakujące czcionki w celu zapewnienia zgodności, powiadamiać użytkowników w interfejsie UI lub automatycznie osadzać czcionki zastępcze przed publikacją. Następnie możesz zbadać **Aspose.Words font substitution policies** lub zintegrować ten przepływ pracy z większym potokiem przetwarzania dokumentów.

Miłego kodowania i niech Twoje dokumenty zawsze wyświetlają się z odpowiednią czcionką!  

---  

![Diagram showing Aspose.Words loading a document, invoking FontSettings, triggering a warning callback, and outputting substitution info](image-placeholder.png "aspose font substitution workflow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}