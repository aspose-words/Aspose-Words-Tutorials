---
category: general
date: 2026-10-04
description: Dowiedz się, jak grupować kształty w programie Word przy użyciu C#. Ten
  przewodnik pokazuje, jak wstawić kształt prostokąta, grupować wiele kształtów oraz
  programowo utworzyć pusty plik Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: pl
lastmod: 2026-10-04
og_description: Grupowanie kształtów w Wordzie przy użyciu C#. Postępuj zgodnie z
  tym przewodnikiem krok po kroku, aby wstawić prostokątny kształt, pogrupować wiele
  kształtów i utworzyć pusty plik Word przy użyciu DocumentBuilder.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: Grupowanie kształtów w Wordzie przy użyciu C# – kompletny samouczek DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: Jak grupować kształty w Wordzie za pomocą C# i DocumentBuilder
url: /pl/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak grupować kształty w Wordzie przy użyciu C# i DocumentBuilder

Jeśli potrzebujesz **grupować kształty w Wordzie** z aplikacji C#, ten tutorial pokaże Ci dokładnie, jak to zrobić. Zobaczysz, jak *wstawić kształt prostokąta*, połączyć kilka rysunków w jedną grupę oraz w końcu **utworzyć pusty plik Word**, który zawiera pogrupowane obiekty.

Praca z kształtami jest częstym wymogiem przy generowaniu raportów, faktur lub niestandardowych szablonów programowo. Po zakończeniu tego przewodnika będziesz mieć wielokrotnego użytku fragment kodu, który możesz wstawić do dowolnego projektu .NET odwołującego się do Aspose.Words.

## Czego się nauczysz

- Utworzyć pusty dokument Word od podstaw.  
- Wstawić kształt prostokąta i elipsę przy użyciu `DocumentBuilder`.  
- **Pogrupować wiele kształtów** w `GroupShape`.  
- Użyć **append child to group**, aby zbudować hierarchię.  
- Zapisać plik na dysku i zweryfikować wynik.

Niewymagane jest wcześniejsze doświadczenie z Aspose.Words, ale powinieneś mieć podstawową znajomość C# i programowania w .NET.

## Wymagania wstępne

| Wymaganie | Powód |
|-------------|--------|
| .NET 6.0 lub nowszy | Zapewnia środowisko uruchomieniowe dla kodu C#. |
| Aspose.Words for .NET (najnowsza wersja) | Dostarcza klasy `Document`, `DocumentBuilder` oraz kształtów. |
| IDE, takie jak Visual Studio 2022 (lub VS Code) | Ułatwia kompilację i uruchomienie przykładu. |
| Uprawnienia do zapisu w folderze na Twoim komputerze | Wymagane dla wywołania `doc.save`. |

Zainstaluj Aspose.Words za pomocą NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Grupowanie kształtów w Wordzie – przewodnik krok po kroku

Poniżej znajduje się pełny, działający program. Każda sekcja jest szczegółowo wyjaśniona, abyś rozumiał **dlaczego** kod jest napisany w ten sposób, a nie tylko **co** robi.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Dlaczego każdy krok ma znaczenie

1. **Utwórz pusty plik Word** – Rozpoczęcie od czystego dokumentu gwarantuje, że żadne ukryte formatowanie nie zakłóca pozycjonowania kształtów.  
2. **Zainicjuj DocumentBuilder** – `DocumentBuilder` abstrahuje manipulację węzłami niskiego poziomu, pozwalając skupić się na układzie.  
3. **Wstaw indywidualne kształty** – Najpierw potrzebujesz oddzielnych obiektów (`insert rectangle shape` i elipsy), zanim je pogrupujesz. Ustawienie `Left` i `Top` zapewnia ich obok siebie położenie.  
4. **Pogrupuj wiele kształtów** – Tworząc `GroupShape` i używając **append child to group**, przekształcasz dwa niezależne rysunki w jedną logiczną jednostkę. Przesuwanie lub zmiana rozmiaru grupy wpłynie jednocześnie na oba elementy podrzędne.  
5. **Zapisz dokument** – Końcowy plik, `GroupedShapes.docx`, można otworzyć w Microsoft Word, aby zweryfikować, że prostokąt i elipsa są rzeczywiście pogrupowane (wybierz jeden, a oba przesuwają się razem).

### Oczekiwany wynik

Otwórz `GroupedShapes.docx` w Microsoft Word:

- Zobaczysz prostokąt i elipsę umieszczone obok siebie.  
- Wybranie dowolnego kształtu podświetli oba, potwierdzając, że należą do tej samej grupy.  
- Grupę można przeciągać, zmieniać jej rozmiar lub formatować jako pojedynczy obiekt.

![Diagram pogrupowanego prostokąta i elipsy w dokumencie Word](https://example.com/grouped-shapes.png){: .center-image alt="Diagram pogrupowanego prostokąta i elipsy w dokumencie Word"}

*Zrzut ekranu ilustruje ostateczne pogrupowane kształty.*

---

## Wstaw kształt prostokąta – dostosowywanie rozmiaru i stylu

Jeśli potrzebujesz prostokąta o określonym kolorze wypełnienia lub obramowaniu, zmodyfikuj obiekt `Shape` po wstawieniu:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

Te właściwości są częścią klasy `Shape` i działają dla dowolnego typu kształtu, nie tylko prostokątów. Dostosowanie stylu przed **append child to group** zapewnia, że grupa dziedziczy ustawione właściwości wizualne.

---

## Grupowanie wielu kształtów – obsługa więcej niż dwóch obiektów

Przykład grupuje prostokąt i elipsę, ale możesz dodać dowolną liczbę kształtów:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Wskazówka:** Po zbudowaniu złożonej grupy możesz zablokować jej układ, aby zapobiec przypadkowym zmianom:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – kolejność ma znaczenie

Kolejność wywołań `AppendChild` definiuje kolejność Z (który kształt znajduje się na wierzchu). W przykładzie najpierw dodawany jest prostokąt, potem elipsa, więc elipsa nakłada się na prostokąt, jeśli się przecinają. Zmiana kolejności jest tak prosta, jak wywołanie `RemoveChild` i ponowne dodanie:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Utwórz pusty plik Word – wielokrotnego użytku metoda pomocnicza

Jeśli Twoja aplikacja często potrzebuje nowego dokumentu, kapsułkuj logikę tworzenia:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

Możesz wtedy zastąpić linię `new Document()` w głównym programie wywołaniem `CreateBlankWordFile()`. Demonstracja koncepcji **create blank word file** w sposób wielokrotnego użytku.

---

## Częste pułapki i jak ich unikać

| Problem | Dlaczego się pojawia | Rozwiązanie |
|-------|----------------|-----|
| Kształty pojawiają się poza stroną | Domyślne wartości `Left`/`Top` wynoszą 0, co umieszcza kształt na marginesie. | Jawnie ustaw `Left` i `Top` po wstawieniu. |
| Grupa traci formatowanie | Zmiana kształtu podrzędnego po jego dodaniu do grupy może zepsuć układ grupy. | Zastosuj wszystkie właściwości wizualne **przed** wywołaniem `AppendChild`. |
| Zapisany plik jest pusty | `DocumentBuilder` nigdy nie został użyty do dodania węzła, lub `doc.Save` został wywołany na innym obiekcie `Document`. | Sprawdź, czy zapisujesz ten sam `Document`, który budowałeś. |
| Ostrzeżenia o kompatybilności w Wordzie | Używanie nowszych funkcji kształtów, które nie są obsługiwane |

## Co powinieneś się nauczyć dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz grupowy kształt w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Wstaw kształty w dokumentach Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Utwórz kształt prostokąta w Wordzie przy użyciu C# – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}