---
"description": "Dowiedz się, jak dodawać kształty grupowe do dokumentów Word za pomocą Aspose.Words dla .NET, korzystając z tego kompleksowego samouczka krok po kroku."
"linktitle": "Dodaj kształt grupy"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Dodaj kształt grupy"
"url": "/pl/net/programming-with-shapes/add-group-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj kształt grupy

## Wstęp

Tworzenie złożonych dokumentów z bogatymi elementami wizualnymi może być czasem zniechęcającym zadaniem, szczególnie w przypadku kształtów grupowych. Ale nie obawiaj się! Aspose.Words dla .NET upraszcza ten proces, czyniąc go dziecinnie prostym. W tym samouczku przeprowadzimy Cię przez kroki dodawania kształtów grupowych do dokumentów Word. Gotowy do działania? Zaczynajmy!

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

1. Aspose.Words dla .NET: Można go pobrać ze strony [Strona wydań Aspose](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: Visual Studio lub inne środowisko IDE zgodne z .NET.
3. Podstawowa znajomość języka C#: Znajomość programowania w języku C# będzie dodatkowym atutem.

## Importuj przestrzenie nazw

Na początek musimy zaimportować niezbędne przestrzenie nazw do naszego projektu. Te przestrzenie nazw zapewniają dostęp do klas i metod wymaganych do manipulowania dokumentami Word za pomocą Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Krok 1: Zainicjuj dokument

Najpierw zainicjujmy nowy dokument Word. Pomyśl o tym jak o stworzeniu pustego płótna, na którym będziemy dodawać nasze kształty grupowe.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

Tutaj, `EnsureMinimum()` dodaje minimalny zestaw węzłów wymaganych dla dokumentu.

## Krok 2: Utwórz obiekt GroupShape

Następnie musimy utworzyć `GroupShape` obiekt. Ten obiekt będzie służył jako pojemnik na inne kształty, pozwalając nam grupować je razem.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Krok 3: Dodaj kształty do grupy kształtów

Teraz dodajmy do naszego projektu pojedyncze kształty. `GroupShape` kontener. Zaczniemy od kształtu obramowania akcentującego, a następnie dodamy kształt przycisku akcji.

### Dodawanie kształtu obramowania akcentującego

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

Ten fragment kodu tworzy kształt obramowania akcentującego o szerokości i wysokości 100 jednostek i dodaje go do `GroupShape`.

### Dodawanie kształtu przycisku akcji

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

Tutaj tworzymy kształt przycisku akcji, umieszczamy go i dodajemy do naszego `GroupShape`.

## Krok 4: Zdefiniuj wymiary kształtu grupy

Aby mieć pewność, że nasze kształty dobrze pasują do grupy, musimy ustalić wymiary `GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

Definiuje szerokość i wysokość `GroupShape` jako 200 jednostek i odpowiednio ustawia rozmiar współrzędnych.

## Krok 5: Wstaw GroupShape do dokumentu

Teraz wstawmy nasze `GroupShape` do dokumentu za pomocą `DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` umożliwia łatwe dodawanie węzłów, w tym kształtów, do dokumentu.

## Krok 6: Zapisz dokument

Na koniec zapisz dokument w wybranym katalogu.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

I masz! Twój dokument z kształtami grupowymi jest gotowy.

## Wniosek

Dodawanie kształtów grupowych do dokumentów Word nie musi być skomplikowanym procesem. Dzięki Aspose.Words dla .NET możesz łatwo tworzyć i manipulować kształtami, dzięki czemu Twoje dokumenty będą bardziej atrakcyjne wizualnie i funkcjonalne. Postępuj zgodnie z krokami opisanymi w tym samouczku, a w mgnieniu oka zostaniesz profesjonalistą!

## Najczęściej zadawane pytania

### Czy mogę dodać więcej niż dwa kształty do GroupShape?
Tak, możesz dodać do pliku dowolną liczbę kształtów. `GroupShape`Po prostu użyj `AppendChild` metodę dla każdego kształtu.

### Czy można stylizować kształty w ramach GroupShape?
Oczywiście! Każdy kształt można stylizować indywidualnie, korzystając z właściwości dostępnych w `Shape` klasa.

### Jak umieścić GroupShape w dokumencie?
Możesz ustawić `GroupShape` ustawiając jego `Left` I `Top` Właściwości.

### Czy mogę dodać tekst do kształtów w GroupShape?
Tak, możesz dodawać tekst do kształtów za pomocą `AppendChild` metoda dodawania `Paragraph` zawierający `Run` węzły z tekstem.

### Czy możliwe jest dynamiczne grupowanie kształtów na podstawie danych wprowadzonych przez użytkownika?
Tak, możesz dynamicznie tworzyć i grupować kształty na podstawie danych wprowadzonych przez użytkownika, odpowiednio dostosowując właściwości i metody.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}