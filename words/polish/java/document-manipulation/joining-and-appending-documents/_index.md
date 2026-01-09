---
date: 2026-01-09
description: Dowiedz się, jak scalać dokumenty przy użyciu Aspose.Words for Java,
  zachowując formatowanie, łącząc nagłówki i stopki oraz inne funkcje.
linktitle: Joining and Appending Documents
second_title: Aspose.Words Java Document Processing API
title: Jak scalić dokumenty przy użyciu Aspose.Words dla Javy
url: /pl/java/document-manipulation/joining-and-appending-documents/
weight: 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak scalać dokumenty przy użyciu Aspose.Words for Java

Łączenie plików Word programowo może być uciążliwe — szczególnie gdy trzeba zachować style, numery stron oraz nagłówki/stopki w nienaruszonym stanie. W tym samouczku odkryjesz **jak scalać dokumenty** przy użyciu biblioteki Aspose.Words for Java, krok po kroku. Omówimy proste dołączanie, zaawansowane opcje importu, obsługę różnych ustawień stron oraz triki potrzebne do **zachowania formatowania przy scalaniu** wyników w różnych scenariuszach rzeczywistych.

## Szybkie odpowiedzi
- **Jaki jest najprostszy sposób na scalenie dokumentów Word?** Użyj `Document.appendDocument` z `ImportFormatMode.KEEP_SOURCE_FORMATTING`.  
- **Czy mogę zachować oryginalne style każdego pliku źródłowego?** Tak — ustaw `ImportFormatMode.USE_DESTINATION_STYLES` lub włącz Smart Style Behavior.  
- **Jak utrzymać poprawne numery stron po scaleniu?** Przekonwertuj pola `NUMPAGES` na odwołania do stron i wywołaj `updatePageLayout()`.  
- **Czy nagłówki i stopki pozostają automatycznie połączone?** Możesz je połączyć lub rozłączyć przy użyciu `linkToPrevious(true/false)`.  
- **Czego potrzebuję przed rozpoczęciem?** Dodaj Aspose.Words for Java do swojego projektu oraz przygotuj pliki źródłowe `.docx`.

## Wprowadzenie do łączenia i dołączania dokumentów w Aspose.Words for Java

W tym samouczku przyjrzymy się, jak łączyć i dołączać dokumenty przy użyciu biblioteki Aspose.Words for Java. Dowiesz się, jak płynnie scalać wiele dokumentów, zachowując formatowanie i strukturę.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że API Aspose.Words for Java jest skonfigurowane w Twoim projekcie Java.

## Opcje łączenia dokumentów

### Proste dołączanie

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Dołączanie z opcjami formatu importu

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Dołączanie do pustego dokumentu

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Dołączanie z konwersją numerów stron

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Convert NUMPAGES fields
dstDoc.updatePageLayout(); // Update page layout for correct numbering
```

## Obsługa różnych ustawień stron

Podczas dołączania dokumentów o różnych ustawieniach stron:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Ensure page setup settings match the destination document
```

## Łączenie dokumentów o różnych stylach

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Zachowanie inteligentnych stylów

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Wstawianie dokumentów przy użyciu DocumentBuilder

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

### Rozłączanie nagłówków i stopek

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Dlaczego ma to znaczenie dla projektów „merge word documents java”

Gdy potrzebujesz **scalać dokumenty Word w stylu java**, zachowanie wyglądu i charakteru każdego pliku jest kluczowe w procesach prawnych, wydawniczych lub raportowych. Stosowanie powyższych technik zapewnia, że:
* Style z każdego źródła pozostają nienaruszone (lub są ujednolicone, w zależności od wyboru).  
* Numeracja stron i podziały sekcji zachowują się przewidywalnie.  
* Nagłówki i stopki mogą być połączone lub pozostawione niezależne przy użyciu jednej linii kodu.  

## Częste pułapki i wskazówki

| Problem | Dlaczego się dzieje | Jak naprawić |
|-------|----------------|------------|
| Utracona numeracja po scaleniu | Pola `NUMPAGES` nadal wskazują na oryginalne sekcje | Wywołaj `convertNumPageFieldsToPageRef` i `updatePageLayout()` |
| Konflikt stylów | Użycie `KEEP_SOURCE_FORMATTING` przy konfliktowych stylach | Przejdź na `USE_DESTINATION_STYLES` lub włącz Smart Style Behavior |
| Pojawiają się puste strony | Różne wartości `SectionStart` | Ustaw `SectionStart.CONTINUOUS` w sekcjach źródłowych przed dołączeniem |

## Najczęściej zadawane pytania

**Q: Jak mogę płynnie połączyć dokumenty o różnych stylach?**  
A: Użyj `ImportFormatMode.USE_DESTINATION_STYLES` przy dołączaniu lub włącz `SmartStyleBehavior` dla inteligentniejszego scalania.

**Q: Czy mogę zachować numerację stron przy dołączaniu dokumentów?**  
A: Tak, skonwertuj pola `NUMPAGES` na odwołania do stron przy użyciu `convertNumPageFieldsToPageRef`, a następnie wywołaj `updatePageLayout()`.

**Q: Czym jest Smart Style Behavior?**  
A: Automatycznie mapuje style źródłowe na style docelowe, gdy to możliwe, pomagając utrzymać spójny wygląd połączonej treści.

**Q: Jak obsłużyć pola tekstowe przy dołączaniu dokumentów?**  
A: Ustaw `importFormatOptions.setIgnoreTextBoxes(false)`, aby pola tekstowe były zachowane podczas scalania.

**Q: Co zrobić, jeśli chcę połączyć lub rozłączyć nagłówki i stopki między dokumentami?**  
A: Użyj `linkToPrevious(true)`, aby połączyć, lub `linkToPrevious(false)`, aby pozostawić je oddzielnie przed wywołaniem `appendDocument`.

## Zakończenie

Aspose.Words for Java oferuje elastyczne i potężne narzędzia do **scalania dokumentów**, niezależnie od tego, czy musisz zachować dokładne formatowanie, obsłużyć różnorodne ustawienia stron, czy kontrolować łączenie nagłówków/stopki. Eksperymentuj z powyższymi fragmentami kodu, aby dopasować je do swojego konkretnego przepływu przetwarzania dokumentów, i będziesz w stanie **scalać dokumenty Word w stylu java** z pewnością.

---

**Ostatnia aktualizacja:** 2026-01-09  
**Testowano z:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}