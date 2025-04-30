---
"description": "Dowiedz się, jak dynamicznie wiązać dane XML ze strukturalnymi znacznikami dokumentu w programie Word przy użyciu Aspose.Words dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku."
"linktitle": "Ustrukturyzowany zakres znaczników dokumentu początkowego mapowania XML"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Ustrukturyzowany zakres znaczników dokumentu początkowego mapowania XML"
"url": "/pl/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ustrukturyzowany zakres znaczników dokumentu początkowego mapowania XML

## Wstęp

Czy kiedykolwiek chciałeś dynamicznie wstawiać dane XML do dokumentu Word? Cóż, masz szczęście! Aspose.Words dla .NET sprawia, że to zadanie staje się proste. W tym samouczku zagłębiamy się w mapowanie początkowego zakresu znaczników XML w ustrukturyzowanym dokumencie. Ta funkcja umożliwia powiązanie niestandardowych części XML z kontrolkami treści, zapewniając bezproblemową aktualizację treści dokumentu za pomocą danych XML. Gotowy, aby przekształcić swoje dokumenty w dynamiczne arcydzieła.

## Wymagania wstępne

Zanim przejdziemy do kodowania, upewnijmy się, że masz wszystko, czego potrzebujesz:

1. Aspose.Words dla biblioteki .NET: Upewnij się, że masz najnowszą wersję. Możesz ją pobrać [Tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: Visual Studio lub inne środowisko IDE obsługujące język C#.
3. Podstawowa znajomość języka C#: Znajomość programowania w języku C# jest koniecznością.
4. Dokument Word: przykładowy dokument Word do pracy.

## Importuj przestrzenie nazw

Po pierwsze, zaimportujmy niezbędne przestrzenie nazw. Dzięki temu będziemy mieć dostęp do wszystkich wymaganych klas i metod w Aspose.Words dla .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Krok 1: Skonfiguruj katalog dokumentów

Każdy projekt potrzebuje fundamentu, prawda? Tutaj ustawiamy ścieżkę do katalogu dokumentów.

```csharp
// Ścieżka do katalogu dokumentów 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Załaduj dokument Word

Następnie ładujemy dokument Word. To jest dokument, do którego będziemy wstawiać nasze dane XML.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Krok 3: Dodaj niestandardową część XML

Musimy skonstruować część XML zawierającą dane, które chcemy wstawić i dodać ją do kolekcji CustomXmlPart dokumentu. Ta niestandardowa część XML będzie służyć jako źródło danych dla naszych ustrukturyzowanych tagów dokumentu.

### Tworzenie części XML

Najpierw wygeneruj unikalny identyfikator dla części XML i zdefiniuj jego zawartość.

```csharp
// Utwórz część XML zawierającą dane i dodaj ją do kolekcji CustomXmlPart dokumentu.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Zweryfikuj zawartość części XML

Aby mieć pewność, że część XML została dodana poprawnie, drukujemy jej zawartość.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## Krok 4: Utwórz ustrukturyzowany znacznik dokumentu

Strukturalny znacznik dokumentu (SDT) to kontrolka zawartości, która może być powiązana z częścią XML. Tutaj tworzymy SDT, który będzie wyświetlał zawartość naszej niestandardowej części XML.

Najpierw zlokalizuj początek zakresu SDT w dokumencie.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Krok 5: Ustaw mapowanie XML dla SDT

Teraz czas powiązać naszą część XML z SDT. Ustawiając mapowanie XML, określamy, która część danych XML powinna być wyświetlana w SDT.

XPath wskazuje na konkretny element w części XML, który chcemy wyświetlić. Tutaj wskazujemy na drugi `<text>` element w `<root>` element.

```csharp
// Ustaw mapowanie dla naszego StructuredDocumentTag
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Krok 6: Zapisz dokument

Na koniec zapisz dokument, aby zobaczyć zmiany w działaniu. SDT w dokumencie Word będzie teraz wyświetlać określoną zawartość XML.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Wniosek

masz to! Udało Ci się zmapować część XML do ustrukturyzowanego znacznika dokumentu w dokumencie Word przy użyciu Aspose.Words dla .NET. Ta potężna funkcja umożliwia Ci bezproblemowe tworzenie dynamicznych i zorientowanych na dane dokumentów. Niezależnie od tego, czy generujesz raporty, faktury czy jakikolwiek inny typ dokumentu, mapowanie XML może znacznie usprawnić Twój przepływ pracy.

## Najczęściej zadawane pytania

### Czym jest strukturalny znacznik dokumentu w programie Word?
Ustrukturyzowane znaczniki dokumentu, znane również jako kontrolki zawartości, to kontenery dla określonych typów zawartości w dokumentach Word. Mogą być używane do wiązania danych, ograniczania edycji lub prowadzenia użytkowników podczas tworzenia dokumentów.

### W jaki sposób mogę dynamicznie aktualizować zawartość części XML?
Zawartość części XML można zaktualizować, modyfikując `xmlPartContent` string przed dodaniem go do dokumentu. Po prostu zaktualizuj string nowymi danymi i dodaj go do `CustomXmlParts` kolekcja.

### Czy mogę powiązać wiele części XML z różnymi SDT w tym samym dokumencie?
Tak, możesz powiązać wiele części XML z różnymi SDT w tym samym dokumencie. Każdy SDT może mieć swoją własną unikalną część XML i mapowanie XPath.

### Czy możliwe jest mapowanie złożonych struktur XML na SDT?
Oczywiście! Możesz mapować złożone struktury XML na SDT, używając szczegółowych wyrażeń XPath, które dokładnie wskazują na pożądane elementy w części XML.

### Jak mogę usunąć część XML z dokumentu?
Możesz usunąć część XML, wywołując `Remove` metoda na `CustomXmlParts` kolekcja, przekazywanie `xmlPartId` części XML, którą chcesz usunąć.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}