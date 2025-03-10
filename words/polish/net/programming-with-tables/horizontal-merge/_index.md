---
title: Łączenie poziome
linktitle: Łączenie poziome
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak scalać poziomo komórki w dokumencie programu Word za pomocą Aspose.Words dla platformy .NET, korzystając ze szczegółowego samouczka krok po kroku.
weight: 10
url: /pl/net/programming-with-tables/horizontal-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Łączenie poziome

## Wstęp

Cześć! Gotowy, aby zanurzyć się w świecie Aspose.Words dla .NET? Dzisiaj zajmiemy się super przydatną funkcją: poziomym scalaniem tabel. Może to brzmieć trochę technicznie, ale nie martw się, mam dla Ciebie wsparcie. Pod koniec tego samouczka będziesz profesjonalistą w programowym scalaniu komórek w dokumentach Word. Więc zakasajmy rękawy i zaczynajmy!

## Wymagania wstępne

Zanim przejdziemy do konkretów, jest kilka rzeczy, które musisz mieć na miejscu:

1. Biblioteka Aspose.Words dla .NET: Jeśli jeszcze tego nie zrobiłeś, pobierz bibliotekę Aspose.Words dla .NET. Możesz ją pobrać[Tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: Upewnij się, że masz skonfigurowane odpowiednie środowisko programistyczne, np. Visual Studio.
3. Podstawowa znajomość języka C#: Podstawowa znajomość programowania w języku C# będzie przydatna.

Gdy już to wszystko załatwisz, będziesz gotowy do drogi!

## Importuj przestrzenie nazw

Zanim zagłębimy się w kod, upewnijmy się, że zaimportowaliśmy niezbędne przestrzenie nazw. W swoim projekcie C# upewnij się, że uwzględniłeś:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Dobrze, przeanalizujmy teraz proces poziomego scalania komórek tabeli w dokumencie programu Word za pomocą Aspose.Words dla platformy .NET.

## Krok 1: Konfigurowanie dokumentu

 Najpierw musimy utworzyć nowy dokument Word i zainicjować go.`DocumentBuilder`:

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ten fragment kodu tworzy nowy dokument i przygotowuje`DocumentBuilder` do działania.

## Krok 2: Wstawianie pierwszej komórki

Następnie zaczynamy od wstawienia pierwszej komórki i oznaczenia jej do scalenia poziomego:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

 Tutaj wstawiamy nową komórkę i ustawiamy jej`HorizontalMerge`nieruchomość do`CellMerge.First`, wskazując, że komórka ta jest początkiem połączonej sekwencji komórek.

## Krok 3: Wstawianie scalonej komórki

Teraz wstawiamy komórkę, która zostanie połączona z poprzednią:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

 Komórka ta jest ustawiona tak, aby połączyć się z poprzednią komórką za pomocą`CellMerge.Previous` . Zauważ, jak kończymy wiersz słowami`builder.EndRow()`.

## Krok 4: Wstawianie niepołączonych komórek

Aby zobrazować różnicę, wstawmy kilka niepołączonych komórek:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Tutaj wstawiamy dwie komórki bez poziomego scalania. Pokazuje to, jak zachowują się komórki, gdy nie są częścią scalonej sekwencji.

## Krok 5: Wykończenie tabeli

Na koniec kończymy tabelę i zapisujemy dokument:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Ten fragment kodu uzupełnia tabelę i zapisuje dokument w określonym katalogu.

## Wniosek

I masz to! Właśnie opanowałeś sztukę poziomego scalania komórek w dokumencie Word za pomocą Aspose.Words dla .NET. Postępując zgodnie z tymi krokami, możesz z łatwością tworzyć złożone struktury tabel. Eksperymentuj i odkrywaj możliwości Aspose.Words, aby Twoje dokumenty były tak dynamiczne i elastyczne, jak potrzebujesz. Miłego kodowania!

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla .NET?
Aspose.Words for .NET to zaawansowana biblioteka umożliwiająca programistom tworzenie, edycję i manipulowanie dokumentami Word programowo w aplikacjach .NET.

### Czy mogę scalać komórki pionowo za pomocą Aspose.Words dla .NET?
 Tak, możesz również scalać komórki w pionie, używając`CellFormat.VerticalMerge` nieruchomość.

### Czy korzystanie z Aspose.Words dla .NET jest bezpłatne?
 Aspose.Words dla .NET oferuje bezpłatną wersję próbną, ale aby uzyskać pełną funkcjonalność, musisz kupić licencję. Możesz uzyskać tymczasową licencję[Tutaj](https://purchase.aspose.com/temporary-license/).

### Jak mogę dowiedzieć się więcej o Aspose.Words dla .NET?
 Możesz zapoznać się ze szczegółową dokumentacją[Tutaj](https://reference.aspose.com/words/net/).

### Gdzie mogę uzyskać pomoc dotyczącą Aspose.Words dla .NET?
 W przypadku pytań lub problemów możesz odwiedzić forum pomocy technicznej Aspose[Tutaj](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
