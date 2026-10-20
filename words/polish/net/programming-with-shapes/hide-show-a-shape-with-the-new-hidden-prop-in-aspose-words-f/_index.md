---
category: general
date: 2026-10-20
description: Ukryj/pokaż kształt za pomocą nowej właściwości `Hidden` w Aspose.Words
  dla C#. Dowiedz się, jak przełączać widoczność kształtu, obsługiwać przypadki brzegowe
  i zapisać wynik.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: pl
lastmod: 2026-10-20
og_description: Ukryj/pokaż kształt za pomocą nowej właściwości `Hidden` w Aspose.Words
  dla C#. Opanuj przełączanie widoczności kształtu i unikaj typowych pułapek.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Ukryj/Pokaż kształt za pomocą nowej właściwości `Hidden` w Aspose.Words
  (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Ukryj/pokaż kształt za pomocą nowej właściwości `Hidden` w Aspose.Words dla
  C#
url: /pl/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ukryj/Pokaż kształt za pomocą nowej `Hidden` prop w Aspose.Words dla C#

Jeśli potrzebujesz **ukryć/pokazać kształt za pomocą nowej `Hidden` prop** w dokumencie Word, ten przewodnik pokaże Ci dokładnie, jak to zrobić przy użyciu Aspose.Words dla .NET. Niezależnie od tego, czy generujesz raporty, tworzysz szablony, czy oczyszczasz zaimportowane dokumenty, programowe sterowanie widocznością kształtów oszczędza Ci ręcznej edycji.

W tym samouczku nauczysz się, jak załadować dokument, zlokalizować kształt, przełączyć właściwość `Hidden` i zapisać zmodyfikowany plik. Kroki obejmują także typowe wariacje, takie jak obsługa wielu kształtów oraz radzenie sobie z grafiką wstawioną w linii i pływającą.

## Wymagania wstępne

* .NET 6.0 (lub nowszy) zainstalowany – Aspose.Words obsługuje .NET Standard 2.0 i .NET Core.
* Licencjonowaną kopię **Aspose.Words for .NET** (bezpłatna wersja próbna działa do eksploracji).
* IDE, takie jak Visual Studio 2022 lub Visual Studio Code.
* Dokument Word (`input.docx`) zawierający przynajmniej jeden kształt (np. obraz, SmartArt lub płótno rysunkowe).

## Krok 1: Załaduj dokument Word

Pierwszą operacją jest utworzenie obiektu `Document`, który reprezentuje plik .docx na dysku.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Dlaczego ten krok jest ważny*: `Document` jest punktem wejścia dla wszystkich operacji Aspose.Words. Załadowanie pliku do pamięci daje pełny dostęp do jego drzewa węzłów, w tym kształtów.

## Krok 2: Pobierz docelowy kształt

Aby przełączyć widoczność, musisz uzyskać referencję do węzła kształtu. Poniższy przykład pobiera pierwszy kształt w dokumencie, ale możesz dostosować logikę, aby znajdować kształty według nazwy, typu lub indeksu.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*Dlaczego ten krok jest ważny*: `GetChild` z parametrem `true` wykonuje głębokie wyszukiwanie, zapewniając, że znajdziesz kształty nawet wtedy, gdy są zagnieżdżone w tabelach lub nagłówkach. Sprawdzanie pod kątem `null` zapobiega `NullReferenceException`, gdy dokument nie zawiera kształtów.

## Krok 3: Ukryj kształt za pomocą właściwości `Hidden`

Aspose.Words wprowadziło właściwość `Hidden`, aby kontrolować, czy kształt jest renderowany lub drukowany. Ustawienie jej na `true` ukrywa kształt; ustawienie na `false` ponownie go wyświetla.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

Jeśli potrzebujesz **pokazać** wcześniej ukryty kształt, po prostu przypisz `false`:

```csharp
// Show the shape again
shape.Hidden = false;
```

*Dlaczego ten krok jest ważny*: Właściwość `Hidden` działa zarówno dla kształtów pływających, jak i wstawionych w linii, i integruje się z natywnym formatowaniem „Hidden” w Wordzie. To podejście jest bardziej niezawodne niż usuwanie kształtu, ponieważ węzeł pozostaje w drzewie dokumentu, zachowując układ i odwołania.

## Krok 4: Zapisz zmodyfikowany dokument

Po dostosowaniu widoczności, zapisz zmiany do nowego pliku (lub nadpisz oryginał, jeśli chcesz).

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*Dlaczego ten krok jest ważny*: `Save` serializuje drzewo węzłów w pamięci do pakietu .docx, który Word może otworzyć. Flaga ukrycia jest zachowywana, więc otwarcie pliku w Microsoft Word wyświetli kształt zgodnie z ustawieniem `Hidden`.

## Pełny, gotowy do uruchomienia przykład

Połączenie wszystkich kroków daje Ci samodzielny program, który możesz skopiować, skompilować i uruchomić.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**Oczekiwany wynik** po uruchomieniu programu:

```
Document saved. Shape hidden = True
```

Otwarcie `ShapeHidden.docx` w Microsoft Word pokazuje dokument bez docelowego kształtu. Jeśli przed zapisem ustawisz `shape.Hidden = false;`, kształt pojawi się ponownie.

## Obsługa wielu kształtów

Powyższy przykład działa dla jednego kształtu. Dokumenty w rzeczywistym świecie często zawierają wiele grafik. Użyj pętli, aby ukryć lub pokazać wszystkie kształty spełniające warunek (np. określoną nazwę lub typ).

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Wskazówka*: Filtrowanie po `ShapeType` zapobiega przypadkowemu ukrywaniu elementów dekoracyjnych, takich jak pola tekstowe czy SmartArt.

## Przypadki brzegowe i najlepsze praktyki

| Sytuacja | Zalecane postępowanie |
|-----------|----------------------|
| **Kształt znajduje się w nagłówku/stopce** | Najpierw pobierz węzeł nagłówka/stopki, a następnie wywołaj `GetChild(NodeType.Shape, …)` na tym poddokumencie. |
| **Dokument nie zawiera kształtów** | Zawsze sprawdzaj `null` po `GetChild` lub zweryfikuj `doc.GetChildNodes(NodeType.Shape, true).Count`. |
| **Musisz zachować flagę ukrycia w różnych wersjach Worda** | Właściwość `Hidden` jest przechowywana w XML kształtu jako `<w:hidden/>`, co jest obsługiwane przez Word 2007 i nowsze. |
| **Wydajność przy dużych dokumentach** | Użyj `doc.GetChildNodes(NodeType.Shape, true)` raz i ponownie wykorzystaj kolekcję zamiast wielokrotnego wywoływania `GetChild`. |

## Porada pro: Połącz `Hidden` z `WrapType`

Gdy kształt jest ukryty, Word nadal rezerwuje miejsce, które by zajmował, chyba że zmienisz także jego zachowanie otaczania. Ustawienie `WrapType = WrapType.None` usuwa obszar zastępczy.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

To zapewnia, że układ zwija się tak, jakby kształt nigdy nie istniał, co jest przydatne przy generowaniu czystych raportów.

## Zakończenie

Teraz wiesz, jak **ukrywać/pokazywać kształt za pomocą nowej właściwości `Hidden`** przy użyciu Aspose.Words dla C#. Rozwiązanie obejmuje ładowanie dokumentu, znajdowanie kształtu, przełączanie właściwości `Hidden` oraz zachowywanie zmiany. Stosując wskazówki najlepszych praktyk — sprawdzanie `null`, obsługę wielu kształtów i dostosowywanie ustawień otaczania — możesz niezawodnie kontrolować widoczność kształtów w dowolnym scenariuszu automatyzacji Worda.

Gotowy, aby odkrywać dalej? Rozważ następujące kolejne kroki:

* **Ukryj/Pokaż wiele kształtów** w oparciu o niestandardowe metadane (używa techniki „programowego ukrywania kształtu”).
* **Połącz `Hidden` z treścią warunkową** przy użyciu pól Aspose.Words do dynamicznego generowania raportów.
* **Zbadaj inne właściwości węzłów**, takie jak `Visible` dla obiektów wykresów lub `IsDeleted` dla kontroli na poziomie akapitu.

Miłego kodowania i ciesz się precyzyjną kontrolą, jaką Aspose.Words zapewnia w zakresie widoczności kształtów w dokumentach Word!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [jak ukryć kształt w Wordzie przy użyciu C# – przewodnik krok po kroku](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [Jak ukryć kształt w Wordzie przy użyciu C# – przewodnik krok po kroku](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Utwórz pusty dokument Word z ukrytym eliptycznym kształtem – pełny przewodnik C#](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}