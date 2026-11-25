---
category: general
date: 2026-11-25
description: Jak grupować kształty w Wordzie przy użyciu Javy oraz jak ustawiać wymiary
  kształtów w pliku DOCX przy użyciu Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: pl
lastmod: 2026-11-25
og_description: Jak grupować kształty w Wordzie przy użyciu Aspose.Words Java API
  i szybko ustawiać rozmiar kształtu w Wordzie. Śledź kompletną instrukcję krok po
  kroku.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Jak grupować kształty w Wordzie i ustawiać ich wymiary – przewodnik Java
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Jak grupować kształty w Wordzie i programowo ustawiać ich wymiary
url: /pl/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak grupować kształty w Wordzie i programowo ustawiać ich wymiary

Jeśli potrzebujesz **jak grupować kształty w Wordzie** i kontrolować ich dokładny rozmiar, ten przewodnik pokaże Ci kompletną, gotową do uruchomienia rozwiązanie. Korzystając z Aspose.Words for Java możesz utworzyć prostokąt, elipsę, dodać je do `GroupShape`, a następnie **jak ustawić wymiary kształtu** takie jak szerokość i wysokość w jednym pliku DOCX.

Nauczysz się jak:

* Utworzyć nowy dokument Word od podstaw.  
* Wstawić `GroupShape` (nowe API w wersji 24.9).  
* Dodać prostokąt i elipsę do grupy.  
* **Ustawić rozmiar kształtu w Wordzie** precyzyjnie przy użyciu `setWidth` i `setHeight`.  
* Zapisz dokument na dysku.

Nie wymaga żadnych zewnętrznych narzędzi — wystarczy Java 17+, Maven oraz biblioteka Aspose.Words for Java.

## Wymagania wstępne

* Java Development Kit 17 lub nowszy.  
* Maven (lub Gradle) do zarządzania zależnościami.  
* Aspose.Words for Java 24.9 lub późniejszy (API `GroupShape` zostało wprowadzone w wersji 24.9).  
* Podstawowa znajomość składni Java oraz koncepcji programowania obiektowego.

Jeśli jeszcze nie dodałeś Aspose.Words do swojego projektu, dołącz następującą zależność Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Krok 1: Utwórz nowy dokument i DocumentBuilder

`Document` reprezentuje cały plik Word, natomiast `DocumentBuilder` zapewnia wygodny sposób dodawania treści.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Dlaczego ten krok?*  
Utworzenie nowego `Document` daje czyste płótno. `DocumentBuilder` jest wysokopoziomowym pomocnikiem, który pozwala wstawiać akapity, tabele i, w tym przypadku, kształty.

## Krok 2: Wstaw `GroupShape` (nowe API w wersji 24.9)

`GroupShape` działa jak kontener; każdy dodany kształt staje się częścią tej samej grupy wizualnej.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Dlaczego używać `GroupShape`?*  
Grupowanie kształtów upraszcza przenoszenie, obracanie lub stosowanie formatowania do wielu obiektów jednocześnie. API zostało dodane w wersji 24.9, więc starsze wersje nie skompilują tej linii.

## Krok 3: Utwórz prostokąt, ustaw jego rozmiar i dodaj go do grupy

Tutaj demonstrujemy **jak ustawić wymiary kształtu** dla prostokąta.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Dlaczego ustawiać szerokość i wysokość explicite?*  
Word przechowuje rozmiar kształtu w punktach. Wywołując `setWidth` i `setHeight` kontrolujesz dokładny wizualny rozmiar, co jest niezbędne przy precyzyjnym układzie lub przy eksporcie do PDF.

## Krok 4: Utwórz elipsę, ustaw jej rozmiar i dodaj ją do tej samej grupy

Ta sama technika **ustawiania rozmiaru kształtu w Wordzie** działa dla każdego typu kształtu.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Dlaczego dodać elipsę do tej samej `GroupShape`?*  
Oba kształty będą się poruszać razem jako jedna jednostka. Jest to przydatne przy tworzeniu ikon, logotypów lub złożonych diagramów, które muszą pozostać wyrównane.

## Krok 5: Zapisz dokument z pogrupowanymi kształtami

Na koniec zapisz plik DOCX na dysku.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

Uruchomienie tego programu tworzy plik o nazwie **GroupShape.docx**, który zawiera prostokąt i elipsę pogrupowane razem. Po otwarciu pliku w Microsoft Word zobaczysz, że dwa kształty zachowują się jako pojedynczy obiekt — możesz je przeciągać, zmieniać rozmiar lub obracać razem.

### Oczekiwany wynik

* Dokument Word (`GroupShape.docx`) z jedną stroną.  
* `GroupShape` zawierający prostokąt 100 × 50 pt oraz elipsę 80 × 80 pt.  
* Wybranie dowolnego kształtu zaznacza całą grupę.

## Częste pytania i przypadki brzegowe

### Jak zmienić pozycję pogrupowanych kształtów?

Po utworzeniu `GroupShape` możesz ustawić jego właściwości `left` i `top`:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Te współrzędne są również mierzone w punktach.

### Co zrobić, jeśli potrzebuję dodać więcej niż dwa kształty?

`GroupShape` działa jak każdy inny węzeł kontenera. Wywołaj `groupShape.appendChild(yourShape)` dla każdego dodatkowego kształtu. API nie ogranicza liczby dzieci.

### Czy mogę zastosować styl (kolor wypełnienia, grubość linii) do poszczególnych kształtów?

Tak. Każdy obiekt `Shape` udostępnia właściwości formatowania:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Czy kod działa ze starszymi wersjami Aspose.Words?

Metoda `insertGroupShape` została wprowadzona w wersji 24.9. Jeśli używasz wcześniejszej wersji, będziesz musiał ręcznie utworzyć `GroupShape` poprzez drzewo węzłów, co jest bardziej skomplikowane. Aktualizacja jest zalecaną ścieżką.

## Porady profesjonalne

* **Używaj punktów dla spójności** – wewnętrzną jednostką Worda jest punkt (1/72 cala). Konwersja z pikseli lub centymetrów może prowadzić do nieoczekiwanych rozmiarów.  
* **Grupuj przed pozycjonowaniem** – pozycjonuj `GroupShape` po dodaniu wszystkich jego dzieci; w przeciwnym razie może być konieczne przeliczenie offsetów.  
* **Ponownie używaj DocumentBuilder** – możesz wstawiać wiele grup w tym samym dokumencie, przesuwając kursor buildera (`builder.moveTo`) przed każdym wywołaniem `insertGroupShape`.

## Zakończenie

Masz teraz kompletny, pełny przykład **jak grupować kształty w Wordzie** i **jak ustawiać wymiary kształtu** przy użyciu Aspose.Words for Java. Samouczek obejmował tworzenie dokumentu, wstawianie `GroupShape`, dodawanie prostokąta i elipsy, ustawianie ich dokładnego rozmiaru oraz zapisywanie wyniku.  

Od tego momentu możesz eksplorować:

* Dodawanie pól tekstowych lub obrazów do tej samej grupy.  
* Animowanie pogrupowanych kształtów przy użyciu funkcji SmartArt w Wordzie (przez API).  
* Eksportowanie pogrupowanych kształtów do PDF lub SVG do użytku w sieci.

Śmiało eksperymentuj z różnymi typami kształtów, rozmiarami i pozycjami — grupowanie daje Ci potężną kontrolę nad złożonymi układami w dokumentach Word.

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak utworzyć pusty dokument Word i grupować kształty w Javie](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [Jak grupować kształty w Wordzie przy użyciu Javy – kompletny przewodnik](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}