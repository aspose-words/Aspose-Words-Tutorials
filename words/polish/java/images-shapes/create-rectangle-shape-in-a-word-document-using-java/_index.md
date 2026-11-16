---
category: general
date: 2026-11-15
description: Utwórz prostokątny kształt w Wordzie przy użyciu Javy i dowiedz się,
  jak dodawać kształty do Worda, ustawiać wymiary kształtu oraz efektywnie zapisywać
  dokument Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: pl
lastmod: 2026-11-15
og_description: Utwórz prostokątny kształt w dokumencie Word przy użyciu Javy. Dowiedz
  się, jak dodawać kształty do Worda, ustawiać wymiary kształtu i zapisywać dokument
  Word w kilka minut.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Tworzenie prostokątnego kształtu w Wordzie przy użyciu Javy – przewodnik
  krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Utwórz prostokątny kształt w dokumencie Word przy użyciu Javy
url: /pl/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tworzenie prostokątnego kształtu w dokumencie Word przy użyciu Javy

Jeśli potrzebujesz **utworzyć prostokątny kształt** w pliku Word, ten przewodnik pokaże Ci dokładnie, jak to zrobić w Javie. Zobaczysz, jak **dodawać kształty do Word**, kontrolować **ustawianie wymiarów kształtu** oraz w końcu **zapisz dokument Word** nie opuszczając IDE.

W kolejnych sekcjach otrzymasz kompletny, gotowy do uruchomienia przykład, wyjaśnienie każdej linii oraz wskazówki dotyczące typowych pułapek, takich jak problemy z rozmiarami i kompatybilnością dokumentu. Nie są wymagane żadne zewnętrzne odniesienia — jedynie biblioteka Aspose.Words for Java.

## Czego się nauczysz

* Jak zainicjalizować `Document` i `DocumentBuilder`.
* Jak wstawić **grupowy kształt** i umieścić w nim prostokąt.
* Jak **zdefiniować rozmiar kształtu** przy użyciu `setWidth` i `setHeight`.
* Jak **zapisz dokument Word** w formacie `.docx`.
* Obsługa przypadków brzegowych dla różnych rozmiarów stron i ustawień DPI.

### Wymagania wstępne

* Java 17 lub nowsza (kod kompiluje się również z Java 8).
* Aspose.Words for Java 23.10 lub nowsza – można ją pobrać z Maven Central.
* Podstawowa znajomość składni Javy oraz koncepcji obiektowo‑zorientowanych.

> **Pro tip:** Jeśli planujesz później dodać więcej kształtów (np. koła lub pola tekstowe), trzymaj je w tym samym `GroupShape`. Ułatwi to przemieszczanie, obracanie lub formatowanie całej kolekcji.

## Krok 1: Inicjalizacja dokumentu i buildera

Pierwszy krok to stworzenie pustego pliku Word oraz `DocumentBuilder`, który pozwala na zapisywanie treści.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Dlaczego to ważne:* `Document` reprezentuje cały plik, natomiast `DocumentBuilder` udostępnia wysokopoziomowe metody do wstawiania tekstu, tabel i **kształtów**. Bez buildera musiałbyś ręcznie manipulować węzłami niskiego poziomu.

## Krok 2: Wstawienie grupowego kształtu, aby pomieścić wiele kształtów

**Grupowy kształt** działa jak kontener; możesz dodać kilka kształtów i traktować je później jako jeden obiekt (np. przesuwać lub obracać razem).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Dlaczego używać grupowego kształtu?* Jeśli później zdecydujesz się dodać strzałki, koła lub etykiety wokół prostokąta, grupa utrzyma wszystko wyrównane. Uprości to **dodawanie kształtów do Word**, ponieważ potrzebujesz tylko jednego wywołania `appendChild` dla każdego nowego kształtu.

## Krok 3: Utworzenie prostokątnego kształtu

Teraz tworzymy właściwy prostokąt, który będzie znajdował się wewnątrz grupy. Konstruktor `Shape` wymaga właściciela `Document` oraz typu kształtu, który chcesz.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Dlaczego prostokąt?* `ShapeType.RECTANGLE` jest najczęściej używaną prymitywą do podświetlania sekcji, tworzenia placeholderów lub rysowania prostych makiet UI bezpośrednio w Wordzie.

## Krok 4: Zdefiniowanie rozmiaru prostokąta

Ustawianie wymiarów to miejsce, w którym **ustawianie wymiarów kształtu** staje się istotne. Możesz używać dowolnej jednostki miary obsługiwanej przez Aspose.Words; domyślnie są to punkty (1 pt = 1/72 cala).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Uwaga:** Jeśli wolisz milimetry, wywołaj `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));`, gdzie `1.39 in ≈ 35 mm`. To pokazuje elastyczność **definiowania rozmiaru kształtu**.

## Krok 5: Dodanie prostokąta do grupowego kształtu

Dołączenie prostokąta do wcześniej utworzonej grupy powoduje jego pojawienie się w dokumencie.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

W tym momencie prostokąt znajduje się w lewym górnym rogu grupy. Możesz go później przesunąć przy pomocy `rectangle.setLeft(...)` i `rectangle.setTop(...)`, jeśli potrzebujesz precyzyjnego położenia.

## Krok 6: (Opcjonalnie) Zapisz dokument, aby zobaczyć rezultat

Na koniec zapisz dokument na dysku. To jest krok **zapisz dokument Word**, który tworzy plik `.docx`, który możesz otworzyć w Microsoft Word, LibreOffice lub Google Docs.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

Uruchomienie programu tworzy `RectangleShapeDemo.docx` zawierający pojedynczy prostokąt wewnątrz grupowego kształtu. Otwarcie pliku pokazuje prosty biały prostokąt — dokładnie o rozmiarze, który określiłeś.

### Oczekiwany wynik

* Plik Word o nazwie `RectangleShapeDemo.docx`.
* W pierwszym akapicie grupowy kształt zawierający prostokąt 100 pt × 50 pt.
* Brak dodanego tekstu, więc prostokąt pojawia się na pustej stronie.

## Różne warianty i przypadki brzegowe

| Sytuacja | Jak dostosować kod |
|-----------|-----------------------|
| **Inny rozmiar strony** (np. A4) | Wywołaj `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` przed wstawieniem kształtu. |
| **Wyższe DPI dla druku** | Pomnóż szerokość/wysokość przez pożądany czynnik DPI, np. `rectangle.setWidth(200 * 2);` dla podwójnej rozdzielczości. |
| **Dodanie etykiety tekstowej wewnątrz prostokąta** | Utwórz `Shape` typu `TEXT_BOX`, ustaw jego `setWidth`/`setHeight` tak, aby pasowały do prostokąta, a następnie dodaj go do tego samego `GroupShape`. |
| **Obracanie prostokąta** | Użyj `rectangle.setRotationAngle(45);`, aby obrócić o 45 stopni zgodnie z ruchem wskazówek zegara. |
| **Zapis jako PDF zamiast DOCX** | Zamień `document.save("output.docx");` na `document.save("output.pdf");` – to samo API działa dla PDF, zachowując prostokąt. |

## Pro tipy dla solidnej implementacji

1. **Ponowne użycie buildera** – po wstawieniu grupowego kształtu możesz kontynuować dodawanie akapitów lub tabel bez tworzenia nowej instancji buildera.
2. **Zwolnienie zasobów** – chociaż garbage collector Javy obsługuje większość obiektów, jawne wywołanie `document.close();` (gdy używasz strumieni) zapobiega wyciekom uchwytów plików.
3. **Walidacja wymiarów** – przed wywołaniem `setWidth`/`setHeight` upewnij się, że wartości są dodatnie; ujemne wartości powodują `IllegalArgumentException`.
4. **Kompatybilność wersji** – kod działa z Aspose.Words 23.x i nowszymi. Starsze wersje mogą wymagać `Shape.setSize(width, height)` zamiast oddzielnych setterów.

## Pełny, gotowy do uruchomienia przykład

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Weryfikacja wyniku:** Otwórz `output/RectangleShapeDemo.docx` w Microsoft Word. Powinieneś zobaczyć prostokąt o określonym rozmiarze, wyśrodkowany u góry pierwszej strony. Jeśli prostokąt wydaje się zbyt mały, dostosuj wartości przekazywane do `setWidth` i `setHeight`.

## Podsumowanie

Teraz wiesz, jak **utworzyć prostokątny kształt** w pliku Word przy użyciu Javy, jak **dodawać kształty do Word** za pomocą `GroupShape`, jak **ustawiać wymiary kształtu** i **definiować rozmiar kształtu**, a na koniec jak **zapisz dokument Word** do dalszej dystrybucji. Ten sam wzorzec działa dla innych typów kształtów, umożliwiając programowe budowanie złożonych diagramów.

### Co dalej?

* Eksploruj **dodawanie kształtów do Word** poprzez wstawianie kół, strzałek lub pól tekstowych.
* Łącz wiele kształtów w jeden `GroupShape` i stosuj transformacje (obracanie, odbijanie).
* Generuj raporty, które osadzają wykresy jako kształty, a następnie **zapisz dokument Word** jako PDF do udostępniania.

Śmiało eksperymentuj z wymiarami, kolorami i pozycjonowaniem, aby dopasować je do swojego konkretnego scenariusza. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Create word document java – hide shape and set fill color](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}