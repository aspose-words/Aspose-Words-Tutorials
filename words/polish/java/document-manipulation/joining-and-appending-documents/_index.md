---
"description": "Dowiedz się, jak bez wysiłku łączyć i dołączać dokumenty za pomocą Aspose.Words for Java. Zachowaj formatowanie, zarządzaj nagłówkami, stopkami i nie tylko."
"linktitle": "Dołączanie i dołączanie dokumentów"
"second_title": "Aspose.Words API przetwarzania dokumentów Java"
"title": "Dołączanie i dołączanie dokumentów w Aspose.Words dla Java"
"url": "/pl/java/document-manipulation/joining-and-appending-documents/"
"weight": 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dołączanie i dołączanie dokumentów w Aspose.Words dla Java


## Wprowadzenie do łączenia i dołączania dokumentów w Aspose.Words dla języka Java

W tym samouczku pokażemy, jak łączyć i dołączać dokumenty za pomocą biblioteki Aspose.Words for Java. Dowiesz się, jak bezproblemowo scalać wiele dokumentów, zachowując formatowanie i strukturę.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że w projekcie Java skonfigurowano Aspose.Words for Java API.

## Opcje łączenia dokumentów

### Proste dołączanie

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Dołącz z opcjami formatu importu

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Dołącz do pustego dokumentu

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Dołącz z konwersją numerów stron

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Konwertuj pola NUMPAGES
dstDoc.updatePageLayout(); // Zaktualizuj układ strony, aby uzyskać prawidłową numerację
```

## Obsługa różnych ustawień strony

Podczas dołączania dokumentów z różnymi ustawieniami strony:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Upewnij się, że ustawienia konfiguracji strony odpowiadają dokumentowi docelowemu
```

## Łączenie dokumentów o różnych stylach

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Zachowanie w stylu Smart

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Wstawianie dokumentów za pomocą DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Zachowanie numeracji źródłowej

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Obsługa pól tekstowych

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Zarządzanie nagłówkami i stopkami

### Łączenie nagłówków i stopek

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Odłączanie nagłówków i stopek

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Wniosek

Aspose.Words for Java zapewnia elastyczne i wydajne narzędzia do łączenia i dołączania dokumentów, niezależnie od tego, czy musisz zachować formatowanie, obsługiwać różne ustawienia stron, czy zarządzać nagłówkami i stopkami. Eksperymentuj z tymi technikami, aby spełnić swoje specyficzne potrzeby w zakresie przetwarzania dokumentów.

## Najczęściej zadawane pytania

### Jak mogę płynnie łączyć dokumenty o różnych stylach?

Aby połączyć dokumenty o różnych stylach, użyj `ImportFormatMode.USE_DESTINATION_STYLES` podczas dołączania.

### Czy mogę zachować numerację stron podczas dołączania dokumentów?

Tak, możesz zachować numerację stron, używając `convertNumPageFieldsToPageRef` metodę i aktualizację układu strony.

### Czym jest Smart Style Behavior?

Smart Style Behavior pomaga zachować spójne style podczas dołączania dokumentów. Używaj go z `ImportFormatOptions` aby uzyskać lepsze wyniki.

### Jak poradzić sobie z polami tekstowymi podczas dołączania dokumentów?

Ustawić `importFormatOptions.setIgnoreTextBoxes(false)` aby uwzględnić pola tekstowe podczas dołączania.

### Co zrobić, jeśli chcę połączyć/odłączyć nagłówki i stopki w różnych dokumentach?

Możesz łączyć nagłówki i stopki za pomocą `linkToPrevious(true)` lub odłącz je od `linkToPrevious(false)` w razie potrzeby.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}