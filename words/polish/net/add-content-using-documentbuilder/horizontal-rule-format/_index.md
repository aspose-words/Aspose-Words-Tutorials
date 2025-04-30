---
"description": "Dowiedz się, jak wstawiać konfigurowalne poziome linie w dokumentach programu Word za pomocą narzędzia Aspose.Words for .NET. Ulepsz automatyzację dokumentów."
"linktitle": "Format linii poziomej w dokumencie Word"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Format linii poziomej w dokumencie Word"
"url": "/pl/net/add-content-using-documentbuilder/horizontal-rule-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Format linii poziomej w dokumencie Word

## Wstęp

W dziedzinie rozwoju .NET manipulowanie i formatowanie dokumentów Word programowo może być zniechęcającym zadaniem. Na szczęście Aspose.Words dla .NET zapewnia solidne rozwiązanie, umożliwiając programistom łatwą automatyzację tworzenia, edycji i zarządzania dokumentami. Ten artykuł zagłębia się w jedną z podstawowych funkcji: wstawianie poziomych linii do dokumentów Word. Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero zaczynasz pracę z Aspose.Words, opanowanie tej możliwości usprawni proces generowania dokumentów.

## Wymagania wstępne

Zanim zaczniesz wdrażać reguły poziome za pomocą Aspose.Words dla platformy .NET, upewnij się, że spełnione są następujące wymagania wstępne:

- Visual Studio: Zainstaluj środowisko IDE Visual Studio do tworzenia oprogramowania .NET.
- Aspose.Words dla .NET: Pobierz i zainstaluj Aspose.Words dla .NET z [Tutaj](https://releases.aspose.com/words/net/).
- Podstawowa wiedza o języku C#: Znajomość podstaw języka programowania C#.
- Klasa DocumentBuilder: zrozumienie `DocumentBuilder` klasa w Aspose.Words do manipulacji dokumentami.

## Importuj przestrzenie nazw

Na początek zaimportuj niezbędne przestrzenie nazw do swojego projektu C#:

```csharp
using Aspose.Words;
using System.Drawing;
```

Te przestrzenie nazw zapewniają dostęp do klas Aspose.Words umożliwiających manipulowanie dokumentami i standardowych klas .NET do obsługi kolorów.

Podzielmy proces dodawania linii poziomej do dokumentu programu Word za pomocą Aspose.Words dla platformy .NET na szczegółowe kroki:

## Krok 1: Zainicjuj DocumentBuilder i ustaw katalog

Najpierw zainicjuj `DocumentBuilder` obiekt i ustaw ścieżkę katalogu, w którym zostanie zapisany dokument.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
DocumentBuilder builder = new DocumentBuilder();
```

## Krok 2: Wstaw poziomą linię

Użyj `InsertHorizontalRule()` metoda `DocumentBuilder` Klasa umożliwiająca dodanie poziomej linii.

```csharp
Shape shape = builder.InsertHorizontalRule();
```

## Krok 3: Dostosuj format linii poziomej

Uzyskaj dostęp do `HorizontalRuleFormat` Właściwość wstawionego kształtu umożliwiająca dostosowanie wyglądu linii poziomej.

```csharp
HorizontalRuleFormat horizontalRuleFormat = shape.HorizontalRuleFormat;
horizontalRuleFormat.Alignment = HorizontalRuleAlignment.Center;
horizontalRuleFormat.WidthPercent = 70;
horizontalRuleFormat.Height = 3;
horizontalRuleFormat.Color = Color.Blue;
horizontalRuleFormat.NoShade = true;
```

- Wyrównanie: Określa wyrównanie linii poziomej (`HorizontalRuleAlignment.Center` w tym przykładzie).
- WidthPercent: Ustawia szerokość linii poziomej jako procent szerokości strony (w tym przykładzie 70%).
- Wysokość: Określa wysokość linii poziomej w punktach (w tym przykładzie 3 punkty).
- Kolor: Ustawia kolor linii poziomej (`Color.Blue` w tym przykładzie).
- NoShade: Określa, czy linia pozioma powinna mieć cień (`true` w tym przykładzie).

## Krok 4: Zapisz dokument

Na koniec zapisz zmodyfikowany dokument za pomocą `Save` metoda `Document` obiekt.

```csharp
builder.Document.Save(dataDir + "AddContentUsingDocumentBuilder.HorizontalRuleFormat.docx");
```

## Wniosek

Opanowanie wstawiania poziomych linii w dokumentach Word przy użyciu Aspose.Words dla .NET zwiększa możliwości automatyzacji dokumentów. Wykorzystując elastyczność i moc Aspose.Words, deweloperzy mogą usprawnić procesy generowania i formatowania dokumentów.

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla .NET?
Aspose.Words for .NET to zaawansowana biblioteka umożliwiająca programową pracę z dokumentami Word w aplikacjach .NET.

### Jak mogę pobrać Aspose.Words dla platformy .NET?
Możesz pobrać Aspose.Words dla .NET z [Tutaj](https://releases.aspose.com/words/net/).

### Czy mogę dostosować wygląd linii poziomych w Aspose.Words?
Tak, możesz dostosować różne aspekty, takie jak wyrównanie, szerokość, wysokość, kolor i cieniowanie linii poziomych, korzystając z Aspose.Words.

### Czy Aspose.Words nadaje się do przetwarzania dokumentów na poziomie korporacyjnym?
Tak, Aspose.Words jest powszechnie używany w środowiskach korporacyjnych ze względu na swoje rozbudowane możliwości manipulowania dokumentami.

### Gdzie mogę uzyskać pomoc dotyczącą Aspose.Words dla .NET?
Aby uzyskać wsparcie i zaangażować się w społeczność, odwiedź stronę [Forum Aspose.Words](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}