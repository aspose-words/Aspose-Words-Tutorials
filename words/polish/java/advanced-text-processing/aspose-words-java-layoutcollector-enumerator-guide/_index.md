---
date: '2025-11-12'
description: Dowiedz się, jak używać LayoutCollector i LayoutEnumerator w Aspose.Words
  for Java do analizy paginacji, przeglądania układu dokumentu, implementacji wywołań
  zwrotnych układu oraz resetowania numeracji stron w sekcjach ciągłych.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- analyze pagination java
- use layoutcollector page span
- traverse document layout
- restart page numbering sections
- implement layout callback
language: pl
title: Analiza paginacji w Javie z narzędziami układu Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Analiza paginacji w Javie przy użyciu narzędzi Layout Aspose.Words

## Wprowadzenie  

Jeśli potrzebujesz **analizować paginację** lub **przeglądać układ dokumentu** w aplikacji Java, Aspose.Words for Java udostępnia dwa potężne API: **`LayoutCollector`** i **`LayoutEnumerator`**. Klasy te pozwalają określić, ile stron zajmuje dany węzeł, przejść przez każdy element układu, reagować na zdarzenia układu oraz ponownie uruchomić numerację stron w sekcjach ciągłych. W tym przewodniku przejdziemy krok po kroku przez każdą funkcję, pokażemy praktyczne fragmenty kodu i wyjaśnimy oczekiwane wyniki, abyś mógł od razu je zastosować.

Nauczysz się:

* **używać LayoutCollector**, aby uzyskać pierwszą i ostatnią stronę dowolnego węzła (use layoutcollector page span)  
* **przeglądać układ dokumentu** za pomocą LayoutEnumerator (traverse document layout)  
* **implementować wywołania zwrotne układu**, aby reagować na zdarzenia paginacji (implement layout callback)  
* **restartować numerację stron** w sekcjach ciągłych (restart page numbering sections)  

Zaczynajmy.

## Wymagania wstępne  

### Wymagane biblioteki  

| Narzędzie budowania | Zależność |
|---------------------|-----------|
| **Maven** | ```xml<br><dependency><groupId>com.aspose</groupId><artifactId>aspose-words</artifactId><version>25.3</version></dependency>``` |
| **Gradle** | ```gradle<br>implementation 'com.aspose:aspose-words:25.3'``` |

> **Uwaga:** Numer wersji jest zachowany ze względu na kompatybilność; kod działa z dowolną aktualną wersją Aspose.Words for Java.

### Środowisko  

* JDK 8 lub nowszy  
* IDE, takie jak IntelliJ IDEA lub Eclipse  

### Wiedza  

Podstawowa znajomość programowania w Javie oraz Maven/Gradle wystarczy, aby podążać za przykładami.

## Konfiguracja Aspose.Words  

Zanim będziesz mógł wywołać dowolne API układu, biblioteka musi być licencjonowana (lub używana w trybie próbnym). Poniższy fragment pokazuje minimalną inicjalizację:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file – skip this line for a trial evaluation
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

*Kod nie modyfikuje żadnego dokumentu; po prostu przygotowuje środowisko Aspose.*  

Teraz możemy przejść do kluczowych funkcji.

## Funkcja 1: Użycie **LayoutCollector** do analizy paginacji  

`LayoutCollector` mapuje każdy węzeł w obiekcie `Document` na strony, które on zajmuje. To najpewniejszy sposób na **use layoutcollector page span** przy analizie paginacji.

### Implementacja krok po kroku  

1. **Utwórz nowy dokument i podłącz LayoutCollector.**  
2. **Wstaw treść wymuszającą podział na strony** (np. podziały stron, podziały sekcji).  
3. **Odśwież układ** przy pomocy `updatePageLayout()`.  
4. **Zapytaj kolektor** o pierwszą stronę, ostatnią stronę i łączną liczbę stron.

#### 1️⃣ Inicjalizacja dokumentu i LayoutCollector  

```java
Document doc = new Document();                 // Empty document
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

#### 2️⃣ Wypełnienie dokumentu  

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

#### 3️⃣ Aktualizacja układu i pobranie metryk  

```java
layoutCollector.clear();          // Reset any previous mappings
doc.updatePageLayout();           // Force pagination calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected: the document occupies 5 pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Oczekiwany wynik**

```
Document spans 5 pages.
```

> **Dlaczego to działa:** `updatePageLayout()` wymusza ponowne obliczenie układu przez Aspose.Words, po czym `LayoutCollector` może dokładnie podać zakresy stron.

## Funkcja 2: Przeglądanie układu dokumentu za pomocą **LayoutEnumerator**  

Gdy potrzebujesz **przeglądać układ dokumentu** (np. w celu własnego renderowania lub analizy), `LayoutEnumerator` udostępnia drzewiastą wizualizację stron, akapitów, linii i słów.

### Implementacja krok po kroku  

1. Wczytaj istniejący dokument zawierający elementy układu.  
2. Utwórz instancję `LayoutEnumerator`.  
3. Przejdź do korzenia – encji `PAGE`.  
4. Przejdź układ do przodu i do tyłu, używając rekurencyjnych metod pomocniczych.

#### 1️⃣ Wczytanie dokumentu i utworzenie enumeratora  

{{CODE