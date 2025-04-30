---
"description": "Dowiedz się, jak formatować etykiety danych na wykresach za pomocą Aspose.Words dla .NET dzięki temu przewodnikowi krok po kroku. Ulepszaj swoje dokumenty Word bez wysiłku."
"linktitle": "Formatuj liczbę etykiet danych na wykresie"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Formatuj liczbę etykiet danych na wykresie"
"url": "/pl/net/programming-with-charts/format-number-of-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formatuj liczbę etykiet danych na wykresie

## Wstęp

Tworzenie angażujących i informacyjnych dokumentów często obejmuje dołączanie wykresów z dobrze sformatowanymi etykietami danych. Jeśli jesteś programistą .NET i chcesz ulepszyć swoje dokumenty Worda za pomocą zaawansowanych wykresów, Aspose.Words dla .NET to fantastyczna biblioteka, która Ci w tym pomoże. Ten samouczek przeprowadzi Cię przez proces formatowania etykiet liczbowych na wykresie za pomocą Aspose.Words dla .NET, krok po kroku.

## Wymagania wstępne

Zanim zagłębisz się w kod, musisz spełnić kilka warunków wstępnych:

- Aspose.Words dla .NET: Upewnij się, że masz zainstalowaną bibliotekę Aspose.Words dla .NET. Jeśli jeszcze jej nie zainstalowałeś, możesz [pobierz tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: Powinieneś mieć skonfigurowane środowisko programistyczne .NET. Visual Studio jest wysoce zalecane.
- Podstawowa znajomość języka C#: Znajomość programowania w języku C# jest niezbędna, ponieważ ten samouczek obejmuje pisanie i rozumienie kodu w języku C#.
- Licencja tymczasowa: Aby korzystać z Aspose.Words bez żadnych ograniczeń, możesz uzyskać [licencja tymczasowa](https://purchase.aspose.com/temporary-license/).

Teraz przeanalizujemy krok po kroku proces formatowania etykiet liczbowych na wykresie.

## Importuj przestrzenie nazw

Po pierwsze, musimy zaimportować niezbędne przestrzenie nazw, aby pracować z Aspose.Words dla .NET. Dodaj następujące wiersze na górze pliku C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Krok 1: Skonfiguruj katalog dokumentów

Zanim zaczniesz manipulować dokumentem Word, musisz określić katalog, w którym dokument zostanie zapisany. Jest to niezbędne do późniejszej operacji zapisywania.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Zastępować `"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką do katalogu dokumentów.

## Krok 2: Zainicjuj dokument i DocumentBuilder

Następnym krokiem jest zainicjowanie nowego `Document` i `DocumentBuilder`. Ten `DocumentBuilder` jest klasą pomocniczą umożliwiającą konstruowanie treści dokumentu.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Wstaw wykres do dokumentu

Teraz wstawmy wykres do dokumentu za pomocą `DocumentBuilder`W tym samouczku użyjemy wykresu liniowego jako przykładu.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Tutaj wstawiamy wykres liniowy o określonej szerokości i wysokości i ustawiamy tytuł wykresu.

## Krok 4: Wyczyść domyślną serię i dodaj nową serię

Domyślnie wykres będzie miał kilka wstępnie wygenerowanych serii. Musimy je wyczyścić i dodać własne serie ze szczegółowymi punktami danych.

```csharp
// Usuń domyślnie wygenerowaną serię.
chart.Series.Clear();

// Dodaj nową serię z niestandardowymi punktami danych.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Krok 5: Włącz etykiety danych

Aby wyświetlić etykiety danych na wykresie, musimy je włączyć dla naszych serii.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Krok 6: Formatowanie etykiet danych

Sednem tego samouczka jest formatowanie etykiet danych. Możemy stosować różne formaty liczb do każdej etykiety danych indywidualnie.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Format waluty
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Format daty
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Format procentowy
```

Dodatkowo możesz połączyć format etykiety danych z komórką źródłową. Po połączeniu `NumberFormat` zostanie zresetowany do ogólnego i odziedziczony z komórki źródłowej.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Krok 7: Zapisz dokument

Na koniec zapisz dokument w podanym katalogu.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Spowoduje to zapisanie dokumentu pod określoną nazwą i zachowanie wykresu ze sformatowanymi etykietami danych.

## Wniosek

Formatowanie etykiet danych na wykresie przy użyciu Aspose.Words dla .NET może znacznie poprawić czytelność i profesjonalizm dokumentów Word. Postępując zgodnie z tym przewodnikiem krok po kroku, powinieneś być teraz w stanie utworzyć wykres, dodać serie danych i sformatować etykiety danych zgodnie ze swoimi potrzebami. Aspose.Words dla .NET to potężne narzędzie, które umożliwia rozległą personalizację i automatyzację dokumentów Word, co czyni je nieocenionym atutem dla programistów .NET.

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla .NET?
Aspose.Words for .NET to zaawansowana biblioteka umożliwiająca programowe tworzenie, modyfikowanie i konwertowanie dokumentów Word przy użyciu języka C#.

### Czy mogę formatować inne typy wykresów za pomocą Aspose.Words dla .NET?
Tak, Aspose.Words dla platformy .NET obsługuje wiele typów wykresów, w tym słupkowe, kolumnowe, kołowe i inne.

### Jak uzyskać tymczasową licencję na Aspose.Words dla .NET?
Możesz uzyskać tymczasową licencję [Tutaj](https://purchase.aspose.com/temporary-license/).

### Czy w programie Excel można powiązać etykiety danych z komórkami źródłowymi?
Tak, można łączyć etykiety danych z komórkami źródłowymi, co umożliwia dziedziczenie formatu liczb z komórki źródłowej.

### Gdzie mogę znaleźć bardziej szczegółową dokumentację Aspose.Words dla .NET?
Można znaleźć kompleksową dokumentację [Tutaj](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}