---
"description": "Dowiedz się, jak eksportować dokumenty Word do Markdown z wyrównanymi tabelami przy użyciu Aspose.Words dla .NET. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby uzyskać idealne tabele Markdown."
"linktitle": "Eksportuj do Markdown z wyrównaniem zawartości tabeli"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Eksportuj do Markdown z wyrównaniem zawartości tabeli"
"url": "/pl/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Eksportuj do Markdown z wyrównaniem zawartości tabeli

## Wstęp

Cześć! Czy kiedykolwiek zastanawiałeś się, jak wyeksportować dokument Worda do formatu Markdown z idealnie wyrównanymi tabelami? Niezależnie od tego, czy jesteś programistą pracującym nad dokumentacją, czy po prostu osobą, która uwielbia Markdown, ten przewodnik jest dla Ciebie. Zanurzymy się w szczegółach korzystania z Aspose.Words dla .NET, aby to osiągnąć. Jesteś gotowy, aby zamienić swoje tabele Worda w starannie wyrównane tabele Markdown? Zaczynajmy!

## Wymagania wstępne

Zanim zagłębimy się w kod, jest kilka rzeczy, które musisz mieć na miejscu:

1. Biblioteka Aspose.Words dla .NET: Upewnij się, że masz bibliotekę Aspose.Words dla .NET. Możesz ją pobrać ze strony [Strona wydań Aspose](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: Skonfiguruj swoje środowisko programistyczne. Visual Studio jest popularnym wyborem do programowania .NET.
3. Podstawowa znajomość języka C#: Znajomość języka C# jest niezbędna, ponieważ będziemy pisać kod w tym języku.
4. Przykładowy dokument Word: Przygotuj dokument Word, którego możesz użyć do testów.

## Importuj przestrzenie nazw

Zanim zaczniemy kodować, zaimportujmy niezbędne przestrzenie nazw. Dadzą nam one dostęp do klas i metod Aspose.Words, których będziemy używać.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Zainicjuj dokument i DocumentBuilder

Najpierw musimy utworzyć nowy dokument Word i zainicjować `DocumentBuilder` obiekt, aby rozpocząć tworzenie naszego dokumentu.

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Utwórz nowy dokument.
Document doc = new Document();

// Zainicjuj DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Wstaw komórki i wyrównaj zawartość

Następnie wstawimy kilka komórek do naszego dokumentu i ustawimy ich wyrównanie. Jest to kluczowe dla zapewnienia, że eksport Markdown zachowa prawidłowe wyrównanie.

```csharp
// Wstaw komórkę i ustaw wyrównanie do prawej.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Wstaw kolejną komórkę i ustaw wyrównanie do środka.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Krok 3: Ustaw wyrównanie zawartości tabeli na potrzeby eksportu do formatu Markdown

Teraz czas na konfigurację `MarkdownSaveOptions` aby kontrolować wyrównanie zawartości tabeli w eksportowanym pliku Markdown. Zapiszemy dokument z różnymi ustawieniami wyrównania, aby zobaczyć, jak to działa.

```csharp
// Utwórz obiekt MarkdownSaveOptions.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Zapisz dokument z wyrównaniem do lewej.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Zmień wyrównanie na prawą i zapisz.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Zmień wyrównanie na środek i zapisz.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Krok 4: Użyj automatycznego wyrównywania zawartości tabeli

Ten `Auto` opcja alignment pobiera wyrównanie z pierwszego akapitu w odpowiedniej kolumnie tabeli. Może to być przydatne, gdy masz mieszane wyrównania w jednej tabeli.

```csharp
// Ustaw wyrównanie na Auto.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Zapisz dokument z automatycznym wyrównaniem.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Wniosek

I masz! Eksportowanie dokumentów Word do Markdown z wyrównanymi tabelami przy użyciu Aspose.Words dla .NET jest dziecinnie proste, gdy już wiesz, jak to zrobić. Ta potężna biblioteka ułatwia kontrolowanie formatowania i wyrównania tabel, zapewniając, że dokumenty Markdown wyglądają dokładnie tak, jak chcesz. Miłego kodowania!

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla .NET?
Aspose.Words for .NET to zaawansowana biblioteka umożliwiająca programistom programowe tworzenie, modyfikowanie, konwertowanie i eksportowanie dokumentów Word.

### Czy mogę ustawić różne wyrównania dla różnych kolumn w tej samej tabeli?
Tak, korzystając z `Auto` opcja wyrównania, możesz mieć różne wyrównania na podstawie pierwszego akapitu w każdej kolumnie.

### Czy potrzebuję licencji, aby używać Aspose.Words dla .NET?
Tak, Aspose.Words dla .NET wymaga licencji dla pełnej funkcjonalności. Możesz uzyskać [licencja tymczasowa](https://purchase.aspose.com/temporary-license/) do oceny.

### Czy można eksportować inne elementy dokumentu do Markdown za pomocą Aspose.Words?
Tak, Aspose.Words obsługuje eksportowanie różnych elementów, takich jak nagłówki, listy i obrazy, do formatu Markdown.

### Gdzie mogę uzyskać pomoc, jeśli wystąpią problemy?
Możesz uzyskać wsparcie od [Forum wsparcia Aspose.Words](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}