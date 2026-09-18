---
category: general
date: 2026-09-18
description: Utwórz prostokątny kształt w dokumencie Word przy użyciu C#. Dowiedz
  się, jak dodać wiele kształtów, dodać kształty do grupy oraz wstawić grupowy kształt
  za pomocą Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: pl
lastmod: 2026-09-18
og_description: Utwórz prostokątny kształt w pliku Word przy użyciu C#. Ten przewodnik
  pokazuje, jak dodać wiele kształtów, dodać kształty do grupy oraz wstawić grupowy
  kształt przy użyciu Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Utwórz kształt prostokąta i grupuj kształty w C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Utwórz kształt prostokąta i grupuj wiele kształtów w C#
url: /pl/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz prostokątny kształt i grupuj wiele kształtów w C#

Jeśli potrzebujesz **create rectangle shape** w dokumencie Word, ten tutorial pokazuje pełne rozwiązanie. Zobaczysz, jak **add multiple shapes**, **add shapes to a group** i **insert group shape** przy użyciu Aspose.Words API dla .NET.

Praca z kształtami jest powszechnym wymogiem przy programowym generowaniu raportów, umów lub materiałów marketingowych. Po zakończeniu tego przewodnika będziesz mieć działającą aplikację konsolową C#, która tworzy plik `.docx` zawierający prostokąt, elipsę i grupę, w której znajdują się oba kształty.

Jedynymi wymaganiami wstępnymi są aktualny .NET SDK (6.0 lub nowszy) oraz licencjonowana kopia Aspose.Words dla .NET. Nie są potrzebne dodatkowe narzędzia.

## Prerequisites

- .NET 6.0 SDK lub nowszy  
- Aspose.Words for .NET (pakiet NuGet `Aspose.Words`)  
- Podstawowa znajomość składni C#  

Możesz zainstalować pakiet za pomocą następującego polecenia:

```bash
dotnet add package Aspose.Words
```

## Krok 1: Utwórz prostokątny kształt przy użyciu Aspose.Words

Pierwszym krokiem jest utworzenie obiektu `Shape` typu `Rectangle`. Obiekt ten reprezentuje wizualny prostokąt, który pojawi się w dokumencie.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Dlaczego to ważne:** `ShapeType.Rectangle` informuje Aspose.Words, aby renderował geometryczny prostokąt. Ustawienie `Width` i `Height` określa jego rozmiar w punktach (1 punkt = 1/72 cala). Dodanie kolorów wypełnienia i obrysu sprawia, że kształt jest widoczny bez dodatkowego stylowania.

## Krok 2: Dodaj wiele kształtów do dokumentu

Po prostokącie możesz utworzyć dowolną liczbę dodatkowych kształtów. W tym przykładzie dodajemy elipsę, aby zademonstrować, jak działa **add multiple shapes**.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Dlaczego to ważne:** Każde wywołanie `new Shape` tworzy niezależny obiekt rysunkowy. Wstawiając je kolejno, budujesz kolekcję kształtów, które później mogą być grupowane lub pozycjonowane indywidualnie.

## Krok 3: Dodaj kształty do grupy

Grupowanie kształtów upraszcza zarządzanie układem, ponieważ grupa zachowuje się jak pojedynczy węzeł. Ten krok pokazuje, jak **add shapes to group** przy użyciu `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Dlaczego to ważne:** `GroupShape` działa jak kontener. Gdy przesuwasz, obracasz lub zmieniasz rozmiar grupy, wszystkie kształty potomne podążają automatycznie. Ramka ograniczająca (200 × 200 punktów) definiuje przestrzeń współrzędnych dla kształtów potomnych.

## Krok 4: Wstaw grupowy kształt do dokumentu

Teraz, gdy grupa zawiera prostokąt i elipsę, musisz **insert group shape** w wybranym miejscu. Builder już umieścił pustą grupę, ale w razie potrzeby możesz ją wstawić w innym miejscu.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Dlaczego to ważne:** Dostosowanie `Left` i `Top` przesuwa całą grupę na stronie. Zapisanie dokumentu zapisuje hierarchię kształtów do pliku `.docx`, który można otworzyć w Microsoft Word, LibreOffice lub dowolnym kompatybilnym przeglądarce.

## Pełny działający przykład

Poniżej znajduje się pełny program łączący wszystkie kroki. Skopiuj kod do nowego projektu konsolowego i uruchom go, aby wygenerować `GroupShapeExample.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Oczekiwany wynik:**  
Otwierając `GroupShapeExample.docx` zobaczysz jedną grupę zawierającą jasno‑niebieski prostokąt i jasno‑koralową elipsę, oba umieszczone wewnątrz kontenera o wymiarach 200 × 200 punktów. Grupę można wybrać jako jeden obiekt w Wordzie, co potwierdza, że **add shapes to group** powiodło się.

## Typowe warianty i przypadki brzegowe

| Sytuacja | Zalecana korekta |
|-----------|------------------------|
| Różne typy kształtów (np. `ShapeType.Line`) | Utwórz kształt z żądanym `ShapeType` i odpowiednio ustaw jego geometrię. |
| Potrzeba obrócenia kształtu | Użyj `shape.Rotation = 45;` (stopnie) przed dodaniem go do grupy. |
| Większe dokumenty z wieloma grupami | Ponownie używaj jednej instancji `DocumentBuilder`; unikaj tworzenia nowego buildera dla każdej grupy, aby zmniejszyć zużycie pamięci. |
| Zapisywanie do PDF zamiast DOCX | Wywołaj `doc.Save("output.pdf", SaveFormat.Pdf);` po wstawieniu grupy. |

**Pro tip:** Zawsze ustawiaj explicite wartości `Left` i `Top` dla grupy, gdy potrzebne jest precyzyjne położenie. Jeśli je pominiesz, grupa dziedziczy bieżącą pozycję kursora buildera, co może prowadzić do nieoczekiwanych rezultatów układu.

## Zakończenie

Teraz wiesz, jak **create rectangle shape**, **add multiple shapes**, **add shapes to group** i **insert group shape** w dokumencie Word przy użyciu C#. Pełny przykład demonstruje kompletny przepływ pracy od tworzenia dokumentu po zapisanie finalnego pliku.  

Następnie, zapoznaj się z powiązanymi tematami, takimi jak **positioning shapes relative to text**, **applying text wrapping**, oraz **exporting grouped shapes to PDF**. Te rozszerzenia pozwalają tworzyć zaawansowane, programowe układy dokumentów przy użyciu Aspose.Words.

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz prostokątny kształt w Word przy użyciu C# – Przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Utwórz grupowy kształt w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Utwórz pusty dokument Word z cieniowanym prostokątnym kształtem – Przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}