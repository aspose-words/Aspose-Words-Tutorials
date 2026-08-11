---
category: general
date: 2026-08-10
description: Utwórz dokument Word programowo przy użyciu Aspose.Words, dowiedz się,
  jak grupować wiele kształtów w Wordzie, dodać prostokąt do Worda oraz utworzyć grupę
  kształtów w C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: pl
lastmod: 2026-08-10
og_description: Twórz dokumenty Word programowo przy użyciu Aspose.Words. Ten przewodnik
  pokazuje, jak grupować wiele kształtów w Wordzie, dodać prostokąt do Worda oraz
  osadzić kontrolkę zawartości tekstu prostego, wszystko w C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Tworzenie dokumentu Word programowo – grupowanie kształtów w C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Tworzenie dokumentu Word programowo i grupowanie kształtów w C#
url: /pl/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz dokument Word programowo i grupuj kształty w C#

Jeśli potrzebujesz **create word document programmatically**, ten tutorial pokazuje, jak zbudować plik DOCX przy użyciu Aspose.Words i **group multiple shapes word** razem. Omówimy także **add rectangle to word** oraz **how to create group shape**, które zawiera zarówno prostokąt, jak i elipsę, plus zwykły tekstowy StructuredDocumentTag do wprowadzania danych przez użytkownika.

Na koniec otrzymasz gotowy plik Word, który zawiera grupowany kształt prostokąt‑elipsa oraz kontrolkę zawartości, w której użytkownik może wpisać imię. Nie jest wymagana ręczna edycja w Word po uruchomieniu kodu.

## Co będzie potrzebne

- .NET 6.0 lub nowszy (przykład jest skierowany do .NET 6, ale działa z każdą nowszą wersją .NET)
- Licencja Aspose.Words for .NET (bezpłatna wersja próbna działa do testów)
- Visual Studio 2022 lub dowolne IDE C#, które preferujesz
- Podstawowa znajomość składni C#

## Tworzenie dokumentu Word programowo – ogólny przepływ pracy

Proces składa się z trzech logicznych faz:

1. **Initialize** obiekt `Document` i `DocumentBuilder` – podstawa każdego pliku Word, który generujesz.
2. **Build a group shape**, które zawiera prostokąt i elipsę – demonstruje **group multiple shapes word** oraz **how to create group shape**.
3. **Insert a StructuredDocumentTag (SDT)** – kontrolka zawartości w formie zwykłego tekstu, która pozwala użytkownikom wprowadzać dane, ilustrując **add rectangle to word** jako część ogólnego układu dokumentu.

Poniżej znajduje się kompletny, gotowy do uruchomienia kod, a następnie szczegółowy podział krok po kroku.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Krok 1 – Inicjalizacja dokumentu i buildera
Obiekt `Document` reprezentuje cały plik DOCX, natomiast `DocumentBuilder` udostępnia wygodne API do dodawania treści. Ich inicjalizacja jest pierwszym wymogiem, gdy **create word document programmatically**.

> **Pro tip:** Jeśli planujesz ponowne użycie tego samego dokumentu w wielu operacjach, zachowaj jedną instancję `DocumentBuilder`, aby uniknąć niepotrzebnego tworzenia obiektów.

### Krok 2 – Utworzenie kontenera grupy kształtów
Obiekt `Shape` z `ShapeType.Group` działa jako płótno, które może zawierać inne kształty. Ustawienie `Width` i `Height` definiuje ramkę ograniczającą grupę. To jest sedno **how to create group shape** w Aspose.Words.

> **Edge case:** Jeśli szerokość grupy jest mniejsza niż łączna szerokość jej elementów, elementy zostaną przycięte. Zawsze twórz grupę wystarczająco dużą, aby pomieścić każdy kształt potomny.

### Krok 3 – Dodanie prostokąta do Word
Prostokąt jest tworzony przy użyciu `ShapeType.Rectangle`. Właściwości `Left` i `Top` pozycjonują go względem początku grupy. Ten krok demonstruje **add rectangle to word** i pokazuje, jak kontrolować dokładne położenie.

> **Common mistake:** Zapomnienie o ustawieniu `Left`/`Top` powoduje, że prostokąt pojawia się w domyślnym początku grupy (0,0), co może nakładać się na inne elementy.

### Krok 4 – Dodanie elipsy (koła) do grupy
Elipsa jest dodawana w ten sam sposób co prostokąt, ale z `ShapeType.Ellipse`. `Left = 210` przesuwa ją w prawo od prostokąta, tworząc wizualnie odrębną parę kształtów wewnątrz tej samej grupy.

> **Why use a group?** Grupowanie pozwala później przesuwać, obracać lub zmieniać rozmiar obu kształtów jednocześnie jedną operacją, zachowując ich względny układ.

### Krok 5 – Wstawienie gotowej grupy kształtów do dokumentu
`builder.InsertNode(groupShape)` umieszcza całą grupę w bieżącej pozycji kursora. Ponieważ grupa już zawiera swoje elementy, nie potrzebujesz dodatkowych wywołań insert dla prostokąta lub elipsy.

### Krok 6 – Utworzenie zwykłego tekstowego StructuredDocumentTag (SDT)
StructuredDocumentTag jest kontrolką zawartości, którą użytkownicy mogą wypełniać po otwarciu dokumentu w Word. Ustawienie `Title = "CustomerName"` nadaje kontrolce znaczący identyfikator, przydatny przy późniejszym wyciąganiu danych.

> **Why a plain‑text SDT?** Ogranicza wprowadzanie do zwykłego tekstu, zapobiegając przypadkowemu formatowaniu, które mogłoby zakłócić dalsze przetwarzanie.

### Krok 7 – Zapisanie dokumentu
`doc.Save("GroupAndSDT.docx")` zapisuje plik na dysku. Powstały DOCX zawiera grupowane kształty oraz SDT. Otwierając plik w Microsoft Word zobaczysz prostokąt obok koła, oba wybieralne jako jeden obiekt, a pod nimi placeholder „Enter name here …”.

#### Oczekiwany wynik
- Plik o nazwie **GroupAndSDT.docx** w folderze wykonywania.
- W Word: grupowany kształt (prostokąt + elipsa), który możesz przesuwać jako jedną jednostkę.
- Bezpośrednio pod grupą, szara kontrolka zawartości zachęcająca użytkownika do wpisania imienia.

## Dodatkowe warianty i najlepsze praktyki

### Użycie różnych typów kształtów
Możesz zamienić `ShapeType.Rectangle` lub `ShapeType.Ellipse` na dowolny inny `ShapeType` (np. `ShapeType.Polygon`, `ShapeType.Line`). Logika grupowania pozostaje identyczna.

### Ustawianie koloru wypełnienia i obramowań
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Dodanie wypełnienia i obrysu poprawia wizualne odróżnienie, szczególnie gdy dokument jest udostępniany osobom nietechnicznym.

### Obracanie całej grupy
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Obracanie grupy jest bardziej wydajne niż obracanie każdego elementu osobno.

### Eksport do PDF
Jeśli potrzebujesz wersji PDF, po prostu wywołaj:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Wszystkie grupowane kształty oraz SDT (wyświetlane jako pole tekstowe) pojawią się w pliku PDF.

## Częste pułapki i jak ich unikać

| Objaw | Przyczyna | Rozwiązanie |
|---------|-------|


## Co warto nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}