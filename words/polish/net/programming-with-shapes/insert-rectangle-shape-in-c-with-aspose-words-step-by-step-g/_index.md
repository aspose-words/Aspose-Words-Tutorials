---
category: general
date: 2026-08-07
description: Wstaw prostokątny kształt w C# przy użyciu Aspose.Words i dowiedz się,
  jak ukryć kształt, ustawić kolor wypełnienia oraz efektywnie dodać prostokąt do
  dokumentu Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: pl
lastmod: 2026-08-07
og_description: Wstaw prostokątny kształt w dokumencie Word przy użyciu C#. Dowiedz
  się, jak ukryć kształt, ustawić kolor wypełnienia i dodać prostokątny kształt za
  pomocą Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Wstaw prostokątny kształt w C# – kompletny samouczek Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Wstaw prostokątny kształt w C# przy użyciu Aspose.Words – przewodnik krok po
  kroku
url: /pl/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw prostokątny kształt w C# przy użyciu Aspose.Words – przewodnik krok po kroku

Jeśli potrzebujesz **wstawić prostokątny kształt** do dokumentu Word z poziomu C#, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Zobaczysz, jak ustawić kolor wypełnienia, ukryć kształt, aby nie pojawiał się w ostatecznym układzie, oraz jak zapisać plik — wszystko przy użyciu kilku linii kodu.

W kolejnych sekcjach omówimy wszystko, co musisz wiedzieć: wymagania wstępne, pełną listę kodu, wyjaśnienia każdego kroku oraz wskazówki dotyczące typowych wariantów, takich jak ponowne wyświetlenie kształtu lub użycie innego koloru. Po zakończeniu będziesz w stanie **dodać prostokątny kształt** do dowolnego pliku .docx programowo.

## Wymagania wstępne

* **Aspose.Words for .NET** (wersja 23.10 lub nowsza). Możesz go zainstalować za pomocą NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK lub nowszy zainstalowany na Twoim komputerze.
* Podstawowa znajomość C# i Visual Studio (lub dowolnego wybranego IDE).

Nie są wymagane dodatkowe biblioteki — API związane z kształtami są częścią podstawowego pakietu Aspose.Words.

## Wstaw prostokątny kształt przy użyciu Aspose.Words

Główną częścią rozwiązania jest krótki, samodzielny program, który tworzy pusty dokument, wstawia prostokąt, nadaje mu kolor, ukrywa go, a następnie zapisuje plik. Poniżej znajduje się pełny kod źródłowy z komentarzami w linii, które wyjaśniają *dlaczego* każda linia jest potrzebna.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### Co robi każdy krok

| Krok | Powód |
|------|--------|
| **Create a new document** | Tworzy czyste płótno; możesz także załadować istniejący plik .docx, podając ścieżkę do `new Document(path)`. |
| **Initialize DocumentBuilder** | `DocumentBuilder` to wysokopoziomowy pomocnik, który pozwala wstawiać tekst, tabele i kształty bez konieczności pracy z niskopoziomowymi drzewami węzłów. |
| **Insert rectangle shape** | Metoda `InsertShape` zwraca obiekt `Shape`, który możesz dalej dostosowywać (rozmiar, pozycję, obramowanie itp.). |
| **Set fill color** | Właściwość `FillColor` kontroluje kolor wypełnienia; możesz użyć dowolnej wartości `Color` (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)` itp.). |
| **Hide the shape** | `Hidden = true` informuje Word, aby zignorował kształt podczas układania, jednocześnie pozostawiając go w XML dokumentu. To standardowy sposób przechowywania niewidzialnych obiektów. |
| **Save the document** | Zapisuje zmiany do pliku .docx. Zapisany plik będzie zawierał ukryty prostokątny kształt. |

## Jak ustawić kolor wypełnienia dla kształtu

Zmiana koloru wypełnienia jest tak prosta, jak przypisanie `System.Drawing.Color` do właściwości `FillColor`. Jeśli potrzebujesz niestandardowego odcienia, użyj `Color.FromArgb`:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Dlaczego to ważne*: Kolor wypełnienia jest przechowywany w XML kształtu (`<w:fill>` atrybut). Gdy kształt jest ukryty, kolor nadal istnieje, co może być przydatne przy dalszym przetwarzaniu (np. wyodrębnianie metadanych na podstawie kodów kolorów).

## Jak ukryć kształt w ostatecznym dokumencie

Flaga `Hidden` jest właściwością typu bool w klasie `Shape`. Ustawienie jej na `true` zapewnia, że kształt zostanie zignorowany przez silnik układu Worda.

```csharp
rectangleShape.Hidden = true;
```

**Typowe pułapki**

* **Ukryty vs. Widoczny** – Jeśli później potrzebujesz, aby kształt się pojawił, po prostu ustaw `Hidden = false`.
* **Kompatybilność** – Starsze wersje Worda (przed 2007) mogą traktować ukryte obiekty rysunkowe inaczej. Aspose.Words zapewnia kompatybilność, przechowując flagę w odpowiednim elemencie OOXML.

## Jak wstawiać kształt programowo

Choć w przykładzie użyto prostokąta, ta sama metoda `InsertShape` działa dla wielu innych kształtów (elipsa, trójkąt, linia itp.). Pierwszy argument to wartość wyliczenia `ShapeType`:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Wskazówka**: Jeśli potrzebujesz umieścić kształt w określonym miejscu na stronie, użyj `builder.MoveTo`, aby ustawić punkt wstawiania przed wywołaniem `InsertShape`.

## Dodaj prostokątny kształt do istniejącego dokumentu

Często będziesz modyfikować szablon zamiast zaczynać od zera. Zastąp krok 1 następującym kodem:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Wszystkie kolejne kroki pozostają identyczne, a prostokąt zostanie dodany w miejscu, w którym znajduje się kursor buildera (zazwyczaj na końcu dokumentu domyślnie).

## Obsługa przypadków brzegowych i wariantów

### 1. Ponowne wyświetlenie kształtu

Jeśli późniejsza część Twojego przepływu pracy wymaga ujawnienia ukrytego prostokąta, możesz przełączyć flagę:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Dodawanie obramowania (stroke)

Ukryty kształt może nadal mieć widoczne obramowanie, gdy zdecydujesz się go pokazać. Ustaw właściwości `LineColor` i `LineWidth`:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Absolutne pozycjonowanie prostokąta

Aby precyzyjnie kontrolować układ, zmień `WrapType` kształtu na `WrapType.Inline` (domyślnie) lub `WrapType.TopBottom` i dostosuj właściwości `Left`/`Top`:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Użycie innej jednostki miary

Aspose.Words działa w punktach (1 pt = 1/72 cala). Jeśli wolisz centymetry, najpierw dokonaj konwersji:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Pełny działający przykład

Poniżej znajduje się *pełny* program, który możesz skopiować, wkleić i uruchomić. Zawiera wszystkie niezbędne dyrektywy `using` oraz używa ścieżek bezwzględnych, które powinieneś dostosować do swojego środowiska.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Oczekiwany rezultat**: Plik `HiddenRectangleShape.docx` otwiera się w Microsoft Word bez *widocznego kształtu*, ale ukryty prostokąt jest obecny w XML dokumentu. Możesz zweryfikować jego istnienie, otwierając plik .docx jako archiwum zip i przeglądając `word/document.xml` pod kątem elementu `<w:shape>` z atrybutami `w:fill="yellow"` oraz `w:hidden="true"`.

## Podsumowanie

Teraz wiesz, jak **wstawić prostokątny kształt** do dokumentu Word przy użyciu C# i Aspose.Words, jak **ustawić kolor wypełnienia** oraz jak **ukryć kształt**, aby był niewidoczny w ostatecznym układzie. Ten sam schemat działa dla innych typów kształtów, niestandardowych kolorów i istniejących szablonów. Eksperymentuj z obramowaniami, absolutnym pozycjonowaniem i różnymi jednostkami miary, aby dopasować kształt do swoich dokładnych wymagań.

### Kolejne kroki

* Zbadaj **jak wstawiać kształt** wewnątrz tabel lub nagłówków/stopki jako znaki wodne.
* Połącz **dodawanie prostokątnego kształtu** z kontrolkami zawartości, aby tworzyć dynamiczne miejsca wstawiania.
* Przejrzyj API **manipulacji kształtami** Aspose.Words pod kątem zaawansowanych funkcji, takich jak obrót, wypełnienia gradientowe i import SVG.

Śmiało dostosuj kod do własnego projektu i daj nam znać w komentarzach, które wyzwanie związane z kształtami rozwiązałeś jako kolejne!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}