---
category: general
date: 2026-09-08
description: Dowiedz się, jak utworzyć pusty dokument Word, wstawić kształt prostokąta
  i grupować wiele kształtów przy użyciu C#. Postępuj zgodnie z tym przewodnikiem
  krok po kroku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: pl
lastmod: 2026-09-08
og_description: Utwórz pusty dokument Word, wstaw kształt prostokąta i grupuj wiele
  kształtów w C#. Ten samouczek przeprowadzi Cię przez cały proces.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Utwórz pusty dokument Word z grupowanymi kształtami w C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Jak utworzyć pusty dokument Word z grupowanymi kształtami
url: /pl/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć pusty dokument Word z grupowanymi kształtami

Jeśli potrzebujesz **utworzyć pusty dokument Word**, który zawiera własne grafiki, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Nauczysz się **wstawiać kształt prostokąta**, **grupować wiele kształtów** oraz **dodawać kształty do grupy** przy użyciu Aspose.Words for .NET.

Pusty dokument daje czyste płótno, a grupowanie kształtów pozwala przesuwać, zmieniać rozmiar lub obracać je jako jedną jednostkę. Ten tutorial obejmuje każdy krok — od inicjalizacji dokumentu po zapisanie finalnego pliku — abyś mógł skopiować kod do własnego projektu i od razu zobaczyć rezultaty.

## Czego będziesz potrzebować

* .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+)
* Ważna licencja Aspose.Words for .NET (darmowa wersja ewaluacyjna działa do testów)
* IDE, np. Visual Studio 2022 lub Visual Studio Code
* Podstawowa znajomość składni C#

## Jak utworzyć pusty dokument Word

Pierwszym krokiem jest utworzenie obiektu `Document`. Obiekt ten reprezentuje pusty plik `.docx`, który możesz edytować przy pomocy `DocumentBuilder`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Konstruktor `Document` tworzy **pusty dokument Word** w pamięci. `DocumentBuilder` zapewnia płynne API do wstawiania tekstu, obrazów i obiektów rysunkowych.

## Wstaw kształt prostokąta do dokumentu

Następnie dodaj kształt prostokąta. Prostokąt będzie pierwszym dzieckiem grupy, którą utworzymy później.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

Wywołanie `InsertShape` z `ShapeType.Rectangle` **wstawia kształt prostokąta** w bieżącej pozycji kursora. Szerokość i wysokość podawane są w punktach (1 pt ≈ 1/72 in).

## Grupuj wiele kształtów razem

`GroupShape` działa jak kontener. Wszystkie kształty podrzędne wewnątrz grupy przemieszczają się i transformują razem. Najpierw utwórz grupę, a potem dodaj prostokąt, który właśnie stworzyliśmy.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

Metoda `InsertGroupShape` umieszcza pustą grupę w miejscu kursora buildera. Dodając prostokąt, **grupujemy wiele kształtów** — prostokąt staje się częścią wewnętrznej kolekcji węzłów grupy.

## Dodaj kształty do grupy i zapisz plik

Teraz dodaj drugi kształt — elipsę — aby pokazać, jak wiele obiektów może współdzielić ten sam kontener. Następnie zapisz dokument.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Wywołanie `InsertShape` **dodaje kształty do grupy**, gdy dołączysz zwrócony `Shape` do `GroupShape`. Zapisanie `Document` tworzy plik `.docx`, który możesz otworzyć w Microsoft Word, LibreOffice lub dowolnym kompatybilnym przeglądarce.

### Oczekiwany wynik

Po otwarciu *GroupShapeDemo.docx* zobaczysz pustą stronę z grupowanym obiektem, który zawiera jasno‑niebieski prostokąt i różową elipsę. Zaznaczenie grupy pozwala przesuwać oba kształty jednocześnie, potwierdzając, że **grupowanie wielu kształtów** działa zgodnie z zamierzeniami.

## Dlaczego używać GroupShape?

* **Atomowe transformacje** – Skalowanie, obracanie lub przesuwanie grupy wpływa na wszystkie elementy równomiernie.
* **Logiczna organizacja** – Trzyma powiązane grafiki razem, ułatwiając utrzymanie struktury dokumentu.
* **Wydajność** – Renderowanie jednego kontenera jest często szybsze niż obsługa wielu niezależnych kształtów.

Jeśli później będziesz musiał zmodyfikować pojedyncze dziecko, możesz je pobrać z `group.ChildNodes` po indeksie lub po właściwości `Name`.

## Typowe warianty i przypadki brzegowe

| **Scenariusz**                           | **Jak dostosować kod**                                                          |
|------------------------------------------|---------------------------------------------------------------------------------|
| **Różne typy kształtów**                 | Zastąp `ShapeType.Rectangle` lub `ShapeType.Ellipse` dowolnym innym `ShapeType` |
| **Dodawanie tekstu wewnątrz kształtu**   | Użyj `Shape.TextPath.Text = "Hello"` po wstawieniu kształtu                    |
| **Ustawianie kąta obrotu**               | `group.Rotation = 45;` (stopnie)                                                |
| **Zapisywanie jako PDF zamiast DOCX**    | `doc.Save("GroupShapeDemo.pdf");`                                               |
| **Dodawanie obramowania do grupy**       | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`              |

## Porady profesjonalne

* **Nazwij swoje kształty** – `rectangle.Name = "MyRect";` ułatwia ich późniejsze odnalezienie.
* **Używaj pozycjonowania względnego** – Ustaw `group.RelativeHorizontalPosition` na `RelativeHorizontalPosition.Page`, jeśli chcesz, aby grupa była przytwierdzona do marginesów strony.
* **Zwalniaj zasoby** – Owiń `Document` w blok `using` przy pracy w większych aplikacjach, aby szybko zwolnić niezarządzaną pamięć.

## Pełny kod źródłowy do szybkiego kopiowania

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Skopiuj kod do nowego projektu konsolowego, przywróć pakiet NuGet `Aspose.Words` i uruchom. Plik wyjściowy pojawi się w folderze projektu `bin/Debug/net6.0` (lub równoważnym).

## Kolejne kroki

Teraz, gdy potrafisz **utworzyć pusty dokument Word**, **wstawić kształt prostokąta** i **grupować wiele kształtów**, możesz rozważyć:

* Dodawanie **pól tekstowych** wewnątrz grupy w celu tworzenia oznakowanych diagramów.
* Eksportowanie grupowanej grafiki do obrazu przy użyciu `doc.Save("image.png", SaveFormat.Png)`.
* Łączenie grup z tabelami w celu uzyskania bogato sformatowanych raportów.

Eksperymentuj z różnymi właściwościami kształtów, hierarchiami grup i formatami eksportu, aby w pełni wykorzystać możliwości rysunkowe Aspose.Words.

--- 

*Pamiętaj*: grupowanie kształtów to potężny sposób na utrzymanie porządku w dokumentach Word i czytelności kodu. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu wraz z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz kształt prostokąta w Wordzie przy użyciu C# – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Wstawianie kształtów w dokumentach Word przy użyciu Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Utwórz grupowy kształt w dokumencie Word przy użyciu Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}