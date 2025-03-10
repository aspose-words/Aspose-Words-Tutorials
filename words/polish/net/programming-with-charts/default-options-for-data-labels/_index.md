---
title: Ustaw domyślne opcje etykiet danych na wykresie
linktitle: Ustaw domyślne opcje etykiet danych na wykresie
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak ustawić domyślne opcje etykiet danych na wykresie przy użyciu Aspose.Words dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby bez wysiłku tworzyć i dostosowywać wykresy.
weight: 10
url: /pl/net/programming-with-charts/default-options-for-data-labels/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ustaw domyślne opcje etykiet danych na wykresie

## Wstęp

Cześć! Czy jesteś podekscytowany zanurzeniem się w świecie automatyzacji dokumentów? Dzisiaj przyjrzymy się, jak używać Aspose.Words dla .NET do tworzenia oszałamiających dokumentów programowo. Aspose.Words to potężna biblioteka, która pozwala z łatwością manipulować dokumentami Word, a w tym samouczku skupimy się na ustawianiu domyślnych opcji etykiet danych na wykresie. Niezależnie od tego, czy jesteś doświadczonym programistą, czy nowicjuszem, ten przewodnik przeprowadzi Cię przez każdy krok, abyś mógł szybko zacząć pracę.

## Wymagania wstępne

Zanim zaczniemy, upewnijmy się, że masz wszystko, czego potrzebujesz, aby śledzić ten samouczek. Oto krótka lista kontrolna:

- Visual Studio lub inne środowisko IDE zgodne z platformą .NET: W tym miejscu będziesz pisać i uruchamiać swój kod.
-  Aspose.Words dla .NET: Możesz[pobierz najnowszą wersję](https://releases.aspose.com/words/net/) i zainstaluj go w swoim projekcie.
- Podstawowa znajomość programowania w języku C#: Chociaż niniejszy przewodnik jest przyjazny dla początkujących, przydatna będzie pewna znajomość języka C#.
- Zainstalowany .NET Framework: Upewnij się, że na Twoim komputerze jest zainstalowany .NET Framework.
-  Tymczasowa licencja na Aspose.Words: Zdobądź jedną[Tutaj](https://purchase.aspose.com/temporary-license/) aby odblokować pełną funkcjonalność.

Gdy już spełnisz te wymagania wstępne, będziemy gotowi do działania!

## Importuj przestrzenie nazw

Najpierw skonfigurujmy nasz projekt i zaimportujmy niezbędne przestrzenie nazw. Te przestrzenie nazw są kluczowe dla dostępu do funkcjonalności Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## Krok 1: Utwórz nowy dokument


 Podróż rozpoczyna się od utworzenia nowego dokumentu i zainicjowania`DocumentBuilder` . Ten`DocumentBuilder` Klasa udostępnia zestaw metod umożliwiających łatwą manipulację zawartością dokumentu.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Utwórz nowy dokument
Document doc = new Document();

// Zainicjuj DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Wyjaśnienie

 W tym kroku skonfigurowaliśmy dokument i kreator, którego użyjemy do wstawiania i formatowania naszej zawartości.`dataDir` zmienna zawiera ścieżkę, pod którą zapiszemy nasz ostateczny dokument.

## Krok 2: Wstaw wykres

 Następnie dodamy wykres kołowy do naszego dokumentu.`InsertChart` metoda`DocumentBuilder` Klasa sprawia, że jest to superłatwe.

```csharp
// Wstaw wykres kołowy
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Uzyskaj dostęp do obiektu wykresu
Chart chart = shape.Chart;
```

### Wyjaśnienie

Tutaj wstawiamy wykres kołowy do naszego dokumentu.`InsertChart` Metoda wymaga typu wykresu, szerokości i wysokości jako parametrów. Po wstawieniu wykresu uzyskujemy dostęp do obiektu wykresu, aby dalej nim manipulować.

## Krok 3: Dostosuj serię wykresów

Teraz wyczyścimy wszystkie istniejące serie na wykresie i dodamy nasze serie niestandardowe. Ta seria będzie reprezentować nasze punkty danych.

```csharp
// Wyczyść istniejącą serię wykresów
chart.Series.Clear();

// Dodaj nową serię do wykresu
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Wyjaśnienie

W tym kroku upewniamy się, że nasz wykres jest pusty, czyszcząc wszelkie istniejące serie. Następnie dodajemy nową serię z niestandardowymi kategoriami i wartościami, które zostaną wyświetlone na naszym wykresie kołowym.

## Krok 4: Ustaw domyślne opcje etykiet danych

Etykiety danych są kluczowe dla uczynienia wykresu informacyjnym. Ustawimy opcje, aby pokazać procent, wartość i dostosować separator.

```csharp
// Uzyskaj dostęp do kolekcji etykiet danych
ChartDataLabelCollection labels = series.DataLabels;

// Ustaw opcje etykiet danych
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Wyjaśnienie

 Tutaj uzyskujemy dostęp do`DataLabels`właściwość naszej serii, aby dostosować wygląd i informacje wyświetlane na każdej etykiecie danych. Wybraliśmy wyświetlanie zarówno procentu, jak i wartości, ukrywanie linii odniesienia i ustawianie niestandardowego separatora.

## Krok 5: Zapisz dokument

Na koniec zapiszemy nasz dokument w określonym katalogu. Ten krok zapewnia, że wszystkie nasze zmiany zostaną zapisane w pliku.

```csharp
// Zapisz dokument
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Wyjaśnienie

 W tym ostatnim kroku zapisujemy nasz dokument za pomocą`Save` metoda. Dokument zostanie zapisany w katalogu określonym przez`dataDir`, o nazwie „WorkingWithCharts.DefaultOptionsForDataLabels.docx”.

## Wniosek

I masz! Udało Ci się utworzyć dokument Word z dostosowanym wykresem kołowym przy użyciu Aspose.Words dla .NET. Ta potężna biblioteka ułatwia automatyzację tworzenia i manipulowania dokumentami, oszczędzając Twój czas i wysiłek. Niezależnie od tego, czy generujesz raporty, faktury czy jakikolwiek inny typ dokumentu, Aspose.Words ma dla Ciebie rozwiązanie.

 Zapraszamy do eksploracji[Dokumentacja Aspose.Words](https://reference.aspose.com/words/net/) aby uzyskać więcej funkcji i przykładów. Miłego kodowania!

## Najczęściej zadawane pytania

### Czy mogę używać Aspose.Words za darmo?
Możesz używać Aspose.Words bezpłatnie z[licencja tymczasowa](https://purchase.aspose.com/temporary-license/) lub poznaj jego funkcje, korzystając z[bezpłatny okres próbny](https://releases.aspose.com/).

### Jak uzyskać pomoc techniczną dotyczącą Aspose.Words?
 Możesz uzyskać wsparcie poprzez[Forum wsparcia Aspose.Words](https://forum.aspose.com/c/words/8).

### Czy mogę dodać inne rodzaje wykresów?
 Tak, Aspose.Words obsługuje różne typy wykresów, takie jak wykresy słupkowe, liniowe i kolumnowe. Sprawdź[dokumentacja](https://reference.aspose.com/words/net/) Aby uzyskać więcej szczegółów.

### Czy Aspose.Words jest kompatybilny z .NET Core?
 Tak, Aspose.Words jest kompatybilny z .NET Core. Więcej informacji znajdziesz w[dokumentacja](https://reference.aspose.com/words/net/).

### Jak mogę zakupić licencję na Aspose.Words?
 Możesz zakupić licencję od[Sklep Aspose](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
