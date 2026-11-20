---
category: general
date: 2026-11-18
description: Dowiedz się, jak utworzyć prostokątny kształt w dokumencie Word przy
  użyciu C#. Poradnik obejmuje także ustawianie rozmiaru kształtu, ustawianie pozycji
  kształtu oraz grupowanie kształtów w Wordzie.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: pl
lastmod: 2026-11-18
og_description: Utwórz prostokątny kształt w pliku Word przy użyciu C# i dowiedz się,
  jak ustawić wymiary kształtu, pozycję kształtu oraz grupować kształty w Wordzie.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Utwórz prostokątny kształt i grupuj kształty w Wordzie przy użyciu C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Jak utworzyć prostokątny kształt i grupować kształty w Wordzie przy użyciu
  C#
url: /pl/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć kształt prostokąta i grupować kształty w Wordzie przy użyciu C#

Jeśli potrzebujesz **utworzyć kształt prostokąta** w dokumencie Word, ten samouczek pokaże Ci kompletną, gotową do uruchomienia rozwiązanie. Zobaczysz, jak ustawić rozmiar kształtu, pozycję kształtu oraz grupować kształty w Wordzie, aby zachowywały się jako pojedynczy obiekt.

Praca z kształtami jest powszechnym wymogiem przy generowaniu raportów, faktur lub diagramów programowo. Po zakończeniu tego przewodnika będziesz w stanie wygenerować plik `.docx`, który zawiera prostokąt, elipsę i zgrupowany kontener — wszystko stworzone przy użyciu Aspose.Words for .NET.

## Wymagania wstępne

- .NET 6.0 SDK lub nowszy (kod działa również z .NET Framework 4.7+)
- Pakiet NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Edytor kodu lub IDE (Visual Studio, VS Code, Rider, itp.)

Nie są wymagane dodatkowe biblioteki.

## Jak utworzyć kształt prostokąta i grupować kształty w Wordzie

Główne kroki to:

1. **Utwórz pusty dokument** i `DocumentBuilder`.
2. **Wstaw `GroupShape`**, który będzie przechowywał poszczególne kształty.
3. **Utwórz kształt prostokąta**, ustaw jego wymiary i dodaj go do grupy.
4. **Utwórz kształt elipsy**, ustaw jego rozmiar i pozycję, a następnie dodaj go do grupy.
5. **Zapisz** dokument.

Każdy krok jest wyjaśniony poniżej, a pełny kod źródłowy znajduje się po wyjaśnieniach.

### Krok 1: Zainicjalizuj dokument i builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` reprezentuje cały plik Word, natomiast `DocumentBuilder` udostępnia płynne API do wstawiania treści. Inicjalizacja ich jest obowiązkowa, zanim będzie można dodać jakiekolwiek kształty.

### Krok 2: Wstaw kształt grupy

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

`GroupShape` działa jak kontener; wszystkie kształty podrzędne poruszają się razem. Jest to zalecany sposób **grupowania kształtów w Wordzie**, gdy potrzebne są zbiorcze transformacje (np. przesuwanie, obracanie lub usuwanie).

### Krok 3: Utwórz prostokąt i ustaw jego rozmiar

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Tutaj **tworzymy kształt prostokąta** i **ustawiamy rozmiar kształtu** poprzez przypisanie `Width` i `Height`. W Aspose.Words rozmiary wyrażane są w punktach (1 pt ≈ 1/72 in). Jawne ustawienie wymiarów zapewnia, że prostokąt pojawi się dokładnie tak, jak zamierzono.

### Krok 4: Utwórz elipsę, ustaw wymiary i pozycję

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

**Ustawienie wymiarów kształtu** dla elipsy jest identyczne dla szerokości i wysokości, co daje idealne koło. Właściwość `Left` demonstruje **ustawienie pozycji kształtu**: elipsa zaczyna się 120 pt w prawo od początku grupy, więc nie nakłada się na prostokąt.

### Krok 5: Zapisz dokument

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

Zapis zapisuje plik Word na dysku. Możesz otworzyć `GroupShape.docx` w Microsoft Word, aby zweryfikować, że prostokąt i elipsa są zgrupowane i poprawnie rozmieszczone.

## Ustawianie wymiarów i rozmiaru kształtu – szczegółowe spojrzenie

- **Punkty vs. cale**: 72 pt = 1 in. Jeśli wolisz cale, pomnóż przez 72 (np. `2.5 * 72` dla 2,5 in).
- **Automatyczne skalowanie**: Jeśli pominiesz `Width` lub `Height`, kształt użyje domyślnego rozmiaru. Jawnie **ustaw rozmiar kształtu**, aby uniknąć niespodzianek w układzie.
- **Proporcje**: Dla kształtów takich jak `Ellipse`, utrzymanie równej wartości `Width` i `Height` zachowuje wygląd koła.

## Pozycjonowanie kształtu w Wordzie

`Left` i `Top` kontrolują przesunięcie kształtu wewnątrz jego kontenera (grupy lub strony). Dodatnie wartości przesuwają kształt w prawo/w dół; ujemne wartości przesuwają go w lewo/w górę. Przy grupowaniu pozycje są względem początku grupy, co upraszcza obliczenia układu.

## Grupowanie kształtów w Wordzie przy użyciu Aspose.Words

Grupowanie jest niezbędne, gdy chcesz, aby wiele kształtów działało jako jedna jednostka. Obiekt `GroupShape`:

- Obsługuje `AppendChild`, aby dodać dowolny `Shape` (prostokąt, elipsę, obraz itp.).
- Umożliwia przesunięcie, obrót lub usunięcie całej grupy jednym wywołaniem.
- Utrzymuje pozycje kształtów podrzędnych względem grupy, co ułatwia zarządzanie złożonymi diagramami.

**Wskazówka:** Po dodaniu wszystkich kształtów podrzędnych możesz dostosować `Width`, `Height`, `Left` i `Top` grupy, aby przemieścić całą kolekcję w jednym kroku.

## Pełny, uruchamialny przykład

Poniżej znajduje się pełny program, który możesz skopiować, wkleić i uruchomić. Zawiera wszystkie dyrektywy `using`, metodę `Main` oraz komentarze wyjaśniające każdą linię.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Oczekiwany wynik:** Po uruchomieniu programu `GroupShape.docx` pojawi się w folderze wykonywania. Otworzenie go w Wordzie pokazuje prostokąt (100 pt × 50 pt) po lewej oraz elipsę (80 pt × 80 pt) umieszczoną 120 pt w prawo, oba wewnątrz jednego zgrupowanego obiektu.

![Dokument Word ze zgrupowanym prostokątem i elipsą](grouped_shapes.png){: .center alt="Zrzut ekranu dokumentu Word pokazującego zgrupowany prostokąt i elipsę utworzone przy użyciu C#" }

*Powyższy obraz ilustruje ostateczny rezultat; prostokąt i elipsa są wybieralne jako jedna grupa.*

## Częste pytania i przypadki brzegowe

| Question | Answer |
|----------|--------|
| **Czy mogę dodać więcej niż dwa kształty?** | Tak. Wywołaj `group.AppendChild(yourShape)` dla każdego dodatkowego kształtu. |
| **Co zrobić, jeśli muszę obrócić grupę?** | Użyj `group.RotationAngle = 45;` (stopnie) po dodaniu wszystkich elementów podrzędnych. |
| **Jak zmienić kolor tła grupy?** | Ustaw `group.FillColor = System.Drawing.Color.LightGray;`. |
| **Czy to będzie działać z plikami .doc?** | Aspose.Words obsługuje `.doc` i `.docx`. Ten sam kod działa; wystarczy zmienić rozszerzenie pliku w `Save`. |
| **Czy grupowanie wielu kształtów wpływa na pamięć?** | Samo grupowanie dodaje minimalny narzut. Główną kwestią jest całkowita liczba kształtów; utrzymuj ją w rozsądnych granicach przy dużych dokumentach. |

## Zakończenie

W tym samouczku nauczyłeś się, jak **utworzyć kształt prostokąta** w pliku Word przy użyciu C#, jak **ustawić rozmiar kształtu**, **ustawić wymiary kształtu**, **ustawić pozycję kształtu**, a na koniec jak **grupować kształty w Wordzie** z użyciem Aspose.Words. Pełny przykład demonstruje czyste, łatwe w utrzymaniu podejście, które możesz rozszerzyć na bardziej złożone diagramy, wykresy lub własne grafiki.

Kolejne kroki:

- Dodawanie tekstu wewnątrz kształtów (`Shape.TextPath.Text = "Hello"`).
- Wstawianie obrazów do `GroupShape`.
- Eksportowanie zgrupowanych kształtów do PDF przy użyciu `doc.Save("output.pdf")`.

Śmiało eksperymentuj z różnymi rozmiarami, pozycjami i dodatkowymi typami kształtów, aby dopasować je do potrzeb swojego projektu. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak utworzyć kształt prostokąta i grupować kształty w Wordzie przy użyciu Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Tworzenie kształtu grupy w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tworzenie kształtu prostokąta w Wordzie przy użyciu C# – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}