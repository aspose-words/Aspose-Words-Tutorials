---
category: general
date: 2026-10-20
description: Jak grupować kształty w Aspose.Words for Java – dowiedz się, jak wstawić
  prostokątny kształt, pogrupować je i zapisać dokument w jednym przewodniku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: pl
lastmod: 2026-10-20
og_description: Jak grupować kształty w Aspose.Words for Java. Ten samouczek pokazuje,
  jak wstawić prostokątny kształt, pogrupować je i wyeksportować wynik.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Jak grupować kształty w Aspose.Words for Java – przewodnik krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Jak grupować kształty w Aspose.Words dla Javy
url: /pl/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak grupować kształty w Aspose.Words for Java

Jeśli potrzebujesz **jak grupować kształty** w dokumencie Word przy użyciu Aspose.Words for Java, ten przewodnik pokaże Ci kompletny przepływ pracy. Nauczysz się, jak **wstawić prostokątny kształt**, dodać drugi prostokąt, pogrupować oba kształty i ostatecznie zapisać plik — wszystko przy użyciu przejrzystego, działającego kodu.

Grupowanie kształtów jest przydatne, gdy chcesz przenieść, obrócić lub sformatować kilka rysunków jako jedną jednostkę. Niezależnie od tego, czy tworzysz szablon raportu, diagram, czy niestandardowy ulotkę, opanowanie grupowania kształtów oszczędza czas i zapewnia spójność układu.

W tym samouczku:

* Utworzyć nowy `Document` i `DocumentBuilder`.
* **Jak wstawić prostokąt** o precyzyjnych wymiarach.
* Pogrupować prostokąty w `GroupShape`.
* Zapisać dokument i zweryfikować wynik.

> **Wymaganie wstępne** – Musisz mieć dodane do projektu Aspose.Words for Java (v23.12 lub nowszy). Użytkownicy Maven mogą dołączyć zależność pokazanej poniżej.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## Czego będziesz potrzebować

| Element | Powód |
|------|--------|
| Java 17+ | Nowoczesne funkcje języka i lepsza wydajność |
| Aspose.Words for Java | Dostarcza API `DocumentBuilder`, `Shape` i `GroupShape` |
| IDE (IntelliJ IDEA, Eclipse, VS Code, itp.) | Do kompilacji i uruchomienia przykładu |
| Uprawnienia do zapisu w folderze | Dokument zostanie zapisany na dysku |

---

## Jak wstawić prostokątny kształt

Pierwszym krokiem jest utworzenie `Document` i `DocumentBuilder`. Builder udostępnia metody, takie jak `insertShape`, do umieszczania obiektów rysunkowych.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Dlaczego to ważne** – Użycie `insertShape` jest standardowym sposobem **jak wstawić prostokąt** w Aspose.Words. Automatycznie dodaje kształt do bieżącego akapitu dokumentu, więc nie musisz zarządzać niskopoziomowym OpenXML.

## Dostosowywanie pozycji prostokąta (opcjonalnie)

Jeśli drugi prostokąt wymaga niestandardowej lokalizacji względem pierwszego, możesz zmodyfikować jego właściwości `left` i `top`. Ten krok jest opcjonalny, ale często potrzebny do precyzyjnego układu diagramu.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Wskazówka:** Wszystkie wymiary podawane są w punktach (1 pt ≈ 1/72 in). Użyj `convertPointsToPixels`, jeśli potrzebujesz wartości w pikselach do obliczeń opartych na interfejsie UI.

## Jak grupować kształty

Teraz, gdy prostokąty istnieją, możesz umieścić je wewnątrz `GroupShape`. Grupowanie sprawia, że dwa prostokąty zachowują się jak pojedynczy obiekt — przenoszenie, obracanie lub formatowanie grupy wpłynie na oba kształty.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Dlaczego grupowanie działa** – `GroupShape` dziedziczy po `Shape`, więc możesz traktować grupę dokładnie tak jak każdy inny obiekt rysunkowy. Gdy wywołujesz `appendChild`, kształty są usuwane z ich pierwotnego miejsca i stają się dziećmi grupy.

## Zapisywanie dokumentu zawierającego pogrupowane kształty

Na koniec zapisz dokument na dysku. Plik będzie zawierał pojedynczy `GroupShape` z dwoma prostokątami wewnątrz.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Oczekiwany wynik

Otwórz `GroupShape.docx` w programie Microsoft Word:

* Zobaczysz dwa prostokąty (niebieski i zielony) ustawione obok siebie.
* Wybranie dowolnego prostokąta zaznacza całą grupę — przeciąganie przesuwa oba razem.
* Grupa ma cienką czerwoną ramkę, co potwierdza zastosowanie właściwości `GroupShape`.

Jeśli klikniesz prawym przyciskiem myszy grupę i wybierzesz **Group → Ungroup**, prostokąty powrócą do niezależnych kształtów, co pokazuje, że operacja grupowania jest odwracalna.

## Typowe warianty i przypadki brzegowe

| Sytuacja | Jak sobie radzić |
|-----------|------------------|
| **Więcej niż dwa kształty** | Wstaw każdy kształt, a następnie dołącz wszystkie do tej samej `GroupShape`. |
| **Różne typy kształtów** (np. elipsa, obraz) | Użyj `builder.insertShape(ShapeType.ELLIPSE, …)` lub `builder.insertImage(...)` przed dołączeniem. |
| **Skalowanie grupy** | Wywołaj `group.setWidth(newWidth)` lub `group.setHeight(newHeight)`; elementy potomne skalują się proporcjonalnie. |
| **Obracanie grupy** | `group.setRotationAngle(45);` obraca całą kolekcję wokół jej środka. |
| **Zachowanie pierwotnych pozycji** | Przechowaj `left`/`top` każdego kształtu przed grupowaniem i przywróć po rozgrupowaniu, jeśli to konieczne. |

## Pełny, działający przykład

Poniżej znajduje się pełna klasa Java, którą możesz skopiować i wkleić do swojego IDE. Zawiera wszystkie importy, obsługę błędów i komentarze dla przejrzystości.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Uruchom program, otwórz powstały `GroupShape.docx` i zobaczysz pogrupowane prostokąty dokładnie tak, jak opisano.

## Podsumowanie

Teraz wiesz **jak grupować kształty** w Aspose.Words for Java, od tworzenia dokumentu, przez wstawianie prostokątnych kształtów, dostosowywanie ich pozycji, aż po grupowanie ich przy użyciu `GroupShape`. Ta technika pozwala traktować wiele rysunków jako jedną jednostkę, upraszczając dostosowania układu i zapewniając spójność wizualną.

**Kolejne kroki**

* Zbadaj **jak wstawić prostokąt** o różnych wzorach wypełnienia lub obramowaniach.
* Połącz **wstawianie prostokątnego kształtu** z polami tekstowymi, aby tworzyć oznaczone diagramy.
* Eksperymentuj z obracaniem lub skalowaniem grupy, aby uzyskać bardziej złożoną grafikę.

Śmiało dostosowuj kod do innych typów kształtów, większych grup lub scenariuszy dynamicznego generowania dokumentów. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [how to insert group shape in Java – Complete Guide](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [How to Set Shadow on a Shape in Aspose.Words – Complete Guide](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}