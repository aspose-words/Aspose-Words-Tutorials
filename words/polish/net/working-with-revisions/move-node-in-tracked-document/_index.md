---
"description": "Dowiedz się, jak przenosić węzły w śledzonym dokumencie Word za pomocą Aspose.Words dla .NET dzięki naszemu szczegółowemu przewodnikowi krok po kroku. Idealne dla programistów."
"linktitle": "Przenieś węzeł w śledzonym dokumencie"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Przenieś węzeł w śledzonym dokumencie"
"url": "/pl/net/working-with-revisions/move-node-in-tracked-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Przenieś węzeł w śledzonym dokumencie

## Wstęp

Cześć, entuzjaści Aspose.Words! Jeśli kiedykolwiek musieliście przenieść węzeł w dokumencie Word podczas śledzenia rewizji, jesteście we właściwym miejscu. Dzisiaj zagłębimy się w to, jak to osiągnąć za pomocą Aspose.Words dla .NET. Nie tylko nauczycie się procesu krok po kroku, ale także poznacie kilka wskazówek i trików, aby manipulacja dokumentem była płynna i wydajna.

## Wymagania wstępne

Zanim zaczniemy pisać kod, upewnijmy się, że masz wszystko, czego potrzebujesz:

- Aspose.Words dla .NET: Pobierz [Tutaj](https://releases.aspose.com/words/net/).
- Środowisko .NET: Upewnij się, że skonfigurowałeś zgodne środowisko programistyczne .NET.
- Podstawowa wiedza o języku C#: W tym samouczku zakładamy, że posiadasz podstawową wiedzę o języku C#.

Masz wszystko? Świetnie! Przejdźmy do przestrzeni nazw, które musimy zaimportować.

## Importuj przestrzenie nazw

Po pierwsze, musimy zaimportować niezbędne przestrzenie nazw. Są one niezbędne do pracy z Aspose.Words i obsługi węzłów dokumentu.

```csharp
using Aspose.Words;
using System;
```

Dobrze, podzielmy proces na łatwe do opanowania kroki. Każdy krok zostanie szczegółowo wyjaśniony, aby upewnić się, że rozumiesz, co dzieje się w każdym punkcie.

## Krok 1: Zainicjuj dokument

Na początek musimy zainicjować nowy dokument i użyć `DocumentBuilder` aby dodać kilka akapitów.

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Dodanie kilku akapitów
builder.Writeln("Paragraph 1");
builder.Writeln("Paragraph 2");
builder.Writeln("Paragraph 3");
builder.Writeln("Paragraph 4");
builder.Writeln("Paragraph 5");
builder.Writeln("Paragraph 6");

// Sprawdź początkową liczbę akapitów
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Krok 2: Rozpocznij śledzenie wersji

Następnie musimy zacząć śledzić rewizje. Jest to kluczowe, ponieważ pozwala nam zobaczyć zmiany wprowadzone do dokumentu.

```csharp
// Rozpocznij śledzenie rewizji
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## Krok 3: Przenieś węzły

Teraz nadchodzi główna część naszego zadania: przeniesienie węzła z jednej lokalizacji do drugiej. Przeniesiemy trzeci akapit i umieścimy go przed pierwszym akapitem.

```csharp
// Zdefiniuj węzeł, który ma zostać przeniesiony, oraz jego zakres końcowy
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// Przesuń węzły w zdefiniowanym zakresie
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## Krok 4: Zatrzymaj śledzenie wersji

Po przeniesieniu węzłów musimy zatrzymać śledzenie wersji.

```csharp
// Zatrzymaj śledzenie rewizji
doc.StopTrackRevisions();
```

## Krok 5: Zapisz dokument

Na koniec zapiszmy zmodyfikowany dokument w podanym katalogu.

```csharp
// Zapisz zmodyfikowany dokument
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// Wyświetl ostateczną liczbę akapitów
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Wniosek

I masz! Udało Ci się przenieść węzeł w śledzonym dokumencie za pomocą Aspose.Words dla .NET. Ta potężna biblioteka ułatwia programowe manipulowanie dokumentami Word. Niezależnie od tego, czy tworzysz, edytujesz, czy śledzisz zmiany, Aspose.Words ma dla Ciebie rozwiązanie. Więc śmiało, wypróbuj. Miłego kodowania!

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla .NET?

Aspose.Words for .NET to biblioteka klas do pracy z dokumentami Word programowo. Umożliwia ona programistom tworzenie, edycję, konwersję i drukowanie dokumentów Word w aplikacjach .NET.

### Jak śledzić zmiany w dokumencie Word za pomocą Aspose.Words?

Aby śledzić zmiany, użyj `StartTrackRevisions` metoda na `Document` obiekt. Umożliwi to śledzenie rewizji, pokazując wszelkie zmiany wprowadzone do dokumentu.

### Czy mogę przenosić wiele węzłów w Aspose.Words?

Tak, możesz przenosić wiele węzłów, iterując po nich i używając metod takich jak `InsertBefLube` or `InsertAfter` aby umieścić je w wybranym miejscu.

### Jak zatrzymać śledzenie wersji w Aspose.Words?

Użyj `StopTrackRevisions` metoda na `Document` sprzeciwu, aby zaprzestać śledzenia rewizji.

### Gdzie mogę znaleźć więcej dokumentacji na temat Aspose.Words dla .NET?

Szczegółową dokumentację można znaleźć [Tutaj](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}