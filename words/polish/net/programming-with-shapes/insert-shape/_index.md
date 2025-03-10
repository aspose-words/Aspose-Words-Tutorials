---
title: Wstaw kształt
linktitle: Wstaw kształt
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak wstawiać i modyfikować kształty w dokumentach programu Word za pomocą pakietu Aspose.Words dla platformy .NET, korzystając z naszego przewodnika krok po kroku.
weight: 10
url: /pl/net/programming-with-shapes/insert-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw kształt

## Wstęp

Jeśli chodzi o tworzenie wizualnie atrakcyjnych i dobrze ustrukturyzowanych dokumentów Word, kształty mogą odgrywać kluczową rolę. Niezależnie od tego, czy dodajesz strzałki, pola, czy nawet złożone niestandardowe kształty, możliwość manipulowania tymi elementami programowo oferuje niezrównaną elastyczność. W tym samouczku zbadamy, jak wstawiać i manipulować kształtami w dokumentach Word za pomocą Aspose.Words dla .NET.

## Wymagania wstępne

Zanim przejdziesz do samouczka, upewnij się, że spełniasz następujące wymagania wstępne:

1.  Aspose.Words dla .NET: Pobierz i zainstaluj najnowszą wersję ze strony[Strona wydań Aspose](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: odpowiednie środowisko programistyczne .NET, np. Visual Studio.
3. Podstawowa wiedza z zakresu języka C#: Znajomość języka programowania C# i podstawowych koncepcji.

## Importuj przestrzenie nazw

Aby rozpocząć, musisz zaimportować niezbędne przestrzenie nazw do swojego projektu C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Krok 1: Skonfiguruj swój projekt

Zanim zaczniesz wstawiać kształty, musisz skonfigurować projekt i dodać bibliotekę Aspose.Words for .NET.

1. Utwórz nowy projekt: Otwórz program Visual Studio i utwórz nowy projekt aplikacji konsolowej C#.
2. Dodaj Aspose.Words dla .NET: Zainstaluj bibliotekę Aspose.Words dla .NET za pomocą Menedżera pakietów NuGet.

```bash
Install-Package Aspose.Words
```

## Krok 2: Zainicjuj dokument

Najpierw musisz utworzyć nowy dokument i kreator dokumentów, który pomoże Ci w jego utworzeniu.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Zainicjuj nowy dokument
Document doc = new Document();

// Zainicjuj DocumentBuilder, aby pomóc w tworzeniu dokumentu
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Wstaw kształt

Teraz wstawmy kształt do dokumentu. Zaczniemy od dodania prostego pola tekstowego.

```csharp
// Wstaw kształt pola tekstowego do dokumentu
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

// Obróć kształt
shape.Rotation = 30.0;
```

tym przykładzie wstawiamy pole tekstowe w pozycji (100, 100) o szerokości i wysokości 50 jednostek każda. Obracamy również kształt o 30 stopni.

## Krok 4: Dodaj inny kształt

Dodajmy kolejny kształt do dokumentu, tym razem nie określając jego położenia.

```csharp
// Dodaj inny kształt pola tekstowego
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

// Obróć kształt
secondShape.Rotation = 30.0;
```

Ten fragment kodu wstawia kolejne pole tekstowe o tych samych wymiarach i obrocie co pierwsze, ale bez określania jego pozycji.

## Krok 5: Zapisz dokument

 Po dodaniu kształtów ostatnim krokiem jest zapisanie dokumentu. Użyjemy`OoxmlSaveOptions` aby określić format zapisu.

```csharp
// Zdefiniuj opcje zapisu zgodnie ze zgodnością
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

// Zapisz dokument
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Wniosek

I masz to! Udało Ci się wstawić i manipulować kształtami w dokumencie Word za pomocą Aspose.Words dla .NET. Ten samouczek obejmował podstawy, ale Aspose.Words oferuje wiele bardziej zaawansowanych funkcji do pracy z kształtami, takich jak niestandardowe style, łączniki i kształty grupowe.

 Aby uzyskać bardziej szczegółowe informacje, odwiedź stronę[Dokumentacja Aspose.Words dla .NET](https://reference.aspose.com/words/net/).

## Najczęściej zadawane pytania

### Jak wstawiać różne typy kształtów?
Możesz zmienić`ShapeType` w`InsertShape` metoda wstawiania różnych typów kształtów, takich jak okręgi, prostokąty i strzałki.

### Czy mogę dodać tekst wewnątrz kształtów?
 Tak, możesz użyć`builder.Write` metoda dodawania tekstu wewnątrz kształtów po ich wstawieniu.

### Czy można stylizować kształty?
 Tak, możesz stylizować kształty, ustawiając właściwości takie jak`FillColor`, `StrokeColor` , I`StrokeWeight`.

### Jak pozycjonować kształty względem innych elementów?
 Użyj`RelativeHorizontalPosition` I`RelativeVerticalPosition` właściwości umożliwiające pozycjonowanie kształtów względem innych elementów dokumentu.

### Czy mogę grupować wiele kształtów?
 Tak, Aspose.Words dla .NET umożliwia grupowanie kształtów za pomocą`GroupShape` klasa.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
