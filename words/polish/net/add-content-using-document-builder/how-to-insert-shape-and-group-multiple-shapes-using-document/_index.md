---
category: general
date: 2026-11-15
description: Dowiedz się, jak wstawić kształt w dokumencie Word i grupować wiele kształtów
  przy użyciu Aspose.Words DocumentBuilder. Zawiera przykłady wstawiania prostokątnego
  kształtu oraz wstawiania wielu kształtów.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: pl
lastmod: 2026-11-15
og_description: Jak wstawić kształt w pliku Word przy użyciu Aspose.Words. Ten przewodnik
  obejmuje grupowanie wielu kształtów, wstawianie prostokątnego kształtu oraz efektywne
  dodawanie wielu kształtów.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: Jak wstawić kształt i grupować wiele kształtów za pomocą DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: Jak wstawić kształt i grupować wiele kształtów przy użyciu DocumentBuilder
  w C#
url: /pl/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wstawiać kształt i grupować wiele kształtów przy użyciu DocumentBuilder w C#

Jeśli potrzebujesz wiedzieć **jak wstawiać kształt** do dokumentu Word przy użyciu Aspose.Words, ten przewodnik pokaże Ci dokładne kroki. Dowiesz się także, jak **grupować wiele kształtów**, aby zachowywały się jak pojedynczy obiekt, oraz jak **wstawiać kształt prostokąta** obok innych grafik.

Automatyzacja dokumentów często wymaga dodawania kilku grafik — wykresów, logo, adnotacji — przy jednoczesnym zachowaniu ich porządku. Po zakończeniu tego samouczka będziesz w stanie **wstawiać wiele kształtów**, umieścić je w grupie i zapisać czysty, wielokrotnego użytku układ.

## Wymagania wstępne

* .NET 6.0 lub nowszy zainstalowany  
* Visual Studio 2022 (lub dowolne IDE C#)  
* Licencja Aspose.Words for .NET lub darmowy klucz ewaluacyjny  
* Podstawowa znajomość C# i klasy Aspose.Words `DocumentBuilder`

Nie potrzebujesz **żadnych** innych bibliotek firm trzecich; wszystko, co jest potrzebne, jest częścią Aspose.Words.

## Krok 1: Zainstaluj Aspose.Words za pomocą NuGet

Otwórz swój projekt w Visual Studio i uruchom następujące polecenie w konsoli Package Manager Console:

```powershell
Install-Package Aspose.Words
```

Pakiet zawiera klasy `DocumentBuilder`, `Shape` i `GroupShape` używane w całym tym samouczku.

## Krok 2: Utwórz instancję DocumentBuilder — podstawę dla **jak wstawiać kształt**

Pierwszą praktyczną linią kodu jest utworzenie `DocumentBuilder`. Ten obiekt daje bezpośredni dostęp do drzewa dokumentu, umożliwiając umieszczanie kształtów dokładnie tam, gdzie ich potrzebujesz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Dlaczego to ważne*: `DocumentBuilder` utrzymuje kursor („punkt wstawiania”). Każde kolejne wywołanie `Insert...` używa tego kursora, dlatego później przenosimy go do `GroupShape`, aby wszystkie kształty były razem.

## Krok 3: **Wstaw kształt prostokąta** — pierwsza grafika, którą dodasz

Prostokąt jest powszechnym miejscem wstawiania tabel, obrazów lub adnotacji. Użyj `InsertShape` z `ShapeType.Rectangle` i określ szerokość oraz wysokość w punktach (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Prostokąt pojawia się w bieżącej pozycji kursora. W razie potrzeby możesz później dostosować jego wypełnienie, styl linii lub tekst.

## Krok 4: Wstaw kolejny kształt — elipsę dla urozmaicenia wizualnego

Dodanie więcej niż jednego kształtu demonstruje **wstawianie wielu kształtów**. Elipsa znajdzie się po prostokącie w przepływie dokumentu.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

W tym momencie dokument zawiera dwa niezależne kształty. Jeśli przesuniesz kursor lub dodasz tekst, kształty pozostaną w miejscu, w którym zostały wstawione.

## Krok 5: **Grupuj wiele kształtów**, aby działały jako jedna jednostka

Grupowanie jest niezbędne, gdy musisz przenieść, obrócić lub sformatować kilka grafik razem. Poniższy kod tworzy `GroupShape`, przenosi kursor buildera do środka i ponownie wstawia te same kształty — tym razem stają się dziećmi grupy.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Dlaczego używać grupy?

* **Jednopunktowa transformacja** — obrót lub zmiana rozmiaru całej grupy jednym wywołaniem.  
* **Logiczna organizacja** — drzewo dokumentu Word odzwierciedla grupowanie, co ułatwia późniejsze edycje.  
* **Spójny układ** — przenoszenie grupy zachowuje względne pozycje jej elementów potomnych.

### Dodawanie kolejnych kształtów — rozszerzanie **wstawiania wielu kształtów** wewnątrz grupy

Możesz nadal wywoływać `InsertShape`, gdy kursor pozostaje wewnątrz `GroupShape`. Na przykład, aby dodać trójkąt:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

Każde wywołanie respektuje kontekst grupy, więc trójkąt automatycznie staje się częścią tego samego zestawu grupowego.

## Krok 6: Zapisz dokument i zweryfikuj wynik

Po umieszczeniu wszystkich kształtów, zapisz dokument do pliku `.docx`. Otworzenie pliku w Microsoft Word (lub dowolnym kompatybilnym przeglądarce) powinno pokazać dwa oddzielne kształty, a następnie zestaw grupowy zawierający ten sam prostokąt, elipsę i trójkąt.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Oczekiwany wynik

* **Pierwsze dwa kształty** — prostokąt i elipsa umieszczone niezależnie na stronie.  
* **Blok grupowy** — prostokąt, elipsa i trójkąt, które poruszają się razem po kliknięciu dowolnego z nich w Wordzie.

Możesz przetestować grupowanie, wybierając dowolny kształt wewnątrz grupy; Word podświetli całą kolekcję, potwierdzając, że operacja **grupowania wielu kształtów** zakończyła się sukcesem.

## Typowe pułapki i wskazówki profesjonalne

| Problem | Dlaczego się pojawia | Rozwiązanie |
|-------|----------------|-----|
| Kształty pojawiają się poza zamierzoną stroną | Kursor buildera nie został przeniesiony do `GroupShape` przed wstawieniem. | Zawsze wywołuj `builder.MoveTo(group)` **przed** jakimikolwiek wywołaniami `InsertShape`, które należą do grupy. |
| Grupa znika po zapisaniu | Grupa została wstawiona bez dodania do kolekcji węzłów dokumentu. | Użyj `builder.InsertNode(group)` natychmiast po utworzeniu `GroupShape`. |
| Nieoczekiwany rozmiar z powodu DPI dokumentu | Aspose.Words używa punktów; jeśli myślisz w pikselach, możesz otrzymać niepasujące wymiary. | Konwertuj piksele na punkty (`points = pixels * 72 / 96`) lub pracuj bezpośrednio w punktach. |
| Kształty nakładają się niezamierzenie | Nie ustawiono explicite położenia; Word umieszcza je kolejno. | Ustaw `Shape.Left` i `Shape.Top` po wstawieniu, aby kontrolować dokładne położenie. |

**Wskazówka profesjonalna:** Po grupowaniu możesz pobrać kolekcję `Shapes` grupy (`group.Shapes`), aby iterować, zmieniać nazwy lub zastosować formatowanie zbiorcze.

## Krok 7: Rozszerzenie przykładu — co dalej?

Teraz, gdy znasz **jak wstawiać kształt**, **wstawiać kształt prostokąta** i **grupować wiele kształtów**, możesz eksplorować:

* **Animowanie grupowanych kształtów** — ustaw właściwości obrotu lub odbicia grupy.  
* **Stosowanie stylów** — użyj `Shape.FillColor`, `Shape.LineFormat` lub `Shape.TextBox`, aby dodać etykiety.  
* **Eksport do PDF** — ten sam układ grupowy renderuje się poprawnie po wywołaniu `doc.Save("output.pdf")`.  

Wszystkie te rozszerzenia wykorzystują ten sam przepływ pracy `DocumentBuilder`, utrzymując kod czystym i łatwym do utrzymania.

## Podsumowanie

Ten samouczek pokazał **jak wstawiać kształt** do dokumentu Word przy użyciu Aspose.Words, jak **wstawiać kształt prostokąta** oraz jak **grupować wiele kształtów**, aby zachowywały się jak pojedynczy obiekt. Postępując zgodnie z kodem krok po kroku, możesz niezawodnie **wstawiać wiele kształtów**, organizować je w grupy i programowo tworzyć dokumenty o profesjonalnym poziomie.

Śmiało eksperymentuj z różnymi typami kształtów, kolorami i transformacjami grup. Gdy będziesz gotowy, włącz ten wzorzec do większych rozwiązań raportowania lub szablonowania, aby automatyzować złożone układy dokumentów. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Wstawianie kształtów w dokumentach Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Jak tworzyć i wstawiać elipsy oraz prostokąty wewnątrz grupy kształtów w dokumencie Word przy użyciu Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Jak grupować kształty w dokumencie Word przy użyciu Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}