---
title: Wstaw dokument podczas zastępowania
linktitle: Wstaw dokument podczas zastępowania
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak bezproblemowo wstawiać jeden dokument Word do drugiego za pomocą Aspose.Words dla .NET dzięki naszemu szczegółowemu przewodnikowi krok po kroku. Idealne dla programistów, którzy chcą usprawnić przetwarzanie dokumentów.
weight: 10
url: /pl/net/clone-and-combine-documents/insert-document-at-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw dokument podczas zastępowania

## Wstęp

Hej, mistrzowie dokumentów! Czy zdarzyło ci się kiedyś utknąć po kolana w kodzie, próbując rozgryźć, jak bezproblemowo wstawić jeden dokument Worda do drugiego? Nie martw się, ponieważ dziś zanurzamy się w świecie Aspose.Words dla .NET, aby ułatwić to zadanie. Przeprowadzimy Cię przez szczegółowy przewodnik krok po kroku, jak używać tej potężnej biblioteki do wstawiania dokumentów w określonych punktach podczas operacji znajdowania i zamieniania. Jesteś gotowy, aby zostać czarodziejem Aspose.Words? Zaczynajmy!

## Wymagania wstępne

Zanim przejdziemy do kodu, jest kilka rzeczy, które musisz mieć na miejscu:

-  Visual Studio: Upewnij się, że masz zainstalowane na swoim komputerze Visual Studio. Jeśli jeszcze go nie masz, możesz go pobrać z[Tutaj](https://visualstudio.microsoft.com/).
-  Aspose.Words dla .NET: Będziesz potrzebować biblioteki Aspose.Words. Możesz ją pobrać z[Strona internetowa Aspose](https://releases.aspose.com/words/net/).
- Podstawowa wiedza o języku C#: Podstawowa znajomość języka C# i .NET ułatwi Ci korzystanie z tego samouczka.

Dobra, skoro to już za nami, zajmijmy się kodowaniem!

## Importuj przestrzenie nazw

Po pierwsze, musimy zaimportować niezbędne przestrzenie nazw, aby pracować z Aspose.Words. To tak, jakbyś zebrał wszystkie swoje narzędzia przed rozpoczęciem projektu. Dodaj te dyrektywy using na górze swojego pliku C#:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

Teraz, gdy mamy już nasze warunki wstępne, podzielmy proces na małe kroki. Każdy krok jest kluczowy i przybliży nas do celu.

## Krok 1: Konfigurowanie katalogu dokumentów

Najpierw musimy określić katalog, w którym przechowywane są nasze dokumenty. To jak przygotowanie sceny przed wielkim występem.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Zastępować`"YOUR DOCUMENT DIRECTORY"` ze ścieżką do Twojego katalogu. To tutaj Twoje dokumenty będą żyć i oddychać.

## Krok 2: Załaduj dokument główny

Następnie ładujemy główny dokument, do którego chcemy wstawić inny dokument. Pomyśl o tym jako o naszej głównej scenie, gdzie będzie się działo cała akcja.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

Ten kod ładuje dokument główny ze wskazanego katalogu.

## Krok 3: Ustaw opcje Znajdź i zamień

Aby znaleźć konkretną lokalizację, w której chcemy wstawić nasz dokument, używamy funkcji „znajdź i zamień”. Jest to jak użycie mapy, aby znaleźć dokładne miejsce dla naszego nowego dodatku.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

Tutaj ustawiamy kierunek na wsteczny i określamy niestandardową funkcję obsługi wywołania zwrotnego, którą zdefiniujemy później.

## Krok 4: Wykonaj operację zamiany

Teraz polecamy naszemu dokumentowi głównemu wyszukanie konkretnego tekstu zastępczego i zastąpienie go niczym, a jednocześnie użycie naszego niestandardowego wywołania zwrotnego w celu wstawienia innego dokumentu.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Ten kod wykonuje operację znalezienia i zamiany, a następnie zapisuje zaktualizowany dokument.

## Krok 5: Utwórz niestandardowy zastępczy program obsługi wywołań zwrotnych

Nasz niestandardowy program obsługi wywołań zwrotnych to miejsce, w którym dzieje się magia. Ten program obsługi określi, w jaki sposób wstawianie dokumentu jest wykonywane podczas operacji znajdowania i zamieniania.

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // Wstaw dokument po akapicie zawierającym tekst dopasowania.
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // Usuń akapit zawierający pasujący tekst.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

Tutaj ładujemy dokument, który ma zostać wstawiony, a następnie wywołujemy metodę pomocniczą, aby wykonać wstawianie.

## Krok 6: Zdefiniuj metodę wstawiania dokumentu

Ostatnim elementem naszej układanki jest metoda, która faktycznie wstawia dokument w określonym miejscu.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // Sprawdź, czy miejscem docelowym wstawiania jest akapit czy tabela
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // Utwórz NodeImporter, aby zaimportować węzły z dokumentu źródłowego
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // Przejdź przez wszystkie węzły na poziomie bloku w sekcjach dokumentu źródłowego
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // Pomiń ostatni pusty akapit sekcji
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // Zaimportuj i wstaw węzeł do miejsca docelowego
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

Ta metoda polega na importowaniu węzłów z dokumentu, które mają zostać wstawione, i umieszczaniu ich we właściwym miejscu w dokumencie głównym.

## Wniosek

oto masz! Kompleksowy przewodnik po wstawianiu jednego dokumentu do drugiego za pomocą Aspose.Words dla .NET. Postępując zgodnie z tymi krokami, możesz łatwo zautomatyzować zadania składania i manipulacji dokumentami. Niezależnie od tego, czy budujesz system zarządzania dokumentami, czy po prostu musisz usprawnić przepływ pracy przetwarzania dokumentów, Aspose.Words jest Twoim zaufanym pomocnikiem.

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla .NET?
Aspose.Words for .NET to potężna biblioteka do programowego manipulowania dokumentami Word. Umożliwia łatwe tworzenie, modyfikowanie, konwertowanie i przetwarzanie dokumentów Word.

### Czy mogę wstawić kilka dokumentów jednocześnie?
Tak, można zmodyfikować procedurę obsługi wywołań zwrotnych, aby obsługiwała wielokrotne wstawianie, poprzez iterowanie po kolekcji dokumentów.

### Czy jest dostępna bezpłatna wersja próbna?
 Oczywiście! Możesz pobrać bezpłatną wersję próbną z[Tutaj](https://releases.aspose.com/).

### Jak uzyskać pomoc techniczną dotyczącą Aspose.Words?
 Możesz uzyskać pomoc odwiedzając stronę[Forum Aspose.Words](https://forum.aspose.com/c/words/8).

### Czy mogę zachować formatowanie wstawionego dokumentu?
 Tak,`NodeImporter` Klasa ta umożliwia określenie sposobu obsługi formatowania podczas importowania węzłów z jednego dokumentu do drugiego.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
