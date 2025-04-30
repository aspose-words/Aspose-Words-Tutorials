---
"date": "2025-03-28"
"description": "Dowiedz się, jak opanować wykrywanie list, obsługę tekstu i wiele więcej, korzystając z Aspose.Words for Java. Ten przewodnik obejmuje wykrywanie list rozdzielonych odstępami, przycinanie spacji, określanie kierunku dokumentu, wyłączanie automatycznego wykrywania numeracji i zarządzanie hiperlinkami."
"title": "Wykrywanie listy głównej i obsługa tekstu w Javie z Aspose.Words&#58; Kompletny przewodnik"
"url": "/pl/java/tables-lists/java-aspose-words-list-detection-text-handling/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Wykrywanie list głównych i obsługa tekstu w Javie z Aspose.Words: kompletny przewodnik

## Wstęp

Praca z dokumentami w postaci zwykłego tekstu często stwarza wyzwania w zakresie identyfikacji ustrukturyzowanych danych, takich jak listy, ze względu na niespójne ograniczniki i problemy z formatowaniem. Biblioteka Aspose.Words for Java zapewnia solidne funkcje do rozwiązywania tych problemów, w tym wykrywanie numeracji z odstępami, przycinanie spacji, określanie kierunku dokumentu, wyłączanie automatycznego wykrywania numeracji i zarządzanie hiperłączami w dokumentach tekstowych. Ten samouczek umożliwia skuteczne manipulowanie danymi tekstowymi za pomocą Aspose.Words.

**Czego się nauczysz:**
- Techniki wykrywania list rozdzielonych odstępami
- Metody usuwania niechcianych spacji z treści dokumentu
- Podejścia do ustalania kierunku odczytu pliku tekstowego
- Sposoby wyłączania automatycznego wykrywania numeracji
- Strategie wykrywania i zarządzania hiperlinkami w dokumentach zwykłego tekstu

Przyjrzyjmy się wymaganiom wstępnym, które należy spełnić przed wdrożeniem tych funkcji.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

### Wymagane biblioteki:
- **Aspose.Words dla Javy**: Wersja 25.3 lub nowsza.

### Konfiguracja środowiska:
- Upewnij się, że Twoje środowisko programistyczne obsługuje Maven lub Gradle, ponieważ są one wymagane do zarządzania zależnościami.

### Wymagania wstępne dotyczące wiedzy:
- Podstawowa znajomość programowania w Javie
- Znajomość systemów kompilacji Maven lub Gradle

## Konfigurowanie Aspose.Words

Aby rozpocząć używanie Aspose.Words dla Java w swoim projekcie, musisz uwzględnić niezbędną zależność. Oto jak to zrobić:

**Maven:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Stopień:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Nabycie licencji

Aby w pełni wykorzystać możliwości Aspose.Words, rozważ nabycie licencji:
- **Bezpłatna wersja próbna**: Dostępne do testowania funkcji.
- **Licencja tymczasowa**:Do celów ewaluacyjnych bez ograniczeń.
- **Zakup**:Pełna licencja do ciągłego użytkowania.

Po uzyskaniu licencji należy ją zainicjować w aplikacji, aby odblokować wszystkie funkcjonalności biblioteki.

## Przewodnik wdrażania

Przyjrzyjmy się bliżej każdej funkcji i zobaczmy, jak ją zaimplementować za pomocą Aspose.Words dla Java.

### Wykrywanie numeracji z odstępami

**Przegląd:** Funkcja ta umożliwia identyfikację list w dokumentach zwykłego tekstu, w których jako ograniczniki używane są spacje.

#### Krok 1: Załaduj dokument
```java
import com.aspose.words.*;

final String TEXT_DOC = "Full stop delimiters:\n" +
    // ...
    "3 Fourth list item 3";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDetectNumberingWithWhitespaces(true);
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
```

#### Krok 2: Sprawdź wykrywanie listy
```java
List<Paragraph> paragraphList = Arrays.stream(doc.getFirstSection().getBody().getParagraphs().toArray())
        .filter(Paragraph.class::isInstance)
        .map(Paragraph.class::cast)
        .collect(Collectors.toList());

boolean detectNumberingWithWhitespaces = true;
if (detectNumberingWithWhitespaces) {
    assert doc.getLists().getCount() == 4 : "Expected four lists.";
    boolean foundFourthList = paragraphList.stream()
        .anyMatch(p -> p.getText().contains("Fourth list") && p.isListItem());
    assert foundFourthList : "Expected to find a fourth list item detected as numbered.";
}
```

*Parametry i metody:*
- `setDetectNumberingWithWhitespaces(true)`: Konfiguruje parser w celu rozpoznawania list z ogranicznikami w postaci spacji.
- `doc.getLists().getCount()`: Pobiera liczbę wykrytych list w dokumencie.

### Przytnij spacje wiodące i końcowe

**Przegląd:** Funkcja ta usuwa zbędne odstępy na początku i na końcu wierszy w dokumentach zwykłego tekstu, zapewniając czyste formatowanie tekstu.

#### Krok 1: Skonfiguruj opcje ładowania
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

String textDoc = "      Line 1 \n" +
    // ...
    " Line 3       ";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);

Document doc = new Document(new ByteArrayInputStream(textDoc.getBytes(StandardCharsets.US_ASCII)), loadOptions);
```

#### Krok 2: Sprawdź przycinanie
```java
ParagraphCollection paragraphs = doc.getFirstSection().getBody().getParagraphs();
for (int i = 0; i < paragraphs.getCount(); i++) {
    Paragraph paragraph = paragraphs.get(i);
    String text = paragraph.getText();
    assert !text.startsWith(" ") : "Expected no leading spaces.";
    assert !text.endsWith(" ") : "Expected no trailing spaces.";
}
```

*Kluczowe konfiguracje:*
- `setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM)`: Przycina spacje na początku wierszy.
- `setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM)`:Usuwa spacje na końcach wierszy.

### Wykryj kierunek dokumentu

**Przegląd:** Określ, czy dokument należy czytać od prawej do lewej (RTL), jak w przypadku tekstu hebrajskiego lub arabskiego.

#### Krok 1: Ustaw automatyczne wykrywanie
```java
TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDocumentDirection(DocumentDirection.AUTO);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Hebrew text.txt", loadOptions);

boolean isBidi = doc.getFirstSection().getBody().getFirstParagraph().getParagraphFormat().isBidi();
assert isBidi : "Expected Hebrew text to be right-to-left.";
```

### Wyłącz automatyczne wykrywanie numeracji

**Przegląd:** Zapobiegaj automatycznemu wykrywaniu i formatowaniu elementów listy przez bibliotekę.

#### Krok 1: Skonfiguruj opcje ładowania
```java
TxtLoadOptions options = new TxtLoadOptions();
options.setAutoNumberingDetection(false);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Number detection.txt", options);

int listItemsCount = 0;
for (Paragraph paragraph : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true)) {
    if (paragraph.isListItem())
        listItemsCount++;
}
assert listItemsCount == 0 : "Expected no detected list items.";
```

### Wykrywaj hiperłącza w tekście

**Przegląd:** Identyfikuj i zarządzaj hiperlinkami w dokumentach w formacie zwykłego tekstu.

#### Krok 1: Ustaw opcje wykrywania
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

final String INPUT_TEXT = "Some links in TXT:\n" +
    // ...
    "https://docs.aspose.com/words/net/";

try (ByteArrayInputStream stream = new ByteArrayInputStream(INPUT_TEXT.getBytes(StandardCharsets.US_ASCII))) {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    loadOptions.setDetectHyperlinks(true);
    Document doc = new Document(stream, loadOptions);

    String[] expectedLinks = {"https://www.aspose.com/”, „https://docs.aspose.com/words/net/”};
    for (int i = 0; i < doc.getRange().getFields().getCount(); i++) {
        String result = doc.getRange().getFields().get(i).getResult().trim();
        assert result.equals(expectedLinks[i]) : "Expected hyperlink does not match.";
    }
}
```

## Zastosowania praktyczne

1. **Systemy zarządzania treścią (CMS):** Automatycznie formatuj treści tworzone przez użytkowników w postaci ustrukturyzowanych list.
2. **Narzędzia do ekstrakcji danych:** Użyj wykrywania list do uporządkowania niestrukturalnych danych na potrzeby analizy.
3. **Przepływy przetwarzania tekstu:** Ulepsz wstępne przetwarzanie dokumentów poprzez przycinanie spacji i wykrywanie kierunku tekstu.

## Rozważania dotyczące wydajności

Aby zoptymalizować wydajność:
- Ładuj dokumenty wykonując minimum czynności i skupiając się na niezbędnych funkcjach.
- Zarządzaj wykorzystaniem pamięci, przetwarzając duże dokumenty w blokach, jeśli jest to możliwe.

## Wniosek

Wykorzystując Aspose.Words for Java, możesz wydajnie zarządzać danymi tekstowymi w dokumentach zwykłego tekstu. Od wykrywania list rozdzielonych odstępami po obsługę kierunku tekstu i hiperłączy, te potężne narzędzia umożliwiają solidną manipulację dokumentami. Aby uzyskać więcej informacji, zapoznaj się z [Dokumentacja Aspose.Words](https://reference.aspose.com/words/java/) lub wypróbuj bezpłatną wersję próbną.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}