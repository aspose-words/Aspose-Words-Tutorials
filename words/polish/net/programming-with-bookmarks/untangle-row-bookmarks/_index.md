---
title: Rozplątaj zakładki wierszy w dokumencie programu Word
linktitle: Rozplątaj zakładki wierszy w dokumencie programu Word
second_title: Aspose.Words API do przetwarzania dokumentów
description: Z łatwością rozwiąż splątane zakładki w dokumentach Word, korzystając z Aspose.Words dla .NET. Ten przewodnik przeprowadzi Cię przez proces przejrzystego i bezpieczniejszego zarządzania zakładkami.
weight: 10
url: /pl/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rozplątaj zakładki wierszy w dokumencie programu Word

## Wstęp

Czy kiedykolwiek spotkałeś się z sytuacją, w której usunięcie wiersza w dokumencie programu Word za pomocą zakładki powoduje bałagan w innych zakładkach w sąsiednich wierszach? Może to być niezwykle frustrujące, szczególnie w przypadku złożonych tabel. Na szczęście Aspose.Words dla .NET oferuje potężne rozwiązanie: rozplątywanie zakładek wierszy. 

Ten przewodnik przeprowadzi Cię przez proces rozplątywania zakładek wierszy w dokumentach programu Word przy użyciu Aspose.Words dla .NET. Podzielimy kod na łatwe do zrozumienia kroki i wyjaśnimy cel każdej funkcji, umożliwiając Ci bezproblemowe radzenie sobie z irytującymi problemami z zakładkami.

## Warunki wstępne

Zanim zaczniesz nurkować, będziesz potrzebować kilku rzeczy:

1.  Aspose.Words dla .NET: Ta komercyjna biblioteka zapewnia funkcje umożliwiające programową pracę z dokumentami programu Word. 2. Możesz pobrać bezpłatną wersję próbną ze strony[link do pobrania](https://releases.aspose.com/words/net/) lub kup licencję od[kupić](https://purchase.aspose.com/buy).
3. Środowisko programistyczne AC#: Visual Studio lub dowolne inne IDE C# będzie działać idealnie.
4. Dokument programu Word z zakładkami wierszy: w celach demonstracyjnych użyjemy przykładowego dokumentu o nazwie „Zakładki kolumn tabeli.docx”.

## Importuj przestrzenie nazw

Pierwszy krok polega na zaimportowaniu niezbędnych przestrzeni nazw do projektu C#. Te przestrzenie nazw zapewniają dostęp do klas i funkcjonalności, których będziemy używać w Aspose.Words dla .NET:

```csharp
using Aspose.Words;
using System;
```

## Krok 1: Załaduj dokument Word

 Zaczynamy od załadowania dokumentu Word zawierającego zakładki ze splątanymi wierszami. The`Document` klasa obsługuje manipulację dokumentami w Aspose.Words. Oto jak załadować dokument:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Zastąp lokalizacją dokumentu
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

 Pamiętaj o wymianie`"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką do pliku „Zakładki kolumn tabeli.docx”.

## Krok 2: Rozplątaj zakładki w rzędach

 To tutaj dzieje się magia! The`Untangle` funkcja zajmuje się rozplątaniem zakładek wierszy. Rozłóżmy jego funkcjonalność:

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   // Pobierz wiersz nadrzędny zarówno zakładki, jak i końca zakładki
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   // Sprawdź, czy wiersze są prawidłowe i sąsiadują ze sobą
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //Przenieś koniec zakładki na ostatni akapit ostatniej komórki w górnym wierszu
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

Oto wyjaśnienie krok po kroku działania kodu:

 Iterujemy po wszystkich zakładkach w dokumencie za pomocą a`foreach` pętla.
Dla każdej zakładki pobieramy wiersz nadrzędny początku zakładki (`bookmark.BookmarkStart`) i koniec zakładki (`bookmark.BookmarkEnd` ) za pomocą`GetAncestor` metoda.
Następnie sprawdzamy, czy znaleziono oba wiersze (`row1 != null`I`row2 != null`) i jeśli są sąsiadującymi rzędami (`row1.NextSibling == row2`). Dzięki temu modyfikujemy tylko zakładki rozciągające się na sąsiednie wiersze.
Jeżeli warunki są spełnione przesuwamy węzeł końcowy zakładki na koniec ostatniego akapitu w ostatniej komórce górnego wiersza (`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`) skutecznie je rozplątując.

## Krok 3: Usuń wiersz według zakładki

 Teraz, gdy zakładki są już rozplątane, możemy bezpiecznie usuwać wiersze, używając ich nazw zakładek. The`DeleteRowByBookmark` funkcja obsługuje to zadanie:

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

Oto podział tej funkcji:

Bierzemy nazwę zakładki (`bookmarkName`) jako dane wejściowe.
 Pobieramy odpowiedni obiekt zakładki za pomocą`doc.Range.Bookmarks[bookmarkName]`.
Następnie otrzymujemy wiersz nadrzędny zakładki, który zaczyna być używany`GetAncestor` (podobnie jak`Untangle` funkcjonować).
Na koniec sprawdzamy, czy zakładka i wiersz istnieją (`bookmark != null` I

## Krok 4: Sprawdź rozplątanie

 Podczas gdy`Untangle` powinna zapewniać bezpieczeństwo innych zakładek, zawsze warto to sprawdzić. Oto jak możemy sprawdzić, czy proces rozplątywania nie spowodował przypadkowego usunięcia końcówki kolejnej zakładki:

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

Ten fragment kodu sprawdza, czy koniec zakładki o nazwie „ROW1” nadal istnieje po usunięciu wiersza z zakładką „ROW2”. Jeśli ma wartość null, zgłaszany jest wyjątek, wskazując problem z procesem rozplątywania. 

## Krok 5: Zapisz dokument

 Na koniec, po rozplątaniu zakładek i ewentualnym usunięciu wierszy, zapisz zmodyfikowany dokument za pomocą`Save` metoda:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

Spowoduje to zapisanie dokumentu z rozplątanymi zakładkami i wszystkimi usuniętymi wierszami pod nową nazwą pliku „WorkingWithBookmarks.UntangleRowBookmarks.docx”. 

## Wniosek

 Wykonując poniższe kroki i korzystając z`Untangle`funkcji, możesz skutecznie rozplątać zakładki wierszy w dokumentach programu Word za pomocą Aspose.Words dla .NET. Dzięki temu usuwanie wierszy według zakładek nie spowoduje niezamierzonych konsekwencji w przypadku innych zakładek w sąsiednich wierszach. Pamiętaj o zastąpieniu symboli zastępczych, takich jak`"YOUR DOCUMENT DIRECTORY"` z rzeczywistymi ścieżkami i nazwami plików.

## Często zadawane pytania

### Czy Aspose.Words dla .NET jest darmowy?

 Aspose.Words dla .NET to biblioteka komercyjna z bezpłatną wersją próbną. Można go pobrać z[link do pobrania](https://releases.aspose.com/words/net/).

### Czy mogę ręcznie rozplątać zakładki wierszy w programie Word?

Ręczne rozplątywanie zakładek w programie Word może być uciążliwe i podatne na błędy, choć jest to technicznie możliwe. Aspose.Words dla .NET automatyzuje ten proces, oszczędzając czas i wysiłek.

###  Co się stanie, jeśli`Untangle` function encounters an error?

Kod zawiera procedurę obsługi wyjątków, która zgłasza wyjątek, jeśli proces rozplątywania przypadkowo usunie koniec innej zakładki. Możesz dostosować tę obsługę błędów do swoich konkretnych potrzeb.

### Czy mogę użyć tego kodu do rozplątania zakładek w niesąsiadujących wierszach?

Obecnie kod koncentruje się na rozplątywaniu zakładek rozciągających się na sąsiednie wiersze. Modyfikowanie kodu w celu obsługi nieprzylegających wierszy wymagałoby dodatkowej logiki w celu zidentyfikowania i obsługi tych scenariuszy.

### Czy istnieją jakieś ograniczenia w stosowaniu tej metody?

Podejście to zakłada, że zakładki są dobrze zdefiniowane w komórkach tabeli. Jeśli zakładki zostaną umieszczone poza komórkami lub w nieoczekiwanych lokalizacjach, proces rozplątywania może nie działać zgodnie z oczekiwaniami.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
