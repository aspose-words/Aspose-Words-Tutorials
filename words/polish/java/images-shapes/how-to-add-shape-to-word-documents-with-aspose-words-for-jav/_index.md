---
category: general
date: 2026-11-22
description: Dowiedz się, jak dodać kształt do dokumentu Word przy użyciu Aspose.Words
  for Java – wstaw prostokąt i ukryj go programowo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: pl
lastmod: 2026-11-22
og_description: Dodaj kształt do Worda przy użyciu Aspose.Words for Java. Ten samouczek
  pokazuje, jak wstawić prostokąt, ukryć kształt i zapisać dokument.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Dodaj kształt do Worda przy użyciu Aspose.Words – przewodnik Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Jak dodać kształt do dokumentów Word przy użyciu Aspose.Words dla Javy
url: /pl/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak dodać kształt do dokumentów Word przy użyciu Aspose.Words dla Javy

Jeśli potrzebujesz **dodać kształt do Word** dokumentów programowo, Aspose.Words for Java ułatwia to. W tym przewodniku dowiesz się **jak wstawić kształt**, kontrolować jego widoczność oraz **jak ukryć kształt**, aby ostateczny plik wyglądał dokładnie tak, jak tego oczekujesz.

Przejdziesz przez kompletny, działający przykład, który wczytuje istniejący plik `.docx`, wstawia prostokąt, ukrywa go i zapisuje wynik. Nie są wymagane żadne zewnętrzne skrypty ani ręczne kroki, a tutorial obejmuje typowe warianty, takie jak tworzenie nowego dokumentu od zera lub ukrywanie kształtu tylko podczas drukowania.

## Wymagania wstępne

* Java 17 (lub nowsza) zainstalowana – wcześniejsze wersje działają, ale najnowszy LTS zapewnia lepszą wydajność.  
* Maven 3.8+ do zarządzania zależnościami.  
* Ważna licencja Aspose.Words for Java (bezpłatna wersja ewaluacyjna wystarczy do nauki).  
* IDE lub edytor tekstu według wyboru (np. IntelliJ IDEA, VS Code).

## Krok 1: Dodaj Aspose.Words do swojego projektu Maven

Dodaj następującą zależność do swojego `pom.xml`. Pobierze ona najnowszą stabilną wersję (stan na listopad 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

**Pro tip:** Użyj klauzuli `<scope>provided</scope>` jeśli planujesz dystrybuować JAR z własną logiką licencjonowania.

## Dodaj kształt do Word – inicjalizacja dokumentu

Pierwszym funkcjonalnym krokiem jest uzyskanie obiektu `Document`. Możesz wczytać istniejący plik lub utworzyć nowy.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Dlaczego to ważne*: Klasa `Document` jest punktem wejścia dla wszystkich manipulacji Word. Wczytanie istniejącego pliku zachowuje style, nagłówki i stopki, natomiast nowy dokument daje czystą kartę.

## Jak wstawić kształt w dokumencie Word

Następnie utwórz `DocumentBuilder`, aby modyfikować zawartość dokumentu. Builder udostępnia metody do wstawiania tekstu, tabel i **kształtów**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

Wywołanie `insertShape` zwraca obiekt `Shape`, który możesz dalej konfigurować (kolor, obramowanie, tekst itp.). Wymiary podawane są w punktach (1 pt = 1/72 in).

*Dlaczego możesz używać prostokąta*: Prostokąty są najczęściej używanymi kontenerami dla adnotacji, znaków wodnych lub placeholderów. Możesz zamienić `ShapeType.RECTANGLE` na `ShapeType.ELLIPSE`, `ShapeType.LINE` itp., aby spełnić różne potrzeby wizualne.

## Jak ukryć kształt w Word

Czasami potrzebujesz, aby kształt istniał w obliczeniach układu, ale nie pojawiał się w ostatecznym renderowaniu. Aspose.Words udostępnia metodę `setHidden(true)`, aby to osiągnąć.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

Flaga ukrycia działa jak opcja formatowania **Hidden** w Microsoft Word: kształt jest pomijany w widocznym układzie, ale nadal uczestniczy w modelu obiektowym dokumentu. Jest to przydatne do:

* Przechowywania metadanych lub znaczników, które później odczytuje Twoja aplikacja.  
* Tworzenia placeholderów, które są usuwane tuż przed publikacją.  
* Kontrolowania widoczności dla różnych formatów wyjściowych (np. ukrycie w HTML, ale zachowanie w PDF).

**Uwaga:** Ukryte kształty są domyślnie eksportowane do PDF. Jeśli potrzebujesz, aby były pomijane także w PDF, ustaw `rectangle.getWrapType() = WrapType.NONE` i odpowiednio dostosuj właściwość `Hidden`.

## Krok 4: Zapisz zmodyfikowany dokument

Na koniec zapisz zmiany do nowego pliku.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

Gdy otworzysz `output.docx` w Microsoft Word, prostokąt nie będzie widoczny, ale pozostanie częścią drzewa dokumentu. Możesz zweryfikować jego obecność programowo, ponownie wczytując plik i sprawdzając `Shape.isHidden()`.

### Oczekiwany wynik

* Plik `output.docx` otwiera się bez widocznych kształtów.  
* Jeśli przeanalizujesz dokument przy użyciu Aspose.Words (np. `doc.getChildNodes(NodeType.SHAPE, true).size()`), liczba kształtów będzie **1**, co potwierdza, że kształt istnieje, ale jest ukryty.

## Zaawansowane warianty i przypadki brzegowe

### 1. Tworzenie kształtu w nowym dokumencie

Jeśli zaczynasz od zera, zamień linię ładowania na:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Precyzyjne pozycjonowanie kształtu

Domyślnie `insertShape` umieszcza kształt w bieżącej pozycji kursora. Aby pozycjonować go absolutnie:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Kontrola widoczności w zależności od formatu wyjściowego

Jeśli potrzebujesz, aby kształt był widoczny w interfejsie Word, ale ukryty przy eksporcie do PDF, użyj `Shape.setWrapType(WrapType.NONE)` razem z `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Dodawanie tekstu wewnątrz kształtu

Prostokąt może zawierać ramkę tekstową:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Możesz następnie ukryć pole tekstowe tym samym wywołaniem `setHidden(true)`.

## Typowe pułapki i jak ich unikać

| Objaw | Przyczyna | Rozwiązanie |
|-------|-----------|-------------|
| Kształt pojawia się mimo `setHidden(true)` | Dokument został zapisany przed ustawieniem flagi ukrycia. | Upewnij się, że wywołujesz `setHidden(true)` **przed** `doc.save()`. |
| Rozmiar kształtu jest zniekształcony | Mieszanie punktów i pikseli na ekranach o wysokiej rozdzielczości DPI. | Używaj punktów (72 pt = 1 in) dla spójnych rozmiarów na wszystkich platformach. |
| Ukryty kształt nadal drukuje się | Niektóre drukarki ignorują flagę ukrycia. | Ustaw `Shape.setWrapType(WrapType.NONE)` i dodatkowo wyczyść `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## Podsumowanie

Teraz wiesz, jak **dodać kształt do dokumentów Word** przy użyciu Aspose.Words for Java, **jak wstawić kształt** oraz **jak ukryć kształt**, aby pozostał niewidoczny dla użytkowników końcowych, a jednocześnie był częścią struktury dokumentu. Pełny przykład powyżej wczytuje plik, wstawia prostokąt, ukrywa go i zapisuje wynik, obejmując zarówno typowe przypadki użycia, jak i kilka sytuacji brzegowych.

Od tego momentu możesz zgłębiać powiązane tematy, takie jak **jak wstawić kształt** z niestandardowymi kolorami wypełnienia, **jak ukryć kształt w Word** dla warunkowego drukowania, czy automatyzacja masowego przetwarzania dokumentów przy użyciu Aspose.Words. Eksperymentuj z różnymi wartościami `ShapeType`, opcjami pozycjonowania i flagami widoczności, aby dopasować je do swojego konkretnego przepływu pracy.

Miłego kodowania i ciesz się elastycznością, jaką programowa manipulacja Word przynosi Twoim aplikacjom Java!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Utwórz dokument Word programowo, dodaj i ukryj kształt w Javie przy użyciu Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Jak ukryć kształt w dokumencie Word przy użyciu Javy](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Utwórz pusty dokument .docx Word i dodaj ukryty prostokątny kształt przy użyciu Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}