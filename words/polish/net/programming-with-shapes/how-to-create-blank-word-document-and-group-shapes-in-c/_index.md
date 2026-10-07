---
category: general
date: 2026-10-07
description: Utwórz pusty dokument Word w C# i naucz się dodawać kształt prostokąta,
  wstawiać kształt obrazu oraz grupować wiele kształtów w dynamicznych raportach.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: pl
lastmod: 2026-10-07
og_description: Utwórz pusty dokument Word w C# przy użyciu Aspose.Words. Dowiedz
  się, jak dodać kształt prostokąta, wstawić kształt obrazu oraz grupować wiele kształtów
  w profesjonalnych dokumentach.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Utwórz pusty dokument Word i grupuj kształty w C# – przewodnik krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Jak utworzyć pusty dokument Word i grupować kształty w C#
url: /pl/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć pusty dokument Word i grupować kształty w C#

Jeśli potrzebujesz **utworzyć pusty dokument Word** programowo, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Zobaczysz, jak **dodać kształt prostokąta**, **wstawić kształt obrazu** oraz **zgrupować wiele kształtów**, aby zachowywały się jako jeden obiekt przy **dodawaniu obrazu do Worda** później.

Praca z plikami Worda z poziomu kodu może wydawać się przytłaczająca, ale Aspose.Words upraszcza cały proces. Po zakończeniu tego tutorialu będziesz mieć gotowy fragment C#, który generuje czysty, pusty plik Word zawierający zgrupowany prostokąt i logo. Możesz osadzić wynik w fakturach, raportach lub w dowolnym zautomatyzowanym przepływie dokumentów.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.7+).  
* Ważną licencję Aspose.Words for .NET lub darmowy klucz ewaluacyjny.  
* Plik obrazu (np. `logo.png`) umieszczony w folderze, do którego możesz odwołać się z kodu.  
* Visual Studio 2022 lub dowolne IDE obsługujące C#.

Nie są wymagane dodatkowe pakiety NuGet poza `Aspose.Words`.

## Jak utworzyć pusty dokument Word przy użyciu Aspose.Words

Pierwszym krokiem zawsze jest **utworzyć pusty dokument Word**. Ten obiekt będzie hostował wszystkie kolejne kształty.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` reprezentuje cały plik `.docx`. W tym momencie plik jest pusty, co spełnia wymóg *utworzenia pustego dokumentu Word*.

## Utwórz kontener do grupowania wielu kształtów

Grupowanie kształtów pozwala na ich jednoczesne przesuwanie, obracanie lub skalowanie. Aspose.Words udostępnia klasę `GroupShape` w tym celu.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

Prostokąt `Bounds` określa, gdzie grupa pojawi się na stronie. Umieszczając grupę w pierwszym akapicie, zapewniasz, że **utworzenie pustego dokumentu Word** od razu zawiera wizualny kontener.

## Jak dodać kształt prostokąta wewnątrz grupy

Częstym wymaganiem jest **dodanie kształtu prostokąta** jako tła lub obramowania. Poniższy kod tworzy prostokąt i dodaje go do wcześniej zdefiniowanej grupy.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Ponieważ prostokąt znajduje się wewnątrz `GroupShape`, będzie się przemieszczać razem z innymi kształtami dodanymi później. To jest sedno funkcjonalności **grupowania wielu kształtów**.

## Jak wstawić kształt obrazu wewnątrz grupy

Następnie **wstawisz kształt obrazu** (logo) i umieścisz go obok prostokąta. To demonstruje przepływ **dodawania obrazu do Worda**.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

Metoda `SetImage` odczytuje plik i osadza go bezpośrednio w dokumencie Word, zapewniając, że obraz pozostanie nawet po przeniesieniu pliku źródłowego. To kończy krok **wstawiania kształtu obrazu** i spełnia wymóg **dodania obrazu do Worda**.

## Zapisz dokument

Na koniec zapisz plik na dysku. Zapisany plik zawiera pusty dokument, zgrupowany prostokąt oraz osadzone logo.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

Po otwarciu `GroupShape.docx` w Microsoft Word zobaczysz jedną grupę, która zawiera jasnoszary prostokąt i logo ustawione obok siebie. Zaznaczenie dowolnej części grupy pozwala przesunąć lub zmienić rozmiar całej kolekcji, co potwierdza, że kształty zostały **zgrupowane**.

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się pełny program, który możesz skopiować, wkleić i uruchomić. Zamień `YOUR_DIRECTORY` na ścieżkę absolutną lub względną istniejącą na Twoim komputerze.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Oczekiwany wynik

* Plik o nazwie `GroupShape.docx` znajdujący się w `YOUR_DIRECTORY`.  
* Po otwarciu pliku w Wordzie zobaczysz jedną wizualną grupę zawierającą szary prostokąt po lewej i `logo.png` po prawej.  
* Zaznaczenie dowolnej części wizualnej grupy umożliwia przesunięcie lub zmianę rozmiaru całej kolekcji, potwierdzając, że kształty zostały poprawnie **zgrupowane**.

## Częste pytania i obsługa przypadków brzegowych

| Pytanie | Odpowiedź |
|---|---|
| **Czy mogę dodać więcej niż dwa kształty do tej samej grupy?** | Tak. Wywołaj `group.AppendChild(yourShape)` dla każdego dodatkowego `Shape`. Grupa może zawierać dowolną liczbę obiektów rysunkowych. |
| **Co się stanie, jeśli plik obrazu będzie brakował?** | `SetImage` rzuci `FileNotFoundException`. Umieść wywołanie w bloku try‑catch i zapewnij alternatywę (np. kształt zastępczy). |
| **Czy muszę ustawiać `WrapType` dla kształtów?** | Domyślnie kształty są inline. Jeśli potrzebujesz zachowania pływającego, ustaw `picture.WrapType = WrapType.Inline;` lub inny tryb przed dodaniem do grupy. |
| **Jak rozmiar dokumentu wpływa na granice grupy?** | Prostokąt `Bounds` jest definiowany w punktach (1 pt ≈ 1/72 in). Dostosuj rozmiar, jeśli umieszczasz grupę w innym układzie strony (np. A4 vs. Letter). |
| **Czy mogę ponownie użyć tej samej grupy w innym dokumencie?** | Tak. Sklonuj grupę przy pomocy `GroupShape cloned = (GroupShape)group.Clone(true);` i wstaw ją do innego `Document`. |

## Porady profesjonalistów

* **Używaj tego samego `DocumentBuilder`** do dodawania tekstu przed lub po grupie. Automatycznie respektuje bieżącą pozycję kursora.  
* **Ustaw `Shape.StrokeColor`**, jeśli potrzebujesz widocznego obramowania prostokąta.  
* **Korzystaj z wysokiej rozdzielczości PNG** dla logo, aby uniknąć pikselizacji przy skalowaniu.

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz szczegółowe wyjaśnienia, pomagające opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}