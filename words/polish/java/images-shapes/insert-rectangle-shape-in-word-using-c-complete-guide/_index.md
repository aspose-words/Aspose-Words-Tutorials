---
category: general
date: 2026-08-04
description: Wstaw prostokątny kształt w dokumencie Word przy użyciu C#. Dowiedz się,
  jak grupować kształty w Wordzie, zapisać dokument jako docx oraz używać DocumentBuilder
  do zaawansowanych układów.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: pl
lastmod: 2026-08-04
og_description: Wstaw prostokątny kształt do pliku Word przy użyciu C# i następnie
  grupuj kształty w celu uzyskania zaawansowanych układów. Ten samouczek obejmuje
  także zapisywanie dokumentu jako docx oraz efektywne korzystanie z DocumentBuilder.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Wstaw kształt prostokąta w Word – przewodnik krok po kroku w C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Wstawianie prostokątnego kształtu w Wordzie przy użyciu C# – kompletny przewodnik
url: /pl/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw prostokątny kształt w Wordzie przy użyciu C# – kompletny przewodnik

Jeśli potrzebujesz **wstawić prostokątny kształt** w dokumencie Word przy użyciu C#, ten samouczek pokaże Ci dokładnie, jak to zrobić. Dowiesz się także **jak grupować kształty** w Wordzie, **zapisać dokument jako docx** oraz **jak używać Buildera** dla czystego, łatwego w utrzymaniu kodu.

Praca z kształtami jest częstym wymogiem przy generowaniu raportów, certyfikatów lub niestandardowych układów programowo. Po zakończeniu tego przewodnika będziesz mieć w pełni działający przykład, który tworzy prostokąt, dodaje elipsę, grupuje je i zapisuje wynik jako plik DOCX.

## Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz:

* .NET 6.0 lub nowszy zainstalowany  
* Visual Studio 2022 (lub dowolne IDE obsługujące C#)  
* Bibliotekę **Aspose.Words for .NET** (dostępną przez NuGet)  

Możesz dodać bibliotekę za pomocą następującego polecenia:

```bash
dotnet add package Aspose.Words
```

## Wstaw prostokątny kształt przy użyciu DocumentBuilder

Pierwszym krokiem jest utworzenie nowego `Document` i `DocumentBuilder`. Builder zapewnia płynne API do wstawiania treści, w tym kształtów.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

Instancja `DocumentBuilder` jest podstawowym obiektem, którego użyjesz do **wstawiania prostokątnego kształtu** oraz innych elementów. Śledzi ona bieżącą pozycję kursora w dokumencie, więc każde wstawienie odbywa się dokładnie tam, gdzie tego potrzebujesz.

## Jak wstawić prostokątny kształt

Gdy builder jest gotowy, wywołaj `InsertShape`. Określasz `ShapeType`, szerokość i wysokość w punktach (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Dlaczego to ważne*: Ustawienie `FillColor` i `StrokeColor` sprawia, że prostokąt jest wizualnie odróżniony, co pomaga przy późniejszym grupowaniu go z innymi kształtami.

## Jak grupować kształty w Wordzie

Grupowanie kształtów pozwala na przemieszczanie, obracanie lub formatowanie wielu obiektów jako jednej jednostki. Po wstawieniu prostokąta, dodaj kolejny kształt (elipsę w tym przykładzie), a następnie utwórz `GroupShape`.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

Wywołanie `InsertGroupShape` tworzy placeholder, który może pomieścić dowolną liczbę kształtów podrzędnych. Dodając prostokąt i elipsę, skutecznie **grupujesz kształty w Wordzie**. Grupa zachowuje się jak pojedynczy kształt — możesz ją przemieścić, dodać obramowanie lub zmienić rozmiar, nie wpływając na wewnętrzny układ poszczególnych elementów.

### Porada profesjonalna

Po grupowaniu możesz zmienić pozycję grupy względem strony:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Zapisz dokument jako docx

Gdy kształty są już ułożone, musisz zapisać plik. Metoda `Document.Save` automatycznie określa format na podstawie rozszerzenia pliku. Aby **zapisać dokument jako docx**, podaj ścieżkę kończącą się na `.docx`.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

Uruchomienie programu tworzy `output.docx`. Otwórz plik w Microsoft Word i zobaczysz jasno‑niebieski prostokąt oraz jasno‑koralową elipsę zgrupowane razem. Możesz kliknąć grupę i przemieścić ją jako pojedynczy obiekt.

## Jak efektywnie używać DocumentBuilder

`DocumentBuilder` to nie tylko wstawianie kształtów; obsługuje także tekst, tabele, nagłówki i stopki. Gdy łączysz tworzenie kształtów z tekstem, pamiętaj o zresetowaniu kursora, jeśli musisz wstawić treść w innym miejscu:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Utrzymywanie stanu buildera w sposób jawny zapobiega przypadkowym nadpisaniom i ułatwia utrzymanie kodu.

## Przypadki brzegowe i warianty

| Sytuacja | Zalecane podejście |
|-----------|----------------------|
| **Więcej niż dwa kształty** | Wstaw każdy kształt, a następnie wywołaj `AppendChild` dla każdego kształtu przed zapisem. |
| **Zagnieżdżone grupy** | Utwórz grupę, dodaj kształty, a następnie wstaw tę grupę do innego `GroupShape`. |
| **Różne jednostki miary** | Użyj `builder.ConvertPixelsToPoints`, jeśli masz wymiary w pikselach. |
| **Kompatybilność ze starszymi wersjami Word** | Zapisz jako `.doc`, zmieniając rozszerzenie; większość funkcji kształtów nadal działa. |

## Kompletny działający przykład

Poniżej znajduje się pełny program, który możesz skopiować i wkleić do nowego projektu konsolowego. Nie są wymagane dodatkowe fragmenty kodu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Oczekiwany wynik**: Po otwarciu `output.docx` zobaczysz jasno‑niebieski prostokąt i jasno‑koralową elipsę zgrupowane razem, umieszczone 150 pt od lewego marginesu i 100 pt od góry. Podpis pojawia się pod grupą.

## Zakończenie

Teraz wiesz, jak **wstawić prostokątny kształt** w pliku Word przy użyciu C#, **jak grupować kształty w Wordzie** oraz **jak zapisać dokument jako docx** przy użyciu Aspose.Words `DocumentBuilder`. Opanowując te kroki, możesz tworzyć złożone układy — certyfikaty, raporty lub niestandardowe formularze — w pełni za pomocą kodu.

Następnie poznaj powiązane tematy, takie jak **dodawanie pól tekstowych**, **praca z tabelami** lub **eksport do PDF**. Każdy z nich opiera się na tych samych podstawach `DocumentBuilder`, które właśnie ćwiczyłeś.

Gotowy, aby zautomatyzować swoje dokumenty Word? Spróbuj rozbudować przykład o więcej kształtów, zastosować gradienty lub iterować po danych, aby wygenerować pełny raport w jednym uruchomieniu. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz grupowy kształt w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Wstaw kształty w dokumentach Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Utwórz prostokątny kształt w Wordzie przy użyciu Aspose.Words – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}