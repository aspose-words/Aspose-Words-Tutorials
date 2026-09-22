---
category: general
date: 2025-12-29
description: Dowiedz się, jak ustawić DPI podczas konwertowania dokumentu Word na
  PNG za pomocą Aspose.Words. Ten krok‑po‑kroku poradnik obejmuje także eksport PNG
  w wysokiej rozdzielczości oraz ustawienia rozdzielczości obrazu.
draft: false
keywords:
- how to set dpi
- convert word to png
- save word as png
- high resolution png export
- set image resolution png
language: pl
og_description: Jak ustawić DPI przy konwertowaniu Worda na PNG przy użyciu Aspose.Words.
  Skorzystaj z tego przewodnika, aby uzyskać eksport PNG w wysokiej rozdzielczości
  i kontrolować rozdzielczość obrazu.
og_title: Jak ustawić DPI przy konwertowaniu Worda na PNG – Kompletny przewodnik C#
tags:
- Aspose.Words
- C#
- Image Export
title: Jak ustawić DPI przy konwertowaniu Worda na PNG – Kompletny przewodnik C#
url: /pl/net/programming-with-imagesaveoptions/how-to-set-dpi-when-converting-word-to-png-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak ustawić DPI przy konwertowaniu Worda na PNG – Kompletny przewodnik C#

Zastanawiałeś się kiedyś **jak ustawić DPI** podczas konwertowania dokumentu Word na PNG? Być może potrzebujesz wyraźnych zrzutów ekranu do prezentacji, albo generujesz materiały do druku, które muszą wyglądać ostro przy 300 dpi. Tak czy inaczej, trafiłeś we właściwe miejsce. W tym samouczku przeprowadzimy Cię przez konwersję wielostronicowego `.docx` na obrazy PNG o wysokiej rozdzielczości przy użyciu Aspose.Words i pokażemy dokładnie, jak ustawić rozdzielczość obrazu, aby wynik nie był rozmazany.

Podamy także wskazówki dotyczące **convert word to png**, **save word as png**, oraz osiągnięcia **high resolution png export** bez wysiłku. Bez zewnętrznych dokumentów, tylko samodzielny, gotowy do uruchomienia przykład, który możesz skopiować i wkleić do Visual Studio.

---

## Czego będziesz potrzebować

- **Aspose.Words for .NET** (najnowsza wersja, np. 24.9).  
- .NET 6+ (lub .NET Framework 4.7.2+) – dowolny nowoczesny runtime działa.  
- Plik Word (`MultiPage.docx`), który chcesz przekształcić w PNG.  
- Środowisko programistyczne – Visual Studio, Rider lub VS Code wystarczy.

To wszystko. Nie potrzebujesz dodatkowych pakietów NuGet poza Aspose.Words.

---

## Krok 1: Załaduj dokument Word

Na początek potrzebujemy reprezentacji pliku Word w pamięci. Klasa `Document` robi to za nas.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the multi‑page document from disk
Document multiPageDoc = new Document("YOUR_DIRECTORY/MultiPage.docx");
```

> **Dlaczego to ważne:** Załadowanie dokumentu daje dostęp do jego `PageCount`, którego będziemy potrzebować później, gdy powiemy Aspose, aby wyeksportował **wszystkie strony** jako PNG.

---

## Krok 2: Skonfiguruj ImageSaveOptions z ustawieniami DPI

Teraz informujemy Aspose, że chcemy wyjście w formacie PNG *i* określamy DPI. Właściwości `ImageHorizontalResolution` i `ImageVerticalResolution` to miejsce, gdzie dzieje się magia.

```csharp
// Create PNG save options and set the DPI to 300
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    // Export every page (0‑based index to PageCount‑1)
    PageSet = new PageSet(0, multiPageDoc.PageCount - 1),

    // Set image resolution – this is the “how to set dpi” part
    ImageHorizontalResolution = 300, // 300 DPI horizontally
    ImageVerticalResolution   = 300, // 300 DPI vertically

    // Give each page a friendly file name
    PageSavingCallback = (sender, args) =>
    {
        args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
    }
};
```

> **Wskazówka:** 300 dpi to de‑facto standard dla grafik gotowych do druku. Jeśli potrzebujesz jedynie jakości wyświetlanej na ekranie, 96 dpi znacznie zmniejszy rozmiar pliku.

---

## Krok 3: Zapisz wszystkie strony jako pojedynczy połączony PNG (lub osobne pliki)

Aspose pozwala albo połączyć każdą stronę w jeden ogromny połączony PNG **lub** zapisać każdą stronę w osobnym pliku. Poniższy przykład pokazuje podejście *pojedynczego połączonego* obrazu, ale `PageSavingCallback`, który dodaliśmy, już zapewnia tworzenie osobnych plików, jeśli przełączysz flagę `ExportImagesAsSeparateFiles`.

```csharp
// Save the whole document as a tiled PNG file
multiPageDoc.Save("YOUR_DIRECTORY/Pages.png", imageSaveOptions);
```

Jeśli wolisz jeden plik na stronę, po prostu ustaw:

```csharp
imageSaveOptions.ExportImagesAsSeparateFiles = true;
```

a wywołanie zwrotne zajmie się nazewnictwem każdego `Page_#.png`.

---

## Krok 4: Zweryfikuj wynik

Po uruchomieniu kodu otwórz `Pages.png` (lub wygenerowane pliki `Page_#.png`) w dowolnym przeglądarce obrazów. Powinieneś zobaczyć wyraźne, wysokiej rozdzielczości obrazy, które odzwierciedlają układ oryginalnych stron Word.

- **Sprawdzenie rozdzielczości:** Kliknij prawym przyciskiem → Właściwości → Szczegóły → Poziomy DPI / Pionowy DPI → powinno wynosić **300**.  
- **Sprawdzenie rozmiaru:** Przy 300 dpi typowa strona A4 (8,27 in × 11,69 in) ma około 2481 × 3508 pikseli – idealna do druku.

---

## Częste pułapki i jak ich uniknąć

| Problem | Dlaczego się pojawia | Rozwiązanie |
|---------|----------------------|-------------|
| **Rozmazany wynik** | DPI pozostawione domyślne (96) | Jawnie ustaw `ImageHorizontalResolution` **i** `ImageVerticalResolution`. |
| **Brakujące strony** | `PageSet` obejmuje tylko podzbiór | Użyj `new PageSet(0, multiPageDoc.PageCount - 1)`, aby uwzględnić wszystkie strony. |
| **Kolizje nazw plików** | Brak ustawionego wywołania zwrotnego | Dostarcz `PageSavingCallback`, który generuje unikalne nazwy. |
| **Duży rozmiar pliku** | 600 dpi lub wyższe bez potrzeby | Wybierz najniższe DPI, które nadal spełnia wymagania jakościowe. |
| **Błędy braku pamięci** przy dużych dokumentach | Eksportowanie ogromnego połączonego PNG | Przełącz na `ExportImagesAsSeparateFiles = true`, aby zapisywać każdą stronę osobno. |

---

## Zaawansowane: Eksport do różnych wariantów PNG

Czasami potrzebujesz **przezroczystego tła** lub **innej głębi kolorów**. Aspose.Words obsługuje te zmiany poprzez `PngOptions` w `ImageSaveOptions`.

```csharp
imageSaveOptions.PngOptions = new PngOptions
{
    // Enable transparency
    Transparency = true,

    // 8‑bit color depth (smaller file) or 24‑bit for full color
    BitDepth = 24
};
```

Możesz także połączyć to z powyższymi ustawieniami DPI, aby uzyskać **high resolution png export**, gotowy zarówno do sieci, jak i druku.

---

## Pełny działający przykład

Poniżej znajduje się kompletny, gotowy do skopiowania program. Wystarczy zamienić `YOUR_DIRECTORY` na rzeczywistą ścieżkę na twoim komputerze.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/MultiPage.docx");

        // 2️⃣ Configure PNG export with 300 DPI
        ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Png)
        {
            PageSet = new PageSet(0, doc.PageCount - 1),
            ImageHorizontalResolution = 300,
            ImageVerticalResolution = 300,
            // Optional: separate files per page
            // ExportImagesAsSeparateFiles = true,

            // 3️⃣ Friendly file names for each page
            PageSavingCallback = (sender, args) =>
            {
                args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
            },

            // 4️⃣ High‑resolution PNG tweaks (transparent background, 24‑bit)
            PngOptions = new PngOptions
            {
                Transparency = true,
                BitDepth = 24
            }
        };

        // 5️⃣ Save – either a tiled PNG or separate files
        doc.Save("YOUR_DIRECTORY/Pages.png", options);

        Console.WriteLine("Conversion complete! Check YOUR_DIRECTORY for the PNG files.");
    }
}
```

Uruchom program, a otrzymasz **high resolution PNG export** każdej strony, każdą w dokładnie ustawionym DPI.

---

## Najczęściej zadawane pytania

**P: Czy to działa ze starszymi plikami `.doc`?**  
O: Zdecydowanie tak. Aspose.Words abstrahuje format, więc ten sam kod obsługuje `.doc`, `.docx`, `.rtf` i nawet `.odt`.

**P: Czy mogę wyeksportować do JPEG zamiast PNG?**  
O: Tak – po prostu zmień `SaveFormat.Png` na `SaveFormat.Jpeg` i w razie potrzeby dostosuj `JpegOptions`.

**P: Co zrobić, jeśli potrzebuję 600 dpi do dużego plakatu?**  
O: Ustaw `ImageHorizontalResolution = 600` i `ImageVerticalResolution = 600`. Monitoruj zużycie pamięci; wysokie wartości DPI szybko zwiększają wymiary w pikselach.

**P: Czy istnieje sposób na przetwarzanie wsadowe wielu plików Word?**  
O: Owiń powyższą logikę w pętlę `foreach (var file in Directory.GetFiles(folder, "*.docx"))`. Pamiętaj o zwolnieniu każdego obiektu `Document` lub ponownym użyciu jednego obiektu `ImageSaveOptions` dla wydajności.

---

## Zakończenie

Omówiliśmy **jak ustawić DPI** przy **konwertowaniu Worda na PNG** przy użyciu Aspose.Words, poruszyliśmy niuanse **high resolution PNG export**, i dostarczyliśmy gotowy do uruchomienia przykład kodu, który **save word as png** z precyzyjną kontrolą rozdzielczości obrazu. Poprzez dostosowanie `ImageHorizontalResolution`, `ImageVerticalResolution` oraz opcjonalnie `PngOptions`, możesz generować grafiki gotowe do druku lub lekkie zasoby internetowe z pewnością.

Następne kroki? Spróbuj eksperymentować z różnymi wartościami DPI, przełącz się na eksport do osobnych plików lub połącz ten przepływ pracy z pipeline'em PDF‑do‑PNG, aby obsłużyć szerszy zakres dokumentów. Te same zasady mają zastosowanie, gdy **set image resolution png** dla innych formatów, więc jesteś teraz przygotowany do obsługi szerokiego zakresu scenariuszy eksportu obrazów.

Miłego kodowania i niech Twoje PNG będą zawsze ostra jak brzytwa!

![How to set DPI when converting Word to PNG – example output](/images/how-to-set-dpi-word-to-png.png "how to set dpi")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}