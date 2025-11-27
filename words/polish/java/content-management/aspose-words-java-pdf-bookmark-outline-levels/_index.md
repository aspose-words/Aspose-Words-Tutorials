---
date: '2025-11-27'
description: Dowiedz się, jak tworzyć zakładki, generować PDF z zakładkami oraz konwertować
  Word na PDF w Javie przy użyciu Aspose.Words. Ten przewodnik obejmuje zagnieżdżone
  zakładki i poziomy konspektu.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
language: pl
title: Jak tworzyć zakładki i ustawiać poziomy konspektu w plikach PDF przy użyciu
  Aspose.Words Java
url: /java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak tworzyć zakładki i ustawiać poziomy konspektu w plikach PDF przy użyciu Aspose.Words Java

## Wprowadzenie
Jeśli kiedykolwiek miałeś problem z **tworzeniem zakładek**, które pozostają uporządkowane podczas konwertowania dokumentu Word do PDF, jesteś we właściwym miejscu. W tym samouczku przeprowadzimy Cię przez cały proces generowania PDF z zakładkami, ich zagnieżdżania oraz przypisywania poziomów konspektu, aby ostateczny PDF był łatwy w nawigacji. Po zakończeniu będziesz w stanie **konwertować Word do PDF w stylu Java** z czystą hierarchią zakładek, działającą w każdym przeglądarce PDF.

### Co się nauczysz
- Skonfiguruj Aspose.Words dla Java w swoim środowisku programistycznym.  
- **Jak programowo tworzyć zakładki** i je zagnieżdżać.  
- Skonfiguruj poziomy konspektu zakładek, aby wygenerować PDF z zakładkami odzwierciedlającymi strukturę dokumentu.  
- Zapisz plik Word jako PDF, zachowując hierarchię zakładek.

## Szybkie odpowiedzi
- **Jaka jest podstawowa klasa do budowania dokumentów?** `DocumentBuilder`.  
- **Która opcja kontroluje hierarchię zakładek?** `BookmarksOutlineLevelCollection` w `PdfSaveOptions`.  
- **Czy mogę używać Maven lub Gradle?** Tak – oba są pokazane poniżej.  
- **Czy potrzebna jest licencja?** Darmowa wersja próbna działa do testów; stała licencja jest wymagana w produkcji.  
- **Czy to podejście jest odpowiednie dla dużych dokumentów?** Tak, ale rozważ techniki optymalizacji pamięci (np. usuwanie nieużywanych zasobów).

### Wymagania wstępne
Przed rozpoczęciem upewnij się, że masz:

- **Biblioteki i zależności** – Aspose.Words dla Java (25.3 lub nowsza).  
- **Środowisko** – JDK 8 lub nowszy oraz IDE, takie jak IntelliJ IDEA lub Eclipse.  
- **Podstawowa wiedza** – podstawy programowania w Javie oraz znajomość Maven lub Gradle.

## Konfiguracja Aspose.Words
Aby rozpocząć, dołącz niezbędne zależności do swojego projektu. Oto jak możesz dodać Aspose.Words przy użyciu Maven lub Gradle:

**Maven:**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Uzyskanie licencji
Aspose.Words jest komercyjną biblioteką, ale możesz zacząć od darmowej wersji próbnej:

1. **Darmowa wersja próbna** – Pobierz ze [strony wydania Aspose](https://releases.aspose.com/words/java/).  
2. **Licencja tymczasowa** – Złóż wniosek na [stronie licencji tymczasowej](https://purchase.aspose.com/temporary-license/), jeśli potrzebujesz krótkoterminowego klucza.  
3. **Pełna licencja** – Kup przez [portal zakupowy Aspose](https://purchase.aspose.com/buy) do użytku produkcyjnego.

Po uzyskaniu pliku licencji, załaduj go przy uruchamianiu aplikacji, aby odblokować wszystkie funkcje.

## Jak tworzyć zakładki w PDF przy użyciu Aspose.Words Java
Poniżej dzielimy implementację na przejrzyste, numerowane kroki. Każdy krok zawiera krótkie wyjaśnienie, a następnie oryginalny blok kodu (bez zmian).

### Krok 1: Zainicjuj dokument i DocumentBuilder
Zaczynamy od nowej instancji `Document` oraz `DocumentBuilder`, które pozwalają wstawiać treść i zakładki.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Krok 2: Wstaw pierwszą (główną) zakładkę
Utwórz zakładkę najwyższego poziomu, która później będzie zawierać zakładkę podrzędną.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

### Krok 3: Zagnieźdź zakładkę podrzędną wewnątrz głównej
Teraz dodajemy drugą zakładkę, która znajduje się wewnątrz pierwszej, demonstrując zagnieżdżanie.

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

### Krok 4: Zamknij główną zakładkę
Zakończ zewnętrzną zakładkę po zawartości zagnieżdżonej.

```java
builder.endBookmark("Bookmark 1");
```

### Krok 5: Dodaj niezależną trzecią zakładkę
Zawsze możesz dodać kolejne zakładki, które nie są zagnieżdżone.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## Konfigurowanie poziomów konspektu zakładek
Po umieszczeniu zakładek informujemy Aspose.Words, jak mają one wyglądać w konspekcie PDF (lewy panel nawigacyjny).

### Krok 6: Przygotuj PdfSaveOptions
`PdfSaveOptions` daje dostęp do ustawień konspektu.

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

### Krok 7: Przypisz poziomy hierarchii
Każda zakładka otrzymuje liczbę całkowitą; niższe liczby oznaczają wyższy poziom w hierarchii.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

### Krok 8: Zapisz dokument jako PDF
Na koniec wyeksportuj dokument Word do PDF, zachowując konspekt zakładek.

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Dlaczego warto używać tego podejścia do generowania PDF z zakładkami?
- **Profesjonalna nawigacja** – Czytelnicy mogą przechodzić bezpośrednio do sekcji, zwiększając użyteczność dużych raportów lub umów prawnych.  
- **Pełna kontrola** – To Ty decydujesz o hierarchii, nie przeglądarka PDF.  
- **Wieloplatformowość** – Działa tak samo na Windows, Linux i macOS, ponieważ jest czystą Javą.  

## Typowe problemy i rozwiązania
| Objaw | Prawdopodobna przyczyna | Rozwiązanie |
|---|---|---|
| Brak zakładek w PDF | `startBookmark` bez pasującego `endBookmark` | Sprawdź, czy każdy `startBookmark` ma odpowiadający `endBookmark`. |
| Nieprawidłowa hierarchia | Poziomy konspektu przypisane w niewłaściwej kolejności | Upewnij się, że zakładki nadrzędne mają niższe numery poziomów niż ich podrzędne. |
| Licencja nie zastosowana | Plik licencji nie został załadowany przed utworzeniem dokumentu | Załaduj licencję na samym początku aplikacji (`License license = new License(); license.setLicense("Aspose.Words.lic");`). |

## Praktyczne zastosowania
1. **Dokumenty prawne** – Szybko nawiguj po klauzulach, załącznikach i dodatkach.  
2. **Raporty finansowe** – Przejdź między sekcjami takimi jak Rachunek zysków i strat, Bilans i Notatki.  
3. **Materiały e‑learningowe** – Zapewnij spis treści odzwierciedlający konspekt PDF.  

## Rozważania dotyczące wydajności
- **Zarządzanie pamięcią** – Dla bardzo dużych plików Word rozważ wywołanie `doc.cleanup()` przed zapisem.  
- **Optymalizacja zasobów** – Usuń nieużywane obrazy lub style, aby utrzymać mały rozmiar PDF.  

## Najczęściej zadawane pytania

**P: Jak zainstalować Aspose.Words dla Java?**  
O: Dodaj zależność Maven lub Gradle pokazane wcześniej, następnie umieść plik licencji w classpath i załaduj go w czasie działania.

**P: Czy mogę tworzyć zakładki bez ustawiania poziomów konspektu?**  
O: Tak, ale przeglądarka PDF wyświetli je jako płaską listę, co może być trudne do nawigacji w złożonych dokumentach.

**P: Czy istnieje limit głębokości zagnieżdżania zakładek?**  
O: Technicznie nie, ale większość przeglądarek PDF obsługuje komfortowo do 9 poziomów. Zachowaj logiczną hierarchię dla czytelników.

**P: Jak Aspose radzi sobie z bardzo dużymi plikami Word?**  
O: Biblioteka strumieniuje zawartość i udostępnia metody takie jak `Document.optimizeResources()`, aby zmniejszyć zużycie pamięci.

**P: Czy mogę edytować zakładki po wygenerowaniu PDF?**  
O: Oczywiście – możesz użyć Aspose.PDF dla Java, aby dodać, usunąć lub zmienić nazwę zakładek w istniejącym PDF.

## Zasoby
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)  
- [Download Latest Releases](https://releases.aspose.com/words/java/)  
- [Purchase a License](https://purchase.aspose.com/buy)  
- [Free Trial](https://releases.aspose.com/words/java/)  
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)  
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Ostatnia aktualizacja:** 2025-11-27  
**Testowano z:** Aspose.Words 25.3 for Java  
**Autor:** Aspose