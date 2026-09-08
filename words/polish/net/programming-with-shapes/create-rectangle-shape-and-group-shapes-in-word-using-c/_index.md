---
category: general
date: 2026-09-08
description: Utwórz prostokątny kształt w dokumencie Word przy użyciu C#. Dowiedz
  się, jak ustawić rozmiar kształtu, grupować wiele kształtów oraz programowo tworzyć
  pusty dokument Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: pl
lastmod: 2026-09-08
og_description: Utwórz prostokątny kształt w dokumencie Word przy użyciu C#. Ten przewodnik
  pokazuje, jak ustawić rozmiar kształtu, grupować wiele kształtów oraz programowo
  utworzyć pusty dokument Word.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Utwórz kształt prostokąta i grupuj kształty w Wordzie przy użyciu C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Utwórz prostokątny kształt i grupuj kształty w Wordzie przy użyciu C#
url: /pl/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tworzenie prostokątnego kształtu i grupowanie kształtów w Wordzie przy użyciu C#

Jeśli potrzebujesz **utworzyć prostokątny kształt** w pliku Word, ten tutorial dostarcza kompletną, gotową do uruchomienia rozwiązanie. Zobaczysz, jak ustawić rozmiar kształtu, grupować wiele kształtów oraz stworzyć pusty dokument Word od podstaw — wszystko przy użyciu biblioteki Aspose.Words for .NET.

Praca z dokumentami Word programistycznie często przypomina żonglowanie wieloma drobnymi szczegółami. Po zakończeniu tego przewodnika będziesz mieć jedną metodę, która generuje plik `.docx` zawierający prostokąt i elipsę połączone w jedną grupę, gotowe do dalszej edycji lub drukowania.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+)
* Licencjonowaną kopię **Aspose.Words for .NET** (można użyć darmowego klucza ewaluacyjnego)
* IDE, np. Visual Studio 2022 lub Visual Studio Code
* Podstawową znajomość składni C#

Nie są wymagane dodatkowe pakiety NuGet poza `Aspose.Words`.

## Krok 1: Utworzenie pustego dokumentu Word

Pierwszym krokiem jest stworzenie pustego dokumentu, który będzie hostował kształty. Spełnia to wymóg *utworzenia pustego dokumentu Word*.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Utworzenie pustego dokumentu daje czyste płótno. Obiekt `Document` reprezentuje cały plik `.docx`, a jego `FirstSection.Body.FirstParagraph` jest domyślnym punktem wstawiania nowych węzłów.

## Krok 2: Utworzenie prostokątnego kształtu

Teraz możesz dodać prostokąt. To właśnie miejsce, w którym zachodzi operacja **utworzenia prostokątnego kształtu**.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Ustawienie wymiarów bezpośrednio odpowiada słowu kluczowemu **set shape size**. Wszystkie wartości rozmiaru wyrażone są w punktach, co zapewnia precyzyjną kontrolę nad wyglądem kształtu w finalnym dokumencie.

## Krok 3: Utworzenie dodatkowego kształtu (elipsa)

Typowym przypadkiem użycia jest połączenie kilku kształtów. Tutaj dodajemy elipsę, która później będzie współdzielić ten sam kontener.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Oba kształty są nadal niezależne. Następny krok pokaże, jak **grupować wiele kształtów** razem.

## Krok 4: Grupowanie kształtów w Wordzie

Grupowanie kształtów pozwala przesuwać, zmieniać rozmiar lub formatować je jako jedną jednostkę. Spełnia to wymagania **group shapes in word** oraz **group multiple shapes**.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

Właściwość `GroupShape.Bounds` określa układ współrzędnych dla kształtów podrzędnych. Umieszczając prostokąt i elipsę w tym samym `GroupShape`, możesz później przesuwać lub obracać je razem jednym wywołaniem.

## Krok 5: Zapisanie dokumentu

Na koniec zapisujemy dokument na dysku. Plik będzie zawierał grupowane kształty, które właśnie utworzyłeś.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

Po uruchomieniu programu otwórz `GroupedShapes.docx` w Microsoft Word. Powinieneś zobaczyć prostokąt i elipsę połączone w jedną grupę; zaznaczenie jednego kształtu zaznacza również drugi, co potwierdza, że grupowanie się powiodło.

## Pełny kod źródłowy

Skopiuj poniższy kompletny program do nowego projektu typu console‑app i uruchom go. Nie jest wymagana dodatkowa kod.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Oczekiwany wynik

Uruchomienie programu tworzy `GroupedShapes.docx`. Otwierając plik w Wordzie zobaczysz:

* **prostokąt** (100 pt × 50 pt) z niebieską obwódką i jasnoszarym wypełnieniem.
* **elipsę** (80 pt × 80 pt) z ciemnozieloną obwódką i jasnożółtym wypełnieniem.
* Oba kształty znajdują się w jednej grupie, więc przesunięcie jednego przesuwa drugi.

## Często zadawane pytania i przypadki brzegowe

| Pytanie | Odpowiedź |
|----------|-----------|
| **Czy mogę dodać więcej niż dwa kształty do grupy?** | Tak. Utwórz dodatkowe obiekty `Shape` i wywołaj `group.AppendChild(yourShape)` dla każdego z nich. |
| **Co zrobić, jeśli muszę obrócić grupę?** | Ustaw `group.RotationAngle = 45;` (stopnie). Wszystkie kształty podrzędne obrócą się razem. |
| **Czy można grupować kształty po zapisaniu dokumentu?** | Musisz zmodyfikować strukturę dokumentu przed zapisem; w przeciwnym razie trzeba wczytać plik, zlokalizować kształty i odtworzyć grupę. |
| **Czy muszę zwalniać jakieś obiekty?** | Aspose.Words zarządza własnymi zasobami, ale powinieneś zwolnić obiekty `FileStream`, jeśli otwierasz strumienie ręcznie. |
| **Czy kod zadziała z formatem .doc (binarnym)?** | Tak, zmień `doc.Save("output.doc")`. Zachowanie grupowania pozostaje identyczne. |

## Podsumowanie

Teraz wiesz, jak **utworzyć prostokątny kształt**, **ustawić rozmiar kształtu** oraz **grupować wiele kształtów** w pliku Word przy użyciu C#. To podejście umożliwia programowe budowanie złożonych diagramów, znaków wodnych lub raportów opartych na szablonach bez ręcznej edycji.

### Kolejne kroki

* Zgłęb **group shapes in word** dalej, dodając pola tekstowe lub obrazy do tej samej grupy.
* Skorzystaj z wzorca `SetShapeSize`, aby dynamicznie obliczać wymiary w zależności od układu strony.
* Połącz tę technikę z polami korespondencji seryjnej, aby generować spersonalizowane dokumenty na dużą skalę.

Śmiało eksperymentuj z różnymi typami kształtów, kolorami i transformacjami grup. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu oraz wyczerpujące wyjaśnienia krok po kroku, pomagające opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}