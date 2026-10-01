---
category: general
date: 2026-09-30
description: Grupowanie kształtów w Wordzie przy użyciu C# – dowiedz się, jak grupować
  kształty, dodawać prostokąt i elipsę oraz programowo wstawiać prostokąt do dokumentów
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: pl
lastmod: 2026-09-30
og_description: Grupuj kształty w programie Word przy użyciu C# i Aspose.Words. Przejdź
  przez ten kompletny przewodnik, aby dodać prostokąt, dodać elipsę i dowiedzieć się,
  jak efektywnie grupować kształty.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Grupowanie kształtów w Wordzie przy użyciu C# – przewodnik krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Jak grupować kształty w Wordzie przy użyciu C# i Aspose.Words
url: /pl/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak grupować kształty w Wordzie przy użyciu C# i Aspose.Words

Jeśli potrzebujesz **grupować kształty w Wordzie** programowo, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Zobaczysz, jak dodać prostokąt, dodać elipsę, a następnie połączyć je w jedną grupę kształtów przy użyciu biblioteki Aspose.Words dla .NET.

Praca z kształtami jest częstym wymogiem przy automatycznym generowaniu raportów, umów czy materiałów marketingowych. Po zakończeniu tego tutorialu będziesz mieć wielokrotnego użytku metodę C#, która ładuje plik DOCX, wstawia prostokąt i elipsę, grupuje je i zapisuje wynik — wszystko bez ręcznego otwierania Worda.

## Prerequisites

Zanim rozpoczniesz, upewnij się, że masz:

* .NET 6.0 SDK lub nowszy zainstalowany  
* Środowisko programistyczne, takie jak Visual Studio 2022 (wersja Community działa)  
* Licencję Aspose.Words for .NET lub darmową wersję ewaluacyjną (API działa bez licencji, ale dodaje znak wodny)  

Potrzebujesz także źródłowego dokumentu Word (`input.docx`) w folderze, do którego możesz odwołać się z kodu. Dokument może być pusty; tutorial koncentruje się na obsłudze kształtów.

## Krok 1: Utwórz nowy projekt konsolowy i dodaj Aspose.Words

Otwórz terminal lub wiersz poleceń Visual Studio i uruchom:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Tworzy to nową aplikację konsolową o nazwie **WordShapeDemo** i dodaje pakiet NuGet `Aspose.Words`, który zawiera klasy `Document` i `DocumentBuilder` używane do manipulacji plikami Word.

## Krok 2: Załaduj lub utwórz dokument

Pierwsza operacja przy pracy z **group shapes in Word** polega na uzyskaniu obiektu `Document`. Możesz załadować istniejący plik DOCX lub rozpocząć od pustego dokumentu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

Klasa `Document` reprezentuje cały plik Word. Załadowanie pliku daje gotowe płótno do wstawiania kształtów.

## Krok 3: Rozpocznij grupę kształtów

*Group shape* pozwala traktować kilka niezależnych kształtów jako jedną jednostkę — idealne do ich jednoczesnego przemieszczania lub zmiany rozmiaru. Aby rozpocząć grupę, wywołaj `StartGroupShape()` na obiekcie `DocumentBuilder`.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

Wywołanie `StartGroupShape` informuje Aspose.Words, że każde kolejne wstawienie kształtu należy do tej samej logicznej grupy, aż do wywołania `EndGroupShape`.

## Krok 4: Jak dodać prostokąt w Wordzie

Teraz, gdy grupa jest otwarta, wstaw prostokąt. Metoda `InsertShape` przyjmuje wyliczenie `ShapeType`, a następnie szerokość i wysokość (w punktach).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Prostokąt staje się pierwszym członkiem grupy. W razie potrzeby możesz później dostosować jego wypełnienie, obrys lub tekst.

## Krok 5: Jak dodać elipsę w Wordzie

Następnie dodaj elipsę (koło, gdy szerokość równa się wysokości). To pokazuje **how to add ellipse** przy użyciu tego samego buildera.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Oba kształty dzielą teraz tę samą przestrzeń współrzędnych wewnątrz grupy, co ułatwia ich wizualne wyrównanie.

## Krok 6: Zamknij definicję grupy kształtów

Gdy dodasz wszystkie pożądane elementy, zamknij grupę. To finalizuje kolekcję kształtów, dzięki czemu Word traktuje je jako jeden obiekt.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

W tym momencie dokument zawiera pojedynczy zgrupowany kształt składający się z prostokąta i elipsy.

## Krok 7: Zapisz zmodyfikowany dokument

Na koniec zapisz zmiany na dysku. Możesz nadpisać oryginalny plik lub utworzyć nowy.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

Uruchomienie programu generuje `output.docx`. Otwórz plik w Microsoft Word, zaznacz kształt i zobaczysz, że prostokąt i elipsa poruszają się razem — dowód, że operacja **group shapes in Word** zakończyła się sukcesem.

### Oczekiwany rezultat

* Plik Word zawiera pojedynczy obiekt grupowy.  
* Wybranie grupy pozwala przeciągać, zmieniać rozmiar lub obracać jednocześnie prostokąt i elipsę.  
* Nie jest wymagana ręczna interakcja z Wordem; wszystko odbywa się za pomocą kodu C#.

![Grouped shapes in Word document](grouped-shapes.png "Screenshot of a Word document showing a grouped rectangle and ellipse shape")

*Tekst alternatywny obrazu: “Screenshot of a Word document showing a grouped rectangle and ellipse shape”* (spełnia wymóg tekstu alternatywnego obrazu).

## Dlaczego grupowanie kształtów ma znaczenie

Grupowanie kształtów to nie tylko wygoda wizualna. Umożliwia ono:

* **Utrzymanie spójności układu** – przemieszczanie grupy zachowuje względne pozycje.  
* **Zastosowanie transformacji jednorazowo** – obracanie lub skalowanie całej grupy zamiast każdego kształtu osobno.  
* **Uproszczenie dalszego przetwarzania** – gdy inne narzędzia odczytują DOCX, widzą pojedynczy kształt złożony, co zmniejsza złożoność.

Jeśli kiedykolwiek będziesz musiał dodać więcej kształtów (np. linię lub pole tekstowe) do tej samej jednostki logicznej, wystarczy wywołać `InsertShape` ponownie przed `EndGroupShape`.

## Typowe warianty i przypadki brzegowe

| Sytuacja | Jak sobie radzić |
|-----------|-----------------|
| **Różne jednostki** – masz wymiary w centymetrach | Przelicz centymetry na punkty (`1 cm ≈ 28.35 pt`) przed wywołaniem `InsertShape`. |
| **Dodawanie etykiety tekstowej** – chcesz podpis wewnątrz grupy | Wstaw `ShapeType.TextBox` po prostokącie i elipsie, a następnie ustaw jego właściwość `Text`. |
| **Zastosowanie koloru wypełnienia** – potrzebujesz niebieskiego prostokąta | Po `InsertShape` pobierz ostatni kształt przez `builder.CurrentParagraph.Runs[0].Font` i ustaw `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Użycie innego formatu dokumentu** – celujesz w `.doc` zamiast `.docx` | Ten sam kod działa; wystarczy zmienić rozszerzenie pliku przy wywołaniu `Save`. Aspose.Words automatycznie obsługuje format. |

## Porady profesjonalne

* **Ponowne użycie buildera** – możesz rozpoczynać i kończyć wiele grup w tym samym dokumencie; po `EndGroupShape` po prostu wywołaj ponownie `StartGroupShape`.  
* **Wydajność** – wsadowe wstawianie kształtów w jednym bloku `StartGroupShape/EndGroupShape` jest szybsze niż wstawianie kształtów pojedynczo poza grupą.  
* **Licencjonowanie** – licencja ewaluacyjna dodaje znak wodny na pierwszej stronie. Zainstaluj właściwą licencję, aby usunąć go w środowiskach produkcyjnych.

## Zakończenie

Teraz wiesz, jak **group shapes in Word** przy użyciu C#, jak **add rectangle**, jak **add ellipse** oraz jak **insert rectangle shape Word** w dokumentach przy pomocy Aspose.Words. Kompletny, działający przykład demonstruje każdy krok od konfiguracji projektu po zapisanie finalnego pliku.

Od tego momentu możesz eksplorować dodatkowe typy kształtów, stosować stylizację lub łączyć grupowane kształty z tabelami i obrazami, aby tworzyć zaawansowane, programowo generowane dokumenty.

---

**Następne kroki**

* Dowiedz się, jak **obracać grupowane kształty**: użyj `Shape.RotationAngle` po zamknięciu grupy.  
* Zbadaj **dostosowywanie wypełnienia i konturu** dla prostokątów i elips.  
* Zintegruj tę logikę z API ASP.NET Core, aby generować raporty na żądanie.  

Miłego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz grupowy kształt w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Wstaw kształty w dokumentach Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Utwórz prostokątny kształt w Word – Pełny przewodnik Aspose.Words](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}