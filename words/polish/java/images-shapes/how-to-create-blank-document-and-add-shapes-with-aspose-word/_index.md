---
category: general
date: 2026-09-30
description: Utwórz pusty dokument i wstaw kształt prostokąta, elipsę oraz grupuj
  wiele kształtów w C# przy użyciu Aspose.Words. Dowiedz się, jak wstawiać kształty
  i jak tworzyć grupę.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: pl
lastmod: 2026-09-30
og_description: Utwórz pusty dokument w C# i dowiedz się, jak wstawiać kształty oraz
  grupować wiele kształtów za pomocą Aspose.Words. Postępuj zgodnie z instrukcją krok
  po kroku.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Utwórz pusty dokument i grupuj kształty w C# – przewodnik Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Jak utworzyć pusty dokument i dodać kształty przy użyciu Aspose.Words w C#
url: /pl/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć pusty dokument i dodać kształty przy użyciu Aspose.Words w C#

Jeśli potrzebujesz **utworzyć pusty dokument** i wypełnić go grafiką, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Zobaczysz, jak **wstawić prostokąt**, dodać inne obiekty rysunkowe oraz **zgrupować wiele kształtów**, aby zachowywały się jak jedna jednostka.

Praca z kształtami jest częstym wymogiem przy generowaniu umów, certyfikatów czy raportów na zamówienie. W tym tutorialu poznasz pełny przepływ pracy, od inicjalizacji dokumentu po zapisanie finalnego pliku, korzystając z API Aspose.Words dla .NET.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* .NET 6.0 (lub nowszy) SDK zainstalowany  
* Ważną licencję Aspose.Words for .NET (bezpłatna wersja próbna wystarczy dla tego przykładu)  
* IDE, takie jak Visual Studio 2022 lub Visual Studio Code  

Nie są wymagane żadne dodatkowe pakiety NuGet poza `Aspose.Words`.

## Jak utworzyć pusty dokument i pracować z kształtami

Pierwszym krokiem jest utworzenie obiektu `Document`. Obiekt ten reprezentuje plik Word w pamięci i daje dostęp do `DocumentBuilder`, który jest podstawowym narzędziem do wstawiania treści.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Dlaczego to ważne:** Pusty dokument zapewnia czyste płótno. `DocumentBuilder` utrzymuje bieżący punkt wstawiania, więc każdy dodany kształt jest automatycznie umieszczany na odpowiedniej stronie.

## Wstaw prostokąt i inne kształty

Następnie dodajemy prostokąt i elipsę. Oba wywołania używają tej samej metody `InsertShape`, co jest zalecaną metodą **wstawiania kształtów** w Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*Metoda `InsertShape` automatycznie pozycjonuje kształt w bieżącym miejscu kursora.* Jeśli potrzebujesz precyzyjnego umiejscowienia, możesz po wstawieniu dostosować `Shape.Left` i `Shape.Top`.

## Zgrupuj wiele kształtów w jeden obiekt

Teraz łączymy prostokąt i elipsę w jedną logiczną jednostkę. Grupowanie jest przydatne, gdy chcesz przesuwać lub zmieniać rozmiar kilku kształtów jednocześnie.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**Jak to działa:** `InsertGroupShape` tworzy kontener zachowujący się jak każdy inny `Shape`. Wywołując `AppendChild`, przenosisz istniejące kształty do kontenera, który automatycznie aktualizuje ich współrzędne względne.

### Praktyczna wskazówka

Jeśli później będziesz potrzebował **utworzyć grupę** programowo dla więcej niż dwóch kształtów, po prostu powtórz `AppendChild` dla każdej dodatkowej instancji `Shape`. Grupa może zawierać dowolną liczbę obiektów rysunkowych, w tym obrazy, pola tekstowe czy nawet inne grupy.

## Pełny przykład – jak wstawić kształty i zapisać dokument

Poniżej znajduje się kompletny, gotowy do uruchomienia program, który demonstruje każdy omawiany krok. Uruchomienie kodu tworzy plik `ShapesDemo.docx` zawierający prostokąt, elipsę oraz zgrupowany kształt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Oczekiwany wynik:** Otwarcie `ShapesDemo.docx` w Microsoft Word pokazuje jedną stronę z niebieskim prostokątem, zieloną elipsą i otaczającą je szarą ramką reprezentującą grupę. Przesunięcie grupy przesuwa oba kształty razem, potwierdzając, że operacja **grupowania wielu kształtów** zakończyła się sukcesem.

## Częste pytania i obsługa przypadków brzegowych

| Pytanie | Odpowiedź |
|----------|-----------|
| *Co zrobić, jeśli potrzebuję kształtów na konkretnej stronie?* | Wywołaj `builder.MoveToDocumentEnd();` przed wstawianiem kształtów lub użyj `builder.MoveToSection(sectionIndex);`, aby skierować się do określonej sekcji. |
| *Czy mogę dodać tekst wewnątrz zgrupowanego kształtu?* | Tak. Utwórz `Shape` typu `ShapeType.TextBox`, skonfiguruj jego tekst i następnie `AppendChild` do `GroupShape`. |
| *Czy wymiary kształtów podawane są w punktach czy pikselach?* | Aspose.Words używa **punktów** (1 pt = 1/72 cala). Zapewnia to spójny rozmiar na drukarkach i wyświetlaczach. |
| *Jak zmienić obrót grupy?* | Ustaw `groupShape.RotationAngle = 45;` (stopnie). Wszystkie kształty podrzędne obracają się wokół punktu początkowego grupy. |

## Podsumowanie

Teraz wiesz, jak **utworzyć pusty dokument**, **wstawić prostokąt**, **wstawiać kształty** takie jak elipsy oraz **zgrupować wiele kształtów** w jeden obiekt przy użyciu Aspose.Words dla .NET. Pełny przykład kodu demonstruje zalecaną metodę, a powyższe wskazówki pomogą Ci dostosować rozwiązanie do bardziej złożonych scenariuszy, takich jak dodawanie pól tekstowych czy obracanie grup.

Gotowy na dalsze eksperymenty? Spróbuj dodać do grupy kształt obrazu, poeksperymentuj z różnymi kolorami wypełnienia lub wygeneruj raport wielostronicowy, w którym każda strona zawiera własny zgrupowany diagram. Te same zasady obowiązują, więc możesz skalować ten wzorzec w dowolnym projekcie automatyzacji dokumentów.

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Utwórz kształt grupowy w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Wstaw kształty w dokumentach Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Utwórz pusty dokument Word przy użyciu Aspose.Words – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}