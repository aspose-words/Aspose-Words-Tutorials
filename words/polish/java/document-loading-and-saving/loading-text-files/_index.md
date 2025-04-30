---
"description": "Odblokuj moc Aspose.Words dla Javy. Naucz się ładować dokumenty tekstowe, zarządzać listami, obsługiwać spacje i kontrolować kierunek tekstu."
"linktitle": "Ładowanie plików tekstowych za pomocą"
"second_title": "Aspose.Words API przetwarzania dokumentów Java"
"title": "Ładowanie plików tekstowych za pomocą Aspose.Words dla Java"
"url": "/pl/java/document-loading-and-saving/loading-text-files/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ładowanie plików tekstowych za pomocą Aspose.Words dla Java


## Wprowadzenie do ładowania plików tekstowych za pomocą Aspose.Words dla Java

W tym przewodniku pokażemy, jak ładować pliki tekstowe za pomocą Aspose.Words for Java i manipulować nimi jako dokumentami Word. Omówimy różne aspekty, takie jak wykrywanie list, obsługa spacji i kontrolowanie kierunku tekstu.

## Krok 1: Wykrywanie list

Aby załadować dokument tekstowy i wykryć listy, wykonaj następujące kroki:

```java
// Utwórz dokument tekstowy w formie ciągu znaków zawierającego części, które można interpretować jako listy.
// Po załadowaniu pierwsze trzy listy będą zawsze wykrywane przez Aspose.Words,
// a po załadowaniu zostaną dla nich utworzone obiekty listy.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// Czwarta lista, z odstępem pomiędzy numerem listy a zawartością elementu listy,
// zostanie wykryty jako lista tylko wtedy, gdy „DetectNumberingWithWhitespaces” w obiekcie LoadOptions zostanie ustawiony na true,
// aby uniknąć sytuacji, w której akapity zaczynające się od liczb zostaną omyłkowo uznane za listy.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Załaduj dokument, stosując LoadOptions jako parametr i sprawdź wynik.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

Ten kod pokazuje, jak załadować dokument tekstowy z różnymi formatami list i użyć `DetectNumberingWithWhitespaces` opcja umożliwiająca prawidłowe wykrywanie list.

## Krok 2: Opcje obsługi przestrzeni

Aby kontrolować spacje na początku i na końcu podczas ładowania dokumentu tekstowego, możesz użyć następującego kodu:

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

W tym przykładzie ładujemy dokument tekstowy i przycinamy spacje początkowe i końcowe za pomocą `TxtLeadingSpacesOptions.TRIM` I `TxtTrailingSpacesOptions.TRIM`.

## Krok 3: Kontrola kierunku tekstu

Aby określić kierunek tekstu podczas ładowania dokumentu tekstowego, możesz użyć następującego kodu:

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

Ten kod ustawia kierunek dokumentu na automatyczne wykrywanie (`DocumentDirection.AUTO`) i ładuje dokument tekstowy z tekstem hebrajskim. Możesz dostosować kierunek dokumentu według potrzeb.

## Kompletny kod źródłowy do ładowania plików tekstowych za pomocą Aspose.Words dla Java

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Utwórz dokument tekstowy w formie ciągu znaków zawierającego części, które można interpretować jako listy.
	// Po załadowaniu pierwsze trzy listy będą zawsze wykrywane przez Aspose.Words,
	// a po załadowaniu zostaną dla nich utworzone obiekty listy.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// Czwarta lista, z odstępem pomiędzy numerem listy a zawartością elementu listy,
	// zostanie wykryty jako lista tylko wtedy, gdy „DetectNumberingWithWhitespaces” w obiekcie LoadOptions zostanie ustawiony na true,
	// aby uniknąć sytuacji, w której akapity zaczynające się od liczb zostaną omyłkowo uznane za listy.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Załaduj dokument, stosując LoadOptions jako parametr i sprawdź wynik.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Wniosek

W tym przewodniku przyjrzeliśmy się sposobom ładowania plików tekstowych za pomocą Aspose.Words for Java, wykrywania list, obsługi spacji i kontrolowania kierunku tekstu. Te techniki pozwalają na efektywne manipulowanie dokumentami tekstowymi w aplikacjach Java.

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla języka Java?

Aspose.Words for Java to potężna biblioteka przetwarzania dokumentów, która umożliwia programistom tworzenie, manipulowanie i konwertowanie dokumentów Word programowo w aplikacjach Java. Zapewnia szeroki zakres funkcji do pracy z tekstem, tabelami, obrazami i innymi elementami dokumentu.

### Jak mogę rozpocząć pracę z Aspose.Words dla Java?

Aby rozpocząć korzystanie z Aspose.Words dla Java, wykonaj następujące kroki:
1. Pobierz i zainstaluj bibliotekę Aspose.Words for Java.
2. Zapoznaj się z dokumentacją pod adresem [Aspose.Words dla Java API Reference](https://reference.aspose.com/words/java/) aby uzyskać szczegółowe informacje i przykłady.
3. Zapoznaj się z przykładowym kodem i samouczkami, aby dowiedzieć się, jak efektywnie korzystać z biblioteki.

### Jak wczytać dokument tekstowy za pomocą Aspose.Words dla Java?

Aby załadować dokument tekstowy za pomocą Aspose.Words dla Java, możesz użyć `TxtLoadOptions` klasa i `Document` class. Upewnij się, że określiłeś odpowiednie opcje obsługi spacji i kierunku tekstu, jeśli to konieczne. Zapoznaj się z przewodnikiem krok po kroku w tym artykule, aby uzyskać szczegółowy przykład.

### Czy mogę przekonwertować załadowany dokument tekstowy do innych formatów?

Tak, Aspose.Words for Java pozwala na konwersję załadowanego dokumentu tekstowego do różnych formatów, w tym DOCX, PDF i innych. Możesz użyć `Document` klasa do wykonywania konwersji. Sprawdź dokumentację pod kątem konkretnych przykładów konwersji.

### Jak radzić sobie ze spacjami w załadowanych dokumentach tekstowych?

Możesz kontrolować sposób obsługi spacji początkowych i końcowych w załadowanych dokumentach tekstowych za pomocą `TxtLoadOptions`Opcje takie jak `TxtLeadingSpacesOptions` I `TxtTrailingSpacesOptions` pozwalają przycinać lub zachowywać spacje w razie potrzeby. Przykład można znaleźć w sekcji „Opcje obsługi spacji” w tym przewodniku.

### Jakie jest znaczenie kierunku tekstu w Aspose.Words dla Java?

Kierunek tekstu jest istotny dla dokumentów zawierających mieszane skrypty lub języki, takie jak hebrajski lub arabski. Aspose.Words for Java udostępnia opcje określania kierunku tekstu, zapewniając prawidłowe renderowanie i formatowanie tekstu w tych językach. Sekcja „Kontrolowanie kierunku tekstu” w tym przewodniku pokazuje, jak ustawić kierunek tekstu.

### Gdzie mogę znaleźć więcej materiałów i pomocy dla Aspose.Words dla Java?

Aby uzyskać dodatkowe zasoby, dokumentację i pomoc, odwiedź stronę [Aspose.Words dla dokumentacji Java](https://reference.aspose.com/words/java/). Możesz również uczestniczyć w forach społeczności Aspose.Words lub skontaktować się z pomocą techniczną Aspose, aby uzyskać pomoc w konkretnych problemach lub zapytaniach.

### Czy Aspose.Words for Java nadaje się do projektów komercyjnych?

Tak, Aspose.Words for Java nadaje się zarówno do projektów osobistych, jak i komercyjnych. Oferuje opcje licencjonowania, aby dostosować się do różnych scenariuszy użytkowania. Upewnij się, że zapoznałeś się z warunkami licencjonowania i cenami na stronie internetowej Aspose, aby wybrać odpowiednią licencję dla swojego projektu.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}