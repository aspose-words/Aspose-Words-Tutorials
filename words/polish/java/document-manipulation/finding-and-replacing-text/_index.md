---
"description": "Dowiedz się, jak znajdować i zamieniać tekst w dokumentach Word za pomocą Aspose.Words for Java. Przewodnik krok po kroku z przykładami kodu. Udoskonal swoje umiejętności manipulowania dokumentami Java."
"linktitle": "Znajdowanie i zastępowanie tekstu"
"second_title": "Aspose.Words API przetwarzania dokumentów Java"
"title": "Znajdowanie i zamiana tekstu w Aspose.Words dla Java"
"url": "/pl/java/document-manipulation/finding-and-replacing-text/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Znajdowanie i zamiana tekstu w Aspose.Words dla Java


## Wprowadzenie do wyszukiwania i zamiany tekstu w Aspose.Words dla Java

Aspose.Words for Java to potężne API Java, które umożliwia programową pracę z dokumentami Word. Jednym z typowych zadań podczas pracy z dokumentami Word jest wyszukiwanie i zastępowanie tekstu. Niezależnie od tego, czy musisz zaktualizować symbole zastępcze w szablonach, czy wykonać bardziej złożone manipulacje tekstem, Aspose.Words for Java może pomóc Ci skutecznie osiągnąć Twoje cele.

## Wymagania wstępne

Zanim przejdziemy do szczegółów wyszukiwania i zamieniania tekstu, upewnij się, że spełnione są następujące warunki wstępne:

- Środowisko programistyczne Java
- Aspose.Words dla biblioteki Java
- Przykładowy dokument Word do pracy

Bibliotekę Aspose.Words for Java można pobrać ze strony [Tutaj](https://releases.aspose.com/words/java/).

## Znajdowanie i zastępowanie prostego tekstu

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Utwórz DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Znajdź i zamień tekst
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

W tym przykładzie ładujemy dokument Word, tworzymy `DocumentBuilder`i użyj `replace` metoda wyszukiwania i zamiany „starego tekstu” na „nowy tekst” w dokumencie.

## Korzystanie z wyrażeń regularnych

Wyrażenia regularne zapewniają potężne możliwości dopasowywania wzorców do wyszukiwania i zamiany tekstu. Aspose.Words for Java obsługuje wyrażenia regularne do bardziej zaawansowanych operacji wyszukiwania i zamiany.

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Utwórz DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Użyj wyrażeń regularnych do wyszukiwania i zamiany tekstu
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

W tym przykładzie wykorzystujemy wzorzec wyrażenia regularnego w celu znalezienia i zamiany tekstu w dokumencie.

## Ignorowanie tekstu wewnątrz pól

Można skonfigurować Aspose.Words tak, aby ignorował tekst wewnątrz pól podczas wykonywania operacji wyszukiwania i zamiany.

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Utwórz instancję FindReplaceOptions i ustaw IgnoreFields na true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Użyj opcji podczas zastępowania tekstu
doc.getRange().replace("text-to-replace", "new-text", options);

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

Jest to przydatne, gdy chcesz wykluczyć tekst znajdujący się wewnątrz pól, np. pól scalania, z możliwości zastąpienia.

## Ignorowanie tekstu wewnątrz Usuń wersje

Można skonfigurować Aspose.Words tak, aby ignorował tekst wewnątrz usuniętych wersji podczas operacji wyszukiwania i zamiany.

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Utwórz instancję FindReplaceOptions i ustaw IgnoreDeleted na true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Użyj opcji podczas zastępowania tekstu
doc.getRange().replace("text-to-replace", "new-text", options);

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

Umożliwia to wykluczenie tekstu oznaczonego do usunięcia w śledzonych zmianach z zastępowania.

## Ignorowanie tekstu wewnątrz wstawianych wersji

Można skonfigurować Aspose.Words tak, aby ignorował tekst wewnątrz wstawianych wersji podczas operacji wyszukiwania i zamiany.

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Utwórz instancję FindReplaceOptions i ustaw IgnoreInserted na true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Użyj opcji podczas zastępowania tekstu
doc.getRange().replace("text-to-replace", "new-text", options);

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

Umożliwia to wykluczenie tekstu oznaczonego jako wstawiony w śledzonych zmianach z zastępowania.

## Zastępowanie tekstu kodem HTML

Aby zastąpić tekst zawartością HTML, można użyć Aspose.Words for Java.

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Utwórz instancję FindReplaceOptions z niestandardowym wywołaniem zwrotnym zastępowania
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Użyj opcji podczas zastępowania tekstu
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

W tym przykładzie używamy niestandardowego `ReplaceWithHtmlEvaluator` aby zastąpić tekst zawartością HTML.

## Zastępowanie tekstu w nagłówkach i stopkach

Możesz wyszukiwać i zamieniać tekst w nagłówkach i stopkach dokumentu Word.

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Pobierz kolekcję nagłówków i stopek
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Wybierz typ nagłówka lub stopki, w którym chcesz zastąpić tekst (np. HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Utwórz instancję FindReplaceOptions i zastosuj ją do zakresu stopki
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

Umożliwia to dokonywanie zamian tekstu, szczególnie w nagłówkach i stopkach.

## Wyświetlanie zmian w zamówieniach nagłówka i stopki

Za pomocą Aspose.Words możesz pokazać zmiany w kolejności nagłówków i stopek w swoim dokumencie.

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Pobierz pierwszą sekcję
Section firstPageSection = doc.getFirstSection();

// Utwórz instancję FindReplaceOptions i zastosuj ją do zakresu dokumentu
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Zamień tekst, który wpływa na kolejność nagłówków i stopek
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

Umożliwia to wizualizację zmian dotyczących kolejności nagłówków i stopek w dokumencie.

## Zastępowanie tekstu polami

Możesz zastąpić tekst polami korzystając z Aspose.Words dla Java.

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Utwórz instancję FindReplaceOptions i ustaw niestandardową funkcję zwrotną zamiany dla pól
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Użyj opcji podczas zastępowania tekstu
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

W tym przykładzie zastępujemy tekst polami i określamy typ pola (np. `FieldType.FIELD_MERGE_FIELD`).

## Zastępowanie przez ewaluatora

Można użyć niestandardowego narzędzia do dynamicznego określania tekstu zastępczego.

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Utwórz instancję FindReplaceOptions i ustaw niestandardową funkcję zwrotną zamiany
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Użyj opcji podczas zastępowania tekstu
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

W tym przykładzie używamy niestandardowego ewaluatora (`MyReplaceEvaluator`) aby zastąpić tekst.

## Zastępowanie za pomocą Regex

Aspose.Words for Java umożliwia zamianę tekstu za pomocą wyrażeń regularnych.

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Użyj wyrażeń regularnych do wyszukiwania i zamiany tekstu
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

W tym przykładzie wykorzystujemy wzorzec wyrażenia regularnego w celu znalezienia i zamiany tekstu w dokumencie.

## Rozpoznawanie i substytucje w ramach wzorców zastępczych

Za pomocą Aspose.Words for Java możesz rozpoznawać i dokonywać podstawień w obrębie wzorców zamiany.

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Utwórz instancję FindReplaceOptions z opcją UseSubstitutions ustawioną na true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Użyj opcji podczas zastępowania tekstu wzorem
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

Umożliwia to wykonywanie substytucji w obrębie wzorców zamiany w celu wykonania bardziej zaawansowanych zamian.

## Zastępowanie ciągiem znaków

Możesz zastąpić tekst prostym ciągiem znaków korzystając z Aspose.Words dla Java.

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Zamień tekst na ciąg znaków
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

tym przykładzie zastępujemy „text-to-replace” przez „new-string” w dokumencie.

## Korzystanie z zamówienia Legacy

Podczas wykonywania operacji znajdowania i zamieniania można używać starszej kolejności.

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Utwórz instancję FindReplaceOptions i ustaw UseLegacyOrder na true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Użyj opcji podczas zastępowania tekstu
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

Umożliwia to korzystanie ze starszej kolejności operacji wyszukiwania i zamiany.

## Zastępowanie tekstu w tabeli

Możesz wyszukiwać i zamieniać tekst w tabelach w dokumencie Word.

```java
// Załaduj dokument
Document doc = new Document("your-document.docx");

// Pobierz konkretną tabelę (np. pierwszą tabelę)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// Użyj FindReplaceOptions do zamiany tekstu w tabeli
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Zapisz zmodyfikowany dokument
doc.save("modified-document.docx");
```

Umożliwia to wykonywanie zamian tekstu specjalnie w tabelach.

## Wniosek

Aspose.Words for Java oferuje kompleksowe możliwości wyszukiwania i zastępowania tekstu w dokumentach Word. Niezależnie od tego, czy musisz wykonać proste zastąpienia tekstu, czy bardziej zaawansowane operacje przy użyciu wyrażeń regularnych, manipulacji polami lub niestandardowych ewaluatorów, Aspose.Words for Java ma wszystko, czego potrzebujesz. Upewnij się, że zapoznałeś się z obszerną dokumentacją i przykładami dostarczonymi przez Aspose, aby wykorzystać pełny potencjał tej potężnej biblioteki Java.

## Najczęściej zadawane pytania

### Jak pobrać Aspose.Words dla Java?

Możesz pobrać Aspose.Words dla Java ze strony internetowej, odwiedzając [ten link](https://releases.aspose.com/words/java/).

### Czy mogę używać wyrażeń regularnych do zastępowania tekstu?

Tak, możesz używać wyrażeń regularnych do zamiany tekstu w Aspose.Words for Java. Pozwala to na wykonywanie bardziej zaawansowanych i elastycznych operacji wyszukiwania i zamiany.

### Jak mogę ignorować tekst wewnątrz pól podczas zamiany?

Aby zignorować tekst wewnątrz pól podczas zamiany, możesz ustawić `IgnoreFields` własność `FindReplaceOptions` Do `true`Dzięki temu tekst w polach, takich jak pola scalania, nie będzie uwzględniany podczas zamiany.

### Czy mogę zastąpić tekst w nagłówkach i stopkach?

Tak, możesz zastąpić tekst wewnątrz nagłówków i stopek dokumentu Word. Po prostu przejdź do odpowiedniego nagłówka lub stopki i użyj `replace` metoda z pożądanym `FindReplaceOptions`.

### Do czego służy opcja UseLegacyOrder?

Ten `UseLegacyOrder` opcja w `FindReplaceOptions` pozwala na użycie starszej kolejności podczas wykonywania operacji wyszukiwania i zamiany. Może to być przydatne w pewnych scenariuszach, w których pożądane jest starsze zachowanie kolejności.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}