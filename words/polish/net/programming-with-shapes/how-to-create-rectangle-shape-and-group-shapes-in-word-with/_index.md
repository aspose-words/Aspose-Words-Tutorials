---
category: general
date: 2026-09-05
description: Utwórz prostokątny kształt w dokumencie Word przy użyciu Aspose.Words,
  a następnie dowiedz się, jak wstawiać elipsę i grupować kształty w Wordzie, aby
  uzyskać bogatsze układy.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: pl
lastmod: 2026-09-05
og_description: Utwórz prostokątny kształt w dokumencie Word przy użyciu Aspose.Words,
  a następnie zobacz, jak wstawić elipsę i grupować kształty w Wordzie w celu tworzenia
  złożonych układów.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Tworzenie prostokątnego kształtu i grupowanie kształtów w Word – przewodnik
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Jak utworzyć prostokątny kształt i grupować kształty w Wordzie przy użyciu
  Aspose.Words
url: /pl/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć prostokątny kształt i grupować kształty w Wordzie przy użyciu Aspose.Words

Jeśli potrzebujesz **utworzyć prostokątny kształt** w dokumencie Word, ten przewodnik pokaże Ci dokładne kroki z użyciem Aspose.Words dla .NET. Zobaczysz także, jak wstawić elipsę, grupować kształty w Wordzie i zapisać wynik jako plik DOCX. Rozwiązanie działa w każdym projekcie .NET 6+ i nie wymaga zainstalowanego Microsoft Office na serwerze.

Samouczek obejmuje wszystko – od konfiguracji projektu po obsługę typowych problemów z układem – więc możesz od razu skopiować kod i uruchomić go.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* .NET 6 SDK lub nowszy zainstalowany  
* IDE zgodne z NuGet (Visual Studio, Rider lub VS Code)  
* Licencję Aspose.Words for .NET (lub tymczasowy klucz ewaluacyjny)  
* Podstawową znajomość C# oraz struktury dokumentu Word  

Te elementy umożliwiają kompilację kodu i prawidłowe renderowanie kształtów.

## Krok 1: Utwórz projekt i dodaj Aspose.Words

Utwórz nowy projekt konsolowy i dodaj pakiet Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Pakiet udostępnia klasy `Document`, `DocumentBuilder`, `Shape` i `GroupShape`, które są używane w całym tym samouczku.

## Krok 2: Zainicjuj pusty dokument i builder

Obiekt `Document` reprezentuje cały plik Word, natomiast `DocumentBuilder` pozwala wstawiać zawartość programowo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Utworzenie dokumentu w pierwszej kolejności zapewnia, że wszystkie późniejsze operacje na kształtach mają prawidłowy kontener.

## Krok 3: **Utwórz prostokątny kształt** i ustaw jego wymiary

Prostokąt jest najczęściej używanym kontenerem dla tekstu lub obrazów. Definiujesz jego rozmiar w punktach (1 pt ≈ 1/72 cala).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

Dlaczego ten krok jest ważny: klasa `Shape` enkapsuluje geometrię, wypełnienie i właściwości linii. Ustawienie `Width` i `Height` przed wstawieniem gwarantuje, że kształt pojawi się w oczekiwanym rozmiarze.

## Krok 4: **Jak wstawić elipsę** – dodaj kształt elipsy

Elipsa może być używana jako ikona, znacznik lub element dekoracyjny. Kod jest analogiczny do tworzenia prostokąta, zmienia się jedynie `ShapeType`.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

Właściwości `FillColor` i `Line.Color` pokazują, jak dostosować wygląd bez użycia zewnętrznych obrazów.

## Krok 5: **Grupowanie kształtów w Wordzie** – połącz prostokąt i elipsę

Grupowanie pozwala przesuwać, zmieniać rozmiar lub obracać wiele kształtów jako jedną jednostkę. Jest to niezbędne, gdy potrzebujesz złożonej grafiki (np. ikony z etykietą).

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

Gdy wywołujesz `AppendChild`, oryginalne kształty są usuwane z głównego przepływu dokumentu i stają się dziećmi `GroupShape`. Grupa zachowuje się jak pojedynczy kształt, co upraszcza późniejsze korekty układu.

## Krok 6: Zapisz dokument

Na koniec zapisz dokument na dysku. Możesz wybrać dowolny obsługiwany format (`.docx`, `.pdf`, `.html` itp.). W tym samouczku pozostajemy przy natywnym formacie Word.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Po uruchomieniu programu otwórz *GroupShape.docx* w Microsoft Word. Zobaczysz prostokąt i elipsę połączone w grupę, umieszczone w określonych współrzędnych.

## Typowe warianty i przypadki brzegowe

| Sytuacja | Co zmienić | Powód |
|-----------|----------------|--------|
| **Inne jednostki rozmiaru** | Użyj `ConvertUtil.InchToPoint(2.5)` dla cali lub `ConvertUtil.MillimeterToPoint(30)` dla milimetrów. | Utrzymuje czytelność kodu przy nie‑punktowych pomiarach. |
| **Dodawanie tekstu wewnątrz prostokąta** | Utwórz węzeł `Paragraph`, ustaw jego właściwość `Text` i dodaj go do `rectangleShape` za pomocą `AppendChild`. | Pozwala oznaczyć kształt bez osobnych pól tekstowych. |
| **Obracanie grupy** | Ustaw `groupShape.Rotation = 45;` (stopnie). | Przydatne przy tworzeniu ukośnych odznak lub znaków wodnych. |
| **Zapis jako PDF** | Wywołaj `doc.Save("GroupShape.pdf");`. | Aspose.Words automatycznie rasteryzuje wektorowe kształty przy eksporcie do PDF. |
| **Wiele grup** | Utwórz dodatkowe instancje `GroupShape` i powtórz kroki dołączania/wstawiania. | Umożliwia złożone układy stron z kilkoma niezależnymi kompozytami. |

### Pro tip

Zawsze dodawaj kształty **przed** ich grupowaniem. Jeśli spróbujesz pogrupować kształt, który już jest częścią innej grupy, Aspose.Words zgłosi `ArgumentException`. Budowanie grupy w jednej metodzie zapobiega temu błędowi w czasie wykonywania.

### Uwaga

* **System współrzędnych** – `Left` i `Top` liczone są od lewego i górnego marginesu strony, a nie od krawędzi dokumentu. Nieporozumienie może spowodować umieszczenie kształtów poza stroną.  
* **Licencjonowanie** – Bez ważnej licencji zapisany dokument będzie zawierał znak wodny „Aspose.Words for .NET Evaluation”. Zastosuj licencję na początku kodu (`License license = new License(); license.SetLicense("Aspose.Words.lic");`), aby go uniknąć.

## Pełny kod źródłowy (gotowy do uruchomienia)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Uruchomienie tego programu tworzy *GroupShape.docx* z pogrupowanymi kształtami dokładnie tak, jak opisano.

## Podsumowanie

Teraz wiesz, jak **utworzyć prostokątny kształt**, **wstawić elipsę** oraz **grupować kształty w Wordzie** przy użyciu Aspose.Words. Pełny przykład demonstruje cały przepływ – od inicjalizacji dokumentu po zapis finalnego pliku – dzięki czemu możesz włączyć obsługę kształtów do dowolnego zautomatyzowanego raportu lub rozwiązania generującego dokumenty.

### Co dalej?

* Poznaj **aspose.words create shapes** dla bardziej złożonej geometrii, takiej jak `Polygon` czy `Freeform`.  
* Połącz pogrupowane kształty z **content controls**, aby budować dynamiczne szablony.  
* Przekonwertuj DOCX na PDF lub HTML, aby zobaczyć, jak wektorowe kształty są renderowane w różnych formatach.  

Śmiało eksperymentuj z różnymi rozmiarami, kolorami i obrotami. Gdy opanujesz grupowanie kształtów, będziesz w stanie tworzyć zaawansowane diagramy, odznaki i niestandardowe elementy UI bezpośrednio w dokumentach Word.


## Co powinieneś nauczyć się następnie?


Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz szczegółowe wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}