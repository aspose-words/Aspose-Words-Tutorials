---
title: Spis treści Generowanie
linktitle: Spis treści Generowanie
second_title: Aspose.Words API przetwarzania dokumentów Java
description: Dowiedz się, jak tworzyć dynamiczny spis treści za pomocą Aspose.Words dla Java. Opanuj generowanie spisu treści dzięki wskazówkom krok po kroku i przykładom kodu źródłowego.
weight: 14
url: /pl/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spis treści Generowanie

## Wstęp

Czy kiedykolwiek miałeś problem z utworzeniem dynamicznego i profesjonalnie wyglądającego spisu treści (TOC) w dokumentach Word? Nie szukaj dalej! Dzięki Aspose.Words for Java możesz zautomatyzować cały proces, oszczędzając czas i zapewniając dokładność. Niezależnie od tego, czy tworzysz kompleksowy raport, czy pracę naukową, ten samouczek przeprowadzi Cię przez programowe generowanie spisu treści za pomocą Javy. Gotowy do działania? Zaczynajmy!

## Wymagania wstępne

Zanim zaczniemy kodować, upewnij się, że masz następujące rzeczy:

1.  Java Development Kit (JDK): Zainstalowany w systemie. Możesz go pobrać z[Strona internetowa Oracle](https://www.oracle.com/java/technologies/javase-downloads.html).
2.  Biblioteka Aspose.Words dla Java: Pobierz najnowszą wersję ze strony[strona wydania](https://releases.aspose.com/words/java/).
3. Zintegrowane środowisko programistyczne (IDE): takie jak IntelliJ IDEA, Eclipse lub NetBeans.
4.  Licencja tymczasowa Aspose: Aby uniknąć ograniczeń dotyczących oceny, uzyskaj[licencja tymczasowa](https://purchase.aspose.com/temporary-license/).

## Importuj pakiety

Aby skutecznie używać Aspose.Words dla Java, upewnij się, że importujesz wymagane klasy. Oto importy:

```java
import com.aspose.words.*;
```

Aby wygenerować dynamiczny spis treści w dokumencie Word, wykonaj poniższe czynności.

## Krok 1: Zainicjuj dokument i DocumentBuilder

 Pierwszym krokiem jest utworzenie nowego dokumentu i użycie`DocumentBuilder` klasa, aby nią manipulować.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`:Reprezentuje dokument Word.
- `DocumentBuilder`:Klasa pomocnicza umożliwiająca łatwą manipulację dokumentem.

## Krok 2: Wstaw spis treści

Teraz wstawmy spis treści na początku dokumentu.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: Wstawia pole TOC. Parametry określają:
  - `\o "1-3"`:Uwzględnij nagłówki poziomów od 1 do 3.
  - `\h`:Utwórz wpisy w postaci hiperłączy.
  - `\z`: Wyłącz numerację stron w dokumentach internetowych.
  - `\u`:Zachowaj style hiperłączy.
- `insertBreak`: Dodaje podział strony po spisie treści.

## Krok 3: Dodaj nagłówki, aby wypełnić spis treści

Aby uzupełnić spis treści, należy dodać akapity ze stylami nagłówków.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` : Ustawia styl akapitu na określony poziom nagłówka (np.`HEADING_1`, `HEADING_2`).
- `writeln`: Dodaje do dokumentu tekst o określonym stylu.

## Krok 4: Dodaj zagnieżdżone nagłówki

Aby zademonstrować poziomy spisu treści, należy zastosować zagnieżdżone nagłówki.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Dodaj nagłówki głębszych poziomów, aby pokazać hierarchię w spisie treści.

## Krok 5: Aktualizacja pól spisu treści

Aby wyświetlić najnowsze nagłówki, należy zaktualizować pole spisu treści.


```java
doc.updateFields();
```

- `updateFields`: Odświeża wszystkie pola w dokumencie, zapewniając, że spis treści odzwierciedla dodane nagłówki.

## Krok 6: Zapisz dokument

Na koniec zapisz dokument w wybranym formacie.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save` :Eksportuje dokument do`.docx` plik. Możesz określić inne formaty, takie jak`.pdf` Lub`.txt` jeśli to konieczne.

## Wniosek

Gratulacje! Udało Ci się utworzyć dynamiczny spis treści w dokumencie Word przy użyciu Aspose.Words for Java. Za pomocą zaledwie kilku linijek kodu zautomatyzowałeś zadanie, które w przeciwnym razie mogłoby zająć godziny. Co dalej? Spróbuj poeksperymentować z różnymi stylami i formatami nagłówków, aby dostosować spis treści do konkretnych potrzeb.

## Najczęściej zadawane pytania

### Czy mogę dodatkowo dostosować format spisu treści?
Oczywiście! Możesz dostosować parametry spisu treści, takie jak uwzględnienie numerów stron, wyrównanie tekstu lub użycie niestandardowych stylów nagłówków.

### Czy licencja jest obowiązkowa dla Aspose.Words for Java?
 Tak, licencja jest wymagana do pełnej funkcjonalności. Możesz zacząć od[licencja tymczasowa](https://purchase.aspose.com/temporary-license/).

### Czy mogę wygenerować spis treści dla istniejącego dokumentu?
 Tak! Załaduj dokument do`Document` obiekt i wykonaj te same kroki, aby wstawić i zaktualizować spis treści.

### Czy to działa w przypadku eksportu do pliku PDF?
 Tak, spis treści pojawi się w pliku PDF, jeśli zapiszesz dokument w formacie`.pdf` format.

### Gdzie mogę znaleźć więcej dokumentacji?
 Sprawdź[Aspose.Words dla dokumentacji Java](https://reference.aspose.com/words/java/) aby zobaczyć więcej przykładów i szczegółów.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
