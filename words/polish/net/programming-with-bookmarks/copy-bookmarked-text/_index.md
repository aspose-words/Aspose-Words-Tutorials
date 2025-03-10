---
title: Kopiuj zakładkę do tekstu w dokumencie Word
linktitle: Kopiuj zakładkę do tekstu w dokumencie Word
second_title: Aspose.Words API przetwarzania dokumentów
description: Bez wysiłku kopiuj zakładki tekstowe między dokumentami Word za pomocą Aspose.Words dla .NET. Dowiedz się, jak to zrobić dzięki temu przewodnikowi krok po kroku.
weight: 10
url: /pl/net/programming-with-bookmarks/copy-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kopiuj zakładkę do tekstu w dokumencie Word

## Wstęp

Czy zdarzyło Ci się kiedyś, że musiałeś skopiować określone sekcje z jednego dokumentu Word do drugiego? Cóż, masz szczęście! W tym samouczku pokażemy Ci, jak skopiować tekst z zakładkami z jednego dokumentu Word do drugiego przy użyciu Aspose.Words dla .NET. Niezależnie od tego, czy tworzysz dynamiczny raport, czy automatyzujesz generowanie dokumentów, ten przewodnik uprości Ci ten proces.

## Wymagania wstępne

Zanim przejdziemy do konkretów, upewnij się, że masz następujące rzeczy:

-  Biblioteka Aspose.Words dla .NET: Można ją pobrać ze strony[Tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne: Visual Studio lub inne środowisko programistyczne .NET.
- Podstawowa znajomość języka C#: Znajomość programowania w języku C# i środowiska .NET.

## Importuj przestrzenie nazw

Na początek upewnij się, że w projekcie zaimportowano niezbędne przestrzenie nazw:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## Krok 1: Załaduj dokument źródłowy

Najpierw musisz załadować dokument źródłowy zawierający zapisany w zakładkach tekst, który chcesz skopiować.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

 Tutaj,`dataDir` jest ścieżką do katalogu dokumentów i`Bookmarks.docx` jest dokumentem źródłowym.

## Krok 2: Zidentyfikuj zakładkę

Następnie zidentyfikuj zakładkę, którą chcesz skopiować z dokumentu źródłowego.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

 Zastępować`"MyBookmark1"` z rzeczywistą nazwą zakładki.

## Krok 3: Utwórz dokument docelowy

Teraz utwórz nowy dokument, do którego zostanie skopiowany zaznaczony tekst.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## Krok 4: Importuj zakładkę z treścią

 Aby mieć pewność, że style i formatowanie zostaną zachowane, użyj`NodeImporter` aby zaimportować dodaną do zakładek zawartość z dokumentu źródłowego do dokumentu docelowego.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## Krok 5: Zdefiniuj metodę AppendBookmarkedText

Tutaj dzieje się magia. Zdefiniuj metodę obsługi kopiowania tekstu z zakładką:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## Krok 6: Zapisz dokument docelowy

Na koniec zapisz dokument docelowy, aby sprawdzić skopiowaną zawartość.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Wniosek

I to wszystko! Udało Ci się skopiować zakładkę tekstu z jednego dokumentu Word do drugiego za pomocą Aspose.Words dla .NET. Ta metoda jest skuteczna w automatyzowaniu zadań związanych z manipulacją dokumentami, dzięki czemu Twój przepływ pracy jest bardziej wydajny i usprawniony.

## Najczęściej zadawane pytania

### Czy mogę skopiować wiele zakładek jednocześnie?
Tak, możesz przeglądać wiele zakładek i używać tej samej metody do kopiowania każdej z nich.

### Co się stanie, jeśli zakładka nie zostanie znaleziona?
 Ten`Range.Bookmarks` nieruchomość powróci`null`, więc upewnij się, że zajmiesz się tym przypadkiem, aby uniknąć wyjątków.

### Czy mogę zachować formatowanie oryginalnej zakładki?
 Oczywiście! Używam`ImportFormatMode.KeepSourceFormatting` zapewnia zachowanie oryginalnego formatowania.

### Czy istnieje ograniczenie rozmiaru tekstu dodawanego do zakładek?
Nie ma konkretnego limitu, ale wydajność może się różnić w przypadku bardzo dużych dokumentów.

### Czy mogę kopiować tekst pomiędzy różnymi formatami dokumentów Word?
Tak, Aspose.Words obsługuje różne formaty Worda, a opisana metoda działa w przypadku wszystkich tych formatów.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
