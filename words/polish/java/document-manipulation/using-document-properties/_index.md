---
date: 2026-01-16
description: Dowiedz się, jak przeliczyć cale na punkty, odczytać metadane dokumentu
  w Javie, dodać własne właściwości w Javie oraz ustawić marginesy strony w Javie
  przy użyciu Aspose.Words dla Javy.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: Konwertuj cale na punkty – używając właściwości dokumentu w Aspose.Words dla
  Javy
url: /pl/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Konwertowanie cali na punkty – użycie właściwości dokumentu w Aspose.Words for Java

W tym samouczku dowiesz się, jak **konwertować cale na punkty** przy ustawianiu marginesów strony, odczytywać metadane dokumentu w Javie, dodawać własne właściwości w Javie oraz pracować z wbudowanymi właściwościami dokumentu przy użyciu Aspose.Words for Java. Niezależnie od tego, czy generujesz raporty, faktury, czy dokumenty prawne, opanowanie tych technik daje Ci precyzyjną kontrolę nad wyglądem i metadanymi plików Word.

## Szybkie odpowiedzi
- **Jak konwertować cale na punkty?** Użyj `ConvertUtil.inchToPoint(value)` z Aspose.Words.
- **Czy mogę odczytać metadane dokumentu w Javie?** Tak – wywołaj `doc.getBuiltInDocumentProperties()` lub `doc.getCustomDocumentProperties()`.
- **Jak dodać własną właściwość w Javie?** Użyj `doc.getCustomDocumentProperties().add(name, value)`.
- **Jaką metodę użyć do ustawiania marginesów strony w punktach?** `PageSetup.setTopMargin`, `setBottomMargin` itd., przyjmują wartości w punktach.
- **Czy obsługiwane jest łączenie do zakładki?** Tak – użyj `addLinkToContent` w kolekcji własnych właściwości.

## Wprowadzenie do właściwości dokumentu

Właściwości dokumentu są nieodłącznym elementem każdego pliku Word. Przechowują informacje takie jak tytuł, autor, temat, słowa kluczowe oraz dowolne własne metadane potrzebne do dalszego przetwarzania. W Aspose.Words for Java możesz manipulować zarówno wbudowanymi, jak i własnymi właściwościami dokumentu, a także kontrolować szczegóły układu, takie jak marginesy, konwertując jednostki miary (np. **convert inches to points**).

## Co to jest „convert inches to points”?

W Wordzie pomiary układu wyrażane są w punktach (1 punkt = 1/72 cala). Konwersja cali na punkty pozwala definiować marginesy, wcięcia i odstępy przy użyciu znanych jednostek imperialnych, podczas gdy API wewnętrznie pracuje z punktami.

## Dlaczego zarządzać metadanymi dokumentu w Javie?

Osadzanie metadanych ułatwia wyszukiwanie, kategoryzowanie i automatyzację przepływów pracy. Na przykład możesz oznaczyć umowę flagą „Authorized” lub przechowywać numer wersji dla ścieżek audytu. Odczytywanie i zapisywanie tych informacji programowo zapewnia spójność w dużych partiach dokumentów.

## Wymagania wstępne
- Java 17+ (lub kompatybilny JDK)
- Biblioteka Aspose.Words for Java dodana do projektu (Maven/Gradle)
- Przykładowy plik `.docx` (np. `Properties.docx`) umieszczony w dostępnym katalogu

## Przewodnik krok po kroku

### Enumeracja wbudowanych właściwości dokumentu
Poniżej znajduje się prosty test, który otwiera dokument i wypisuje wszystkie wbudowane właściwości, takie jak Title, Author i Keywords.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Wskazówka:** Użyj tego fragmentu, aby zweryfikować, że Twoje metadane zostały poprawnie zapisane w poprzednich krokach.

### Dodawanie własnych właściwości dokumentu (add custom properties java)
Własne właściwości pozwalają przechowywać dowolny potrzebny typ danych — boolean, string, date, number itp.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Dlaczego to ważne:** Dodanie flagi takiej jak **Authorized** może sterować dalszymi procesami zatwierdzania bez modyfikacji treści dokumentu.

### Usuwanie własnej właściwości
Jeśli właściwość nie jest już potrzebna, możesz ją usunąć w sposób czysty.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Konfigurowanie linku do treści (łączenie zakładek)
Możesz utworzyć zakładkę, a następnie dodać własną właściwość, która wskazuje na tę zakładkę, umożliwiając dynamiczne odwołania krzyżowe.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Konwersja jednostek miary (ustawianie marginesów strony w Javie)
Tutaj pojawia się główne słowo kluczowe. Ustawiamy marginesy w calach, a następnie **konwertujemy cale na punkty** przy użyciu `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Uwaga:** `ConvertUtil` udostępnia także `pointToInch`, `mmToPoint` itp., umożliwiając elastyczną obsługę układu.

### Używanie znaków kontrolnych (read document metadata java)
Znaki kontrolne pomagają w czyszczeniu strumieni tekstu. Ten przykład zamienia powrót karetki (`\r`) na sekwencję zakończenia linii Windows (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Typowe problemy i rozwiązania
| Problem | Przyczyna | Rozwiązanie |
|---------|-----------|-------------|
| Marginesy wyglądają nieprawidłowo po konwersji | Użycie niewłaściwej jednostki (np. cm zamiast cali) | Zweryfikuj, że wywołujesz `ConvertUtil.inchToPoint` dla wartości w calach |
| Własna właściwość nie pojawia się | Właściwość dodana po zapisaniu dokumentu | Wywołaj `doc.save(...)` po dodaniu właściwości |
| Link do zakładki jest uszkodzony | Literówka w nazwie zakładki | Upewnij się, że nazwa zakładki dokładnie odpowiada w `addLinkToContent` |

## FAQ

### Jak uzyskać dostęp do wbudowanych właściwości dokumentu?

Aby uzyskać dostęp do wbudowanych właściwości dokumentu w Aspose.Words for Java, możesz użyć metody `getBuiltInDocumentProperties` na obiekcie `Document`. Metoda ta zwraca kolekcję wbudowanych właściwości, które możesz iterować.

### Czy mogę dodać własne właściwości dokumentu do dokumentu?

Tak, możesz dodać własne właściwości dokumentu przy użyciu kolekcji `CustomDocumentProperties`. Możesz definiować własne właściwości o różnych typach danych, w tym string, boolean, date i wartości numeryczne.

### Jak usunąć konkretną własną właściwość dokumentu?

Aby usunąć konkretną własną właściwość dokumentu, możesz użyć metody `remove` na kolekcji `CustomDocumentProperties`, przekazując nazwę właściwości, którą chcesz usunąć, jako parametr.

### Jaki jest cel łączenia do treści w dokumencie?

Łączenie do treści w dokumencie pozwala tworzyć dynamiczne odwołania do konkretnych części dokumentu. Może to być przydatne przy tworzeniu interaktywnych dokumentów lub odwołań krzyżowych między sekcjami.

### Jak mogę konwertować pomiędzy różnymi jednostkami miary w Aspose.Words for Java?

Możesz konwertować pomiędzy różnymi jednostkami miary w Aspose.Words for Java, używając klasy `ConvertUtil`. Udostępnia ona metody konwersji jednostek, takich jak inches to points, points to centimeters i inne.

## Najczęściej zadawane pytania

**Q: Jak odczytać metadane dokumentu w Javie bez ładowania całego pliku?**  
A: Użyj `DocumentInfo`, aby pobrać podstawowe właściwości bez pełnego ładowania zawartości dokumentu.

**Q: Czy mogę programowo ustawić marginesy strony w Javie dla istniejących dokumentów?**  
A: Tak — otwórz dokument, zmodyfikuj marginesy `PageSetup` (konwertując cale na punkty w razie potrzeby) i zapisz.

**Q: Czy można wyeksportować własne właściwości do metadanych PDF?**  
A: Podczas zapisu do PDF, Aspose.Words automatycznie mapuje własne właściwości dokumentu do własnych metadanych PDF.

**Q: Czy znaki kontrolne wpływają na konwersję do PDF?**  
A: Są zachowywane podczas konwersji; jednak możesz chcieć znormalizować zakończenia linii dla spójności.

**Q: Jakiej wersji Aspose.Words potrzebuję do `ConvertUtil`?**  
A: `ConvertUtil` jest dostępny od wersji Aspose.Words 16.5; każda nowsza wersja go obsługuje.

## Podsumowanie

Opanowując **convert inches to points**, odczytywanie metadanych dokumentu w Javie oraz dodawanie własnych właściwości w Javie, zyskujesz pełną kontrolę zarówno nad wizualnym układem, jak i ukrytymi danymi swoich plików Word. Te możliwości pozwalają budować zautomatyzowane pipeline’y dokumentów, egzekwować zgodność i tworzyć bogato sformatowane raporty — wszystko przy użyciu Aspose.Words for Java.

---

**Last Updated:** 2026-01-16  
**Tested With:** Aspose.Words for Java 24.11  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}