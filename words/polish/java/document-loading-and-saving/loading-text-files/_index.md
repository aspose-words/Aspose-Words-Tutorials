---
date: 2025-12-27
description: Dowiedz się, jak ustawić kierunek, wczytać pliki txt, usunąć spacje i
  konwertować txt na docx przy użyciu Aspose.Words for Java.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Jak ustawić kierunek i wczytać pliki tekstowe przy użyciu Aspose.Words dla
  Javy
url: /pl/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak ustawić kierunek i ładować pliki tekstowe przy użyciu Aspose.Words dla Javy

## Wprowadzenie do ładowania plików tekstowych przy użyciu Aspose.Words dla Javy

W tym przewodniku odkryjesz **how to set direction** podczas ładowania dokumentów tekstowych oraz zobaczysz praktyczne sposoby **load txt**, **trim spaces** i **convert txt to docx** przy użyciu Aspose.Words for Java. Niezależnie od tego, czy tworzysz usługę konwersji dokumentów, czy potrzebujesz precyzyjnej kontroli nad wykrywaniem list, ten tutorial przeprowadzi Cię przez każdy krok z jasnymi wyjaśnieniami i gotowym do uruchomienia kodem.

## Szybkie odpowiedzi
- **Jak ustawić kierunek tekstu dla załadowanego pliku TXT?** Użyj `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` lub określ `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`.
- **Czy Aspose.Words może wykrywać listy numerowane w zwykłym tekście?** Tak – włącz `DetectNumberingWithWhitespaces` w `TxtLoadOptions`.
- **Jak mogę przyciąć początkowe i końcowe spacje?** Ustaw `TxtLeadingSpacesOptions.TRIM` oraz `TxtTrailingSpacesOptions.TRIM`.
- **Czy można skonwertować plik TXT do DOCX w jednej linii?** Załaduj TXT przy użyciu `TxtLoadOptions` i wywołaj `Document.save("output.docx")`.
- **Jaka wersja Javy jest wymagana?** Java 8+ jest wystarczająca dla Aspose.Words 24.x.

## Co to jest „how to set direction” w Aspose.Words?

Gdy plik tekstowy zawiera skrypty od prawej do lewej (np. hebrajski lub arabski), biblioteka musi znać kolejność czytania. Enum `DocumentDirection` pozwala **set direction** ręcznie lub pozwolić Aspose automatycznie wykryć ją, zapewniając prawidłowy układ i formatowanie bidi.

## Dlaczego warto używać Aspose.Words do ładowania plików TXT?

- **Accurate list detection** – obsługuje listy numerowane, wypunktowane i listy oddzielone białymi znakami.
- **Fine‑grained space handling** – przycina lub zachowuje początkowe/końcowe spacje.
- **Automatic text‑direction detection** – idealne dla dokumentów wielojęzycznych.
- **One‑step conversion** – załaduj `.txt` i zapisz jako `.docx`, `.pdf` lub dowolny obsługiwany format.

## Wymagania wstępne
- Java 8 lub nowsza.
- Biblioteka Aspose.Words for Java (dodaj zależność Maven/Gradle lub plik JAR do projektu).
- Podstawowa znajomość strumieni I/O w Javie.

## Przewodnik krok po kroku

### Krok 1: Wykrywanie list (how to load txt)

Aby załadować dokument tekstowy i automatycznie wykrywać listy, utwórz instancję `TxtLoadOptions` i włącz wykrywanie list. Poniższy kod pokazuje kilka stylów list i włącza numerację uwzględniającą białe znaki.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
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
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Pro tip:** Jeśli potrzebujesz tylko podstawowego wykrywania list, możesz pominąć opcję białych znaków – Aspose nadal rozpozna standardowe wzorce `1.` i `1)`.

### Krok 2: Opcje obsługi spacji (how to trim spaces)

Początkowe i końcowe spacje często powodują problemy formatowania. Użyj `TxtLeadingSpacesOptions` i `TxtTrailingSpacesOptions`, aby kontrolować to zachowanie.

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

> **Why it matters:** Przycinanie spacji zapobiega niechcianemu wcięciu w wynikowym DOCX, dzięki czemu dokument wygląda czysto bez ręcznego post‑procesowania.

### Krok 3: Kontrola kierunku tekstu (how to set direction)

Dla języków od prawej do lewej ustaw kierunek dokumentu przed ładowaniem. Poniższy przykład ładuje plik tekstowy w języku hebrajskim i wypisuje flagę bidi, aby potwierdzić kierunek.

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

> **Common pitfall:** Zapomnienie o ustawieniu `DocumentDirection` może prowadzić do zniekształconego tekstu arabskiego/hebrajskiego, gdzie znaki pojawiają się w niewłaściwej kolejności.

### Pełny kod źródłowy do ładowania plików tekstowych przy użyciu Aspose.Words for Java

Poniżej znajduje się pełny, gotowy do uruchomienia kod, który łączy wykrywanie list, obsługę spacji i kontrolę kierunku. Możesz go skopiować i wkleić do jednej klasy oraz uruchomić trzy metody testowe osobno.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
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
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
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

## Typowe problemy i rozwiązania

| Problem | Przyczyna | Rozwiązanie |
|---------|-----------|-------------|
| Listy nie wykryte | `DetectNumberingWithWhitespaces` pozostawiono `false` dla list oddzielonych białymi znakami | Włącz `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| Dodatkowe wcięcie po załadowaniu | Początkowe spacje zostały zachowane | Ustaw `TxtLeadingSpacesOptions.TRIM` |
| Tekst hebrajski wyświetlany odwrócony | Kierunek dokumentu nie ustawiono lub ustawiono na `LEFT_TO_RIGHT` | Użyj `DocumentDirection.AUTO` lub `RIGHT_TO_LEFT` |
| Wyjściowy DOCX jest pusty | Strumień wejściowy nie został zresetowany przed drugim ładowaniem | Utwórz ponownie `ByteArrayInputStream` dla każdego wywołania ładowania |

## Najczęściej zadawane pytania

### Q: Co to jest Aspose.Words for Java?
A: Aspose.Words for Java to potężna biblioteka do przetwarzania dokumentów, która umożliwia programistom tworzenie, modyfikowanie i konwertowanie dokumentów Word programowo w aplikacjach Java. Obsługuje szeroki zakres funkcji, od prostego ładowania tekstu po zaawansowane formatowanie i konwersję.

### Q: Jak mogę rozpocząć pracę z Aspose.Words for Java?
A: 1. Pobierz i zainstaluj bibliotekę Aspose.Words for Java. 2. Zapoznaj się z dokumentacją pod adresem [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) aby uzyskać szczegółowe informacje i przykłady. 3. Przeglądaj przykładowy kod i samouczki, aby nauczyć się efektywnego używania biblioteki.

### Q: Jak załadować dokument tekstowy przy użyciu Aspose.Words for Java?
A: Użyj klasy `TxtLoadOptions` razem z konstruktorem `Document`. Określ opcje takie jak wykrywanie list, obsługa spacji lub kierunek tekstu, jak pokazano w powyższych sekcjach krok po kroku.

### Q: Czy mogę skonwertować załadowany dokument tekstowy do innych formatów?
A: Tak. Po załadowaniu pliku TXT do obiektu `Document` wywołaj `doc.save("output.pdf")`, `doc.save("output.docx")` lub dowolny inny obsługiwany format.

### Q: Jak obsługiwać spacje w załadowanych dokumentach tekstowych?
A: Kontroluj początkowe i końcowe spacje przy użyciu `TxtLeadingSpacesOptions` i `TxtTrailingSpacesOptions`. Ustaw je na `TRIM`, aby usunąć niechciane białe znaki, lub na `PRESERVE`, jeśli potrzebujesz zachować oryginalne odstępy.

### Q: Jakie znaczenie ma kierunek tekstu w Aspose.Words for Java?
A: Kierunek tekstu zapewnia prawidłowe renderowanie skryptów od prawej do lewej (hebrajski, arabski itp.). Ustawiając `DocumentDirection`, gwarantujesz, że tekst bidi będzie wyświetlany poprawnie w wynikowym dokumencie.

### Q: Gdzie mogę znaleźć więcej zasobów i wsparcia dla Aspose.Words for Java?
A: Odwiedź [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) aby uzyskać referencje API, przykłady kodu i szczegółowe przewodniki. Możesz także dołączyć do forów społeczności Aspose lub skontaktować się z pomocą techniczną Aspose w celu uzyskania konkretnych pytań.

### Q: Czy Aspose.Words for Java nadaje się do projektów komercyjnych?
A: Tak. Oferuje opcje licencjonowania zarówno do użytku osobistego, jak i komercyjnego. Przejrzyj warunki licencjonowania na stronie Aspose, aby wybrać odpowiedni plan dla swojego projektu.

## Podsumowanie

Masz teraz kompletny zestaw narzędzi do **load txt files**, **detect lists**, **trim spaces** i **set direction** przy konwertowaniu zwykłego tekstu na bogate dokumenty Word przy użyciu Aspose.Words for Java. Zastosuj te wzorce, aby zautomatyzować przepływy dokumentów, poprawić wsparcie wielojęzyczne i zapewnić czysty, profesjonalny wynik za każdym razem.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}