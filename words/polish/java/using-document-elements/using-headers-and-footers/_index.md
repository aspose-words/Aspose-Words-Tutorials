---
"description": "Dowiedz się krok po kroku, jak używać nagłówków i stopek w Aspose.Words dla Java. Twórz profesjonalne dokumenty bez wysiłku."
"linktitle": "Korzystanie z nagłówków i stopek"
"second_title": "Aspose.Words API przetwarzania dokumentów Java"
"title": "Używanie nagłówków i stopek w Aspose.Words dla Java"
"url": "/pl/java/using-document-elements/using-headers-and-footers/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Używanie nagłówków i stopek w Aspose.Words dla Java


W tym kompleksowym przewodniku przeprowadzimy Cię przez proces pracy z nagłówkami i stopkami w Aspose.Words for Java. Nagłówki i stopki są niezbędnymi elementami formatowania dokumentów, a Aspose.Words zapewnia potężne narzędzia do ich tworzenia i dostosowywania zgodnie z Twoimi potrzebami.

Przyjrzyjmy się teraz szczegółowo każdemu z tych kroków.

## 1. Wprowadzenie do Aspose.Words

Aspose.Words to potężne API Java, które umożliwia programowe tworzenie, manipulowanie i renderowanie dokumentów Word. Zapewnia rozbudowane funkcje formatowania dokumentów, w tym nagłówki i stopki.

## 2. Konfigurowanie środowiska Java

Zanim zaczniesz używać Aspose.Words, upewnij się, że Twoje środowisko programistyczne Java jest poprawnie skonfigurowane. Niezbędne instrukcje konfiguracji znajdziesz na stronie dokumentacji Aspose.Words: [Dokumentacja Aspose.Words Java](https://reference.aspose.com/words/java/).

## 3. Tworzenie nowego dokumentu

Aby pracować z nagłówkami i stopkami, musisz utworzyć nowy dokument za pomocą Aspose.Words. Poniższy kod pokazuje, jak to zrobić:

```java
// Kod Java do tworzenia nowego dokumentu
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. Zrozumienie ustawień strony

Ustawienia strony są kluczowe dla kontrolowania układu dokumentu. Możesz określić różne właściwości związane z nagłówkami i stopkami za pomocą `PageSetup` klasa. Na przykład:

```java
// Konfigurowanie właściwości strony
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. Inny nagłówek/stopka pierwszej strony

Aspose.Words pozwala na posiadanie różnych nagłówków i stopek dla pierwszej strony dokumentu. Użyj `pageSetup.setDifferentFirstPageHeaderFooter(true);` aby włączyć tę funkcję.

## 6. Praca z nagłówkami

### 6.1. Dodawanie tekstu do nagłówków

Możesz dodać tekst do nagłówków za pomocą `DocumentBuilder`Oto przykład:

```java
// Dodawanie tekstu do nagłówka pierwszej strony
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. Wstawianie obrazów do nagłówków

Aby wstawić obrazy do nagłówków, możesz użyć `insertImage` metoda. Oto przykład:

```java
// Wstawianie obrazu do nagłówka
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. Dostosowywanie stylów nagłówka

Możesz dostosować style nagłówka, ustawiając różne właściwości, takie jak czcionka, wyrównanie i inne, jak pokazano w powyższych przykładach.

## 7. Praca ze stopkami

### 7.1. Dodawanie tekstu do stopek

Podobnie jak w przypadku nagłówków, do stopek można dodawać tekst za pomocą `DocumentBuilder`Oto przykład:

```java
// Dodawanie tekstu do stopki głównej
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// Wstaw tekst i pola według potrzeb
```

### 7.2. Wstawianie obrazków do stopek

Aby wstawić obrazy do stopek, użyj `insertImage` metody, podobnie jak w nagłówkach.

### 7.3. Dostosowywanie stylów stopki

Dostosuj style stopki za pomocą `DocumentBuilder`, podobnie jak dostosowywanie nagłówków.

## 8. Numerowanie stron

Numery stron można umieszczać w nagłówkach i stopkach za pomocą pól takich jak: `PAGE` I `NUMPAGES`. Pola te są automatycznie aktualizowane w miarę dodawania i usuwania stron.

## 9. Informacje o prawach autorskich w stopkach

Aby dodać informacje o prawach autorskich do stopki dokumentu, możesz użyć tabeli z dwiema komórkami, wyrównując jedną do lewej, a drugą do prawej, jak pokazano we fragmencie kodu.

## 10. Praca z wieloma sekcjami

Aspose.Words umożliwia pracę z wieloma sekcjami w dokumencie. Możesz ustawić różne ustawienia strony i nagłówki/stopki dla każdej sekcji.

## 11. Orientacja pozioma

W razie potrzeby można zmienić orientację poszczególnych sekcji na tryb poziomy.

## 12. Kopiowanie nagłówków/stopek z poprzednich sekcji

Kopiowanie nagłówków i stopek z poprzednich sekcji może zaoszczędzić czas podczas tworzenia złożonych dokumentów.

## 13. Zapisywanie dokumentu

Po utworzeniu i dostosowaniu dokumentu nie zapomnij go zapisać za pomocą `doc.save()` metoda.

## Kompletny kod źródłowy
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // Określ, czy nagłówki/stopki pierwszej strony mają się różnić od nagłówków/stopek pozostałych stron.
        // Można również użyć właściwości PageSetup.OddAndEvenPagesHeaderFooter, aby określić
        // różne nagłówki/stopki dla stron nieparzystych i parzystych.
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        // Wstaw odpowiednio umieszczony obraz w lewym górnym rogu nagłówka.
        // Odległość od górnej/lewej krawędzi strony jest ustawiona na 10 punktów.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // Używamy tabeli składającej się z dwóch komórek, aby utworzyć jedną część tekstu w wierszu (z numeracją stron).
        // Należy wyrównać do lewej, a pozostałą część tekstu (z prawami autorskimi) do prawej.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // Używa pól PAGE i NUMPAGES do automatycznego obliczania numeru bieżącej strony i liczby kolejnych stron.
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        // Utwórz podział strony, aby utworzyć drugą stronę, na której będą widoczne główne nagłówki i stopki.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // Ta sekcja nie wymaga odrębnego nagłówka/stopki na pierwszej stronie, w dokumencie potrzebujemy tylko jednej strony tytułowej,
        // a nagłówek/stopka tej strony została już zdefiniowana w poprzedniej sekcji.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // W tej sekcji wyświetlane są nagłówki/stopki z poprzedniej sekcji
        // domyślnie wywołaj currentSection.HeadersFooters.LinkToPrevious(false), aby anulować tę szerokość strony
        // jest inna dla nowej sekcji, dlatego musimy ustawić różne szerokości komórek dla tabeli stopki.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // Jeśli chcemy wykorzystać już istniejący zestaw nagłówków/stopek dla tej sekcji.
        // Ale po wprowadzeniu drobnych modyfikacji może być wskazane skopiowanie nagłówków i stopek
        // z poprzedniej sekcji i zastosuj niezbędne modyfikacje tam, gdzie ich potrzebujemy.
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
Kod źródłowy metody copyHeadersFootersFromPreviousSection
```java
    /// <podsumowanie>
    //Klonuje i kopiuje nagłówki/stopki z poprzedniej sekcji do określonej sekcji.
    /// </podsumowanie>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## Wniosek

W tym samouczku omówiliśmy podstawy pracy z nagłówkami i stopkami w Aspose.Words for Java. Nauczyłeś się, jak tworzyć, dostosowywać i stylizować nagłówki i stopki, a także innych podstawowych technik formatowania dokumentów.

Więcej szczegółów i zaawansowanych funkcji znajdziesz w [Dokumentacja Aspose.Words Java](https://reference.aspose.com/words/java/).

## Często zadawane pytania

### 1. Jak mogę dodać numery stron do stopki dokumentu?
Możesz dodać numery stron, wstawiając `PAGE` pole do stopki za pomocą Aspose.Words.

### 2. Czy Aspose.Words jest kompatybilny ze środowiskami programistycznymi Java?
Tak, Aspose.Words zapewnia wsparcie dla rozwoju Java. Upewnij się, że masz niezbędne ustawienia.

### 3. Czy mogę dostosować czcionkę i styl nagłówków i stopek?
Oczywiście, możesz dostosować czcionki, wyrównanie i inne style, aby Twoje nagłówki i stopki wyglądały atrakcyjnie.

### 4. Czy możliwe jest ustawienie różnych nagłówków dla stron nieparzystych i parzystych?
Tak, możesz użyć `PageSetup.OddAndEvenPagesHeaderFooter` aby określić różne nagłówki dla stron nieparzystych i parzystych.

### 5. Jak rozpocząć pracę z Aspose.Words dla Java?
Aby rozpocząć, odwiedź [Dokumentacja Aspose.Words Java](https://reference.aspose.com/words/java/) aby uzyskać kompleksowe wskazówki dotyczące korzystania z API.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}