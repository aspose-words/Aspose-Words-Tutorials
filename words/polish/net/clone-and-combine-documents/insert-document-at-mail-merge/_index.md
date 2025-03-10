---
title: Wstaw dokument do korespondencji seryjnej
linktitle: Wstaw dokument do korespondencji seryjnej
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak wstawiać dokumenty w polach korespondencji seryjnej za pomocą Aspose.Words for .NET, korzystając z tego kompleksowego samouczka krok po kroku.
weight: 10
url: /pl/net/clone-and-combine-documents/insert-document-at-mail-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw dokument do korespondencji seryjnej

## Wstęp

Witamy w świecie automatyzacji dokumentów z Aspose.Words dla .NET! Czy kiedykolwiek zastanawiałeś się, jak dynamicznie wstawiać dokumenty do określonych pól w dokumencie głównym podczas operacji korespondencji seryjnej? Cóż, jesteś we właściwym miejscu. Ten samouczek przeprowadzi Cię krok po kroku przez proces wstawiania dokumentów do pól korespondencji seryjnej przy użyciu Aspose.Words dla .NET. To jak układanie puzzli, w których każdy element idealnie pasuje do siebie. Więc zanurzmy się!

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

1.  Aspose.Words dla .NET: Możesz[pobierz najnowszą wersję tutaj](https://releases.aspose.com/words/net/) . Jeśli potrzebujesz kupić licencję, możesz to zrobić[Tutaj](https://purchase.aspose.com/buy) Alternatywnie możesz otrzymać[licencja tymczasowa](https://purchase.aspose.com/temporary-license/) lub wypróbuj z[bezpłatny okres próbny](https://releases.aspose.com/).
2. Środowisko programistyczne: Visual Studio lub inne środowisko IDE C#.
3. Podstawowa znajomość języka C#: Znajomość programowania w języku C# sprawi, że zapoznanie się z tym kursem będzie proste.

## Importuj przestrzenie nazw

Po pierwsze, musisz zaimportować niezbędne przestrzenie nazw. Są one jak podstawowe elementy Twojego projektu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Podzielmy proces na łatwe do opanowania kroki. Każdy krok będzie bazował na poprzednim, prowadząc do kompletnego rozwiązania.

## Krok 1: Konfigurowanie katalogu

Zanim zaczniesz wstawiać dokumenty, musisz zdefiniować ścieżkę do katalogu dokumentów. To tutaj przechowywane są Twoje dokumenty.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Ładowanie dokumentu głównego

Następnie załadujesz dokument główny. Ten dokument zawiera pola scalania, w których zostaną wstawione inne dokumenty.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Krok 3: Ustawianie wywołania zwrotnego scalania pól

Aby obsłużyć proces scalania, musisz ustawić funkcję wywołania zwrotnego. Ta funkcja będzie odpowiedzialna za wstawianie dokumentów w określonych polach scalania.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Krok 4: Wykonywanie korespondencji seryjnej

Teraz czas na wykonanie korespondencji seryjnej. To tutaj dzieje się magia. Określisz pole korespondencji seryjnej i dokument, który powinien zostać wstawiony w tym polu.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Krok 5: Zapisywanie dokumentu

Po zakończeniu korespondencji seryjnej zapiszesz zmodyfikowany dokument. Ten nowy dokument będzie miał wstawioną treść dokładnie tam, gdzie chcesz.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## Krok 6: Tworzenie programu obsługi wywołań zwrotnych

Obsługujący wywołanie zwrotne to klasa, która wykonuje specjalne przetwarzanie dla pola scalania. Ładuje dokument określony w wartości pola i wstawia go do bieżącego pola scalania.

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## Krok 7: Wkładanie dokumentu

Ta metoda wstawia określony dokument do bieżącego akapitu lub komórki tabeli.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## Wniosek

I masz to! Udało Ci się wstawić dokumenty do określonych pól podczas operacji korespondencji seryjnej przy użyciu Aspose.Words dla .NET. Ta potężna funkcja może zaoszczędzić Ci mnóstwo czasu i wysiłku, zwłaszcza przy pracy z dużymi wolumenami dokumentów. Pomyśl o tym jak o osobistym asystencie, który wykona za Ciebie całą ciężką robotę. Więc śmiało, spróbuj. Miłego kodowania!

## Najczęściej zadawane pytania

### Czy mogę wstawić wiele dokumentów w różnych polach scalania?
Tak, możesz. Wystarczy określić odpowiednie pola scalania i odpowiadające im ścieżki dokumentów w`MailMerge.Execute` metoda.

### Czy istnieje możliwość sformatowania wstawionego dokumentu inaczej niż dokumentu głównego?
 Oczywiście! Możesz użyć`ImportFormatMode` parametr w`NodeImporter` aby kontrolować formatowanie.

### A co jeśli nazwa pola scalania jest dynamiczna?
Można obsługiwać dynamiczne nazwy pól scalania, przekazując je jako parametry do funkcji obsługi wywołania zwrotnego.

### Czy mogę stosować tę metodę do różnych formatów plików?
Tak, Aspose.Words obsługuje różne formaty plików, w tym DOCX, PDF i inne.

### Jak postępować w przypadku błędów podczas wstawiania dokumentu?
Zaimplementuj obsługę błędów w programie obsługi wywołań zwrotnych, aby zarządzać wszelkimi wyjątkami, które mogą wystąpić.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
