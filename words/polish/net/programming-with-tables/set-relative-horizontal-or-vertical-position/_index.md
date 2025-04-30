---
"description": "Dowiedz się, jak ustawić względne położenie poziome i pionowe tabel w dokumentach programu Word za pomocą Aspose.Words dla platformy .NET, korzystając z tego przewodnika krok po kroku."
"linktitle": "Ustaw względną pozycję poziomą lub pionową"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Ustaw względną pozycję poziomą lub pionową"
"url": "/pl/net/programming-with-tables/set-relative-horizontal-or-vertical-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ustaw względną pozycję poziomą lub pionową

## Wstęp

Czy kiedykolwiek czułeś się zablokowany, nie wiedząc, jak pozycjonować tabele dokładnie tak, jak chcesz w swoich dokumentach Word? Cóż, nie jesteś sam. Niezależnie od tego, czy tworzysz profesjonalny raport, czy stylową broszurę, wyrównanie tabel może mieć ogromne znaczenie. Właśnie tutaj Aspose.Words dla .NET okazuje się przydatny. Ten samouczek krok po kroku przeprowadzi Cię przez proces ustawiania względnych pozycji poziomych lub pionowych tabel w dokumentach Word. Zanurzmy się!

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

1. Aspose.Words dla .NET: Jeśli jeszcze tego nie zrobiłeś, możesz to pobrać [Tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: Visual Studio lub inne środowisko IDE zgodne z platformą .NET.
3. Podstawowa wiedza o języku C#: W tym samouczku zakładamy, że znasz podstawy programowania w języku C#.

## Importuj przestrzenie nazw

Po pierwsze, musisz zaimportować niezbędne przestrzenie nazw. Jest to niezbędne do dostępu do funkcjonalności Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Krok 1: Załaduj swój dokument

Aby zacząć, musisz załadować dokument Word do programu. Oto, jak to zrobić:

```csharp
// Ścieżka do katalogu dokumentów 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Ten fragment kodu ustawia ścieżkę do katalogu dokumentów i ładuje konkretny dokument, nad którym chcesz pracować. Upewnij się, że ścieżka dokumentu jest poprawna, aby uniknąć problemów z ładowaniem.

## Krok 2: Uzyskaj dostęp do tabeli

Następnie musimy uzyskać dostęp do tabeli w dokumencie. Zazwyczaj chciałbyś pracować z pierwszą tabelą w sekcji body.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Ta linia kodu pobiera pierwszą tabelę z treści dokumentu. Jeśli dokument ma wiele tabel, możesz odpowiednio dostosować indeks.

## Krok 3: Ustaw pozycję poziomą

Teraz ustawmy poziomą pozycję tabeli względem określonego elementu. W tym przykładzie umieścimy ją względem kolumny.

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

Ustawiając `HorizontalAnchor` Do `RelativeHorizontalPosition.Column`, wydajesz polecenie tabeli, aby wyrównała się poziomo względem kolumny, w której się znajduje.

## Krok 4: Ustaw pozycję pionową

Podobnie jak w przypadku pozycjonowania poziomego, możesz również ustawić pozycję pionową. Tutaj pozycjonujemy ją względem strony.

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

Ustawianie `VerticalAnchor` Do `RelativeVerticalPosition.Page` zapewnia pionowe wyrównanie tabeli względem strony.

## Krok 5: Zapisz swój dokument

Na koniec zapisz zmiany w nowym dokumencie. Jest to kluczowy krok, aby upewnić się, że zmiany zostaną zachowane.

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

To polecenie zapisuje zmodyfikowany dokument pod nową nazwą, dzięki czemu masz pewność, że oryginalny plik nie zostanie nadpisany.

## Wniosek

I masz! Udało Ci się ustawić względne pozycje poziome i pionowe dla tabeli w dokumencie Word za pomocą Aspose.Words dla .NET. Dzięki tej nowo odkrytej umiejętności możesz poprawić układ i czytelność swoich dokumentów, sprawiając, że będą wyglądać bardziej profesjonalnie i dopracowane. Eksperymentuj z różnymi pozycjami i sprawdź, co najlepiej odpowiada Twoim potrzebom.

## Najczęściej zadawane pytania

### Czy mogę pozycjonować tabele względem innych elementów?  
Tak, Aspose.Words pozwala na pozycjonowanie tabel względem różnych elementów, takich jak marginesy, strony, kolumny i inne.

### Czy potrzebuję licencji, aby używać Aspose.Words dla .NET?  
Tak, możesz kupić licencję [Tutaj](https://purchase.aspose.com/buy) lub uzyskaj tymczasową licencję [Tutaj](https://purchase.aspose.com/temporary-license/).

### Czy jest dostępna bezpłatna wersja próbna Aspose.Words dla .NET?  
Oczywiście! Możesz pobrać bezpłatną wersję próbną [Tutaj](https://releases.aspose.com/).

### Czy mogę używać Aspose.Words z innymi językami programowania?  
Aspose.Words został zaprojektowany przede wszystkim dla platformy .NET, ale dostępne są wersje dla platform Java, Python i innych.

### Gdzie mogę znaleźć bardziej szczegółową dokumentację?  
Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z dokumentacją Aspose.Words [Tutaj](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}