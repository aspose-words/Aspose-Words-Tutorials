---
"description": "Dowiedz się, jak dodać i dostosować kontrolkę zawartości pola tekstu sformatowanego w dokumencie programu Word za pomocą pakietu Aspose.Words dla platformy .NET, korzystając ze szczegółowego przewodnika krok po kroku."
"linktitle": "Kontrola zawartości pola tekstu sformatowanego"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Kontrola zawartości pola tekstu sformatowanego"
"url": "/pl/net/programming-with-sdt/rich-text-box-content-control/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kontrola zawartości pola tekstu sformatowanego

## Wstęp

W świecie przetwarzania dokumentów możliwość dodawania interaktywnych elementów do dokumentów Word może znacznie zwiększyć ich funkcjonalność. Jednym z takich interaktywnych elementów jest kontrolka zawartości pola tekstu sformatowanego. Używając Aspose.Words dla .NET, możesz łatwo wstawiać i dostosowywać pole tekstu sformatowanego w swoich dokumentach. Ten przewodnik przeprowadzi Cię przez proces krok po kroku, zapewniając, że rozumiesz, jak skutecznie wdrożyć tę funkcję.

## Wymagania wstępne

Zanim przejdziesz do samouczka, upewnij się, że posiadasz następujące elementy:

1. Aspose.Words dla .NET: Upewnij się, że masz zainstalowany Aspose.Words dla .NET. Jeśli jeszcze tego nie zrobiłeś, możesz pobrać go z [Tutaj](https://releases.aspose.com/words/net/).

2. Visual Studio: Środowisko programistyczne, takie jak Visual Studio, pomoże Ci pisać i wykonywać kod.

3. Podstawowa znajomość języka C#: Znajomość języka C# i programowania .NET będzie przydatna, ponieważ będziemy pisać kod w tym języku.

4. .NET Framework: Upewnij się, że Twój projekt jest ukierunkowany na zgodną wersję .NET Framework.

## Importuj przestrzenie nazw

Aby rozpocząć, musisz uwzględnić niezbędne przestrzenie nazw w swoim projekcie C#. Pozwala to na korzystanie z klas i metod dostarczonych przez Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Drawing;
```

Teraz przyjrzymy się bliżej procesowi dodawania kontrolki zawartości pola tekstu sformatowanego do dokumentu Word.

## Krok 1: Określ ścieżkę do katalogu dokumentów

Najpierw określ ścieżkę, w której chcesz zapisać dokument. To tutaj zostanie zapisany wygenerowany plik.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Zastępować `"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką, pod którą chcesz zapisać dokument.

## Krok 2: Utwórz nowy dokument

Utwórz nowy `Document` obiekt, który będzie stanowił podstawę Twojego dokumentu Word.

```csharp
Document doc = new Document();
```

Spowoduje to utworzenie pustego dokumentu Word, do którego można dodać treść.

## Krok 3: Utwórz strukturalny znacznik dokumentu dla tekstu sformatowanego

Aby dodać pole tekstu sformatowanego, należy utworzyć `StructuredDocumentTag` (SDT) typu `RichText`.

```csharp
StructuredDocumentTag sdtRichText = new StructuredDocumentTag(doc, SdtType.RichText, MarkupLevel.Block);
```

Tutaj, `SdtType.RichText` określa, że SDT będzie polem tekstu sformatowanego i `MarkupLevel.Block` definiuje jego zachowanie w dokumencie.

## Krok 4: Dodaj zawartość do pola tekstu sformatowanego

Utwórz `Paragraph` i `Run` obiekt do przechowywania treści, którą chcesz wyświetlić w polu Rich Text Box. Dostosuj tekst i formatowanie według potrzeb.

```csharp
Paragraph para = new Paragraph(doc);
Run run = new Run(doc);
run.Text = "Hello World";
run.Font.Color = Color.Green;
para.Runs.Add(run);
sdtRichText.ChildNodes.Add(para);
```

W tym przykładzie dodajemy akapit zawierający tekst „Witaj świecie” z zieloną czcionką do pola tekstu sformatowanego.

## Krok 5: Dołącz pole tekstu sformatowanego do dokumentu

Dodaj `StructuredDocumentTag` do treści dokumentu.

```csharp
doc.FirstSection.Body.AppendChild(sdtRichText);
```

Ten krok zapewnia uwzględnienie pola tekstu sformatowanego w treści dokumentu.

## Krok 6: Zapisz dokument

Na koniec zapisz dokument w podanym katalogu.

```csharp
doc.Save(dataDir + "WorkingWithSdt.RichTextBoxContentControl.docx");
```

Spowoduje to utworzenie nowego dokumentu Word zawierającego kontrolkę zawartości pola tekstu sformatowanego.

## Wniosek

Dodawanie kontrolki zawartości pola tekstu sformatowanego za pomocą Aspose.Words dla .NET to prosty proces, który zwiększa interaktywność dokumentów Word. Postępując zgodnie z krokami opisanymi w tym przewodniku, możesz łatwo zintegrować pole tekstu sformatowanego ze swoimi dokumentami i dostosować je do swoich potrzeb.

## Najczęściej zadawane pytania

### Czym jest strukturalny znacznik dokumentu (SDT)?
Strukturalny znacznik dokumentu (SDT) to typ kontrolki zawartości w dokumentach programu Word służący do dodawania interaktywnych elementów, takich jak pola tekstowe i listy rozwijane.

### Czy mogę dostosować wygląd pola tekstu sformatowanego?
Tak, możesz dostosować wygląd, modyfikując właściwości `Run` obiekt, taki jak kolor, rozmiar i styl czcionki.

### Jakie inne typy SDT mogę stosować z Aspose.Words?
Oprócz formatu RTF, Aspose.Words obsługuje również inne typy SDT, takie jak zwykły tekst, selektor dat i lista rozwijana.

### Jak dodać wiele pól tekstu sformatowanego do dokumentu?
Możesz utworzyć wiele `StructuredDocumentTag` wystąpienia i dodawać je sekwencyjnie do treści dokumentu.

### Czy mogę używać Aspose.Words do modyfikowania istniejących dokumentów?
Tak, Aspose.Words umożliwia otwieranie, modyfikowanie i zapisywanie istniejących dokumentów Word, w tym dodawanie lub aktualizowanie SDT.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}