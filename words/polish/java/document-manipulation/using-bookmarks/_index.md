---
date: 2026-01-11
description: Dowiedz się, jak wyświetlać i ukrywać zakładki oraz tworzyć zakładki
  w Javie przy użyciu Aspose.Words for Java, aby efektywnie nawigować i manipulować
  dokumentami.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Pokaż/Ukryj zakładki przy użyciu Aspose.Words dla Javy
url: /pl/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Pokaż i ukryj zakładki w Aspose.Words dla Javy

## Wprowadzenie do używania zakładek w Aspose.Words dla Javy

Zakładki są potężną funkcją w Aspose.Words dla Javy, która pozwala **create bookmark java**, nawigować do określonej treści oraz nawet **show hide bookmarks**, gdy potrzebujesz generować różne wersje dokumentu. W tym przewodniku krok po kroku przeprowadzimy Cię przez tworzenie, dostęp, aktualizację, kopiowanie i przełączanie widoczności zakładek, dając pełną kontrolę nad manipulacją dokumentem.

## Szybkie odpowiedzi
- **What is the primary purpose of bookmarks?** Aby oznaczyć i później odczytać określone części dokumentu.  
- **Can I hide bookmark markers in the final output?** Tak — użyj interfejsu API show/hide, aby przełączać ich widoczność.  
- **How do I create a bookmark inside a table cell?** Rozpocznij i zakończ zakładkę przy użyciu `DocumentBuilder`, gdy kursor znajduje się wewnątrz komórki.  
- **Is it possible to copy bookmarked text to another document?** Oczywiście — użyj `NodeImporter`, aby zachować formatowanie.  
- **What version of Aspose.Words is required?** Dowolna najnowsza wersja; kod działa z najnowszą kompilacją 2026.

## Czym jest „show hide bookmarks”?

Funkcja **show hide bookmarks** pozwala programowo wyświetlać lub ukrywać delimitery zakładek w zapisywanym dokumencie. Jest to przydatne, gdy chcesz generować czysty wynik dla końcowych użytkowników, jednocześnie zachowując dane zakładek do wewnętrznego przetwarzania.

## Dlaczego używać zakładek w automatyzacji dokumentów w Javie?

- **Efficient navigation** – Przejdź bezpośrednio do sekcji bez przeszukiwania całego pliku.  
- **Dynamic content generation** – Wstawiaj, zamieniaj lub usuwaj tekst powiązany z zakładką.  
- **Conditional visibility** – Pokaż lub ukryj znaczniki zakładek w zależności od preferencji użytkownika lub formatu wyjściowego.  
- **Reusability** – Kopiuj fragmenty z zakładkami między dokumentami, zachowując style.

## Wymagania wstępne
- Java Development Kit (JDK) 8 lub nowszy.  
- Biblioteka Aspose.Words for Java dodana do projektu (Maven/Gradle lub JAR).  
- Podstawowa znajomość klas `Document` i `DocumentBuilder`.

## Przewodnik krok po kroku

### Krok 1: Utwórz zakładkę (create bookmark java)

Aby dodać zakładkę, rozpoczynasz ją, zapisujesz treść, a następnie kończysz. Ten przykład tworzy prostą zakładkę o nazwie **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Krok 2: Uzyskaj dostęp do zakładek (access bookmarks java)

Zakładki można pobrać zarówno po ich indeksie zerowym, jak i po nazwie. Poniższy kod demonstruje oba podejścia.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Krok 3: Zaktualizuj dane zakładki (update bookmark text)

Możesz zmienić nazwę zakładki lub zastąpić jej treść tekstową. Jest to przydatne, gdy podstawowy dokument ulega zmianie.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Krok 4: Pracuj z tekstem zakładki (copy bookmarked text)

Kopiowanie fragmentu z zakładką do innego dokumentu przy zachowaniu oryginalnego formatowania jest proste przy użyciu `NodeImporter`.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Krok 5: Pokaż i ukryj zakładki (show hide bookmarks)

Poniższy fragment kodu pokazuje, jak ukryć znaczniki zakładki w zapisywanym pliku. Przekaż `false`, aby ukryć, `true`, aby pokazać.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Krok 6: Rozplącz zakładki wierszy (bookmark table cell)

Gdy zakładki obejmują wiersze tabeli, mogą się splątać. Poniższe metody pomocnicze je rozplątują i pozwalają usunąć konkretny wiersz na podstawie jego zakładki.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Typowe problemy i rozwiązania

| Problem | Rozwiązanie |
|-------|----------|
| **Zakładka nie znaleziona** | Sprawdź, czy nazwa zakładki dokładnie się zgadza (uwzględniając wielkość liter) oraz czy dokument został zapisany po jej utworzeniu. |
| **Skopiowany tekst traci formatowanie** | Użyj `ImportFormatMode.KEEP_SOURCE_FORMATTING` z `NodeImporter`, jak pokazano w Kroku 4. |
| **Pokaż/ukryj nie wpływa na wynik** | Upewnij się, że wywołujesz `showHideBookmarkedContent` **przed** zapisaniem dokumentu. |
| **Zakładka wewnątrz komórki tabeli jest ignorowana** | Umieść wywołania start/end, gdy kursor buildera znajduje się wewnątrz docelowej komórki. |

## Najczęściej zadawane pytania

**Q: Jak utworzyć zakładkę w komórce tabeli?**  
A: Użyj `DocumentBuilder`, aby przenieść kursor do wybranej komórki, a następnie wywołaj `startBookmark` i `endBookmark` wokół zawartości komórki.

**Q: Czy mogę skopiować zakładkę do innego dokumentu?**  
A: Tak — użyj klasy `NodeImporter` (zobacz Krok 4), aby zaimportować węzeł z zakładką, zachowując jego oryginalne formatowanie.

**Q: Jak usunąć wiersz na podstawie jego zakładki?**  
A: Najpierw znajdź wiersz zawierający zakładkę, a następnie wywołaj `remove` na węźle wiersza (jak pokazano w Kroku 6).

**Q: Jakie są typowe zastosowania zakładek?**  
A: Generowanie spisu treści, wyodrębnianie konkretnych sekcji do raportów oraz automatyzacja składania dokumentów na podstawie wyborów użytkownika.

**Q: Gdzie mogę znaleźć więcej informacji o Aspose.Words for Java?**  
A: Szczegółową dokumentację i pliki do pobrania znajdziesz pod adresem [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Ostatnia aktualizacja:** 2026-01-11  
**Testowano z:** Aspose.Words for Java 24.11 (2026)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}