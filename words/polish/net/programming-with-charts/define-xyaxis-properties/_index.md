---
title: Definiowanie właściwości osi XY na wykresie
linktitle: Definiowanie właściwości osi XY na wykresie
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak definiować właściwości osi XY na wykresie za pomocą Aspose.Words dla .NET dzięki temu przewodnikowi krok po kroku. Idealne dla programistów .NET.
weight: 10
url: /pl/net/programming-with-charts/define-xyaxis-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Definiowanie właściwości osi XY na wykresie

## Wstęp

Wykresy są potężnym narzędziem do wizualizacji danych. Kiedy musisz tworzyć profesjonalne dokumenty z dynamicznymi wykresami, Aspose.Words for .NET jest nieocenioną biblioteką. Ten artykuł przeprowadzi Cię przez proces definiowania właściwości osi XY na wykresie przy użyciu Aspose.Words for .NET, rozbijając każdy krok, aby zapewnić przejrzystość i łatwość zrozumienia.

## Wymagania wstępne

Zanim zaczniesz kodować, musisz spełnić kilka warunków wstępnych:

1. Aspose.Words dla .NET: Upewnij się, że masz bibliotekę Aspose.Words dla .NET. Możesz[pobierz tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: Potrzebujesz zintegrowanego środowiska programistycznego (IDE), takiego jak Visual Studio.
3. .NET Framework: Upewnij się, że Twoje środowisko programistyczne jest przygotowane pod kątem programowania w środowisku .NET.
4. Podstawowa wiedza o języku C#: W tym przewodniku zakładamy, że posiadasz podstawową wiedzę na temat programowania w języku C#.

## Importuj przestrzenie nazw

Na początek musisz zaimportować niezbędne przestrzenie nazw do swojego projektu. Dzięki temu masz dostęp do wszystkich klas i metod wymaganych do tworzenia i manipulowania dokumentami i wykresami.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Podzielimy ten proces na proste kroki, z których każdy będzie skupiał się na konkretnym fragmencie definiowania właściwości osi XY na wykresie.

## Krok 1: Zainicjuj dokument i DocumentBuilder

 Najpierw musisz zainicjować nowy dokument i`DocumentBuilder` obiekt.`DocumentBuilder` pomaga w umieszczaniu treści w dokumencie.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Wstaw wykres

Następnie wstawisz wykres do dokumentu. W tym przykładzie użyjemy wykresu obszarowego. Możesz dostosować wymiary wykresu według potrzeb.

```csharp
// Wstaw wykres
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## Krok 3: Wyczyść domyślną serię i dodaj niestandardowe dane

Domyślnie wykres będzie miał kilka predefiniowanych serii. Wyczyścimy je i dodamy nasze niestandardowe serie danych.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
	new DateTime[]
	{
		new DateTime(2002, 01, 01), new DateTime(2002, 06, 01), new DateTime(2002, 07, 01),
		new DateTime(2002, 08, 01), new DateTime(2002, 09, 01)
	},
	new double[] { 640, 320, 280, 120, 150 });
```

## Krok 4: Zdefiniuj właściwości osi X

Teraz czas zdefiniować właściwości osi X. Obejmuje to ustawienie typu kategorii, dostosowanie przecięcia osi oraz dostosowanie znaczników i etykiet.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; //Mierzone w jednostkach wyświetlanych na osi Y (setkach).
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## Krok 5: Zdefiniuj właściwości osi Y

Podobnie ustawisz właściwości dla osi Y. Obejmuje to ustawienie pozycji etykiety znacznika, jednostek głównych i pobocznych, jednostki wyświetlania i skalowania.

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## Krok 6: Zapisz dokument

Na koniec zapisz dokument w określonym katalogu. Spowoduje to wygenerowanie dokumentu Word z dostosowanym wykresem.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Wniosek

Tworzenie i dostosowywanie wykresów w dokumentach Word przy użyciu Aspose.Words dla .NET jest proste, gdy zrozumiesz kroki. Ten przewodnik przeprowadzi Cię przez proces definiowania właściwości osi XY na wykresie, od inicjalizacji dokumentu do zapisania produktu końcowego. Dzięki tym umiejętnościom możesz tworzyć szczegółowe, profesjonalnie wyglądające wykresy, które wzbogacą Twoje dokumenty.

## Najczęściej zadawane pytania

### Jakie typy wykresów mogę tworzyć za pomocą Aspose.Words dla .NET?
Możesz tworzyć różne rodzaje wykresów, w tym wykresy warstwowe, słupkowe, liniowe, kołowe i inne.

### Jak zainstalować Aspose.Words dla .NET?
 Możesz pobrać Aspose.Words dla .NET z[Tutaj](https://releases.aspose.com/words/net/) postępuj zgodnie z wyświetlanymi instrukcjami instalacji.

### Czy mogę dostosować wygląd moich wykresów?
Tak, Aspose.Words dla .NET umożliwia szeroką personalizację wykresów, obejmującą kolory, czcionki i właściwości osi.

### Czy jest dostępna bezpłatna wersja próbna Aspose.Words dla .NET?
 Tak, możesz otrzymać bezpłatną wersję próbną[Tutaj](https://releases.aspose.com/).

### Gdzie mogę znaleźć więcej samouczków i dokumentacji?
 Więcej samouczków i szczegółowej dokumentacji znajdziesz na stronie[Strona dokumentacji Aspose.Words dla .NET](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
