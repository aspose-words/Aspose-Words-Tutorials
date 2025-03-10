---
title: Dostosuj pojedynczy punkt danych wykresu na wykresie
linktitle: Dostosuj pojedynczy punkt danych wykresu na wykresie
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak dostosować pojedyncze punkty danych wykresu za pomocą Aspose.Words dla .NET w szczegółowym przewodniku krok po kroku. Ulepsz swoje wykresy za pomocą unikalnych znaczników i rozmiarów.
weight: 10
url: /pl/net/programming-with-charts/single-chart-data-point/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dostosuj pojedynczy punkt danych wykresu na wykresie

## Wstęp

Czy zastanawiałeś się kiedyś, jak sprawić, by Twoje wykresy wyróżniały się unikalnymi punktami danych? Cóż, dziś jest Twój szczęśliwy dzień! Zanurzamy się w dostosowywaniu pojedynczego punktu danych wykresu za pomocą Aspose.Words dla .NET. Zapnij pasy i przejdź przez samouczek krok po kroku, który jest nie tylko pouczający, ale także zabawny i łatwy do naśladowania.

## Wymagania wstępne

Zanim zaczniemy, upewnijmy się, że masz wszystko, co niezbędne:

-  Biblioteka Aspose.Words for .NET: Upewnij się, że masz najnowszą wersję.[Pobierz tutaj](https://releases.aspose.com/words/net/).
- .NET Framework: Upewnij się, że na Twoim komputerze jest zainstalowany .NET Framework.
- Podstawowa znajomość języka C#: Przydatna będzie podstawowa znajomość programowania w języku C#.
- Zintegrowane środowisko programistyczne (IDE): Zalecane jest środowisko Visual Studio.

## Importuj przestrzenie nazw

Najpierw zaimportujmy niezbędne przestrzenie nazw, aby rozpocząć działanie:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Krok 1: Zainicjuj dokument i DocumentBuilder

Dobrze, zacznijmy od zainicjowania nowego dokumentu i DocumentBuilder. To będzie płótno dla naszego wykresu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Tutaj,`dataDir` jest ścieżką do katalogu, w którym zapiszesz swój dokument.`DocumentBuilder` Klasa pomaga w konstruowaniu dokumentu.

## Krok 2: Wstaw wykres

Następnie wstawmy wykres liniowy do dokumentu. To będzie nasz plac zabaw do dostosowywania punktów danych.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

 Ten`InsertChart` Metoda przyjmuje typ wykresu, szerokość i wysokość jako parametry. W tym przypadku wstawiamy wykres liniowy o szerokości 432 i wysokości 252.

## Krok 3: Dostęp do serii wykresów

Teraz czas na dostęp do serii na naszym wykresie. Wykres może mieć wiele serii, a każda seria zawiera punkty danych.

```csharp
ChartSeries series0 = chart.Series[0];
ChartSeries series1 = chart.Series[1];
```

Tutaj uzyskujemy dostęp do pierwszych dwóch serii na naszym wykresie. 

## Krok 4: Dostosuj punkty danych

Tutaj dzieje się magia! Dostosujmy konkretne punkty danych w naszej serii.

```csharp
ChartDataPointCollection dataPointCollection = series0.DataPoints;
ChartDataPoint dataPoint00 = dataPointCollection[0];
ChartDataPoint dataPoint01 = dataPointCollection[1];
```

Pobieramy punkty danych z pierwszej serii. Teraz dostosujmy te punkty.

### Dostosuj punkt danych 00

```csharp
dataPoint00.Explosion = 50;
dataPoint00.Marker.Symbol = MarkerSymbol.Circle;
dataPoint00.Marker.Size = 15;
```

 Dla`dataPoint00`, ustawiamy eksplozję (przydatne w przypadku wykresów kołowych), zmieniamy symbol znacznika na okrąg i ustawiamy rozmiar znacznika na 15.

### Dostosuj punkt danych 01

```csharp
dataPoint01.Marker.Symbol = MarkerSymbol.Diamond;
dataPoint01.Marker.Size = 20;
```

 Dla`dataPoint01`, zmieniamy symbol znacznika na romb i ustawiamy rozmiar znacznika na 20.

### Dostosuj punkt danych w serii 1

```csharp
ChartDataPoint dataPoint12 = series1.DataPoints[2];
dataPoint12.InvertIfNegative = true;
dataPoint12.Marker.Symbol = MarkerSymbol.Star;
dataPoint12.Marker.Size = 20;
```

 W przypadku trzeciego punktu danych`series1`, ustawiamy ją na odwrócenie, jeśli wartość jest ujemna, zmieniamy symbol znacznika na gwiazdkę i ustawiamy rozmiar znacznika na 20.

## Krok 5: Zapisz dokument

Na koniec zapiszemy nasz dokument ze wszystkimi zmianami.

```csharp
doc.Save(dataDir + "WorkingWithCharts.SingleChartDataPoint.docx");
```

 Ten wiersz zapisuje dokument w określonym katalogu pod nazwą`WorkingWithCharts.SingleChartDataPoint.docx`.

## Wniosek

masz to! Udało Ci się dostosować poszczególne punkty danych na wykresie za pomocą Aspose.Words dla .NET. Zmieniając kilka właściwości, możesz sprawić, że Twoje wykresy będą o wiele bardziej informacyjne i atrakcyjne wizualnie. Więc eksperymentuj z różnymi znacznikami i rozmiarami, aby zobaczyć, co najlepiej sprawdzi się w przypadku Twoich danych.

## Najczęściej zadawane pytania

### Czy mogę dostosować punkty danych na innych typach wykresów?

Oczywiście! Możesz dostosować punkty danych w różnych typach wykresów, w tym wykresach słupkowych, wykresach kołowych i innych. Proces jest podobny w różnych typach wykresów.

### Czy można dodawać niestandardowe etykiety do punktów danych?

 Tak, możesz dodawać niestandardowe etykiety do punktów danych za pomocą`ChartDataPoint.Label` Własność. Pozwala to na zapewnienie większego kontekstu dla każdego punktu danych.

### Jak mogę usunąć punkt danych z serii?

 Możesz usunąć punkt danych, ustawiając jego widoczność na fałsz za pomocą`dataPoint.IsVisible = false`.

### Czy mogę używać obrazów jako znaczników punktów danych?

Chociaż Aspose.Words nie obsługuje bezpośredniego używania obrazów jako znaczników, można tworzyć własne kształty i używać ich jako znaczników.

### Czy można animować punkty danych na wykresie?

Aspose.Words dla .NET nie obsługuje animacji punktów danych wykresu. Możesz jednak tworzyć animowane wykresy za pomocą innych narzędzi i osadzać je w dokumentach Word.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
