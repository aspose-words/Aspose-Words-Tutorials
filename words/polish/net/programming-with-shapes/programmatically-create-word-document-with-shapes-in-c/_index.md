---
category: general
date: 2026-11-22
description: Programowo tworzyć dokument Word w C# i wstawiać prostokątny kształt,
  wstawiać wiele kształtów oraz zapisywać kształty w Wordzie przy użyciu Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: pl
lastmod: 2026-11-22
og_description: Programowo tworzyć dokument Word w C# poprzez wstawianie prostokątnego
  kształtu, wstawianie wielu kształtów i zapisywanie kształtów do Worda przy użyciu
  Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Programowo twórz dokument Word z kształtami w C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Programowo tworzyć dokument Word z kształtami w C#
url: /pl/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programowo tworzyć dokument Word z kształtami w C#

Jeśli potrzebujesz **programowo tworzyć dokument Word**, który zawiera własne grafiki, ten przewodnik pokaże Ci, jak to zrobić przy użyciu Aspose.Words for .NET. Nauczysz się wstawiać kształt prostokąta, dodawać dodatkowe kształty, grupować je oraz ostatecznie zapisywać kształty do Worda — wszystko w kilku linijkach C#.

Tworzenie pliku Word z grafiką nie wymaga już ręcznej edycji ani skryptów makr. Po zakończeniu tego samouczka będziesz mieć wielokrotnego użytku metodę, która generuje plik `.docx` zawierający prostokąt i elipsę zgrupowane razem, gotowe do dalszego przetwarzania lub raportowania.

## Czego będziesz potrzebować

- .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+)
- Aspose.Words for .NET (pakiet NuGet `Aspose.Words`)
- IDE, np. Visual Studio 2022 (dowolny edytor, który potrafi kompilować C#)

> **Wskazówka:** Zainstaluj pakiet przy użyciu polecenia CLI `dotnet add package Aspose.Words` przed rozpoczęciem kodowania.

## Programowo tworzyć dokument Word – przegląd

Cały przepływ składa się z trzech logicznych faz:

1. **Initialize** a new `Document` and a `DocumentBuilder`.  
2. **Insert multiple shapes** (prostokąt i elipsa) i umieść je wewnątrz `GroupShape`.  
3. **Write shapes to Word** poprzez zapisanie `Document` do pliku `.docx`.

Każda faza jest zamknięta w dedykowanym kroku poniżej, więc możesz skopiować‑wkleić kod bezpośrednio do swojego projektu.

![Programowo tworzyć dokument Word z grupowanymi kształtami](grouped-shapes.png){: .align-center alt="Programowo tworzyć dokument Word z grupowanymi kształtami"}

## Krok 1: Zainicjalizuj dokument i builder

Klasa `Document` reprezentuje cały plik Word, natomiast `DocumentBuilder` udostępnia płynne API do dodawania treści.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Dlaczego to ważne:* Utworzenie najpierw `Document` daje czyste płótno. `DocumentBuilder` śledzi bieżący punkt wstawiania, co jest niezbędne, gdy później dołączasz kształty do hierarchii akapitu.

## Krok 2: Wstaw kontener grupowego kształtu

`GroupShape` pozwala traktować kilka pojedynczych kształtów jako jedną jednostkę. Jest to przydatne, gdy chcesz przesuwać lub zmieniać ich rozmiar razem.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Wyjaśnienie:* `InsertGroupShape` wstawia pusty kontener i automatycznie ustawia go jako bieżący kształt. Wszystkie kolejne wstawienia kształtów będą dodawane do tego kontenera, dopóki nie zamkniesz grupy.

## Wstaw kształt prostokąta

Teraz dodajemy pierwszą grafikę — prostokąt. Spełnia to wymaganie **insert rectangle shape**.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Prostokąt dziedziczy kontekst formatowania grupy, więc pojawia się wewnątrz `GroupShape`. Możesz także później ustawić kolor linii, wypełnienie lub tekst, jeśli zajdzie taka potrzeba.

## Wstaw wiele kształtów

Aby zademonstrować możliwość **insert multiple shapes**, dodajemy elipsę zaraz po prostokącie. Możesz dalej dodawać dowolną liczbę kształtów (np. trójkąty, gwiazdy) przed zamknięciem grupy.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

W tym momencie grupa zawiera dwa odrębne kształty: prostokąt i elipsę. Ponieważ mają tego samego rodzica, możesz przesuwać je jako jedną jednostkę.

## Krok 3: Dołącz grupowy kształt do hierarchii akapitu

Dokumenty Word przechowują zawartość w drzewie akapitów. Aby grupa była widoczna w ostatecznym pliku, musimy dołączyć ją do bieżącego akapitu.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Dlaczego ten krok jest wymagany:* Bez dołączenia grupy do akapitu kształty istnieją tylko w pamięci i są pomijane przy zapisie dokumentu.

## Krok 4: Zapisz dokument — zapisz kształty do Worda

Na koniec zapisujemy w‑pamięci `Document` na dysk. Spełnia to cel **write shapes to word**.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Gdy otworzysz `GroupShape.docx` w programie Microsoft Word, zobaczysz prostokąt i elipsę zgrupowane razem, dokładnie tak, jak wstawił je kod.

### Oczekiwany wynik

- Plik o nazwie **GroupShape.docx** znajdujący się w folderze wyjściowym projektu.
- W pliku Word: pojedynczy akapit zawierający zgrupowany prostokąt (100 pt × 50 pt) i elipsę (80 pt × 40 pt). Wybranie dowolnego kształtu zaznacza całą grupę.

## Obsługa typowych przypadków brzegowych

| Situation | Recommendation |
|-----------|----------------|
| **Inna rozdzielczość DPI lub rozmiar strony** | Ustaw explicite `builder.PageSetup.PaperSize` przed wstawianiem kształtów, aby uniknąć nieoczekiwanego skalowania. |
| **Potrzeba precyzyjnego pozycjonowania kształtów** | Użyj `builder.MoveTo`, aby przenieść punkt wstawiania, a następnie ustaw właściwości `groupShape.Left` i `groupShape.Top` (wartości w punktach). |

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz dokument Word — wstaw prostokąt i cień w C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Utwórz dokument Word programowo i grupuj kształty w C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programowo utwórz dokument Word z grupowym kształtem](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}