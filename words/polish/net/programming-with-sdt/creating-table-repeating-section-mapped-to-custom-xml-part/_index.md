---
"description": "Dowiedz się, jak utworzyć tabelę z powtarzalną sekcją zamapowaną na CustomXmlPart w dokumencie programu Word przy użyciu Aspose.Words for .NET."
"linktitle": "Tworzenie powtarzającej się sekcji tabeli zamapowanej na niestandardową część XML"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Tworzenie powtarzającej się sekcji tabeli zamapowanej na niestandardową część XML"
"url": "/pl/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tworzenie powtarzającej się sekcji tabeli zamapowanej na niestandardową część XML

## Wstęp

W tym samouczku przejdziemy przez proces tworzenia tabeli z powtarzającą się sekcją, która jest mapowana na niestandardową część XML przy użyciu Aspose.Words dla .NET. Jest to szczególnie przydatne do dynamicznego generowania dokumentów na podstawie ustrukturyzowanych danych.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:
1. Zainstalowano bibliotekę Aspose.Words dla .NET. Możesz ją pobrać ze strony [Strona internetowa Aspose](https://releases.aspose.com/words/net/).
2. Podstawowa znajomość języka C# i XML.

## Importuj przestrzenie nazw

Pamiętaj o uwzględnieniu w projekcie niezbędnych przestrzeni nazw:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Krok 1: Zainicjuj dokument i DocumentBuilder

Najpierw utwórz nowy dokument i zainicjuj `DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Dodaj niestandardową część XML

Dodaj niestandardową część XML do dokumentu. Ten XML zawiera dane, które chcemy zmapować do naszej tabeli:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Krok 3: Utwórz strukturę tabeli

Następnie użyj `DocumentBuilder` aby utworzyć nagłówek tabeli:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Krok 4: Utwórz sekcję powtarzalną

Utwórz `StructuredDocumentTag` (SDT) dla powtarzającej się sekcji i zamapuj ją na dane XML:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Krok 5: Utwórz powtarzający się element sekcji

Utwórz SDT dla elementu sekcji powtarzalnej i dodaj go do sekcji powtarzalnej:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Krok 6: Mapowanie danych XML do komórek tabeli

Utwórz SDT dla tytułu i autora, zmapuj je do danych XML i dołącz do wiersza:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Krok 7: Zapisz dokument

Na koniec zapisz dokument w podanym katalogu:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Wniosek

Postępując zgodnie z tymi krokami, udało Ci się utworzyć tabelę z powtarzającą się sekcją zamapowaną na niestandardową część XML przy użyciu Aspose.Words dla .NET. Umożliwia to dynamiczne generowanie treści na podstawie ustrukturyzowanych danych, dzięki czemu tworzenie dokumentów jest bardziej elastyczne i wydajne.

## Najczęściej zadawane pytania

### Czym jest StructuredDocumentTag (SDT)?
SDT, znany również jako kontrolka zawartości, to ograniczony obszar w dokumencie, który służy do przechowywania ustrukturyzowanych danych.

### Czy mogę używać innych typów danych w niestandardowej części XML?
Tak, możesz utworzyć strukturę własnego pliku XML przy użyciu dowolnych typów danych i odpowiednio je mapować.

### Jak dodać więcej wierszy do sekcji powtarzalnej?
Sekcja powtarzalna automatycznie replikuje strukturę wiersza dla każdego elementu w mapowanej ścieżce XML.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}