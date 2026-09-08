---
category: general
date: 2026-09-08
description: Dowiedz się, jak grupować kształty w Wordzie za pomocą DocumentBuilder,
  utworzyć pusty dokument Word i wstawić prostokątny kształt w zaledwie kilku linijkach
  kodu C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: pl
lastmod: 2026-09-08
og_description: Grupowanie kształtów w Wordzie przy użyciu DocumentBuilder. Ten samouczek
  pokazuje, jak utworzyć pusty dokument Word, wstawić kształt prostokąta i połączyć
  kształty w GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Grupowanie kształtów w Wordzie przy użyciu DocumentBuilder – kompletny przykład
  w C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Jak grupować kształty w Wordzie przy użyciu DocumentBuilder – przewodnik krok
  po kroku
url: /pl/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak grupować kształty w Wordzie przy użyciu DocumentBuilder – przewodnik krok po kroku

Jeśli potrzebujesz **grupować kształty w Wordzie** programowo, ten tutorial pokazuje kompletne rozwiązanie w C#. Zobaczysz, jak **utworzyć pusty dokument Word**, użyć **DocumentBuilder** oraz **wstawić kształt prostokąta**, a następnie pogrupować go z elipsą. Wynikiem jest pojedynczy `GroupShape`, który możesz przesuwać, zmieniać rozmiar lub stylizować jako jeden obiekt.

Ten przewodnik obejmuje wszystko, co musisz wiedzieć, aby wygenerować dokument Word z pogrupowanymi grafikami przy użyciu biblioteki Aspose.Words for .NET. Po zakończeniu artykułu będziesz mieć działający projekt, który tworzy plik `GroupedShapes.docx` zawierający prostokąt i elipsę połączone w jeden kształt.

## Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.7.2+)
- Pakiet NuGet Aspose.Words for .NET (`Aspose.Words`) – wersja 23.12 lub nowsza
- IDE C# takie jak Visual Studio 2022 lub Visual Studio Code
- Podstawowa znajomość składni C# i programowania obiektowego

> **Pro tip:** Zainstaluj pakiet NuGet z linii poleceń, aby utrzymać projekt w porządku:  
> `dotnet add package Aspose.Words --version 23.12.0`

## Krok 1: Utwórz pusty dokument Word

Pierwszą operacją jest utworzenie obiektu `Document`, który reprezentuje pusty plik Word, oraz `DocumentBuilder`, który umożliwia dodawanie zawartości.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Dlaczego to ważne:** `Document` zapewnia kontener pliku, natomiast `DocumentBuilder` oferuje płynne API do wstawiania tekstu, obrazów i kształtów. Bez `DocumentBuilder` musiałbyś ręcznie manipulować drzewem węzłów dokumentu, co jest podatne na błędy.

## Krok 2: Wstaw kształt prostokąta

Prostokąt jest powszechnym elementem budulcowym diagramów. Użyj `InsertShape` z `ShapeType.Rectangle` i określ szerokość oraz wysokość w punktach (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Dlaczego to ważne:** Ustawienie `Left` i `Top` pozycjonuje prostokąt precyzyjnie na stronie, co jest niezbędne, gdy później będziesz go grupować z innymi kształtami. Metoda `InsertShape` automatycznie dodaje kształt do bieżącego akapitu.

## Krok 3: Wstaw kształt elipsy

Następnie dodaj elipsę, która będzie leżeć obok prostokąta.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Dlaczego to ważne:** Użycie innego `ShapeType` pokazuje, jak to samo API `DocumentBuilder` może tworzyć różnorodne grafiki. Pozycjonowanie elipsy tak, aby nachodziła na prostokąt, uwidacznia efekt grupowania.

## Krok 4: Grupuj dwa kształty

`GroupShape` działa jak kontener. Dodając prostokąt i elipsę jako dzieci, zachowują się jako pojedynczy obiekt.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Dlaczego to ważne:** Właściwość `Bounds` określa, gdzie grupa znajduje się na stronie. Dodając kształty podrzędne, zachowujesz ich indywidualne formatowanie, jednocześnie umożliwiając wspólne transformacje (przesuwanie, obrót, zmiana rozmiaru).

## Krok 5: Zapisz dokument

Na koniec zapisz dokument na dysku. Możesz zmienić ścieżkę na dowolny folder, który preferujesz.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Po otwarciu `GroupedShapes.docx` w Microsoft Word zobaczysz prostokąt i elipsę pogrupowane razem. Wybranie grupy podświetli oba kształty, umożliwiając przeciąganie lub zmianę rozmiaru jako jednej jednostki.

### Oczekiwany wynik

- Plik Word o nazwie **GroupedShapes.docx**
- Na pierwszej stronie znajduje się **prostokąt** (100 pt × 50 pt) w pozycji (50, 50)
- **Elipsa** (80 pt × 80 pt) w pozycji (200, 70)
- Oba kształty są częścią **GroupShape** o ramce ograniczającej 300 pt × 200 pt

## Typowe warianty i przypadki brzegowe

| Scenariusz | Dostosowanie |
|------------|--------------|
| **Inny rozmiar strony** | Ustaw `document.Sections[0].PageSetup.PageWidth` i `PageHeight` przed wstawianiem kształtów. |
| **Więcej niż dwa kształty** | Utwórz dodatkowe obiekty `Shape` i wywołaj `groupShape.AppendChild(newShape)` dla każdego z nich. |
| **Zastosowanie koloru wypełnienia** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **Obrócenie grupy** | `groupShape.Rotation = 45;` (stopnie) |
| **Eksport do PDF** | Po zapisaniu DOCX, wywołaj `document.Save("GroupedShapes.pdf");` |

## Pełny kod źródłowy (gotowy do uruchomienia)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Skopiuj kod do nowego projektu konsolowego, przywróć pakiet NuGet Aspose.Words i uruchom. Konsola potwierdzi lokalizację pliku, a otwarcie pliku pokaże pogrupowane grafiki.

## Zakończenie

Teraz wiesz, **jak grupować kształty w Wordzie** przy użyciu `DocumentBuilder` z Aspose.Words. Tutorial przeprowadził Cię przez tworzenie **pustego dokumentu Word**, **wstawianie kształtu prostokąta**, dodanie elipsy oraz połączenie ich w `GroupShape`. Dzięki tej bazie możesz budować bardziej rozbudowane diagramy, schematy blokowe lub własne grafiki bezpośrednio z C#.

### Co dalej?

- Poznaj **jak używać DocumentBuilder** do tabel, nagłówków i stopek.
- Połącz techniki **insert rectangle shape Word** z polami tekstowymi, aby tworzyć diagramy z adnotacjami.
- Użyj **create blank word doc** jako szablonu do automatycznego generowania raportów.

Śmiało eksperymentuj z kolorami, gradientami i dodatkowymi kształtami. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}