---
"description": "Dowiedz się, jak dodać wartości daty i godziny do osi wykresu za pomocą Aspose.Words dla .NET, korzystając z tego kompleksowego przewodnika krok po kroku."
"linktitle": "Dodaj wartości daty i godziny do osi wykresu"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Dodaj wartości daty i godziny do osi wykresu"
"url": "/pl/net/programming-with-charts/date-time-values-to-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj wartości daty i godziny do osi wykresu

## Wstęp

Tworzenie wykresów w dokumentach może być skutecznym sposobem wizualizacji danych. Podczas pracy z danymi szeregów czasowych dodawanie wartości daty i godziny do osi wykresu jest kluczowe dla przejrzystości. W tym samouczku przeprowadzimy Cię przez proces dodawania wartości daty i godziny do osi wykresu przy użyciu Aspose.Words dla .NET. Ten przewodnik krok po kroku pomoże Ci skonfigurować środowisko, napisać kod i zrozumieć każdą część procesu. Zanurzmy się!

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że spełnione są następujące wymagania wstępne:

1. Visual Studio lub dowolne środowisko IDE .NET: potrzebujesz środowiska programistycznego, aby pisać i uruchamiać kod .NET.
2. Aspose.Words dla .NET: Powinieneś mieć zainstalowaną bibliotekę Aspose.Words dla .NET. Możesz ją pobrać z [Tutaj](https://releases.aspose.com/words/net/).
3. Podstawowa znajomość języka C#: W tym samouczku zakładamy, że posiadasz podstawową wiedzę na temat programowania w języku C#.
4. Ważna licencja Aspose: Licencję tymczasową można uzyskać od [Tutaj](https://purchase.aspose.com/temporary-license/).

## Importuj przestrzenie nazw

Na początek upewnij się, że masz niezbędne przestrzenie nazw zaimportowane do swojego projektu. Ten krok jest kluczowy dla dostępu do klas i metod Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Krok 1: Skonfiguruj katalog dokumentów

Najpierw musisz zdefiniować katalog, w którym zostanie zapisany Twój dokument. Jest to ważne dla uporządkowania plików i zapewnienia, że Twój kod działa poprawnie.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Utwórz nowy dokument i DocumentBuilder

Następnie utwórz nową instancję `Document` klasa i `DocumentBuilder` obiekt. Te obiekty pomogą Ci budować i manipulować Twoim dokumentem.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Wstaw wykres do dokumentu

Teraz wstaw wykres do dokumentu za pomocą `DocumentBuilder` obiekt. W tym przykładzie używamy wykresu kolumnowego, ale możesz wybrać również inne typy.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Krok 4: Wyczyść istniejące serie

Wyczyść wszystkie istniejące serie na wykresie, aby mieć pewność, że zaczynasz od pustej karty. Ten krok jest niezbędny w przypadku danych niestandardowych.

```csharp
chart.Series.Clear();
```

## Krok 5: Dodaj wartości daty i godziny do serii

Dodaj wartości daty i godziny do serii wykresu. Ten krok obejmuje tworzenie tablic dla dat i odpowiadających im wartości.

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## Krok 6: Skonfiguruj oś X

Ustaw skalowanie i znaczniki osi X. Dzięki temu daty będą wyświetlane poprawnie i w odpowiednich odstępach czasu.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## Krok 7: Zapisz dokument

Na koniec zapisz dokument w określonym katalogu. Ten krok kończy proces, a dokument powinien teraz zawierać wykres z wartościami daty i godziny na osi X.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Wniosek

Dodawanie wartości daty i godziny do osi wykresu w dokumencie to prosty proces dzięki Aspose.Words dla .NET. Postępując zgodnie z krokami opisanymi w tym samouczku, możesz tworzyć przejrzyste i informacyjne wykresy, które skutecznie wizualizują dane szeregów czasowych. Niezależnie od tego, czy przygotowujesz raporty, prezentacje czy jakikolwiek dokument wymagający szczegółowej reprezentacji danych, Aspose.Words zapewnia narzędzia potrzebne do osiągnięcia sukcesu.

## Najczęściej zadawane pytania

### Czy mogę używać innych typów wykresów z Aspose.Words dla .NET?

Tak, Aspose.Words obsługuje różne typy wykresów, w tym liniowe, słupkowe, kołowe i inne.

### Jak mogę dostosować wygląd mojego wykresu?

Możesz dostosować wygląd wykresu, uzyskując dostęp do jego właściwości i ustawiając style, kolory itp.

### Czy można dodać wiele serii do wykresu?

Oczywiście! Możesz dodać wiele serii do swojego wykresu, wywołując `Series.Add` metodę wielokrotnie z różnymi danymi.

### Co zrobić, jeśli muszę dynamicznie aktualizować dane na wykresie?

Dane na wykresie można aktualizować dynamicznie, manipulując właściwościami serii i osi programowo zgodnie ze swoimi wymaganiami.

### Gdzie mogę znaleźć bardziej szczegółową dokumentację Aspose.Words dla .NET?

Bardziej szczegółową dokumentację można znaleźć [Tutaj](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}