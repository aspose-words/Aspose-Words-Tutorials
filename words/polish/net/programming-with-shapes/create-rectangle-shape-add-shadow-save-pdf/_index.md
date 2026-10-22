---
category: general
date: 2026-02-24
description: Utwórz prostokątny kształt w C# przy użyciu Aspose.Words, dodaj cień
  do kształtu i zapisz dokument jako PDF. Dowiedz się, jak dodać cień i jak zapisać
  PDF w kilka minut.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: pl
og_description: Utwórz prostokątny kształt w C# przy użyciu Aspose.Words, następnie
  dodaj cień do kształtu i zapisz dokument jako PDF – kompletny, krok po kroku przewodnik.
og_title: Utwórz kształt prostokąta, dodaj cień i zapisz jako PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: Utwórz kształt prostokąta, dodaj cień i zapisz PDF
url: /pl/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz prostokątny kształt, dodaj cień i zapisz jako PDF

Kiedykolwiek potrzebowałeś **utworzyć prostokątny kształt** w dokumencie Word, ale chciałeś także ładny cień i wyjście w formacie PDF? Nie jesteś sam. W wielu projektach raportowych lub generujących faktury wykończenie wizualne — takie jak subtelny cień — decyduje o różnicy między „kolejnym plikiem” a „dokumentem klasy profesjonalnej”.

W tym samouczku przejdziemy krok po kroku przez to: użycie **Aspose.Words for .NET** do stworzenia prostokątnego kształtu, dodania cienia oraz **zapisania dokumentu jako PDF**. Po zakończeniu będziesz mieć gotową aplikację konsolową w C#, która generuje PDF z cieniowanym prostokątem, a także zrozumiesz, jak dostosować cień lub zmienić opcje eksportu.

## Co będzie potrzebne

- .NET 6 SDK (lub dowolna nowsza wersja .NET) – API działa tak samo na .NET Framework 4.x.  
- Pakiet NuGet **Aspose.Words for .NET** (`Aspose.Words`) – zainstaluj go poleceniem `dotnet add package Aspose.Words`.  
- Edytor kodu – Visual Studio, VS Code lub Rider będą odpowiednie.  

Nie ma dodatkowych kroków licencyjnych w tym przykładzie; tryb darmowej ewaluacji wystarczy, aby zobaczyć wynikowy PDF.

## Krok 1: Utwórz projekt i zaimportuj przestrzenie nazw

Na początek uruchommy projekt konsolowy i wczytajmy klasy, które będą potrzebne.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Dlaczego to ważne:* `Document` i `DocumentBuilder` dają nam „płótno”, a `Shape` i `ShadowFormat` pozwalają rysować i stylizować prostokąt. Importowanie ich od razu utrzymuje późniejszy kod schludnym.

## Krok 2: **Utwórz prostokątny kształt** o żądanych wymiarach

Teraz faktycznie tworzymy pusty dokument i wstawiamy prostokąt. Zwróć uwagę, że metoda `InsertShape` zwraca obiekt `Shape`, który od razu możemy stylizować.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Wyjaśnienie*: Rozmiar podawany jest w punktach (1 pt = 1/72 in). Dostosuj liczby do swojego układu. Dajemy kształtowi jasnoniebieskie wypełnienie, aby cień był widoczny.

## Krok 3: **Dodaj cień do kształtu** – doprecyzuj efekt

Cień to nie tylko „włącz/wyłącz”. Możesz kontrolować jego kolor, rozmycie, odległość, kierunek i nawet przezroczystość. Oto praktyczna konfiguracja, która sprawdza się w większości raportów.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Dlaczego możesz chcieć zmienić te wartości:*  
- **BlurRadius** – zwiększ, aby uzyskać efekt rozmycia, zmniejsz, aby uzyskać wyraźną krawędź.  
- **Direction** – 0° wskazuje w prawo, 90° w dół, 180° w lewo itd. Obróć, aby dopasować do układu strony.  
- **Transparency** – ustaw `0` dla pełnego cienia, `0.5` dla półprzezroczystego itp.

### Jak dodać cień – alternatywne podejścia

Jeśli potrzebujesz **cienia wielowarstwowego** (np. ciemniejszy cień zewnętrzny i jaśniejszy wewnętrzny), możesz utworzyć drugi kształt, przesunąć go i ustawić inny `ShadowFormat`. Albo, aby uzyskać szybki efekt „bez rozmycia”, ustaw `BlurRadius = 0`.

## Krok 4: **Zapisz dokument jako PDF** – końcowy eksport

Gdy prostokąt i jego cień są gotowe, ostatnim krokiem jest zapisanie pliku jako PDF. Aspose.Words obsługuje konwersję wewnętrznie; wystarczy wywołać `Save` z żądanym formatem.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Wskazówka*: Jeśli musisz kontrolować zgodność PDF (PDF/A, PDF/X) lub osadzić czcionki, użyj przeciążenia:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

To właśnie **jak zapisać PDF** w skrócie.

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do `Program.cs`. Kompiluje się i działa od razu (upewnij się tylko, że folder wyjściowy istnieje).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Oczekiwany rezultat

Otwórz wygenerowany plik `ShadowRectangle.pdf`. Zobaczysz jedną stronę z jasnoniebieskim prostokątem, miękkim szarym cieniem przesuniętym o 45° w dół‑w prawo oraz czystymi krawędziami. PDF powinien być wyświetlany w każdym nowoczesnym czytniku (Adobe Acrobat, Edge, Chrome).

![Utwórz prostokątny kształt z cieniem w PDF](/images/shadow-rectangle.png "Utwórz prostokątny kształt z cieniem w PDF")

*(Tekst alternatywny obrazu zawiera główne słowo kluczowe pod kątem SEO.)*

## Częste pytania i obsługa wyjątków

**Co zrobić, gdy cień znika w PDF?**  
Upewnij się, że używasz najnowszej wersji Aspose.Words (≥23.3). Starsze wersje miały błąd, w którym niektóre właściwości cienia były pomijane podczas konwersji do PDF.

**Czy mogę zmienić kolor cienia, aby pasował do mojej marki?**  
Oczywiście — po prostu zamień `System.Drawing.Color.Gray` na dowolny `Color`, np. `Color.FromArgb(128, 0, 0, 255)` dla półprzezroczystego niebieskiego.

**Jak dodać cień do innych kształtów (elipsa, gwiazda itp.)?**  
Ten sam `ShadowFormat` działa dla każdego obiektu `Shape`. Po utworzeniu kształtu pobierz jego `ShadowFormat` i ustaw właściwości.

**Co z DPI lub skalowaniem?**  
Renderowanie PDF respektuje rozmiar kształtu w punktach. Jeśli potrzebujesz wyższej rozdzielczości (np. do druku), dostosuj wymiary kształtu lub ustaw `PdfSaveOptions.ImageResolution`.

**Czy mogę eksportować do innych formatów, np. PNG?**  
Tak — po prostu wywołaj `document.Save("output.png", SaveFormat.Png)`. Cień zostanie wyrenderowany w ten sam sposób.

## Porady profesjonalistów i dobre praktyki

- **Wykorzystuj ponownie builder**: Jeśli dodajesz wiele kształtów, trzymaj jedną instancję `DocumentBuilder`; jest to tańsze niż tworzenie wielu.  
- **Zapis wsadowy**: Generując wiele PDF‑ów w pętli, ponownie używaj obiektu `PdfSaveOptions`, aby uniknąć wielokrotnych alokacji.  
- **Testowanie**: Zawsze otwieraj PDF po zapisaniu, aby zweryfikować, że cień jest widoczny. Niektóre przeglądarki renderują cienie nieco inaczej; Adobe Acrobat jest najpewniejszym odniesieniem.  
- **Wydajność**: W dużych dokumentach wyłącz automatyczne podziały stron przy `DocumentBuilder.InsertShape`, ustawiając `builder.PageSetup.DifferentFirstPageHeaderFooter = false`, jeśli nie są potrzebne.

## Zakończenie

Omówiliśmy wszystko, co potrzebne, aby **utworzyć prostokątny kształt**, **dodać cień do kształtu** i **zapisać dokument jako PDF** przy użyciu Aspose.Words for .NET. Kod jest zwięzły, koncepcje wyjaśnione, a Ty masz solidną bazę do eksperymentowania z innymi kształtami, stylami cieni i opcjami eksportu.  

Co dalej? Spróbuj zamienić prostokąt na zaokrąglony‑

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}