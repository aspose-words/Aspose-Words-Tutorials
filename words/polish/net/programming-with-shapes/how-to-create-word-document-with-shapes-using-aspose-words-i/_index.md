---
category: general
date: 2026-09-11
description: Dowiedz się, jak utworzyć dokument Word, dodać kształt prostokąta i ustawić
  wymiary kształtu za pomocą Aspose.Words. Przewodnik krok po kroku w C# dotyczący
  precyzyjnego określania rozmiarów kształtu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: pl
lastmod: 2026-09-11
og_description: Utwórz dokument Word przy użyciu Aspose.Words w C#. Ten przewodnik
  pokazuje, jak dodać kształt prostokąta, ustawić rozmiar kształtu i zarządzać wymiarami
  kształtu programowo.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Tworzenie dokumentu Word z kształtami – samouczek Aspose.Words C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Jak utworzyć dokument Word z kształtami przy użyciu Aspose.Words w C#
url: /pl/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć dokument Word z kształtami przy użyciu Aspose.Words w C#

Jeśli potrzebujesz **utworzyć dokument Word**, który zawiera własne grafiki, możesz zrobić to w pełni w kodzie. Ten tutorial przeprowadzi Cię przez tworzenie pliku Word, dodawanie prostokątnego kształtu oraz kontrolowanie każdego wymiaru tego kształtu. Po zakończeniu będziesz mieć gotowy fragment kodu, który możesz wstawić do dowolnego projektu .NET.

Nauczysz się, jak **dodać prostokątny kształt**, **ustawić rozmiar kształtu** oraz **ustawić wymiary kształtu** wewnątrz grupowanego kontenera. Przykład używa Aspose.Words 13.9, ale koncepcje mają zastosowanie także do późniejszych wersji. Nie wymagana jest wcześniejsza znajomość API rysowania Aspose — wystarczy podstawowa wiedza o C#.

## Wymagania wstępne

- .NET 6.0 lub nowszy zainstalowany  
- Pakiet NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- IDE, np. Visual Studio 2022 (dowolny edytor obsługujący C#)  

Posiadanie tych narzędzi pozwala uruchomić kod od razu, bez dodatkowej konfiguracji.

## Krok 1: Inicjalizacja dokumentu i buildera – podstawy tworzenia dokumentu Word

Pierwszą operacją jest utworzenie obiektu `Document` oraz `DocumentBuilder`. `Document` reprezentuje sam plik, natomiast `DocumentBuilder` udostępnia płynne API do wstawiania treści.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Dlaczego to ważne:**  
Utworzenie dokumentu na początku daje czyste płótno. Kursor buildera zaczyna się w pierwszym paragrafie, czyli w miejscu, w którym później **utworzymy kształty w Word**.

## Krok 2: Zbudowanie GroupShape, aby pomieścić wiele grafik

`GroupShape` działa jak kontener; możesz przesuwać, obracać lub zmieniać rozmiar całej grupy jako jednej jednostki. Tutaj definiujemy szerokość i wysokość kontenera w punktach (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Dlaczego to ważne:**  
Grupowanie kształtów upraszcza zarządzanie układem. Jeśli później dodasz kolejne kształty (np. koła lub pola tekstowe), odziedziczą one pozycję i skalowanie grupy.

## Krok 3: Utworzenie prostokątnego kształtu i skonfigurowanie jego wymiarów

Teraz dodajemy rzeczywisty prostokąt. Konstruktor `Shape` wymaga referencji do dokumentu oraz typu kształtu. Po utworzeniu wyraźnie **ustawiamy rozmiar kształtu** oraz **ustawiamy wymiary kształtu**.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Dlaczego to ważne:**  
Określenie szerokości, wysokości, lewego i górnego położenia daje kontrolę piksel‑perfekcyjną nad kształtem. Jest to niezbędne, gdy dokument musi odpowiadać specyfikacji projektu lub wydrukowanej formularzowi.

## Krok 4: Złożenie grupy przez dołączenie prostokąta

Dołączenie prostokąta do `GroupShape` czyni go węzłem potomnym. Możesz dodać dowolną liczbę dzieci przed wstawieniem grupy do dokumentu.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Wskazówka:** Jeśli planujesz dodać drugi kształt, utwórz go w ten sam sposób i wywołaj `group.AppendChild(secondShape)`. Wszystkie dzieci korzystają z tego samego systemu współrzędnych grupy.

## Krok 5: Wstawienie grupowanego kształtu do dokumentu i zapis

Po pełnym zbudowaniu grupy umieszczamy ją w bieżącym paragrafie. Właściwość `CurrentParagraph` buildera zapewnia bezpośredni dostęp do drzewa węzłów.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Dlaczego to ważne:**  
Dołączenie grupy do paragrafu zapewnia, że kształt pojawi się w linii z przepływem tekstu. Zapisanie dokumentu finalizuje operację **utworzenia dokumentu Word**.

## Typowe warianty i przypadki brzegowe

| Scenariusz | Dostosowanie |
|------------|--------------|
| **Inna orientacja strony** | Ustaw `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` przed utworzeniem grupy. |
| **Wiele prostokątów** | Utwórz dodatkowe obiekty `Shape` i wywołaj `group.AppendChild(newRect)` dla każdego z nich. |
| **Dynamiczny rozmiar w zależności od zawartości** | Oblicz szerokość/wysokość na podstawie wymiarów obrazu lub metryk tekstu, a następnie przypisz do `rectangle.Width` / `rectangle.Height`. |
| **Eksport do PDF** | Po `doc.Save` wywołaj `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **Kompatybilność ze starszymi wersjami Word** | Zapisz używając `SaveFormat.Doc` zamiast `Docx` dla kompatybilności z Word 97‑2003. |

Te warianty pokazują, jak tę samą podstawową logikę można dostosować do wielu rzeczywistych wymagań.

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się kompletny program, który możesz skopiować, wkleić i uruchomić. Zawiera wszystkie dyrektywy `using`, punkt wejścia `Main` oraz komentarze wyjaśniające każdy wiersz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Oczekiwany wynik:**  
Po otwarciu *GroupShape.docx* pierwsza strona pokaże prostokąt z szarym obramowaniem, umieszczony 50 pt od lewego/górnego marginesu, a sam prostokąt będzie odsunięty o 10 pt wewnątrz grupy. Wymiary będą odpowiadały wartościom ustawionym w kodzie.

## Podsumowanie

Teraz wiesz, jak **utworzyć dokument Word**, **dodać prostokątny kształt** oraz precyzyjnie **ustawić rozmiar kształtu** i **ustawić wymiary kształtu** przy użyciu Aspose.Words. Podejście z grupowanym kształtem utrzymuje układ elastycznym i gotowym na przyszłe rozszerzenia, takie jak dodatkowe grafiki czy pola tekstowe.

Następnie odkryj powiązane tematy, takie jak **tworzenie kształtów w Word** dla kół, strzałek lub własnych ścieżek SVG oraz dowiedz się, jak **ustawić kolor wypełnienia kształtu** lub **zastosować obrót**. Eksperymentuj z różnymi jednostkami, aby zobaczyć, jak Word renderuje punkty versus centymetry, i zintegrować kod w większych pipeline'ach generowania dokumentów.

Miłego kodowania i śmiało dostosowuj ten wzorzec do wszelkich scenariuszy automatycznego raportowania lub wypełniania formularzy!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu oraz wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i poznać alternatywne podejścia implementacyjne w własnych projektach.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}