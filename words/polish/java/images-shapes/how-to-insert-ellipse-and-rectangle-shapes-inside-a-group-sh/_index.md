---
category: general
date: 2026-10-23
description: Dowiedz się, jak wstawić elipsę i jak dodać kształt prostokąta w programie
  Word przy użyciu Aspose.Words. Zawiera informacje o przenoszeniu kursora do kształtu
  oraz o tworzeniu grupy kształtów.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: pl
lastmod: 2026-10-23
og_description: Jak wstawić elipsę i jak dodać prostokąt w Wordzie przy użyciu Aspose.Words.
  Postępuj zgodnie z przewodnikiem krok po kroku, aby przenieść kursor do kształtu
  i utworzyć grupę kształtów.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Jak wstawić elipsę i prostokąt w grupie kształtów w programie Word
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Jak wstawić kształty elipsy i prostokąta wewnątrz grupy kształtów przy użyciu
  Aspose.Words
url: /pl/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wstawić elipsę i prostokąt wewnątrz kształtu grupy przy użyciu Aspose.Words

Jeśli potrzebujesz wiedzieć **jak wstawić elipsę** w dokumencie Word programowo, ten przewodnik pokazuje kompletny proces. Zobaczysz także **jak dodać prostokąt** jako kształt, nauczysz się **przenieść kursor do kształtu**, oraz odkryjesz **jak utworzyć kształt grupy**, który zawiera wiele obiektów rysunkowych.

Automatyzacja Worda często wymaga precyzyjnego pozycjonowania obiektów rysunkowych. Po zakończeniu tego samouczka będziesz mógł wygenerować plik `.docx`, który zawiera pogrupowany prostokąt i elipsę, gotowy do dalszego stylizowania lub eksportu. Nie są wymagane żadne zewnętrzne narzędzia poza biblioteką Aspose.Words for .NET oraz środowiskiem programistycznym .NET.

## Wymagania wstępne

* Zainstalowany .NET 6.0 lub nowszy.
* Aspose.Words for .NET (pakiet NuGet `Aspose.Words`) dodany do projektu.
* Podstawowa znajomość składni C# oraz Visual Studio (lub dowolnego IDE).

Te wymagania zapewniają, że kod kompiluje się bez dodatkowej konfiguracji.

## Jak utworzyć kształt grupy w Wordzie

Kształt grupy działa jako kontener, który pozwala przenosić, obracać lub formatować kilka kształtów jako jedną jednostkę. Poniższy kod tworzy grupę o określonym rozmiarze (300 × 200 punktów) i przygotowuje dokument do dalszych operacji rysunkowych.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Dlaczego ten krok ma znaczenie*: Kształt grupy definiuje lokalny układ współrzędnych. Wszystkie kształty dodane po przeniesieniu kursora do grupy będą pozycjonowane względem początku grupy, co upraszcza obliczenia układu.

## Jak dodać prostokątny kształt w Wordzie

Teraz, gdy grupa istnieje, możesz **wstawić prostokątny kształt** wewnątrz niej. Prostokąt będzie służył jako tło lub wizualny placeholder dla innych treści.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Wyjaśnienie*: `MoveTo(group)` informuje builder, że aktywny punkt wstawiania znajduje się w kształcie grupy. Bez przeniesienia kursora, `InsertShape` dodałby prostokąt do głównego ciała dokumentu zamiast do grupy.

## Jak wstawić elipsę

Mając prostokąt na miejscu, możesz teraz pokazać **jak wstawić elipsę**. Elipsa będzie wyśrodkowana w tej samej grupie, nachodząc na prostokąt, jeśli tak zechcesz.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Dlaczego kursor musi być przeniesiony*: Każde wywołanie `InsertShape` respektuje bieżącą pozycję kursora. Ponowne wywołanie `MoveTo(group)` gwarantuje, że elipsa również jest dzieckiem grupy, zachowując zamierzoną hierarchię.

## Przenieś kursor do kształtu przed wstawianiem dodatkowych obiektów

Jeśli później potrzebujesz dodać więcej kształtów, zawsze **przenoś kursor do kształtu** przed każdym wstawieniem. Ten wzorzec zapobiega przypadkowemu umieszczeniu poza grupą.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Wskazówka*: Ponowne użycie `MoveTo(group)` jest tanie i poprawia czytelność kodu. Ułatwia także przyszłą konserwację, ponieważ kontekst wstawiania jest wyraźny.

## Zapisz dokument

Na koniec zapisz dokument na dysku. Przykład zapisuje plik jako `GroupShape.docx` w wybranym przez Ciebie folderze.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

Gdy otworzysz zapisany plik w Microsoft Word, zobaczysz jedną grupę zawierającą prostokąt i elipsę, oba poprawnie pozycjonowane.

### Oczekiwany wynik

* Plik `.docx` o nazwie `GroupShape.docx`.
* Wewnątrz dokumentu, pogrupowany obiekt rysunkowy o rozmiarze 300 × 200 punktów.
* W grupie:
  * Prostokąt (100 × 50 punktów) umieszczony w początku grupy.
  * Elipsa (80 × 80 punktów) nachodząca na prostokąt.
  * Dowolne dodatkowe kształty, które dodałeś po przeniesieniu kursora.

## Typowe warianty i przypadki brzegowe

| Sytuacja | Zalecane podejście |
|-----------|----------------------|
| **Różne rozmiary jednostek** | Aspose.Words uses points (1 pt = 1/72 in). Convert centimeters or inches to points before calling `InsertShape`. |
| **Obracanie kształtów wewnątrz grupy** | After inserting a shape, retrieve its `ShapeBase` object and set `ShapeBase.RotationAngle`. |
| **Dodawanie tekstu wewnątrz kształtu** | Use `ShapeBase.AppendChild(new Paragraph(document))` and then add a `Run` with the desired text. |
| **Zapisywanie do PDF zamiast DOCX** | Call `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – the group hierarchy is preserved in the PDF output. |

Te warianty pokazują, że ta sama logika **jak wstawić elipsę** może być dostosowana do wielu rzeczywistych scenariuszy.

## Porady profesjonalne

* **Używaj tego samego obiektu `DocumentBuilder`** – zmniejsza to zużycie pamięci i utrzymuje spójny stan dokumentu.
* **Waliduj wymiary kształtu** – bardzo duże szerokości lub wysokości mogą powodować problemy z renderowaniem w starszych wersjach Worda.
* **Grupuj przed stylizacją** – zastosowanie kolorów wypełnienia lub stylów linii do grupy po dodaniu wszystkich elementów zapewnia jednolity wygląd.

## Zakończenie

Teraz rozumiesz **jak wstawić elipsę** i **jak dodać prostokąt** wewnątrz pogrupowanego kontenera w dokumencie Word przy użyciu Aspose.Words. Poprzez konsekwentne **przenoszenie kursora do kształtu** przed każdym wstawieniem, utrzymujesz czystą hierarchię i unikasz przypadkowego umieszczenia. Pełny przykład kompiluje się, uruchamia i tworzy pogrupowany kształt, który można dalej dostosowywać lub eksportować.

Gotowy, aby odkrywać dalej? Spróbuj połączyć tę technikę z **jak utworzyć kształt grupy** dla złożonych diagramów lub eksperymentuj z **wstawianiem prostokątnego kształtu w Wordzie** wraz z polami tekstowymi dla bogatego generowania raportów. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak utworzyć prostokątny kształt i grupować kształty w Wordzie przy użyciu Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Jak utworzyć pusty dokument Word i dodać ukryty kształt elipsy w C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [Jak utworzyć docx z kształtem grupy i dodać interaktywne kontrolki w C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}