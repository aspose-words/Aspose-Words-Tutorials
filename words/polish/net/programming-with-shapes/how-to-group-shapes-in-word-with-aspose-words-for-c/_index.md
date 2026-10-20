---
category: general
date: 2026-09-21
description: Dowiedz się, jak grupować kształty w programie Word przy użyciu Aspose.Words
  dla C#. Ten przewodnik krok po kroku obejmuje tworzenie, pozycjonowanie i zapisywanie
  grupowanych kształtów.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: pl
lastmod: 2026-09-21
og_description: Grupuj kształty w programie Word przy użyciu Aspose.Words dla C#.
  Skorzystaj z tego zwięzłego samouczka, aby programowo tworzyć, pozycjonować i zapisywać
  grupowane kształty.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Grupowanie kształtów w Wordzie przy użyciu Aspose.Words – kompletny przewodnik
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Jak grupować kształty w Wordzie przy użyciu Aspose.Words dla C#
url: /pl/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak grupować kształty w Wordzie przy użyciu Aspose.Words dla C#

Jeśli potrzebujesz **grupować kształty w Wordzie** programowo, Aspose.Words umożliwia to w prosty sposób. Ten samouczek pokazuje, jak utworzyć dwa prostokątne kształty, umieścić je obok siebie, połączyć je w `GroupShape` i zapisać wynik jako plik DOCX.

Zobaczysz kompletny, gotowy do uruchomienia przykład, wyjaśnienia, dlaczego każdy krok ma znaczenie, oraz wskazówki dotyczące obsługi typowych przypadków brzegowych, takich jak nakładające się kształty czy dynamiczne rozmiary. Po zakończeniu tego przewodnika będziesz mógł zintegrować grupowanie kształtów w dowolnym projekcie automatyzacji Worda.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* .NET 6.0 (lub nowszy) – Aspose.Words obsługuje .NET Standard 2.0+, .NET Core i .NET Framework.  
* Ważną licencję Aspose.Words for .NET (lub tymczasowy klucz ewaluacyjny) – biblioteka działa bez licencji, ale dodaje znak wodny.  
* Visual Studio 2022 (lub dowolne IDE C#) do kompilacji i uruchomienia przykładu.

Nie są wymagane dodatkowe pakiety NuGet poza `Aspose.Words`.

## Jak grupować kształty w Wordzie przy użyciu Aspose.Words

Sednem rozwiązania jest obiekt **`GroupShape`**, który działa jako kontener dla poszczególnych kształtów. Poniżej dzielimy proces na przejrzyste kroki.

### Krok 1: Utwórz pusty dokument i `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Dlaczego ten krok?*  
`Document` reprezentuje cały plik DOCX, natomiast `DocumentBuilder` udostępnia płynne metody (np. `InsertShape`), które automatycznie umieszczają nowe elementy w bieżącej pozycji kursora.

### Krok 2: Wstaw pierwszy prostokąt

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Wywołanie `InsertShape` dodaje kształt do dokumentu i zwraca obiekt `Shape`, który możesz dalej konfigurować (kolor, obramowanie itp.). Rozmiar podawany jest w punktach (1 pt ≈ 1/72 cala).

### Krok 3: Wstaw drugi prostokąt i przesuń go

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

Ustawienie `Left` pozycjonuje kształt względem marginesu strony. Przesunięcie musi być większe niż szerokość pierwszego kształtu (100 pt), aby uniknąć nakładania się; używamy 120 pt, aby zostawić małą przerwę.

### Krok 4: Utwórz `GroupShape` wystarczająco duży dla obu prostokątów

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` przyjmuje właścielski `Document` oraz wymiary kontenera. Szerokość kontenera powinna przewyższać prawą krawędź najdalszego kształtu; w przeciwnym razie drugi kształt zostanie przycięty.

### Krok 5: Dodaj poszczególne kształty do grupy

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

Dodanie przenosi kształty do wewnętrznej kolekcji grupy. Po tym wywołaniu kształty nie są już niezależnymi obiektami w drzewie dokumentu – należą do grupy.

### Krok 6: Wstaw zgrupowany kształt z powrotem do dokumentu

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` umieszcza cały `GroupShape` w miejscu, w którym aktualnie znajduje się kursor. Jeśli potrzebujesz grupy w konkretnym akapicie, najpierw przesuń builder do tego akapitu.

### Krok 7: Zapisz dokument

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

Powstały plik zawiera dwa prostokąty zachowujące się jako pojedynczy obiekt – możesz je przesuwać, zmieniać rozmiar lub usuwać razem w Microsoft Word.

## Pełny kod źródłowy

Połączenie wszystkich kroków daje samodzielny program:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Oczekiwany wynik:** Otwarcie *GroupedShapes.docx* w Microsoft Word pokazuje dwa prostokąty obok siebie, traktowane jako jeden wybieralny obiekt. Przeciągnięcie grupy przesuwa oba prostokąty jednocześnie.

## Typowe wariacje i przypadki brzegowe

| Sytuacja | Zalecana modyfikacja |
|-----------|------------------------|
| **Więcej niż dwa kształty** | Utwórz dodatkowe obiekty `Shape`, odpowiednio je pozycjonuj i dodaj każdy do tej samej `GroupShape`. |
| **Dynamiczny rozmiar** | Oblicz szerokość/wysokość grupy na podstawie maksymalnych wartości `Right` i `Bottom` kształtów potomnych. |
| **Różne typy kształtów** | `ShapeType.Ellipse`, `ShapeType.Triangle` itp. można wstawiać w ten sam sposób; kontener grupy nie rozróżnia typu. |
| **Obrócone kształty** | Ustaw `shape.Rotation = 45;` przed dodaniem do grupy; obrót zostanie zachowany wewnątrz grupy. |
| **Zapis jako PDF** | Wywołaj `doc.Save("GroupedShapes.pdf");` – grupa zostanie zachowana w renderingu PDF. |

**Pro tip:** Po zgrupowaniu nadal możesz modyfikować poszczególne kształty, odwołując się do `group.GetChildNodes(NodeType.Shape, true)`. Jest to przydatne, gdy trzeba zmienić kolor wypełnienia jednego prostokąta bez rozbijania grupy.

## Jak zweryfikować grupowanie programowo

Jeśli musisz potwierdzić, że kształty zostały prawidłowo zgrupowane (np. w testach jednostkowych), przejrzyj hierarchię węzłów dokumentu:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

Wynik powinien wyglądać tak:

```
Number of groups: 1
Children in first group: 2
```

Potwierdza to, że **grupowanie kształtów w Wordzie** zostało utworzone zgodnie z oczekiwaniami.

## Zakończenie

Teraz wiesz, jak **grupować kształty w Wordzie** przy użyciu Aspose.Words dla C#. Proces polega na tworzeniu poszczególnych kształtów, ich pozycjonowaniu, opakowaniu ich w `GroupShape` i wstawieniu grupy z powrotem do dokumentu. Dzięki pełnemu przykładowi powyżej możesz rozszerzyć technikę na dowolną liczbę kształtów, różne typy, a nawet połączyć ją z polami tekstowymi i obrazami.

Następnie zgłęb tematy pokrewne, takie jak **grupowanie kształtów w Aspose.Words**, **manipulacja kształtami Word w C#** oraz **DocumentBuilder insert shape**, aby poznać bardziej zaawansowane scenariusze automatyzacji dokumentów. Eksperymentuj z dynamicznym rozmiarem, warunkowym grupowaniem i eksportem do PDF, aby w pełni wykorzystać możliwości Aspose.Words.

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu oraz wyjaśnienia krok po kroku, pomagające opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Wstawianie kształtów w dokumentach Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Tworzenie prostokątnego kształtu w Wordzie z Aspose.Words – przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Samouczek cieniowania kształtów Aspose.Words – Dodaj cień do kształtu Word w C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}