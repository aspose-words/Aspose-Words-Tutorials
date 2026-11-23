---
category: general
date: 2026-11-22
description: Dodaj prostokątny kształt w dokumencie Word przy użyciu Javy, ustaw rozmiar
  kształtu, grupuj wiele kształtów i efektywnie dodawaj kształt do grupy.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: pl
lastmod: 2026-11-22
og_description: Dodaj prostokątny kształt w dokumencie Word przy użyciu Javy, następnie
  ustaw rozmiar kształtu, grupuj wiele kształtów i dołącz kształt do grupy w jednym
  procesie.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Dodaj kształt prostokąta i grupuj kształty w Javie – pełny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Dodaj kształt prostokąta i grupuj kształty w Javie
url: /pl/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj kształt prostokąta i grupuj kształty w Javie

Jeśli potrzebujesz **add rectangle shape** do dokumentu Word przy użyciu Javy, ten przewodnik przeprowadzi Cię krok po kroku. Dowiesz się także, jak **set shape size**, **group multiple shapes** oraz **append shape to group** bez opuszczania IDE.

Praca z grafiką wektorową wewnątrz pliku DOCX często przypomina żonglowanie oddzielnymi API. Po zakończeniu tego samouczka będziesz mieć pojedynczy, samodzielny program, który tworzy prostokąt, elipsę oraz dowolne dodatkowe kształty, które mogą być potrzebne, a następnie grupuje je, aby poruszały się jako jeden obiekt. Nie są wymagane żadne zewnętrzne narzędzia poza Aspose.Words for Java.

## Prerequisites

* Java 17 lub nowszy zainstalowany.
* Maven 3.8+ (lub Gradle) do zarządzania zależnościami.
* Ważna licencja Aspose.Words for Java (wersja ewaluacyjna działa do testów).
* IDE, takie jak IntelliJ IDEA lub VS Code, choć dowolny edytor tekstu się sprawdzi.

Te wymagania pozwalają kodowi kompilować się i działać w każdym nowoczesnym środowisku programistycznym.

## Krok 1: Skonfiguruj projekt Maven

Utwórz nowy projekt Maven lub dodaj zależność Aspose.Words do istniejącego pliku `pom.xml`:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

Zależność pobiera wszystkie klasy potrzebne do manipulacji dokumentem, w tym `Document`, `DocumentBuilder`, `Shape` i `GroupShape`. Maven automatycznie pobierze pliki JAR, gdy uruchomisz `mvn compile`.

## Krok 2: Załaduj dokument i utwórz DocumentBuilder

`DocumentBuilder` zapewnia płynne API do wstawiania treści. Załaduj istniejący plik DOCX lub rozpocznij od pustego dokumentu:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Wczesne utworzenie buildera daje Ci kursor umieszczony na początku dokumentu, gotowy do wstawiania kształtów.

## Dodaj kształt prostokąta do dokumentu Word

### Krok 3: Wstaw kształt prostokąta

Prostokąt jest pierwszym elementem wizualnym, który chcemy umieścić w dokumencie. Korzystając z konstruktora `Shape` z `ShapeType.RECTANGLE`, otrzymujesz w pełni edytowalny obiekt.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Dodanie prostokąta w tym miejscu nie wpływa na układ, dopóki nie zostanie określony jego rozmiar i nie zostanie dołączony do kontenera.

### Ustaw rozmiar i wymiary kształtu

#### Krok 4: Zdefiniuj szerokość i wysokość

Ustawienie wymiarów kształtu określa, jak będzie się on wyświetlał na stronie. Wartości szerokości i wysokości mierzone są w punktach (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

Możesz dostosować te liczby do wymagań swojego projektu. Te same metody działają na dowolnej instancji `Shape`, więc możesz je ponownie wykorzystać dla kół, strzałek lub własnych rysunków.

#### Krok 5: Wstaw prostokąt do dokumentu

Teraz, gdy prostokąt ma rozmiar, umieść go na stronie. Metoda `insertShape` klasy `DocumentBuilder` dodaje kształt w bieżącej pozycji kursora.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

Na tym etapie prostokąt pojawia się sam na stronie. Kolejne kroki pokażą, jak połączyć go z innymi kształtami.

## Grupuj wiele kształtów razem

Grupowanie kształtów pozwala na ich przemieszczanie, obracanie lub zmianę rozmiaru jako jednej jednostki. Jest to szczególnie przydatne przy tworzeniu złożonych diagramów.

### Krok 6: Utwórz kontener grupy kształtów

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

Wywołanie `insertGroupShape` dodaje pusty kontener do dokumentu. Wszystkie kształty dołączone do tego kontenera stają się częścią grupy.

### Dołącz kształt do grupy

#### Krok 7: Dodaj prostokąt do grupy

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

Dołączenie przenosi prostokąt z ciała dokumentu do wewnętrznej kolekcji grupy. Prostokąt teraz respektuje transformacje grupy.

#### Krok 8: Dodaj elipsę w celach demonstracyjnych

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

Elipsa korzysta z tej samej przestrzeni współrzędnych co prostokąt, więc możesz je wizualnie wyrównać, dostosowując ich właściwości `setLeft` i `setTop`, jeśli zajdzie taka potrzeba.

### Krok 9: Zapisz dokument

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

Uruchomienie programu generuje `output.docx`. Otwórz plik w Microsoft Word lub LibreOffice; zobaczysz prostokąt i elipsę zgrupowane razem. Wybranie dowolnego kształtu podświetla całą grupę, potwierdzając, że **append shape to group** zakończyło się sukcesem.

![Add rectangle shape example in Java](image.png){alt="Przykład dodania kształtu prostokąta w Javie"}

*Zrzut ekranu pokazuje prostokąt i elipsę wewnątrz jednej grupy, gotowe do wspólnej manipulacji.*

## Dlaczego to podejście ma znaczenie

* **Single source of truth** – Wszystkie właściwości kształtu są ustawiane przed utworzeniem grupy, co zapobiega problemom z układem.
* **Reusability** – Te same metody `setWidth`/`setHeight` działają na każdym kształcie, więc możesz rozszerzyć przykład o strzałki, gwiazdy lub własne SVG.
* **Performance** – Grupowanie zmniejsza liczbę obiektów rysunkowych, które renderer Word musi obsłużyć, co przyspiesza otwieranie dużych dokumentów.
* **Maintainability** – Trzymając tworzenie kształtów i logikę grupowania razem, przyszli deweloperzy mogą modyfikować wymiary lub dodawać nowe kształty bez przeszukiwania niepowiązanego kodu.

## Typowe warianty i przypadki brzegowe

| Scenario | Adjustment |
|----------|------------|
| **Różne jednostki** | Użyj konwersji `PointsToPixels` lub ustaw `Shape.setWrapType(WrapType.INLINE)` dla umieszczenia inline. |
| **Obracanie grupy** | Wywołaj `groupShape.setRotation(45);`, aby obrócić wszystkie kształty podrzędne o 45°. |
| **Dodawanie tekstu do kształtu** | Użyj `Shape.setText("Label");` po ustawieniu rozmiaru. |
| **Dynamiczne rozmiarowanie** | Pobierz wymiary strony za pomocą `doc.getFirstSection().getPageSetup().getPageWidth()` i oblicz rozmiary kształtów proporcjonalnie. |

Te warianty ilustrują, jak podstawowy wzorzec — **add rectangle shape**, **set shape size**, **group multiple shapes**, **append shape to group** — dostosowuje się do wielu rzeczywistych wymagań.

## Podsumowanie

Teraz wiesz, jak **add rectangle shape** do dokumentu Word przy użyciu Javy, **set shape size**, **group multiple shapes** oraz **append shape to group** w czysty, łatwy do utrzymania sposób. Pełny przykład kompiluje się do jednej klasy uruchamialnej, a powstały plik DOCX pokazuje oczekiwany rezultat.

Od tego miejsca możesz eksplorować:

* Dodawanie etykiet tekstowych lub hiperłączy do każdego kształtu.
* Zagnieżdżanie grup w celu budowy hierarchicznych diagramów.
* Eksportowanie dokumentu do PDF przy zachowaniu grup kształtów.

Śmiało eksperymentuj z różnymi wymiarami, kolorami i dodatkowymi typami kształtów. Opanowanie manipulacji kształtami otwiera drzwi do automatycznego generowania raportów, dynamicznych diagramów i bogatych doświadczeń dokumentowych — wszystko bezpośrednio z kodu Javy.

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Wstaw kształt prostokąta w Javie – grupowanie i pozycjonowanie kształtów](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [Jak tworzyć i wstawiać elipsy oraz prostokąty wewnątrz grupy kształtów w dokumencie Word przy użyciu Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Utwórz kształt prostokąta w dokumencie Word przy użyciu Javy](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}