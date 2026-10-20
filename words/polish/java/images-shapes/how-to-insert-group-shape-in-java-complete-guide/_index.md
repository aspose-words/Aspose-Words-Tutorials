---
category: general
date: 2026-07-16
description: jak wstawić grupę kształtów w Javie przy użyciu Aspose.Words – dodać
  kształt prostokąta, ustawić wymiary kształtu oraz utworzyć kolorowy prostokąt i
  koło.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: pl
lastmod: 2026-07-16
og_description: 'jak wstawić grupę kształtów w Javie: praktyczny przewodnik, jak dodać
  kształt prostokąta, ustawić wymiary kształtu oraz stworzyć kolorowy prostokąt i
  koło przy użyciu Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Wstaw grupowy kształt w Javie – Pełny samouczek Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Jak wstawić grupowy kształt w Javie – kompletny przewodnik
url: /pl/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# jak wstawić grupowy kształt w Javie – Kompletny przewodnik

Zastanawiałeś się kiedyś **jak wstawić grupowy kształt** w dokumencie Word przy użyciu Javy? Nie jesteś jedyny. Niezależnie od tego, czy tworzysz generator raportów, czy dynamiczny kreator ulotek, grupowanie kształtów utrzymuje układ w porządku i kod w łatwej do zarządzania formie.

W tym samouczku przeprowadzimy Cię krok po kroku przez **dodawanie prostokątnego kształtu**, **ustawianie wymiarów kształtu**, oraz **tworzenie kolorowego prostokąta** i **tworzenie kolorowego koła** przy użyciu biblioteki Aspose.Words. Po zakończeniu będziesz mieć działający program, który generuje plik .docx z niebieskim prostokątem i czerwonym kołem starannie umieszczonymi w grupie.

## Prerequisites

- Java 17 (lub dowolny nowoczesny JDK) zainstalowany i skonfigurowany.
- Maven lub Gradle do zarządzania zależnościami.
- Aspose.Words for Java 23.9 lub nowszy – możesz go pobrać z Maven Central.
- Podstawowa znajomość składni Javy – nic skomplikowanego nie jest wymagane.

Jeśli brakuje Ci któregoś z tych elementów, pobierz JDK ze strony Oracle i dodaj zależność Aspose.Words do swojego `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Teraz, gdy podłoże jest gotowe, zabierzmy się do pracy.

## jak wstawić grupowy kształt – przegląd

Podstawowa idea jest prosta: tworzymy `Document`, otwieramy `DocumentBuilder`, wstawiamy **grupowy kształt**, a następnie dodajemy poszczególne kształty (prostokąt i koło) do tej grupy. Grupa działa jak kontener, więc późniejsze przemieszczanie jej spowoduje przesunięcie wszystkiego, co znajduje się wewnątrz – idealne dla złożonych układów.

Poniżej znajduje się pełny, gotowy do uruchomienia kod. Śmiało skopiuj‑wklej go do nowej klasy Javy o nazwie `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Wskazówka:** Wartości `setLeft` i `setTop` są względne względem początku grupy, a nie strony. Dzięki temu późniejsze przemieszczanie całej grupy jest bardzo proste.

### Co się właśnie stało?

1. **Document & Builder** – Tworzymy pusty plik Word oraz `DocumentBuilder`, który umożliwia wstawianie treści.
2. **Group Shape** – `builder.insertGroupShape()` tworzy kontener. Pomyśl o nim jak o folderze dla obiektów rysunkowych.
3. **Blue Rectangle** – Tworzymy obiekt `Shape` typu `RECTANGLE`, ustawiamy jego rozmiar, pozycję i wypełniamy go niebieskim kolorem – to krok **create colored rectangle**.
4. **Red Circle** – Ten sam schemat, ale używamy `ELLIPSE` dla idealnego koła, które następnie wypełniamy czerwonym kolorem – to część **create colored circle**.
5. **Saving** – Na koniec zapisujemy wszystko do pliku `GroupShapeDemo.docx`.

Uruchom program (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) i otwórz wygenerowany plik. Powinieneś zobaczyć niebieski prostokąt po lewej i czerwone koło po prawej, oba zamknięte w jednej grupie.

## Dodawanie prostokątnego kształtu

Jeśli potrzebujesz tylko prostokąta bez grupowania, możesz pominąć wywołanie `insertGroupShape()` i dodać prostokąt bezpośrednio do ciała dokumentu. Jednak grupowanie daje możliwość przemieszczania, obracania lub usuwania wielu kształtów jednocześnie.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Zauważ, że użyliśmy tutaj logiki **add rectangle shape**. Prostokąt pojawia się na stronie jako niezależny obiekt. W większości rzeczywistych scenariuszy będziesz chciał użyć grupy, ponieważ zachowuje ona względne pozycjonowanie.

## Ustawianie wymiarów kształtu

Kiedy widzisz metody takie jak `setWidth` i `setHeight`, pamiętaj, że przyjmują **punkty** (1/72 cala). Jeśli wolisz milimetry, najpierw dokonaj konwersji:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Ten fragment pokazuje **set shape dimensions** z konwersją jednostek – przydatne, gdy specyfikacje projektu pochodzą z makiety UI używającej jednostek metrycznych.

## Tworzenie kolorowego prostokąta

Kolorowanie kształtu jest tak proste, jak wywołanie `getFill().setForeColor()`. Możesz przekazać dowolny `java.awt.Color`. Chcesz gradient? Użyj `setForeColor` dla koloru początkowego i `setBackColor` dla końcowego.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

To szybki sposób na **create colored rectangle** z wypełnieniem gradientowym zamiast jednolitego koloru.

## Tworzenie kolorowego koła

Koła to po prostu elipsy o równej szerokości i wysokości. Ta sama logika kolorowania ma zastosowanie:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Jeśli potrzebujesz przezroczystego wypełnienia, ustaw kanał alfa:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Teraz opanowałeś technikę **create colored circle**.

## Zapisywanie dokumentu

Aspose.Words umożliwia eksport do wielu formatów: DOCX, PDF, HTML, PNG – jakiego tylko potrzebujesz. W tym demo pozostajemy przy DOCX, ponieważ zachowuje on wektorowe kształty w doskonałej jakości.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Zmiana `SaveFormat` to wszystko, co trzeba, aby wygenerować wersję PDF tego samego grupowego rysunku.

## Częste pułapki i jak ich unikać

- **Zapomniałeś dodać kształt do grupy?** Kształt pojawi się na stronie, ale nie będzie się przemieszczał wraz z grupą. Zawsze wywołuj `group.appendChild(yourShape)`.

## Co warto nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz dokument Word w Javie – Dodaj prostokątny kształt z efektem cienia](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Jak tworzyć pola formularza i dodawać treść przy użyciu DocumentBuilder w Aspose.Words dla Javy](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Utwórz prostokątny kształt w Wordzie z Aspose.Words – Przewodnik krok po kroku](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}