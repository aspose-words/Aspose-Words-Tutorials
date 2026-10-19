---
category: general
date: 2026-03-08
description: Niestandardowe ustawienia czcionek pozwalają ustawić parametry czcionek,
  bezpiecznie wczytać dokument Word oraz obsłużyć brakujące czcionki przy użyciu Aspose.Words.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: pl
og_description: Niestandardowe ustawienia czcionek pozwalają ustawić parametry czcionek,
  bezpiecznie wczytać dokument Word oraz obsłużyć brakujące czcionki przy użyciu Aspose.Words.
og_title: Niestandardowe ustawienia czcionek w C# – Ładowanie Worda i obsługa brakujących
  czcionek
tags:
- Aspose.Words
- C#
- Font Management
title: Niestandardowe ustawienia czcionek w C# – Ładowanie Word i obsługa brakujących
  czcionek
url: /pl/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ustawienia niestandardowych czcionek w C# – Ładowanie Word i obsługa brakujących czcionek

Zastanawiałeś się kiedyś, jak działają **ustawienia niestandardowych czcionek**, gdy plik Word odwołuje się do czcionek, których nie masz zainstalowanych? To częsty problem — dokument wygląda dobrze na jednym komputerze, a nagle każdy akapit przechodzi na czcionkę zapasową na innym.  

Dobra wiadomość? Dzięki Aspose.Words możesz **ustawić ustawienia czcionek**, **załadować zawartość dokumentu Word** i **obsłużyć brakujące czcionki** w jednym schludnym przepływie. Poniżej znajdziesz kompletny, gotowy do uruchomienia przykład, który pokazuje dokładnie, jak to zrobić, oraz „dlaczego” każdego kroku.

## Czego się nauczysz

W tym przewodniku omówimy:

* Tworzenie obiektu `LoadOptions` i podłączanie do niego instancji `FontSettings`.  
* Rejestrowanie callbacku ostrzeżeń, aby zobaczyć, które czcionki zostały zastąpione.  
* Ładowanie pliku DOCX, który może mieć brakujące czcionki, oraz wypisywanie szczegółów substytucji na konsolę.  

Po zakończeniu będziesz mógł z pewnością wypuścić swoją aplikację C#, wiedząc, że każdy scenariusz brakującej czcionki jest logowany i może być później rozwiązany.

> **Wymagania wstępne:** Aspose.Words for .NET (v23.12 lub nowszy) zainstalowany przez NuGet oraz podstawowa znajomość aplikacji konsolowych C#.

---

## Ustawienia niestandardowych czcionek – konfiguracja LoadOptions

Pierwszą rzeczą, której potrzebujesz, jest obiekt `LoadOptions`. Informuje on Aspose.Words, jak traktować wczytywany plik. Przypisując nową instancję `FontSettings`, dajemy bibliotece miejsce, w którym ma szukać niestandardowych czcionek.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Dlaczego to ważne:**  
Jeśli pominiesz `FontSettings`, Aspose.Words domyślnie użyje kolekcji czcionek systemowych. To oznacza, że każda brakująca czcionka zostanie cicho zastąpiona i nie dowiesz się, które elementy zostały podmienione. Tworząc wyraźny kontener `FontSettings`, zyskujesz pełną kontrolę nad procesem wyszukiwania.

---

## Ustawienie Font Settings w LoadOptions

Teraz, gdy mamy obiekt `FontSettings`, możesz się zastanawiać, gdzie go skierować. Zazwyczaj dodaje się folder zawierający czcionki, które dystrybuujesz wraz z aplikacją:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Jeśli nie masz prywatnego folderu, możesz pominąć ten blok — Aspose.Words nadal zgłosi brakujące czcionki za pośrednictwem callbacku ostrzeżeń.*

**Wskazówka:** Użyj flagi `recursive: true`, jeśli Twoje czcionki są rozproszone w podfolderach. Dzięki temu nie będziesz musiał ręcznie dodawać każdej ścieżki.

---

## Ładowanie dokumentu Word z niestandardowymi ustawieniami czcionek

Po przygotowaniu opcji ładowanie dokumentu jest banalne. Konstruktor `Document` przyjmuje ścieżkę do pliku oraz `LoadOptions`, które właśnie stworzyliśmy.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**Co się dzieje w tle?**  
Aspose.Words parsuje DOCX, sprawdza każde odwołanie `<w:font>` i korzysta z podanych `FontSettings`. Jeśli czcionka nie zostanie znaleziona, wywoływane jest ostrzeżenie typu `FontSubstitution`. Nasz własny handler (pokazany dalej) przechwyci te ostrzeżenia.

---

## Obsługa brakujących czcionek za pomocą callbacku ostrzeżeń

Interfejs `IWarningCallback` pozwala reagować na wszelkie problemy pojawiające się podczas ładowania. Implementacja jest prosta:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Gdy dokument zostanie załadowany, każda brakująca czcionka spowoduje pojawienie się linii w stylu:

```
Font substituted: Arial -> Liberation Sans
```

**Dlaczego warto to logować:**  
W środowisku produkcyjnym możesz przekierować te komunikaty do pliku lub systemu telemetrycznego, co ułatwi wykrycie, które czcionki trzeba dołączyć lub licencjonować.

---

## Pełny działający przykład

Poniżej znajduje się samodzielny program konsolowy, który łączy wszystkie elementy. Skopiuj‑wklej go do nowego projektu .NET Core i uruchom **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Oczekiwany wynik** (zakładając, że `input.docx` używa czcionki, której nie masz):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Jeśli wszystkie czcionki są dostępne, zobaczysz jedynie końcową linię potwierdzającą.

---

## Często zadawane pytania i przypadki brzegowe

| Pytanie | Odpowiedź |
|----------|-----------|
| **Co zrobić, jeśli muszę osadzić brakujące czcionki w PDF?** | Po załadowaniu wywołaj `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";`, a następnie włącz osadzanie za pomocą `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **Czy mogę zrezygnować z ostrzeżeń zamiast je logować?** | Tak — ustaw `loadOptions.WarningCallback = null;` lub zaimplementuj callback, aby ignorował ostrzeżenia nie‑dotyczące czcionek. |
| **Czy to działa z plikami `.doc` i `.rtf`?** | Oczywiście. Ten sam obiekt `LoadOptions` ma zastosowanie do każdego formatu obsługiwanego przez Aspose.Words. |
| **Czy callback jest bezpieczny wątkowo?** | Callback uruchamiany jest w tym samym wątku, który ładuje dokument, więc możesz bezpiecznie pisać na konsolę. W scenariuszach wielowątkowych użyj kolekcji współbieżnej lub frameworka logowania. |

---

## Wskazówki i pułapki

* **Wskazówka:** Jeśli dystrybuujesz czcionkę, która nie jest zainstalowana na docelowej maszynie, dodaj ją do folderu przekazywanego do `SetFontsFolder`. Zapewni to deterministyczne renderowanie.
* **Uważaj na licencje:** Niektóre czcionki wymagają komercyjnych licencji na osadzanie. Zawsze sprawdzaj EULA czcionki przed jej dołączeniem.
* **Uwaga dotycząca wydajności:** Ładowanie dużych bibliotek czcionek może spowolnić parsowanie dokumentu. Trzymaj folder schludny — dołączaj tylko te czcionki, które naprawdę są potrzebne.
* **Przypadek brzegowy:** Gdy dokument odwołuje się do czcionki po *nazwie PostScript* zamiast nazwy rodziny, Aspose.Words i tak ją rozwiąże, o ile plik czcionki znajduje się w ścieżce wyszukiwania.

---

## Podsumowanie

Masz teraz kompletny, gotowy do produkcji wzorzec używania **niestandardowych ustawień czcionek** w C#. Konfigurując `LoadOptions`, rejestrując callback ostrzeżeń i opcjonalnie wskazując prywatny folder czcionek, możesz **ustawić ustawienia czcionek**, **załadować zawartość dokumentu Word** w sposób niezawodny.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}