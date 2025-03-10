---
title: Wstaw wykres obszarowy do dokumentu Word
linktitle: Wstaw wykres obszarowy do dokumentu Word
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak wstawić wykres obszarowy do dokumentu za pomocą Aspose.Words dla .NET. Dodaj dane serii i zapisz dokument z wykresem.
weight: 10
url: /pl/net/programming-with-charts/insert-area-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw wykres obszarowy do dokumentu Word

## Wstęp

Witamy w tym przewodniku krok po kroku, jak wstawić wykres obszarowy do dokumentu Word za pomocą Aspose.Words dla .NET. Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero zaczynasz, ten samouczek przeprowadzi Cię przez wszystko, co musisz wiedzieć, aby tworzyć oszałamiające i pouczające wykresy obszarowe w dokumentach Word. Omówimy wymagania wstępne, pokażemy, jak importować niezbędne przestrzenie nazw i poprowadzimy Cię przez każdy etap procesu za pomocą jasnych, łatwych do naśladowania instrukcji.

## Wymagania wstępne

Zanim przejdziemy do konkretów, upewnijmy się, że masz wszystko, czego potrzebujesz, aby zacząć:

1.  Aspose.Words dla .NET: Upewnij się, że masz zainstalowany Aspose.Words dla .NET. Możesz go pobrać[Tutaj](https://releases.aspose.com/words/net/).
2. .NET Framework: Upewnij się, że na Twoim komputerze jest zainstalowany .NET Framework.
3. IDE: Zintegrowane środowisko programistyczne (IDE) podobne do Visual Studio, służące do pisania i wykonywania kodu.
4. Podstawowa wiedza w języku C#: Przydatna będzie podstawowa znajomość programowania w języku C#.

Gdy spełnisz te wymagania wstępne, będziesz gotowy, aby tworzyć piękne wykresy obszarowe w dokumentach programu Word.

## Importuj przestrzenie nazw

Najpierw zaimportujmy niezbędne przestrzenie nazw. Te przestrzenie nazw zapewniają klasy i metody wymagane do pracy z dokumentami Word i wykresami w Aspose.Words dla .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
```

Teraz, gdy zaimportowaliśmy podstawowe przestrzenie nazw, możemy przejść do tworzenia dokumentu i wstawiania wykresu warstwowego krok po kroku.

## Krok 1: Utwórz nowy dokument Word

Zacznijmy od utworzenia nowego dokumentu Word. Będzie to baza, do której wstawimy nasz wykres obszarowy.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

 W tym kroku inicjujemy nowy`Document` obiekt, który reprezentuje nasz dokument Word.

## Krok 2: Użyj DocumentBuilder, aby wstawić wykres

 Następnie użyjemy`DocumentBuilder` klasę umożliwiającą wstawienie wykresu obszarowego do naszego dokumentu.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
```

 Tutaj tworzymy`DocumentBuilder` obiekt i użyj go, aby wstawić do naszego dokumentu wykres obszarowy o określonych wymiarach (432x252).

## Krok 3: Uzyskaj dostęp do obiektu wykresu

 Po wstawieniu wykresu musimy uzyskać dostęp do`Chart` obiekt umożliwiający dostosowanie naszego wykresu obszarowego.

```csharp
Chart chart = shape.Chart;
```

 Ta linia kodu pobiera`Chart` obiekt z kształtu, który właśnie wstawiliśmy.

## Krok 4: Dodaj dane serii do wykresu

Teraz czas dodać trochę danych do naszego wykresu. Dodamy serię z datami i odpowiadającymi im wartościami.

```csharp
chart.Series.Add("Aspose Series 1", new []
{
    new DateTime(2002, 05, 01),
    new DateTime(2002, 06, 01),
    new DateTime(2002, 07, 01),
    new DateTime(2002, 08, 01),
    new DateTime(2002, 09, 01)
}, 
new double[] { 32, 32, 28, 12, 15 });
```

tym kroku dodajemy serię o nazwie „Aspose Series 1” zawierającą zestaw dat i odpowiadających im wartości.

## Krok 5: Zapisz dokument

Na koniec zapiszemy nasz dokument z wstawionym wykresem powierzchniowym.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertAreaChart.docx");
```

Ta linia kodu zapisuje dokument w określonym katalogu pod podaną nazwą pliku.

## Wniosek

Gratulacje! Udało Ci się wstawić wykres obszarowy do dokumentu Word za pomocą Aspose.Words dla .NET. Ten przewodnik przeprowadzi Cię przez każdy krok, od konfiguracji środowiska po zapisanie ostatecznego dokumentu. Dzięki Aspose.Words dla .NET możesz tworzyć szeroką gamę wykresów i innych złożonych elementów w dokumentach Word, dzięki czemu Twoje raporty i prezentacje będą bardziej dynamiczne i pouczające.

## Najczęściej zadawane pytania

### Czy mogę używać Aspose.Words dla .NET z innymi językami .NET?
Tak, Aspose.Words dla .NET obsługuje inne języki .NET, takie jak VB.NET.

### Czy można dostosować wygląd wykresu?
Oczywiście! Aspose.Words dla .NET zapewnia rozbudowane opcje dostosowywania wyglądu wykresów.

### Czy mogę dodać wiele wykresów do jednego dokumentu Word?
Tak, do jednego dokumentu Word możesz wstawić dowolną liczbę wykresów.

### Czy Aspose.Words dla platformy .NET obsługuje inne typy wykresów?
Tak, Aspose.Words dla platformy .NET obsługuje różne typy wykresów, w tym słupkowe, liniowe, kołowe i inne.

### Gdzie mogę uzyskać tymczasową licencję na Aspose.Words dla .NET?
 Możesz uzyskać tymczasową licencję od[Tutaj](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
