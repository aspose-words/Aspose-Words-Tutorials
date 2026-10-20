---
category: general
date: 2026-09-21
description: Utwórz dokument Word programowo przy użyciu Javy. Dowiedz się, jak grupować
  kształty w Wordzie, wstawiać prostokąt, ustawiać rozmiar kształtu i dodawać kształty
  do dokumentu Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: pl
lastmod: 2026-09-21
og_description: 'Tworzenie dokumentu Word programowo w Javie: ten przewodnik pokazuje,
  jak grupować kształty w Wordzie, wstawiać prostokątne kształty, ustawiać rozmiar
  kształtu i dodawać kształty do dokumentu Word.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Tworzenie dokumentu Word programowo, grupowanie kształtów w Javie
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Tworzenie dokumentu Word programowo, grupowanie kształtów w Javie
url: /pl/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz dokument Word programowo, grupuj kształty w Javie

Jeśli potrzebujesz **tworzyć dokument Word programowo**, ten przewodnik przeprowadzi Cię przez kompletną rozwiązanie. Zobaczysz, jak **grupować kształty w Wordzie**, wstawić prostokąt, ustawić jego rozmiar i dodać inne kształty — wszystko przy użyciu Javy i biblioteki Aspose.Words for Java.

Poradnik obejmuje każdy krok, od konfiguracji projektu po zapisanie finalnego pliku .docx. Po zakończeniu będziesz w stanie wygenerować dokument Word, który zawiera prostokąt i obraz owinięte w jedną grupę, co ułatwia ich jednoczesne przenoszenie lub skalowanie. Nie wymagana jest wcześniejsza znajomość API Aspose.Words, ale powinieneś mieć podstawowe środowisko programistyczne Javy.

## Wymagania wstępne

* Java Development Kit (JDK) 8 lub nowszy  
* Maven lub Gradle do zarządzania zależnościami  
* Aspose.Words for Java 23.9 (lub najnowsza wersja) – biblioteka jest darmowa w wersji ewaluacyjnej  
* Plik obrazu (np. `sample.jpg`) umieszczony w znanym katalogu  

Posiadanie tych elementów zapewnia, że kod uruchomi się bez dodatkowej konfiguracji.

## Krok 1: Skonfiguruj projekt i zaimportuj Aspose.Words

Utwórz projekt Maven (lub dodaj zależność do istniejącego `pom.xml`):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Jeśli wolisz Gradle, dodaj następujące linie do `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

Po rozwiązaniu zależności, zaimportuj wymagane klasy w swoim pliku źródłowym Java:

```java
import com.aspose.words.*;
import java.io.File;
```

## Krok 2: Utwórz dokument Word programowo

Pierwszą operacją w każdym scenariuszu automatyzacji jest utworzenie obiektu `Document` oraz `DocumentBuilder`. Builder upraszcza wstawianie tekstu, obrazów i kształtów.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

W tym momencie dokument istnieje wyłącznie w pamięci. Możesz teraz rozpocząć dodawanie kształtów.

## Krok 3: Wstaw kształt prostokąta – jak wstawić kształt prostokąta

Prostokąt to podstawowy `Shape` z `ShapeType.RECTANGLE`. Kontrolujesz jego wymiary za pomocą `setWidth`, `setHeight`, a pozycję przy pomocy `setTop` i `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Dlaczego to ważne:** Ustawienie rozmiaru i pozycji explicite (`set shape size word`) gwarantuje, że prostokąt pojawi się dokładnie tam, gdzie tego oczekujesz, niezależnie od domyślnego układu dokumentu.

## Krok 4: Wstaw obraz – dodaj kształty do dokumentu Word

`DocumentBuilder` może wstawić obraz bezpośrednio z ścieżki pliku. Po wstawieniu możesz przemieścić obraz tak samo, jak każdy inny kształt.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Zarówno prostokąt, jak i obraz są teraz niezależnymi kształtami wewnątrz dokumentu.

## Krok 5: Grupuj kształty – jak grupować kształty w Wordzie

Grupowanie kształtów jest przydatne, gdy chcesz przenosić lub skalować je jako jedną jednostkę. Aspose.Words udostępnia kontener `GroupShape` w tym celu.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

Po zapisaniu grupy, Word traktuje dwa elementy jako jeden logiczny obiekt. Później możesz wybrać grupę i przeciągnąć ją, a zarówno prostokąt, jak i obraz podążą za nią.

## Krok 6: Zapisz dokument

Na koniec zapisz dokument na dysku. Ścieżka musi być zapisywalna przez proces Java.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Uruchomienie metody `main` tworzy plik o nazwie **GroupShapeExample.docx**. Otwórz go w Microsoft Word, aby zobaczyć prostokąt i obraz zablokowane razem w grupie. Wybranie grupy pozwala przenieść oba obiekty jednocześnie, potwierdzając, że grupowanie się powiodło.

## Oczekiwany wynik

* Plik Word (`GroupShapeExample.docx`) znajdujący się w katalogu, który określiłeś.  
* Wewnątrz pliku prostokąt (wypełnienie jasnoszare) pojawia się w lewym górnym rogu, a obraz znajduje się bezpośrednio pod nim.  
* Oba obiekty są częścią jednej grupy, więc przeciągnięcie jednego przesuwa drugi.

## Typowe warianty i przypadki brzegowe

| Situation | Recommendation |
|-----------|----------------|
| **Different image formats** | Aspose.Words supports PNG, BMP, GIF, and TIFF. Use the appropriate file extension in `insertImage`. |
| **Negative dimensions** | The API throws `ArgumentException`. Always validate width and height before calling `setWidth` / `setHeight`. |
| **Large documents** | Grouping many shapes can increase file size. Consider merging shapes into a single picture when performance matters. |
| **Word version compatibility** | GroupShape works with Word 2007 (`.docx`) and later. For older `.doc` files, the group will be flattened. |
| **Dynamic positioning** | Use calculations based on page size (`doc.getFirstSection().getPageSetup().getPageWidth()`) if you need adaptive placement. |

**Wskazówka:** Po utworzeniu grupy możesz zmienić

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}