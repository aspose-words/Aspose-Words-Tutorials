---
category: general
date: 2026-08-07
description: Utwórz pusty dokument Word z grupowanymi kształtami w Javie przy użyciu
  Aspose.Words. Dowiedz się, jak grupować kształty, ustawiać ich rozmiar i dodawać
  kształty do Worda.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: pl
lastmod: 2026-08-07
og_description: Utwórz pusty dokument Word z grupowanymi kształtami w Javie. Skorzystaj
  z tego przewodnika, aby ustawić rozmiar kształtu, dodać kształty do Worda i opanować,
  jak grupować kształty.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Utwórz pusty dokument Word z grupowanymi kształtami – samouczek Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Utwórz pusty dokument Word z grupowanymi kształtami w Javie
url: /pl/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz pusty dokument Word z grupowanymi kształtami w Javie

Jeśli potrzebujesz **create blank Word document**, który zawiera kilka kształtów ułożonych jako jedna jednostka, ten tutorial pokaże Ci dokładnie, jak to zrobić. Zobaczysz kompletny, gotowy do uruchomienia przykład, który demonstruje **how to group shape** obiekty, dostosowuje ich wymiary oraz **add shapes to Word** przy użyciu Aspose.Words for Java.

Poradnik przechodzi przez każdy krok — od konfiguracji projektu po zapisanie końcowego pliku .docx — abyś mógł skopiować kod bezpośrednio do własnej aplikacji. Nie są wymagane żadne zewnętrzne odwołania, a rozwiązanie działa z Aspose.Words 23.9 lub nowszą wersją.

## Wymagania wstępne

* Java 17 (lub dowolny obsługiwany JDK)
* Maven lub Gradle do zarządzania zależnościami
* Licencja Aspose.Words for Java (lub tymczasowy klucz ewaluacyjny)
* Przykładowy plik obrazu (np. `sample.jpg`) umieszczony w znanym katalogu

Jeśli którekolwiek z tych elementów brakuje, zainstaluj je najpierw; reszta tutorialu zakłada, że środowisko jest gotowe.

## Krok 1: Dodaj Aspose.Words do swojego projektu

Dodaj zależność Aspose.Words do swojego `pom.xml` (Maven) lub `build.gradle` (Gradle). Ta biblioteka dostarcza klasy `Document`, `DocumentBuilder`, `GroupShape` i `Shape` używane później.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Dlaczego to ważne:** Bez tej biblioteki żadne API do przetwarzania Word nie jest dostępne i nie możesz **create blank Word document** programowo.

## Krok 2: Utwórz pusty dokument Word

Pierwszym konkretnym działaniem jest utworzenie obiektu `Document`, który reprezentuje **blank Word document** w pamięci.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* tworzy **blank Word document** z ustawieniami domyślnymi (strona A4, domyślne marginesy). Towarzyszący `DocumentBuilder` pozwala wstawiać zawartość w bieżącej pozycji kursora.

## Krok 3: Wstaw grupowy kształt (how to group shape)

*group shape* działa jako kontener dla innych kształtów. W tym kroku nauczysz się **how to group shape** obiektów, aby poruszały się razem.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

Metoda `insertGroupShape` umieszcza kontener w miejscu kursora buildera. Grupowanie jest niezbędne, gdy chcesz traktować wiele rysunków jako jedną jednostkę — to jest sedno funkcjonalności **group shapes word**.

## Krok 4: Utwórz prostokąt i ustaw jego rozmiar

Teraz dodaj prostokąt do grupy. To demonstruje **set shape size**, co jest niezbędne do precyzyjnego układu.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Dlaczego ustawiać wymiary?* Jawne wywołanie `setWidth` i `setHeight` zapewnia, że prostokąt pojawi się dokładnie tak, jak zamierzono, niezależnie od domyślnych stylów kształtów w dokumencie.

## Krok 5: Wstaw obraz i dodaj go do grupy

Dodanie obrazu pokazuje kolejny typowy przypadek użycia **add shapes to word**. Obraz staje się częścią tej samej grupy, poruszając się razem z prostokątem.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Jeśli plik obrazu jest nieobecny, Aspose.Words zgłasza wyjątek. Praktyczna wskazówka: sprawdź ścieżkę wcześniej:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Krok 6: Zapisz dokument zawierający grupowane kształty

Na koniec zapisz **blank Word document** (teraz wypełniony grupowanym kształtem) na dysku.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Gdy otworzysz `GroupShapeDemo.docx` w Microsoft Word, zobaczysz pojedynczy grupowany obiekt, który zawiera prostokąt i obraz. Wybranie dowolnej części grupy przesuwa cały kontener, potwierdzając, że kształty zostały poprawnie **grouped**.

### Oczekiwany wynik

* Plik o nazwie `GroupShapeDemo.docx` w określonym katalogu.
* Otwierając plik, zobaczysz kontener 300 × 200 punktów z:
  * Prostokątem 100 × 50 punktów umieszczonym w (20, 20).
  * Obrazem umieszczonym w (150, 30) wewnątrz tego samego kontenera.

## Przypadki brzegowe i warianty

| Sytuacja | Jak sobie radzić |
|-----------|-----------------|
| **Różny rozmiar strony** | Wywołaj `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` przed wstawieniem grupy. |
| **Wiele grup** | Powtórz kroki 3‑5 z nową instancją `GroupShape`; każda grupa może być pozycjonowana niezależnie. |
| **Obracanie kształtów** | Użyj `shape.setRotationAngle(45.0);` aby obrócić prostokąt lub obraz przed dodaniem go do grupy. |
| **Kształty nie‑obrazowe** | Utwórz obiekty `Shape` typu `ShapeType.ELLIPSE`, `ShapeType.LINE` itp., i dołącz je tak jak prostokąt. |
| **Duże obrazy** | Skaluj obraz za pomocą `picture.setWidth(80.0); picture.setHeight(60.0);` aby utrzymać grupę w jej pierwotnych granicach. |

## Praktyczne wskazówki z doświadczenia

* **Pro tip:** Ustaw `RelativeHorizontalPosition` i `RelativeVerticalPosition` grupy na `RelativeHorizontalPosition.PAGE` oraz `RelativeVerticalPosition.PAGE`, jeśli chcesz, aby grupa była przytwierdzona do strony, a nie do kursora.
* **Watch out for:** Dodanie kształtu, który przekracza wymiary grupy; kształt zostanie przycięty w Wordzie. Dostosuj rozmiar grupy za pomocą `group.setWidth()` i `group.setHeight()`.
* **Performance note:** Jeśli generujesz wiele dokumentów w pętli, ponownie użyj jednej instancji `DocumentBuilder` i wywołaj `doc.clone()`, aby zmniejszyć narzut związany z tworzeniem obiektów.

## Zakończenie

Teraz wiesz, jak **create blank Word document**, który zawiera grupowaną kolekcję kształtów przy użyciu Aspose.Words for Java. Tutorial obejmował pełny przepływ pracy: konfigurację biblioteki, tworzenie dokumentu, wstawianie grupy, **set shape size**, **add shapes to word**, oraz zapisanie wyniku.

Od tego momentu możesz eksplorować bardziej zaawansowane funkcje, takie jak grupowanie wykresów, stosowanie stylów do poszczególnych kształtów lub eksportowanie dokumentu do PDF. Każdy z tych tematów opiera się na tych samych zasadach przedstawionych w tym przewodniku.

---

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}