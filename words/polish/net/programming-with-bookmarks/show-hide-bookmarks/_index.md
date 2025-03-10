---
title: Pokaż Ukryj zakładki w dokumencie programu Word
linktitle: Pokaż Ukryj zakładki w dokumencie programu Word
second_title: Aspose.Words API do przetwarzania dokumentów
description: Dowiedz się, jak dynamicznie wyświetlać lub ukrywać zakładki w dokumencie programu Word za pomocą Aspose.Words dla .NET, korzystając z naszego przewodnika krok po kroku. Idealny dla programistów.
weight: 10
url: /pl/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pokaż Ukryj zakładki w dokumencie programu Word

## Wstęp

Czy kiedykolwiek zdarzyło Ci się, że musiałeś dynamicznie ukrywać lub pokazywać pewne części dokumentu programu Word? Cóż, masz szczęście! Dzięki Aspose.Words dla .NET możesz łatwo zarządzać widocznością treści zakładek w swoich dokumentach. Ten samouczek przeprowadzi Cię przez proces pokazywania i ukrywania zakładek w dokumencie programu Word przy użyciu Aspose.Words dla .NET. Podzielimy kod krok po kroku, więc niezależnie od tego, czy jesteś doświadczonym programistą, czy nowicjuszem, korzystanie z tego przewodnika będzie łatwe.

## Warunki wstępne

Zanim zagłębimy się w kod, upewnijmy się, że masz wszystko, czego potrzebujesz:

1.  Aspose.Words dla .NET: Upewnij się, że masz zainstalowaną bibliotekę Aspose.Words dla .NET. Jeśli nie, możesz go pobrać[Tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: IDE takie jak Visual Studio.
3. Podstawowa znajomość języka C#: Znajomość programowania w języku C# będzie korzystna.
4. Dokument programu Word: przykładowy dokument programu Word z zakładkami.

## Importuj przestrzenie nazw

Przed rozpoczęciem pracy z kodem musisz zaimportować niezbędne przestrzenie nazw. Dodaj następujący wpis na początku pliku C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## Krok 1: Załaduj swój dokument

Najpierw musisz załadować dokument Word zawierający zakładki. Oto jak możesz to zrobić:

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Wyjaśnienie

- dataDir: Jest to ścieżka katalogu, w którym znajduje się dokument programu Word.
-  Dokument dokumentu: inicjuje nową instancję pliku`Document` class z określonym plikiem.

## Krok 2: Pokaż lub ukryj zawartość dodaną do zakładek

Następnie zdefiniujemy metodę pokazywania lub ukrywania zawartości dodanej do zakładek. Oto pełna metoda:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{Zakładka MERGEFIELD}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Wyjaśnienie

- Bookmark bm: Pobiera zakładkę z dokumentu.
- Kreator DocumentBuilder: Pomaga w nawigacji i modyfikowaniu dokumentu.
- Pole pola: Wstawia pole JEŻELI w celu sprawdzenia stanu zakładki.
- Węzeł currentNode: Przechodzi przez węzły, aby znaleźć początek i koniec pola.

## Krok 3: Wykonaj funkcję Pokaż/Ukryj

 Teraz musisz zadzwonić do`ShowHideBookmarkedContent` metodę, przekazując dokument, nazwę zakładki i flagę widoczności:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Wyjaśnienie

- doc: Twój obiekt dokumentu.
- „Moja zakładka1”: nazwa zakładki, którą chcesz pokazać/ukryć.
- false: Flaga widoczności (true dla pokazywania, false dla ukrywania).

## Krok 4: Zapisz swój dokument

Na koniec zapisz zmodyfikowany dokument:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Wyjaśnienie

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": Ścieżka i nazwa nowego dokumentu, w którym zostaną zapisane zmiany.

## Wniosek

I masz to! Pomyślnie nauczyłeś się, jak pokazywać i ukrywać zakładki w dokumencie programu Word przy użyciu Aspose.Words dla .NET. Technika ta może być niezwykle przydatna do dynamicznego generowania dokumentów z zawartością warunkową.

## Często zadawane pytania

### Co to jest Aspose.Words dla .NET?
Aspose.Words dla .NET to potężna biblioteka do przetwarzania dokumentów, która umożliwia programistom programowe tworzenie, modyfikowanie i konwertowanie dokumentów programu Word.

### Jak zdobyć Aspose.Words dla .NET?
 Możesz pobrać Aspose.Words dla .NET z[Tutaj](https://releases.aspose.com/words/net/). Dostępny jest również bezpłatny okres próbny.

### Czy mogę użyć tej metody do innych typów zakładek?
Tak, tę metodę można dostosować do zarządzania widocznością dowolnych zakładek w dokumencie programu Word.

### Co się stanie, jeśli mój dokument nie zawiera określonej zakładki?
Jeśli zakładka nie istnieje, metoda zgłosi błąd. Zanim spróbujesz ją pokazać/ukryć, upewnij się, że zakładka istnieje.

### Jak mogę uzyskać pomoc, jeśli napotkam problemy?
 Możesz uzyskać wsparcie od społeczności Aspose[Tutaj](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
