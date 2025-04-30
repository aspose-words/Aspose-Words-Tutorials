---
"description": "Dowiedz się, jak połączyć dwa dokumenty Word za pomocą Aspose.Words dla .NET. Przewodnik krok po kroku, jak wstawić dokument za pomocą DocumentBuilder i zachować formatowanie."
"linktitle": "Wstaw dokument za pomocą kreatora"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Wstaw dokument za pomocą kreatora"
"url": "/pl/net/join-and-append-documents/insert-document-with-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw dokument za pomocą kreatora

## Wstęp

Masz więc dwa dokumenty Worda i chcesz je połączyć w jeden. Możesz pomyśleć: „Czy istnieje łatwy sposób, aby zrobić to programowo?” Oczywiście! Dzisiaj przeprowadzę Cię przez proces wstawiania jednego dokumentu do drugiego za pomocą biblioteki Aspose.Words dla .NET. Ta metoda jest bardzo przydatna, zwłaszcza gdy masz do czynienia z dużymi dokumentami lub gdy musisz zautomatyzować proces. Zaczynajmy!

## Wymagania wstępne

Zanim zaczniemy, upewnijmy się, że masz wszystko, czego potrzebujesz:

1. Aspose.Words dla .NET: Jeśli jeszcze tego nie zrobiłeś, możesz pobrać ze strony [Tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: Upewnij się, że masz zainstalowany program Visual Studio lub inne odpowiednie środowisko programistyczne.
3. Podstawowa znajomość języka C#: Niewielka znajomość języka C# okaże się bardzo pomocna.

## Importuj przestrzenie nazw

Po pierwsze, musisz zaimportować niezbędne przestrzenie nazw, aby uzyskać dostęp do funkcjonalności biblioteki Aspose.Words. Oto, jak możesz to zrobić:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Teraz, gdy już spełniliśmy wszystkie wymagania wstępne, przeanalizujmy proces krok po kroku.

## Krok 1: Konfigurowanie katalogu dokumentów

Zanim zaczniemy kodować, musisz ustawić ścieżkę do katalogu dokumentów. To tutaj przechowywane są dokumenty źródłowe i docelowe.

```csharp
// Ścieżka do katalogu dokumentów 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Zastępować `"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką, gdzie znajdują się Twoje dokumenty. To pomoże programowi łatwo znaleźć Twoje pliki.

## Krok 2: Ładowanie dokumentów źródłowych i docelowych

Następnie musimy załadować dokumenty, z którymi chcemy pracować. W tym przykładzie mamy dokument źródłowy i dokument docelowy.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

Tutaj używamy `Document` klasa z biblioteki Aspose.Words do ładowania naszych dokumentów. Upewnij się, że nazwy plików są zgodne z tymi w Twoim katalogu.

## Krok 3: Tworzenie obiektu DocumentBuilder

Ten `DocumentBuilder` Klasa jest potężnym narzędziem w bibliotece Aspose.Words. Pozwala nam nawigować i manipulować dokumentem.

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

W tym kroku utworzyliśmy `DocumentBuilder` obiekt dla naszego dokumentu docelowego. Pomoże nam to wstawić treść do dokumentu.

## Krok 4: Przejście na koniec dokumentu

Przed wstawieniem dokumentu źródłowego musimy przenieść kursor konstruktora na koniec dokumentu docelowego.

```csharp
builder.MoveToDocumentEnd();
```

Gwarantuje to, że dokument źródłowy zostanie wstawiony na końcu dokumentu docelowego.

## Krok 5: Wstawianie podziału strony

Aby zachować porządek, dodajmy podział strony przed wstawieniem dokumentu źródłowego. Spowoduje to rozpoczęcie treści dokumentu źródłowego na nowej stronie.

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

Podział strony zapewnia, że treść źródłowego dokumentu zaczyna się na nowej stronie, dzięki czemu scalony dokument wygląda profesjonalnie.

## Krok 6: Wstawianie dokumentu źródłowego

Teraz nadchodzi najbardziej ekscytująca część — faktyczne wstawienie dokumentu źródłowego do dokumentu docelowego.

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

Korzystanie z `InsertDocument` metodą, możemy wstawić cały dokument źródłowy do dokumentu docelowego. `ImportFormatMode.KeepSourceFormatting` zapewnia zachowanie formatowania dokumentu źródłowego.

## Krok 7: Zapisywanie scalonego dokumentu

Na koniec zapiszmy scalony dokument. To połączy dokumenty źródłowe i docelowe w jeden plik.

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

Zapisując dokument, kończymy proces scalania dwóch dokumentów. Twój nowy dokument jest teraz gotowy i zapisany w określonym katalogu.

## Wniosek

I masz! Udało Ci się wstawić jeden dokument do drugiego za pomocą Aspose.Words dla .NET. Ta metoda jest nie tylko wydajna, ale również zachowuje formatowanie obu dokumentów, zapewniając płynne scalanie. Niezależnie od tego, czy pracujesz nad jednorazowym projektem, czy potrzebujesz zautomatyzować przetwarzanie dokumentów, Aspose.Words dla .NET ma dla Ciebie rozwiązanie.

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla .NET?  
Aspose.Words for .NET to zaawansowana biblioteka umożliwiająca programistom programistyczne tworzenie, edycję, konwertowanie i manipulowanie dokumentami Word.

### Czy mogę zachować formatowanie dokumentu źródłowego?  
Tak, za pomocą `ImportFormatMode.KeepSourceFormatting`formatowanie dokumentu źródłowego zostaje zachowane po wstawieniu go do dokumentu docelowego.

### Czy potrzebuję licencji, aby używać Aspose.Words dla .NET?  
Tak, Aspose.Words dla .NET wymaga licencji dla pełnej funkcjonalności. Możesz uzyskać [licencja tymczasowa](https://purchase.aspose.com/temporary-license/) do oceny.

### Czy mogę zautomatyzować ten proces?  
Oczywiście! Opisaną metodę można włączyć do większych aplikacji w celu automatyzacji zadań przetwarzania dokumentów.

### Gdzie mogę znaleźć więcej materiałów i wsparcia?  
Aby uzyskać więcej informacji, sprawdź [dokumentacja](https://reference.aspose.com/words/net/)lub odwiedź [forum wsparcia](https://forum.aspose.com/c/words/8) po pomoc.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}