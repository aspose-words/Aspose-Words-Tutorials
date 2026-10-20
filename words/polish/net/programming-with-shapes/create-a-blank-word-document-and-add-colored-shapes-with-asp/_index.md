---
category: general
date: 2026-09-21
description: Utwórz pusty dokument Word przy użyciu Aspose.Words, ustaw rozmiar kształtu,
  ustaw pozycję kształtu, ustaw kolor kształtu i zapisz plik docx w jednym przebiegu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: pl
lastmod: 2026-09-21
og_description: Utwórz pusty dokument Word, ustaw rozmiar kształtu, ustaw pozycję
  kształtu, ustaw kolor kształtu i zapisz plik docx za pomocą Aspose.Words w kilka
  minut.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Utwórz pusty dokument Word i dodaj kolorowe kształty – przewodnik Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Utwórz pusty dokument Word i dodaj kolorowe kształty przy użyciu Aspose.Words
url: /pl/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz pusty dokument Word i dodaj kolorowe kształty przy użyciu Aspose.Words

Jeśli potrzebujesz **utworzyć pusty dokument Word** programowo, ten przewodnik pokaże Ci, jak to zrobić z Aspose.Words. Nauczysz się **ustawiać rozmiar kształtu**, **ustawiać pozycję kształtu**, **ustawiać kolor kształtu**, a na koniec **zapisać plik docx** bez wychodzenia z IDE.

Praca z plikami Word w C# często wymaga ręcznego wywoływania niskopoziomowych metod OpenXML, ale Aspose.Words upraszcza tę złożoność. Po zakończeniu tego samouczka będziesz mieć w pełni funkcjonalny plik `.docx`, który zawiera grupowany kształt złożony z dwóch kolorowych prostokątów — idealny do raportów, certyfikatów lub własnych szablonów.

## Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.7+)
- Aspose.Words for .NET 23.9 lub nowszy (instalacja przez NuGet: `Install-Package Aspose.Words`)
- Podstawowa znajomość C# i Visual Studio (lub dowolnego edytora C#)

Nie jest wymagany żaden istniejący plik Word; samouczek zaczyna się od **utworzenia pustego dokumentu Word** od zera.

## Utwórz pusty dokument Word przy użyciu Aspose.Words

Pierwszym krokiem jest utworzenie obiektu `Document`. Obiekt ten reprezentuje pusty plik Word w pamięci.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` jest początkowo pusty, co jest dokładnie tym, czego potrzebujesz, **tworząc pusty dokument Word**. Obiekt `builder` zostanie później użyty do wstawienia grupy kształtów w bieżącej pozycji kursora.

## Ustaw rozmiar kształtu i utwórz GroupShape

`GroupShape` działa jak kontener, który może przechowywać wiele pojedynczych kształtów. Najpierw określ ogólne wymiary kontenera.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Tutaj **ustawiamy rozmiar kształtu** dla samej grupy (300 × 200). Te same nazwy właściwości (`Width`, `Height`) są używane dla każdego podrzędnego kształtu, dając precyzyjną kontrolę nad każdym elementem.

## Dodaj pierwszy prostokąt i ustaw kolor kształtu

Teraz dodaj prostokąt do grupy i nadaj mu kolor tła.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

Właściwość `FillColor` **ustawia kolor kształtu**. Użycie `System.Drawing.Color` pozwala wybrać dowolną predefiniowaną lub własną wartość ARGB.

## Dodaj drugi prostokąt, ustaw jego rozmiar, pozycję i kolor

Drugi prostokąt pokazuje, jak **ustawić pozycję kształtu** względem grupy i jak zmienić jego kolor.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Ponieważ szerokość grupy wynosi 300 punktów, dwa prostokąty po 120 punktów mieszczą się wygodnie z odstępem 30 punktów. Dostosuj `Left` i `Top`, jeśli potrzebujesz innego układu.

## Wstaw GroupShape do dokumentu

Po pełnym skonfigurowaniu grupy, umieść ją w bieżącej pozycji kursora.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` zapisuje kształt bezpośrednio w ciele dokumentu, zachowując dokładną **ustawioną pozycję kształtu**, którą zdefiniowano wcześniej.

## Zapisz plik docx

Ostatnim krokiem jest zapisanie dokumentu na dysku. To demonstruje operację **zapisz plik docx**.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

Po uruchomieniu programu otwórz `GroupShape.docx` w Microsoft Word. Powinieneś zobaczyć pustą stronę z grupowanym kształtem zawierającym dwa kolorowe prostokąty ustawione obok siebie.

### Oczekiwany wynik

- Jednostronicowy plik `.docx`.
- Strona zawiera grupę kształtów umieszczoną 100 pt od lewego i górnego marginesu.
- Wewnątrz grupy po lewej stronie znajduje się jasnoniebieski prostokąt, a po prawej jasnokoralowy prostokąt, każdy o wymiarach 120 × 80 pt.

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się kompletny program, który możesz skopiować i wkleić do aplikacji konsolowej. Nie są wymagane żadne dodatkowe pliki.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Uruchomienie tego programu tworzy dokładnie opisany wcześniej dokument, spełniając wszystkie cztery cele: **utworzyć pusty dokument Word**, **ustawić rozmiar kształtu**, **ustawić pozycję kształtu**, **ustawić kolor kształtu** oraz **zapisz plik docx**.

## Typowe warianty i przypadki brzegowe

| Scenariusz | Co zmienić | Dlaczego ma to znaczenie |
|------------|------------|--------------------------|
| **Inne typy kształtów** | Zamień `ShapeType.Rectangle` na `ShapeType.Ellipse`, `ShapeType.Triangle` itp. | Pozwala tworzyć bardziej złożone grafiki bez użycia zewnętrznych obrazów. |
| **Dynamiczne wymiary** | Oblicz `Width` i `Height` na podstawie danych wejściowych użytkownika lub plików konfiguracyjnych. | Umożliwia ponowne użycie rozwiązania w wielu szablonach dokumentów. |
| **Zapis jako PDF** | Wywołaj `document.Save("output.pdf", SaveFormat.Pdf);` | Jeśli odbiorcy potrzebują formatu nieedytowalnego, PDF jest bezpiecznym wyborem. |
| **Dodawanie tekstu wewnątrz kształtu** | Utwórz kształt `TextBox` i ustaw `TextBox.Text`. | Przydatne przy tworzeniu oznaczonych odznak lub dymków. |
| **Wiele grup na jednej stronie** | Powtórz kroki 2‑5 z różnymi wartościami `Left`/`Top`. | Umożliwia budowanie pulpitów nawigacyjnych lub układów wielosekcyjnych. |

### Pro tip

Gdy potrzebujesz precyzyjnego wyrównania kształtów, użyj właściwości `ShapeBase.WrapType = WrapType.Inline` przed wstawieniem grupy. Spowoduje to, że grupa zachowa się jak akapit, zapobiegając nieoczekiwanemu przepływowi tekstu wokół niej.

## Podsumowanie

Teraz wiesz, jak **utworzyć pusty dokument Word** przy użyciu Aspose.Words, **ustawić rozmiar kształtu**, **ustawić pozycję kształtu**, **ustawić kolor kształtu** oraz **zapisać plik docx**. Pełny przykład demonstruje czysty, wielokrotnego użytku wzorzec dodawania grupowanych grafik do dowolnego projektu automatyzacji Worda.

Od tego momentu możesz eksplorować:

- Dodawanie kolejnych kształtów lub obrazów do tej samej `GroupShape` (różne **ustawienia rozmiaru kształtu**, **koloru kształtu**).
- Użycie `ShapeBase.Rotation` do obracania prostokątów w celach dekoracyjnych.
- Eksportowanie tego samego dokumentu jako PDF lub HTML, aby zwiększyć zasięg dystrybucji (alternatywa **zapisz plik docx**).

Śmiało eksperymentuj z różnymi kolorami, rozmiarami i logiką układu, aby dopasować je do konkretnych potrzeb raportowania lub szablonowania. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu oraz szczegółowe wyjaśnienia krok po kroku, pomagające opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}