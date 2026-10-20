---
category: general
date: 2026-08-14
description: Grupowanie kształtów w Wordzie przy użyciu Javy i Aspose.Words. Dowiedz
  się, jak utworzyć prostokątny kształt, ustawić wymiary kształtu i grupować wiele
  kształtów w pustym dokumencie Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: pl
lastmod: 2026-08-14
og_description: Grupuj kształty w programie Word przy użyciu Aspose.Words for Java.
  Utwórz pusty dokument Word, stwórz prostokątny kształt, ustaw wymiary kształtu i
  grupuj wiele kształtów w ciągu kilku minut.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Grupowanie kształtów w Wordzie – przykład w Javie dla programistów
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Grupowanie kształtów w Wordzie – kompletny przewodnik programistyczny
url: /pl/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Grupowanie kształtów w Word – kompletny przewodnik programistyczny

Jeśli potrzebujesz **grupować kształty w Word**, ten tutorial przeprowadzi Cię przez cały proces przy użyciu Javy i Aspose.Words. Dowiesz się, jak **utworzyć pusty dokument Word**, **stworzyć prostokątny kształt**, **ustawić wymiary kształtu**, a na koniec **zgrupować wiele kształtów**, aby zachowywały się jak jeden obiekt.

Praca z kształtami w pliku Word często przypomina rysowanie na płótnie bez pędzla. Po zakończeniu tego przewodnika będziesz mieć gotowy fragment kodu, który możesz wkleić do dowolnego projektu Java, niezależnie od tego, czy generujesz raporty, faktury, czy własne szablony.

## Co będziesz potrzebować

- Java 8 lub nowsza
- Aspose.Words for Java (najświeższa wersja, np. 24.9)
- IDE, takie jak IntelliJ IDEA lub Eclipse
- Podstawowa znajomość programowania obiektowego

Wszystkie te elementy są dostępne bezpłatnie, a poniższy kod kompiluje się przy użyciu jednej zależności Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Krok 1: Utwórz pusty dokument Word i zainicjalizuj builder

Pierwszą rzeczą, którą musisz zrobić, jest **utworzenie pustego dokumentu Word**. Daje to czyste płótno, na którym później możesz wstawiać kształty.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` reprezentuje cały plik *.docx*, natomiast `DocumentBuilder` jest pomocnikiem, który wstawia akapity, tabele i kształty. Inicjalizacja obu obiektów jest podstawą każdego zadania automatyzacji Word.

## Krok 2: Wstaw kontener grupowego kształtu

**Grupowy kształt** działa jak folder, który może przechowywać inne kształty. Najpierw tworzymy kontener o stałym rozmiarze 400 pt × 200 pt.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

Metoda `insertGroupShape` zwraca obiekt `GroupShape`. Wszystkie kolejne kształty, które chcesz traktować jako jedną jednostkę, muszą być dołączone do tego obiektu.

## Krok 3: Utwórz prostokątne kształty i ustaw ich wymiary

Teraz **tworzymy obiekty prostokątnych kształtów**, konfigurujemy ich rozmiar i pozycjonujemy je wewnątrz grupy. Ten krok pokazuje także, jak **precyzyjnie ustawić wymiary kształtu**.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Oba prostokąty mają te same wymiary, ale ich właściwości `left` różnią się, więc pojawiają się obok siebie. Możesz zmienić `setTop` i `setLeft`, aby uzyskać dowolny układ.

## Krok 4: Zapisz dokument zawierający zgrupowane prostokąty

Po umieszczeniu kształtów w grupie po prostu zapisujesz obiekt `Document`. Powstały plik pokaże dwa prostokąty, które poruszają się razem po zaznaczeniu.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Uruchomienie programu tworzy plik `GroupShape.docx` w katalogu roboczym. Otwórz go w Microsoft Word, zaznacz jeden prostokąt i zauważysz, że cała grupa przemieszcza się jako jedna jednostka — dokładnie tak, jak powinny działać **grupowane kształty w Word**.

![Przykład grupowania kształtów w Word](group-shapes.png){alt="Przykład grupowania kształtów w Word"}

*Rysunek: Dwa prostokątne kształty zgrupowane razem w dokumencie Word.*

## Porada pro: Ponowne użycie tego samego grupowego kształtu

Jeśli później potrzebujesz dodać więcej kształtów (np. koła, pola tekstowe), zachowaj odwołanie do `groupShape` i kontynuuj wywoływanie `appendChild`. Dzięki temu nie musisz ponownie tworzyć kontenera, a wszystkie elementy pozostają zsynchronizowane.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Przypadki brzegowe i typowe pytania

- **Co zrobić, gdy kształty się nakładają?** Nakładanie jest dozwolone; Word renderuje je w kolejności, w jakiej zostały dodane. Użyj `setZOrder`, jeśli potrzebujesz wyraźnego ustalenia kolejności.
- **Czy mogę grupować kształty na różnych stronach?** Nie. `GroupShape` jest ograniczony do jednej strony, ponieważ jego system współrzędnych jest względny względem strony.
- **Czy grupowane kształty dziedziczą formatowanie?** Każde dziecko zachowuje własne formatowanie (kolor wypełnienia, styl linii). Aby zastosować jednolity styl, przeiteruj `groupShape.getChildNodes()` i ustaw właściwości programowo.

## Pełny kod źródłowy do wglądu

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Uruchomienie programu generuje plik DOCX, w którym dwa prostokąty są **zgrupowane**. Zaznaczenie dowolnego prostokąta przesuwa oba, potwierdzając, że udało Ci się **zgrupować wiele kształtów**.

## Zakończenie

Teraz wiesz, jak **grupować kształty w Word** przy użyciu Javy, od **tworzenia pustego dokumentu Word**, przez **tworzenie prostokątnego kształtu**, **ustawianie wymiarów kształtu**, aż po **grupowanie wielu kształtów** w jeden, ruchomy obiekt. Ten wzorzec skaluje się do dowolnej liczby kształtów i może być łączony z tekstem, obrazami czy wykresami, aby tworzyć bogate, programistyczne dokumenty.

### Co dalej?

- Eksperymentuj z **grupowaniem wielu kształtów** różnych typów (elipsy, strzałki, pola tekstowe).
- Dodawaj kolory wypełnienia lub obramowania, wywołując `shape.getFillColor()` oraz `shape.getLine().setColor()`.
- Wstaw zgrupowany kształt do komórki tabeli, aby uzyskać strukturalne raporty.
- Połącz to podejście z korespondencją seryjną, aby generować spersonalizowane umowy zawierające markowe grafiki.

Śmiało eksperymentuj, dostosowuj wymiary lub osadzaj dodatkową treść. Gdy opanujesz grupowanie, Twoje skrypty automatyzacji Word staną się znacznie bardziej elastyczne i łatwiejsze w utrzymaniu. Powodzenia w kodowaniu!

## Co powinieneś się nauczyć dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz szczegółowe wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Używanie kształtów dokumentu w Aspose.Words dla Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Tworzenie dokumentu Word w Java – Dodaj prostokątny kształt z efektem cienia](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tworzenie grupowego kształtu w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}