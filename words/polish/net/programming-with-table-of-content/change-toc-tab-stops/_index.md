---
"description": "Dowiedz się, jak zmienić tabulatory TOC w dokumentach Worda za pomocą Aspose.Words dla .NET. Ten przewodnik krok po kroku pomoże Ci utworzyć profesjonalnie wyglądający spis treści."
"linktitle": "Zmiana tabulatorów spisu treści w dokumencie Word"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Zmiana tabulatorów spisu treści w dokumencie Word"
"url": "/pl/net/programming-with-table-of-content/change-toc-tab-stops/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zmiana tabulatorów spisu treści w dokumencie Word

## Wstęp

Czy zastanawiałeś się kiedyś, jak urozmaicić spis treści (TOC) w dokumentach Word? Może chcesz, aby tabulatory były idealnie wyrównane, aby uzyskać profesjonalny efekt. Jesteś we właściwym miejscu! Dzisiaj zagłębimy się w to, jak możesz zmienić tabulatory TOC za pomocą Aspose.Words dla .NET. Zostań, a obiecuję, że wyjdziesz z tego ze wszystkimi umiejętnościami, aby Twój spis treści wyglądał elegancko i schludnie.

## Wymagania wstępne

Zanim zaczniemy, upewnijmy się, że masz wszystko, czego potrzebujesz:

1. Aspose.Words dla .NET: Możesz [pobierz tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: Visual Studio lub dowolne środowisko IDE zgodne z C#.
3. Dokument Word: konkretnie taki, który zawiera spis treści.

Zrozumiałeś wszystko? Super! Zaczynajmy.

## Importuj przestrzenie nazw

Po pierwsze, musisz zaimportować niezbędne przestrzenie nazw. To tak, jakbyś pakował swoje narzędzia przed rozpoczęciem projektu.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Podzielmy ten proces na proste, przyswajalne kroki. Przejdziemy przez ładowanie dokumentu, modyfikowanie tabulatorów spisu treści i zapisywanie zaktualizowanego dokumentu.

## Krok 1: Załaduj dokument

Dlaczego? Musimy uzyskać dostęp do dokumentu Word, który zawiera spis treści, który chcemy zmodyfikować.

Jak? Oto prosty fragment kodu, który pomoże Ci zacząć:

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Załaduj dokument zawierający spis treści
Document doc = new Document(dataDir + "Table of contents.docx");
```

Wyobraź sobie, że Twój dokument jest jak ciasto, a my zaraz dodamy trochę lukru. Pierwszym krokiem jest wyjęcie tego ciasta z pudełka.

## Krok 2: Zidentyfikuj akapity spisu treści

Dlaczego? Musimy wskazać akapity, które tworzą spis treści. 

Jak? Przejrzyj akapity i sprawdź ich style:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        // Znaleziono akapit spisu treści
    }
}
```

Wyobraź sobie skanowanie tłumu w poszukiwaniu znajomych. Tutaj szukamy akapitów stylizowanych na wpisy TOC.

## Krok 3: Modyfikowanie tabulatorów

Dlaczego? To właśnie tutaj dzieje się magia. Zmiana tabulatorów nadaje spisowi treści czystszy wygląd.

Jak? Usuń istniejący tabulator i dodaj nowy w zmodyfikowanej pozycji:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        TabStop tab = para.ParagraphFormat.TabStops[0];
        para.ParagraphFormat.TabStops.RemoveByPosition(tab.Position);
        para.ParagraphFormat.TabStops.Add(tab.Position - 50, tab.Alignment, tab.Leader);
    }
}
```

To jak ustawianie mebli w salonie, aż będą idealnie pasować. Dopracowujemy te ograniczniki, aby były idealne.

## Krok 4: Zapisz zmodyfikowany dokument

Dlaczego? Aby mieć pewność, że cała Twoja ciężka praca zostanie zapisana i będzie można ją przeglądać lub udostępniać.

Jak? Zapisz dokument pod nową nazwą, aby zachować oryginał w nienaruszonym stanie:

```csharp
// Zapisz zmodyfikowany dokument
doc.Save(dataDir + "WorkingWithTableOfContent.ChangeTocTabStops.docx");
```

I voila! Twój spis treści ma teraz tabulatory dokładnie tam, gdzie chcesz.

## Wniosek

Zmiana tabulatorów TOC w dokumencie Word przy użyciu Aspose.Words dla .NET jest prosta, gdy już się ją rozłoży. Ładując dokument, identyfikując akapity TOC, modyfikując tabulatory i zapisując dokument, można uzyskać dopracowany i profesjonalny wygląd. Pamiętaj, że praktyka czyni mistrza, więc eksperymentuj z różnymi pozycjami tabulatorów, aby uzyskać dokładnie taki układ, jakiego pragniesz.

## Najczęściej zadawane pytania

### Czy mogę modyfikować tabulatory dla różnych poziomów spisu treści osobno?
Tak, możesz! Wystarczy sprawdzić każdy konkretny poziom TOC (Toc1, Toc2 itd.) i odpowiednio dostosować.

### Co zrobić, jeśli mój dokument ma wiele spisów treści?
Kod skanuje wszystkie akapity ze stylem TOC, więc zmodyfikuje wszystkie spisy treści obecne w dokumencie.

### Czy można dodać wiele tabulatorów do wpisu w spisie treści?
Oczywiście! Możesz dodać tyle tabulatorów, ile potrzebujesz, dostosowując `para.ParagraphFormat.TabStops` kolekcja.

### Czy mogę zmienić wyrównanie tabulatora i styl linii wiodącej?
Tak, możesz określić różne wyrównania i style linii odniesienia podczas dodawania nowego tabulatora.

### Czy potrzebuję licencji, aby używać Aspose.Words dla .NET?
Tak, potrzebujesz ważnej licencji, aby używać Aspose.Words dla .NET po okresie próbnym. Możesz uzyskać [licencja tymczasowa](https://purchase.aspose.com/tempLubary-license/) or [kup jeden](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}