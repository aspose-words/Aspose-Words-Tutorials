---
category: general
date: 2026-09-11
description: Dowiedz się, jak ukryć kształt w programie Word przy użyciu C#. Ten przewodnik
  pokazuje również, jak wstawić prostokątny kształt oraz wstawić kształt do dokumentu
  Word przy użyciu Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: pl
lastmod: 2026-09-11
og_description: Jak ukryć kształt w Wordzie przy użyciu C# i Aspose.Words. Postępuj
  zgodnie z instrukcją krok po kroku, aby wstawić prostokątny kształt i zarządzać
  kształtami w dokumencie Word.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Jak ukryć kształt w Wordzie – kompletny przewodnik C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Jak ukryć kształt w Wordzie przy użyciu C# i Aspose.Words
url: /pl/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak ukryć kształt w Wordzie przy użyciu C# i Aspose.Words

Jeśli potrzebujesz ukryć kształt w Wordzie, zachowując go w strukturze dokumentu, ten samouczek pokaże Ci dokładnie, jak to zrobić. Korzystając z Aspose.Words for .NET możesz wstawić prostokątny kształt, ukryć go i nadal zachować jego pozycję do późniejszej obróbki.

Automatyzacja Worda często wymaga precyzyjnej kontroli nad kształtami — niezależnie od tego, czy generujesz szablony, przygotowujesz raporty, czy budujesz usługę edycji dokumentów. Po przeczytaniu tego przewodnika będziesz w stanie:

* Wstawić prostokątny kształt do dokumentu Word (`insert rectangle shape`).
* Ukryć dowolny kształt bez jego usuwania (`how to hide shape in word`).
* Zapisać wynik i zweryfikować, że ukryty kształt nie pojawia się w renderowanym widoku (`insert shape into word document`).

Przykład działa z Aspose.Words 24.10 lub nowszym i jest przeznaczony dla .NET 6.0+, ale koncepcje mają zastosowanie także do wcześniejszych wersji.

## Wymagania wstępne

* **Aspose.Words for .NET** ≥ 24.10. Możesz uzyskać darmową tymczasową licencję na stronie Aspose.
* **.NET SDK** 6.0 lub nowszy zainstalowany na Twoim komputerze.
* Środowisko programistyczne, takie jak Visual Studio 2022, VS Code lub Rider.
* Podstawowa znajomość C# oraz koncepcji Word Open XML (opcjonalnie, ale pomocna).

## Jak ukryć kształt w Wordzie przy użyciu Aspose.Words

Poniżej znajduje się kompletny, gotowy do uruchomienia program, który demonstruje cały przepływ pracy — od tworzenia dokumentu, przez wstawianie prostokątnego kształtu, aż po jego ukrycie.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Wyjaśnienie poszczególnych kroków

1. **Utworzenie nowego dokumentu** – `Document` reprezentuje plik Word w pamięci. `DocumentBuilder` zapewnia płynne API do wstawiania treści.
2. **Wstawienie prostokątnego kształtu** – `InsertShape` tworzy obiekt rysunkowy typu `Rectangle`. Wymiary podawane są w punktach (1 pt ≈ 1/72 in). Spełnia to wymaganie `insert rectangle shape`.
3. **Ukrycie kształtu** – Ustawienie `Shape.Hidden = true` oznacza kształt jako ukryty w znacznikach Worda (`<w:hidden/>`). Kształt pozostaje częścią drzewa dokumentu, więc możesz go później odkryć lub odwołać się do niego programowo. To sedno `how to hide shape in word`.
4. **Zapisanie pliku** – Dokument jest zapisywany do `output.docx`. Po otwarciu w Microsoft Word prostokąt nie będzie widoczny, ale nadal istnieje w XML i można go sprawdzić przy pomocy przeglądarki ZIP lub Open XML SDK.

### Oczekiwany rezultat

Otwórz `output.docx` w Microsoft Word:

* Dokument wydaje się pusty — brak widocznego kształtu.
* Jeśli przejrzysz wewnętrzny XML (`word/document.xml`), znajdziesz element `<w:pict>` z atrybutem `<w:hidden/>`, co potwierdza, że kształt jest obecny, ale ukryty.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

Ukryty kształt można ponownie uczynić widocznym, ustawiając `Hidden = false` i ponownie zapisując dokument.

## Wstaw prostokątny kształt do dokumentu Word

Choć głównym celem jest ukrycie kształtu, wiele scenariuszy zaczyna się od jego wstawienia. Metoda `InsertShape` obsługuje wiele wartości `ShapeType`, w tym `Rectangle`, `Ellipse`, `Line` oraz obrazy niestandardowe.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Dlaczego używać prostokąta?**  
Prostokąt zapewnia czysty, osiowo wyrównany kontener, który może pomieścić tekst, obrazy lub inne zagnieżdżone kształty. Często służy jako placeholder dla dynamicznej treści, takiej jak tabele czy wykresy. Wstawiając prostokąt najpierw, zachowujesz spójność układu nawet po jego późniejszym ukryciu.

## Wstawianie kształtu do dokumentu Word — dobre praktyki

Podczas `insert shape into word document` rozważ następujące kwestie:

* **Ustaw wyraźne wymiary** – Unikaj polegania na automatycznym dopasowywaniu; podaj szerokość i wysokość w punktach, aby zapewnić spójny układ na różnych platformach.
* **Zdefiniuj pozycjonowanie** – Domyślnie kształt jest zakotwiczony do bieżącego akapitu. Użyj `builder.MoveTo` lub `builder.StartBookmark`, aby umieścić go precyzyjnie.
* **Zastosuj stylizację wcześnie** – Kolor wypełnienia, styl linii i opływanie tekstu wpływają na ostateczny wygląd. Nawet ukryte kształty korzystają z prawidłowej stylizacji, ponieważ znacznik pozostaje niezmieniony.
* **Kompatybilność wersji** – Właściwość `Hidden` jest dostępna dopiero od Aspose.Words 24.10. Jeśli celujesz w starszą wersję, możesz ręcznie dodać atrybut `<w:hidden/>` przy użyciu API `Node`.

### Ręczne dodawanie atrybutu hidden (fallback)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Kompletny przykład end‑to‑end

Łącząc wszystko razem, oto pojedynczy program, który:

1. Wstawia prostokątny kształt.
2. Ukrywa go.
3. Wstawia widoczną elipsę dla kontrastu.
4. Zapisuje dokument.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

Uruchomienie programu generuje `demo_output.docx`. Po otwarciu zobaczysz tylko koralową elipsę; zielony prostokąt jest obecny w XML, ale ukryty w widoku.

## Częste pytania i przypadki brzegowe

**P: Czy ukrycie kształtu wpływa na paginację?**  
O: Nie. Ukryte kształty są ignorowane przez silnik układu, więc nie zajmują miejsca. Jest to przydatne przy placeholderach, które nie powinny wpływać na podziały stron.

**P: Czy mogę ukryć kształt będący częścią nagłówka lub stopki?**  
O: Tak. Ta sama właściwość `Hidden` działa na kształtach znajdujących się w dowolnym miejscu drzewa dokumentu, w tym w nagłówkach, stopkach i nawet wewnątrz tabel.

**P: Co zrobić, gdy muszę ukryć wiele kształtów jednocześnie?**  
O: Przejdź przez kolekcję `Document.GetChildNodes(NodeType.Shape, true)` i ustaw `Hidden = true` dla każdego docelowego kształtu.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**P: Czy atrybut hidden jest zachowywany przy konwersji do PDF?**  
O: Przy konwersji do PDF ukryte kształty są domyślnie pomijane, co odpowiada zachowaniu Worda. Jeśli potrzebujesz ich w PDF, musisz je odkryć przed konwersją.

## Wskazówki i pułapki

* **Pro tip:** Ustaw `shape.WrapType = WrapType.None` przed ukryciem, jeśli planujesz później odkryć kształt bez zakłócania otaczającego tekstu.
* **Uwaga na starsze wersje Aspose.Words:** Właściwość `Hidden` rzuca `NotSupportedException` przed wersją 24.10. W takim wypadku użyj ręcznego podejścia XML.
* **Testowanie:** Zawsze otwieraj wygenerowany `.docx` w Wordzie i używaj opcji „Pokaż znacznik XML” (zakładka Developer), aby zweryfikować obecność atrybutu `<w:hidden/>`.

## Podsumowanie

Teraz wiesz, jak ukryć kształt w Wordzie przy użyciu C# i Aspose.Words, a także jak wstawić prostokątny kształt i wstawiać kształt do dokumentu Word z pełną kontrolą nad widocznością. Dzięki właściwości `Hidden` możesz zachować kształty w modelu dokumentu do późniejszej obróbki, jednocześnie prezentując czysty widok użytkownikom.

Następnie odkryj powiązane tematy, takie jak **aktualizacja właściwości kształtu w czasie wykonywania**, **konwersja ukrytych kształtów na obrazy** lub **użycie Open XML SDK do bezpośredniej manipulacji ukrytymi elementami**. Te rozszerzenia pogłębią Twoją wiedzę.

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz szczegółowe wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i eksplorować alternatywne podejścia w własnych projektach.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}