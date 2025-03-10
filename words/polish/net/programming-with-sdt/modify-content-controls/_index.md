---
title: Modyfikuj kontrolki zawartości
linktitle: Modyfikuj kontrolki zawartości
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak modyfikować strukturalne znaczniki dokumentu w programie Word za pomocą Aspose.Words dla .NET. Aktualizuj tekst, listy rozwijane i obrazy krok po kroku.
weight: 10
url: /pl/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Modyfikuj kontrolki zawartości

## Wstęp

Jeśli kiedykolwiek pracowałeś z dokumentami Word i musiałeś zmodyfikować kontrolki zawartości strukturalnej — takie jak zwykły tekst, listy rozwijane lub obrazy — używając Aspose.Words dla .NET, jesteś we właściwym miejscu! Znaczniki strukturalne dokumentu (SDT) to potężne narzędzia, które ułatwiają i uelastyczniają automatyzację dokumentów. W tym samouczku zagłębimy się w to, jak możesz modyfikować te SDT, aby dopasować je do swoich potrzeb. Niezależnie od tego, czy aktualizujesz tekst, zmieniasz wybory rozwijane, czy zamieniasz obrazy, ten przewodnik przeprowadzi Cię przez ten proces krok po kroku.

## Wymagania wstępne

Zanim przejdziemy do szczegółów modyfikacji elementów sterujących treścią, upewnij się, że masz następujące elementy:

1.  Aspose.Words dla .NET zainstalowany: Upewnij się, że masz zainstalowaną bibliotekę Aspose.Words. Jeśli nie, możesz[pobierz tutaj](https://releases.aspose.com/words/net/).

2. Podstawowa wiedza o języku C#: W tym samouczku zakładamy, że znasz podstawowe koncepcje programowania w języku C#.

3. Środowisko programistyczne .NET: konieczne jest skonfigurowanie środowiska IDE, takiego jak Visual Studio, do uruchamiania aplikacji .NET.

4. Przykładowy dokument: Użyjemy przykładowego dokumentu Word z różnymi typami SDT. Możesz użyć tego z przykładu lub utworzyć własny.

5.  Dostęp do dokumentacji Aspose: Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z dokumentacją Aspose.[Dokumentacja Aspose.Words](https://reference.aspose.com/words/net/).

## Importuj przestrzenie nazw

Aby rozpocząć pracę z Aspose.Words, musisz zaimportować odpowiednie przestrzenie nazw do swojego projektu C#. Oto, jak to zrobić:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Te przestrzenie nazw zapewnią Ci dostęp do klas i metod niezbędnych do manipulowania strukturalnymi znacznikami dokumentów w dokumentach Word.

## Krok 1: Ustaw ścieżkę dokumentu

 Przed wprowadzeniem jakichkolwiek zmian musisz określić ścieżkę do swojego dokumentu. Zastąp`"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką, pod którą przechowywany jest Twój dokument.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Krok 2: Przejrzyj ustrukturyzowane znaczniki dokumentu

 Aby zmodyfikować SDT, najpierw musisz przejść przez wszystkie SDT w dokumencie. Robi się to za pomocą`GetChildNodes` metoda pobierania wszystkich węzłów typu`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Modyfikuj SDT na podstawie ich typu
}
```

## Krok 3: Modyfikuj SDT w postaci zwykłego tekstu

Jeśli SDT jest zwykłym tekstem, możesz zastąpić jego zawartość. Najpierw wyczyść istniejącą zawartość, a następnie dodaj nowy tekst.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 Wyjaśnienie: Tutaj,`RemoveAllChildren()`czyści istniejącą zawartość SDT. Następnie tworzymy nową`Paragraph` I`Run` obiekt, aby wstawić nowy tekst.

## Krok 4: Modyfikuj SDT listy rozwijanej

 W przypadku SDT z listy rozwijanej możesz zmienić wybrany element, uzyskując dostęp do`ListItems` kolekcja. Tutaj wybieramy trzeci element na liście.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Wyjaśnienie: Ten fragment kodu wybiera element o indeksie 2 (trzeci element) z listy rozwijanej. Dostosuj indeks zgodnie ze swoimi potrzebami.

## Krok 5: Modyfikuj obraz SDT

Aby zaktualizować obraz w obrazie SDT, możesz zastąpić istniejący obraz nowym.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

 Wyjaśnienie: Ten kod sprawdza, czy kształt zawiera obraz, a następnie zastępuje go nowym obrazem znajdującym się w`ImagesDir`.

## Krok 6: Zapisz zmodyfikowany dokument

Po wprowadzeniu wszystkich niezbędnych zmian zapisz zmodyfikowany dokument pod nową nazwą, aby zachować oryginalny dokument w stanie nienaruszonym.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Wyjaśnienie: Spowoduje to zapisanie dokumentu pod nową nazwą pliku, dzięki czemu będzie można go łatwo odróżnić od oryginału.

## Wniosek

Modyfikowanie kontrolek zawartości w dokumencie Word przy użyciu Aspose.Words dla .NET jest proste, gdy zrozumiesz kroki. Niezależnie od tego, czy aktualizujesz tekst, zmieniasz wybory rozwijane, czy zamieniasz obrazy, Aspose.Words zapewnia solidny interfejs API do tych zadań. Postępując zgodnie z tym samouczkiem, możesz skutecznie zarządzać i dostosowywać ustrukturyzowane kontrolki zawartości dokumentu, dzięki czemu dokumenty będą bardziej dynamiczne i dostosowane do Twoich potrzeb.

## Często zadawane pytania

1. Czym jest strukturalny znacznik dokumentu (SDT)?

SDT to elementy w dokumentach Worda, które pomagają zarządzać zawartością dokumentu, np. polami tekstowymi, listami rozwijanymi i obrazami, oraz ją formatować.

2. Jak mogę dodać nowy element listy rozwijanej do SDT?

 Aby dodać nowy element, użyj`ListItems` właściwość i dołącz nową`SdtListItem` do kolekcji.

3. Czy mogę użyć Aspose.Words do usunięcia SDT z dokumentu?

Tak, możesz usunąć SDT, uzyskując dostęp do węzłów dokumentu i usuwając żądany SDT.

4. Jak obsługiwać SDT zagnieżdżone w innych elementach?

 Użyj`GetChildNodes` metoda z odpowiednimi parametrami umożliwiająca dostęp do zagnieżdżonych SDT.

5. Co powinienem zrobić, jeśli SDT, który muszę zmodyfikować, nie jest widoczny w dokumencie?

Upewnij się, że SDT nie jest ukryty ani chroniony. Sprawdź ustawienia dokumentu i upewnij się, że kod poprawnie kieruje do typu SDT.


### Przykładowy kod źródłowy dla funkcji Modify Content Controls przy użyciu Aspose.Words dla platformy .NET 

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

To wszystko! Udało Ci się zmodyfikować różne typy kontrolek zawartości w dokumencie Word za pomocą Aspose.Words dla .NET.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
